# Redis

redis是nosql，相较于之前学习的mysql，它是非结构化，无关联，事务特性呈base的。

### 安装Redis

安装了redis命令行客户端并设置了开机自启，安装了图形化界面客户端。

### Redis通用命令

Redis通用命令包括：

- `DEL`: 删除指定的key
- `EXISTS`: 检查key是否存在
- `KEYS`: 列出所有符合给定模式的key
- `RENAME`: 重命名key
- `TYPE`: 返回key存储的值的类型

### 数据类型及命令示例

1. **String**
   - *语法*: `SET key value`
   - *示例*:
     - 设置值: `SET mykey "Hello"`
     - 获取值: `GET mykey`

2. **Hash**
   - *语法*:
     - 设置单个字段: `HSET key field value`
     - 获取单个字段值: `HGET key field`
   - *示例*:
     - 设置字段值: `HSET user:id name "John"`
     - 获取字段值: `HGET user:id name`

3. **List**
   - *语法*:
     - 从左边插入元素: `LPUSH key value1 [value2 ...]`
     - 从右边插入元素: `RPUSH key value1 [value2 ...]`
     - 获取指定范围的元素: `LRANGE key start stop`
   - *示例*:
     - 插入元素: `LPUSH mylist "a" "b" "c"`
     - 获取范围元素: `LRANGE mylist 0 -1`

4. **Set**
   - *语法*:
     - 添加元素: `SADD key member1 [member2 ...]`
     - 获取所有元素: `SMEMBERS key`
   - *示例*:
     - 添加元素: `SADD myset "apple" "banana" "cherry"`
     - 获取所有元素: `SMEMBERS myset`

5. **Sorted Set**
   - *语法*:
     - 添加元素: `ZADD key score1 member1 [score2 member2 ...]`
     - 获取分数范围内的元素: `ZRANGEBYSCORE key min max`
   - *示例*:
     - 添加元素: `ZADD myzset 1 "one" 2 "two" 3 "three"`
     - 获取分数范围内的元素: `ZRANGEBYSCORE myzset 1 2`

### Redis的Key的层级格式

可以将 key 视为文件路径，Redis 使用冒号 `:` 作为分隔符来创建层级结构。

### Redis的Java客户端

当涉及与 Redis 进行 Java 交互时，Jedis 是一个常用的 Java 客户端库。它允许你在 Java 程序中连接到 Redis 服务器并与之交互。

#### 安装 Jedis

在你的 Maven 项目的 `pom.xml` 文件中，添加以下依赖：

```xml
<dependency>
    <groupId>redis.clients</groupId>
    <artifactId>jedis</artifactId>
    <version>3.6.0</version> 
</dependency>

```

#### 使用 Jedis

```java
import redis.clients.jedis.Jedis;

public class JedisExample {
    public static void main(String[] args) {
        // 创建 Jedis 实例，连接到本地 Redis 服务器
        Jedis jedis = new Jedis("localhost");

        // 检查是否连接成功
        System.out.println("Server is running: " + jedis.ping());
        
        jedis.close();
    }
}
```

在程序结束时关闭 Jedis 连接来释放资源。