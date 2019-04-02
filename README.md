# study-nosql

## Not Only Sql

단순히 기존 관계형 DBMS가 갖고있는 특성뿐만 아니라, 다른 특성들을 부가적으로 지원한다는 것을 의미합니다.

이 용어가 처음으로 등장한 것응ㄴ 1998년 카를로 스트로찌(Carlo Strozzi)라는 엔지니어가 공개한 표준 SQL 인터페이스를 채용하지 않은 자신의 경량 Open Source 데이터베이스를 NoSQL이라고 명명한데서 유래했다고 합니다.

이때부터 기존의 관계형 데이터베이스 시스템의 주요 특성을 보장하는 ACID(Atomic, Consistency, Integrity, Duarabity) 특성을 제공하지 않는, 그렇지만 뛰어난 확장성이나 성능 등의 특성을 갖는 수많은 비관계형, 분산 데이터 베이스들이 등장했고 NoSQL이라는 용어가 보편적으로 사용되었습니다. 

NoSQL이 등장한 이후에도 시장에서는 관계형 데이터베이스가 데이터를 처리하는데 가장 최적의 시스템으로 받아들이고 있었습니다. 
특히 기업의 ERP나, MIS 시스템 등 데이터의 정확한 처리가 필수적인 시스템에서는 현재도 관계형 데이터베이스를 사용하고 있습니다. 또한 무엇보다도 SQL 이라고 하는 데이터를 처리하는 언어의 편이성 때문에 NoSQL 등 다른 데이터베이스 시스템들은 많이 활용 되지 않고 있었습니다. 

그러나, 2000년 후반으로 넘어오면서 인터넷이 활성화되고, 소셜네트워크 서비스 등이 등장하면서 관계형 데이터 또는 정형데이터가 아닌 데이터, 즉 비정형데이터라는 것을 보다 쉽게 담아서 저장하고 처리할 수 있는 구조를 가진 데이터 베이스들이 관심을 받게 되었고, 해당 기술이 점점 더 발전하게 되면서, NoSQL 데이터베이스가 각광을 받게 된 것입니다. 
이러한 배경하에서 어떤 엔지니어들은 NoSQL을 Modern web-scale databases라고 정의하기도 합니다. 

NoSQL 데이터베이스의 특징을 살펴보면, 기존의 관계형 데이터베이스 보다 더 융통성 있는 데이터 모델을 사용하고, 데이터의 저장 및 검색을 위한 특화된 매커니즘을 제공합니다. 
이를 통해 NoSQL 데이터베이스는 단순 검색 및 추가 작업에 있어서 매우 최적화된 키 값 저장 기법을 사용하여, 응답속도나, 처리 효율 등에 있어서 매우 뛰어난 성능을 나타냅니다. 이 특징들을 요약해보면 기존 관계형 데이터베이스와 다음과 같은 차이점을 보입니다. 

- 관계형 모델을 사용하지 않으며 테이블간의 조인 기능 없음
- 직접 프로그래밍을 하는 등의 비SQL 인터페이스를 통한 데이터 액세스
- 대부분 여러 대의 데이터베이스 서버를 묶어서(클러스터링) 하나의 데이터베이스를 구성
- 관계형 데이터베이스에서는 지원하는 Data처리 완결성(Transaction ACID 지원) 미보장
- 데이터의 스키마와 속성들을 다양하게 수용 및 동적 정의 (Schema-less)
- 데이터베이스의 중단 없는 서비스와 자동 복구 기능지원
- 다수가 Open Source로 제공
- 확장성, 가용성, 높은 성능 



NoSQL에는 어떤 것들이 있나요?

앞 세션에서 NoSQL의 개념에 대해서 상세하게 알아보았는데, 저장되는 데이터의 구조에(Data Model) 따라 아래와 같이 나누어 볼 수 있습니다. 

- Key Value DB
  Key와 Value의 쌍으로 데이터가 저장되는 가장 단순한 형태의 솔루션으로 Amazon의 Dynamo Paper에서 유래되었습니다. Riak, Vodemort, Tokyo 등의 제품이 많이 알려져 있습니다.
