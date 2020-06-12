# Elasticsearch RESTful API

## 1. 查询DSL

Elasticsearch提供了基于JSON完整的查询DSL（Domain Specific Language，特定领域语言）来定义查询。将查询的DSL视为查询的AST（Abstract Syntax Tree，抽象语法树），它由两种子句组成：

**叶子查询子句**

​		叶子查询子句在特定字段中查找特定值，例如`match`，`term`或`range`查询。这些查询可以自己使用。

**复合查询子句**

​		复合查询子句包装叶子查询或其他复合查询，并用于以逻辑方式组合多个查询（例如`bool`或`dis_max`查询），或更改其行为（例如`constant_score`查询）。

查询子句在`查询上下文`和`过滤上下文`中的查询行为是不同的。

### 1.1 复合查询

**bool query**

**boosting query**

**constant_score query**

**dis_max query**

**function_score query**

​		