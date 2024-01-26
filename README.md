Задание 1 - Написать ответ - почему массивы в JS являются "неправильными" и совмещают в себе несколько структур данных? Какие?

`Массивы в JS могут быть "неправильными" потому что они не строго типизированы и могут содержать элементы различных типов данных.
Это связано с тем, что массивы в JavaScript основаны на объектах, а не на строгой последовательности элементов одного типа, как в других ЯП.
В результате совмещают в себе несколько структур данных:`
`1) Список (List): могут быть использованы как список элементов, где каждый элемент имеет свой индекс. Они обеспечивают быстрый доступ к элементам по индексу.`
`2) Стек (Stack) и Очередь (Queue): могут использоваться как стек или очередь благодаря методам push() и pop() для стека, а также shift() и unshift() для очереди.`
`3) Ассоциативный массив (Associative Array) или Хеш-таблица (Hash Table): Из-за того, что массивы в JavaScript являются объектами, они могут содержать не только числовые индексы, но и строки в качестве ключей, что делает их похожими на ассоциативные массивы или хеш-таблицы.`
`4) Список списков: Массивы могут содержать в себе другие массивы, создавая таким образом списки списков или многомерные массивы.`

Задание 2 - Привязать контекст объекта к функции logger, чтобы при вызове this.item выводило - some value (Привязать через bind, call, apply)

`Bind:`
```javascript
function logger() {
    console.log(`I output only external context: ${this.item}`);
}

const obj = { item: "some value" };

const bindLogger = logger.bind(obj);
bindLogger();
```

`Call:`
```javascript
function logger() {
    console.log(`I output only external context: ${this.item}`);
}

const obj = { item: "some value" };
logger.call(obj); 
```

`Apply:`
```javascript
function logger() {
    console.log(`I output only external context: ${this.item}`);
}

const obj = { item: "some value" };
logger.apply(obj);
```

Бонус задание: Реализовать полифил(собственную функцию реализующую встроенную в js) метода bind()

```javascript
Funtion.proptotype.bind = funtion(context){
	const func = this;
	return function(…args) {

		return func.apply(
			context,
			args
		);
	}
}
```
