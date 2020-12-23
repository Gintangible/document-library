## vscode

### 插件推荐

* Auto Close Tag（自动闭合 `HTML/XML` 标签）
* Auto Rename Tag（自动重名名成对的 `HTML` 标签）
* Bracker Pair Colorizer（把成对的括号做颜色区分，并且提供一根连接线。）
* Chinese（VSCode 汉化包）
* CSS Peek（CSS 样式查看器）
* Image preview（鼠标悬浮在链接上可及时预览图片）
* Path Intellisense（自动提示文件路径，支持各种快速引入文件）
* Prettier
* Npm Intellisense（自动完成导入语句中的npm模块）
* Settting Sync
* Vetur
* VSCode-icons（图标主题）
* open in browse（快速打开`html`文件到浏览器预览）
* git lens

### setting.json

```
{
  "window.zoomLevel": 1,
  "editor.wordWrap": "on",
  // 竖线
  "editor.renderIndentGuides": true,、
  // vscode默认启用了根据文件类型自动设置tabsize的选项
  "editor.detectIndentation": false,
  "vetur.format.defaultFormatterOptions": {
    "prettier": {
      // 行尾需要有分号
      "semi": true,
      // 使用单引号
      "singleQuote": true,
      // 大括号内的首尾需要空格
      "bracketSpacing": true,
      // 代码缩进是否用制表符tab
      "useTabs": false,
      // 制表符tab的宽度
      "tabWidth": 4,
      // 末尾逗号
      "trailingComma": "none",
      // 箭头函数，只有一个参数的时候，也需要括号
      "arrowParens": "always",
      "useEditorConfig": false,
      // 对象属性的引号使用
      "quoteProps": "consistent"
    }
  },
  "[vue]": {
    "editor.defaultFormatter": "octref.vetur"
  },
  "editor.renderWhitespace": "all",
  "editor.renderControlCharacters": false,
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "git.path": "/usr/bin/git"
}
```