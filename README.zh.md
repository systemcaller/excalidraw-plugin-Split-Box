
# Excalidraw 插件：Split Box

[English](README.md) | [简体中文](README.zh.md)

*一个简单而强大的 Excalidraw 插件，用于将矩形框分割成矩阵结构。*

[![GitHub Stars](https://img.shields.io/github/stars/SystemCaller/excalidraw-plugin-Split-Box?style=social)](https://github.com/SystemCaller/excalidraw-plugin-Split-Box/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/SystemCaller/excalidraw-plugin-Split-Box?style=social)](https://github.com/SystemCaller/excalidraw-plugin-Split-Box/network/members)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## 概述

**分割框 (Split Box)** 是一个专为 Excalidraw 设计的插件，旨在增强你的绘图体验。它允许你轻松地将矩形框水平、垂直或同时分割，创建类似矩阵的结构。完美适用于创建网格、表格、流程图或任何需要细分区域的布局。

- **主要特性**：
  - 水平分割：将矩形分割成多行
  - 垂直分割：将矩形分割成多列
  - 矩阵生成：结合两种方式创建网格布局
  - 可自定义分割：根据需要调整分割数量
  - 与 Excalidraw 绘图工具无缝集成

此插件非常适合经常处理结构化图表的用户，例如思维导图、组织架构图或 UI 线框图。

## 安装

要在 Excalidraw 中安装 Split Box 插件：

1. **下载插件**：
   - 克隆此仓库：
     ```
     git clone https://github.com/SystemCaller/excalidraw-plugin-Split-Box.git
     ```
   - 或从[发布页面](https://github.com/SystemCaller/excalidraw-plugin-Split-Box/releases)下载 ZIP 文件

2. **在 Excalidraw 中加载**：
   - 在浏览器中打开 Excalidraw（例如 [excalidraw.com](https://excalidraw.com)）
   - 进入菜单：`Menu > Load Plugin`（菜单 > 加载插件）
   - 选择下载仓库中的 `Split Box.md` 或 `Split Box.svg` 文件
   - 插件现在将出现在你的 Excalidraw 工具栏中

3. **依赖项**：
   - 无需额外依赖项。适用于标准的 Excalidraw 环境

> **注意**：确保使用最新版本的 Excalidraw 以获得兼容性。如果遇到问题，请查看 [Excalidraw 文档](https://docs.excalidraw.com/docs/plugins/introduction)

## 使用方法

安装后，使用 Split Box 非常简单：

1. **绘制矩形**：
   - 使用 Excalidraw 的矩形工具创建基础框

2. **激活插件**：
   - 选择矩形
   - 点击工具栏中的 "Split Box"（分割框）图标（或使用配置的快捷键）

3. **配置分割**：
   - **水平分割**：输入行数（例如 2 表示对半分割）
   - **垂直分割**：输入列数（例如 3 表示三分）
   - **矩阵模式**：同时启用两者以创建网格（例如 2x3 矩阵）

4. **应用并编辑**：
   - 插件将自动生成具有相等间距的分割
   - 你可以进一步编辑线条、添加文本或根据需要连接元素

### 示例

以下是逐步示例：

- **输入**：单个矩形
- **操作**：水平分割成 2 部分
- **输出**：两个相等的行

<img width="979" height="356" alt="image" src="https://github.com/user-attachments/assets/c847b64c-49ba-4db5-be16-2750f6f93353" />

对于 2x3 矩阵：

- 选择矩形 → 水平分割（2） → 垂直分割（3）

<img width="978" height="364" alt="image" src="https://github.com/user-attachments/assets/bdb80100-4306-4e09-a9b9-454e24bc92e0" />

有关更多高级用法，请参阅此仓库中的 [Split Box.md](Split%20Box.md) 文件，其中包含详细的代码片段和配置。

## 贡献

我们欢迎贡献！参与方式：

1. Fork 此仓库
2. 创建新分支：`git checkout -b feature/your-feature`
3. 提交更改：`git commit -m 'Add some feature'`
4. 推送到分支：`git push origin feature/your-feature`
5. 提交 Pull Request

请阅读 [CONTRIBUTING.md](CONTRIBUTING.md) 了解我们的行为准则和提交流程详情。（如果不存在，欢迎创建！）

## 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件。

## 致谢

- 为 Excalidraw 社区倾心打造
- 灵感来自生产力工具中的常见绘图需求
- 感谢贡献者：[]

如果你觉得此插件有用，请在 GitHub 上给它一个 ⭐！

---

*最后更新：2025 年 2 月*
*作者：SystemCaller*
*如需支持，请在 GitHub 上提交 issue。*
