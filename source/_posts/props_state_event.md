---
title: Props、State、Refs 與表單處理
---
文章連結 https://github.com/kdchang/reactjs101/blob/master/Ch04/props-state-introduction.md

# 1. props驗證與預設值

針對傳入的 props 設計驗證和預設值，讓我們撰寫的元件可以更加穩定健壯（robust）。

在以下的例子中，使用 Welcome 的人沒有正確使用，導致 Welcome 無法正確顯示。驗證器會將錯誤訊息寫在 console，以協助我們除錯。

## 作業一：
請按下面的 `EDIT ON CODEPEN`，把 Welcome 依照驗證器指定的格式修復好。

## __NOTE:__
React v15.5 之後，教學裡使用的 `React.PropTypes` 被獨立出來了，因此需要額外安裝。以下範例已經有安裝好了。
安裝教學：https://github.com/facebook/prop-types

<iframe height='411' scrolling='no' title='Typechecking With PropTypes' src='//codepen.io/iampaul83/embed/mBrpzy/?height=411&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='https://codepen.io/iampaul83/pen/mBrpzy/'>Typechecking With PropTypes</a> by Paul Tsai (<a href='https://codepen.io/iampaul83'>@iampaul83</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

# 2. State

在 Timer 例子中可以看到以下這個程式碼：

```js
tick() {
    this.setState({secondsElapsed: this.state.secondsElapsed + 1});
}
```

根據[官網教學：State Updates May Be Asynchronous][1]：
> `setState`時，不能應該使用`this.state`的值

[1]: https://facebook.github.io/react/docs/state-and-lifecycle.html#state-updates-may-be-asynchronous

解決方法是：
傳入一個`function`給`setState`，使用這個function的prevState與props參數來設定下一個state:
```js
this.setState((prevState, props) => {
    return {secondsElapsed: prevState.secondsElapsed + 1};
})
```

## 作業二：
請按下面的 `EDIT ON CODEPEN`，依照上面的方式修正，讓畫面正常顯示成以下結果：
```
count1 == 1
count2 == 1
```

<iframe height='441' scrolling='no' title='state陷阱' src='//codepen.io/iampaul83/embed/PJGRaX/?height=441&theme-id=0&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='https://codepen.io/iampaul83/pen/PJGRaX/'>state陷阱</a> by Paul Tsai (<a href='https://codepen.io/iampaul83'>@iampaul83</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>


# 3. 事件處理（Event Handle）

JSX 和 HTML 的 event 語法不太一樣：

| JSX | HTML | 說明 |
| --- | ---- | --- |
| onclick | onClick | JSX 要用 camelCase 命名規則 |
| `onclick="someFunction()"` | onClick={someFunction} | JSX 要使用 `{ aFunction }` 的語法 |

## 作業三：
請加下面的 HTML 語法，改成用 JSX 撰寫

```html
<button onclick="activateLasers()">
  Activate Lasers
</button>
```

## 可略過的作業四：
請加下面的 HTML 語法，改成用 JSX 撰寫

<iframe height='157' scrolling='no' title='pWEKoa' src='//codepen.io/iampaul83/embed/pWEKoa/?height=157&theme-id=0&default-tab=html,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='https://codepen.io/iampaul83/pen/pWEKoa/'>pWEKoa</a> by Paul Tsai (<a href='https://codepen.io/iampaul83'>@iampaul83</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

