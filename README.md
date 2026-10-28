# 数学可视化 · 六门计算数学课的概念实验台

打开就能拖的数学讲义：每一页是一个交互实验台，拖滑杆或切换预设，图、公式、读数同时变化。

**在线地址：<https://cotigo-cmd.github.io/math-visualization/>**

不需要账号、不需要注册、不需要是某所学校的学生。零依赖，双击 HTML 文件就能离线打开
（公式首次渲染需联网加载 MathJax）。

## 为什么会有这个站

课本上的公式是静态的，而「ε 变小误差为什么反而变大」「SVD 到底把圆变成了什么」
这类问题，看一百遍推导也不如把滑杆拖一遍。所以这里的每一页都围绕一个问题建：

- 想看清 SVD 在做什么 → [SVD 的几何](numerical_linear_algebra/SVD-几何与低秩近似.html)
- 想知道为什么不用正规方程解最小二乘 → [QR 与三种解法](numerical_linear_algebra/QR分解-Gram-Schmidt与Householder.html)
- 想知道误差怎么被放大 → [条件数](numerical_linear_algebra/条件数-几何与误差放大.html)
- 想知道插值为什么在两端炸掉 → [Runge 现象](numerical_analysis/插值-Runge现象与切比雪夫节点.html)
- 想知道 δ 函数怎么「算」→ [广义函数与基本解](pde/广义函数与基本解-弱导数与卷积法.html)
- 想知道 3 维为什么才有清晰波前 → [球平均法与泊松公式](pde/高维波动方程-球平均法与泊松公式.html)

完整入口在[首页](index.html)，按「问题」或按「学科」两种方式都能进。

## 内容

40 个交互页，六个学科：

| 目录 | 学科 | 主要教材 | 页数 |
| --- | --- | --- | --- |
| `numerical_linear_algebra/` | 数值线性代数 | Trefethen & Bau | 13 |
| `pde/` | 数学物理方程 | 谷超豪（第四版） | 13 |
| `numerical_analysis/` | 数值分析 | 按常见课程讲序编排（其他教材可按概念名对应） | 7 |
| `cpp_programming/` | C++ 程序设计 | 谭浩强 | 3 |
| `functional_analysis/` | 泛函分析 | 江泽坚、孙善利 | 3 |
| `parallel_computing/` | 并行算法 | Quinn（MPI/OpenMP） | 1 |

用这些教材的读者会看到页码与节号对照；用别的教材也不影响阅读，页面按概念命名，不按章节命名。

## 一个不太常见的做法：页内数字都是算出来的

站内没有「看起来合理」的示例数字。每个页面配一份独立验证脚本，用**另一条算法路径**重算页面上的
读数再逐项比对（例如页面用闭式公式，脚本就用幂迭代；页面用 Simpson，脚本就用 Gauss–Legendre）。
收敛阶、误差、条件数、加速比，都是本机真实跑出来的。

因此你会看到一些「教材上不会写」的结果，比如：Hermite 插值在某组结点上**反而比 Lagrange 差**
（结点落在函数零点上时），页面如实保留为反例，没有藏起来。

## 技术

- 单文件 HTML，无构建步骤，无框架，无追踪脚本
- 公式用 MathJax 3（SVG 输出），交互用原生 JS + Canvas/SVG
- 移动端：公式容器显式 `min-width:0`，长公式在框内横向滑动而不溢出（MathJax 默认的内联
  `min-width` 会压过 `max-width`，这是个容易反复踩的坑）

## 本地使用

双击 `index.html` 即可；或在本目录跑 `python -m http.server 8000`，访问 <http://localhost:8000>。

## 目录结构

```
index.html                     总导航
<学科>/index.html              学科章节导航
<学科>/<页面>.html             教学页
.nojekyll                      关闭 Jekyll 处理，静态文件原样发布
```

## 更新（给自己看）

```bash
git add -A && git commit -m "说明改了什么" && git push
```

推送后 GitHub Pages 自动重建，约 30 秒生效。
