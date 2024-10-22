# ElasticSearch

### 엘라스틱서치(Elasticsearch) 기본 개념&#x20;

#### Elasticsearch 기본 개념&#x20;

* &#x20;Near Realtime&#x20;
* Cluster : 전체 데이터를 함께 보유하고 모든 노드에서 연합 인덱싱 및 검색 기능을 제공하는 하나 이상의 노드 모음&#x20;
* Node : 클러스터의 일부이며 데이터를 저장하고 클러스터의 인덱싱 및 검색 기능에 참여하는 단일 서버&#x20;
* Index : 다소 유사한 특성을 갖는 문서들의 집합&#x20;
* Type : Index 내에서 하나 이상의 Type을 정의&#x20;
* Document : Index를 생성 할 수 있는 기본 정보 단위, JSON표현&#x20;
* Shards : shards를 이용하여 Index를 여러 조각으로 분할 가능, 기본 4개 제공&#x20;
* Replication : 장애가 발생할 경우 고가용성을 제공, 기본 1개 제공&#x20;

#### 관계형 데이터베이스와 Elasticsearch 용어 비교&#x20;

<table><thead><tr><th>관계형 데이터베이스</th><th>Elasticsearch </th><th data-hidden></th></tr></thead><tbody><tr><td>Database</td><td>Index </td><td></td></tr><tr><td>Table</td><td>Type</td><td></td></tr><tr><td>Row</td><td>Document </td><td></td></tr><tr><td>Column</td><td>Field </td><td></td></tr><tr><td>Schema</td><td>Mapping </td><td></td></tr><tr><td>Index</td><td>Everything is indexed </td><td></td></tr><tr><td>SQL</td><td>Query DSL</td><td></td></tr></tbody></table>

### &#x20;엘라스틱서치(Elasticsearch) 구성도

#### 아키텍처

<figure><img src=".gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

#### 개념적 구성도

<figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

#### REST API 기본 구조&#x20;

* Elasticsearch는 REST (Representational State Transfer) API를 제공하여 다양한 환경에서 사용 가능&#x20;
* REST에서 Methods의 주요 용도
  * POST : 등록 (Create)
  * PUT : 수정 (Replace), 데이터가 없을 경우에는 등록 (Create)
  * DELETE : 삭제 (Delete)
  * GET : 조회 (List, Retrieve)



### REST API

#### URI 기본형태

* http://localhost:9200/index/type/id?parameters&#x20;
* http://localhost:9200/\[index/\[type/]action?parameters]&#x20;
  * index : DBMS에서 데이터베이스에 해당&#x20;
  * type : DBMS에서 테이블에 해당&#x20;
  * id : DBMS에서 레코드에 해당하는 Document의 ID&#x20;
  * index, type, id를 여러 개 지정할 경우 ","를 사용하여 구분 "\*"를 사용하여 모두 지정 가능
  * action : 특정 작업을 지시
  * 공통 parameters (pretty, v, help, h=컬럼1,컬럼2, bytes=b)

#### Action

<table><thead><tr><th width="155">Action</th><th>Description</th></tr></thead><tbody><tr><td>_cluster</td><td>클러스터 관련 작업</td></tr><tr><td>_nodes</td><td>노드 관련 작업</td></tr><tr><td>_aliases</td><td>Index alias 관련 작업</td></tr><tr><td>_analyze</td><td>analyzer 관련 작업</td></tr><tr><td>_cache</td><td>Cache 관련 작업</td></tr><tr><td>_flush</td><td>Transaction log 또는 Memory free 작업</td></tr><tr><td>_optimize</td><td>Segment 파일 병합 작업</td></tr><tr><td>_stats</td><td>시스템 또는 색인의 통계 정보</td></tr><tr><td>_search</td><td>검색 작업</td></tr><tr><td>_msearch</td><td>Multi 검색 작업</td></tr><tr><td>_mget</td><td>Multi Document patch 작업</td></tr><tr><td>_validate</td><td>Query에 대한 유효성 검사 작업</td></tr><tr><td>_suggest</td><td>검색어 자동 완성</td></tr><tr><td>_bulk</td><td>Bulk 색인 작업</td></tr><tr><td>_count</td><td>문서 count 작업</td></tr><tr><td>_settings</td><td><p>elasticsearch.yml에 설정한 global settings 정보 조회<br><code>http://localhost:9200/index/_settings?pretty=true</code><br><strong>number_of_shards</strong>: Shard 개수</p><p><strong>number_of_replicas</strong>: Replica 개수</p><p><strong>index.refresh_interval</strong>: Index 변경 후 검색 결과에 반영되는 시간 설정</p><p><strong>analysis</strong>: analyzer와 tokenizer 설정</p><p><strong>store</strong>: 저장 옵션</p></td></tr></tbody></table>

#### Mapping

