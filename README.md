Задание 1 – Создать объект counter всеми возможными способами;

`Литеральная нотация:`

```javascript
let counter = { key: 'value' };
```

`С помощью конструктора Object:`

```javascript
let counter = new Object();```
counter.key = 'value';
```

`С использованием Object.create():`

```javascript
let counter = Object.create(null);
counter.key = 'value';
```

`С использованием синтаксиса класса:`

```javascript
class newCounter {
  constructor() {
    this.key = 'value';
  }
}
let counter = new newCounter();
```

`С использованием Object.assign():`

```javascript
let counter = Object.assign({}, { key: 'value' });
```

`С использованием spread-оператора:`

```javascript
let counter = { ...{ key: 'value' } };`
```


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
