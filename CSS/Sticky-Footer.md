### 什么是'Sticky Footer'?

`Sticky Footer`:如果页面内容不足够长时，页脚固定在浏览器窗口的底部；如果内容足够长时，页脚固定在页面的最底部。
总而言之，就是页脚一直处于最底，如图：
![test](https://misc.aotu.io/liqinuo/sticky_02.png)


### 实现'Sticky Footer'的几种方式：

**Margin1**

```html
// HTML结构如：
<body>
  <div class="wrapper">

      content

    <div class="push"></div>
  </div>
  <footer class="footer"></footer>
</body>

// CSS
html, body {
  height: 100%;
  margin: 0;
}
.wrapper {
  min-height: 100%;
  margin-bottom: -50px;
}
.footer,
.push {
  height: 50px;
}
```

**Margin2**

```html
// html结构如：
<body>
  <div class="content">
    <div class="content-inside">
      content
    </div>
  </div>
  <footer class="footer"></footer>
</body>

// CSS
html, body {
  height: 100%;
  margin: 0;
}
.content {
  min-height: 100%;
}
.content-inside {
  padding: 20px;
  padding-bottom: 50px;
}
.footer {
  height: 50px;
  margin-top: -50px;
}
```

**Calc**

```html
// html结构如：
<body>
  <div class="content">
    content
  </div>
  <footer class="footer"></footer>
</body>

// CSS
.content {
  min-height: calc(100vh - 70px);
}
.footer {
  height: 50px;
}
```


**Flexbox**

```html
// html结构如：
<body>
  <div class="content">
    content
  </div>
  <footer class="footer"></footer>
</body>

// CSS
html, body {
  height: 100%;
}
body {
  display: flex;
  flex-direction: column;
}
.content {
  flex: 1 0 auto;
}
```


**Grid**

```html
// html结构如：
<body>
  <div class="content">
    content
  </div>
  <footer class="footer"></footer>
</body>

// CSS
html {
  height: 100%;
}
body {
  min-height: 100%;
  display: grid;
  grid-template-rows: 1fr auto;
}
.footer {
  grid-row-start: 2;
  grid-row-end: 3;
}
```

### 参考文献：
[Sticky Footer, Five Ways](https://css-tricks.com/couple-takes-sticky-footer/)
