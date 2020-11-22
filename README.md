# vue-cropper-new

这是效果截图
![Image text](https://github.com/521707/vue-cropper-new/blob/master/00.png?raw=true)

这是使用方法简介

![Image text](https://raw.githubusercontent.com/521707/vue-cropper-new/master/1.png)

<table style="text-align: center">
  <thead>
    <tr>
        <td>名称</td>
        <td>功能</td>
        <td>默认值</td>
        <td>可选值</td>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>img</td>
        <td>裁剪图片的地址</td>
        <td>空</td>
        <td>url 地址 || base64 || blob</td>
    </tr>
    <tr>
        <td>outputSize</td>
        <td>裁剪生成图片的质量</td>
        <td>1</td>
        <td>0.1 - 1</td>
    </tr>
    <tr>
        <td>outputType</td>
        <td>裁剪生成图片的格式</td>
        <td>jpg (jpg 需要传入jpeg)</td>
        <td>jpeg || png || webp</td>
    </tr>
    <tr>
        <td>info</td>
        <td>裁剪框的大小信息</td>
        <td>true</td>
        <td>true || false</td>
    </tr>
    <tr>
        <td>canScale</td>
        <td>图片是否允许滚轮缩放</td>
        <td>true</td>
        <td>true || false</td>
    </tr>
    <tr>
        <td>autoCrop</td>
        <td>是否默认生成截图框</td>
        <td>false</td>
        <td>true || false</td>
    </tr>
    <tr>
        <td>autoCropWidth</td>
        <td>默认生成截图框宽度</td>
        <td>容器的80%</td>
        <td>0~max</td>
    </tr>
    <tr>
        <td>autoCropHeight</td>
        <td>默认生成截图框高度</td>
        <td>容器的80%</td>
        <td>0~max</td>
    </tr>
    <tr>
        <td>fixed</td>
        <td>是否开启截图框宽高固定比例</td>
        <td>true</td>
        <td>true | false</td>
    </tr>
    <tr>
        <td>fixedNumber</td>
        <td>截图框的宽高比例</td>
        <td>[1, 1]</td>
        <td>[宽度, 高度]</td>
    </tr>
    <tr>
        <td>full</td>
        <td>是否输出原图比例的截图</td>
        <td>false</td>
        <td>true | false</td>
    </tr>
    <tr>
        <td>fixedBox</td>
        <td>固定截图框大小 不允许改变</td>
        <td>false</td>
        <td>true | false</td>
    </tr>
    <tr>
        <td>canMove</td>
        <td>上传图片是否可以移动</td>
        <td>true</td>
        <td>true | false</td>
    </tr>
    <tr>
        <td>canMoveBox</td>
        <td>截图框能否拖动</td>
        <td>true</td>
        <td>true | false</td>
    </tr>
    <tr>
        <td>original</td>
        <td>上传图片按照原始比例渲染</td>
        <td>false</td>
        <td>true | false</td>
    </tr>
    <tr>
        <td>centerBox</td>
        <td>截图框是否被限制在图片里面</td>
        <td>false</td>
        <td>true | false</td>
    </tr>
	<tr>
        <td>high</td>
        <td>是否按照设备的dpr 输出等比例图片</td>
        <td>true</td>
        <td>true | false</td>
    </tr>
    <tr>
        <td>infoTrue</td>
        <td>true 为展示真实输出图片宽高  false 展示看到的截图框宽高</td>
        <td>false</td>
        <td>true | false</td>
    </tr>
    <tr>
        <td>maxImgSize</td>
        <td>限制图片最大宽度和高度</td>
        <td>2000</td>
        <td>0-max</td>
    </tr>
    <tr>
        <td>enlarge</td>
        <td>图片根据截图框输出比例倍数</td>
        <td>1</td>
        <td>0-max(建议不要太大不然会卡死的呢)</td>
    </tr>
    <tr>
        <td>mode</td>
        <td>图片默认渲染方式</td>
        <td>contain</td>
        <td>contain , cover, 100px, 100% auto</td>
    </tr>
  </tbody>
</table>

### 内置方法 通过 this.\$refs.cropper 调用

##### this.\$refs.cropper.startCrop() 开始截图

##### this.\$refs.cropper.stopCrop() 停止截图

##### this.\$refs.cropper.clearCrop() 清除截图

##### this.\$refs.cropper.changeScale() 修改图片大小 正数为变大 负数变小

##### this.\$refs.cropper.getImgAxis() 获取图片基于容器的坐标点

##### this.\$refs.cropper.getCropAxis() 获取截图框基于容器的坐标点

##### this.\$refs.cropper.goAutoCrop 自动生成截图框函数

##### this.\$refs.cropper.rotateRight() 向右边旋转 90 度

##### this.\$refs.cropper.rotateLeft() 向左边旋转 90 度

#### 图片加载的回调 imgLoad 返回结果 success, error

#### 获取截图信息

this.\$refs.cropper.cropW 截图框宽度

this.\$refs.cropper.cropH 截图框高度

````js
// 获取截图的base64 数据
this.$refs.cropper.getCropData((data) => {
  // do something
  console.log(data)
})

// 获取截图的blob数据
this.$refs.cropper.getCropBlob((data) => {
  // do something
  console.log(data)
})


### 预览
``` html
@realTime="realTime"
// Real time preview function
realTime(data) {
  var previews = data;
  var h = 0.5;
  var w = 0.2;

  this.previewStyle1 = {
    width: previews.w + "px",
    height: previews.h + "px",
    overflow: "hidden",
    margin: "0",
    zoom: h
  };

  this.previewStyle2 = {
    width: previews.w + "px",
    height: previews.h + "px",
    overflow: "hidden",
    margin: "0",
    zoom: w
  };

  固定为100宽度
  this.previewStyle3 = {
    width: previews.w + "px",
    height: previews.h + "px",
    overflow: "hidden",
    margin: "0",
    zoom: 100 / preview.w
  };

  固定为100高度
  this.previewStyle4 = {
    width: previews.w + "px",
    height: previews.h + "px",
    overflow: "hidden",
    margin: "0",
    zoom: 100 / preview.h
  };
  this.previews = data;
},


<div class="show-preview" :style="{'width': previews.w + 'px', 'height': previews.h + 'px',  'overflow': 'hidden',
    'margin': '5px'}">
  <div :style="previews.div">
    <img :src="option.img" :style="previews.img">
  </div>
</div>
<p>中等大小</p>
<div :style="previewStyle1">
  <div :style="previews.div">
    <img :src="previews.url" :style="previews.img">
  </div>
</div>

<p>迷你大小</p>
<div :style="previewStyle2">
  <div :style="previews.div">
    <img :src="previews.url" :style="previews.img">
  </div>
</div>
=
````

#### 图片移动回调函数 @imgMoving

```
data type
{
   moving: true, // moving 是否在移动
   axis: {
    x1: 1, // 左上角
	 x2: 1，// 右上角
	 y1: 1，// 左下角
	 y2: 1 // 右下角
   }
 }
```

#### 截图框移动回调函数 @cropMoving

```
data type
{
   moving: true, // moving 是否在移动
   axis: {
    x1: 1, // 左上角
	 x2: 1，// 右上角
	 y1: 1，// 左下角
	 y2: 1 // 右下角
   }
 }
```
