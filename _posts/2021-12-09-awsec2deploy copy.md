---
layout: post
title: Flutter 알아보기
category: 02_Programming
tag: [Android, Dart]
---



![example](/assets/images/flutter.png)

> 앱을 구축하는데 있어서 주된 걸림돌인 Android, iOS 등의 상이한 아키텍쳐가 있었으나, 구글에서 개발한 `Flutter` 는 이를 보완하고 보다 직관적으로 개발을 할 수 있게 한다. 기본적인 내용 및 개발 시 참조해야 할 만한 사항을 정리하고자 합니다..

---
 
### 주요 에러 해결 방법

#### `don't support null safety: - package:english_words` 에러
- Run --> Edit Configurations --> Add Additional Run args 에서 `--no-sound-null-safety` 를 추가한다.

#### 이후..