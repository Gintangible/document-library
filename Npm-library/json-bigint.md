# json-bigint 后端数据精度丢失。

`js` 的整数有安全范围，如果超过了这个返回可能会精度丢失。

`json-bigint` 可以像 `JSON.parse` 一样方便转换。

```
import JSONbig from 'json-bigint';

jsonParser = JSONbig({
  storeAsString: true,  // 把64位整数存储为字符串
});

// 解析后端数据
const data = jsonParser(res.data);
```



