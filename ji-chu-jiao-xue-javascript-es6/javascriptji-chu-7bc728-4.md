## Exports & Imports (Modules)

在撰寫 API 過程中你會將很多分支檔案拆開寫，一方面是減少過長的程式碼另一方面是日後好管理。你必須要先匯出分支檔(export)再經由主檔案中被引入(import)，以下有個簡單例子，第一個分支檔 person.js 將函式 person 匯出，第二支分支檔將函式 clean 和變數 bastData 匯出 (另一種匯出寫法) ，最後再主檔案 index.js 引入被呼叫使用。

- 分支檔 person.js、utility.js
```js
// person.js 分支檔1
const person ={
  name:'Andy'
} 

export default person;
```

```js
// utility.js 分支檔2
export const clean = () => {}
export const bastData = 10;
```

- 主檔 index.js
```js
// index.js
//default export
import person from './person.js';
//named export
import {baseData} from './utility.js';
import {clean} from './utility.js';

//named export (rename)
import {clean as c} from './utility.js';
import * as c from './utility.js';

```
### 四種不同寫法

1. export default{ } 集中匯出

- 分支檔 utility.js
```js
//utility.js

const app1 = () => {
  console.log('app1');
};

const app2 = () => {
  console.log('app2');
};

export default { app1, app2 };

```

- 主檔 index.js
```js
//index.js
import app from './utility';

app.app1();
app.app2();

```

2. 單個變數匯出，並ㄧ次引入所有

此寫法可以注意觀察主檔 index.js，使利用萬用字元 `*` 表示該檔內所有變數引入。 

- 分支檔 utility.js
```js
//utility.js
export const app1 = () => {
  console.log('app1');
};

export const app2 = () => {
  console.log('app2');
};
```

- 主檔 index.js
```js
//index.js
import * as app from './utility';


app.app1();
app.app2();
```
3. 單個變數匯出，並分別引入

此寫法在主檔 index.js 引入時在大括號內著名是要引入哪個變數。

- 分支檔 utility.js
```js
//utility.js
export const app1 = () => {
  console.log('app1');
};

export const app2 = () => {
  console.log('app2');
};
```

- 主檔 index.js
```js
//index.js
import { app1 } from './utility';
import { app2 } from './utility';

app1();
app2();
```

4. 單個變數匯出，並分別引入與重新命名

此寫法與第三種相類似差別在於引入進來的變數給予重新命名。

- 分支檔 utility.js
```js
//utility.js
export const app1 = () => {
  console.log('app1');
};

export const app2 = () => {
  console.log('app2');
};
```

- 主檔 index.js
```js
//index.js
import { app1 as App1 } from './utility';
import { app2 as App2 } from './utility';

App1();
App2();
```


## Classes

在物件導向程式設計，類別是一種物件導向電腦程式語言的構造，是建立物件的藍圖，描述了所建立的物件共同的屬性和方法。

- ㄧ個 class 是由屬性 (Property) 和方法 (Method) 所組成


```js
class Person {
  constructor() {
    this.name = 'Andy';
  }
  call=() => {
    console.log(this.name);
  }
}

const myPerson = new Person();

myPerson.call();

```

- 繼承寫法

```js
class Human {
  constructor() {
    this.gender = 'male';
  }
}

class Person extends Human {
  constructor() {
    super();
    this.name = 'Andy';
  }
  call=() => {
    console.log(this.name);
    console.log(this.gender);
  }
}

const myPerson = new Person();

myPerson.call();
```
由於上述都是 ES6 寫法，可以利用線上編譯器來編譯程式碼。

https://jsbin.com/sobapehifu/edit?html,js,console,output


文章同時發表於：https://andy6804tw.github.io/2017/12/21/js-tutorial-part4/