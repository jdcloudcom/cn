## SDK的使用  

**推流SDK的基本使用流程**  
1、配置推流参数。  
2、创建推流接口。  
3、创建推流预览视图。  
4、开始推流。  
5、推流过程中其他功能设置。  
6、结束推流。    
下面按照步骤分别介绍具体使用方法：  

**1.配置推流参数** 

JDLConfig类配置推流参数，每个属性参数有一个对应的默认值，关于默认值和参数范围，参考API文档或注释。可以根据需求修改对应的属性值。如要在推流过程中实时修改参数，参见JDLConfig类提供的属性和方法。  
使用：  
在在需要使用推流器的 ViewController中引用头文件 #import <jdcloud_live_sdk_ios/JDLive.h>，示例代码如下：   
```
    //初始化默认配置方法  
JDLConfig* config = [JDLConfig defaultConfig];

//**** 以下均有默认有参数，可以不用设置，也可以重新设置 ***//
//采集音视频的来源类型 默认摄像头
config.captureSourceType = JDLCaptureSourceType_Camera;
//采集分辨率 默认720*1280
config.captureResolution = JDLPushResolution720P;
//推流分辨率 默认540*960
config.pushResolution = JDLPushResolution540P;
    //性能模式 默认均衡
config.videoPerformanceMode = JDLVideoPerformanceMode_Balance;
    //视频直播场景 默认自动
config.videoLiveScene = JDLVideoLiveScene_Scene0;
    //帧率 默认15fps
config.fps = 15;
    //最大帧率 默认15fps
config.fpsMin = 15;
    //最小帧率 默认15fps
config.fpsMax = 15;
    //码率, 默认800kbps
config.videoBitrate = 800;
    //最大码率, 默认1200kbps
config.videoBitrateMax = 1200;
    //最小码率, 默认500kbps
config.videoBitrateMin = 500;
    //视频旋转方向 默认竖直
config.videoOrientation = UIInterfaceOrientationPortrait;
    //最大重连次数 默认3次
config.maxReconnectCount = 3;
    //重连时间间隔 默认1秒
config.reconnectInterval = 1.0;
    //摄像头类型 默认前置摄像头
config.cameraType = JDLPushCameraTypeFront;
    //视频编码模式  默认自动
config.videoEncoderMode = JDLPushVideoEncoderMode_AUTO;
    //音频编码模式 默认AAC_LC
config.audioEncoderMode = JDLPushAudioEncoderMode_AAC_LC;
    //音频码率 默认32kbps
config.audioBitrate = 32;
    //音频采样率 默认44100
config.audioSampleRate = 44100;
    //通道 默认单通道
config.audioChannel = JDLPushAudioChannel_1;
    //关键帧间隔 默认3秒
config.keyIntervalTime = 3;
//预览是否镜像 默认NO
config.previewMirror = NO;
    //推流是否镜像 默认NO
config.pushMirror = NO;
    //只有音频 默认NO
config.audioOnly = NO;
    //后台推流开关 默认YES
config.isBackgroundPush = YES;
```
**2.创建推流接口类**

JDLive类，为推流SDK的核心类，提供摄像头预览、推流回调、推流控制、推流过程中的参数调节等功能。  
引入头文件#import <jdcloud_live_sdk_ios/JDLive.h>   
```
@property (nonatomic, strong) JDLive *live;//直播推流接口类。
```  

在配置好推流参数后，可以使用推流SDK的 initWithConfig方法进行初始化。示例代码如下：    
```
self.live = [[JDLive alloc] initWithConfig:config]
```  

**3.创建推流预览视图**    

3.1 初始化    
live对象初始化完成之后，可以进行开始预览操作。预览时需要传入摄像头预览的显示view(继承自UIView)。示例代码如下：  
初始化    
```
@property (nonatomic, strong) UIView *previewView;//预览视图
```
3.2 live接口类加入预览视图    
```
//开始预览
[self.live startPreview:self.previewView]
//停止预览
[self.live stopPreview];
```                                                                                
**4.开始推流**  

4.1 填写推流地址  
    填写推流地址，推流SDK支持RTMP的推流地址。使用正确的推流地址开始推流后，可用播放器（京东云播放器、ffplay、VLC等）进行拉流测试。  
```
[self.live setPushStreamUrl:[NSURL URLWithString:self.pushUrl]];
//开始推流
[self.live startPushStream];
```  
其他推流控制，接口示例代码如下：  

