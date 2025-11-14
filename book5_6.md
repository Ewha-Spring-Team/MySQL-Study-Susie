# SQL 코드 & 명령어 정리 (5·6장)
# 개념 설명 링크: https://blog.naver.com/ewhanthbeot/223616636207

---

## 5장 — 집계함수 / GROUP BY / HAVING / 서브쿼리

### 📌 1) 행 개수
```sql
SELECT COUNT(열) FROM 테이블;
````

### 📌 2) 집계함수 NULL 처리

* COUNT, SUM, AVG, MIN, MAX 모두 `NULL`은 무시됨.

### 📌 3) 중복 제거

```sql
SELECT DISTINCT 열 FROM 테이블;
```

---

## 📌 4) 기본 집계 함수

합계:

```sql
SELECT SUM(열) FROM 테이블;
```

평균:

```sql
SELECT AVG(열) FROM 테이블;
```

최소/최대:

```sql
SELECT MIN(열), MAX(열) FROM 테이블;
```

---

## 📌 5) GROUP BY (그룹화)

```sql
SELECT 열
FROM 테이블
GROUP BY 열1, 열2;
```

그룹별 통계:

```sql
SELECT 열1, COUNT(열2), SUM(열3)
FROM 테이블
GROUP BY 열1;
```

---

## 📌 6) HAVING (GROUP BY 조건)

⚠️ WHERE에서 집계함수 사용 불가
→ HAVING 사용

```sql
SELECT 열, COUNT(열)
FROM 테이블
GROUP BY 열
HAVING COUNT(열) = 1;
```

처리 순서:

```
WHERE → GROUP BY → HAVING → SELECT → ORDER BY
```

---

## 📌 7) 그룹화 후 정렬

```sql
SELECT 열1, SUM(열2)
FROM 테이블
GROUP BY 열1
ORDER BY SUM(열3);
```

---

## 📌 8) 서브쿼리 기본형

### WHERE 사용

```sql
SELECT 열
FROM 테이블
WHERE 열1 = (SELECT MAX(열1) FROM 테이블);
```

### SELECT 절에서 서브쿼리

```sql
SELECT
  (SELECT COUNT(열1) FROM 테이블) AS 별명1,
  (SELECT COUNT(열2) FROM 테이블) AS 별명2;
```

### UPDATE SET 서브쿼리

```sql
UPDATE 테이블
SET a = (SELECT MAX(a) FROM 테이블);
```

### FROM 절 서브쿼리

```sql
SELECT 열
FROM (SELECT 열 FROM 테이블) AS 서브;
```

### INSERT + 서브쿼리

```sql
INSERT INTO 테이블
SELECT 값1, 값2;
```

---

## 📌 9) 상관 서브쿼리 (EXISTS / NOT EXISTS)

### EXISTS

```sql
UPDATE 테이블
SET a = '있음'
WHERE EXISTS (
  SELECT *
  FROM 테이블
  WHERE 인덱스 = no
);
```

### NOT EXISTS

```sql
SELECT *
FROM 테이블
WHERE NOT EXISTS (
  SELECT *
  FROM 서브
);
```

### IN (집합 비교)

```sql
WHERE no IN (3, 5);
```

---

# 6장 — 객체 / 스키마 / DDL / 제약조건 / 인덱스 / 뷰

## 📌 10) 테이블 생성 (CREATE TABLE)

```sql
CREATE TABLE 테이블명 (
  열1 자료형 [기본값] [NOT NULL],
  열2 자료형,
  ...
);
```

제약 이름 부여:

```sql
CREATE TABLE 테이블명 (
  열1 자료형,
  CONSTRAINT 제약명 제약종류 (열1, 열2)
);
```

---

## 📌 11) 테이블 삭제 / 변경

### DROP TABLE

```sql
DROP TABLE 테이블명;
```

### TRUNCATE (전체 데이터 삭제)

```sql
TRUNCATE TABLE 테이블명;
```

### ALTER TABLE

열 추가:

```sql
ALTER TABLE 테이블명 ADD 열명 자료형;
```

열 삭제:

```sql
ALTER TABLE 테이블명 DROP 열명;
```

열 수정:

```sql
ALTER TABLE 테이블명 MODIFY 열명 자료형;
```

열 이름 변경:

```sql
ALTER TABLE 테이블명 CHANGE 기존열 새열 자료형;
```

---

## 📌 12) 제약 조건

NOT NULL 추가:

```sql
ALTER TABLE 테이블명 MODIFY 열명 자료형 NOT NULL;
```

테이블 제약 추가:

```sql
ALTER TABLE 테이블명 ADD CONSTRAINT 제약명 제약종류 (열명);
```

제약 삭제:

```sql
ALTER TABLE 테이블명 DROP CONSTRAINT 제약명;
```

기본키:

```sql
ALTER TABLE 테이블명 ADD PRIMARY KEY (열1, 열2);
```

---

## 📌 13) 인덱스

인덱스 생성:

```sql
CREATE INDEX 인덱스명 ON 테이블명 (열);
```

인덱스 삭제:

```sql
DROP INDEX 인덱스명 ON 테이블명;
```

인덱스 사용 확인:

```sql
EXPLAIN SELECT 열 FROM 테이블 WHERE 조건;
```

---

## 📌 14) VIEW (뷰)

뷰 생성:

```sql
CREATE VIEW 뷰명 AS
SELECT 열 FROM 테이블;
```

뷰 삭제:

```sql
DROP VIEW 뷰명;
```