- Wide Columnar Store
  Big Table DB라고도 하며, Google의 BigTable Paper에서 유래되었습니다. Key Value 에서 발전된 형태의 Column Family 데이터 모델을 사용하고 있고, HBase, Cassandra, ScyllaDB 등이 이에 해당합니다.
- Document DB
  Lotus Notes에서 유래되었으며, JSON, XML과 같은 Collection 데이터 모델 구조를 채택하고 있습니다. MongoDB, CoughDB가 이 종류에 해당합니다.
- Graph DB
  Euler & Graph Theory에서 유래한 DB입니다. Nodes, Relationship, Key-Value 데이터 모델을 채용하고 있습니다. Neo4J, OreientDB 
- ![주요 NoSQL제품인 HBase, Cassandra, MongoDB의 일반 특성에 대한 설명입니다. 1. HBase : Master-Slave구조로 구성환경이 복잡하다. HBASE+HDFS+ZOOKEEPER 이 필수 구성이다. 복제의 경우 HDFS를 이용해서 block replication하고, HDFS에서 replication 지정한 개수만큼 쓰기 성공시 완료 처리된다. Sharding의 경우 row key 전체가 sharding key가 되며, range 방식으로 분산하고 hash방식의 분산은 app에서 구현이 필요하다. Hadoop 자체가 저장소이므로 분석용 데이터센터로 연동이 용이하다.  2. Cassandra : Decentralized 구조로 모든 노드가 동등하다. Cassandra 단일구성으로 구성환경이 단순하다. 복제의 경우 Replication factor 수 만큼 shard를 복제한다. consistency level이 ALL인 경우를 제외하고는 consistency level에서 요구되는 수준만 쓰기 성공 시 완료 처리하고 이후 백그라운드 프로세스로 나머지 복제처리를 수행한다. Sharding의 경우  row key의 일부 속성으로 sharding key 지정이 가능하고 Hash 방식 분산을 권고하지만 range방식도 가능하다. Hadoop 연동을 위해 DSE 제품 사용이 요구될 수 있다. 이때 비용이 소요된다. 3. MongoDB : Master-Slave구조이나 구성환경이 단순하다. Sharding 시 Config서버, Mongos서버의 추가 구성이 필요하다. 복제의 경우 Master-Slave 구조로 replication하고, replication 개수 만큼 slave를 생성한다. writeConcern level이 요구하는 수준만 복제 성공시 완료처리되며 이후 백그라운드 프로세스로 나머지 복제처리를 수행한다. Sharding의 경우 row key가 아닌 일반 컬럼을 sharding key로 지정 가능하고, Hash, range 방식 모두 가능하다. Hadoop 연동 Connector를 사용하며 Hbase 보다는 용이하지 않다. ](https://image.samsungsds.com/global/ko/support/insights//08_04.JPG?queryString=20190328051811)등의 제품이 있습니다.

1. MongoDB는 Memory Mapped File 기법에 의해 데이터 처리하기 때문에 최초 메모리 크기는 생성되 는 Namespace와 Data-File에 맞는 적정한 Mapped Area 크기가 요구된다.

(64 Bit, 최초 Namespace 16MB+첫 번째 Data-File 64MB x 2의 가상 메모리 공간)



메모리 맵 파일 : 메모리 맵 파일을 통해 프로세스의 가상 메모리 주소 공간에 파일을 매핑한 뒤 가상 메모 리 주소에 직접 접근하는 것으로 파일 읽기/쓰기를 대신한다.



2. 사용자의 데이터를 위한 Virtual Memory와 함께 MongoDB 서버를 원활하게 운영하기 위한 Resident Area(Working Set)가 요구된다.



이 공간은 서버에 의해 동적으로 할당되며 PageFault가 발생하면 커진다. - Page Fault : 자주 사용되는 데이터를 Page 단위로 메모리에 올려(Workin Set)서 사용하는데, 필요로한 데이터가 Working Set에 없어서 디스 크 IO가 발생하는 것을 Page Fault라고 한다.



3. Mapped File 크기가 2GB인 경우(최대 크기를 기준으로 본다.) 요구되는 RAM 메모리는 약 10GB~12GB 정도가 요구된다. SYSTEM 메모리가 부족한 경운 Page Fault가 발생하여 성능 저하 현상이 발생할 수 있다.



Global/Database/Collection/Page lock 기능

2.2 버전에서의 개선 부분은 2 가지 

- global reader/writer lock 의 제거 – 첫 시도로 database level lock
- PageFaultException 구조 – page fault 시에 Lock 양보.

Promise of 2.8 comes in with **document level locking.** 



##### MongoDB Chunk

Sharding의 가장 큰 목적은 파티셔닝을 통한 데이터 분산 처리와 성능 향상을 위한 Load Balancing이다. 빅 데이터의 효율적 관리와 백업 및 복구 전략 수립을 위한 솔루션이기도 한다.

여러 개의 샤드 서버가 있을 때 하나의 서버에만 데이터가 쌓인다면 쓰기 지연 현상이 발생하는데, 이런 경우를 위해 하나의 서버에 저장되는 데이터들을 여러 개의 논리적 구조로 분할 저장 해 두었다가 일정한 데이터 양 에 도달했을 때 두 번째, 세 번째 서버로 분할 데이터의 일부를 이동 저장하는데 이 분할 단위를 Chunk라고 한다.



Chunk 크기에 따라 다른 서버로 빈번하게 데이터가 전송 될 수도 있고 그렇지 않을 수도 있기 때문에 데 이터의 양에 따라 적절한 튜닝이 필요하다.



**메모리에 저장되는 내용**

메모리에 저장되는 내용은 실제 데이타 블록과, Index 자체가 저장이 된다. mongodb에서 index를 남용하지 말라는 이야기가 있는데, 이는 index를 생성 및 업데이트 하는 데 자원이 들어갈뿐더러, index가 메모리에 상주하고 있어야 제대로 된 성능을 낼 수 있기 때문이기도 하다.



만약에 Physical Memory에 해당 데이타 블록이 없다면, page fault가 발생하게 되고, disk에서 그 데이타 블록을 loading하게 된다. 물론 그 데이타 블록을 loading하기 위해서는 다른 데이타 블록을 disk에 써야 한다.

즉, page fault가 발생하면, page를 memory와 disk 사이에 switching하는 현상이 일어나기 때문에, disk io가 발생하고, 성능 저하를 유발하게 된다.



즉 메모리 용량을 최대한 크게 해서 이 page fault를 예방하라는 이야기이다.

그러나, page fault가 안 발생할 수 는 없고, (1TB 저장하려고, 메모리를 진짜 1TB를 저장할 수 없는 노릇이니...). page fault를 줄이는 전략으로 접근 하는 것이 옳은 방법인데..



page fault시 disk로 write되는 데이타는 LRU 로직에 의해서 결정이 된다. 그래서, 자주 안쓰는 데이타가 disk로 out되는데, 일반적인 application에서 자주 쓰는 데이타 (최근 데이타)의 비율은 그리 크지 않다. 예를 들어 게시판이나 블로그만을 생각해보더라도, 앞의 1~10 페이지 정도가 많이 보게 되지 뒤의 데이타를 잘 안보게 된다. 



이렇게 자주 억세스 되는 데이타를 Hot Data라고 하는데,이 Hot Data 들이 집중되서 메모리에 올라가도록 key 설계를 하는 것이 핵심이다.

쓸떼 없이 전체 데이타를 scan하는 등의 작업을 하게 되면, 100% page fault가 발생하기 때문에, table scan등이 필요한 시나리오는 별도의 index table(summary table)을 만들어서 사용하는 등의 전략이 필요하다.



##### find()


```
db.getCollection('messages').find(
    {
        "create_time" : { "$gte" : new Date( "2019-01-01T00:00:00.000Z")}
    }
)
```


##### findOne()

```
db.bios.findOne(
   { contribs: 'OOP' },
   { _id: 0, 'name.first': 0, birth: 0 }
)
```

##### aggregate()

```
db.getCollection("room_histories").aggregate(
    [
        {
            $match: { room_no : "22001",
                      type : 'I',
                      create_time : {"$gte" : new Date("2018-12-04T00:00+09:00") },
                      update_time : null
                    }
        },
        {
            $group: {
               _id : {
                   room_no:'$room_no'
               },
                count: {
                    '$sum' : 1
                }              
            }
        }
    ]
);
```

##### update()

```
db.people.update(
   { name: "Andy" },
   {
      name: "Andy",
      rating: 1,
      score: 1
   },
   { upsert: true }
)

db.books.update(
   { item: "EFG222" },
   { $set: { reorder: false, tags: [ "literature", "translated" ] } },
   { upsert: true, multi: true }
)
```



##### findOneAndUpdate() → 필터 기준에 따라 도큐먼트 업데이트

```
db.scores.findOneAndUpdate(
   { "name" : "A.B. Abracus" },
   { $set: { "name" : "A.B. Abracus", "assignment" : 5}, $inc : { "points" : 5 } },
   { sort: { "points" : 1 }, upsert:true, returnNewDocument : true }
);
$inc → 값을 증가시키거나 감소
```



##### findAndModify() → 단일 도큐먼트를 수정하고 반환.

```
db.people.findAndModify({
    query: { name: "Andy" },
    sort: { rating: 1 },
    update: { $inc: { score: 1 } },
    upsert: true,
    new: true → 수정된 도큐먼트를 반환
})
```

insert() 단일 또는 다수의 도큐먼트를 입력할 때 사용 

주로 insertOne과 insertMany를 사용 update도 마찬가지

updateOne 또는 

##### insertOne() 단일 도큐먼트 입력 → writeResult 반환

```
db.employee.insertOne(
	{ ename : "김디디", 
	  depart : "디자인팀", 
	  status : "B", 
	  height: 177 
	})
```



```
db.employee.insertMany([                                             { ename : "김디디", depart : "디자인팀", status : "A", height: 157 }                                              , { ename : "송행정", depart : "행팀", status : "B", height: 195 }                                             , { ename : "나법무", depart : "법무팀", status : "C", height: 175}                                             ])

```



1) Collection 생성 : Collection이 존재하지 않으면, Insert 동작이 Collection 을 생성합니다.