<table><thead><tr><th width="196">Attribute</th><th width="169">Default Value</th><th>Description</th></tr></thead><tbody><tr><td>store</td><td>no</td><td>원본 저장 여부</td></tr><tr><td>index</td><td>analyzed</td><td>색인 방식 지정 (options: no, not_analyzed, analyzed)</td></tr><tr><td>term_vector</td><td>no</td><td>색인어에 대한 메타 정보 저장 방식 (options: yes, no, with_offsets, with_positions, with_positions_offsets)</td></tr><tr><td>boost</td><td>1.0</td><td>Boost 값</td></tr><tr><td>null_value</td><td></td><td>필드의 값이 null일 경우의 default 값</td></tr><tr><td>omit_norms</td><td>true</td><td>Lucene의 norms 사용 여부</td></tr><tr><td>index_options</td><td>positions</td><td>색인 시 저장할 메타 정보 설정 (options: positions, docs)</td></tr><tr><td>analyzer</td><td></td><td>색인 및 검색 시 사용할 Global analyzer</td></tr><tr><td>index_analyzer</td><td></td><td>색인 시 사용할 analyzer</td></tr><tr><td>search_analyzer</td><td></td><td>검색 시 사용할 analyzer</td></tr><tr><td>include_in_all</td><td>true</td><td>_all 필드에 검색 가능한 모든 필드를 포함할지 여부</td></tr><tr><td>ignore_above</td><td></td><td>문자열 필드에서 정해진 크기를 넘는 문자는 무시하도록 설정</td></tr><tr><td>position_offset_gap</td><td></td><td>Phrase 검색에서 전후 텍스트 간의 간격 설정</td></tr><tr><td>precision_step</td><td></td><td>최대 number_term 설정</td></tr><tr><td>ignore_malformed</td><td>false</td><td>잘못된 number, date 무시 여부</td></tr><tr><td>format</td><td>dateOptionalTime</td><td>Date format</td></tr></tbody></table>

#### REST API 등록/수정/삭제/조회

<table><thead><tr><th width="186">Operation</th><th>Description &#x26; Command Example</th></tr></thead><tbody><tr><td>등록 (POST/PUT)</td><td><strong>customer 인덱스 생성</strong><br>curl -XPUT 'node201.hadoop.com:9200/customer?pretty'<br>curl -GET 'node201.hadoop.com:9200/_cat/indices?v'</td></tr><tr><td>등록 (POST)</td><td><strong>External 타입으로 문서 추가 (문서 번호 자동 생성)</strong><br>curl -XPOST 'node201.hadoop.com:9200/customer/external?pretty' -d '{ "name": "Mountain Lover" }'<br>curl -XGET 'node201.hadoop.com:9200/customer/external/1lz2jL6CQui07FnZGd_R9w?pretty'</td></tr><tr><td>등록 (PUT)</td><td><strong>External 타입으로 1번 문서 추가</strong><br>curl -XPUT 'node201.hadoop.com:9200/customer/external/1?pretty' -d '{ "name": "Mountain Lover" }'<br>curl -XGET 'node201.hadoop.com:9200/customer/external/1?pretty'</td></tr><tr><td>수정 (POST)</td><td><strong>External 타입으로 1번 문서 수정</strong><br>curl -XPOST 'node201.hadoop.com:9200/customer/external/1/_update?pretty' -d '{ "doc": { "name": "Mountain Lover!", "age": 20 } }'<br>curl -XGET 'node201.hadoop.com:9200/customer/external/1?pretty'</td></tr><tr><td>수정 (PUT)</td><td><strong>External 타입으로 1번 문서 수정</strong><br>curl -XPUT 'node201.hadoop.com:9200/customer/external/1?pretty' -d '{ "name": "Mountain Lover!" }'<br>curl -XGET 'node201.hadoop.com:9200/customer/external/1?pretty'</td></tr><tr><td>삭제 (DELETE)</td><td><strong>문서 삭제</strong><br>curl -XDELETE 'node201.hadoop.com:9200/customer/external/1?pretty'<br>curl -XGET 'node201.hadoop.com:9200/customer/external/1?pretty'<br>curl -XDELETE 'node201.hadoop.com:9200/customer/external/_query?pretty' -d '{ "query": { "match": { "name": "Mountain Lover!" } } }'<br>curl -XGET 'node201.hadoop.com:9200/customer/external/1?pretty'</td></tr><tr><td>삭제 (DELETE)</td><td><strong>customer 인덱스 삭제</strong><br>curl -XDELETE 'node201.hadoop.com:9200/customer?pretty'<br>curl -GET 'node201.hadoop.com:9200/_cat/indices?v'</td></tr><tr><td>조회 (GET)</td><td><strong>조회</strong><br>curl -GET 'node201.hadoop.com:9200/_cat/indices?v'<br>curl -XGET 'node201.hadoop.com:9200/customer/external/1?pretty'</td></tr><tr><td></td><td><p><strong>조회되는 데이터 구조</strong><br>_index,</p><p>_type, </p><p>_id, </p><p>_version : 1, 2, 3, ..., </p><p>_source : { name1: value1, name2: value2 }</p></td></tr><tr><td>검색 (GET)</td><td><strong>REST request URI 검색</strong><br><code>curl -XGET 'node201.hadoop.com:9200/customer/_search?q=*&#x26;pretty'</code></td></tr><tr><td>검색 (POST)</td><td><strong>REST request body 검색</strong><br><code>curl -XPOST 'node201.hadoop.com:9200/customer/_search?pretty' -d '{ "query": { "match_all": {} } }'</code></td></tr></tbody></table>

