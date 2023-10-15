## MongoDB

MongoDB是最像关系型数据库的非关系型数据库，它以高性能、高存储、高可用性著称。

### MongoDB 查询操作

MongoDB 支持丰富的查询操作：

- **查询所有数据**: `db.collection.find()`
- **条件查询**: `db.collection.find({ key: value })`
- **范围查询**: `db.collection.find({ key: { $gte: value1, $lte: value2 } })`
- **AND 查询**: `db.collection.find({ key1: value1, key2: value2 })`
- **OR 查询**: `db.collection.find({ $or: [{ key1: value1 }, { key2: value2 }] })`
- **更新数据**: `db.collection.updateOne({ key: value }, { $set: { newKey: newValue } })`
- **删除数据**: `db.collection.deleteOne({ key: value })`

### 索引

#### 1. 单字段索引

单字段索引是在一个字段上创建的索引。示例：

```
javascriptCopy code
db.collection.createIndex({ field: 1 });
```

**查询使用单字段索引：**

```
javascriptCopy code
db.collection.find({ field: value });
```

#### 2. 复合索引

复合索引是在多个字段上创建的索引。它可以用于优化基于多个字段的查询。示例：

```
javascriptCopy code
db.collection.createIndex({ field1: 1, field2: -1 });
```

**查询使用复合索引：**

```
javascriptCopy code
db.collection.find({ field1: value1, field2: value2 });
```

#### 3. 多键索引

多键索引允许一个字段包含多个值，这些值将被索引。示例：

```
javascriptCopy code
db.collection.createIndex({ tags: 1 });
```

**查询使用多键索引：**

```
javascriptCopy code
db.collection.find({ tags: "tag_value" });
```

### 副本集 

MongoDB 中用于提供高可用性和数据冗余的机制。副本集由多个 MongoDB 实例组成，其中一个是主节点，其他是从节点。主节点负责处理所有写操作，从节点负责复制主节点的数据。如果主节点失效，系统会自动选择一个从节点作为新的主节点。

### 分片 

用于处理大规模数据和提高系统性能的方法。通过将数据划分为多个分片，MongoDB可以在多个服务器上分布数据。

#### 分片策略

MongoDB 支持多种分片策略，常见的有三种：

1. **范围分片**：将数据按照分片键的范围进行划分，每个分片负责一定范围的值。
2. **哈希分片**：对分片键进行哈希运算，根据哈希值的范围将数据分配给不同的分片。这样可以确保数据分布更加均匀。
3. **自定义分片**：允许用户自定义数据如何分布到分片上，可以根据业务需求自由划分。