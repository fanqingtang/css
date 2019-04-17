# css 常用笔记记录

---

## Sticky Footer布局

1. 在最外层 div 设置最小高度为 min-height: 100%,例如 footer 的 height: 60px;，就给最外层 div 里面的第二层 div 设置 padding-bottom: 60px;。然后给 footer 设置 margin-top: -60px;,代码如下。

```html
<div class="wrap">
  <div class="inner-wrap">
    <header>Hi 我是小堂</header>
    <section class="content">
      <p>大家好啊，我是来自江西的小镇青年一枚。还望大家多多指教哦!</p>
    </section>
  </div>
</div>
<footer class="footer">这是我的底部哦</footer>
```

```css
* {
  margin: 0;
  padding: 0;
}
.wrap {
  min-height: 100%;
}
.inner-wrap {
  padding-bottom: 60px;
}
header {
  height: 60px;
  line-height: 60px;
  text-align: center;
  background: #108540;
  color: #fff;
}
section.content {
  text-indent: 30px;
  padding: 10px 0;
  height: 1000px;
  border: 1px solid #ccc;
  background: #fff;
  color: #108540;
}
footer {
  height: 60px;
  line-height: 60px;
  text-align: center;
  margin-top: -60px;
  background: #108540;
  color: #fff;
}
```

2. 用 css3 来实现，使用 Flexbox。主要的做法是在包含页面主要内容的 div 上使用不太知名的 flex-grow 属性，在下面的示例中，我使用的是 main 标签。flex-grow 控制 flex 项目对于其他 flex 元素填充其容器的数量。当值为 0 时，它不会增长，所以我们需要将它设置为 1 或更多。在下面的示例中，我使用了简写属性 flex：auto，它将 flex-grow 默认设置为 1。为了防止任何不必要的行为，我们还可以在 footer 标签中添加 flex-shrink:0。flex-shrink 实际上与 flex-grow 属性相反，控制 flex 元素收缩到适合其容器的大小，将 ta 设置为 0 刚防止 footer 标签收缩，确保它保留其尺寸,代码如下。

```html
<div id="wrap">
  <main>
    <h1>Hi 我是小堂</h1>
    <p>大家好啊，我是来自江西的小镇青年一枚。还望大家多多指教哦!</p>
  </main>
  <footer>
    这是我的底部哦
  </footer>
</div>
```

```css
* {
  margin: 0;
  padding: 0;
}
#wrap {
  height: 100vh;
  display: flex;
  flex-direction: column;
}
main {
  flex: auto;
}
main h1 {
  height: 60px;
  line-height: 60px;
  text-align: center;
  background: #108540;
  color: #fff;
}
main p {
  text-indent: 30px;
  padding: 10px 0;
  background: #fff;
  color: #108540;
}
footer {
  flex-shrink: 0;
  height: 60px;
  line-height: 60px;
  text-align: center;
  margin-top: -60px;
  background: #108540;
  color: #fff;
}
```
