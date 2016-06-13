title: elasticsearch集群搭建和压测
date: 2015-11-23 10:03:55
tags: elasticsearch
---

先把压测结果发出来,以后再补搭建流程

## 相关配置信息
### 虚机
cpu:2 core

memory:4g

### elasticsearch
version: 1.7

jvm: -Xms1g -Xmx2g -XX:MaxPermSize=512m

shards(主分片): 5

replicas(从分片): 1 (比例)

## 创建索引
### 执行命令
请求量100W 并发1000

ab -n 1000000 -c1000 -p abtest http://172.31.14.244:9200/group/group

### 结果
qps: 3357.64 s

tps: 297.828 ms

cpu: 75%

load average: 4

## 搜索
100W条数据中查询并命中10条
### 执行
请求量100W 并发100

ab -n 1000000 -c 100 http://172.31.14.244:9200/group/_search?q=description:呵呵
### 结果
qps: 2727.95 s

tps: 36.658 ms

cpu: 50%

load average: 4

GC数据: 

### 执行
请求量100W 并发500

ab -n 1000000 -c 500 http://172.31.14.244:9200/group/_search?q=description:呵呵
### 结果
qps: 2727.95 s

tps: 184.812 ms

cpu: 50%

load average: 4

GC数据: 







