# 地图

cedarkit-maps 的 `cedarkit.maps.map` 模块负责地图加载，主要解决 Cartopy 的中国地图问题。目前支持两种地图底图，通过类的形式封装，所有地图包类继承自 `MapLoader`。

- 默认地图 (`cedarkit.maps.map.default.DefaultMapLoader`)：使用内置的开源项目 china-shapefiles 资源文件绘制中国地图。
- CEMC 地图 (`cedarkit.maps.map.cemc.CemcMapLoader`)：使用内部项目 cemc-meda-data 中的 CEMC 地图绘制地图。

cedarkit-maps 默认使用 `DefaultMapLoader` 底图包，可以使用 `set_default_map_loader_package` 修改默认使用的地图包，底图布局类调用  `get_map_class` 函数获取当前默认的地图包类。

下面代码将默认地图包设为项目内置的 CEMC 地图包。

```{note}
需要单独安装内部项目库 cemc-meda-data 才能使用 CEMC 地图包
```

```python
from cedarkit.maps.map import set_default_map_loader_package

set_default_map_loader_package("cedarkit.maps.map.cemc")
```