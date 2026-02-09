---
AIGC:
    ContentProducer: Minimax Agent AI
    ContentPropagator: Minimax Agent AI
    Label: AIGC
    ProduceID: "00000000000000000000000000000000"
    PropagateID: "00000000000000000000000000000000"
    ReservedCode1: 3045022100ec8277024927c94656c011bbe0cc659a56f6cac4938c4c4b77bae368e4cf14f8022015726edc7af506b267fbbe68b570133a29fa7cb0afc3f7ce78cbbb05f2be6aee
    ReservedCode2: 3045022071e5bd2cc061131e779d32d9bfe2c9b7f71e973ba1cd3992118e37cad6d46cda022100d885d434cdb054966aa298d7aac6936e43f35df552521ff306c586eaf3b17dd7
---

# Flutter核心服务框架

一个完整的Flutter核心服务框架，提供了移动应用开发中常用的核心服务组件，包括权限管理、悬浮窗控制、屏幕截取、音频录制、网络请求和本地存储等功能。

## 📋 目录结构

```
/workspace/lib/services/
├── service_manager.dart           # 服务管理器 - 统一管理所有后台服务
├── permission_manager.dart        # 权限管理器 - 封装Android权限相关操作
├── floating_window_controller.dart # 悬浮窗控制器 - 控制小窗显示和交互
├── screen_capture_service.dart    # 屏幕截取服务 - 实现屏幕内容获取
├── audio_recording_service.dart   # 音频录制服务 - 实现语音录制和预处理
├── network_service.dart          # 网络请求封装 - HTTP客户端和AI API调用封装
├── storage_service.dart          # 本地存储服务 - 配置信息和缓存管理
└── services_example.dart          # 使用示例和演示应用
```

## 🚀 核心服务

### 1. 服务管理器 (ServiceManager)
- **功能**: 统一管理所有后台服务的生命周期和状态
- **特性**:
  - 服务初始化和启动/停止
  - 服务状态监听和健康检查
  - 服务依赖管理
  - 统一错误处理

### 2. 权限管理器 (PermissionManager)
- **功能**: 封装Android权限相关操作
- **支持权限**:
  - 麦克风权限 (microphone)
  - 存储权限 (storage)
  - 摄像头权限 (camera)
  - 悬浮窗权限 (systemAlertWindow)
  - 位置权限 (location)
  - 通知权限 (notification)
- **特性**:
  - 权限状态检查和请求
  - 批量权限操作
  - 权限引导和设置页面跳转

### 3. 悬浮窗控制器 (FloatingWindowController)
- **功能**: 控制小窗显示和交互
- **特性**:
  - 创建、显示、隐藏、销毁悬浮窗
  - 窗口拖拽和触摸控制
  - 窗口位置和大小调整
  - 窗口层级管理
  - 实时窗口状态监听

### 4. 屏幕截取服务 (ScreenCaptureService)
- **功能**: 实现屏幕内容获取
- **支持功能**:
  - 全屏截取
  - 指定区域截取
  - Widget截取
  - 实时截取（定时截取）
  - 图像格式转换和质量控制
- **特性**:
  - 高性能截取
  - 多种图像格式支持 (JPEG, PNG, WebP)
  - 截取进度监控
  - 自动保存到相册

### 5. 音频录制服务 (AudioRecordingService)
- **功能**: 实现语音录制和预处理
- **特性**:
  - 开始/暂停/停止/恢复录制
  - 多种音频格式支持 (AAC, MP3, WAV, FLAC)
  - 音频质量控制 (采样率、比特率、声道数)
  - 实时音频数据获取
  - 音频预处理 (降噪、增益、滤波)
  - 语音识别集成

### 6. 网络请求封装 (NetworkService)
- **功能**: HTTP客户端和AI API调用封装
- **基础功能**:
  - GET/POST/PUT/DELETE请求
  - 文件上传和下载
  - 请求/响应拦截器
  - 超时和重试机制
  - 请求取消支持
- **AI API集成**:
  - 文本生成 (GPT类模型)
  - 图像生成 (DALL-E类模型)
  - 语音识别 (Whisper类模型)
  - 语音合成 (TTS模型)
  - 向量嵌入 (Embedding模型)

