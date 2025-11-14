# SQL 첫걸음 2주차 — 코드 & 명령어 정리 (3장·4장)
# 개념 설명 링크: https://blog.naver.com/ewhanthbeot/223608295132

---

## 📌 1. 정렬 (ORDER BY)

```sql
ORDER BY 열이름;          -- 기본: 오름차순(ASC)
ORDER BY 열이름 DESC;     -- 내림차순 정렬
ORDER BY 열이름 ASC;      -- 오름차순(명시적)
````

여러 열 정렬:

```sql
ORDER BY 열1, 열2;
ORDER BY 열1 ASC, 열2 DESC;
```

NULL 정렬 순서(DBMS마다 다름)

---

## 📌 2. 행 제한 (LIMIT / OFFSET)

```sql
LIMIT 행개수;
LIMIT 행개수 OFFSET 시작행;
```

예)

```sql
LIMIT 10;               -- 첫 10개 행만
LIMIT 10 OFFSET 20;     -- 21번째 행부터 10개 출력
```

---

## 📌 3. 산술 연산 (+ - * / %)

연산자 우선순위:

* `* / %` → 먼저 계산
* `+ -` → 나중 계산

연산 결과 출력:

```sql
SELECT 열1, A * B;
SELECT 열1, A * B AS "에곱비";    -- 별명(alias)
```

연산 + 조건:

```sql
SELECT * FROM table WHERE A * B > 10;
```

반올림:

```sql
SELECT ROUND(열, 자리수);
```

NULL 연산:

* `NULL`이 포함된 계산 결과는 항상 `NULL`.

---

## 📌 4. 문자열 함수

문자열 결합:

```sql
SELECT CONCAT(열1, 열2);
```

문자열 일부 추출:

```sql
SUBSTRING(셀, 시작위치, 길이);
```

공백 제거:

```sql
TRIM(열);
```

문자 길이:

```sql
CHARACTER_LENGTH(열);
```

---

## 📌 5. 날짜 관련

현재 날짜/시간:

```sql
SELECT CURRENT_TIMESTAMP;
```

날짜 형변환:

```sql
SELECT TO_DATE('2024/10/06', 'YYYY/DD/MM');
```

날짜 덧셈·뺄셈 가능.

---

## 📌 6. CASE 문 (데이터 조건 변환)

```sql
CASE
  WHEN 조건1 THEN 값1
  WHEN 조건2 THEN 값2
  ELSE 값3
END
```

ELSE 생략 시:

* 해당되지 않는 경우는 전부 `NULL`.

NULL 처리 편의:

```sql
COALESCE(열, 대체값);
```

---

## 📌 7. INSERT / DELETE / UPDATE

### 행 추가

```sql
INSERT INTO 테이블명(열1, 열2, ...)
VALUES (값1, 값2, ...);
```

### 행 삭제

```sql
DELETE FROM 테이블명 WHERE 조건;
```

### 값 갱신

```sql
UPDATE 테이블명
SET 열1 = 값1, 열2 = 값2
WHERE 조건;
```

* `=` 는 대입 연산자

---

## 📌 8. 물리삭제 vs 논리삭제 (개념)

* **물리삭제**: 데이터를 완전히 제거하는 방식
* **논리삭제**: 삭제 플래그 사용, 실제 데이터는 남음

(코드 없음 → 설계 개념)

---

## 📌 9. MySQL 클라이언트 명령 (실행 관련)

MySQL 종료:

```sql
exit
```
