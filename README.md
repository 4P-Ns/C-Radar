
<img src="https://capsule-render.vercel.app/api?type=waving&color=0E4C92&height=300&section=header&text=C-Radar&fontSize=70&fontColor=FFFFFF&animation=fadeIn&width=1200" width="1200" />


## <div align="center" style="font-size: 70px; color: #000080; animation: glow 1.5s infinite;">  🔎 Catch your Log, 이탈자 방지와 이상 탐지를 한 번에 🔎</div>

   <p align="center">
      <img src="https://github.com/user-attachments/assets/f4c1d2a7-eeb7-4e11-a74a-f098196c6a94" width=50%>
   </p>


<br>

## 📍 Contents
- [1️⃣ Overview](#1%EF%B8%8F⃣-overview)
- [2️⃣ Contributors](#2%EF%B8%8F⃣-contributors)
- [3️⃣ Environment Settings](#3%EF%B8%8F⃣-environment-settings)
- [4️⃣ ERD](#4%EF%B8%8F⃣-erd)
- [5️⃣ Trouble Shooting](#5%EF%B8%8F⃣-trouble-shooting)
- [6️⃣ Retrospective](#6%EF%B8%8F⃣-retrospective)


<br>

<br>

## 1️⃣ Overview
이 프로젝트는 **시스템 로그를 분석**하여 이탈자 탐지와 이상 행동을 식별하는 것을 목표로 합니다.  
**INFO, WARN, ERROR, FATAL** 로그 데이터를 기반으로 사용자 행동과 에러 발생 패턴을 시각화하고,  
서비스의 품질 향상을 위한 통찰을 제공합니다. 

### 💡 Background

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

### ❗ Customer Needs

![image](https://github.com/user-attachments/assets/00577483-2a32-495b-a709-8a2e49d75fe8)


### 📊 Core Features
1. **서비스 이탈자 분석**  
   - 사용 중: INFO 로그 및 반복 WARN 로그 탐지  
   - 사용 종료: 로그 메시지에서 `exit` 또는 `background` 키워드 분석  

2. **이상 탐지**  
   - 로그 레벨(INFO, WARN, ERROR, FATAL) 기반의 이상 행동 식별  

3. **로그 데이터를 활용한 "대시보드"로 시각화 제공**

   <a href="service/demo.md">
     <button style="font-size: 100px;">💥 데모 시연</button>
   </a>


</br>


<br>

## 2️⃣ Contributors

|<img src="https://avatars.githubusercontent.com/u/80048007?v=4" width="220" height="200"/>|<img src="https://avatars.githubusercontent.com/u/60309978?v=4" width="220" height="200"/>|<img src="https://avatars.githubusercontent.com/u/193213283?v=4" width="220" height="200"/>|<img src="https://avatars.githubusercontent.com/u/115103394?v=4" width="220" height="200"/>|
|:-:|:-:|:-:|:-:|
|박영진<br/>[@DoomchitYJ](https://github.com/DoomchitYJ)|박정호<br/>[@Jeongho427](https://github.com/Jeongho427)|박진현<br/>[@jinhyunpark929](https://github.com/jinhyunpark929)|이현정<br/>[@nanahj](https://github.com/nanahj)|

<br>

## 3️⃣ Environment Settings

### 🛠 Skills

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

### 🖥️ Architecture

![image](https://github.com/user-attachments/assets/9f48e40b-36ac-48e6-83b8-909d26a72de4)

<br>

### 🛠 Configuration

**1. MySQL Connector 설치**

https://downloads.mysql.com/archives/c-j/

![image](https://github.com/user-attachments/assets/c28f7618-24f1-40ba-844c-96160eb55c35)

Windows는 Operating System: 선택 항목에 없다. Platform Independent로 선택한다.

"Platform Independent (Architecture Independent), Compressed TAR Archive"로 다운로드하고 원하는 경로에 압축을 해제한다.

**2. .conf 파일 수정**

JDBC 코드를 입력한다.

**a. input**
```
input {
  jdbc {
    jdbc_driver_library => "C:/02.devEnv/mysql-connector-java/mysql-connector-java-8.0.18.jar"
    jdbc_driver_class => "com.mysql.cj.jdbc.Driver"
    jdbc_connection_string => "jdbc:mysql://IP주소/DB이름?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=Asia/Seoul"
    jdbc_user => "유저이름"
    jdbc_password => "비밀번호"
    schedule => "* * * * *" # 1분 주기로 업데이트
    
    # SQL_LAST_VALUE를 추적할 컬럼 설정
    use_column_value => true
    tracking_column => "created_at"  # MySQL에서 지정한 column명으로 변경
    tracking_column_type => "timestamp"
    
    # 마지막 실행 시간 저장 위치
    last_run_metadata_path => "C:/02.devEnv/ELK/logstash-7.11.1/last_run_metadata.txt"
    
    # 증분 업데이트를 위한 SQL 쿼리
    # statement => "SELECT * FROM log WHERE timestamp > :sql_last_value ORDER BY timestamp ASC"
    statement => "SELECT *, UNIX_TIMESTAMP(created_at) AS unix_ts_in_secs FROM log WHERE (UNIX_TIMESTAMP(created_at) > :sql_last_value AND created_at < NOW()) ORDER BY created_at ASC"
  }
}
```

<br>

>**🧨 참고: schedule 표현식**
>
>```
>* * * * *
>```
>각 위치는 특정 시간 단위를 나타내며, 왼쪽에서 오른쪽으로 아래와 같이 해석된다.
>
> 분 (Minutes): 0-59
>
> 시간 (Hours): 0-23 (24시간 형식)
>
> 일 (Day of Month): 1-31
>
> 월 (Month): 1-12
>
> 요일 (Day of Week): 0-6 (0은 일요일)
>
><br>
>
> **와일드카드와 값 설명**
>
> *: 모든 값 (예: 모든 분, 모든 시간 등).
>
> */n: 매 n 단위 (예: */15는 15분 간격).
>
> a-b: 범위 (예: 9-17은 9시부터 17시까지).
>
> a,b: 특정 값들 (예: 1,15는 1일과 15일).
>
> ?: 특정 값 생략 (주로 일(Day of Month)과 요일(Day of Week) 중 하나를 생략할 때 사용).
<br>

**b. filter**

```
filter {
  mutate {
    remove_field => [ "@timestamp" ]
  }
}
```

이벤트가 Logstash에 의해 수집되었을 때의 시간인 **@timestamp** 필드는 제거하였다.

<br>

**c. output**

```
output {
  elasticsearch {
    hosts => ["localhost:9200"]
    index => "인덱스명"
    document_id => "%{id}"
  }
  stdout { codec => json_lines }
}
```


<br>

## 4️⃣ ERD
### MySQL
<div style="display: flex; justify-content: center; gap: 200px;">
  <img src="https://github.com/user-attachments/assets/a19248dc-a26a-4fe0-8a80-cb89726b119a" alt="Image 1" width="165">
  <img src="https://github.com/user-attachments/assets/eaea307a-1785-4971-8485-deeba36077ca" alt="Image 2" width="400">
</div>

<br>

### Elasticsearch
![image](https://github.com/user-attachments/assets/7867c7cd-d689-4411-8e31-cbb30c805c03)

<br>

## 5️⃣ Trouble Shooting

**⚔ MySQL 데이터가 ElasticSearch에 들어가지 않는 문제**

**발생한 에러 로그:**
```
[2025-01-21T15:14:00,207][ERROR][logstash.inputs.jdbc     ][main][1c1466bdc1156c09cdaa6367548cadf70059fe13237f40acbcf85fddd30f859c] Unable to connect to database. Tried 1 times {:error_message=>"Java::JavaSql::SQLException: The server time zone value 'KST' is unrecognized or represents more than one time zone. You must configure either the server or JDBC driver (via the serverTimezone configuration property) to use a more specifc time zone value if you want to utilize time zone support."}
```

**해결방안:** 타임존(Asia/Seoul)을 구체적으로 지정한다.

```
    jdbc_connection_string => "jdbc:mysql://192.168.1.77:3306/cradar?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=Asia/Seoul"
```

<br><br>

**⚔ MySQL의 중복 데이터가 ElasticSearch에 주기마다 삽입되는 문제**

**해결방안:** logstash의 .conf 파일 output 파트에 ```document_id => "%{id}"```를 삽입한다.

>
>```document_id => "%{id}"```의 의미: 
>Logstash에서 Elasticsearch에 데이터를 삽입할 때, Logstash의 이벤트에서 id 필드에 해당하는 값을 **Elasticsearch 문서의 ID로 사용**하겠다는 뜻이다.
>
>이렇게 설정하면, Logstash가 MySQL에서 가져온 각 데이터 항목에 포함된 id 값을 Elasticsearch 문서의 고유 ID로 지정하며 **같은 ID를 가진 문서가 이미 존재하면 해당 문서를 업데이트**한다.
>
>따라서, document_id => "%{id}"를 설정하면, 동일한 id를 가진 데이터가 새로 들어오더라도 **이미 Elasticsearch에 존재하는 문서가 덮어쓰여지거나 업데이트**된다.

**예시:**

```java
output {
  elasticsearch {
    hosts => ["localhost:9200"]
    index => "cradar"
    document_id => "%{id}"
  }
  stdout { codec => json_lines }
}
```


## 6️⃣ Retrospective

### 프로젝트 경험 개괄 정리

1. **가치 제안(Value Proposition)의 중요성**  
   - 프로젝트를 통해 시장 적합성을 검증하는 과정에서 명확한 가치 제안이 필수적임을 체감함.

2. **데이터 시각화와 사용자 중심 UX 설계**  
   - 단순한 데이터 전달을 넘어, 의미를 명확히 전달하는 데이터 시각화의 중요성을 인식.  
   - 데이터 흐름과 상관관계를 효과적으로 표현하기 위한 시각화 설계와 사용자 선호도 반영의 필요성 체감.  
   - 데이터 시각화가 데이터 분석의 핵심임을 다시 깨닫게 됨.

3. **실전적인 로그 데이터 활용**  
   - 가상 로그 데이터를 기반으로 한 시나리오 설계로 몰입감 상승.  
   - Logstash를 활용해 데이터베이스와 Elasticsearch를 연결하는 파이프라인 구축 경험.  
   - 데이터 분석 결과를 시각화하여 유의미한 인사이트를 도출하고, 향후 프로젝트에 적용 가능성을 확인.

4. **기술적 역량 강화**  
   - Logstash의 필요성과 기능을 심도 있게 이해하며 활용 능력을 향상시킴.  
   - 복잡하고 도전적인 프로젝트에 참여할 수 있는 기술적 자신감을 얻음.


<img src="https://capsule-render.vercel.app/api?type=waving&color=0E4C92&height=150&section=footer" width="1000" />
