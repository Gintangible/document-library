## vscode

### 插件推荐

* Auto Close Tag
* Auto Rename Tag
* Chinese
* Path Intellisense
* Prettier
* Npm Intellisense
* Settting Sync
* Vetur
* VSCode-icons
* open in browse
* git lens

### setting.json

```
{
  "window.zoomLevel": 1,
  "editor.wordWrap": "on",
  // 竖线
  "editor.renderIndentGuides": true,
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