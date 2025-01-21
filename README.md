
<img src="https://capsule-render.vercel.app/api?type=waving&color=0E4C92&height=300&section=header&text=C-Radar&fontSize=70&fontColor=FFFFFF&animation=fadeIn&width=1200" width="1200" />


## <div align="center" style="font-size: 70px; color: #000080; animation: glow 1.5s infinite;">  🔎 Catch your Log, 이탈자 방지와 이상 탐지를 한 번에 🔎 </div>

<br>

<br>

<br>

## 📍목차
- [1️⃣ 프로젝트 개요](#1%EF%B8%8F⃣-프로젝트-개요)
- [2️⃣ 팀원 소개](#2%EF%B8%8F⃣-팀원-소개)
- [3️⃣ 개발 환경 설정](3%EF%B8%8F⃣-개발-환경-설정)
- [4️⃣ ERD](#4%EF%B8%8F⃣-erd)
- [5️⃣ 회고](#5%EF%B8%8F⃣-회고)
- [6️⃣ 피드백](#6%EF%B8%8F⃣-피드백)


<br>

<br>

## 1️⃣ 프로젝트 개요
이 프로젝트는 **서비스 로그를 분석**하여 이탈자 탐지와 이상 행동을 식별하는 것을 목표로 합니다.  
**INFO, WARN, ERROR, FATAL** 로그 데이터를 기반으로 사용자 행동과 에러 발생 패턴을 시각화하고,  
서비스의 품질 향상을 위한 통찰을 제공합니다. 

>### 💡 개발 배경
>
>**고객 이탈**에는 크게 **자발적 이탈**과 **비자발적 이탈**의 두 가지 유형이 있습니다.
>
>### 자발적 이탈
>
>고객의 선호도 변화와 관련이 있는 이탈 유형 
>
>### 비자발적 이탈
>
>기술 또는 결제 문제, 자연재해 등 고객이 통제할 수 없는 문제
>
><br>
>출처: https://www.ibm.com/kr-ko/think/topics/customer-churn
<br>

### 📊 핵심 기능
1. **서비스 이탈자 분석**  
   - 사용 중: INFO 로그 및 반복 WARN 로그 탐지  
   - 사용 종료: 로그 메시지에서 `exit` 또는 `background` 키워드 분석  

2. **이상 탐지**  
   - 로그 레벨(INFO, WARN, ERROR, FATAL) 기반의 이상 행동 식별  

3. **로그 데이터를 활용한 "대시보드"로 시각화 제공**

   - 대시보드 URL: [Dashboard 바로가기](http://192.168.1.77:5601/app/dashboards#/view/39ad3630-d7da-11ef-97a0-756f62d8a917?_g=(filte[…]A(from%3A'2024-10-29T17%3A55%3A57.524Z'%2Cto%3Anow)))


</br>


<br>

## 2️⃣ 팀원 소개

### [🙆🏻‍♂️ 팀원](#목차)

|<img src="https://avatars.githubusercontent.com/u/80048007?v=4" width="220" height="200"/>|<img src="https://avatars.githubusercontent.com/u/60309978?v=4" width="220" height="200"/>|<img src="https://avatars.githubusercontent.com/u/193213283?v=4" width="220" height="200"/>|<img src="https://avatars.githubusercontent.com/u/115103394?v=4" width="220" height="200"/>|
|:-:|:-:|:-:|:-:|
|박영진<br/>[@DoomchitYJ](https://github.com/DoomchitYJ)|박정호<br/>[@Jeongho427](https://github.com/Jeongho427)|박진현<br/>[@jinhyunpark929](https://github.com/jinhyunpark929)|이현정<br/>[@nanahj](https://github.com/nanahj)|

<br>

## 3️⃣ 개발 환경 설정

### 🛠 기술 스택

**Tech Stack**

<div>
<img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white"> 
<img src="https://img.shields.io/badge/linux-FCC624?style=for-the-badge&logo=linux&logoColor=black"> 
<img src="https://img.shields.io/badge/dbeaver-846d5e?style=for-the-badge&logo=dbeaver&logoColor=white"> 
<img src="https://img.shields.io/badge/elasticsearch-3db9ac?style=for-the-badge&logo=elasticsearch&logoColor=white"> 
<img src="https://img.shields.io/badge/kibana-f04e98?style=for-the-badge&logo=kibana&logoColor=white">   
</div>

<br>

**Co-work Stack**

<div>
<img src="https://img.shields.io/badge/notion-000000?style=for-the-badge&logo=notion&logoColor=white"> 
<img src="https://img.shields.io/badge/github-303a50?style=for-the-badge&logo=github&logoColor=white">
<img src="https://img.shields.io/badge/slack-e01e5a?style=for-the-badge&logo=slack&logoColor=white">
</div>

<br>

### 🖥️ 아키텍처


![image](https://github.com/user-attachments/assets/83cb6460-a3c0-498a-8623-12702e5d5309)



<br>

<br>

## 4️⃣ 테이블 형태

![image](https://github.com/user-attachments/assets/a19248dc-a26a-4fe0-8a80-cb89726b119a)

| Field | Contents |
| :---: | :---: |
| LEVEL | INFO, WARN, ERROR, FATAL |
| TIMESTAMP | "2025-01-20T14:12:34Z” Format |
| SOURCE | ERROR 발생 위치 |
| USERID | 서비스 사용자 ID |
| MESSAGE | USER 행동 or ERROR 내용 |
| LOG_TYPE | 400, 200 |

### LEVEL

INFO, WARN, ERROR, FATAL

### TIMESTAMP

ex.. "2025-01-20T14:12:34Z”

### SOURCE

어디서 에러가 나는가?

### USERID

서비스를 사용한 user의 id

### MESSAGE

user의 행동 혹은 error 내용

### LOG_TYPE

ex.. 404 200


<br>

## 5️⃣ 트러블슈팅

**⚔ MySQL 데이터가 ElasticSearch에 들어가지 않는 문제**

발생한 에러 로그:
```
[2025-01-21T15:14:00,207][ERROR][logstash.inputs.jdbc     ][main][1c1466bdc1156c09cdaa6367548cadf70059fe13237f40acbcf85fddd30f859c] Unable to connect to database. Tried 1 times {:error_message=>"Java::JavaSql::SQLException: The server time zone value 'KST' is unrecognized or represents more than one time zone. You must configure either the server or JDBC driver (via the serverTimezone configuration property) to use a more specifc time zone value if you want to utilize time zone support."}
```

**⚔ MySQL의 중복 데이터가 ElasticSearch에 주기마다 삽입되는 문제**

해결방안: logstash의 .conf 파일에 ```document_id => "%{id}"```를 삽입한다.

>
>```document_id => "%{id}"```의 의미: 
>Logstash에서 Elasticsearch에 데이터를 삽입할 때, Logstash의 이벤트에서 id 필드에 해당하는 값을 Elasticsearch 문서의 ID로 사용하겠다는 뜻이다.
>
>이렇게 설정하면, Logstash가 MySQL에서 가져온 각 데이터 항목에 포함된 id 값을 Elasticsearch 문서의 고유 ID로 지정하며 같은 ID를 가진 문서가 이미 존재하면 해당 문서를 업데이트한다.
>
>따라서, document_id => "%{id}"를 설정하면, 동일한 id를 가진 데이터가 새로 들어오더라도 이미 Elasticsearch에 존재하는 문서가 덮어쓰여지거나 업데이트된다.

예시: 

```java
input {
  jdbc {
    jdbc_driver_library => "C:/02.devEnv/mysql-connector-java/mysql-connector-java-8.0.18.jar"
    jdbc_driver_class => "com.mysql.cj.jdbc.Driver"
    jdbc_connection_string => "jdbc:mysql://192.168.1.77:3306/cradar?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=Asia/Seoul"
    jdbc_user => "cradar"
    jdbc_password => "cradar"
    schedule => "* * * * *"
    
    # SQL_LAST_VALUE를 추적할 컬럼 설정
    use_column_value => true
    tracking_column => "created_at"  # 또는 updated_at 등 타임스탬프 컬럼
    tracking_column_type => "timestamp"
    
    # 마지막 실행 시간 저장 위치
    last_run_metadata_path => "C:/02.devEnv/ELK/logstash-7.11.1/last_run_metadata.txt"
    
    # 증분 업데이트를 위한 SQL 쿼리
    # statement => "SELECT * FROM log WHERE timestamp > :sql_last_value ORDER BY timestamp ASC"
    statement => "SELECT *, UNIX_TIMESTAMP(created_at) AS unix_ts_in_secs FROM log WHERE (UNIX_TIMESTAMP(created_at) > :sql_last_value AND created_at < NOW()) ORDER BY created_at ASC"
  }
}

filter {
  mutate {
    remove_field => [ "@timestamp" ]
  }
}

output {
  elasticsearch {
    hosts => ["localhost:9200"]
    index => "cradar"
    document_id => "%{id}"
  }
  stdout { codec => json_lines }
}
```


## 6️⃣ 회고


## 7️⃣ 피드백


<img src="https://capsule-render.vercel.app/api?type=waving&color=0E4C92&height=150&section=footer" width="1000" />