### 7. 本地存储服务 (StorageService)
- **功能**: 配置信息和缓存管理
- **存储类型**:
  - SharedPreferences (轻量级配置)
  - FlutterSecureStorage (安全存储)
  - 文件系统存储
  - 内存缓存
- **特性**:
  - 数据加密存储
  - 缓存过期管理
  - 自动缓存清理
  - 存储统计和监控

## 🛠️ 安装和配置

### 依赖包配置

在 `pubspec.yaml` 中添加以下依赖：

```yaml
dependencies:
  flutter:
    sdk: flutter
  
  # 权限管理
  permission_handler: ^11.0.1
  
  # 网络请求
  dio: ^5.3.2
  
  # 安全存储
  flutter_secure_storage: ^9.0.0
  
  # 轻量级存储
  shared_preferences: ^2.2.2
  
  # 路径管理
  path_provider: ^2.1.1
  
  # 图像处理
  image: ^4.0.17
  
  # 图像保存
  image_gallery_saver: ^2.0.3
  
  # 加密
  crypto: ^3.0.3

dev_dependencies:
  flutter_test:
    sdk: flutter
```

### 权限配置

在 `android/app/src/main/AndroidManifest.xml` 中添加必要权限：

```xml
<!-- 权限声明 -->
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.RECORD_AUDIO" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.POST_NOTIFICATIONS" />
```

### Android平台配置

在 `android/app/src/main/AndroidManifest.xml` 的 `<application>` 标签内添加：

```xml
<!-- 悬浮窗服务声明 -->
<service
    android:name=".FloatingWindowService"
    android:enabled="true"
    android:exported="false" />

<!-- 屏幕截取服务声明 -->
<receiver
    android:name=".ScreenCaptureReceiver"
    android:enabled="true"
    android:exported="false" />
```

## 📖 使用方法

### 基础使用

```dart
import 'services/service_manager.dart';

// 1. 初始化服务管理器
final serviceManager = ServiceManager();

// 2. 初始化所有服务
await serviceManager.initialize();

// 3. 启动所有服务
bool success = await serviceManager.startAllServices();

if (success) {
  print('所有服务启动成功');
}

// 4. 获取服务实例
final permissionManager = serviceManager.permissionManager;
final networkService = serviceManager.networkService;
final storageService = serviceManager.storageService;
```

### 权限管理示例

```dart
// 检查权限
bool hasPermission = await permissionManager.checkAllPermissions();

if (!hasPermission) {
  // 请求权限
  await permissionManager.requestAllPermissions();
}

// 检查特定权限
bool microphonePermission = await permissionManager.checkPermission(Permission.microphone);
```

### 屏幕截取示例

```dart
// 截取全屏
CaptureResult? result = await screenCaptureService.captureFullScreen();

// 截取指定区域
Rect region = Rect.fromLTWH(100, 100, 300, 200);
CaptureResult? regionResult = await screenCaptureService.captureRegion(region: region);

// 实时截取
await screenCaptureService.startRealTimeCapture(
  interval: Duration(seconds: 2),
);
```

### 音频录制示例

```dart
// 开始录制
await audioRecordingService.startRecording(
  fileName: 'my_recording',
  config: RecordingConfig(
    sampleRate: 44100,
    channels: AudioChannel.mono,
    format: AudioFormat.aac,
  ),
);

// 暂停录制
await audioRecordingService.pauseRecording();

// 恢复录制
await audioRecordingService.resumeRecording();

// 停止录制
await audioRecordingService.stopRecording();

// 实时获取音频数据
AudioData? audioData = await audioRecordingService.getRealTimeAudioData();
```

### 网络请求示例

```dart
// 基础HTTP请求
NetworkResponse response = await networkService.get('/api/users');

// 文件上传
NetworkResponse uploadResult = await networkService.uploadFile(
  '/api/upload',
  File('path/to/file.jpg'),
);

// AI文本生成
AIResponse aiResponse = await networkService.generateText(
  prompt: '写一首关于春天的诗',
  maxTokens: 200,
  temperature: 0.8,
);

if (aiResponse.success) {
  print('生成的文本: ${aiResponse.textContent}');
}

// 语音识别
AIResponse transcription = await networkService.transcribeAudio(
  audioFilePath: 'path/to/audio.mp3',
  language: 'zh-CN',
);
```

