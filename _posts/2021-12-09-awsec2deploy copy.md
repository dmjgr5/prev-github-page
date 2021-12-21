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


 
### 주요 예제




![example](/assets/images/flutterex1.png)

```

import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'BBANTO',
      home: Grade(),
    );
  }
}

class Grade extends StatelessWidget {
  const Grade({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.amber[800],
      appBar: AppBar(
        title: Text('BBANTO'),
        backgroundColor: Colors.amber[700],
        centerTitle: true,
        elevation: 0.0,
      ),
      body: Padding(
        padding: EdgeInsets.fromLTRB(30.0, 40.0, 0.0, 0.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Center(
              child: CircleAvatar(
                backgroundImage: AssetImage(
                  'assets/bc9.png'
                ),
                radius: 60.0,

              ),
            ),
            Divider(
              height: 60.0,
              color: Colors.grey[850],
              thickness: 0.5,
              endIndent: 30.0,
            ),
            Text('NAME',
               style: TextStyle(
                 color: Colors.white,
                 letterSpacing: 2.0
               )
            ),
            SizedBox(
              height: 10.0,
            ),
            Text('BBANTO',
            style: TextStyle(
              color: Colors.white,
              letterSpacing: 2.0,
              fontSize: 28.0,
              fontWeight: FontWeight.bold
            ),),
            SizedBox(
              height: 30,
            ),
            Text('BBANTOPOWER LEVEL',
                style: TextStyle(
                    color: Colors.white,
                    letterSpacing: 2.0
                )
            ),
            SizedBox(
              height: 10.0,
            ),
            Text('14',
              style: TextStyle(
                  color: Colors.white,
                  letterSpacing: 2.0,
                  fontSize: 28.0,
                  fontWeight: FontWeight.bold
              ),
            ),
          SizedBox(
            height: 30.0,
          ),
          Row(
            children: [
              Icon(Icons.check_circle_outline),
              SizedBox(
                width: 10.0,
              ),
              Text('using lightsaber',
              style: TextStyle(
                fontSize: 16.0,
                letterSpacing: 1.0,
              ),),
            ],
          ),
            Row(
              children: [
                Icon(Icons.check_circle_outline),
                SizedBox(
                  width: 10.0,
                ),
                Text('face hero tatoo',
                  style: TextStyle(
                    fontSize: 16.0,
                    letterSpacing: 1.0,
                  ),),
              ],
            ),
            Row(
              children: [
                Icon(Icons.check_circle_outline),
                SizedBox(
                  width: 10.0,
                ),
                Text('fire flagem',
                  style: TextStyle(
                    fontSize: 16.0,
                    letterSpacing: 1.0,
                  ),),
              ],
            ),
            Center(
              child: CircleAvatar(
                backgroundImage: AssetImage(
                  'assets/bcw.jpg'
                ),
                radius: 40.0,
                backgroundColor: Colors.amber[800],
              ),
            )
          ],
        ),
      ),
    );
  }
}



```