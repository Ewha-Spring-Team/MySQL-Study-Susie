# SQL 첫걸음 1주차 — 코드 & 핵심 명령 요약 (1장, 2장)
# 개념 설명 링크: https://blog.naver.com/ewhanthbeot/223600013331

## 1. NULL 체크
```sql
SELECT * FROM sample21 WHERE birthday IS NULL;
````

---

## 2. SELECT 기본 구조

```sql
SELECT 열 FROM 테이블명;
```

여러 열 조회:

```sql
SELECT col1, col2, col3 FROM 테이블명;
```

---

## 3. 행(ROW) 조건 조회 — WHERE

```sql
SELECT 열 FROM 테이블명 WHERE 조건식;
```

비교 연산자:

```sql
=      -- 같다
<>     -- 같지 않다
>=     -- 이상
<=     -- 이하
```

---

## 4. 전체 열 조회

```sql
SELECT * FROM 테이블명;
```

---

## 5. 논리 연산자

```sql
WHERE 조건1 AND 조건2;
WHERE 조건1 OR 조건2;
WHERE NOT 조건;
```

※ AND 연산이 OR보다 먼저 계산됨.

---

## 6. 부분 검색(패턴 매칭) — LIKE, %, _

문자열 시작/포함 검색:

```sql
SELECT * FROM 테이블명
WHERE 열 LIKE 'SQL%';   -- SQL로 시작하는 모든 문자열
```

언더스코어(_) 사용:

```sql
WHERE 열 LIKE 'A_';     -- A로 시작 + 글자 1개
```

% 문자를 검색하고 싶을 때(escape):

```sql
WHERE 열 LIKE '\%';
```

---

## 7. 문장 종료

```sql
;     -- 모든 SQL 문장은 세미콜론으로 끝남
```

---

## 8. 용어/명령 아님(터미널 명령) — DESC

```bash
DESC
```
