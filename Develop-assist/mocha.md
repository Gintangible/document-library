# 测试用例

[mocha 官方文档](https://mochajs.org/)

断言库

- [should.js](https://github.com/shouldjs/should.js)
- [expect.js](https://github.com/LearnBoost/expect.js)
- [chai](http://chaijs.com/)
- [better-assert](https://github.com/visionmedia/better-assert)
- [unexpected](http://unexpected.js.org/)

测试脚本与所要测试的源码脚本同名，但是后缀名为`.test.js`（表示测试）或者`.spec.js`（表示规格）。比如，`add.js`的测试脚本名字就是`add.test.js`。

### 安装 mocha

```bash
yarn add mocha --dev

# 其他依赖
yarn add @babel/core --dev
yarn add @babel/preset-env --dev
yarn add @babel/register --dev
yarn add must --dev
```

```json
"scripts": {
   "test": "mocha --require @babel/register"
}
```

命令中需要添加 `--require @babel/register` ，不然在 `test` 文件中不能使用 es6 语法。

> 示例 **.test.js

```javascript
import expect from 'must';
import add from 'add.js';

describe('add', () => {
  it('测试', () => 
    expect(add(1, 1)).equal(2);
  });
}
```

### 生成报告

`mochawesome` 可以生产一份漂亮的测试报告

```bash
yarn add mochawesome --dev
```

```json
"scripts": {
    "mocha": "node node_modules/mocha/bin/mocha --require @babel/register --reporter mochawesome"
}
```

运行 **mocha** 会在根目录生产 `mochawesome-report` 目录，用浏览器打开 `mochawesome.html` 文件。

### 配置.mocharc.json

```json
{
  // 显示不同断言库特征。
  "diff": true,
  "extension": ["js"],
  // "package": "./package.json",
  // 测试报告的格式
  "reporter": "nyan",
  /* Mocha默认只执行test子目录下面第一层的测试用例，不会执行更下层的用例。
   * test子目录下面所有的测试用例----不管在哪一层----都会执行。
   */
  "recursive": true,
  // 高亮显示超过 75ms 的例子。
  "slow": 75,
  // 测试脚本的转码器
  "require": "@babel/register",
  "timeout": 5000,
  // 指定用户界面
  "ui": "bdd"
  // 监视指定的测试脚本。只要测试脚本有变化，就会自动运行Mocha
  // "watch": true
}
```

### 脚本运行

> 命令

```json
"scripts": {
    "test": "mocha",
    "mocha": "node node_modules/mocha/bin/mocha --require @babel/register --reporter mochawesome"
 }
```

>mocha_awesome.sh

```shell
yarn mocha
# 系统默认浏览器打开百度 start
start ./mochawesome-report/mochawesome.html
```

> mocha_test.sh

```shell
yarn test
```

