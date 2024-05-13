# 绘图种类

本节首先以 [CMA-GFS 东亚区域 500 hPa 高度场 + 850 hPa 风场图片产品](http://10.1.64.146/npt/f/p-57489) 为例，介绍如何单独绘制集中基本绘图类型，包括：

- 等值线
- 填充图
- 风场图

然后介绍如何将以上几种图形叠加到一张图片中。


## 基本绘图步骤

绘图分为三步：准备数据、配置样式和绘制图形。

### 准备数据

使用 reki 库从 GRIB2 文件中加载要素场，示例代码：

```python
from reki.format.grib.eccodes import load_field_from_file

field = load_field_from_file(
    data_path,
    parameter="parameter name",
    level_type="level type name",
    level=some_level
)
```

### 配置样式

每类图形有自己的样式，比如

- `ContourStyle`：等值线/填充图样式
- `BarbStyle`：风场图样式

```python
from cedarkit.maps.style import ContourStyle

contour_style = ContourStyle(
    levels=contour_levels,
    colors=contour_color",
    linewidths=contour_linewidths,
)
```

### 绘制图形

使用内置底图布局 (`EastAsiaMapDomain`) 和高层 API 接口 (`Panel`) 绘制图形

```python
from cedarkit.maps.chart import Panel
from cedarkit.maps.domains import EastAsiaMapDomain

domain = EastAsiaMapDomain()
panel = Panel(domain=domain)
panel.plot(field, style=contour_style)
panel.show()
```