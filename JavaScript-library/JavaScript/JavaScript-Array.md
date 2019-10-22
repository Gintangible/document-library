# Array

常见的数组方法如下，查看[更多数组方法](<https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array>)。

## 一、增删改查

**1. push()**

将一个或多个元素添加到数组的末尾，并返回该数组的新长度。

```javascript
let a = [1,2,3];
a.push(4,5);
console.log(a); // [1,2,3,4,5];
```

**2. unshift()**

此方法是将一个或多个元素添加到数组的开头，并返回新数组的长度。

```javascript
let a = [1,2,3];
a.unshift(4,5);
console.log(a); // [4,5,1,2,3];
console.log(a.length); // 5;
```

**3. splice(start, deleteCount, item1, item2)**

通过删除或替换现有元素或者原地添加新的元素来修改数组,并以数组形式返回被修改的内容。此方法会改变原数组。

* `start`

​		指定修改的开始位置（从0计数）。如果超出了数组的长度，则从数组末尾开始添加内容；如果是负值，则表示从数组末位开始的第几位（从-1计数，这意味着-n是倒数第n个元素并且等价于`array.length-n`）；如果负数的绝对值大于数组的长度，则表示开始位置为第0位。

* `deleteCount` 可选

​		整数，表示要移除的数组元素的个数。

​		如果 `deleteCount` 大于 `start` 之后的元素的总数，则从 `start` 后面的元素都将被删除（含第 `start` 位）。

​		如果 `deleteCount` 被省略了，或者它的值大于等于`array.length - start`(也就是说，如果它大于或者等于`start`之后的所有元素的数量)，那么`start`之后数组的所有元素都会被删除。

如果 `deleteCount` 是 0 或者负数，则不移除元素。这种情况下，至少应添加一个新元素

* `item1, item2, *...*` 可选

​		要添加进数组的元素,从`start` 位置开始。如果不指定，则 `splice()` 将只删除数组元素。

**4. concat()**

合并两个或多个数组。此方法不会更改现有数组，而是返回一个新数组。

```javascript
let array1 = ['a', 'b', 'c'];
let array2 = ['d', 'e', 'f'];

console.log(array1.concat(array2)); // ["a", "b", "c", "d", "e", "f"]
```

**5. pop()**

删除数组中**最后一个**元素，并返回该元素的值。此方法更改数组的长度。

```javascript
let a = [1,2,3];
a.pop();
console.log(a); // [1,2]
a.pop();
console.log(a); // [1]
```

**6. shift()**

删除数组中**第一个**元素，并返回该元素的值。此方法更改数组的长度。

```javascript
let a = [1,2,3];
a.shift();
console.log(a); // [2,3]
a.shift();
console.log(a); // [3]
```

**7. splice()**

见增splice

**8. slice()**

返回一个新的数组对象，这一对象是一个由 `begin` 和 `end` 决定的原数组的**浅拷贝**（包括 `begin`，不包括`end`）。原始数组不会被改变。

```javascript
let a = [1,2,3,4];
let b = a.slice(1,2);
console.log(a); // [1,2,3,4]
console.log(b); // [2]
```

**9. indexOf()/lastIndexOf()**

返回在数组中可以找到一个给定元素的第一个索引，如果不存在，则返回-1。

```javascript
let ls = ['a', 'b', 'c', 'd'];
console.log(ls.indexOf('a')); // 0
console.log(ls.indexOf('e')); // -1
```

## 五、其余方法

**1. sort()**

对数组的元素进行排序，并返回数组。

```javascript
console.log([3,1,4,2].sort((a, b) => a < b)); // [4,3,2,1]
```

**2. reserve()**

将数组中元素的位置颠倒，并返回该数组。该方法会改变原数组。

**3. map()**

创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。

```javascript
console.log([1,2,3].map(item => item * 2)); // [2,4,6]
```

**4. forEach()**

对数组的每个元素执行一次提供的函数。即`for`循环。

**5. filter()**

创建一个新数组, 其包含通过所提供函数实现的测试的所有元素。 

```javascript
console.log([1,2,3].filter(item => item > 2)); // 3
```

**6. every()**

测试一个数组内的所有元素是否都能通过某个指定函数的测试。它返回一个布尔值。

```javascript
console.log([1,2,3,4].every(item => item < 10)); // true
console.log([1,2,3,4].every(item => item > 2)); // false
```

**7. some()**

测试是否至少有一个元素可以通过被提供的函数方法。该方法返回一个Boolean类型的值。

```javascript
console.log([1,2,3,4].every(item => item < 2)); // true
console.log([1,2,3,4].every(item => item > 0)); // false
```

**8. join()**

将一个数组（或一个[类数组对象](https://developer.mozilla.org/zh-CN//docs/Web/JavaScript/Guide/Indexed_collections#Working_with_array-like_objects)）的所有元素连接成一个字符串并返回这个字符串。如果数组只有一个项目，那么将返回该项目而不使用分隔符。

```javascript
console.log([1,2,3].join('a')); // 1a2a3
```

**9. reduce()**

对数组中的每个元素执行一个由您提供的**reducer**函数(升序执行)，将其结果汇总为单个返回值。

>  arr.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])

* accumulator (acc) (累计器)
* currentValue (cur) (当前值)
* index (idx) (当前索引)
* initialValue (src) (源数组)

```javascript
console.log([1,2,3,4,5].reduce((a,b,c,d) => a + b)); // 15

console.log([1,2,3,4,5].reduce((a,b,c,d) => a + 1)); // 5
```



## 六、ES6 新增

**1. includes()**

判断一个数组是否包含一个指定的值，根据情况，如果包含则返回 true，否则返回false。

**注意：对象数组不能使用includes方法来检测。**

```javascript
let pets = ['cat', 'dog', 'bat'];

console.log(pets.includes('cat')); // true

console.log(pets.includes('at')); // false

```

**2. from()**

从一个类似数组或可迭代对象中创建一个新的，浅拷贝的数组实例。

[MDN](<https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/from>)

> ```javascript
> arrayLike[, mapFn[, thisArg]]
> ```

* arrayLike

​		想要转换成数组的伪数组对象或可迭代对象。

* mapFn (可选参数)

​		如果指定了该参数，新数组中的每个元素会执行该回调函数。

* thisArg (可选参数)

​		可选参数，执行回调函数 `mapFn` 时 `this` 对象。





