## DATA_ANALYTICS_MANAGER (데이터분석시스템 관리도구)

### 1. 데이터분석시스템 설명
"DATA_ANALYTICS_MANAGER"는 사내 솔루션으로 사용자는 **웹 기반의 인터페이스를 통해 데이터 관리, 머신러닝 & 딥러닝 분석 및 테스트, 분석된 데이터 다운로드 등의 기능**들을 이용할 수 있습니다.

제공하는 메뉴는 크게 8가지입니다. <br />
- **대시보드:** 초기 접속 화면으로 도메인, 모델, 프로젝트 현황과 저장용량, 최근 분석 내역을 확인할 수 있습니다.
- **알고리즘 조회:** 데이터분석시스템에서 제공하는 머신러닝 & 딥러닝 알고리즘 목록과 상세 정보를 제공합니다.
- **데이터 관리:** 사용자는 개개인의 데이터를 저장할 수 있고 샘플을 볼 수 있습니다.
- **머신러닝 관리:** 머신러닝 분석 및 테스트를 진행할 수 있습니다.
- **딥러닝 관리:** 딥러닝 분석 및 테스트를 진행할 수 있습니다.
- **도메인 관리:** 머신러닝 혹은 딥러닝 분석의 산출물을 등록하여 다운로드 및 테스트해볼 수 있습니다.
- **사용자 가이드:** 데이터분석시스템을 처음 접하는 사용자들에게 가이드를 제공해줍니다.
- **사용자 관리**: 관리자 전용 메뉴로 데이터분석시스템을 이용하는 사용자들을 관리할 수 있습니다.

```
- 시큐어 쉘: ssh daumsoft@10.1.1.61
- 도커 컨테이너 접속: docker exec -it dasolution /bin/bash
- 웹 화면: http://10.1.1.61:2030
v. 관리자 계정: admin /admin
v. 사용자 계정: 미정 / 미정
```

<br/>
<br/>

### 2. 개발환경 및 라이브러리

#### A. 개발 환경
**\<OS\>**
- **Develop OS:** Windows 10 <br />
- **Target OS:** Windows 10 <br />

**\<PROGRAM\>**
- **Database:** PostgreSQL <br />

**\<FRAMEWORK\>**
- **Framework:** Spring Boot 2.2.4 RELEASE <br />

**\<LANGUAGE\>**
- **Back-end Language:** JAVA 1.8 <br />
- **Serverside Template Language:** Thymeleaf <br />
- **Clientside Script:** Javascript, Jquery <br />

#### B. 라이브러리 목록([상세보기](./DataAnalyticsManager/pom.xml))

**<웹 개발>**
- spring-boot-starter-web: web 구축에 대한 기본 내장형 Tomcat
- spring-boot-start-thymeleaf: thymeleaf views
- thymeleaf-layout-dialect: thymeleaf의 layout/decorator
<br />

**\<JDBC\>**
- mybatis-spring-boot-starter: mybatis application
- postgresql: postgresql
<br />

**<데이터베이스 Connection Pool>**
- com.zaxxer : hikariCp(Connection pool)
<br/>

**\<JUNIT\>** 
- spring-boot-starter-test : JUnit, Hamcrest, Mockito 라이브러리를 활용하여 spring boot application 테스트
<br/>

**<HTTP 통신>** 
- okhttp : HTTP client
<br/>

**<JSON 활용>** 
- gson : JSON 데이터 처리
- json-lib : beans, maps, collections, array, xml을 JSON으로 변환
<br/>

**<파일 업로드>** 
- commons-fileupload : java 파일 업로드
- commons-io : IO를 지원
<br/>

**<로깅>**
- log4jdbc-log4j2-jdbc4.1 : Log4jdbc를 사용해 실행쿼리 로그출력
<br/>

**<프로그래 성능 모니터>**
- spring-boot-starter-actuator : spring boot application 모니터
<br/>

