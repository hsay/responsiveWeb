> 这是为了学习响应式网站创建的一个Demo,该Demo用到的一些技术和思想在平时工作中也很有用，故在这里把用到的一些知识点和自己遇到的坑记录下来。

# 响应式网站
## 项目截图
<img src="img/homeSmall.png" width="40%"/>

## 涉及技术
> 弹性布局、媒体查询、自适应图片、轮播图

## 媒体查询的使用
> 这里有如下测试代码：
```<html>
<head>
<style>
    h1{
        color:red;
    }
    @media only screen and (max-width: 400px) {
    body {
        background-color:red;
    }
}
</style>
</head>
    <body>
        <h1>It works hello!new</h1>
    </body>
</html>
```
> 这里认为这样就可以实现自适应了，当在PC上改变视窗大小确实可以，但是手机就不行了。
> 手机上实现自适应要在头部加上如下代码：
```
<metaname="viewport"content="width=device-width, initial-scale=1.0">
```
> 这里要有一些基本概念的常识
* viewport 是用户网页的可视区域。
* viewport 翻译为中文可以叫做"视区"。
* 手机浏览器是把页面放在一个虚拟的"窗口"（viewport）中，通常这个虚拟的"窗口"（viewport）比屏幕宽，这样就不用把每个网页挤到很小的窗口中（这样会破坏没有针对手机浏览器优化的网页的布局），用户可以通过平移和缩放来看网页的不同部分。
* width：控制 viewport 的大小，可以指定的一个值，如果 600，或者特殊的值，如 device-width 为设备的宽度（单位为缩放为 100% 时的 CSS 的像素）。
* height：和 width 相对应，指定高度。
* initial-scale：初始缩放比例，也即是当页面第一次 load 的时候缩放比例。
* maximum-scale：允许用户缩放到的最大比例。//加上该语句后在手机上就不能进行缩放了
* minimum-scale：允许用户缩放到的最小比例。
* user-scalable：用户是否可以手动缩放
###视口宽度和设备宽度
* width只视口宽度，device-width为设备宽度
####重点理解视口的概念
> 对于桌面浏览器，只有一个视口。
> 但是对于手机浏览器有三个视口概念：
* 布局视口(layout viewport)
* 可视视口(visual viewport)
* 理想视口(ideal viewport)//只有为手机优化后的页面才使用，使用方式就是<metaname="viewport"content="width=device-width, initial-scale=1.0">
如果不指定这句话，布局视口就是厂商的默认值，如980px，如果设置了这句话，布局视口就是理想视口了。
在默认情况下，一般来讲，移动设备上的viewport都是要大于浏览器可视区域的，这是因为考虑到移动设备的分辨率相对于桌面电脑来说都比较小，所以为了能在移动设备上正常显示那些传统的为桌面浏览器设计的网站，移动设备上的浏览器都会把自己默认的viewport设为980px或1024px。

## 自适应图片
> 自适应图片不光是图片显示尺寸的自适应，同时也包括客户端根据自身情况在服务器端加载不同的图片。
自适应图片的两种方式：  使用img标签中的srcset属性，使用picture标签
### srcset实践
```
<img src="img/ad001.png"
    srcset="img/ad001.png 480w, img/ad001-m.png 800w, img/ad001-l.png 1600w "/>
```
```
<img src="img/ad001.png"
        srcset="img/ad001.png 480w, img/ad001-m.png 800w, img/ad001-l.png 1600w">
```
> 这里如果视口大小为<=480px,则会显示img/ad001.png,480-800px显示m,大于800px的显示l.
> 这里的w更多的是规格的意思，用来告知浏览器前面描述的图片的规格，浏览器才会根据当前的显示屏幕(去匹配最合适规格的图片显示)，如img/ad001.png 480w告诉浏览器img/ad001.png该图片的规格是 480w,当目前视口小于480px时规格为480w的图片是最适合显示的，所以加载该图片，而当视口为 500px时，480w规格的图片就不满足要求了，规格为800w的图片最为合适。

