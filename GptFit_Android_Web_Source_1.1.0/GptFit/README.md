# GptFit Android + Web Preview

GptFit 是本地优先的训练记录与习惯养成应用。Android 版使用 Kotlin + WebView；网页预览版与 Android 版共用同一套 HTML/CSS/JavaScript 和动作数据库。

## 先预览网页（无需 Android Studio）

上传本项目到 GitHub 后：
1. 打开仓库 **Settings → Pages**。
2. 在 **Build and deployment → Source** 选择 **GitHub Actions**。
3. 打开 **Actions → Deploy GptFit Web Preview → Run workflow**（也会在推送 docs 目录变更时自动发布）。
4. 成功后在 Actions 的部署记录中打开 `github-pages` 环境链接。网页可在电脑或手机浏览器使用。

网页预览地址通常为 `https://你的GitHub用户名.github.io/仓库名/`。首次部署后以 Actions 显示的 URL 为准。

## 云端构建 Android APK（无需本地 Android Studio）

1. 上传项目根目录中的全部文件到 GitHub 仓库。
2. 打开 **Actions → Android Debug APK → Run workflow**，或推送到 main/master 自动触发。
3. 构建成功后下载 Artifact：`GptFit-debug-apk`，解压得到 `app-debug.apk`。
4. 将 APK 传到 Android 手机安装。

## 项目环境
- JDK 17
- Android SDK Platform 35
- Gradle 8.9（GitHub Actions 自动配置）
- Android Gradle Plugin 8.7.3 / Kotlin 2.0.21

## 当前功能
- 首页：积分、训练次数、习惯状态和快捷入口。
- 训练中心：L1–L4 四级周计划与训练记录入口。
- 动作库：18 个肌群 × 4 种训练方式 × 4 个等级，共 288 条基础动作映射；支持搜索、筛选和动作详情。
- 训练记录：动作、组数、次数、重量、RPE、日期与备注。
- 成长：习惯打卡、积分、目标进度和基础徽章。
- 我的：个人设置、本地 JSON 备份导出、清空本地数据。

## 目录
- `app/src/main/java/com/gptfit/app/MainActivity.kt`：Kotlin Activity 与 WebView 容器。
- `app/src/main/assets/`：Android 本地网页资源。
- `docs/`：GitHub Pages 网页预览资源（与 Android 前端保持同步）。
- `.github/workflows/android.yml`：云端构建 Debug APK。
- `.github/workflows/pages.yml`：云端发布网页预览。

## 数据与限制
训练数据保存在当前设备/浏览器的 localStorage 中。网页预览与 Android App 的数据互不共享；清除浏览器数据、卸载应用或清除应用数据可能导致记录丢失，请定期导出 JSON 备份。动作库属于基础映射资料，部分参数尚未逐条经过运动医学或专业教练审核。首版不包含 AI 视频识别、云端同步或真实动作 GIF/视频。