```
//获取SDK版本号
[self.live getSDKVersion];
//获取推流地址
[self.live getPushStreamUrl];
//开始推流
[self.live startPushStream];
//停止推流
[self.live stopPushStream];
//查询当前是否在推流
[self.live isPushStreaming];
//获取推流状态
JDLPushStreamState *state = [self.live getPushStreamState];
```

4.2 注册推流回调
   引入<JDLiveDelegate>	 推流回调代理
```
[self.live setLiveDelegate:self];
```
推流回调有五个，注册delegate可接受对应的回调，代码如下：   

```
//流状态发生改变
(void)onPushStreamStateChange:(JDLPushStreamState)pushStreamState;
//推流错误回调
(void)onPushStreamError:(JDLPushStreamErrorCode)errorCode;
//网络健康状态发生改变
(void)onNetworkStatusChange:(JDLNetworkStateCode)networkStateCode;
//视频录制状态改变
(void)onMediaRecordStateChange:(JDLMediaRecordState)mediaRecordState;
//推流模式改变
(void)onPushStreamModeChange:(JDLPushStreamMode)pushStreamMode; 
```
示例代码如下： 

```
//推流状态通知
- (void)updateUIWithPushStreamState:(JDLPushStreamState)state
{
        switch (state) {
            // 初始化时状态为空闲
            case JDLPushStreamState_Idle：
                  break;
            // 连接中
            case JDLPushStreamState_Connecting:
                  break;
            // 已连接
            case JDLPushStreamState_Connected:
                  break;
            // 断开连接中
            case JDLPushStreamState_Disconnecting:
                   break;
            // 推流出错
            case JDLPushStreamState_Error:
                   break;
            default:
                   break;
    }
}

//视频录制状态改变
- (void)updateUIWithMediaRecordState:(
JDLMediaRecordState)state{
    switch (state) {
           // 初始状态
        case JDLMediaRecordState_Idle:
break;
           //录像失败
        case JDLMediaRecordState_Record_Error:
break;
           // 录像中
        case JDLMediaRecordState_Recording:
break;
           //录像停止
        case JDLMediaRecordState_Record_Stopped:
            break;
        default:
            break;
    }
}

//推流模式改变
- (void)updateUIWithPushStream
{
    //当前模式
    JDLPushStreamMode mode = [self.context.live getPushStreamMode];
    switch (mode) {
            //正常推流
        case JDLPushStreamMode_Normal:
            break;
        //背景图推流
        case JDLPushStreamMode_Audio:
            break;
        //音频推流
        case JDLPushStreamMode_Image_Audio:
            break;
        default:
            break;
    }
}
```

**5.更多接口**    
    在推流过程中，可以进行一下功能的设置，设置接口在JDLive类中有详细备注，详细解释和示例代码如下：  
    
5.1 前后置摄像头切换
默认是使用前置摄像头（可以通过修改 JDLConfig的配置项 cameraType来修改这个默认值），调用一次switchCamera切换一次，注意切换摄像头前必须保证live对象都已经初始化。  
```
if ([self.live isCaptureRunning]){
[self.live switchCamera];
}
```
5.2 闪光灯开关  
只有后置摄像头才可以打开闪光灯（您可以通过JDLConfig里面的cameraType成员来确认当前摄像头是前置还是后置）  
```
if([self.live isFlashLightSupported]){
[self.live toggleFlashLight];
 }else{
NSLog（@” 后置摄像头时，闪光灯可用。”）
  }
```
5.3 美颜和滤镜  
setVideoBeautyWhiteLevel接口可以设置美颜级别，美颜级别0-5级，等级越高，美颜效果约明显。

```
[self.live setVideoBeautyWhiteLevel:level];
```

setVideoFilterEffectIndex接口可以设置不同的滤镜效果，我们目前支持六种不同风格的滤镜，分别为0-5.  

```
[self.live setVideoFilterEffectIndex:level];
```
5.4 是否静音  
在推流过程中，可以进行是否静音推流的设置。  
```
[self.live setAudioStreamMute:YES];
```

5.5 推流过程中截屏  
  在推流过程中，可以进行截屏，必须要保证是在推流过程中，才能截到推流的某一帧。  
```
JDLPushStreamState pushStatus = [self.live getPushStreamState];
if (pushStatus != JDLPushStreamState_Connected) {
NSLog（@"请先开启推流,才能截屏哦~"）
}
else{  //在推流，可以截图
[self.live snapshotFromStreamWithCompletion:^(UIImage* img){ 
if (img) {
//显示在window上
//保存相册
}
}];
}
```

