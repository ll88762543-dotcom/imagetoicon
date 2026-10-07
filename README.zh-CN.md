# ImageToIcon

<p align="center">
<a href="README.md">English</a> | <a href="README.zh-CN.md">简体中文</a>
</p>

<p align="center">
<a href="https://dotnet.microsoft.com/download"><img src="https://img.shields.io/badge/.NET-10-512BD4?style=for-the-badge&logoColor=white" title=".NET 10 or higher" alt=".NET"></a>
<a href="https://learn.microsoft.com/dotnet/csharp/"><img src="https://img.shields.io/badge/language-C%23-239120?style=for-the-badge&logo=csharp&logoColor=white" title="Written in C#" alt="C#"></a>
<a href="https://avaloniaui.net/"><img src="https://img.shields.io/badge/UI-Avalonia-8B5CF6?style=for-the-badge&logoColor=white" title="Built with Avalonia UI" alt="Avalonia"></a>
<a href="https://distrochooser.de/"><img src="https://img.shields.io/badge/cross%E2%80%93platform-Linux%2BWindows-blue?style=for-the-badge&logo=linux&logoColor=silver" title="Runs on Linux and Windows" alt="Platform"></a>
<a href="LICENSE.txt"><img src="https://img.shields.io/github/license/Si13n7/ImageToIcon?style=for-the-badge" title="Read the license terms" alt="License"></a>
</p>
<p align="center">
<a href="../../issues"><img src="https://img.shields.io/github/issues/Si13n7/ImageToIcon?logo=github&logoColor=silver&style=for-the-badge" title="Browse open issues" alt="Open Issues"></a>
<a href="../../commits/master"><img src="https://img.shields.io/github/last-commit/Si13n7/ImageToIcon?logo=github&logoColor=silver&style=for-the-badge" title="Check the last commits" alt="Last Commit"></a>
<a href="../../releases/latest"><img src="https://img.shields.io/github/v/release/Si13n7/ImageToIcon?logo=github&logoColor=silver&style=for-the-badge" title="Check the latest release" alt="Release"></a>
</p>

**ImageToIcon** 是一款小巧的跨平台工具，可将任意图片转换为多尺寸的 Windows `.ico` 文件。只需拖入一张图片，它便会一次性生成所有标准图标尺寸，并采用干净的 Lanczos 缩放算法——没有广告、也没有捆绑一堆小工具。

> 过去每一个图标生成都意味着要摆弄三个工具：一个用于缩放，一个用于合成，一个用于导出。ImageToIcon 将其合并为一个窗口和一个保存按钮。

---

## 预览（浅色 / 深色）
<p align="center"><a href="media/"><img src="media/preview.png"></a></p>

---

## 功能特性

- 原生运行于 Linux 和 Windows——相同的C#逻辑，相同的输出
- 支持加载任何常见的图片格式：`PNG`、`JPG`、`BMP`、`TIF`、`GIF`、`WEBP`、`TGA`、`QOI`、`PBM`/`PGM`/`PPM`/`PNM`
- 可直接加载 `SVG` 文件（通过 Skia 栅格化），并可直接从 `ICO`、`EXE` 和 `DLL` 文件中提取图标帧
- 默认预设匹配当前 Windows 11 应用程序图标集（256、64、48、40、32、24、20、16）
- 可自由添加、编辑或删除自定义尺寸——从 2&nbsp;px 到 4096&nbsp;px 的任意值，右键单击尺寸即可管理
- 高质量的 Lanczos-3 重采样，确保每个尺寸都清晰锐利
- 可手动替换单个尺寸——为 16&nbsp;px 或 32&nbsp;px 换入手工调校的图片，它会被就地缩放以适配对应尺寸
- 支持将文件拖放到主窗口和单个缩略图上
- 提供 CLI 模式，用于批量转换和脚本编写——一次调用即可处理整个文件夹的图片
- 在 `ICO` 容器内使用 `PNG` 压缩帧，以减小文件体积，在 256&nbsp;px 及以上尺寸尤为明显

---

## 下载

最新版本可在 [Releases](https://github.com/Si13n7/ImageToIcon/releases/latest) 页面获取——无需安装，解压后直接运行可执行文件即可——Windows 上为 *ImageToIcon.exe*，Linux 上为 *ImageToIcon*。

---

## 命令行

ImageToIcon 也可以无界面运行。任何包含 `--cli`（或 `/cli`）的调用都会跳过 UI，直接处理文件：

```bash
ImageToIcon --cli --o=./out image1.png image2.jpg
ImageToIcon --cli --o=./out --sizes=16,32,48,256 logo.png
```

| 选项 | 说明 |
| --- | --- |
| `--cli`, `/cli` | 以 CLI 模式运行。 |
| `--o=DIR`, `/o=DIR` | 生成的 `.ico` 文件的输出目录。 |
| `--sizes=<list>` | 以逗号分隔的图标尺寸列表（2–4096）。 |
| `--help`, `/?` | 显示用法信息。 |

---

## 系统要求

### Linux
- 任意现代 x64 Linux 发行版
- 无需 .NET 运行时——以自包含的单文件可执行程序发布

### Windows
- Windows 10 或更高版本（x64）
- 无额外依赖——以自包含的单文件可执行程序发布

---

## 从源代码构建

### 前置条件

- [.NET 10 SDK](https://dotnet.microsoft.com/download)

### 构建

```bash
# 调试构建（默认，仅 linux-x64）
./build.sh

# 发布构建（linux-x64 和 win-x64）
./build.sh Release
```

### 直接运行（无需完整构建）

```bash
cd src/ImageToIcon
dotnet run
```
