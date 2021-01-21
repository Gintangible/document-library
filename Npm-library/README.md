# npm utils

### 1. [es-check](https://www.npmjs.com/package/es-check)

检测对代码含有 es。如：

`es-check es5 './vendor/js/*.js' './dist/**/*.js'`

### 2. js base64 

```javascript
import { Base64 } from 'js-base64';

// 编码
const data = Base64.encode(string);
// 解码
const data = Base64.decode(string);
```

### 3. json-bigint

`js` 的整数有安全范围，如果超过了这个返回可能会精度丢失。

`json-bigint` 可以像 `JSON.parse` 一样方便转换，将超大的数字变成字符串。

```javascript
import JSONbig from 'json-bigint';

jsonParser = JSONbig({
  storeAsString: true,  // 把64位整数存储为字符串
});

// 解析后端数据
const data = jsonParser(res.data);
```

### 4. queryString

`base64` 中有 `+` 时会解析乱码。

### 5. mockjs 

[Mock 文档](https://github.com/nuysoft/Mock/wiki)