5.6 录制推流中视频  
使用 startMediaRecord接口可以启动本地录制，录制格式为 MP4，通过recordFilePath可以指定 MP4 文件的存放路径。  
```
DLPushStreamState pushStatus = [self.live getPushStreamState];
 if (pushStatus != JDLPushStreamState_Connected) {  //不再推流中，无法开启录制
NSLog[@"请先开启推流,才能录制哦~"];
}
 else{  //在推流，可以录制
               
//录制的状态开始或者结束控制
    JDLMediaRecordState state = [self.live getMediaRecordState];
    if(state != JDLMediaRecordState_Recording){
        NSString * dir = [NSHomeDirectory() stringByAppendingString:@"/Documents/"];
self.recordFilePath = [dir stringByAppendingPathComponent:@"video_record.mp4"];
        [self.live startMediaRecord:[NSURL fileURLWithPath:self.recordFilePath]];
     }
else{
     [self.live stopMediaRecord];
     }
}
```

5.7 纯音频推流  
如果你的直播场景是声音直播，那么需要更新下推流的配置信息。使用以下代码设置纯音频推流并启动推流。纯音频推流可以设置封面。  
```
if([self.live getPushStreamMode] != JDLPushStreamMode_Normal){ //不是正常推流，即已经是纯音频推流
return;
}
//弹出是否设置封面提示
[[[JDActionController alloc]init] showAlertControllerWithTitle:@"纯音频推流" message:@"是否设置封面？" preferredStyle:UIAlertControllerStyleAlert otherButtonTitles:@[@"不设置",@"是"] superViewController:(UIViewController*)self.context actionControllerBlock:^(NSString *buttonTitle) {
if ([buttonTitle isEqualToString:@"是"]){
[SharePhotoManager ShowSheetToSelectedMediaWithInFatherVC:(UIViewController*)self.context FinishPickingMediaBlock:^(UIImage *assetImage, NSURL *assetURL) {
        //有封面推流
[self.live startBGImagePushStream:assetImage];
        }];
}
else if ([buttonTitle isEqualToString:@"不设置"]){
    [self.live startBGImagePushStream:nil];
}
}];

//恢复纯音频推流
[self.live resumeNormalPushStream];
```

5.8 水印  
直播视频可以支持打上水印。水印类型支持图片、文字、时间等设置，图片可进行本地照片上传或直接拍摄，文字、时间可进行字体颜色的设置；支持设置透明度；还支持360度的旋转和拉伸。代码示例如下：
```
//导入#import "WaterMarkEditView.h"
//导入#import "TextWaterMarkEditView.h"
//导入#import "TimestampWaterMarkEditView.h"
//<UIImagePickerControllerDelegate, WaterMarkEditViewDelegate>

//图片类型水印
WaterMarkEditView *waterMarkEditView = [[PictureWaterMarkEditView alloc] initWithFrame:[self getInitPictureEditViewRect]];
waterMarkEditView.delegate = self;
[self.view addSubview:waterMarkEditView];

//文字类型水印
TextWaterMarkEditView *textWaterMarkEditView = [[TextWaterMarkEditView alloc] initWithFrame:[self getInitTextEditViewRect]];
textWaterMarkEditView.delegate = self;
[textWaterMarkEditView setText:@"试试"];
 [textWaterMarkEditView setTextFont:[UIFont systemFontOfSize:14.0]];
 [self.view addSubview:textWaterMarkEditView];

//时间类型水印
TimestampWaterMarkEditView *timestampWaterMarkEditView = [[TimestampWaterMarkEditView alloc] initWithFrame:[self getInitTimeEditViewRect]];
timestampWaterMarkEditView.delegate = self;
[timestampWaterMarkEditView setTextFont:[UIFont systemFontOfSize:14.0]];
    [timestampWaterMarkEditView setTextColor:[UIColor whiteColor]];
    [self.view addSubview:timestampWaterMarkEditView];
```

5.9 叠加UIView  
除了水印，还在流中可以叠加任意的UIView。例如画笔。  
以画笔为例：  
```
@property (nonatomic, assign) int brushLayerId;                       //画笔图层号
@property (nonatomic, strong) BrushView* brushView;                     //画笔推流View


//创建View
self.brushView = [[BrushView alloc] init];
                [self.brushView setBackgroundColor:[UIColor clearColor]];
                [self.brushView setFrame:_context.previewView.frame];
                [self addSubview:self.brushView];
                [self sendSubviewToBack:self.brushView];
 //view加的图层号
                self.brushLayerId = [self.live addUIViewWithView:self.brushView rect:CGRectMake(0, 0, 1, 1) rotation:0 alpha:1 rotationMode:kJDLNoRotation];
```

