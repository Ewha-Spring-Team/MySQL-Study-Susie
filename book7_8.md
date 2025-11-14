# SQL 코드 & 명령어 정리 (7·8장)
# 개념 설명 링크: https://blog.naver.com/ewhanthbeot/223645681585

---

# 7장 — 집합 연산 & JOIN

## 📌 1) 집합 연산 (UNION / INTERSECT / EXCEPT)

### 합집합
```sql
SELECT 열 FROM 테이블1
UNION
SELECT 열 FROM 테이블2;
````

중복 포함:

```sql
SELECT 열 FROM 테이블1
UNION ALL
SELECT 열 FROM 테이블2;
```

UNION 뒤 ORDER BY:

```sql
SELECT ... 
UNION
SELECT ...
ORDER BY 열;
```

---

### 교집합

```sql
SELECT 열 FROM 테이블1
INTERSECT
SELECT 열 FROM 테이블2;
```

### 차집합

```sql
SELECT 열 FROM 테이블1
EXCEPT
SELECT 열 FROM 테이블2;
```

---

## 📌 2) JOIN (테이블 결합)

### 교차결합 (CROSS JOIN)

```sql
SELECT *
FROM 테이블1, 테이블2;
```

또는:

```sql
SELECT *
FROM 테이블1
CROSS JOIN 테이블2;
```

---

## 📌 3) 내부결합 (INNER JOIN)

```sql
SELECT *
FROM 테이블A
INNER JOIN 테이블B
  ON 테이블A.기본키 = 테이블B.기본키;
```

여러 테이블:

```sql
FROM 테이블A
INNER JOIN 테이블B ON 조건
INNER JOIN 테이블C ON 조건;
```

---

## 📌 4) 자기결합 (Self Join)

```sql
SELECT A.열, B.열
FROM 테이블 AS A
JOIN 테이블 AS B
  ON A.기본키 = B.외부키;
```

---

## 📌 5) 외부결합 (LEFT / RIGHT JOIN)

LEFT JOIN:

```sql
SELECT *
FROM 테이블A
LEFT JOIN 테이블B
  ON 테이블A.기본키 = 테이블B.기본키;
```

RIGHT JOIN:

```sql
SELECT *
FROM 테이블A
RIGHT JOIN 테이블B
  ON 테이블A.기본키 = 테이블B.기본키;
```

---

# 8장 — DB 설계, 정규화, 트랜잭션

## 📌 6) 테이블 생성 / 변경 / 삭제 (DDL)

### CREATE TABLE

```sql
CREATE TABLE 테이블명 (
  열1 자료형,
  열2 자료형,
  ...
);
```

### DROP TABLE

```sql
DROP TABLE 테이블명;
```

### ALTER TABLE — 열 추가/삭제/변경

```sql
ALTER TABLE 테이블 ADD new_col 자료형;
ALTER TABLE 테이블 DROP col;
ALTER TABLE 테이블 MODIFY col 자료형;
ALTER TABLE 테이블 CHANGE old_col new_col 자료형;
```

---

## 📌 7) 제약조건 (Constraints)

### NOT NULL

```sql
ALTER TABLE 테이블 MODIFY 열 자료형 NOT NULL;
```

### 기본키 추가

```sql
ALTER TABLE 테이블 ADD PRIMARY KEY (열);
```

### 제약 추가

```sql
ALTER TABLE 테이블 ADD CONSTRAINT 제약명 제약종류 (열);
```

### 제약 삭제

```sql
ALTER TABLE 테이블 DROP CONSTRAINT 제약명;
```

---

## 📌 8) 정규화 (코드 없음 — 설계 개념)

정규화 과정 자체는 SQL 문이 아니라 설계 개념이므로 코드 제외.

---

## 📌 9) 트랜잭션 (START TRANSACTION / COMMIT / ROLLBACK)

### 트랜잭션 기본 흐름

```sql
START TRANSACTION;

INSERT INTO 주문 VALUES (...);
INSERT INTO 주문상품 VALUES (...);
INSERT INTO 주문상품 VALUES (...);

COMMIT;
```

### 롤백

```sql
ROLLBACK;
```

---

# ✔ 전체 요약된 명령어 목록

## 집합 연산

```
UNION
UNION ALL
INTERSECT
EXCEPT
```

## JOIN

```
(CROSS) JOIN
INNER JOIN
LEFT JOIN
RIGHT JOIN
```

## DDL

```
CREATE TABLE
DROP TABLE
ALTER TABLE ADD
ALTER TABLE DROP
ALTER TABLE MODIFY
ALTER TABLE CHANGE
```

## 제약

```
NOT NULL
PRIMARY KEY
CONSTRAINT
```

## 트랜잭션

```
START TRANSACTION
COMMIT
ROLLBACK
```
