Задание 1 – Создать объект counter всеми возможными способами;

`Литеральная нотация:`
<pre>
```javascript
let counter = { key: 'value' };
```
</pre>
`С помощью конструктора Object:`
<pre>
```javascript
let counter = new Object();```
counter.key = 'value';
```
</pre>
`С использованием Object.create():`
<pre>
```javascript
let counter = Object.create(null);
counter.key = 'value';
```
</pre>
`С использованием синтаксиса класса:`
<pre>
```javascript
class newCounter {
  constructor() {
    this.key = 'value';
  }
}
let counter = new newCounter();
```
</pre>
`С использованием Object.assign():`
<pre>
```javascript
let counter = Object.assign({}, { key: 'value' });
```
</pre>
`С использованием spread-оператора:`
<pre>
```javascript
let counter = { ...{ key: 'value' } };`
```
</pre>

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
