# Arrays 
# 객체

Objects allow you to store keyed collections of values. That's fine.
객체를 이용하면 key가 있는 값들의 모음을 저장할 수 있습니다.

But quite often we find that we need an *ordered collection*, where we have a 1st, a 2nd, a 3rd element and so on. For example, we need that to store a list of something: users, goods, HTML elements etc. 
하지만 첫 번째, 두 번째, 세 번째 요소 등 요소에 *순서가 있는 모음*이 필요할 때가 꽤 많습니다. 예를 들어 유저, 상품, HTML 요소 등의 목록을 저장하려면 순서가 있는 모음이 필요합니다. 

It is not convenient to use an object here, because it provides no methods to manage the order of elements. We can’t insert a new property “between” the existing ones. Objects are just not meant for such use.
이럴 때 객체를 쓰는 건 불편합니다. 왜냐하면 객체에는 요소의 순서를 조작할 수 있는 메서드가 없기 때문입니다.
이미 존재하는 프로퍼티 "사이"에 새로운 프로퍼티를 삽입할 수는 없습니다. 애초에 객체는 그런 용도가 아닙니다.  

There exists a special data structure named `Array`, to store ordered collections. 
`배열`은 순서가 있는 모음을 저장하기 위한 특별한 자료 구조입니다. 


## Declaration

There are two syntaxes for creating an empty array:
빈 배열을 만드는 방법은 두 가지가 있습니다. 

```js
let arr = new Array();
let arr = [];
```

Almost all the time, the second syntax is used. We can supply initial elements in the brackets:
대부분 두 번째 방법을 사용합니다. 각괄호 안에 요소들을 넣어 선언할 수도 있습니다.

```js
let fruits = ["Apple", "Orange", "Plum"];
```

Array elements are numbered, starting with zero.
배열 요소의 순서는 0부터 시작합니다. 

We can get an element by its number in square brackets:
각괄호 안에 요소의 순서를 넣어 요소의 값을 얻을 수 있습니다. 

```js run
let fruits = ["Apple", "Orange", "Plum"];

alert( fruits[0] ); // Apple
alert( fruits[1] ); // Orange
alert( fruits[2] ); // Plum
```

We can replace an element:
요소를 교체할 수도 있습니다.

```js
fruits[2] = 'Pear'; // now ["Apple", "Orange", "Pear"]
```

...Or add a new one to the array:
또는 배열에 새 요소를 추가할 수도 있습니다.

```js
fruits[3] = 'Lemon'; // now ["Apple", "Orange", "Pear", "Lemon"]
```

The total count of the elements in the array is its `length`:
배열에 들어있는 요소의 총 개수는 요소의 `length`입니다.

```js run
let fruits = ["Apple", "Orange", "Plum"];

alert( fruits.length ); // 3
```

We can also use `alert` to show the whole array.
또한 `alert`를 사용해 전체 배열을 볼 수 있습니다. 

```js run
let fruits = ["Apple", "Orange", "Plum"];

alert( fruits ); // Apple,Orange,Plum
```

An array can store elements of any type.
하나의 배열에 모든 종류의 요소를 저장할 수 있습니다.

For instance:
예를 들면 아래와 같습니다. 

```js run no-beautify
// mix of values
let arr = [ 'Apple', { name: 'John' }, true, function() { alert('hello'); } ];

// get the object at index 1 and then show its name
alert( arr[1].name ); // John

// get the function at index 3 and run it
arr[3](); // hello
```


````smart header="Trailing comma"
An array, just like an object, may end with a comma:
객체와 마찬가지로 배열에서도 마지막 요소 끝에 콤마를 붙여줄 수 있습니다.   
```js 
let fruits = [
  "Apple", 
  "Orange", 
  "Plum"*!*,*/!*
];
```

The "trailing comma" style makes it easier to insert/remove items, because all lines become alike.
트레일링 콤마를 사용하면 모든 라인이 통일성있게 보여 가시성이 좋아집니다. 따라서 요소의 삽입 및 삭제가 편리해집니다.  
````


## 메서드 pop/push, shift/unshift

