# HTML


# 行内元素、块元素、行内块元素

## 特点：

- 行内元素：(1)设置宽高无效(2)对margin仅设置左右方向有效，上下无效；padding设置上下左右都有效，即会撑大空间(3)不会自动进行换行【span,a,b,i,br...】
- 块元素：(1)能够识别宽高(2)margin和padding的上下左右均对其有效(3)可以自动换行(4)多个块状元素标签写在一起，默认排列方式为从上至下【html，div，body，h1-h6,p...】
- 行内块元素：(1)不自动换行(2)能够识别宽高(3)默认排列方式为从左到右【img,input,button,select】

## 元素类型转换：
{ dislay:block块元素/inline行内元素/inline-block行内块元素/table-cell单元格/non隐藏e/list-item转成列表即li默认类型 }

# [BFC](https://blog.csdn.net/sinat_36422236/article/details/88763187)

## 概念
(Block formatting context)直译为"块级格式化上下文"。BFC是一个独立的布局环境，其中的元素布局是不受外界的影响，并且在一个BFC中，块盒与行盒（行盒由一行中所有的内联元素所组成）都会垂直的沿着其父元素的边框排列。

## 口述
BFC就是页面上一个隔离的独立容器，内部元素与外部元素互不影响。因此， 当BFC外部存在浮动时，它不应该影响BFC内部Box的布局，BFC会通过变窄，而不与浮动有重叠。同样的，当BFC内部有浮动时，为了不影响外部元素的布局，BFC计算高度时会包括浮动的高度。避免margin重叠也是这样的一个道理。

## BFC的布局规则

- 内部的Box会在垂直方向，一个接一个地放置。
- Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠。
- 每个盒子（块盒与行盒）的margin box的左边，与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。
- BFC的区域不会与float box重叠。
- BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此。
- 计算BFC的高度时，浮动元素也参与计算。

## 如何创建BFC

- float的值不是none。
- position的值不是static或者relative。(absolute,fixed)
- display的值是inline-block、table-cell、flex、table-caption或者inline-flex
- overflow的值不是visible（hidden,scroll,auto）
- body 根元素

## BFC的作用

- 利用BFC避免margin重叠。
- 自适应两栏布局（1.float：left;2.BFC）
- 清除浮动

# H5的新特性：

