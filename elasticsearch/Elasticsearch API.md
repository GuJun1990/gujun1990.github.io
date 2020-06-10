# Elasticsearch API分析

## 1. 文档API

### 1.1 Index API

```java
IndexRequest request = new IndexRequest("index", "type", "docId");
String json = ""; // JSON类型的文档
request.source(json, XContentType.JSON);
```

### 1.2 Get API

```java
GetRequest request = new GetRequest("index", "type", "docId");
```

### 1.3 Delete API

```java
DeleteRequest request = new DeleteRequest("index", "type", "docId");
```

### 1.4 Update API

```java
UpdateRequest request = new UpdateRequest("index", "type", "docId");
String json = ""; // 需要更新的字段
request.doc(json, XContentType.JSON);
```

### 1.5 Multi-Get API

```java

```

### 1.6 Buik API

```java

```

## 2. 搜索API