A [queue](https://en.wikipedia.org/wiki/Queue_(abstract_data_type)) is one of most common uses of an array. In computer science, this means an ordered collection of elements which supports two operations:
[큐](https://en.wikipedia.org/wiki/Queue_(abstract_data_type))는 배열의 가장 흔한 활용 중 하나입니다. 컴퓨터 과학에서 큐는 다음과 같은 두 개의 동작이 가능한, 순서가 있는 요소들의 컬렉션입니다. 

- `push` appends an element to the end.
- `push` 끝에 요소를 추가합니다.
- `shift` get an element from the beginning, advancing the queue, so that the 2nd element becomes the 1st.
- `shift` 맨 앞에 있는 요소를 가져오고, 2번째 요소가 1번째 요소가 되도록 합니다.


![](queue.png)

Arrays support both operations.
배열은 두 가지 동작이 모두 가능합니다.

In practice we meet it very often. For example, a queue of messages that need to be shown on-screen.
연습문제에서 우리는 큐를 자주 보게 될 것입니다. 예를 들어 스크린에 보여져야 할 메세지의 큐 같은 것 말입니다. 

There's another use case for arrays -- the data structure named [stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type)). 
배열의 또다른 활용 예시도 있습니다. [스택](https://en.wikipedia.org/wiki/Stack_(abstract_data_type))이라는 자료구조입니다. 


It supports two operations:
스택은 두 가지 동작이 가능합니다. 

- `push` adds an element to the end.
- `push`는 끝에 요소를 추가합니다. 
- `pop` takes an element from the end.
- `pop`은 끝에서 요소를 꺼내옵니다. 

So new elements are added or taken always from the "end".
즉 새로운 요소들은 항상 "끝"에 추가되며, 기존 요소들은 항상 "끝"에서 꺼내집니다.

A stack is usually illustrated as a pack of cards: new cards are added to the top or taken from the top:
스택은 보통 카드뭉치로 비유됩니다: 새로운 카드들은 위쪽에 올리고, 기존 카드들은 위에서부터 가져옵니다.

![](stack.png)

For stacks, the latest pushed item is received first, that's also called LIFO (Last-In-First-Out) principle. For queues, we have FIFO (First-In-First-Out).
스택에서는 가장 최근에 추가된 요소를 먼저 받습니다. 이는 LIFO (후입선출, Last-In-First-Out)라고도 합니다. 
큐의 경우는 FIFO(선입선출, First-In-First-Out)이라고 합니다. 

Arrays in JavaScript can work both as a queue and as a stack. They allow you to add/remove elements both to/from the beginning or the end. 
자바스크립트의 배열은 스택으로도, 큐로도 작동할 수 있습니다. 가장 처음 혹은 맨 끝에서 요소를 추가/삭제하는 것이 가능하기 때문입니다. 

In computer science the data structure that allows it is called [deque](https://en.wikipedia.org/wiki/Double-ended_queue).
컴퓨터 과학에서 그러한 동작이 가능한 자료구조를 [deque](https://en.wikipedia.org/wiki/Double-ended_queue)라고 합니다. 

**Methods that work with the end of the array:**
**배열의 끝에서 동작하는 메소드들**

`pop`
: Extracts the last element of the array and returns it:
: 배열의 마지막 요소를 추출하여 리턴합니다:

    ```js run
    let fruits = ["Apple", "Orange", "Pear"];

    alert( fruits.pop() ); // remove "Pear" and alert it "Pear"을 삭제하고 alert합니다. 

    alert( fruits ); // Apple, Orange
    ```

`push`
: Append the element to the end of the array:
: 배열의 끝에 요소를 추가합니다:

    ```js run
    let fruits = ["Apple", "Orange"];

    fruits.push("Pear");

    alert( fruits ); // Apple, Orange, Pear
    ```

    The call `fruits.push(...)` is equal to `fruits[fruits.length] = ...`.
    `fruits.push(...)`와 `fruits[fruits.length] = ...`의 결과는 동일합니다.

**Methods that work with the beginning of the array:**
**배열의 시작 부분에서 작동하는 메소드들**

`shift`
: Extracts the first element of the array and returns it:
: 배열의 가장 처음 요소를 빼낸 뒤 리턴합니다:

    ```js
    let fruits = ["Apple", "Orange", "Pear"];

    alert( fruits.shift() ); // Apple을 제거한 뒤 alert합니다 

    alert( fruits ); // Orange, Pear
    ```

`unshift`
: Add the element to the beginning of the array:
: 배열의 시작 부분에 요소를 추가합니다:

    ```js
    let fruits = ["Orange", "Pear"];

    fruits.unshift('Apple');

    alert( fruits ); // Apple, Orange, Pear
    ```

Methods `push` and `unshift` can add multiple elements at once:
`push`와 `unshift` 메소드는 여러 개의 요소를 한번에 더할 수 있습니다:

```js run
let fruits = ["Apple"];

fruits.push("Orange", "Peach");
fruits.unshift("Pineapple", "Lemon");

// ["Pineapple", "Lemon", "Apple", "Orange", "Peach"]
alert( fruits );
```

## Internals
## 인터널

An array is a special kind of object. The square brackets used to access a property `arr[0]` actually come from the object syntax. Numbers are used as keys. 
배열은 특별한 종류의 객체입니다. 요소값에 접근하기 위한 각괄호는 객체 문법에서 유래한 것입니다. 숫자가 key로 사용되지요. 

They extend objects providing special methods to work with ordered collections of data and also the `length` property. But at the core it's still an object.
순서가 있는 데이터 컬렉션을 다루기 위한 특별한 메소드들과 `lenght` 프로퍼티를 사용할 수 있지만, 본질적으로 배열은 객체입니다. 

Remember, there are only 7 basic types in JavaScript. Array is an object and thus behaves like an object. 
자바스크립트에는 7개의 기본 타입이 있다는 것을 기억하세요. 배열은 객체이며 따라서 객체처럼 행동합니다. 

For instance, it is copied by reference:
예를 들어, 배열은 by reference로 복사됩니다:

```js run
let fruits = ["Banana"]

let arr = fruits; // copy by reference (두 변수가 동일한 배열을 참조)

alert( arr === fruits ); // true
 
arr.push("Pear"); // by reference로 배열을 수정

alert( fruits ); // Banana, Pear - 이제 요소가 2개입니다. 
```

...But what makes arrays really  special is their internal representation. The engine tries to store its elements in the contiguous memory area, one after another, just as depicted on the illustrations in this chapter, and there are other optimizations as well, to make arrays work really fast.
...하지만 배열을 정말 특별하게 만드는 것은 인터널 표현입니다.(?)  이 챕터의 그림들에서 배열의 요소들이 순차적으로 나열된 모습으로 묘사되었듯이, 엔진은 배열의 요소들을 메모리 상에 연속적으로 저장하려고 시도합니다. 물론 배열이 매우 빨리 작동하게끔 하는 다른 최적화들도 있습니다.

But they all break if we quit working with an array as with an "ordered collection" and start working with it as if it were a regular object.

For instance, technically we can do this:

```js
let fruits = []; // make an array

fruits[99999] = 5; // assign a property with the index far greater than its length

fruits.age = 25; // create a property with an arbitrary name
```

That's possible, because arrays are objects at their base. We can add any properties to them.

But the engine will see that we're working with the array as with a regular object. Array-specific optimizations are not suited for such cases and will be turned off, their benefits disappear.

The ways to misuse an array:

- Add a non-numeric property like `arr.test = 5`. 
- Make holes, like: add `arr[0]` and then `arr[1000]` (and nothing between them).
- Fill the array in the reverse order, like `arr[1000]`, `arr[999]` and so on.

Please think of arrays as special structures to work with the *ordered data*. They provide special methods for that. Arrays are carefully tuned inside JavaScript engines to work with contiguous ordered data, please use them this way. And if you need arbitrary keys, chances are high that you actually require a regular object `{}`.

## Performance

Methods `push/pop` run fast, while `shift/unshift` are slow.

![](array-speed.png)

Why is it faster to work with the end of an array than with its beginning? Let's see what happens during the execution:

```js
fruits.shift(); // take 1 element from the start
```

It's not enough to take and remove the element with the number `0`. Other elements need to be renumbered as well.

The `shift` operation must do 3 things:

1. Remove the element with the index `0`.
2. Move all elements to the left, renumber them from the index `1` to `0`, from `2` to `1` and so on.
3. Update the `length` property.

![](array-shift.png)

**The more elements in the array, the more time to move them, more in-memory operations.**

The similar thing happens with `unshift`: to add an element to the beginning of the array, we need first to move existing elements to the right, increasing their indexes.

And what's with `push/pop`? They do not need to move anything. To extract an element from the end, the `pop` method cleans the index and shortens `length`.

The actions for the `pop` operation:

```js
fruits.pop(); // take 1 element from the end
```

![](array-pop.png)

**The `pop` method does not need to move anything, because other elements keep their indexes. That's why it's blazingly fast.**

The similar thing with the `push` method.

## Loops

One of the oldest ways to cycle array items is the `for` loop over indexes:

```js run
let arr = ["Apple", "Orange", "Pear"];

*!*
for (let i = 0; i < arr.length; i++) {
*/!*
  alert( arr[i] );
}
```

But for arrays there is another form of loop, `for..of`:

```js run
let fruits = ["Apple", "Orange", "Plum"];

// iterates over array elements
for (let fruit of fruits) {
  alert( fruit ); 
}
```

The `for..of` doesn't give access to the number of the current element, just its value, but in most cases that's enough. And it's shorter.

Technically, because arrays are objects, it is also possible to use `for..in`:

```js run
let arr = ["Apple", "Orange", "Pear"];

*!*
for (let key in arr) {
*/!*
  alert( arr[key] ); // Apple, Orange, Pear
}
```

But that's actually a bad idea. There are potential problems with it:

1. The loop `for..in` iterates over *all properties*, not only the numeric ones.

    There are so-called "array-like" objects in the browser and in other environments, that *look like arrays*. That is, they have `length` and indexes properties, but they may also have other non-numeric properties and methods, which we usually don't need. The `for..in` loop will list them though. So if we need to work with array-like objects, then these "extra" properties can become a problem.

2. The `for..in` loop is optimized for generic objects, not arrays, and thus is 10-100 times slower. Of course, it's still very fast. The speedup may only matter in bottlenecks or seem irrelevant. But still we should be aware of the difference.

Generally, we shouldn't use `for..in` for arrays.


## A word about "length"

The `length` property automatically updates when we modify the array. To be precise, it is actually not the count of values in the array, but the greatest numeric index plus one.

For instance, a single element with a large index gives a big length:

```js run
let fruits = [];
fruits[123] = "Apple";

alert( fruits.length ); // 124
```

Note that we usually don't use arrays like that. 

Another interesting thing about the `length` property is that it's writable.

If we increase it manually, nothing interesting happens. But if we decrease it, the array is truncated. The process is irreversible, here's the example:

```js run
let arr = [1, 2, 3, 4, 5];

arr.length = 2; // truncate to 2 elements
alert( arr ); // [1, 2]

arr.length = 5; // return length back
alert( arr[3] ); // undefined: the values do not return
```

So, the simplest way to clear the array is: `arr.length = 0;`.


## new Array() [#new-array]

There is one more syntax to create an array:

```js
let arr = *!*new Array*/!*("Apple", "Pear", "etc");
```

It's rarely used, because square brackets `[]` are shorter. Also there's a tricky feature with it.

If `new Array` is called with a single argument which is a number, then it creates an array *without items, but with the given length*.

Let's see how one can shoot themself in the foot:

```js run
let arr = new Array(2); // will it create an array of [2] ?

alert( arr[0] ); // undefined! no elements.

alert( arr.length ); // length 2
```

In the code above, `new Array(number)` has all elements `undefined`.

To evade such surprises, we usually use square brackets, unless we really know what we're doing.

## Multidimensional arrays

Arrays can have items that are also arrays. We can use it for multidimensional arrays, to store matrices:

```js run
let matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

alert( matrix[1][1] ); // the central element
```

## toString

Arrays have their own implementation of `toString` method that returns a comma-separated list of elements.

For instance:


```js run
let arr = [1, 2, 3];

alert( arr ); // 1,2,3
alert( String(arr) === '1,2,3' ); // true
```

Also, let's try this:

```js run
alert( [] + 1 ); // "1"
alert( [1] + 1 ); // "11"
alert( [1,2] + 1 ); // "1,21"
```

Arrays do not have `Symbol.toPrimitive`, neither a viable `valueOf`, they implement only `toString` conversion, so here `[]` becomes an empty string, `[1]` becomes `"1"` and `[1,2]` becomes `"1,2"`.

When the binary plus `"+"` operator adds something to a string, it converts it to a string as well, so the next step looks like this:

```js run
alert( "" + 1 ); // "1"
alert( "1" + 1 ); // "11"
alert( "1,2" + 1 ); // "1,21"
```

## Summary

Array is a special kind of object, suited to storing and managing ordered data items.

- The declaration:

    ```js
    // square brackets (usual)
    let arr = [item1, item2...];

    // new Array (exceptionally rare)
    let arr = new Array(item1, item2...);
    ```

    The call to `new Array(number)` creates an array with the given length, but without elements.

- The `length` property is the array length or, to be precise, its last numeric index plus one. It is auto-adjusted by array methods. 
- If we shorten `length` manually, the array is truncated.

We can use an array as a deque with the following operations:

- `push(...items)` adds `items` to the end.
- `pop()` removes the element from the end and returns it.
- `shift()` removes the element from the beginning and returns it.
- `unshift(...items)` adds items to the beginning.

To loop over the elements of the array:
  - `for (let i=0; i<arr.length; i++)` -- works fastest, old-browser-compatible.
  - `for (let item of arr)` -- the modern syntax for items only,
  - `for (let i in arr)` -- never use.

We will return to arrays and study more methods to add, remove, extract elements and sort arrays in the chapter <info:array-methods>.

