# 理想气体的压强公式 · 3D 交互推导

依据《大学物理》第十二章 12.3 节制作的单页 3D 交互课件。从一次分子碰撞出发，经过冲量、速度圆柱、统计求和与各向同性，推导：

\[
P=\frac{1}{3}nm\overline{v^2}=\frac{2}{3}n\bar{\varepsilon}_k
\]

页面为纯静态单文件：`index.html` 已内嵌全部 HTML、CSS、JavaScript 与 MathML 公式，不依赖 CDN，可离线运行，也可直接部署到 GitHub Pages。

![页面预览](preview.png)

## 功能

- 可拖动旋转、滚轮缩放的 3D 气体容器
- 分子与器壁弹性碰撞、冲量波纹、碰撞频率显示
- 七步交互推导：微观模型 → 一次碰撞 → 冲量 → 速度圆柱 → 统计求和 → 各向同性 → 压强公式
- 第 04 步使用圆柱体展示 \(dN_i=n_i v_{ix}\,dt\,ds\)
- 第 05 步完整展示 \(n_i\) 的代换：
  \[
  n_i=\frac{N_i}{V}
  =\frac{N_i}{V}\cdot\frac{N}{N}
  =\frac{N_i}{N}\cdot\frac{N}{V}
  =w_i n
  \]
- 实时调节温度 \(T\) 与分子数密度 \(n\)，同步更新压强、方均根速率、麦克斯韦速率分布
- 公式使用浏览器原生 MathML 排版，分式、求和号、上下标与等号对齐
- 响应式布局：桌面双栏，平板/手机自动单栏

## 本地使用

直接双击打开 `index.html`，推荐使用较新的 Chrome / Edge / Firefox / Safari。

也可以在本目录启动一个静态服务器：

```bash
# Python 3
python -m http.server 8080
```

然后访问 `http://localhost:8080/`。

## 部署到 GitHub Pages

1. 新建一个 GitHub 仓库，例如 `ideal-gas-pressure-3d`。
2. 将本目录中的文件上传到仓库**根目录**（确保 `index.html` 在根目录）。
3. 打开仓库的 **Settings → Pages**。
4. 在 **Build and deployment** 中选择：
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/ (root)`
5. 保存后等待片刻，访问：
   `https://你的用户名.github.io/ideal-gas-pressure-3d/`

本页面不需要构建步骤，也不需要 Node.js 或任何第三方依赖。

## URL 参数

可以直接指定打开第几步以及初始参数：

```text
index.html?step=5
index.html?step=4&t=500&n=3.2
index.html?step=1&paused=1
```

- `step`：1–7，打开指定步骤
- `t`：温度，200–600 K
- `n`：分子数密度，0.8–3.6（单位：\(10^{25}\,\mathrm{m^{-3}}\)）
- `paused=1`：以暂停状态打开

## 文件说明

| 文件 | 说明 |
| --- | --- |
| `index.html` | 完整交互课件，单文件、可离线运行 |
| `preview.png` | 页面整体预览 |
| `step-04-cylinder.png` | 第 04 步圆柱体示意预览 |
| `step-05-formula.png` | 第 05 步公式与 \(n_i\) 代换预览 |
| `conclusion.png` | 结论区预览 |
| `.nojekyll` | 跳过 GitHub Pages 的 Jekyll 构建 |

## 操作提示

- **拖动**：旋转 3D 视角
- **滚轮 / 双指捏合**：缩放
- **点击分子**：锁定并查看速度分量
- **空格**：暂停 / 继续
- **R**：重置视角
- **← / →**：上一步 / 下一步
- **1–7**：切换推导步骤

## 内容依据

- 大学物理 第十二章 12.3 理想气体的压强公式
- 页面中的温度、数密度与速率数值按氮气 \(M=28\,\mathrm{g/mol}\) 估算，用于课堂演示
