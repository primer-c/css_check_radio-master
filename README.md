## README

1. checkbox_svg
2. slider_radio_img

### 1. checkbox_svg

#### 1.1 项目搭建

1. 引入css文件和vue.js文件

2. 该项目引入了vue.js, 需要设置id="app"的容器

  ```html
  <body>
    <div id="app"></div>
    <script>
      const app = new Vue({
        el: "#app",
        data: {}
      })
    </script>
  </body>
  ```

#### 1.2 项目居中对齐

1. 创建类名为container的容器;

2. 设置`#app`高度为一个屏高： `100vh`

3. 设置`#app`布局模式： flex;

4. 设置主轴方向(默认为水平方向)居中对齐： `justify-content: center`;

5. 设置交叉轴方向(默认为垂直方向)居中对齐： `align-items: center`;

- checkbox_svg.less文件

  ```less
  .center {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  #app {
    .center;
    min-height: 100vh;
  }
  ```
#### 1.2 SVG绘图

1. 创建SVG画板

  ```html
  <svg width="400" height="400"></svg>
  ```
2. 在画布上画一个圆：

- 无填充、画笔颜色：`#68e534`、线宽： 20px、圆心： 200px,200px、半径：190px

  ```html
   <circle fill="none"
    stroke="#68e534"
    stroke-width="20"
    cx="200"
    cy="200"
    r="190"
    class="circle"></circle>
  ```

3. 在画布上画一个弯钩：

- 无填充、画笔颜色：`#68e534`、线宽： 24px、三点坐标：`88,214 173,284 304,138`

- 折线两端、接合部呈圆形`round`

  ```html
  <polyline 
    fill="none"
    stroke="#68e534"
    stroke-width="24"
    points="88,214 173,284 304,138"
    stroke-linecap="round"
    stroke-linejoin="round"
    class="tick"></polyline>
  ```

4. 添加项目标题

  ```html
  <h2>Payment Success</h2>
  ```

#### 3. 

1. 设置circle样式

- 设置圆周长：`stroke-dasharray: 1194;`,圆周长= `2x3.14x190`;

- 设置边偏移：`stroke-dashoffset: 0`，试试改变其值： `100/200/500/1194` ,看看圆周变化；

  ```less
  .circle {
    stroke-dasharray: 1194;
    stroke-dashoffset: 0;
    stroke-linecap: round;
  }
  ```

- 该项目的妙点就在初始化时，圆周长为零，圆周不显示，即`stroke-dashoffset: 1194`也设置为1194,使园隐藏；

- 利用`input[type=checkbox]`的`checked`属性,结合动画,使`stroke-dashoffset: 0`也设置为0,使园显示，因此，代码修改为；

  ```less
  .circle {
    stroke-dasharray: 1194;
    stroke-dashoffset: 1194;
    stroke-linecap: round;
  }
  ```

2. 设置polyline样式

- 同上改变`stroke-dashoffset: 0;`值，观察折线变化；

- 同理起始时设置`stroke-dashoffset:350;`，利用动画

  ```less
  .tick {
    stroke-dasharray: 350;
    stroke-dashoffset: 0;
  }
  ```

3. h2动画，初始化时设置h2的透明度0；d动画结束时透明度为1；

4. 注意三个动画的时延： circle动画完成，开始polyline动画，polyline结束动画，h2动画开始；

5. 添加input标签

- 完整代码

  - html: checkbox_svg.html

  - less: checkbox_svg.less

  - css: checkbox_svg.css

### 2. slider_radio_img
