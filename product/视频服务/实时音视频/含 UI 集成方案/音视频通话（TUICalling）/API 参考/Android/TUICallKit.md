## TUICallKit API 简介

TUICallKit API 是音视频通话组件的**含 UI 接口**，使用TUICallKit API，您可以通过简单接口快速实现一个类微信的音视频通话场景，更详细的接入步骤，详见：[快速接入TUICallKit（）]()

<h2 id="TUICallKit">API 概览</h2>


| API | 描述 |
|-----|-----|
| [createInstance](#sharedinstance) | 创建 TUICallKit 实例（单例模式）|
| [setSelfInfo](#setSelfInfo) | 设置用户的昵称、头像|
| [call](#call) | 发起 1v1 通话|
| [groupCall](#groupCall) | 发起群组通话|
| [joinInGroupCall](#joinInGroupCall) | 主动加入当前的群组通话中 |
| [setCallingBell](#setCallingBell) | 设置自定义来电铃音 |
| [enableMuteMode](#enableMuteMode) | 开启/关闭静音模式 |
| [enableFloatWindow](#enableFloatWindow) | 开启/关闭悬浮窗功能 |

<h2 id="TUICallKit">API 详情</h2>

### createInstance
创建 TUICallKit 的单例。
```java
TUICallKit createInstance(Context context)
```

### setSelfInfo
设置用户昵称、头像。用户昵称不能超过500字节，用户头像必须是URL格式。
```java
void setSelfInfo(String nickname, String avatar, TUICommonDefine.Callback callback)
```
| 参数 | 类型 | 含义 |
|-----|-----|-----|
| nickname | String | 目标用户的昵称 |
| avatar | String | 目标用户的头像 | 

### call
拨打电话（1v1通话）

```java
 void call(String userId, TUICallDefine.MediaType callMediaType)
```

参数如下表所示：

| 参数 | 类型 | 含义 |
|-----|-----|-----|
| userId | String | 目标用户的userId |
| callMediaType | TUICallDefine.MediaType  | 通话的媒体类型，比如视频通话、语音通话 |

### groupCall
发起群组通话，注意：使用群组通话前需要创建IM 群组，如果已经创建，请忽略；

```java
void groupCall(String groupId, List<String> userIdList, TUICallDefine.MediaType callMediaType) {
```

| 参数 | 类型 | 含义 |
|-----|-----|-----|
| groupId | String | 此次群组通话的群 Id. |
| userIdList | List | 目标用户的userId 列表 |
| callMediaType | TUICallDefine.MediaType | 通话的媒体类型，比如视频通话、语音通话 |

### joinInGroupCall
发起群组通话，注意：使用群组通话前需要创建IM 群组，如果已经创建，请忽略；

```java
void joinInGroupCall(TUICommonDefine.RoomId roomId, String groupId, TUICallDefine.MediaType callMediaType, TUICommonDefine.Callback callback);
```

| 参数 | 类型 | 含义 |
|-----|-----|-----|
| roomId | TUICommonDefine.RoomId | 此次通话的音视频房间 Id，目前仅支持数字房间号，后续版本会支持字符串房间号 |
| groupId | String | 此次群组通话的群 Id |
| callMediaType | TUICallDefine.MediaType | 通话的媒体类型，比如视频通话、语音通话 |


### setCallingBell
设置自定义来电铃音

这里仅限传入本地文件地址，需要确保该文件目录是应用可以访问的。

铃声设置后与设备绑定，更换用户，铃声依旧会生效。
如需恢复默认铃声，`filePath`传空即可。

```java
void setCallingBell(String filePath);
```

### enableMuteMode
开启/关闭静音模式

```java
void enableMuteMode(boolean enable);
```

### enableFloatWindow
开启/关闭悬浮窗功能

默认为`false`，通话界面左上角的悬浮窗按钮隐藏，设置为`true`后显示。

```java
void enableFloatWindow(boolean enable);
```

