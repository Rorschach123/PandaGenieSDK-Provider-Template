# PandaGenieSDK Provider Template

**中文优先说明 | English follows**

[官网](https://cf.pandagenie.ai) | [SDK 注册](https://cf.pandagenie.ai/sdk) | [SDK 源码](https://github.com/Rorschach123/PandaGenieSDK) | [PandaGenieSource](https://github.com/Rorschach123/PandaGenieSource) | [Discord](https://discord.gg/Cfc7pjrjt2)

---

## 中文说明

这是一个独立 Android 模板工程，用于帮助第三方应用接入 PandaGenieSDK，并把自己的能力暴露给 PandaGenie 或其他已审核 AI 助手调用。

适合场景：

- 你的 App 想提供“打开到指定页面并展示传入内容”。
- 你的 App 想提供本地数据查询、创建、更新或导出能力。
- 你的 App 想通过 Service、Activity、ContentProvider 或 BroadcastReceiver 暴露能力。
- 你希望调用方必须经过包名、Release 签名和角色审核。

## 项目结构

```text
.
├── app/                         # Demo Provider 应用
│   └── src/main/AndroidManifest.xml
├── build.gradle                 # 根 Gradle 配置
├── settings.gradle              # Android 工程设置
└── README.md                    # 当前说明
```

## 快速开始

1. 在 Android Studio 中打开本工程。
2. 修改 `applicationId`、包名、应用名称和能力清单。
3. 使用 Release 签名构建 APK。
4. 到 [SDK 注册页](https://cf.pandagenie.ai/sdk) 提交应用。
5. 审核通过后，安装到同一台手机上的 PandaGenie 就可以发现并调用你的能力。

## 依赖

```gradle
dependencies {
    implementation("ai.rorsch.pandagenie:pandagenie-sdk:0.1.0-preview")
}
```

如果你正在本地开发 SDK，可以改成 composite build 或本地模块依赖。

## 获取 Release SHA-256 签名

```bash
apksigner verify --print-certs app-release.apk
```

或：

```bash
keytool -list -v -keystore release.jks -alias your_alias
```

注册页接受带冒号或不带冒号的 SHA-256，提交时会统一规范化为 64 位大写十六进制。

## Demo 能力

模板建议至少包含下面几类示例，便于 PandaGenie 验证 SDK 互操作链路：

- Activity：打开 App 指定页面，并显示调用方传入的文字。
- Service：接收 JSON 参数，返回 JSON 结果。
- ContentProvider：提供只读示例数据。
- BroadcastReceiver：接收事件型调用。

## 能力清单示例

```json
[
  {
    "id": "demo.open_text",
    "name": "打开文本展示页",
    "kind": "open_ui",
    "description": "打开应用页面并展示传入文本",
    "params": {
      "text": "string"
    }
  }
]
```

---

## English

This is a standalone Android template for apps that want to expose callable capabilities to PandaGenie or another trusted AI assistant through PandaGenieSDK.

Use it when your app needs to:

- Publish a machine-readable capability manifest.
- Receive calls from verified AI assistants.
- Expose Activity, Service, ContentProvider, or BroadcastReceiver examples.
- Validate callers through the PandaGenie SDK trust registry.
- Return structured results that assistants can show to users.

## Structure

```text
.
├── app/                         # Demo provider application
│   └── src/main/AndroidManifest.xml
├── build.gradle                 # Root Gradle configuration
├── settings.gradle              # Android project settings
└── README.md                    # This guide
```

## Quick Start

1. Open this project in Android Studio.
2. Replace `applicationId`, package names, app label, and exported capabilities.
3. Build a release APK with your signing key.
4. Register the app at [SDK Registration](https://cf.pandagenie.ai/sdk).
5. After approval, PandaGenie can discover and invoke your app on the same device.

## Links

- Website: <https://cf.pandagenie.ai>
- SDK registration: <https://cf.pandagenie.ai/sdk>
- SDK source: <https://github.com/Rorschach123/PandaGenieSDK>
- PandaGenie source: <https://github.com/Rorschach123/PandaGenieSource>
- Discord: <https://discord.gg/Cfc7pjrjt2>