#### Document API&#x20;

* index api : -XPUT : 등록, -XPOST : 등록 (id 자동 생성)&#x20;
* get api : -XGET&#x20;
* delete api : -XDELETE&#x20;
* update api : -XPUT&#x20;
* multi get api : -XGET, /\_mget

#### Search API

* q : Query String Query&#x20;
* analyzer&#x20;
* default\_operator : OR (default), AND&#x20;
* \_source = false, \_source\_include, \_source\_exclude&#x20;
* &#x20;df : 디폴트 필드 지정&#x20;
* fields : 필드 지정&#x20;
* sort : field:asc, field:desc

Basic API – Index 관리

* curl -X GET http://node201.hadoop.com:9200/\_status #--- 상태 확인&#x20;
* curl -X POST http://node201.hadoop.com:9200/index001 #--- index 생성
* curl -X DELETE http://node201.hadoop.com:9200/index001 #--- index 삭제&#x20;
* curl -X GET http://node201.hadoop.com:9200/index001/\_mapping #--- Mapping 조회&#x20;
* curl -X GET http://node201.hadoop.com:9200/index001/\_status #--- 상태 확인&#x20;
* curl -X GET http://node201.hadoop.com:9200/index001/\_search #--- 검색&#x20;
* curl -X GET http://node201.hadoop.com:9200/\_all/\_search #--- 검색
* curl -X POST http://node201.hadoop.com:9200/index001/type001 -d '{ title: "Greeting", body: "Hello World!" }'&#x20;
* curl -X DELETE http://node201.hadoop.com:9200/index001/type001 #--- type 삭제&#x20;
* curl -X GET http://node201.hadoop.com:9200/index001/type001/\_mapping #--- Mapping 조회&#x20;
* curl -X GET http://node201.hadoop.com:9200/index001/type001/\_status #--상태 확인&#x20;
* curl -X GET http://node201.hadoop.com:9200/index001/type001/\_search #--검색&#x20;
* http://node201.hadoop.com:9200/index001/type001/\_search?q=title:Gre\*ting

Basic API – Mapping 관리

```bash
#--- Mapping 생성
curl -X PUT http://node201.hadoop.com:9200/index001/type001/_mapping -d '{
type001: {
    properties: {
        title: {
            type: "string",
            index: "not_analyzed"
        } …..
curl -X GET http://node201.hadoop.com:9200/index001/type001/_mapping #---
Mapping 조회
```

Basic API – Document 관리 (레코드)

```bash
curl -X POST http://node201.hadoop.com:9200/index001/type001/data001 -d '{ title:
"Greeting", body: "Hello World!" }'
curl -X POST http://node201.hadoop.com:9200/index001/type001/data001/_update -
d '{ title: "Greeting", body: "Hello World!" }'
curl -X DELETE http://node201.hadoop.com:9200/index001/type001/data001 #---
data001 데이터 삭제
curl -X GET http://node201.hadoop.com:9200/index001/type001/data001 #---
data001 데이터 조회
curl -X GET http://node201.hadoop.com:9200/index001/type001/_search -d '{query:
{text: {_all: "Hello"}}}‘#--- document 검색
```

#### Bulk API

```bash
# Bulk로 문서 등록, 수정, 삭제 
curl -XPOST 'node201.hadoop.com:9200/customer/external/_bulk?pretty' -d ' 
{"index":{"_id":"1"}}
{"name": "John Doe" } 
{"index":{"_id":"2"}} 
{"name": "Jane Doe" }
```

### Summary Note

* 엘라스틱서치는 클러스터, 노드, 인덱스, 샤드와 같은 기본 개념이 있다.
* 클러스터는 일반적으로 여러개의 노드로 구성되어 있고, 노드 내부에는 일반적으로 인덱스가 있다.
* 인덱스 내부에는 여러개의 샤드로 쪼개진 데이터들이 있으며, 샤드 내부에는 문서가 있고, 문서는 필드와 매핑(Mapping)을 갖고 있다.
* 자원별로 고유 URL로 접근이 가능해며 http 메서드, PUT, POST, GET, DELETE를 이용하여 자원을 처리한다.
