## Baidu Cloud Player Android SDK

百度智能云播放器 Android SDK(以下简称“SDK”）是百度智能云推出的 Android 平台视频播放器软件开发工具包 (SDK)，为 Android 开发者提供简单、便捷的开发接口，帮助开发者在 Android 移动设备上实现媒体播放功能。SDK 提供简单、便捷的媒体应用开发能力。

在标准版SDK之外，还提供了高级版SDK，包含有全景声（WANOS）音频格式解码与音效处理、HDR多标准视频解码与渲染、超低延时直播、VR视频播放、智能防挡弹幕、投屏、绿幕抠图等高级功能，为用户带来更丰富的音视频体验。


| 终端类别 | Demo体验 | 下载地址 | API参考 | 帮助文档 |
| --- | --- | --- | --- | --- |
| Android端 | ![JZYK.png](https://bce.bdstatic.com/doc/bce-doc/MCT/JZYK_733369a.png) |[SDK + Demo](https://cloud.baidu.com/doc/Developer/index.html)  |  [接口速查](https://cloud.baidu.com/doc/VideoCreatingSDK/s/Eldy8a0wc)  |[播放器Android SDK](https://cloud.baidu.com/doc/VideoCreatingSDK/s/Wldy8749w) |

<br>

详细的集成方式和接口文档参考百度智能云官网[文档](https://cloud.baidu.com/doc/VideoCreatingSDK/s/Wldy8749w)。

gradle集成：
```
buildscript {
    repositories {
        mavenCentral()
    }
}

allprojects {
    repositories {
        mavenCentral()
    }
}

defaultConfig {
    packagingOptions {
        pickFirst 'lib/armeabi-v7a/*.so'
        pickFirst 'lib/arm64-v8a/*.so'
    }
}

dependencies {
    // 按需在以下四个版本的baiduPlayerSDK中选择一个即可
    // 流媒体标准版
    implementation "com.baidubce.mediasdk:baiduPlayerSDK:3.8.0"
    // 全媒体标准版
    // implementation "com.baidubce.mediasdk:baiduPlayerSDK-full:3.8.0"
    // 流媒体高级版
    // implementation "com.baidubce.mediasdk:baiduPlayerSDK-advance:3.8.0"
    // 全媒体高级版
    // implementation "com.baidubce.mediasdk:baiduPlayerSDK-full-advance:3.8.0"
    
    implementation "com.baidubce.mediasdk:playerlicense:3.8.0"
    implementation "com.baidubce.mediasdk:videocache:3.8.0"
    implementation "com.baidubce.mediasdk:danmaku-wrapper:1.0.0"
    // 以下组件为高级版特有
    // HDR组件
    implementation "com.baidubce.mediasdk:hdrkit:1.0.1"
    // 超低延时组件
    implementation "com.baidubce.mediasdk:rtcplayer-wrapper:1.0.24"
    // 投屏组件
    implementation "com.baidubce.mediasdk:projection-wrapper:1.0.5"
    // VR组件
    implementation "com.baidubce.mediasdk:vrkit:1.0.0"
    // 绿幕抠像组件
    implementation "com.baidubce.mediasdk:virtualLiveKit:1.0.0"
}
```

开发者可以按需选择。

### Android高级版SDK功能简介

#### 全景声（WANOS）音频格式解码与音效处理

全景声（WANOS）是我国完全自主知识产权的音频编码技术，结合多声道和多声音对象编码，可以提供沉浸式的全景听觉体验。在高级版SDK中，我们提供了全景声（WANOS）音频格式的解码播放能力。

不仅如此，我们还基于全景声（WANOS）空间音效处理算法，针对包括扬声器和耳机在内的不同输出设备，提供了原声模式、电影模式、音乐模式、全景环绕模式等音效处理和切换能力，为用户带来更多样的音频玩法。

[百度智能云音视频处理（MCP）](https://cloud.baidu.com/product/mct.html)同时支持全景声（WANOS）音频内容的生产，为用户提供完整的端到端全景声解决方案。

- [Android端全景声功能接入](https://cloud.baidu.com/doc/VideoCreatingSDK/s/Zldy8fl3m)


#### HDR多标准视频解码与渲染
HDR视频具有高动态范围、宽色域、高位深的特点，可以呈现更细腻真实的视觉体验。在高级版SDK中，我们不仅提供了HDR10和HLG标准的支持，还支持了我国自主知识产权的HDR Vivid标准，其具备动态元数据、色调映射和饱和度调节能力。

除此之外，我们还通过高性能的后处理算法，让HDR视频在不支持HDR显示的低端机型上也能呈现出正确的色彩，让更多用户感受到HDR画面带来的震撼影像体验。

[百度智能云音视频处理（MCP）](https://cloud.baidu.com/product/mct.html)同时支持HDR视频内容的生产，为用户提供完整的端到端HDR解决方案。

- [Android端HDR功能接入](https://cloud.baidu.com/doc/VideoCreatingSDK/s/1ldy8hxoy)


#### 超低延时直播
百度智能云超低延时直播利用百度RTC技术，实现端到端延迟低于1s的直播观看体验，适用于电商直播、秀场直播等对实时互动性有要求的业务场景。

在高级版SDK中，我们不仅提供了超低延时直播的播放端支持，还利用UDP信令方案进一步优化首屏时间，同时支持H264/HEVC视频编码和AAC音频编码，还提供了对B帧的支持。

[百度智能云音视频直播（LSS）](https://cloud.baidu.com/product/lss.html)支持超低延时直播的推流、分发，如您有接入需求，请提交工单或联系您的客户经理。

- [Android端超低延时直播功能接入](https://cloud.baidu.com/doc/VideoCreatingSDK/s/jldy8jn9x)


#### VR视频播放
在高级版SDK中，提供了VR全景视频的高性能渲染能力，支持点播、直播流，同时支持基于陀螺仪的视角控制。

- [Android端VR功能接入](https://cloud.baidu.com/doc/VideoCreatingSDK/s/Klfbz7ib9)


#### 智能防挡弹幕
利用[百度智能云音视频处理（MCP)](https://cloud.baidu.com/product/mct.html)对视频中的人体、人脸等重要信息进行预先分析并生成蒙版，可以在高级版SDK中实现防挡弹幕效果，保留弹幕互动性的同时不遮挡画面重要内容，提升用户体验。

#### 投屏
在高级版SDK中，提供了DLNA投屏能力，允许用户将手机端的多媒体内容投送到盒子、投影、电视等大屏设备上，并且可以在手机端控制大屏端的媒体播放。


- [Android端投屏功能接入](https://cloud.baidu.com/doc/VideoCreatingSDK/s/Jlfbyvd7c)


### 绿幕抠图
在高级版SDK中，提供了高精度、高性能的绿幕抠图能力，可实现对绿色或其他纯色背景的自动识别和抠像，背景可以实时替换为2D视频画面或虚拟3D场景，适用于电商直播、虚拟主播、元宇宙直播等场景。绿幕抠图功能可以配合播放内核使用，也支持作为独立组件单独使用。

- [Android端绿幕抠图功能接入](https://cloud.baidu.com/doc/VideoCreatingSDK/s/Rliij6p24)
