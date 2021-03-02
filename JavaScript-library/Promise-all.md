## Promise all

[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)

Promise.all(iterable) 返回一个 `Promise` 实例，此实例在 `iterable` 参数内所有的 `promise` 都“完成（resolved）”或参数中不包含 `promise` 时回调完成（resolve）；如果参数中 `promise` 有一个失败 `rejected`，此实例回调失败 `reject`，失败原因的是第一个失败 `promise` 的结果。

返回状态：

* 如果传入的参数中的 `promise` 都变成完成状态，`Promise.all` 返回的 `promise` 异步地变为完成。
* 如果传入的参数中，有一个 `promise` 失败，`Promise.all` 异步地将失败的那个结果给失败状态的回调函数，而不管其它 `promise` 是否完成
* 在任何情况下，`Promise.all` 返回的 `promise` 的完成状态的结果都是一个数组。

```
Promise.all = function(promises) {
    return new Promise((resolve, reject) => {
        promises = Array.from(promises);

        if (promises.length === 0) {
            resolve([]);
        } else {
            let result = [];
            let index = 0;

            for (let i = 0; i < promises.length; i++) {
                Promise.resolve(promises[i]).then(data => {
                    result[i] = data;

                    if (++index === promises.length) {
                        resolve[result];
                    } 
                },err => {
                    reject(err);
                    return;
                });
            }
        }
    });
};
```
