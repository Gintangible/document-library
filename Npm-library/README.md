# npm utils

## <span id="top">目录</span>

- [检测 es5 es-check](#es_check)
- [base64编码——js base64 ](# js_base64 )
- [大数据丢失精度——json-bigint](#json_bigint)
- [qs](#qs)
- [模拟数据——mock](#mockjs)
- [Vant Cli](#vant_cli)

**[在线测试npm包](https://npm.runkit.com/)**

### 1. <span id="es_check">es-check</span>

[es-check 文档](https://www.npmjs.com/package/es-check)

检测对代码含有 es。如：

`es-check es5 './vendor/js/*.js' './dist/**/*.js'`

### 2. <span id=" js_base64 ">js base64 </span>

```javascript
import { Base64 } from 'js-base64';

// 编码
const data = Base64.encode(string);
// 解码
const data = Base64.decode(string);
```

[▲ 回顶部](#top)

### 3. <span id="json_bigint">json-bigint</span>

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

[▲ 回顶部](#top)

### 4. <span id="qs">qs</span>

解析和格式化 URL 查询字符串的实用工具，功能强于 `query-string`。

[参考文档](https://www.npmjs.com/package/qs)

[▲ 回顶部](#top)

### 5. <span id="mockjs">mockjs </span>

[Mock 文档](https://github.com/nuysoft/Mock/wiki)

[▲ 回顶部](#top)

### <span id="vant_cli">6. Vant Cli</span>

[文档地址](https://github.com/youzan/vant/tree/dev/packages/vant-cli)

基于 `vant` 组件库进行二次开发。

### 7. js-file-download 

文件下载。 移动端下载会有点问题，pc 端ok。