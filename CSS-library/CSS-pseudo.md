## 伪类 伪元素

**伪元素**（**::** 表示）：是一个附加至选择器末的关键词，允许你对被选择元素的特定部分修改样式。例如`::before`，`::after`，`::first-letter`等。它是创造出一个并不存在的“元素”内容，并附加样式。
**伪类**（**:** 表示）：没有创造元素内容，只是选中某些状态下的已有元素，并附加样式。比如`:first-child`，`:active`，`:focus`等等。

1. **::first-letter**

   对块级元素第一行的第一个字符设置样式，并且这个字符前面没有其他内容（例如图片或者内联表格），只对块级元素生效。

   ```css
   xx::first-letter {
     float: left;
     padding: 6px 3px;
     margin-right: 6px;
     color: #fff;
     background-color: #000;
     border-radius: 2px;
     box-shadow: 3px 3px 0 red; 
   }
   ```

2. **::first-line**

   用于设置文本或者块级元素的第一行内容的样式。(很多属性在 ::first-line 伪元素里是无效的)

   ```css
   xx::first-line {
     color: #f00;
     text-transform: uppercase;
   }
   ```

3. **::selection**

   设置元素被用户选中高亮后的样式。对该伪元素生效的只有少数样式属性：`color`、`background properties`、`text-shadow`。

   ```css
   xx::selection {
     color: #f00;
     background: #fff;
   }
   ```

4. **::backdrop**

   跟 viewport 大小一致的盒子，当页面处于全屏模式时充当背景。比如利用它设置全屏视频的背景色：

   ```
   video::backdrop {
     background-color: #448;
   }
   ```

5. **::placeholder**

   `<input>`或者`<textarea>`的输入提示性文字，默认是灰色的，可以自定义文字样式。