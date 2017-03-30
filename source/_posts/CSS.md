---
title: CSS 笔记
date: 2017-02-21 16:59:27
tags:
    - css
categories: css
---
### 属性
1.overflow-scrolling: touch

2.pointer-events: none 设置元素点击穿透

3.transform-origin 设置变换源
<!--more-->
### 多行文本溢出
1.display: -webkit-box 将对象作为弹性伸缩盒子模型显示；

2.-webkit-line-clamp: 2; 私有属性限制行数

3.-webkit-box-orient 设置或检索伸缩盒对象的子元素的排列方式；

4.text-overflow: ellipsis 用省略号“…”隐藏超出范围的文本。

5.**元素设置有padding的时候 会漏出**

```css
display: -webkit-box;
overflow : hidden;
text-overflow: ellipsis;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
```
### -webkit-font-smoothing
Windows系统上-webkit-font-smoothing属性不造成区别。
iOS上，修改-webkit-font-smoothing属性，结果是：
-webkit-font-smoothing: none: 无抗锯齿
-webkit-font-smoothing: antialiased | subpixel-antialiased | default: 灰度平滑
### 单行文本溢出省略号
```css
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
```
### Iconfont 字体图标居中问题
原因：baseline偏上
```text
上边界（ascent）
下边界（descent)
bbox: bounding box
    bbox="0 -212 1026.5 896"  //有问题
    bbox="-0.161291 -128 1707 900" //优化后的
```
解决：在iconfont项目中编辑图标，保存后回自动调整基线

### DPI/PPI
+ DPI（dots per inch）
    - css像素
    - 设备独立像素
+ PPI（pixels per inch）
    - 物理像素
    - 一个屏幕下拥有的物理显示单元的个数
    - 计算：PPI = √ w^2 + h^2 / 对角线长度
    - PPI 120-160 低密度 160-240 中密度 240-320 高密度 320+ 超高密度(Retina)
+ DPR (device pixel ratio)
    - 设备像素比
    - 设备像素比 = 物理像素 / 设备独立像素 // 在某一方向上，x方向或者y方向
    - window.devicePixelRatio获取到当前设备的dpr。
    - -webkit-device-pixel-ratio，-webkit-min-device-pixel-ratio，-webkit-max-device-pixel-ratio进行媒体查询
+ 例：
    - iphone 6 
        + dpi 375\*667
        + dpr = 2
        + ppi = 375\*2/667\*2
    ```css
      dpr = 2
      width: 2px
      height: 2px
      => dpi 2/2
      => ppi 2*2/2*2  //占用16个
    
      dpr = 3 
      width: 2px
      height: 2px
      => dpi 2/2
      => ppi 2*3/2*3   //占用36个
    ```
        
