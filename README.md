# css 常用笔记记录

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


## 鼠标移动上去图片放大效果

1. 要达到这个效果，需要用 __div__ 标签包裹 __img__ 标签。
2. 要使此效果生效，需要设置父元素的 __width__ 和 __height__ ,并确保将 __overflow__ 设置为 __hidden__
然后，你可以将任何类型的转换动画效果应用于内部图像。
``` html 
    <div class="wrap">
        <img src="https://source.unsplash.com/random/400x400" class="innerWrap">
    </div> 
```
``` css
    .wrap {
      width: 400px;
      height: 400px;
      overflow: hidden;
    }
    .innerWrap {
      transition: all 0.3s;
      cursor: pointer;
    }
    .innerWrap:hover {
      transform: scale(1.1);
    }

```
## css夜间模式

1. 如果你正在寻找一个快速的方法来应用 __夜间模式__ 皮肤到你的网站，可以使用 __invert__ 和 __hue-rotate__ 过滤器。
   > filter: invert() 的范围是从 0 到 1,其中 1 从白色变成为黑色。
     filter: hue-rotate() 改变元素的颜色内容,使它们或多或少保持相同的分离水平，其值范围为 __0deg__ 到 __360deg__。
2. 通过将这些效果组合在 __body__ 标签上，可以快速试用网站夜间模式(注意，为了影响背景，你必须给它一个颜色。)

``` html
    <h1>Hi 小堂</h1>
```
``` css
    *{
        margin: 0;
        padding: 0;
      
      }
      html,body {
          background:rgb(255,255,255);
          height: 100%;
          width: 100%;
          filter: invert(.1);
      }
      h1 {
          width:150px;
          height: 60px;
          line-height: 60px;
          text-align: center;
          position: absolute;
          top: 0;
          bottom: 0;
          left: 0;
          right: 0;
          margin: auto;
          color: #108540;
      }


```
## css3伪标签实现面包屑右侧箭头

1. 利用伪元素 __content__ 属性，还要依赖css3提供的 __first-child__ 和 __last-child__。

``` html
    <div class="wrap">
        <a>Home</a>
        <a>Shop</a>
        <a>T-Shifts</a>
    </div>
```

``` css
      .wrap a:first-child::before {
          content:">>";
      }
      .wrap a::after {
          content: "/";
      } 
      .wrap a:last-child::after {
          content: "";
      } 

```
