# 2. 部署第一个隐私计算网络

标签: ``搭建隐私计算网络``

----

本章介绍搭建隐私计算网络的必要安装和配置。通过在单机上部署一个2机构的WeDPR隐私计算网络，帮助用户掌握WeDPR隐私计算平台的部署流程，请参考(系统和硬件要求)[./hardware_requirements.md]使用支持的硬件和平台错左。

## 2.1 部署前置依赖

WeDPR隐私计算平台搭建前，需准备好[MYSQL](https://hub.docker.com/_/mysql), [HDFS](https://github.com/apache/hadoop/tree/trunk)和[FISCO BCOS v3.0]((https://fisco-bcos-doc.readthedocs.io/zh-cn/latest/index.html))区块链系统环境，

```eval_rst
.. note::
   - MySQL可选用Docker安装方式
   - HDFS的详细搭建流程参考 `这里 <https://hadoop.apache.org/docs/r1.0.4/cn/cluster_setup.html>`_ 
   - FISCO BCOS v3.0区块链网络搭建指南请参考 `这里 <https://fisco-bcos-doc.readthedocs.io/zh-cn/latest/docs/quick_start/air_installation.html>`_
```

这里以安装单机版本的MySQL、HDFS、FISCO-BCOS区块链系统为例，简单介绍前置依赖搭建步骤。

### 2.1.1 安装依赖

**安装macos依赖**

```bash
brew install openssl@1.1 curl wget
```

**安装ubuntu依赖**

```bash
sudo apt install -y curl openssl wget default-jdk
```

**安装centos依赖**

```bash
sudo yum install -y curl openssl openssl-devel wget java-1.8.0-openjdk
```

### 2.1.2 部署MYSQL

```eval_rst
.. note::
   这里使用Docker搭建MySQL环境，请确保您的机器搭建了Docker环境。
```

```bash
# 拉取mysql镜像
docker pull mysql:8

# 启动mysql镜像
# Note: 
# 1. 生产环境可根据实际需求挂载配置、数据目录
# 2. MYSQL_ROOT_PASSWORD参数指定了mysql密码，需根据实际安全需求设置
docker run -p 3306:3306 --name wedpr_mysql -e MYSQL_ROOT_PASSWORD=WeDPR2024 -d mysql
```

### 2.1.3 部署HDFS

```eval_rst
.. note::
   - HDFS更详细的搭建步骤可参考 `这里 <https://www.alibabacloud.com/help/zh/ecs/use-cases/build-a-hadoop-environment>`_ 
   - 安装HDFS需要有root权限
```
**步骤一：获取hadoop安装包**

```bash
# 下载v3.3.6版本的hadoop安装包
wget https://mirrors.bfsu.edu.cn/apache/hadoop/common/hadoop-3.3.6/hadoop-3.3.6.tar.gz

# 将hadoop安装解压到/opt/hadoop
sudo tar -zxvf hadoop-3.3.6.tar.gz -C /opt/
sudo mv /opt/hadoop-3.3.6 /opt/hadoop
```

**步骤二：配置hadoop环境**

```bash
sudo sh -c "echo 'export HADOOP_HOME=/opt/hadoop' >> /etc/profile"
sudo sh -c "echo 'export PATH=\$PATH:/opt/hadoop/bin' >> /etc/profile"
sudo sh -c "echo 'export PATH=\$PATH:/opt/hadoop/sbin' >> /etc/profile"
source /etc/profile
```

**步骤三：配置hadoop使用的Java环境**

```bash
# 获取java路径
$ which java
# 输出: /usr/bin/java，说明java_home是/user

# 配置JAVA_HOME(这里的路径请根据which java输出的java二进制所在目录调整)
sudo sh -c 'echo "export JAVA_HOME=/usr" >> /opt/hadoop/etc/hadoop/yarn-env.sh'
sudo sh -c 'echo "export JAVA_HOME=/usr" >> /opt/hadoop/etc/hadoop/hadoop-env.sh'

# 检查hadoop是否安装成功, 若安装成功会有对应的版本信息输出
hadoop version
# 输出如下信息表明hadoop安装成功
Hadoop 3.3.6
Source code repository https://github.com/apache/hadoop.git -r 1be78238728da9266a4f88195058f08fd012bf9c
Compiled by ubuntu on 2023-06-18T08:22Z
Compiled on platform linux-x86_64
Compiled with protoc 3.7.1
From source with checksum 5652179ad55f76cb287d9c633bb53bbd
This command was run using /usr/local/hadoop/share/hadoop/common/hadoop-common-3.3.6.jar
```

**步骤四：配置hadoop**




### 2.1.4 部署区块链系统


### 2.2 
