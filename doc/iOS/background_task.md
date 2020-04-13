# iOS的后台保活

iOS可以做到后台保活.

- 短时间保活方式有beginBackgroundTaskWithName;
- App长时间保活方式有: 播放无声音乐,后台持续定位,后台下载资源,BGTaskScheduler等
- 唤醒App的方式: 推送,VoIP等


# App运行状态及状态变化

![iOS13+后台状态](https://user-gold-cdn.xitu.io/2020/1/9/16f8978f99261d5b?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

iOS13+的设备,支持多场景,共有:

- unattached: 多个场景的情况,如果创建的场景不是当前显示的场景,那么场景处于unattached状态;
- Foreground Inactive:应用启动后,显示启动图的过程中;
- Foreground Active:应用启动后,显示出来我们设置的rootViewController之后;
- Foreground Inactive:应用启动后,场景处于显示状态,数据加载完毕,且用户和App没有交互过程中;
- Background:用户点击Home,或者切换App,锁屏后;
- Suspended:进入Background后,应用的代码不执行后,应用进入Suspended状态;(代码是否在运行,可以在应用写定时器,定时输出内容,从Xcode控制台,或者Mac端控制台查看是否有输出内容来判断);

![iOS13-后台状态](https://user-gold-cdn.xitu.io/2020/1/9/16f8978f99008b75?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

低于iOS13的设备,app的运行状态:

- Not Running:用户没有启动App,或者Terminate App后,App处于的状态;
- Foreground Inactive:(同上);
- Foreground Active:(同上);
- Foreground Inactive:(同上);
- Background:(同上);
- Suspended:(同上);


# iOS后台保活方式简介

## 短时间App后台保活
*beginBackgroundTaskWithName*和*endBackgroundTask*

系统低于iOS13的设备,后台运行时间3分钟;
系统高于iOS13的设备,后台运行时间约31秒;


## 播放无声音乐
App进入后台后,播放无声音乐,适用于音视频类App.

## 后台持续定位
对于定位类App,持续定位App,可以实现App
后台保活.

## 后台下载资源
对于要下载资源的App,需要后台下载资源,比如我们在某App下载资源的时候,我们希望切换App时候,或者App退出后台后,资源仍然继续下载,这样我们打开App的时候,资源已经下载好了.

## BackgroundTasks
BackgroundTasks.framework是iOS13新增的framework.

