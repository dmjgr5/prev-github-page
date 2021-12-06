---
layout: post
title: Panabara 프로젝트 환경 설정
category: 08_ToyProject
tag: [Django]
---



![example](/assets/images/panabarabasic.png)
>
> Panabara 프로젝트를 진행하면서 유용한 팁들을 정리해 보고자 합니다.
>

---


### sqllite3 초기화 및 기타 설정

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

### 테이블 기본 정보 생성

#### 1. StockBaseInfo 테이블

- 국내, 미국, 코인 전 종목의 기본 정보를 가져와 저장한다.

- `__init__.py` 주석 해제 후 stockinfo update : `python manage.py runserver --noreload`


#### 2. MyStocks, Balances 테이블

- 보유 종목, 월별 총액 정보를 엑셀 정보로 부터 가져온다.


    ```
    txtuploader_banance.py, txtuploader_mystocks.py 실행
    ```
