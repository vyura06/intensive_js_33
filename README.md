Домашнее задание(Порешать типовые задачи - написать порядок и вывод в консоли): 

1)
```javascript
let promiseTwo = new Promise((resolve, reject) => {
   resolve("a");
});

promiseTwo
.then((res) => {
   return res + "b";
})
.then((res) => {
   return res + "с";
})
.finally((res) => {
   return res + "!!!!!!!";
})
.catch((res) => {
   return res + "d";
})
.then((res) => {
   console.log(res);
});
```

`Порядок:`

`1) PromiseTwo //a`

`2) then() для promiseTwo //ab`

`3) следующий метод then() //abc`

`4) finally, но он будет проигнорирован, т.к не возвращает промис`

`5) catch, но проигнорирован, т.к промис выполнен`

`6) then() принимает 'abc' и выводит в консоль`

`Результат: 'abc'`

2)
```javascript
function doSmth() {
   return Promise.resolve("123");
}

doSmth()
.then(function (a) {
   console.log("1", a); //
   return a;
})
.then(function (b) {
   console.log("2", b);
   return Promise.reject("321");
})
.catch(function (err) {
   console.log("3", err);
})
.then(function (c) {
   console.log("4", c);
return c;
});
```

`Порядок:`

`1) Вызывается фунция doSmth //123`

`2) метод .then() для этого Promise, возвращает а //1 123`

`3) следующий .then(), возвращает '321' //2 123`

`4) из-за того, что промис был отклонен дальше вызывается catch и добавляет //3 321`

`5) следующий .then(), примимает c, но аргумент не определен //4 undefined`

`Результат: 
'1 123'
'2 123'
'3 321'
'4 undefined'
`

3) Напишите функцию, которая будет проходить через массив целых чисел и выводить индекс каждого элемента с задержкой в 3 секунды.
Входные данные: [10, 12, 15, 21]

```javascript
function printIndexesWithDelay(array) {
    array.forEach((element, index) => {
        setTimeout(() => {
            console.log(index);
        }, index * 3000);
    });
}

const numbers = [10, 12, 15, 21];
printIndexesWithDelay(numbers);
```

4) Прочитать про Top Level Await (можно ли использовать await вне функции async)

БОНУС ЗАДАНИЕ 
/* Необходимо реализовать функцию fetchUrl, которая будет использоваться следующим образом.
Внутри fetchUrl можно использовать условный метод fetch, который просто возвращает
Promise с содержимым страницы или вызывает reject */
fetchUrl('https://google/com&#39;)
.then(...)
.catch(...) // сatch должен сработать только после 5 неудачных попыток
получить содержимое страницы внутри fetchUrl

```javascript
function fetchUrl(url, attempts = 5) {
    return new Promise((resolve, reject) => {
        const tryFetch = (remainingAttempts) => {
            fetch(url)
                .then(response => {
                    if (response.ok) {
                        return response.text();
                    } else {
                        throw new Error('Network response was not ok');
                    }
                })
                .then(resolve)
                .catch(error => {
                    if (remainingAttempts === 1) {
                        reject(error);
                    } else {
                        console.log(`Attempt ${6 - remainingAttempts} failed. Retrying...`);
                        setTimeout(() => tryFetch(remainingAttempts - 1), 1000);
                    }
                });
        };

        tryFetch(attempts);
    });
}

fetchUrl('https://google.com')
    .then(content => {
        console.log(content);
    })
    .catch(error => {
        console.error('Failed to fetch URL:', error);
    });
```
