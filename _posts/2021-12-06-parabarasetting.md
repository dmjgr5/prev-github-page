---
layout: post
title: Panabara 프로젝트 환경 설정
category: 08_ToyProject
tag: [Django]
---



![example](/assets/images/panabarabasic.png)

> Panabara 프로젝트를 진행하면서 유용한 팁들을 정리해 보고자 합니다.


---


### <U>sqllite3 초기화 및 기타 설정</U>

#### 1. 사전 삭제 파일
기존의 DB 정보 삭제와 초기화를 위해서 아래와 같은 절차로 진행한다.

    - migrations 폴더 내 `init.py` 외 파일
    - db.sqlite3


#### 2. migrate 실행

```
python manage.py makemigrations
python manage.py migrate
```

#### 3. Django Super User 생성

```
>python manage.py createsuperuser
Username (leave blank to use 'pinco'): xxxx
Email address: test@example.com
Password:xxxx
Password (again):xxxx
Superuser created successfully.
```

### <U>테이블 기본 정보 생성</U>

#### 1. StockBaseInfo 테이블

- 국내, 미국, 코인 전 종목의 기본 정보를 가져와 저장한다.

- `__init__.py` 주석 해제 후 stockinfo update : `python manage.py runserver --noreload`


#### 2. MyStocks, Balances 테이블

- 보유 종목, 월별 총액 정보를 엑셀 정보로 부터 가져온다.

- `txtuploader_banance.py`
    - 월별 잔액 정보를 Balances 테이블에 Insert 한다.

- `txtuploader_mystocks.py`
    - 보유 종목 정보를 MyStocks 테이블에 Insert 한다.
 



### <U>sqlite3 실행하기</U>
가상환경을 Activate 한 후, 아래 명령어로 테이블 정보를 조회한다. 테이블 조회는 해당 모델 앞에 `상위폴더_` 를 추가하여 조회한다.

```
> python manage.py dbshell

sqlite> .tables  

-- users 테이블 보기

sqlite> .schema examples_mystocks

sqlite> select * from auth_user;

sqlite> select * from examples_mystocks where author_id ='3';

sqlite> select * from examples_stockbaseinfo;

sqlite> select * from examples_MyStocks;

select * from examples_balances;

-- 유저별로 남긴 코멘트 조회 (join문)
sqlite> select users.naeme, comments.content
        from users join comments
        on comments.author_id = users.id;

-- 유저ID 1번이 남긴 코멘트 조회
sqlite> select users.naeme, comments.content
        from users join comments
        on comments.author_id = users.id
        where users.id=1;
```


### <U>Library 관련</U>
- YahooFinance 업데이트로 아래로 재설치 필요
    - 에러 내용 :  `json.decoder.jsondecodeerror expecting value line 1 column 1 (char 0)`
        - `pip install yfinance --upgrade --no-cache-dir`


### <U>bulk_update 관련</U>
- 일단 50 개씩 자르자.

    ```
    result = list(divide_list(update_queries,50)) # 이거 나중에 const 로 바꾸자.
    for rs in result :
        MyStocks.objects.bulk_update(rs, ['kcurrencyrate','kbuyprice','kcurprice','iunitcurprice',
    'ktotalcurprice','ktotalbuyprice','kprofitratio','ktotalprevbuyprice','ktotalprevprice','kprofitpreratio','iupdatedate'])
    ```

이 에러는 왜나는거지??
  File "d:\1_GitSource\PANABARA\pnbr_env\lib\site-packages\django\db\backends\sqlite3\base.py", line 383, in execute
    return Database.Cursor.execute(self, query, params)
django.db.utils.OperationalError: too many SQL variables
[07/Dec/2021 23:32:35] "GET /refresh/ HTTP/1.1" 500 305677