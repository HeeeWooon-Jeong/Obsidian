[오라클 오토인크리먼트](https://gent.tistory.com/393)

```
CREATE TABLE T_URL (
  URL_SEQ NUMBER(11) PRIMARY KEY,
  URL_NAME VARCHAR2(1000),
  MLCS_STTS CHAR(1) DEFAULT 'Y',
  URL_YN CHAR(1) DEFAULT 'Y',
  URL_CNT NUMBER,
  URL_DATE TIMESTAMP
  );
```

- 조회수
```
UPDATE T_URL SET  
   LEAD_CNT = LEAD_CNT+1  
WHERE URL_SEQ = 1;
```

---

최대 url 바이트 = 2175
