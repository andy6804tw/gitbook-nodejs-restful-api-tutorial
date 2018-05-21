## 控制流程
任何一種程式語言程式碼都是由上而下逐一執行的，此外有時候必須程式判斷依照不同的數值給予不同的路徑輸出，稱之為控制流程。

### 區塊(block)
ES6 中新增了程式區塊是用大括號包起來的區域：
```js
{
  statement 1
  statement 2
  ...
  statement n
}
```
### if...esle 判斷式

if...else 是任何語言最常見的控制流程語句，他的概念非常簡單以下用 pseudo code 演示：
```js
if (今天天氣好) {

  出處走走

} else {
  
  關在家裡

}
```

此外在開發上若遇到大量的if、esle if、else 會造成程式冗長與不易閱讀，所以這時就可以使用 switch 判斷也可以達到相同效果。

```js
switch (expression) {
  case value1:
    //符合時執行語句
    break;
  case value2:
    //符合時執行語句
    break;
  ...
  default:
    //以上都無則進入此區域
    break;n
}
```
## 迴圈
迴圈總共分為三種寫法分別有 for、while、do while，其中最常見也被最常使用的就非 for 迴圈莫屬了，故這邊就先只提 for 一種。

### for 語句
for 迴圈的小括號內有三個參數用分號隔開，它們各自有其功用，for迴圈的基本語法如下:

- 參數一控制變數初始值
- 參數二設定週期
- 參數三設定每次間隔

```js
for (let i = 0 ; i < 10 ; i +=1){
    console.log(i);
}
```
這邊值得一提的是我並不是使用 `i++` 做每次間隔，由於 ESLint 建議`Unary operator '++' used. (no-plusplus)` 不要使用 `++ --` [官方](https://github.com/airbnb/javascript)是這樣說的
> Why? Per the eslint documentation, unary increment and decrement statements are subject to automatic semicolon insertion and can cause silent errors with incrementing or decrementing values within an application. It is also more expressive to mutate your values with statements like num += 1 instead of num++ or num ++. Disallowing unary increment and decrement statements also prevents you from pre-incrementing/pre-decrementing values unintentionally which can also cause unexpected behavior in your programs.

簡單來說使用一元遞增(減)會導致程序中的意外行為所以盡量不要使用

### for of 和 foEach 語句

* for of

for of 是 ES6 新增的語句，可用於迭代就件上取出容器裡的值例如陣列、Map、Set、字串等等。

```js
let mArray = [1, 2, 3]
for (let value of mArray) {
  console.log(value); // 1 2 3
}

```

* foEach

foEach是屬於陣列裡的一個方法他也可以做出相同的事情。
```js
const numbers = [1, 2, 3, 4, 5];
let sum = 0;
numbers.forEach(num => sum += num);
console.log(sum) // 15
```


## 函式(function)
箭頭函式在 JavaScript 中改寫原本 function 的撰寫方式。除了較短的語法外，它們在保持this  關鍵字範圍方面也有優勢 [參見這裡](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#No_binding_of_this)，此外在 ESLint 中官方也建議使用箭頭函式取代傳統寫法。

函式 (function) 又稱方法 (method)，用於程式碼過多重複時定義一個方法來去重複呼叫他來解省我們的開發效率，以下為範例：

#### 原本寫法

```js
// 使用有名稱的函式
function sum(a, b){
    return a+b;
}

// 常數指定為匿名函式
const sum = function(a, b) {
    return a+b;
}
```

#### 變成

```js
const sum = (x, y) => {
  return x + y;
};

console.log(sum(1, 3)); 

```
> output: 4


### 撰寫方式

##### 1. 當你在宣告時若沒有傳入值(arguments)，必須放空括號。

```js
const callMe = () => { 
    console.log('Max!');
}
```

##### 2. 當只有一個傳入值(arguments)，可以省略括號。

```js
const callMe = name => { 
    console.log(name);
}
```

##### 3. 當函式有回傳時可濃縮一行

```js
const doubleNum = num => num * 2;

console.log(doubleNum(5));
```

相等於

```js
const doubleNum = (num) => {
  return num * 2;
};
console.log(doubleNum(5));

```

> output: 10



文章同時發表於：https://andy6804tw.github.io/2017/12/19/js-tutorial-psrt2/