### 本地存储示例

```dart
// SharedPreferences
await storageService.setString('username', '张三');
await storageService.setInt('score', 100);
await storageService.setBool('is_premium', true);
await storageService.setJson('user_config', {
  'theme': 'dark',
  'language': 'zh-CN',
});

// 安全存储
await storageService.setSecureString('api_key', 'your-secret-api-key');
await storageService.setSecureBytes('private_key', sensitiveBytes);

// 文件存储
await storageService.saveFile('config.json', configBytes);

// 缓存管理
await storageService.setCache('api_response', responseData, 
  expiry: Duration(hours: 1));

dynamic cachedData = storageService.getCache('api_response');
```

## 🔧 自定义配置

### 服务配置

```dart
// 自定义权限配置
final customPermissions = [
  Permission.microphone,
  Permission.camera,
  Permission.storage,
];

// 自定义录制配置
final customRecordingConfig = RecordingConfig(
  sampleRate: 48000,
  channels: AudioChannel.stereo,
  bitRate: 256000,
  format: AudioFormat.wav,
  enableNoiseSuppression: true,
  enableEchoCancellation: true,
);

// 自定义网络配置
final customNetworkConfig = NetworkConfig(
  baseUrl: 'https://your-api.com',
  timeout: Duration(seconds: 30),
  retryCount: 3,
);
```

### 事件监听

```dart
// 监听服务状态变化
serviceManager.onInitComplete.listen((initialized) {
  print('服务初始化完成: $initialized');
});

// 监听权限状态变化
permissionManager.onPermissionStatusChanged.listen((status) {
  print('权限状态变化: $status');
});

// 监听网络请求
networkService.onRequest.listen((request) {
  print('发送请求: ${request.method} ${request.url}');
});

networkService.onResponse.listen((response) {
  print('收到响应: ${response.statusCode}');
});

// 监听存储事件
storageService.onStorageEvent.listen((event) {
  print('存储事件: ${event.operation} ${event.key} ${event.success}');
});
```

## 📱 平台特定说明

### Android

1. **权限适配**: Android 6.0+需要动态权限申请
2. **悬浮窗**: 需要特殊权限 `SYSTEM_ALERT_WINDOW`
3. **后台录制**: 需要前台服务权限
4. **屏幕录制**: 需要MediaProjection API

### iOS (待扩展)

1. **权限系统**: 使用iOS原生权限框架
2. **悬浮窗**: iOS不支持系统级悬浮窗
3. **屏幕录制**: 使用iOS屏幕录制API
4. **音频录制**: 使用AVFoundation框架

## 🔒 安全考虑

1. **敏感数据**: 使用FlutterSecureStorage存储
2. **网络请求**: 启用HTTPS和证书校验
3. **权限最小化**: 只申请必要的权限
4. **数据加密**: 重要数据本地加密存储
5. **访问控制**: 实现细粒度的功能访问控制

## 🚧 注意事项

1. **平台兼容性**: 部分功能仅支持Android
2. **权限处理**: 需要用户明确授权才能使用某些功能
3. **性能影响**: 某些服务可能影响设备性能
4. **电池优化**: 避免在后台进行大量操作
5. **内存管理**: 及时释放不需要的资源

## 🐛 常见问题

### Q: 权限被拒绝怎么办？
A: 引导用户到设置页面手动开启权限，或提供功能降级方案。

### Q: 悬浮窗无法显示？
A: 检查是否有SYSTEM_ALERT_WINDOW权限，确保在Android 6.0+上正确申请。

### Q: 屏幕截取失败？
A: 检查MediaProjection权限，确保设备支持屏幕录制功能。

### Q: 音频录制音质不佳？
A: 调整录制配置，使用更高的采样率和比特率。

### Q: 网络请求超时？
A: 检查网络连接，调整超时时间，启用重试机制。

## 📄 许可证

MIT License - 详见LICENSE文件

## 🤝 贡献

欢迎提交Issue和Pull Request来改进这个框架。

## 📞 支持

如有问题或建议，请创建Issue或联系开发团队。