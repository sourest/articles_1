---
title: HTML 5 相关资料整理
author: 我拿青春换口饭
authorURL: http://github.com/dotkiro
---

`HTML5` 是 `HTML` 的最新标准，广义上可包含我们 `<style>` 标签和 `<script>` 标签中的内容；狭义上一般指除 `<style>` 标签和 `<script>` 标签中语法规范外的所有内容。因为浏览器对`<style rel="stylesheet">` 标签和 `<script type="javascript">` 标签进行额外的语法解析。今天主要学习下一般指向的 `HTML5`。

## 常用概念

### 原生标签元素
HTML5
* 新增语义化标签：`<header>`，`<footer>`，`<section>`，`<article>`，`<aside>`，`<nav>`；
* 新增多媒体元素：`<audio>`，`<video>`；
* 新增画布元素：`<canvas>`。

### 属性
HTML5 新增元素属性：
* data-* 定义自定义属性；
* contenteditable 规定是否允许用户编辑内容；
* contextmenu 规定元素的上下文菜单；
* draggable 规定是否允许用户拖动元素；
* hidden 规定元素是否显示；

### 事件
拖放事件
触摸世界
等等

### Web Sockets API
WebSockets 是一种先进的技术。它可以在用户的浏览器和服务器之间打开交互式通信会话。使用此API，您可以向服务器发送消息并接收事件驱动的响应，而无需通过轮询服务器的方式以获得响应。

### Web Storage API
Web Storage 目前两种机制：
* sessionStorage 为每一个给定的源（given origin）维持一个独立的存储区域，该存储区域在页面会话期间可用（即只要浏览器处于打开状态，包括页面重新加载和恢复）。
* localStorage 同样的功能，但是在浏览器关闭，然后重新打开后数据仍然存在。

常用操作：
* Storage.setItem(keyName, keyValue) 增，改
* Storage.removeItem(keyName) 删
* Storage.getItem(keyName) 查
* Storage.clear() 清空

storage 事件：
window.onstorage

### Video and Audio API
我们可以通过  `<video>` 和 `<audio>` 元素来承载音视频内容。音视频相关API大多相同。
* src 指定资源源
* controls 控制视频和音频播放
* autoplay 音频或视频立即开始播放，同时加载页面的其余部分。建议您不要使用。
* loop 视频（或音频）在完成后再次开始播放。建议您不要使用。
* muted 默认情况下关闭声音的情况下播放媒体。
* poster 将图像的URL作为其值，该图像将在播放视频之前显示。它旨在用于启动或广告屏幕。
* preload 此属性用于缓冲大文件。

### Canvas API
Canvas API 通过的 JavaScript 和 HTML `<canvas>` 元素绘制图形。除此之外，它还可用于动画，游戏图形，数据可视化，照片处理和实时视频处理。

### WebGL API

WebGL API 用于在任何兼容的Web浏览器中呈现交互式 3D 和 2D 图形，而无需使用插件。 WebGL 通过引入一个与可以在 HTML5 `<canvas>` 元素中使用的 OpenGL ES 2.0 紧密相符的 API 来实现这一点。

### SVG 支持

SVG 是一种基于 XML 的标记语言，用于描述基于二维的矢量图形。SVG 本质上是描述图形的 HTML 文本。

### Web Workers API
Web Worker 为 Web 内容在后台线程中运行脚本提供了一种简单的方法。线程可以执行任务而不干扰用户界面。此外，他们可以使用 XMLHttpRequest 执行 I/O 。一旦创建， 一个 worker 可以将消息发送到创建它的 JavaScript 代码, 通过将消息发布到该代码指定的事件处理程序（反之亦然）。

### History API
DOM window 对象通过 history 对象提供了对浏览器历史的访问。它暴露了很多有用的方法和属性，允许你在用户浏览历史中向前和向后跳转，同时——从 HTML5 开始——提供了对 history 栈中内容的操作。

### Fullscreen API
Fullscreen API 为使用用户的整个屏幕展现网络内容提供了一种简单的方式。这种 API 让你可以简单地控制浏览器，使得一个元素与其子元素，如果存在的话，可以占据整个屏幕，并在此期间，从屏幕上隐藏所有的浏览器用户界面以及其他应用。

### HTML Drag and Drop API
HTML 拖放接口使应用程序能够在浏览器中使用拖放功能。通过这些功能，用户可以使用鼠标选择可拖动元素，将元素拖动到可放置元素，并通过释放鼠标按钮来放置这些元素。可拖动元素的一个半透明表示在拖动操作期间跟随鼠标指针。

## 其它不常用 API

### IndexedDB API
IndexedDB 用于存储大量结构化数据（包括文件/ blob ）的客户端。此 API 使用索引来启用对此数据的高性能搜索。虽然 Web 存储对于存储较少量的数据很有用，但对于存储大量结构化数据却没那么有用。IndexedDB 提供了一个解决方案。

由于移动端的支持并非良好，此处不再详述。

### Camera API
通过 Camera API 你可以使用手机的摄像头拍照,然后把拍到的照片发送给当前网页。这些操作主要是通过一个 input 元素来实现的，其中该元素的 type 属性必须为 "file" ， accept 属性要允许图片格式，这样才能知道这个文件选择框是用来选择图片的。

### Geolocation API
Geolocation API 允许用户向 Web 应用程序提供他们的位置。出于隐私考虑，报告地理位置前会先请求用户许可。

### 检测设备方向支持
越来越多地，基于 Web 的设备能够确定它们的方向; 也就是说，它们可以报告指示相对于重力拉力的它们的取向的改变的数据。特别地，通过这些数据，像手机等一些手持设备可以实现自动调整旋转角度来保持显示直立，以及当设备旋转到宽屏时（宽度大于高度），自动提供宽屏的网页效果。

### WebRTC API
WebRTC 是一种实时通信技术，它使 Web 应用程序和站点能够捕获和可选地传输音频或视频媒体，以及在浏览器之间交换任意数据而无需中介。包含 WebRTC 的标准集使得可以共享数据并执行对等的电话会议，而无需用户安装插件或任何其他第三方软件。

WebRTC由几个相互关联的API和协议组成，它们协同工作来实现这一目标。您可以在此处找到的文档将帮助您了解WebRTC的基础知识，如何设置和使用数据和媒体连接等。
