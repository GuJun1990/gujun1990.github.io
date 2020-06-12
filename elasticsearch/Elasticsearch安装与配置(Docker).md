# Elasticsearch安装与配置-Docker版本

## 1. 拉取指定版本的ES镜像

```shell
docker pull docker.elastic.co/elasticsearch/elasticsearch:6.0.1
```

## 2. 启动ES容器

```shell
docker run -d --name es-6.0.1 -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e "xpack.security.enabled=false" docker.elastic.co/elasticsearch/elasticsearch:6.0.1
```

注：

	1. 9200作为Http协议，主要用于外部通讯；
 2. 9300作为Tcp协议，主要用于集群各个节点之间通讯。

## 3. 查看ES容器是否启动成功，

浏览器输入`http://localhost:9200`

## 4. 安装IK分词器

1. 进入ES容器`docker exec -it es-6.0.1 /bin/bash`
2. 执行安装插件命令 `./bin/elasticsearch-plugin install https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v6.0.1/elasticsearch-analysis-ik-6.0.1.zip`

## 5. 设置自定义词典

1. 进入ES容器`docker exec -it es-6.0.1 /bin/bash`
2. 编辑`config/analysis-ik/IKAnalyzer.cfg.xml`文件，其中`<entry key="ext_dict">"自定义词典文件名"</entry>`

该目录下有许多文件，含义如下：

1. main.dic： IK原生内置的中文字库，里面有N多条现成的词语；
2. quantifier.dic： 量词和单位名称，如个，斤，克，米之类；
3. suffix.dic：常见后缀词，如江，村，省，市，局等；
4. surname.dic： 中国姓氏；
5. stopword.dic： 停用词，默认是几个英文单词，如and,a,the等。这类词分词时直接被干掉；
6. preposition.dic： 副词，语气助词等没有实际含义的词语，如却，也，是，否则之类

## 6. 设置同义词

同义词组件是ES自带的，不需要额外安装插件，但是要想让同义词和IK一起使用，就需要配置自己的分析器。

1. 进入ES容器`docker exec -it es-6.0.1 /bin/bash`
2. 创建同义词字典`mkdir config/analysis && vi config/analysis/synonym.dic`



















