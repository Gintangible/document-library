## 深拷贝与浅拷贝的区别

浅拷贝：复制了对象的引用地址，两个对象指向同一个内存地址。修改其中任意的值，另一个都会随之变化。浅拷贝只复制对象的第一层属性。

浅拷贝：第一层数据为基本数据类型时，改变不会使原数据一同改变；原数据包含对象时，改变会是原数据一同改变。

```
function simpleCopy(obj) {
    let objClone = Array.isArray(obj) ? [] : {};
    for (let key in obj) {
        objClone[key] = obj[key];
    }
    return objClone;
}
```

`Object.assign(obj)` 进行的是浅拷贝，拷贝的是对象的属性的引用，而不是对象本身。当 `obj` 只有一层的时候，是深拷贝。

深拷贝：将对象及值复制过来，两个对象修改其中任意的值另一个不会改变。深拷贝可以对对象的属性进行递归复制。

深拷贝：第一层数据为基本数据类型时，改变不会使原数据一同改变；原数据包含对象时，改变不会是原数据一同改变

1.`JSON.parse()` 和 `JSON.stringify()`，但会丢失 `constructor`，`RegExp` 无法实现。适合 `json` 格式的对象，`function` 就不可以了。

```
function deepClone(obj) {
    let _obj = JSON.stringify(obj),
        objClone = JSON.parse(_obj);
    return objClone;
}
```

2.深拷贝方式二

```
function deepClone(target) {
    if (typeof target !== 'object' || target === null || target.constructor === RegExp) {
        return target;
    }

    let cloneTarget = Array.isArray(target) ? [] : {};

    for (const key in target) {
        if(target.hasOwnProperty(key)) {
            cloneTarget[key] = typeof target[key] === 'object' ? deepClone(target[key]) : target[key];
        }
    }

    return cloneTarget;
}
```
