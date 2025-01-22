
<img src="https://capsule-render.vercel.app/api?type=waving&color=0E4C92&height=300&section=header&text=C-Radar&fontSize=70&fontColor=FFFFFF&animation=fadeIn&width=1200" width="1200" />


## <div align="center" style="font-size: 70px; color: #000080; animation: glow 1.5s infinite;">  🔎 Catch your Log, 이탈자 방지와 이상 탐지를 한 번에 🔎 </div>

<br>

<br>

<br>

## 📍 Contents
- [1️⃣ Overview](#1%EF%B8%8F⃣-overview)
- [2️⃣ Contributors](#2%EF%B8%8F⃣-contributors)
- [3️⃣ Environment Settings](#3%EF%B8%8F⃣-environment-settings)
- [4️⃣ ERD](#4%EF%B8%8F⃣-erd)
- [5️⃣ Trouble Shooting](#5%EF%B8%8F⃣-trouble-shooting)
- [6️⃣ Retrospective](#6%EF%B8%8F⃣-retrospective)
- [7️⃣ Feedbacks](#7%EF%B8%8F⃣-feedbacks)


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


![image](https://github.com/user-attachments/assets/83cb6460-a3c0-498a-8623-12702e5d5309)


<br>

<br>

## 4️⃣ ERD

<div style="display: flex; justify-content: center; gap: 200px;">
  <img src="https://github.com/user-attachments/assets/a19248dc-a26a-4fe0-8a80-cb89726b119a" alt="Image 1" width="165">
  <img src="https://github.com/user-attachments/assets/eaea307a-1785-4971-8485-deeba36077ca" alt="Image 2" width="400">
</div>

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


## 7️⃣ Feedbacks


<img src="https://capsule-render.vercel.app/api?type=waving&color=0E4C92&height=150&section=footer" width="1000" />