**<개발 보조도구>**
- spring-boot-devtool : livereload, restart 자동 빌드
- spring-restdocs-mockmvc : RESTful 서비스 문서화
- lombok : get, set, toString method 자동화
- spring-boot-configuration-processor : configuration properties
<br/>

**<로그인 처리>**
- aspectjweaver : AspectJ(Spring AOP)
- aspectjrt : AspectJ(Spring AOP)
<br/>

<br/>
<br/>

### 3. 배포방법
- DataAnalyticsManager-0.0.1-SNAPSHOT.jar 파일로 묶음 
- DataAnalyticsManager-0.0.1-SNAPSHOT.jar과 application.yml을 배포할 디렉토리에 복사
- 명령어 실행 
 => nohup java -Dspring.config.location=/home/dasolution/DATA_ANALYTICS_MANAGER/application.yml -jar /home/dasolution/DATA_ANALYTICS_MANAGER/DataAnalyticsManager-0.0.1-SNAPSHOT.jar 1> /dev/null 2>&1 &
 - 로그 확인
 => tail -100f ./logs/logback.log

<br/>
<br/>

### 4. Contributor 
* 대리 안정현
* 대리 이호준
* 사원 이승우
<br/>
<br/>

### 5. License
* 미정

<br/>
<br/>

### application.yml 설정

```bash
    # application.yml 경로: /home/dasolution/DATA_ANALYTICS_MANAGER/application.yml
    spring:
        # 프로젝트에서 사용할 웹 관련 설정
        http:
            encoding: "언어셋"
            enabled: "사용 여부"
            force: "강제 적용할지 여부"

        # view 관련 설정
        thymeleaf:
            prefix: "view 경로 중 생략할 접두사"
            check-template-location: "template 위치 확인할 지 여부"
            suffix: "view 경로 중 생략할 접미사"
            mode: "HTML 모드"
            cache: "캐시 저장 여부"

        # 데이터베이스 설정
        datasource:
            hikari:
                driver-class-name: "사용할 드라이버 이름"
                jdbc-url: "DB 주소"
                username: "유저 이름"
                password: "유저 비밀번호"
                connection-test-query: "실행 시 TEST할 QUERY"
            main:
                allow-bean-definition-overriding: "동일한 이름의 빈 등록 허용 여부"

        # Spring 프로젝트 개발 관련 설정
        devtools:
            livereload:
                enabled: "프론트엔드 코드 수정시 자동 반영 여부"
            restart:
                enabled: "백엔드 코드 수정시 자동 재시작 여부"

        # 파일 업로드 용량 설정
        servlet:
            multipart:
                max-file-size: "단일 파일 업로드 한도"
                max-request-size: "단일 업로드 요청 에 있는 모든 파일의 총 크기 한도"
                location: "파일 업로드시 임시로 저장하는 절대경로"
                file-size-threshold: "업로드하는 파일이 임시로 파일로 저장되지 않고 메모리에서 바로 스트림으로 전달되는 크기의 한계"
                enabled: "멀티파트 업로드 지원 여부"

        # Spring 리소스 관련 설정
        management:
            endpoints:
                web:
                    exposure:
                        include: "Spring 리소스 노출할 정보"

        # MyBatis 관련 설정
        mybatis:
            configuration:
                map-underscore-to-camel-case: "DB 컬럼 (user_name)과 DAO 변수 (userName) 매칭 설정"
        
        # 톰캣 설정
        server:
            tomcat:
                uri-encoding: "언어셋"
            port: "포트 번호"

        # 데이터 분석 모듈 관련 정보
        module:
        ip: "ip 주소"
        port: "포트 번호"
        method: "기본 경로"
        localFiles: "로컬용 경로"
        healthCheck: "헬스 체크용 경로"
        asyncSecond: "비동기 전처리 처리 조회 주기"
        asyncPeriod: "비동기 전처리 처리 횟수"

        # 개발용 변수들
        filePath: "데이터 저장 경로"
        fileTestPath: "로컬용 데이터 저장 경로"
        isTest: "로컬 여부"
        userMaxSpace: "사용자 최대 데이터 저장 크기"
```

<br/> 