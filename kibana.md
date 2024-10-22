# Kibana

### Kibana 모니터링&#x20;

#### 시각화 플랫폼 개요&#x20;

* &#x20;Kibana는 Elasticsearch와 함께 사용하도록 설계된 오픈소스 분석 및 시각화 플랫폼&#x20;
* Kibana를 사용하여 Elasticsearch 색인에 저장된 데이터를 검색하고 확인하는 상호 작용을 수행 가능&#x20;
* 손쉽게 고급 데이터 분석을 수행하고 다양한 차트, 테이블, 지도의 형태로 데이터를 시각화&#x20;
* 간단한 브라우저 기반 인터페이스에서 Elasticsearch 쿼리의 변경 사항을 실시간으로 표시하는 동적 대시보드를 신속하게 생성하고 공유 가능&#x20;
* Kibana에서 모든 사용자 인터페이스 행위가 발생
* Elasticsearch가 분석 및 처리를 하고 Kibana는 이를 렌더링하는 <mark style="color:red;">**웹 애플리케이션**</mark>&#x20;
* Kibana는 Elasticsearch 집계에 시각적 능력을 부여해서 시계열 데이터 집합이나 데이터 필드 일부분을 쉽게 원형 차트 생성&#x20;
* Kibana는 색인된 도큐먼트를 파헤치면서 데이터를 발굴&#x20;
* 대시보드에서 다양한 시각화를 작성하면서 분석 경험&#x20;
* Kibana가 데이터를 분석할 뿐만 아니라 Elastic Stack을 모니터링하고, Document 간 관계를 만들고, Metric 분석&#x20;
* Kibana 핵심 기능: Discover, Visualize, Dashboard, Console&#x20;
* Kibana 플러그인: Timelion, Graph, Monitoring, elastic, Logout&#x20;

#### Elastic Stack 한눈에 보기&#x20;

* Elasticsearch, Kibana, Beats, Logstash의 성능 모니터링

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

#### 알림 기능을 통한 클러스터 위험 방지

* 강력한 알림 기능을 통해 클러스터의 상태와 라이센스 만료 여부, 기타 다양한 Elasticsearch, Kibana, Logstash 메트릭들의 변화에 대한 알림을 자동 수신

<figure><img src=".gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

#### 색인 패턴&#x20;

* 사용자가 아직 데이터를 갖고 있지 않다면, CSV Importer를 사용해 입력 가능&#x20;
* Elastic Search에 데이터가 이미 있다면, 사용자는 색인 패턴 생성 필요
* 색인 패턴의 개념이 실제 색인 구조 위에 메타 구조를 기술&#x20;
* Kibana가 데이터 계층을 추상화하는 용도로만 사용&#x20;
* Kibana는 데이터 계층에 영향을 주지않고 시각화 계층에서만 사용자 지정을 허용

### Kibana Discover&#x20;

#### 데이터 검색&#x20;

* Kibana 데이터 탐색/검색 기능을 표시하려면 사이드 탐색 메뉴에서 검색 을 클릭&#x20;

<div align="center" data-full-width="false">

<figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

</div>

* Discover 섹션은 Elasticsearch에서 어떤 데이터를 색인하면 데이터를 탐색하기 위해 가장 먼저 확인하게 되는 메뉴
* 시간에 따른 이벤트 개수(날짜 히스토그램 형태)&#x20;
* 색인된 도큐먼트 및 단일 항목을 확장하면 도큐먼트 상세 가능&#x20;
* 선택한 Index Pattern 과 일치하는 Time Picker 기간 내의 모든 데이터를 조회 가능&#x20;
* Query bar를 통한 검색과 'Add a Filter' 를 통해 데이터를 필터링 가능
* &#x20;조회된 데이터는 Histogram과 Document Table에서 확인 가능



#### 데이터 시각화

* 데이터 시각화를 시작하려면 탐색 메뉴에서 시각화(Visualize)를 클릭&#x20;

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

#### 대시보드로 통합&#x20;

* 대시보드는 사용자가 배치하고 공유할 수 있는 여러 시각화의 모음

<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### Summary Note

* Kibana는 Elasticsearch와 함께 사용하도록 설계된 오픈 소스분석 및 시각화 플랫폼이다.
* Kibana를 사용하여 Elasticsearch 색인에 저장된 데이터를 검색하고 확인하는 상호 작용을 수행 가능하다.
* Kibana는 Elasticsearch집계에 시각적 능력을 부여해서 시계열 데이터 집합이나 데이터 필드 일부분을 쉽게 원형 차트 생성 가능하다.
* 강력한 알림 기능을 통해 클러스터의 상태와 라이센스 만료여부, 기타 다양한 Elasticsearch, kibana, logstash메트릭들의 변화에 대한 알림을 자동 수신이 가능하다.
* Kibana Discover 섹션은 Elasticsearch에서 어떤 데이터를 색인하면 데이터를 탐색하기 위해 가장 먼저확인하게 되는 메뉴이다.
* 데이터 시각화를 시작하려면 탐색 메뉴에서 시각화(Visualize)를 메뉴를 활용한다.
* 대시보다는 사용자가 배치하고 공유할 수 있는 여러 시각화의 모음이다.
