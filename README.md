mapbox：http://www.kingpika.top:3392/mapbox/mapboxstyle.html
leaflet：http://www.kingpika.top:3392/leaflet/vectortiles.html
maptalks：http://www.kingpika.top:3392/maptalks/demo/

# PosTile 

[![Docker image](https://images.microbadger.com/badges/image/oslandia/postile.svg)](https://hub.docker.com/r/oslandia/postile/)

Fast Mapbox Vector Tile Server

## Features

- serve Mapbox Vector Tiles from a PostGIS backend 
- can read TM2 file data sources with postgis 
- can serve PostGIS layers individually 
- handle on-the-fly reprojection to web mercator projection (only for single layers, not tm2 sources)
- Connection pooling and asynchronous requests thanks to [asyncpg](https://github.com/MagicStack/asyncpg)
- tested with [openmaptiles vector tile schema](https://github.com/openmaptiles/openmaptiles)

## Requires 

- features stored with PostGIS >= 2.4.0

## Installation 

**Python 3.6** is required to run Postile

    pip install cython
    pip install -e .
    postile --help

## Using a Docker container

Start Postile with:

    docker run --network host oslandia/postile postile --help

## Example of serving postgis layers individually

    postile --pguser **** --pgpassword **** --pgdatabase mydb --pghost localhost --listen-port 8080 --cors

Then layer `boundaries` can be served with: 

    http://localhost:8080/boundaries/z/x/y.pbf?fields=id,name

`fields` is optional, and when absent only geometries are encoded in the vector tile.

You can specify schema in this way:

    http://localhost:8080/public.xxx/z/x/y.pbf
    
the default schema is 'public'

---

*For a concrete example using OpenMapTiles schema see [this tutorial](https://github.com/ldgeo/postile-openmaptiles)*


# ——————————中文——————————

# 前端演示demo
mapbox：http://www.kingpika.top:3392/mapbox/mapboxstyle.html
leaflet：http://www.kingpika.top:3392/leaflet/vectortiles.html
maptalks：http://www.kingpika.top:3392/maptalks/demo/

# PosTile 

[![Docker image](https://images.microbadger.com/badges/image/oslandia/postile.svg)](https://hub.docker.com/r/oslandia/postile/)

快速搭建postgis瓦片服务（基于mapbox pbf格式）

## 功能点

- 从PostGIS后端提供Mapbox Vector Tiles
- 可以使用postgis读取TM2文件数据源
- 可以单独为PostGIS图层提供服务
- 处理web mercator投影的动态重投影（仅适用于单层，而不是tm2源）
- 感谢[asyncpg]（https://github.com/MagicStack/asyncpg）的连接池和异步请求
- 使用[openmaptiles vector tile schema]进行测试（https://github.com/openmaptiles/openmaptiles）

## 环境要求 

- PostGIS版本 >= 2.4.0

## 安装 

需要事先安装**Python 3.6** 

    pip install cython
    pip install -e .
    postile --help

## 使用docker

使用以下命令启动:

    docker run --network host oslandia/postile postile --help

## 单独指定postgis图层的示例

    postile --pguser **** --pgpassword **** --pgdatabase mydb --pghost localhost --listen-port 8080 --cors

如果你有一个图层`boundaries` ，你可以这样获取它的切片: 

    http://localhost:8080/boundaries/z/x/y.pbf?fields=id,name

`fields`是可选的，当不存在时，默认返回所有属性字段。

你可以用以下方式指定schema:

    http://localhost:8080/public.xxx/z/x/y.pbf
    
默认schema是'public'

---

*有关使用OpenMapTiles模式的具体示例，请参阅[本教程]（https://github.com/ldgeo/postile-openmaptiles）*



