---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# 数据源

cedarkit-maps 不限定数据加载的工具库，可以支持多种数据源。
只要加载后的数据对象满足下面给出的基本条件，就可以被正确识别。

```{admonition} 基本条件
格点数据为 `xarray.DataArray` 格式，以纬度 (latitude)、经度 (longitude) 为坐标的二维数组，按行存储（纬度）。
```

## 示例

使用 reki 加载 CMA-MESO 的 2 米温度场

```{code-cell} ipython3
import pandas as pd
from reki.data_finder import find_local_file
from reki.format.grib.eccodes import load_field_from_file

file_path = find_local_file(
    "cma_meso_3km/grib2/orig",
    start_time=pd.to_datetime("2024-04-01 00:00"),
    forecast_time=pd.to_timedelta("24h"),
)
  
t_2m_field = load_field_from_file(
    file_path,
    parameter="2t",  
) - 273.15
t_2m_field
```

上述要素场包含两个维度属性

- `latitude`：纬度
- `longitude`：经度

同时包含其他非维度的坐标属性

- `time`：起报时次
- `step`：预报时效
- `valid_time`：预报时间
- `heightAboveGround`：层次类型，离地面高度，单位米