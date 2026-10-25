<h4 align="right">
  <a href="./README.en-US.md">English</a>
  <span style="margin:0 10px;color:#24292f">简体中文</span>
</h4>
<p align="center">
<img src="https://jjp2.pages.dev/1.png" width="300"/>
</p>
<h1 align="center">JJP｜对抗性图像扰动生成器</h1>
<p align="center">
静态网页实现,用户图片不会上传至任何远端服务器。
</p>
<p align="center">
<a href="https://github.com/jjp117/128/releases">
<img src="https://img.shields.io/github/v/release/jjp117/128?style=flat-square&logo=github" alt="Release">
</a>
<a href="https://github.com/jjp117/128/stargazers">
<img src="https://img.shields.io/github/stars/jjp117/128?style=flat-square&logo=github" alt="Stars">
</a>
<a href="https://github.com/jjp117/128/blob/main/LICENSE">
<img src="https://img.shields.io/github/license/jjp117/128?style=flat-square&logo=github" alt="License">
</a>
</p>
<br>
<p align="center">
<a href="https://aino.pages.dev/" target="_blank">
<img src="https://img.shields.io/badge/🔗立即访问‑AI迷彩-2563eb?style=for-the-badge&logo=https://aino.pages.dev/&logoColor=white" width="320" alt="打开AI迷彩">
</a>
&nbsp;&nbsp;
<a href="https://github.com/jjp117/128/releases" target="_blank">
<img src="https://img.shields.io/badge/📥下载源码-red?style=for-the-badge&logo=github&logoColor=white" width="320" alt="下载源码">
</a>
</p>

# JJP AI Camouflage
## 这是什么
JJP AI Camouflage 是一款基于数学算法的图像预处理工具。它通过在像素层面注入结构化噪声与几何畸变，破坏图像的低阶视觉特征（边缘、纹理、色彩相关性），旨在提高自动化 OCR 工具和轻量级计算机视觉模型的识别成本。

## 设计目标
为非专业用户提供一种简单、直接的版权保护辅助手段。使用者无需掌握深度学习知识、无需训练模型、无需 GPU 算力，仅需通过浏览器即可完成对画作、文档截图等内容的“防抓取”处理。

## 运行方式
完全运行在浏览器本地。所有扰动计算均基于 Canvas ImageData API 与原生 JavaScript 数学库完成，不依赖任何后端服务，不调用任何 AI 推理接口。

## 算法原理
采用混合扰动策略：
1. **亚像素几何畸变**：对 Sobel 梯度场施加微小正弦位移（振幅 ≤1.5px），打断 Canny/Sobel 算子的边缘连续性。
2. **通道相位解耦**：对 R/G/B 三通道独立施加异相伪随机偏移，破坏自然图像的色彩空间相关性。
3. **结构化摩尔纹叠加**：合成低频棋盘格纹理（Opacity 5-15%），混淆 LBP/GLCM 局部二值模式特征提取。

## 强度分级
提供三个预设档位与自由滑块：
- **Human First (0-30%)**：画质优先。肉眼几乎不可见噪点，防御力较弱，适用于日常分享。
- **Balanced (30-70%)**：均衡模式。轻微颗粒感，能有效干扰传统 OCR 引擎，推荐默认使用。
- **Machine Blind (70-100%)**：防御优先。明显噪点与模糊，针对绝大多数自动化爬虫具备显著阻断效果，但牺牲美观度。

## 使用方式
打开网页版即可使用。用户将图片拖入页面，调整强度滑块预览效果；确认后点击导出按钮，生成带有对抗性扰动的 PNG 文件。注意：必须导出为 PNG，JPG 压缩会平滑掉高频保护噪点导致失效。
> 网页版：https://aino.pages.dev/

## ⚠️ 浏览器兼容提示
依赖高性能 Canvas 像素操作。处理 4K 及以上分辨率图片时可能出现短暂卡顿。建议在配备 SSD 与 ≥8GB 内存的设备上使用。老旧移动端浏览器可能因内存溢出而崩溃。

## 安全性与局限性声明
- **非隐形迷彩**：中高強度下噪点人眼可见。这是一种显性的威慑手段，而非完美的隐身技术。
- **防御天花板**：主要针对 Tesseract/EasyOCR 等传统引擎及轻量级 CNN。对于 GPT-4V/Claude 3 等多模态大模型，其上下文理解能力极强，本工具仅能增加其计算负担，无法保证 100% 不被识别。
- **艺术性损害**：处理后图像并非原始无损状态，追求极致画质的场景请慎用。

## 已知限制
- 不支持矢量图 (SVG) 的直接编辑，需先栅格化。
- 无法防御针对性的去噪算法攻击。
- 单次处理耗时随分辨率线性增长。

