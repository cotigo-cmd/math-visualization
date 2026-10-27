# 数学可视化 · 交互教学门户

计算数学系列课程的配套交互教学页。每页一个可拖动的实验台：零依赖、可离线打开（公式渲染需联网加载 MathJax），页内所有数值结论都由本地脚本实测得出。

线上地址：<https://cotigo-cmd.github.io/math-visualization/>

## 结构

```
index.html                     总导航
<学科>/index.html              学科章节导航
<学科>/<页面>.html             教学页
.nojekyll                      关闭 Jekyll 处理，静态文件原样发布
```

## 学科

| 目录 | 内容 | 状态 |
| --- | --- | --- |
| `pde/` | 数学物理方程（谷超豪 第四版）：卷积与热核、分离变量法、傅里叶变换、唯一性与稳定性、达朗贝尔公式、高维波动方程、调和方程、方程分类、一阶方程组、广义函数与基本解 | 13 页 |
| `numerical_analysis/` | 数值分析（川大 2026 课件，朱瑞）：误差与浮点、Lagrange/Newton/Hermite/分段插值、数值积分与 Romberg、非线性方程迭代 | 7 页 |
| `numerical_linear_algebra/` | 数值线性代数（Trefethen & Bau）：矩阵—向量乘积、范数、SVD、投影算子、QR、最小二乘、条件数、共轭梯度；另含作业向三页（SVD 超椭圆、Givens/Householder、完全 QR）、期中复习指南与两套模拟卷 | 13 页 |
| `cpp_programming/` | C++ 程序设计（谭浩强）：指针与内存布局、对象内存模型、递归调用栈 | 3 页 |
| `functional_analysis/` | 泛函分析（江泽坚、孙善利）：单位球与开闭集、正交投影与最佳逼近、算子范数与共轭空间 | 3 页 |
| `parallel_computing/` | 并行算法（Quinn）：Amdahl 与 Gustafson-Barsis 加速比 | 1 页 |

## 更新

```bash
git add -A
git commit -m "内容更新：说明改了什么"
git push
```

推送后 GitHub Pages 会自动重新发布，通常 30 秒内生效。

## 本地预览

直接双击 `index.html` 即可；或在仓库根目录跑 `python -m http.server 8000`，访问 <http://localhost:8000>。
