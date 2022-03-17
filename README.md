KV存储引擎

众所周知，非关系型数据库redis，以及levedb，rockdb其核心存储引擎的数据结构就是跳表。

本项目就是基于跳表实现的轻量级键值型存储引擎，使用C++实现。插入数据、删除数据、查询数据、数据展示、数据落盘、文件加载数据，以及数据库大小显示。

在随机写读情况下，该项目每秒可处理啊请求数（QPS）: 24.39w，每秒可处理读请求数（QPS）: 18.41w

# 项目中文件

* main.cpp 包含skiplist.h使用跳表进行数据操作
* skiplist.h 跳表核心实现
* bin 生成可执行文件目录 
* makefile 编译脚本
* store 数据持久化文件夹
* stress_test_start.sh 压力测试脚本

# 提供接口

* insertElement（插入数据）
* deleteElement（删除数据）
* searchElement（查询数据）
* display_from_k1_to_k2  (查询从k1到k2的数据)
* displayList（展示已存数据）
* dumpFile（数据落盘）
* loadFile（加载数据）
* size（返回数据规模）


# 存储引擎数据表现

## 插入操作

跳表树高：18 


每秒可处理写请求数（QPS）: 24.39w

## 取数据操作

每秒可处理读请求数（QPS）: 18.41w

# 项目运行方式

```
make            // complie demo main.cpp
./bin/main      // run 
```

可以运行如下脚本测试kv存储引擎的性能（当然你可以根据自己的需求进行修改）

```
sh stress_test_start.sh 
```

# 待优化 

* 加入分布式协议变成分布式存储
