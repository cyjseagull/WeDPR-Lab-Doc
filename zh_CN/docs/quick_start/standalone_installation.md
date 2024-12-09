# 2. 部署第一个隐私计算网络

标签: ``搭建隐私计算网络``

----

本章介绍搭建隐私计算网络的必要安装和配置。通过在单机上部署一个2机构的WeDPR隐私计算网络，帮助用户掌握WeDPR隐私计算平台的部署流程，请参考(系统和硬件要求)[./hardware_requirements.md]使用支持的硬件和平台错左。

## 2.1 部署前置依赖

WeDPR隐私计算平台搭建前，需准备好[MYSQL](https://hub.docker.com/_/mysql), [HDFS](https://github.com/apache/hadoop/tree/trunk)和[FISCO BCOS v3.0]((https://fisco-bcos-doc.readthedocs.io/zh-cn/latest/index.html))区块链系统环境。
前置依赖的搭建可参考[依赖安装](../op/pre_installation.md).


## 2.2 下载部署脚本

```bash
# 创建操作目录
mkdir -p /data/home/wedpr
cd /data/home/wedpr

# 下载并解压环境部署脚本wedpr-builder
curl -#LO https://github.com/WeBankBlockchain/WeDPR/releases/download/v3.0.0/wedpr-builder.tar.gz && tar -xvf wedpr-builder.tar.gz && cd wedpr-builder
```

## 2.3 隐私计算平台部署配置

**步骤一: 拷贝配置模板**

```eval_rst
.. note::
   - 部署脚本的配置详细介绍参考 `这里 <../op/wedpr_builder.html>`_
   - HDFS的详细搭建流程参考 `这里 <https://hadoop.apache.org/docs/r1.0.4/cn/cluster_setup.html>`_ 
   - FISCO BCOS v3.0区块链网络搭建指南请参考 `这里 <https://fisco-bcos-doc.readthedocs.io/zh-cn/latest/docs/quick_start/air_installation.html>`_
```

```bash
conf/config-example.toml config.toml
```