## 用于绘画 canvas 元素。
[<canvas>](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/canvas) 是 [HTML5](https://developer.mozilla.org/zh-CN/docs/HTML/HTML5) 新增的元素，可用于通过使用[JavaScript](https://developer.mozilla.org/zh-CN/docs/JavaScript)中的脚本来绘制图形。例如，它可以用于绘制图形，制作照片，创建动画，甚至可以进行实时视频处理或渲染。
Demo：
```
<!DOCTYPE html>
<html lang="en">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta http-equiv="X-UA-Compatible" content="ie=edge">
<title>Document</title>
</head>

<body>
<canvas id="canvas"></canvas>
<script>
var canvas = document.getElementById('canvas');
var ctx = canvas.getContext('2d');

ctx.fillStyle = 'green';
ctx.fillRect(10, 10, 100, 100);
</script>
</body>

</html>
```
基本api使用：
(一) 颜色、样式和阴影：
1. [fillStyle](http://www.w3school.com.cn/tags/canvas_fillstyle.asp)：设置或返回用于填充绘画的颜色、渐变或模式
属性值

| color | 指示绘图填充色的 [CSS 颜色值](http://www.w3school.com.cn/css/css_colors_legal.asp)。默认值是 #000000。 |
| --- | --- |
| gradient | 用于填充绘图的渐变对象（[线性](http://www.w3school.com.cn/tags/canvas_createlineargradient.asp)或[放射性](http://www.w3school.com.cn/tags/canvas_createradialgradient.asp)） |
| pattern | 用于填充绘图的 pattern 对象 |

如：
		var c = document.getElementById("myCanvas");
var ctx = c.getContext("2d");
var my_gradient = ctx.createLinearGradient(0, 0, 0, 170);
my_gradient.addColorStop(0, "black");
my_gradient.addColorStop(1, "white");
ctx.fillStyle = my_gradient;
ctx.fillRect(20, 20, 150, 100);

2. strokeStyle 属性设置或返回用于笔触的颜色、渐变或模式。
属性如fillStyle
Demo:
var c = document.getElementById("myCanvas");
var ctx = c.getContext("2d");
ctx.font = "30px Verdana";
// 创建渐变
var gradient = ctx.createLinearGradient(0, 0, c.width, 0);
gradient.addColorStop("0", "magenta");
gradient.addColorStop("0.5", "blue");
gradient.addColorStop("1.0", "red");
// 用渐变进行填充
ctx.strokeStyle = gradient;
ctx.strokeText("Big smile!", 10, 50);
3. shadowColor 属性设置或返回用于阴影的颜色。
 ctx.shadowColor="black";
4. shadowBlur 属性设置或返回阴影的模糊级数。
ctx.shadowBlur=20;
5. shadowOffsetX 属性设置或返回形状与阴影的水平距离。
shadowOffsetX=0 指示阴影位于形状的正下方。
shadowOffsetX=20 指示阴影位于形状 left 位置右侧的 20 像素处。
shadowOffsetX=-20 指示阴影位于形状 left 位置左侧的 20 像素处。
6. shadowOffsetY 属性设置或返回形状与阴影的垂直距离。
shadowOffsetY=0 指示阴影位于形状的正下方。
shadowOffsetY=20 指示阴影位于形状 top 位置下方的 20 像素处。
shadowOffsetY=-20 指示阴影位于形状 top 位置上方的 20 像素处。
7. createLinearGradient() 方法创建线性的渐变对象。
context.createLinearGradient(x0,y0,x1,y1);

| 参数 | 描述 |
| --- | --- |
| x0 | 渐变开始点的 x 坐标 |
| y0 | 渐变开始点的 y 坐标 |
| x1 | 渐变结束点的 x 坐标 |
| y1 | 渐变结束点的 y 坐标 |

8. createPattern() 方法在指定的方向内重复指定的元素。
context.createPattern(image,"repeat|repeat-x|repeat-y|no-repeat");
9. createRadialGradient () 方法创建放射状/圆形渐变对象
context.createRadialGradient(x0,y0,r0,x1,y1,r1);
10. addColorStop() 方法规定 gradient 对象中的颜色和位置。
var grd=ctx.createLinearGradient(0,0,170,0);
grd.addColorStop(0,"black");
(二) 线条样式
1. lineCap 属性设置或返回线条末端线帽的样式。

| 值 | 描述 |
| --- | --- |
| butt | 默认。向线条的每个末端添加平直的边缘。 |
| round | 向线条的每个末端添加圆形线帽。 |
| square | 向线条的每个末端添加正方形线帽。 |

2. lineJoin 属性设置或返回所创建边角的类型，当两条线交汇时。
Bevel: 创建斜角
Round: 创建圆角。
Miter: 默认。创建尖角。
3. lineWidth 属性设置或返回当前线条的宽度，以像素计。

4. miterLimit 属性设置或返回最大斜接长度。
只有当 lineJoin 属性为 "miter" 时，miterLimit 才有效。
边角的角度越小，斜接长度就会越大。
Demo：
		ctx.lineWidth = 10;
ctx.lineJoin = "miter";
ctx.miterLimit = 5;
ctx.moveTo(20, 20);
ctx.lineTo(50, 27);
ctx.lineTo(20, 34);
ctx.stroke();

(三) 矩形
1. rect() 方法创建矩形。
context.rect(x,y,width,height);
2. fillRect() 方法绘制“已填色”的矩形。默认的填充颜色是黑色，[fillStyle](http://www.w3school.com.cn/tags/canvas_fillstyle.asp) 属性来设置用于填充绘图的颜色、渐变或模式。
context.fillRect(x,y,width,height);

3. strokeRect() 方法绘制矩形（不填色）。笔触的默认颜色是黑色。
context.strokeRect(x,y,width,height);

4. clearRect() 方法清空给定矩形内的指定像素。
context.clearRect(x,y,width,height);

(四) 路径
1. fill() 方法填充当前的图像（路径）。默认颜色是黑色。使用 fillStyle 属性来填充另一种颜色/渐变
ctx.rect(20, 20, 150, 100);
ctx.fillStyle = "green";
ctx.fill();
2. stroke() 方法会实际地绘制出通过 moveTo() 和 lineTo() 方法定义的路径。默认颜色是黑色。
3. beginPath() 方法开始一条路径，或重置当前的路径。
var ctx=c.getContext("2d");

ctx.beginPath();
ctx.lineWidth="5";
ctx.strokeStyle="red"; // 红色路径
ctx.moveTo(0,75);
ctx.lineTo(250,75);
ctx.stroke(); // 进行绘制

ctx.beginPath();
ctx.strokeStyle="blue"; // 蓝色路径
ctx.moveTo(50,0);
ctx.lineTo(150,130);
ctx.stroke(); // 进行绘制
4. moveTo开始一条直线的方法
5. closePath() 方法创建从当前点到开始点的路径，无参数

6. lineTo() 方法添加一个新点，然后创建从该点到画布中最后指定点的线条（该方法并不会创建线条）。

7. setLineDash：设置虚线
setLineDash（a,b）:a为实线的长度，b为虚线的长度
8. clip() 方法从原始画布中剪切任意形状和尺寸。
Demo：
// 剪切矩形区域
ctx.rect(50, 20, 200, 120);
ctx.stroke();
ctx.clip();
9. quadraticCurveTo() 方法通过使用表示二次贝塞尔曲线的指定控制点，向当前路径添加一个点。
ctx.beginPath();
ctx.moveTo(20, 20);
ctx.quadraticCurveTo(20, 100, 200, 20);
ctx.stroke();


10. bezierCurveTo() 方法通过使用表示三次贝塞尔曲线的指定控制点，向当前路径添加一个点。
ctx.beginPath();
ctx.moveTo(20, 20);
ctx.bezierCurveTo(20, 100, 200, 100, 200, 20);


11. arc() 方法创建弧/曲线（用于创建圆或部分圆）。
ctx.beginPath();
ctx.arc(100, 75, 50, 0, 2 * Math.PI);
ctx.stroke();

context.arc(x,y,r,sAngle,eAngle,counterclockwise);

| 参数 | 描述 |
| --- | --- |
| x | 圆的中心的 x 坐标。 |
| y | 圆的中心的 y 坐标。 |
| r | 圆的半径。 |
| sAngle | 起始角，以弧度计。（弧的圆形的三点钟位置是 0 度）。 |
| eAngle | 结束角，以弧度计。 |
| counterclockwise | 可选。规定应该逆时针还是顺时针绘图。False = 顺时针，true = 逆时针。 |


12. arcTo() 方法在画布上创建介于两个切线之间的弧/曲线。
Demo：

ctx.beginPath();
ctx.beginPath();
ctx.moveTo(20, 20); // 创建开始点
ctx.lineTo(100, 20); // 创建水平线
ctx.arcTo(150, 20, 150, 70, 50); // 创建弧
ctx.lineTo(150, 120); // 创建垂直线
ctx.stroke();


context.fillRect(x1,y1,x2,y2,r);

| 参数 | 描述 |
| --- | --- |
| x1 | 弧的起点的 x 坐标 |
| y1 | 弧的起点的 y 坐标 |
| x2 | 弧的终点的 x 坐标 |
| y2 | 弧的终点的 y 坐标 |
| r | 弧的半径 |


13. isPointInPath() 方法返回 true，如果指定的点位于当前路径中；否则返回 false。
Demo:
ctx.rect(20, 20, 150, 100);
if (ctx.isPointInPath(20, 50)) {
ctx.stroke();
};

(五) 转换
1. scale() 方法缩放当前绘图，更大或更小。
Demo:
		ctx.strokeRect(5, 5, 25, 15);
ctx.scale(2, 2);
ctx.strokeRect(5, 5, 25, 15);
2. rotate() 方法旋转当前的绘图。旋转角度
Demo:
ctx.rotate(20 * Math.PI / 180);
ctx.fillRect(50, 20, 100, 50);
3. translate() 方法重新映射画布上的 (0,0) 位置。
ctx.translate(70, 70);
ctx.fillRect(10, 10, 100, 50);

(六) 文本
1. font 属性设置或返回画布上文本内容的当前字体属性。
Demo：
ctx.font = "40px Arial";
ctx.fillText("Hello World", 10, 50);
2. textAlign 属性根据锚点，设置或返回文本内容的当前对齐方式。

Demo：
ctx.textAlign = "end";
ctx.fillText("textAlign=end", 150, 80);
3. textBaseline 属性设置或返回在绘制文本时的当前文本基线。

ctx.textBaseline = "top";
ctx.fillText("Top", 5, 100);
4. fillText() 方法在画布上绘制填色的文本。文本的默认颜色是黑色。
ctx.font = "20px Georgia";
ctx.fillText("Hello World!", 10, 50);

5. strokeText() 方法在画布上绘制文本（没有填色）。文本的默认颜色是黑色。
Demo：
ctx.font = "20px Georgia";
ctx.strokeText("Hello World!", 10, 50);

(七) 图像绘制
1. drawImage() 方法在画布上绘制图像、画布或视频。方法也能够绘制图像的某些部分，以及/或者增加或减少图像的尺寸。
context.drawImage(img,sx,sy,swidth,sheight,x,y,width,height);

| 参数 | 描述 |
| --- | --- |
| img | 规定要使用的图像、画布或视频。 |
| sx | 可选。开始剪切的 x 坐标位置。 |
| sy | 可选。开始剪切的 y 坐标位置。 |
| swidth | 可选。被剪切图像的宽度。 |
| sheight | 可选。被剪切图像的高度。 |
| x | 在画布上放置图像的 x 坐标位置。 |
| y | 在画布上放置图像的 y 坐标位置。 |
| width | 可选。要使用的图像的宽度。（伸展或缩小图像） |
| height | 可选。要使用的图像的高度。（伸展或缩小图像） |





Demo1：
let $img = new Image()
$img.src = "/img/databse.jpg";
$img.onload = function() {
ctx.drawImage($img, 0, 0, 300, 300, 0, 0, 300, 300)
}
Demo2：（播放视频）
		let v = document.querySelector("#vedios")
let lasttime
requestAnimationFrame(() => {
if (lasttime && new Date().getTime() - lasttime > 30) {
ctx.drawImage(v, 0, 0, 270, 135);
}

})

(八) 像素操作
1. createImageData() 方法创建新的空白 ImageData 对象。新对象的默认像素值 transparent black。
对于 ImageData 对象中的每个像素，都存在着四方面的信息，即 RGBA 值：
R - 红色 (0-255)
G - 绿色 (0-255)
B - 蓝色 (0-255)
A - alpha 通道 (0-255; 0 是透明的，255 是完全可见的)
因此，transparent black 表示 (0,0,0,0)。
color/alpha 以数组形式存在，并且既然数组包含了每个像素的四条信息，数组的大小是 ImageData 对象的四倍。（获得数组大小有更简单的办法，就是使用 ImageDataObject.data.length）
demo：
var imgData = ctx.createImageData(100, 100);
for (var i = 0; i < imgData.data.length; i += 4) {
imgData.data[i + 0] = 255;
imgData.data[i + 1] = 0;
imgData.data[i + 2] = 0;
imgData.data[i + 3] = 255;
}
ctx.putImageData(imgData, 10, 10);

2. getImageData() 方法返回 ImageData 对象，该对象拷贝了画布指定矩形的像素数据。
对于 ImageData 对象中的每个像素，都存在着四方面的信息，即 RGBA 值：
R - 红色 (0-255)
G - 绿色 (0-255)
B - 蓝色 (0-255)
A - alpha 通道 (0-255; 0 是透明的，255 是完全可见的)
color/alpha 以数组形式存在，并存储于 ImageData 对象的 [data](http://www.w3school.com.cn/tags/canvas_imagedata_data.asp) 属性中。
Demo：
var imgData = ctx.getImageData(10, 10, 50, 50);
ctx.putImageData(imgData, 10, 70);

3. putImageData() 方法将图像数据（从指定的 ImageData 对象）放回画布上。
putImageData() 方法将图像数据（从指定的 ImageData 对象）放回画布上。

| 参数 | 描述 |
| --- | --- |
| imgData | 规定要放回画布的 ImageData 对象。 |
| x | ImageData 对象左上角的 x 坐标，以像素计。 |
| y | ImageData 对象左上角的 y 坐标，以像素计。 |
| dirtyX | 可选。水平值（x），以像素计，在画布上放置图像的位置。 |
| dirtyY | 可选。水平值（y），以像素计，在画布上放置图像的位置。 |
| dirtyWidth | 可选。在画布上绘制图像所使用的宽度。 |
| dirtyHeight | 可选。在画布上绘制图像所使用的高度。 |









4. globalCompositeOperation 属性设置或返回如何将一个源（新的）图像绘制到目标（已有）的图像上。


Demo：
ctx.fillStyle = "red";
ctx.fillRect(20, 20, 75, 50);
ctx.globalCompositeOperation = "source-over";
ctx.fillStyle = "blue";
ctx.fillRect(50, 50, 75, 50);

| 值 | 描述 |
| --- | --- |
| source-over | 默认。在目标图像上显示源图像。 |
| source-atop | 在目标图像顶部显示源图像。源图像位于目标图像之外的部分是不可见的。 |
| source-in | 在目标图像中显示源图像。只有目标图像内的源图像部分会显示，目标图像是透明的。 |
| source-out | 在目标图像之外显示源图像。只会显示目标图像之外源图像部分，目标图像是透明的。 |
| destination-over | 在源图像上方显示目标图像。 |
| destination-atop | 在源图像顶部显示目标图像。源图像之外的目标图像部分不会被显示。 |
| destination-in | 在源图像中显示目标图像。只有源图像内的目标图像部分会被显示，源图像是透明的。 |
| destination-out | 在源图像外显示目标图像。只有源图像外的目标图像部分会被显示，源图像是透明的。 |
| lighter | 显示源图像 + 目标图像。 |
| copy | 显示源图像。忽略目标图像。 |
| xor | 使用异或操作对源图像与目标图像进行组合。 |


(九) canvas常用方法
1. save()：保存当前环境的状态
2. restore()：返回之前保存过的路径状态和属性
一般是save和restore方法相结合着使用；
Demo：
context.save(); //保存第一次的状态
context.rotate(30 / 180 * Math.PI);
context.beginPath();
context.moveTo(0, -180);
context.lineTo(0, -200);
context.stroke();
context.restore(); //进行第二次绘制前，将状态恢复到初始状态

context.rotate(30 / 180 * Math.PI);
context.beginPath();
context.moveTo(0, -140);
context.lineTo(0, -160);
context.stroke();
toDataURL()可以得到以 base64 编码的 dataURL

3. demo：
function getBase64(url) {
//通过构造函数来创建的 img 实例，在赋予 src 值后就会立刻下载图片，相比 createElement() 创建 <img> 省去了 append()，也就避免了文档冗余和污染
var Img = new Image(),
dataURL = '';
Img.src = url;
Img.onload = function() { //要先确保图片完整获取到，这是个异步事件
var canvas = document.createElement("canvas"), //创建canvas元素
width = Img.width, //确保canvas的尺寸和图片一样
height = Img.height;
canvas.width = width;
canvas.height = height;
canvas.getContext("2d").drawImage(Img, 0, 0, width, height); //将图片绘制到canvas中
dataURL = canvas.toDataURL('image/jpeg'); //转换图片为dataURL
};

(十) 弧度制和角度制：
1° = π / 180 ≈ 0.01745 rad
1rad = 180 / π = 57.30°
角度制，就是用角的大小来度量角的大小的方法。在角度制中，把周角的1/360看作1度，那么，半周就是180度，一周就是360度。由于1度的大小不因为圆的大小而改变，所以角度大小是一个与圆的半径无关的量。
弧度制，顾名思义，就是用弧的长度来度量角的大小的方法。单位弧度定义为圆周上长度等于半径的圆弧与圆心构成的角。由于圆弧长短与圆半径之比，不因为圆的大小而改变，所以弧度数也是一个与圆的半径无关的量。角度以弧度给出时，通常不写弧度单位，有时记为rad或R
(十一) 三角函数：


## 用于媒介回放的 video 和 audio 元素。
video元素 定义视频
```
<video src="movie.ogg"controls="controls">Video元素</video>
```
audio元素 定义音频
```
<audio src="someaduio.wav">Audio元素</audio>
```

   - controls属性：如果出现该属性，则向用户显示控件，比如播放按钮。
   - autoplay属性：如果出现该属性，则视频在就绪后马上播放。
   - loop属性：重复播放属性。
   - muted属性：静音属性。
   - poster属性：规定视频正在下载时显示的图像，直到用户点击播放按钮。

## 本地离线存储
本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；sessionStorage 的数据在浏览器关闭后自动删除。

## 语意化标签

### 什么是语义化标签？
标签赋予一定的含义称为语义化。

### 语义化标签有：
header 头部 表示文档中的页眉的标签
footer 尾部 
section 主体内容，文档中的节 
aside 侧边栏 侧导航
article 来自论坛或者博客的独立的文章 强调独立性 配合aside使用 
nav 表示导航
address 地址 默认字体倾斜 定义文档中的作者，联系人，信息的标签
time 时间 //行内
sub 下标 //行内
sup 上标 //行内
button 按钮 //行内块
main 主体（旧H5）（ie不兼容）

### 主体标签：
section、nav、aside、article、time

### 非主体标签：
header、footer、main、address

## 新增表单控件
表单控件，calendar、date、time、email、url、search。

## input新增type：

- type="url" 限制用户必须输入url类型，否则不允许提交 网址
-  email 限制用户必须输入email类型
-  number 数字文本框

 <input name=“number1” type=“number” min=“10” max=“100” step=“5” />

-  min:最小值
-  max:最大值
- **step**:步长值(默认从0开始)
-  search 产生一个搜索意义的表单 多出一个删除X
-  color 产生一个颜色选择的表单
-  date 日期（选取日，月，年）
-  month 月（选取月和年）
-  week 周 （选取周，年）
-  time 时间
-  datetime 日期/时间
-  datetime-local 时间（年月日时间）
-  range 设置0-100之间的范围 可拖动
-  min \max\**step**
- type="tel" 电话 pattern

## 表单控件属性
datalist:选项列表

### 新增的属性
placeholder：
文本框处于未输入状态时文本框中显示的输入提示。聚焦后自动消失
autofocus属性：
给文本框、选择框、或者按钮控件加上该属性，当打开页面时，该控件自动获得国标焦点，一个页面只能有一个。
required属性：
验证输入不能为空
list属性：
结合datalist元素使用

# meta标签
iPhoneX的适配---适配方案viewport-fit
```
<meta name="viewport"content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no">
```
①viewport获取视口宽度
②device-width设备宽度
③initial-scale初始化缩放比例
④minimum-scale最小缩放比例
⑤maximum-scale最大缩放比例
⑥user-scalable=no禁止用户缩放
默认值是yes开启状态



> 原文: <https://www.yuque.com/guxinbo/ps8gra/ggweig>