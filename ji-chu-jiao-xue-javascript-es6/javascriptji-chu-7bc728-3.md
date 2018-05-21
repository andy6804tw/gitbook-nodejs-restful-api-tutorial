## 陣列 Array
這篇文章要來介紹容器，首先先來談談陣列，陣列是有順序地存放大量資料的結構，大多數程式語言都是 0 為起始點，例如 `arr[0]` ， JavaScript 也不例外，當然 JavaScript 的陣列也內建很多函式可以直接呼叫例如 length、match...等。

### 陣列的使用
陣列的初始化有兩種方式一種是立即給值，另一種是後續給值。

- 立即給值

```js
const arr = [1, 2, 3]
console.log(arr.length) // 3
```

- 後續給值

```js
const arr = []
arr[0] = 1
arr[1] = 2
arr[2] = 3
console.log(arr.length) // 3
```

### 展開(spread)運算子

展開運算值是 ES6 的一個新的特性，可以使用 `...` 代表陣列，以下用函式來做示範，當不知道引數有多少時可以很方便使用，這邊先粗略提起稍後會拉出來更詳細解說。

```js
const call = (...arr) => {
  console.log(arr); // [ 1, 2, 3 ]
};
call(1, 2, 3); 
```

## 物件 Object
物件是現今儲存資料最常見的一種型態，主要是以一個鍵 (key) 搭配一個值 (value) ，如下範例。

```js
const dog = {
      name: 'Tom',
      breed: 'Golden Retriever',
      weight: 60
    }
```

### 如何存取物件內的值

有兩種方法分別如下，第一種是利用 `物件名稱.key` 拿取值，第二種方法是利用陣列回傳方式 `物件名稱[key]` 取得相對應內容。

```js
console.log(dog.breed) // Golden Retriever
console.log(dog[breed]) // Golden Retriever
```

## 物件使用 forEach 方法
這邊介紹陣列的 forEach 方法，雖然 for...in 也是可以，但  ESLint 並不推薦你這樣做，所以就不再今天討論範圍囉！

```js
const dog = {
      name: 'Tom',
      breed: 'Golden Retriever',
      weight: 60
    };
    Object.keys(dog).forEach((key) => {
      console.log(dog[key]);
    });

  輸出：
        // Tom
        // Golden Retriever
        // 60
```

### 物件夾帶方法
是的沒錯在物件中不僅僅只儲存值方法也行，就把它想成一個 function 存在一個變數中就對了使用方法延伸上面的例子如下。

```js
const dog = {
      name: 'Tom',
      breed: 'Golden Retriever',
      weight: 60,
      breaks() {
        console.log('woof'); 
      }
    };
dog.breaks(); // woof
``` 

##  Spread & Rest Operators

- 符號都是三個點(...)(free dots)
- 都是在陣列值運算
- 一個是展開陣列中的值，一個是集合其餘的值成為陣列

### 展開運算子
- 展開運算子(Spread Operator)
  - Used to split up array element or object poperties
  - 簡單來說像是陣列與物件的變數繼承

```js
// 陣列展開用法
const numbers = [1, 2, 3];
const newNumbers = [...numbers, 4];

console.log(newNumbers);
```
> output: [1, 2, 3, 4]

```js
// 物件展開用法
const person = {
  name: 'Andy',
};
const newPerson = {
  ...person,
  age: 21,
};

console.log(newPerson);
```
> output: { name: 'Andy', age: 21 }


### 其餘運算符

- 其餘運算符(Rest Operator)
  - Used to merge a list of function arguments into an array
  - 雖然與展開運算子特性的符號是一模一樣的，都是三個點(...)，但使用的情況與意義不同

Array.filter()方法會過濾陣列的元素，並將通過測試的元素傳回成為一個新陣列。
Array.filter()方法使用回呼函式來對元素進行過濾，須由設計師自行撰寫過濾程式。
```js
// Array.filter() 過濾陣列元素
const filter = (...args) => args.filter(el => el === 2);

console.log(filter(1, 2, 3));
```
> output: [ 2 ]


## Destructuring Assignment (解構賦值)

- Easily extract array elements or object properties and store them in variables
- 解構解構允許你拉出單個元素或屬性，並將他們儲存在數組的變數中

- Array Destructuring
```js
const numbers = [1, 2, 3];
const [num1, num2] = numbers;

console.log(num1, num2);
```

## Reference and Primitive Types

- 變數參數傳值(passed by value)
```js
let num1 = 1;
const num2 = num1;
num1 = 2;

console.log(num1, num2);
```
> output: 2 1

- 物件傳址(passed by reference)
```js
const person = {
  name: 'Andy'
};
const secondPerson = person;

person.name = 'Tank';

console.log(secondPerson);
```
> output: { name: 'Tank' }


此方法是複製屬性而不是整個物件
```js
const person = {
  name: 'Andy'
};
const secondPerson = {
  ...person
};

person.name = 'Tank';

console.log(secondPerson);
```
> output: { name: 'Andy' }


文章同時發表於：https://andy6804tw.github.io/2017/12/20/js-tutorial-psrt3/
