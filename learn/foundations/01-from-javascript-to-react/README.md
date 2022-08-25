# 从javascript 到react
## 使用js 更新DOM
在刚工作的前几年，不仅仅要写后端代码，还要写js，html，css，jsp等。那个时候写前端js的时候，操作DOM还是很原始的。
就如例子中的这个样子
``` javascript
<html>
  <body>
    <div id="app"></div>

    <script type="text/javascript">
      // Select the div element with 'app' id
      const app = document.getElementById('app');

      // Create a new H1 element
      const header = document.createElement('h1');

      // Create a new text node for the H1 element
      const headerContent = document.createTextNode(
        'Develop. Preview. Ship. 🚀',
      );

      // Append the text to the H1 element
      header.appendChild(headerContent);

      // Place the H1 element inside the div
      app.appendChild(header);
    </script>
  </body>
</html>
```

这种命令式的操作方式确实会让前端代码写的很繁杂。当时的项目幸亏在架构上做了组件和模块的抽象。否则想想针对页面的变化全部操作原生的DOM对象是多么的头疼。
当然了，轻微的操作DOM是很可取的。毕竟是命令式的，只要需求明确，写起来也是挺舒适的。jQuery让操作DOM的代码量小了很多也方便了很多。但是那得有很多的HTML，这些HTML对应的js和css又有很多。

## 使用react
- react is the core React library.
- react-dom provides DOM-specific methods that enable you to use React with the DOM.

``` javascript
<html>
  <body>
    <div id="app"></div>

    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

    <script type="text/jsx">
      const app = document.getElementById('app');
      ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app);
    </script>
  </body>
</html>
```

以上页面的加载与之前的不同在于：
1.  react使用的是jsx，所以需要被compare。所以需要引入babel
2.  `<script>` 标签的type需要改为jsx

## react 核心Concepts
### Component
组件的概念在很早之前就已经接触。大概的意思就是将同类页面封装并提供对应的使用。在16年，我待的第一家公司，公司要做自己的产品。将前端运行在一个外壳（浏览器内核）中。对外提供的EXE安装包，启动程序会加载JSP。
JSP中有会有三个iframe，存放HTML：
- 一个是head，放的是公共信息
  - 银行名称和logo
  - 日期和时间
  - 等等
- 一个是main，放的是APP的run区域
  - 主页面，首页是App列表
  - 点击进入每一个APP
  - APP对应HTML，HTML由组件构成
- 一个是bottom
  - 一个主菜单按钮，类似home按钮
### Props
属性，可以自己定义对应组件的属性来协助完成特定的行为。

### Stats