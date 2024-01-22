1) Подробно прочитать про метод запроса OPTIONS - и кратко его описать, когда вызывается, где используется, что передает и принимает.
`Метод OPTIONS служит для получения параметров для ресурса или для сервера в целом и при этом сам ресурс ни как не затрагивается (то есть это более дешевая операция по сравнению с HEAD)
Вызывается и используется: клиентом для запроса информации о сервере или ресурсе, а также для предварительной проверки (preflight) перед совершением CORS запросов.
(Пример:
-Запрос:
curl -X OPTIONS http://example.org -i
-Ответ:
HTTP/1.1 200 OK
Allow: OPTIONS, GET, HEAD, POST
Cache-Control: max-age=604800
Date: Thu, 13 Oct 2016 11:45:00 GMT
Expires: Thu, 20 Oct 2016 11:45:00 GMT
Server: EOS (lax004/2813)
x-ec-custom-error: 1
Content-Length: 0)
Передача: Обычно, запрос OPTIONS не содержит тела (body), но может содержать заголовки, которые могут быть использованы для определения поддерживаемых методов и другой информации.
Прием: Сервер отвечает на запрос OPTIONS, предоставляя информацию о поддерживаемых методах, заголовках, разрешенных источниках (в случае CORS) и других параметрах соединения.`

2) Прочитать и описать ключевые особенности "HTTP" Версии 3.0
`HTTP/1
Блокировка соединения (Head-of-Line Blocking): Одновременно может передаваться только один запрос на одном соединении. Ожидание ответа на один запрос блокирует другие запросы.
Время установления соединения: Требует нескольких рукопожатий для установления соединения, что может замедлять начало передачи данных.
Объем обязательных данных: Заголовки передаются в текстовом виде, что занимает много места, и несжатые повторяющиеся части заголовков повторяются для каждого запроса.
HTTP/2
Мультиплексирование: Позволяет передавать несколько запросов и ответов одновременно на одном соединении, устраняя блокировку соединения.
Улучшенное установление соединения: Уменьшено количество рукопожатий для ускорения начала передачи данных.
Сжатие заголовков: Заголовки передаются в бинарном виде и сжимаются, уменьшая объем обязательных данных.
HTTP/3
Протокол QUIC: Использует протокол QUIC вместо TCP для устранения блокировки соединения и улучшения производительности.
Улучшенное установление соединения: Устанавливает соединение с помощью единственного рукопожатия, ускоряя начало передачи данных.
Объем обязательных данных: Заголовки передаются сжатыми и в бинарном виде, что сокращает объем передаваемых данных.
Общий фактор: Все версии направлены на улучшение скорости передачи данных, сокращение времени установления соединения и оптимизацию объема обязательных данных. HTTP/3 с протоколом QUIC призван решить проблемы, которые остались в HTTP/2 на уровне транспортного соединения.`

3) Прочитать про способы отмены запроса, включая объект "AbortController"
`Способы:
-Timeout: Установка таймера (setTimeout) для операции и отмена ее выполнения по истечении определенного времени.
-Promises с использованием флага: Использование флага для отслеживания состояния выполнения операции и отмены ее выполнения по необходимости.
-Использование статуса: Использование переменной для отслеживания статуса выполнения операции и ее отмены при необходимости.
-Использование асинхронных функций и async/await: Возвращение из асинхронной функции промиса, который может быть отменен внешними средствами (например, через AbortController).
Подробнее про AbortController:
AbortController - это интерфейс, предоставляющий простой механизм отмены асинхронных операций, таких как HTTP-запросы. Он обеспечивает удобный способ отслеживания и управления отменой асинхронных операций, что полезно в сценариях работы с сетевыми запросами.
Способ использования:
-Создание экземпляра: const controller = new AbortController();
-Получение объекта сигнала (AbortSignal): const signal = controller.signal;
-Отмена операции: controller.abort();`

5) Написать по 2 примера создания примитивных значений (если есть несколько способов - использовать) (string, number, boolean, null, undefined, symbol, bigInt)
`-string:
-- const string = 'Hello';
-- const string = new String ('Hello');
-- const string = (42).toString();   
-number:
-- const number = 42;
-- const number = new Number (42);
-- const number = parseInt('42', 10);
-boolean:
-- const boolean = true;
-- const boolean = new Boolean (true);
-- const boolean = 5 > 3;
-- const boolean = true && false;   
-null:
-- const null = null;
-undefinded:
-- const undefinded = undefinded;
-symbol:
-- const symbol = Symbol('Hello');
-- const symbol = Symbol.for('Hello');
-- const symbol = Symbol.iterator;
-bigInt:
-- const bigInt = 42n;
-- const bigInt = BigInt(42);`
  
7) Почему, если обратиться к переменным созданным через let, const до их объявления - мы получаем ReferenceError?
`В JS, переменные, объявленные с использованием let и const, подвергаются ]hoisting (поднятие). При поднятии переменные объявляются, но остаются неинициализированными, их значение остается undefined. Но если вы попытаться обратиться к переменной до её объявления, то получите ReferenceError.
Пример:
console.log(myVar); // ReferenceError: myVar is not defined
var myVar = 42;
console.log(myLet); // ReferenceError: Cannot access 'myLet' before initialization
let myLet = 42;
console.log(myConst); // ReferenceError: Cannot access 'myConst' before initialization
const myConst = 42;
В случае с var, переменные поднимаются со значением undefined. Однако, в случае с let и const, они поднимаются, но остаются в "зоне видимости" (temporal dead zone) и не могут быть использованы до фактического объявления.
Это сделано для того, чтобы предотвратить использование переменных, когда их значения еще не определены, что может привести к неочевидным ошибкам в коде`

8) Решить:
javascript```
const res = "B" + "a" + (1 - "hello");
console.log(res); //BaNaN
_____________________________________
const res2 = (true && 3) + "d";
console.log(res2); //3d
_____________________________________
const res3 = Boolean(true && 3) + "d";
console.log(res3); //trued
```
