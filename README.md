Задание 1 – Создать объект counter всеми возможными способами;
`Литеральная нотация:`
```javascript
let objLiteral = { key: 'value' };```
<pre>
```javascript
let objLiteral = { key: 'value' };
```</pre>
`С помощью конструктора Object:`
```javascript
let objConstructor = new Object();```
objConstructor.key = 'value';
С использованием Object.create():
javascript
Copy code
let objCreate = Object.create(null);
objCreate.key = 'value';
С использованием синтаксиса класса:
javascript
Copy code
class MyObject {
  constructor() {
    this.key = 'value';
  }
}

let objClass = new MyObject();
С использованием Object.assign():
javascript
Copy code
let objAssign = Object.assign({}, { key: 'value' });
С использованием spread-оператора:
javascript
Copy code
let objSpread = { ...{ key: 'value' } };`

Задание 2 – Скопировать объект counter всеми
возможными способами;

Задание 3 – Создать функцию makeCounter всеми описанными и возможными способами;

Бонус
Задание 1 –
Написать функцию глубокого сравнения двух объектов:


const obj1 = { here: { is:
"on", other: "3" }, object: "Y" };

const obj2 = { here: { is:
"on", other: "2" }, object: "Y" };

const deepEqual =
(obj1, obj2) => {};


Бонус 
Задание 2 –
Развернуть строку в обратном направлении при помощи методов массивов:

function reverseStr(str) {
  return …
}
