1) Какие бывают алгоритмы сортировок?
   
`- Сортировка пузырьком (Bubble Sort): Этот алгоритм многократно проходит по списку, сравнивая каждую пару соседних элементов и меняя их местами, если они стоят в неправильном порядке. Сложность: O(n^2).`

`- Сортировка вставками (Insertion Sort): Этот алгоритм поочередно берет каждый элемент из списка и вставляет его в правильную позицию среди ранее отсортированных элементов. Сложность: O(n^2).`

`- Сортировка выбором (Selection Sort): На каждом шаге алгоритм выбирает наименьший (или наибольший) элемент из неотсортированной части списка и ставит его в начало (или конец) отсортированной части. Сложность: O(n^2).`

`- Сортировка слиянием (Merge Sort): Этот алгоритм использует принцип "разделяй и властвуй". Он разбивает список на меньшие списки, сортирует их, а затем объединяет в один отсортированный список. Сложность: O(n log n).`

`- Быстрая сортировка (Quick Sort): Этот алгоритм также использует принцип "разделяй и властвуй", разбивая список на подсписки вокруг опорного элемента и рекурсивно сортируя их. Сложность в среднем: O(n log n), в худшем случае: O(n^2).`

`- Пирамидальная сортировка (Heap Sort): Этот алгоритм строит двоичное дерево (кучу) из элементов списка и последовательно извлекает из него максимальный элемент, что приводит к сортированному списку. Сложность: O(n log n).`

`- Сортировка расческой (Comb Sort): Этот алгоритм является улучшенной версией сортировки пузырьком, который имеет более эффективный шаг сравнения элементов. Сложность: в среднем O(n^2), в лучшем случае O(n log n).`

`- Сортировка Шелла (Shell Sort): Этот алгоритм улучшает сортировку вставками, разделяя список на подсписки и сортируя их, а затем постепенно уменьшая размер этих подсписков. Сложность: в среднем O(n log n), но зависит от выбранного промежутка.`

2) Прочитать про "Операторы и выражения, циклы в JS"
3) Создать объект Person несколькими способами, после создать объект Person2, чтобы в нём были доступны методы объекта Person. Добавить метод logInfo чтоб он был доступен всем объектам.

javascript```
function Person(name, age) {
    this.name = name;
    this.age = age;
}
Person.prototype.sayHello = function() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
};
const person1 = new Person("John", 30);```
javascript```
function Person2(name, age) {
    Person.call(this, name, age);
}
Person2.prototype = Object.create(Person.prototype);
Person2.prototype.constructor = Person2;```
javascript```
Person.prototype.logInfo = function() {
    console.log(`Logging info for ${this.name}`);
};
const person2 = new Person2("Alice", 25);```

4) Создать класс PersonThree c get и set для поля name и конструктором, сделать класс наследник от класса Person.

javascript```
class Person {
    constructor(name) {
        this.name = name;
    }
    get name() {
        return this._name;
    }
    set name(newName) {
        this._name = newName;
    }
}
class PersonThree extends Person {
    constructor(name, age) {
        super(name); // Вызов конструктора родительского класса
        this.age = age;
    }
}
const personThree = new PersonThree("John", 30);```

БОНУС: 
1) Написать функцию, которая вернет массив с первой парой чисел, сумма которых равна total:

`Задание:`
javascript```arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
total = 13;
//result = [4, 9]
const firstSum = (arr, total) => {
      //Решение
}
firstSum(arr,total)```

`Решение:`
javascript```const firstSum = (arr, total) => {
    const seen = new Set();
    for (let num of arr) {
        const complement = total - num;
        if (seen.has(complement)) {
            return [complement, num];
        }
        seen.add(num);
    }
    return [];
};
const arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
const total = 13;
console.log(firstSum(arr, total));```

2) Какая сложность у вашего алгоритма?
`O(n)`
