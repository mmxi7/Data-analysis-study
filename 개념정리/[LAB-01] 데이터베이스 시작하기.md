# 데이터베이스 시작하기

## 1. MariaDB 설치

### 데이터베이스란?

- **DB(Database)** : 특정한 목적을 가진 데이터의 집합
- **DBMS(Database Management System)** : 데이터베이스를 관리하기 위한 시스템

### DBMS의 주요 기능

1. 데이터 저장 및 검색
2. 데이터 보안
3. 동시성 제어
4. 백업 및 복구

### 주요 DBMS

- Oracle
- MySQL
- MariaDB
- Microsoft SQL Server

스터디 기간 동안 **MariaDB**를 사용한다.

### MariaDB란?

MySQL에서 파생된 **오픈소스 RDBMS**(관계형 데이터베이스 관리 시스템)이다.

### MariaDB 접속

```bash
mariadb -u사용자이름 -p --host=localhost --port=포트번호
```

예시:

```bash
mariadb -uroot -p --host=localhost --port=9090
```

---

## 2. 데이터베이스의 구성

### 서버와 클라이언트

- **클라이언트(Client)** : 서버에 요청을 보내는 쪽
- **서버(Server)** : 클라이언트의 요청을 받아 처리하고 응답하는 쪽
- MariaDB는 별도의 UI 없이 백그라운드에서 실행되는 서버 프로그램이다.
- `mariadb.exe`는 MariaDB에 명령을 전달하는 CLI 클라이언트 프로그램이다.

### 데이터베이스의 구조

DBMS 안에는 여러 개의 데이터베이스가 존재하고,  
하나의 데이터베이스 안에는 여러 개의 테이블이 존재한다.

Excel과 비교하면 다음과 같다.

- Excel 프로그램 → DBMS
- Excel 파일 → Database
- Excel 시트 → Table
- 행(Row) → Record
- 열(Column) → Field 또는 Column

즉,

**DBMS → Database → Table → Row / Column**

---

## 3. 데이터베이스 살펴보기

### 데이터베이스 목록 확인

```sql
SHOW DATABASES;
```

### 사용할 데이터베이스 선택

```sql
USE myschool;
```

### 현재 데이터베이스의 테이블 목록 확인

```sql
SHOW TABLES;
```

### 테이블의 데이터 조회

```sql
SELECT * FROM departments;
```

### 테이블 구조 확인

```sql
DESC departments;
```

---

## 4. 테이블의 구조

테이블은 **행(Row)**과 **열(Column)**로 구성된다.

- **행(Row)** : 하나의 데이터 → Record
- **열(Column)** : 데이터의 속성 → Field 또는 Column

예를 들어 학과 테이블에서 하나의 학과가 하나의 행이고,  
학과번호·학과명·위치·전화번호 등이 각각의 열이 된다.

### DESC 명령어

```sql
DESC 테이블명;
```

테이블의 구조와 각 컬럼의 정보를 확인할 수 있다.

- `Field` : 컬럼 이름
- `Type` : 데이터 타입과 크기
- `Null` : NULL 허용 여부
- `Key` : 키 여부
- `Default` : 기본값
- `Extra` : 추가 속성

### auto_increment

새로운 데이터가 저장될 때 숫자가 자동으로 1씩 증가하는 속성이다.

---

## 5. 데이터 타입

컬럼에 어떤 종류의 데이터를 저장할 수 있는지를 지정한다.

- `INT` : 정수
- `CHAR(n)` : 고정 길이 문자열
- `VARCHAR(n)` : 가변 길이 문자열
- `DATE` : 날짜 (`YYYY-MM-DD`)
- `DATETIME` : 날짜와 시간 (`YYYY-MM-DD HH:MM:SS`)
- `ENUM` : 정해진 값 중 하나를 저장

### CHAR와 VARCHAR

- `CHAR(n)` : 길이가 고정된 문자열
- `VARCHAR(n)` : 길이가 변할 수 있는 문자열

---

## 핵심 정리

**데이터베이스 구조**

`DBMS → Database → Table → Row / Column`

**데이터베이스 확인 순서**

`SHOW DATABASES` → `USE` → `SHOW TABLES` → `DESC`

**기본 명령어**

```sql
SHOW DATABASES;
USE myschool;
SHOW TABLES;
DESC departments;
SELECT * FROM departments;
```