那为何又要引入size,其值代表什么?
以上的过程是图片的显示占满整个视口。但是有这样一个问题：
当视口宽度为481px时就显示了宽度为800px的图片(如果是图片占满整行这样还是能够理解的，因为没有空间浪费)。
但是，如果我们将图片显示到视口的一部分时呢?
```
<!DOCTYPE html>
<html>
<head>
    <title></title>
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <style>
        .content{
            width:50%;
            margin:0px auto;
        }
        img{
            display: block;
            width:100%;//图片大小也是
        }
    </style>
</head>
<body>
    <div class="content">
        <img src="img/ad001.png"
        srcset="img/ad001.png 480w, img/ad001-m.png 800w, img/ad001-l.png 1600w">
    </div>
</body>
</html>
```
即图片只会占到视口的一半，当视口宽度为481px时就显示了宽度为800px的图片(即这里选择的条件仍然是整个视口宽度，而不是根据图片的包裹层去判断/因为这里默认的sizes是100vm)，此时800px的显示宽度只有240px；
配合size使用（当size不设置时，默认值是100vm/视口宽度）
如果这里加上
```
srcset="img/ad001.png 480w, img/ad001-m.png 800w, img/ad001-l.png 1600w" sizes = "50vw">
```
那么就会在viewport为960px的时候显示800px的图片，那么此时图片的实际显示尺寸就是480px了，而不是之前的240px。
那么这里sizes中定义的值跟srcset中定义的值有什么关系呢?
sizes中定义的尺寸是图片预估尺寸，即在某种条件下，图片的显示尺寸，有了这个显示尺寸，浏览器就根据当前图片的规格去显示相应的。
比如说这里规格sizes= "50vw"，即不管什么媒体条件下，图片的预估尺寸为50vw，即viewport的一半，当当前viewport的宽度为960px时，显示图片的宽度应为480px，那么根据该条件和srcset中描述的图片规格去下载相应的图片。

当sizes= "100vw"时，当当前viewport宽度为480px时，图片预估宽度为100vw,即480px，(这时不管实际图片的包裹层)，那么浏览器就会选择800px的图片（其实此时图片事件显示的宽度是240px）.
### 实例
```
<!DOCTYPE html>
<html>
<head>
    <title></title>
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <style>
        .content{
            width:100%;
            margin:0px auto;
        }
        img{
            display: block;
            /*width:100%;*/
            max-width: 100%;
        }
    </style>
</head>
<body>
    <!-- <div class="content">
        <img src="img/ad001.png"
        srcset="img/ad001.png 480w, img/ad001-m.png 800w, img/ad001-l.png 1600w"
        sizes="10vm">
    </div> -->
    <div class="content">
        <img src="img/mm-width-128px.jpg"
        srcset="img/mm-width-128px.jpg 128w, img/mm-width-256px.jpg 256w, img/mm-width-512px.jpg 512w"
        sizes="(min-width : 256px) 256px, 100vw">
    </div>
</body>
</html>
```
以上代码主要实现的功能，当viewport宽度大于等于256px时，显示256px的图片，图片实际显示尺寸为256px，其他情况显示图片的实际尺寸为当前viewport的宽度

所选择的图片当viewport的宽度大于256时选择   256px图片，，，小于时选择128px.
图片宽度预估 50vw（sizes="50vw"）

### 总结
srcset描述了一些图片（包括每张图片的地址和规格），浏览器可以根据当前实际情况去选择下载哪张图片。
sizes可以根据媒体查询去设定想要显示图片的尺寸，浏览器根据这个希望和实际的srcset中图片的描述去选择图片。

### picture标签
根据媒体查询给img设置相应的srcset
```
<picture>
    <source media="(max-width:30em)" srcset="1.png 528w"/>
    <source srcset="2.png 228w"/>
    <img src="3.png"  />
</picture>
```
这是根据媒体查询触发的图片选择，也就是说如果加载了较大的图片，viewport缩小时还会重新加载较小的图片，而不像之前的有了大图片就一直显示。
匹配到source之后，该srcset就作为img的属性了。都匹配不上，直接使用img。


