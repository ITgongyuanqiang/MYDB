# SampleDB
一个简单的数据库实现
SampleDB 是一个 Java 实现的简单的数据库，部分原理参照自 MySQL、PostgreSQL 和 SQLite。实现了以下功能：

- 数据的可靠性和数据恢复
- 两段锁协议（2PL）实现可串行化调度
- MVCC
- 两种事务隔离级别（读提交和可重复读）
- 死锁处理
- 简单的表和字段管理
- 简单的 SQL 解析
- 基于 socket 的 server 和 client

## 运行方式
注意首先需要在 pom.xml 中调整编译版本，如果导入 IDE，请更改项目的编译版本以适应你的 JDK

首先执行以下命令编译源码:(在这个目录下启动终端 F:\JAVA\sourceCode\SampleDB-master)

```
mvn compile
```

接着执行以下命令以 /tmp/mydb 作为路径创建数据库：

```
mvn exec:java -Dexec.mainClass="top.gongyuanqiang.sampledb.backend.Launcher" -Dexec.args="-create F:\JAVA\tmp\mydb"
```

随后通过以下命令以默认参数启动数据库服务：

```
mvn exec:java -Dexec.mainClass="top.gongyuanqiang.sampledb.backend.Launcher" -Dexec.args="-open F:\JAVA\tmp\mydb"
```

这个时候数据库服务就已经启动在本机的9999端口。重新启动一个终端(在这个目录下启动终端 F:\JAVA\sourceCode\SampleDB-master)，执行以下指令启动客户端连接数据库：

```
mvn exec:java -Dexec.mainClass="top.gongyuanqiang.mydb.client.Launcher"
```

会启动一个交互方式指令行，就可以在这里输入类SQL语句，回车会发送语句语句到服务，并输出执行的结果。

![SampleDB](https://camo.githubusercontent.com/dfe61eb3da416015d692c39e2d696b58393f4afde36126a4c1cf928347518645/68747470733a2f2f73332e626d702e6f76682f696d67732f323032312f31312f323734393930363837303237363930342e706e67 "简单数据库")