5.10 音频调用  
在直播时可以设置自己喜欢的音乐加入直播中，可以从iOS的本地媒体库中获取音乐文件。音频调用的接口如下：  
```
//开始播放背景音乐  audioPath 本地音乐文件 
-(void)startBGMusic:(NSString*)audioPath;
//停止播放背景音乐
-(void)stopBGMusicWithComplete:(void (^)(void))completion;
//暂停播放背景音乐
-(void)pauseBGMusic;
//恢复播放背景音乐
-(void)resumeBGMusic;
//设置播放完成回调
- (void)setBGMusicFinishBlock:(void (^)(void))block;
//设置播放状态改变回调
- (void)setBGMusicStateChangeBlock:(void (^)(void))block;
```

使用示例代码如下：  
```
//循环播放
[self.live setBGMusicFinishBlock:^(){
if(self.strMusicUrl && ![ self.strMusicUrl isEqualToString:@""]){
     [self.live startBGMusic:self.strMusicUrl];
   }
}];

//添加背景音乐，url是本地文件路径
if(self.strMusicUrl && ![ self.strMusicUrl isEqualToString:@""]){
    [self.live startBGMusic: self.strMusicUrl];
 }else{
    //停止
 [self.live stopBGMusicWithComplete:^(){
}
```  

5.11 音频升降调  
setAudioEffectCustomFlag在直播过程中自定义音频升降调效果类型，类型为0-7。
```
[self.live setAudioEffectCustomFlag:level];
```

5.12 混音  
推流过程中支持背景混音，支持背景音乐和麦克风的音轨混合，同时可以对其音量进行适当调节。  
```
// track 1背景音乐
[self.live setAudioMixEnable:YES withTrackId:1];
 [self.live setAudioMixVolume:translucentValue withTrackId:1];

// track 0：麦克风
[self.live setAudioMixEnable:YES withTrackId:0];
[self.live setAudioMixVolume:translucentValue withTrackId:0];
```  

5.13 贴纸    
直播视频可以支持打上贴纸。  
5.14 变声  
在直播过程中，可以对声音进行处理。变声类型包括：大叔、萝莉、机器人、庄重等，还可以选择关闭变声。  
```
//设置音频变声效果类型
// type 0关闭（默认）1大叔 2萝莉 3宏大 4机器人
[self.live setAudioEffectType:type];
``` 

5.15 镜像推流  
镜像设置。镜像相关接口有两个，setPushStreamHFlip推流镜像和setPreviewHFlip预览镜像。setPushStreamHFlip设置仅对播放画面生效，setPreviewHFlip仅对预览画面生效，两者互不影响
```
//预览视图镜像
[self.live setPreviewHFlip:isOn];
//推流镜像
[self.live setPushStreamHFlip:isOn];
```

5.16 音频降噪  
在直播过程中，可以对周边噪音进行处理,以保证主播的声音更加清晰。处理的参数范围为： 1-4 ，默认0：关闭降噪。  
```
[self.live setAudioNoiseHandleParam:isOn?3:0];
```

5.17 自动对焦   
手动点击屏幕，会根据手指聚焦的坐标进行自动对焦。   
```
//摄像头自动变焦
[self.live setCaptureFocusPoint:point];
//摄像头自动曝光
[self.live setCaptureExposureAtPoint:point];
```  

5.19 悬浮窗推流   
悬浮窗推流是在不销毁之前推流页面的情况下，改变推流预览的尺寸。悬浮窗加在window上，可以出现在任何ViewController中。  
```
self.isNeedFloatPush = isOn;
if(self.isNeedFloatPush){
 FloatPushStreamView* floatView = [[FloatPushStreamView alloc] initWithContext:self.context];
    [floatView showInWindow];
}
```  

5.19 耳返  
指的是当主播带上耳机来唱歌时，耳机中要能实时反馈主播的声音，这是由于主播自己的声音是通过头部骨骼（固体）传入耳朵，而观众听到声音最终是通过空气介质传入耳朵，这两种方式听的声音是有很大差异的，因此主播有需求直接听到观众端的效果。示例代码如下：
```
if([self.live isHeadsetPlugIn]){
     [self.live setAudioFoldbackEnable:isOn];
}
else{
     NSLog[@"请先插入耳机！"];
}
``` 

5.20 旋转锁定   
在推流过程中，屏幕转动时，不想改变直播视频方向，可以设置屏幕旋转锁定，这样直播推流就只有竖直状态。  
```
self.isOrientationLock = isOn;
//处理屏幕旋转 
 [self.live setVideoPushStreamOrientation:(UIInterfaceOrientation)deviceOrientation]；
```
**6 结束推流**  

```
//停止推流
[self.live stopPushStream];
```
