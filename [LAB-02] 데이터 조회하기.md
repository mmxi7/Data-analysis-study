# 데이터 조회하기

## 1. SELECT 기본 구조

`SELECT`는 테이블에서 원하는 데이터를 조회할 때 사용한다.

```sql
SELECT 컬럼명
FROM 테이블명;
```

- `SELECT` : 조회할 컬럼을 지정
- `FROM` : 데이터를 조회할 테이블을 지정

### 전체 컬럼 조회

`*`를 사용하면 모든 컬럼을 조회할 수 있다.

```sql
SELECT *
FROM departments;
```

### 특정 컬럼만 조회

```sql
SELECT dname, email, phone, loc
FROM departments;
```

필요한 컬럼만 명시해서 조회하는 것이 좋다.

---

## 2. 컬럼에 별칭 사용하기

`AS`를 사용하여 조회 결과의 컬럼 이름을 변경할 수 있다.

```sql
SELECT name AS 이름,
       position AS 직급,
       status AS '재직 상태'
FROM professors;
```

- `AS`는 생략 가능
- 별칭에 공백이 있으면 따옴표로 묶는다.

---

## 3. 조회하면서 연산하기

컬럼에 사칙연산을 적용하여 조회할 수 있다.

```sql
SELECT name,
       position,
       sal * 12 + 100
FROM professors;
```

원본 데이터가 변경되는 것은 아니며 **조회 결과에만 연산이 적용**된다.

연산 결과에도 별칭을 지정할 수 있다.

```sql
SELECT name,
       position,
       sal * 12 + 100 AS salary
FROM professors;
```

---

## 4. 데이터 정렬하기

`ORDER BY`를 사용하여 조회 결과를 정렬한다.

```sql
SELECT 컬럼명
FROM 테이블명
ORDER BY 정렬기준;
```

- `ASC` : 오름차순
- `DESC` : 내림차순
- 생략하면 기본값은 `ASC`

### 오름차순

```sql
SELECT name, position, sal
FROM professors
ORDER BY sal ASC;
```

### 내림차순

```sql
SELECT name, position, sal
FROM professors
ORDER BY sal DESC;
```

### 여러 기준으로 정렬

```sql
SELECT grade, name, gender
FROM students
ORDER BY grade ASC, name ASC;
```

먼저 `grade`로 정렬하고, 같은 학년 안에서는 `name`으로 다시 정렬한다.

### 별칭을 이용한 정렬

연산식을 다시 작성하는 것보다 별칭을 사용하는 것이 효율적이다.

```sql
SELECT name,
       position,
       sal * 12 + 100 AS salary
FROM professors
ORDER BY salary DESC;
```

---

## 5. LIMIT

`LIMIT`은 조회되는 데이터의 범위를 제한한다.

### 상위 N개 조회

```sql
SELECT name, position, user_id, sal
FROM professors
ORDER BY sal DESC
LIMIT 5;
```

급여가 높은 순서로 정렬한 뒤 **상위 5개 데이터만 조회**한다.

### 특정 위치부터 조회

```sql
SELECT id, dname, loc
FROM departments
LIMIT 3, 3;
```

`LIMIT 시작위치, 개수`

- 시작 위치는 `0`부터 계산
- `LIMIT 0, 3` → 처음부터 3개
- `LIMIT 3, 3` → 4번째부터 3개
- `LIMIT 6, 3` → 7번째부터 3개

---

## 핵심 정리

### SELECT 기본 순서

```sql
SELECT 컬럼명
FROM 테이블명
ORDER BY 정렬기준
LIMIT 개수;
```

### 기억할 것

- `SELECT` : 조회할 컬럼 선택
- `FROM` : 조회할 테이블 선택
- `AS` : 컬럼에 별칭 지정
- `ORDER BY` : 데이터 정렬
- `ASC` : 오름차순
- `DESC` : 내림차순
- `LIMIT` : 조회할 데이터 개수 또는 범위 제한
- `LIMIT`의 시작 위치는 `0`부터 센다.
