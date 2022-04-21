---
layout: post
title: Django 백엔드 서버 프로젝트 생성하기
category: 05_Cloud
tag: [Django, backend]
---


Django 서버 구축

---

- 가상환경 세팅

	- 프로젝트 폴더 생성하기
	- 프로젝트 폴더 내 가상환경 생성하기
		```dcjam@DESKTOP-605KI17 MINGW64 /d/5_Django/quiz_backend_test
			$ python -m venv venv
		```
	- 가상환경 활성화 하기
		`actiate`
	- 장고, 장고프레임워크 설치하기
		`(venv) D:\5_Django\quiz_backend_test\venv\Scripts>pip install django djangorestframework`
	- 프로젝트 시작
		`django-admin startproject myapi .`
	- 앱시작하기
		`python manage.py startapp quiz`


1) 가상환경 만들기
먼저 장고 프로젝트에 필요한 플로그인 등의 버전을 관리하기 위해 가상환경을 만들어보도록 하겠습니다. 가상환경 없이 그냥 설치해버리면 프로젝트마다의 프로그램 버전이 달라서 문제가 발생할 수 있습니다. 한 프로젝트마다 해당 프로젝트에 맞는 도구들을 넣는 공구함이라고 생각하면 됩니다.

(1) 바탕화면 혹은 원하는 장소에 프로젝트 폴더를 만듭니다. (cmd를 활용해 만드셔도 무방합니다.)
(2) VScode를 열고, Ctrl + Shift + E를 눌러 만든 폴더를 불러옵니다.
(3) VScode에서 Ctrl + `를 눌러 터미널을 실행시킵니다.
(4) 아래와 같이 입력해 만든 폴더 내에 가상환경 폴더를 만듭니다.




(5) 설치가 끝나면 f1을 누르고 Select Interpreter를 치시고 Python: Select Interpreter를 선택, 아래와 같은 목록이 뜨면 생성했던 가상환경 폴더와 같은 이름이 있는 항목을 선택합니다. *만약 아래와 같이 나타나지 않는다면 VScode를 종료 후 실행시켜보시기 바랍니다.


(6) 선택 후 단축키(Ctrl + Shift + `)를 눌러 새로운 터미널을 실행시킵니다. 혹은 단축키(Ctrl + `)를 눌러 터미널을 실행시킨 후 우측 상단의 + 모양을 눌러 터미널을 실행시킵니다. 


* 만약 이 과정에서 오류(venv\Script\activate.ps1 파일을 로드할 수 없습니다.)가 생긴다면, 윈도우 검색을 이용해 Windows PowerShell을 관리자 권한으로 실행한 후 다음을 입력하면 됩니다. 입력한 뒤에는 다시 6번을 실행해주시면 됩니다.


오류 발생시 관리자 권한으로 powershell 실행
 

 

2) 장고(Django) 설치 및 실행
(1) 위의 과정이 끝났으면 가상환경 터미널에서 장고를 설치하도록 하겠습니다.
(2) 장고 설치를 위해 아래와 같이 입력합니다.


(3) 설치가 완료된 화면입니다. 아래 뜨는 WARNING은 pip 버전이 낮아서 생기는 경고인데, pip을 최신버전으로 업데이트 해주면 해결됩니다.


(4) 본격적으로 장고 프로젝트를 생성하도록 하겠습니다. 시작하기에 앞서 TEST폴더 밑에 FirstProject라는 폴더를 만들어 이곳에 Project를 실행하도록 하겠습니다. 실행 후에는 폴더를 FirstProject로 이동하도록 하겠습니다.


폴더를 만들 때는 "mkdir 폴더명" 을 입력하면 됩니다.

폴더를 이동할 때는 "cd 폴더명"으로 이동하고, 하위폴더로 이동할 때는 "cd .."을 입력하면 됩니다.
