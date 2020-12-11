# css 规范

规范参考[腾讯code规范](http://alloyteam.github.io/CodeGuide/)

**1. 属性声明顺序**

```css
  /* 位置属性 */
  position: relative;
  top: 100px;
  left: 10px;
  z-index: 99;
  display: block;
  float: left;

  /* 大小 */
  width: 100px;
  height: 100px;
  padding: 20px;
  margin: 0;

  /* 文字系列 */
  font-size: 14px;
  line-height: 20px;
  letter-spacing: 0;
  color:#fff;
  text-align: center;

  /* 背景 */
  border: 1px solid #f00;
  border-radius: 5px;
  box-sizing: border-box;
  background: #000;

  /* 其他 */
  transform: translateX(-20px);
  transition: width 2s;
  animation: name duration timing-function delay iteration-count direction;
```

**2. CSS 文件要求**

1. 命名：
   1. 类名使用小写字母，以`-`分隔；
   2. id采用驼峰式命名
   3. scss中的变量、函数、混合、placeholder采用驼峰式命名
2. 缩进：一般4个空格。
3. 分号：每个属性声明末尾都要加分号。
4. 空格：
   1. 需要空格：属性值前，选择器'>', '+', '~'前后，'{'前，`!important` '!'前，属性值中的','后，注释'/\*'后和'\*/'前；
   2. 不需要：属性名后；多个规则的分隔符','前，!important '!'后，属性值中'('后和')'前，行末不要有多余的空格。
5. 空行：
   1. 文件最后保留一个空行；
   2. `}`后最好跟一个空行，包括scss中嵌套的规则；
   3. 属性之间需要适当的空行，具体见属性声明顺序。
6. 注释：注释统一用'/* */'；缩进与下一行代码保持一致；代码行的末尾，与代码间隔一个空格。
7. 引号：使用`""`。

**3. 属性值**

1. 十六进制值应该全部小写，例如，`#fff`。尽量使用**简写**形式的十六进制值，例如，用 `#fff` 代替 `#ffffff`。
2. 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，`.5` 代替 `0.5`；`-.5px` 代替 `-0.5px`）。
3. 避免为 0 值指定单位，例如，用 `margin: 0;` 代替 `margin: 0px;`。