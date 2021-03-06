# GyroscopeImageDemo

利用陀螺仪滑动图片的处理，以及针对陀螺仪图片控件的平滑转场动画。

我写了博客[《陀螺仪图片控件 & 平滑转场动画的相关解析》](https://www.jianshu.com/p/1d3abe34c895)，分享我的想法和思路。

欢迎讨论并提出您的宝贵建议。

## Use GyroscopeImageView just like ImageView


<img src="screenshots/GyroscopeImageView.gif" width="270">


在使用`GyroscopeImageView`控件时，若用 Picasso 加载图片 ，可利用 `GyroscopeTransFormation`， 传入控件的宽高即可合理地对图像尺寸做处理(当然你也可以自己处理图像的加载和图像的大小):
```java
//用 Picasso加载图像 可将控件的宽高传入自定义的 TransFormation 来处理图像大小
Picasso.get()
    .load(picUrl)
    .transform(new GyroscopeTransFormation(width, height))
    .into(gyroscopeImageView);
```

## Register the GyroscopeManager in related Activity

在相关`Activity`的`onResume`和`onPause`中对陀螺仪传感器进行注册和注销监听:
```java
  @Override protected void onResume() {
    super.onResume();
    //利用我们的 GyroscopeManager 来注册传感器监听
    GyroscopeManager.getInstance().register(this);
  }

  @Override protected void onPause() {
    super.onPause();
    //利用我们的 GyroscopeManager 来注销监听
    GyroscopeManager.getInstance().unregister(this);
  }
```

## Smoothly Transfer

<img src="screenshots/SmoothlyTransfer.gif" width="270">


平滑转场:
```java
CoverActivity.startActivityWithAnimation(ImageMoveActivity.this, PIC_URL, gyroscopeImageView);
```

Found this project useful
-------
<p align="center">:heart: Hope this article can help you. Support by clicking the :star:, or share it with people around you. :heart:  </p>


## About me

email : jiangye39@gmail.com

blog  : [jiangye](https://www.jianshu.com/u/6d9e544ead47)