2) _id : Collection에 저장된 각 문서에는 Primary key 역할을하는 고유 한 _id 필드가 필요합니다. _id 필드를 생략하면 위와 같이 ObjectId 타입으로 키가 자동으로 생성됩니다.

3) update 를 수행하는 명령어의 upsert : true 옵션을 주면 Insert 동작을 수행합니다.    

- update - upsert : true 옵션을 주었을 때
- updateOne - upsert : true 옵션을 주었을 때
- updateMany - upsert : true 옵션을 주었을 때
- findAndModify - upsert : true 옵션을 주었을 때
- findAndUpdate - upsert : true 옵션을 주었을 때
- findAndReplace - upsert : true 옵션을 주었을 때



Insert 방법 말고 데이터를 Insert할수 있는 명령어로는 save와 bulkWrite가 있습니다.



 save 명령어는 document가 존재하면 update, 존재하지 않으면 insert 입니다. update명령어와 차이점은 Document단위로 데이터를 변경합니다. document 단위로 데이터를 변경하는 것은 save 가 효율적이지만, 필드 단위로 변경하는 경우에는 update 문이 더 효율적입니다.



**Autoincrement Id 만들어 입력하기**

관계형 데이터베이스에서는 대부분 연속적인 자동 증가값을 구현할수 있는 방법을 제공합니다. MongoDB에서는 그러한 기능이 기본적으로 제공되지는 않지만 다음과 같이 함수를 이용하여 직접 생성할 수 있습니다.

```
 function seq_no(name){     
     var ret = db.seq_no.findAndModify(
     {
        query : {_id : name},
        update :{$inc:{next:1}},
        "new":true, upsert:true
     });     
     return ret.next; 
 } 
db.ord_no.insert({_id:seq_no("ord_no"), name: "스타워즈레고"}) db.ord_no.insert({_id:seq_no("ord_no"), name:"닌자고레고"}) db.ord_no.find()
```



