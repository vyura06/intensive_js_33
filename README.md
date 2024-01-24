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

`Spread-оператор:`

```javascript
const counter = { key: 'value' };
const newCounter = { ...counter };
```

`Object.assign():`

```javascript
const counter = { key: 'value' };
const newCounter = Object.assign({}, counter)
```

`JSON.parse() и JSON.stringify():`

```javascript
const counter = { key: 'value' };
const newCounter = JSON.parse(JSON.stringify(counter));
```

`Object.create() и Object.getOwnPropertyDescriptors():`

```javascript
const counter = { key: 'value' };
const newCounter = Object.create(Object.getPrototypeOf(counter), Object.getOwnPropertyDescriptors(counter));
```

`Расширение объекта (Object.assign() с Object.create()):`
```javascript
const counter = { key: 'value' };
const newCounter = Object.create(Object.getPrototypeOf(counter));
Object.assign(newCounter, counter);
```

Задание 3 – Создать функцию makeCounter всеми описанными и возможными способами;

`Объявление функции:`

```javascript
function makeCounter() {}
```

`Функциональное выражение:`

```javascript
const makeCounter = function() {};
```

`Стрелочная функция:`

```javascript
const makeCounter = () => {};
```

`Конструктор Function:`

```javascript
const makeCounter = new Function('arg1', 'arg2', 'return arg1 + arg2');
```

`Метод объекта:`

```javascript
const counter = {
  makeCounter: function() {}
};
```

`Функция-генератор:`

```javascript
function* makeCounter() {}
```

`Функция-конструктор:`

```javascript
function counter() {
  this.counterProperty = 'value';
}
const makeCounter = new counter();
```

`Функция высшего порядка (функция, возвращающая функцию):`

```javascript
function outerCounter() {
  return function innerCounter() {
  };
}
const makeCounter = outerCounter();
```

Бонус
Задание 1 –
Написать функцию глубокого сравнения двух объектов:

`Задание:`

```javascript
const obj1 = { here: { is:
"on", other: "3" }, object: "Y" };

const obj2 = { here: { is:
"on", other: "2" }, object: "Y" };

const deepEqual =
(obj1, obj2) => {};
```

`Решение:`

```javascript
const areDeeplyEqual = (obj1, obj2) => {
  if (obj1 === obj2) return true;

  if (Array.isArray(obj1) && Array.isArray(obj2)) {
    if (obj1.length !== obj2.length) return false;

    return obj1.every((elem, index) => {
      return areDeeplyEqual(elem, obj2[index]);
    });
  }

  if (typeof obj1 === "object" && typeof obj2 === "object" && obj1 !== null && obj2 !== null) {
    if (Array.isArray(obj1) || Array.isArray(obj2)) return false;

    const keys1 = Object.keys(obj1);
    const keys2 = Object.keys(obj2);

    if (keys1.length !== keys2.length || !keys1.every(key => keys2.includes(key))) return false;

    for (let key in obj1) {
      let isEqual = areDeeplyEqual(obj1[key], obj2[key]);
      if (!isEqual) {
        return false;
      }
    }

    return true;
  }

  return false;
};

const obj1 = { here: { is: "on", other: "3" }, object: "Y" };
const obj2 = { here: { is: "on", other: "2" }, object: "Y" };

const deepEqual = (obj1, obj2) => {
  return areDeeplyEqual(obj1, obj2);
};
```

Бонус 
Задание 2 –
Развернуть строку в обратном направлении при помощи методов массивов:

```javascript
function reverseString(str) {
    return str.split("").reverse().join("");
}
```
