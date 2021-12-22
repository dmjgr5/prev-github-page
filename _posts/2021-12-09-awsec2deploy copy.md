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

#### 코드 정렬
- 단축키 Ctl+Alt+L을 누르면 아래와 같이 자동정렬이 됩니다. 

#### Flutter Layout 학습 사이트
- [https://medium.com/flutter-community/flutter-layout-cheat-sheet-5363348d037e](https://medium.com/flutter-community/flutter-layout-cheat-sheet-5363348d037e)

### 주요 예제



#### 기본 레이아웃

![example](/assets/images/flutterex1.png)

```java

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


#### App Bar 메뉴

![example](/assets/images/flutterex2.png)

```java
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'AppBar',
      theme: ThemeData(
        primarySwatch: Colors.red
      ),
      home: MyPage(),
    );
  }
}

class MyPage extends StatelessWidget {
  const MyPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Appbar icon menu'),
        centerTitle: true,
        elevation: 0.0,
        leading: IconButton(
          icon: Icon(Icons.menu),
          onPressed: () {
            print('menu button clicked');
          },
        ),
        actions: [

          IconButton(
            icon: Icon(Icons.shopping_cart),
            onPressed: () {
              print('shopping cart button clicked');
            },
          ),
          IconButton(
            icon: Icon(Icons.search),
            onPressed: () {
              print('search button clicked');
            },
          )
        ],
      ),
    );
  }
}
```



#### Drawer 메뉴

![example](/assets/images/flutterex3.png)

```java
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'AppBar',
      theme: ThemeData(
        primarySwatch: Colors.red
      ),
      home: MyPage(),
    );
  }
}

class MyPage extends StatelessWidget {
  const MyPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Appbar icon menu'),
        centerTitle: true,
        elevation: 0.0,

        actions: [
          IconButton(
            icon: Icon(Icons.shopping_cart),
            onPressed: () {
              print('shopping cart button clicked');
            },
          ),
          IconButton(
            icon: Icon(Icons.search),
            onPressed: () {
              print('search button clicked');
            },
          )
        ],
      ),
      drawer: Drawer(
        child: ListView(
          padding: EdgeInsets.zero,
          children: [
            UserAccountsDrawerHeader(
              currentAccountPicture: CircleAvatar(
                backgroundImage: AssetImage('assets/bc9.png'),
                backgroundColor: Colors.white,
              ),
              otherAccountsPictures: [
                CircleAvatar(
                  backgroundImage: AssetImage('assets/bcw.jpg'),
                  backgroundColor: Colors.white,
                ),
                // CircleAvatar(
                //   backgroundImage: AssetImage('assets/bcw.jpg'),
                //   backgroundColor: Colors.white,
                // )
              ],
              accountName: Text('BAANTO'),
              accountEmail: Text('aaa@gmail.com'),
              onDetailsPressed: (){
                print('arrow is clicked..');
              },
              decoration: BoxDecoration(
                color: Colors.red[200],
                borderRadius: BorderRadius.only(
                  bottomLeft: Radius.circular(40.0),
                  bottomRight: Radius.circular(40.0),
                )
              ),
            ),

            ListTile(
              leading: Icon(Icons.home,
              color: Colors.grey[800]),
              title: Text('Home'),
              onTap: () {
                print('Home is clicked..');
              },
              trailing: Icon(Icons.add),

            ),
            ListTile(
              leading: Icon(Icons.settings,
                  color: Colors.grey[800]),
              title: Text('Setting'),
              onTap: () {
                print('Setting is clicked..');
              },
              trailing: Icon(Icons.add),

            ),
            ListTile(
              leading: Icon(Icons.question_answer,
                  color: Colors.grey[800]),
              title: Text('Q&A'),
              onTap: () {
                print('Q&A is clicked..');
              },
              trailing: Icon(Icons.add),

            )
          ],
        ),
      ),
    );
  }
}
```


#### Navigator 페이지 이동

![example](/assets/images/flutterex4.png)

```java
import 'package:flutter/material.dart';
import 'package:fluttertoast/fluttertoast.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'SnackBar',
      theme: ThemeData(primarySwatch: Colors.blue),
      home: FirstPage(),
    );
  }
}

class FirstPage extends StatelessWidget {
  const FirstPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context2) {
    return Scaffold(
      appBar: AppBar(
        title: Text('frist page'),
      ),
      body: Center(
        child: RaisedButton(
          child: Text('Go to the second page'),
          onPressed: () {
            Navigator.push(
                context2, MaterialPageRoute(builder: (_) => SecondPage()));
          },
        ),
      ),
    );
  }
}

class SecondPage extends StatelessWidget {
  const SecondPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext ctx) {
    return Scaffold(
      appBar: AppBar(
        title: Text('second page'),
      ),
      body: Center(
        child: RaisedButton(
          child: Text('Go to the first page'),
          onPressed: () {
            Navigator.pop(ctx);
          },
        ),
      ),
    );
  }
}

```



#### Multi 페이지 구성 및 이동

![example](/assets/images/flutterex5.png)

`main.dart`
```java

import 'package:coding_chef1st/ScreenB.dart';
import 'package:coding_chef1st/ScreenC.dart';
import 'package:flutter/material.dart';
import 'package:coding_chef1st/ScreenA.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      initialRoute: '/',
      routes: {
        '/' : (context) => ScreenA(),
        '/b': (context) => ScreenB(),
        '/c': (context) => ScreenC()
      },
    );
  }
}

```

`ScreenA.dart`
```java
import 'package:flutter/material.dart';

class ScreenA extends StatelessWidget {
  const ScreenA({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('ScreenA')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            RaisedButton(
              color: Colors.red,
              child: Text('Go to Screen B'),
              onPressed: (){
                Navigator.pushNamed(context, '/b');
              },
            ),
            RaisedButton(
              color: Colors.red,
              child: Text('Go to Screen C'),
              onPressed: (){
                Navigator.pushNamed(context, '/c');
              },
            )
          ],
        )
      ),
    );
  }
}

```

`ScreenB.dart`
```java
import 'package:flutter/material.dart';

class ScreenB extends StatelessWidget {
  const ScreenB({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('ScreenB')),
      body: Center(
        child: Text(
          'ScreenB',
          style: TextStyle(fontSize: 24.0),
        ),
      ),
    );
  }
}

```

`ScreenC.dart`
```java
import 'package:flutter/material.dart';

class ScreenC extends StatelessWidget {
  const ScreenC({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('ScreenC')),
      body: Center(
        child: Text(
          'ScreenC',
          style: TextStyle(fontSize: 24.0),
        ),
      ),
    );
  }
}

```

코딩셰프 순한맛 24 강부터 시작하기
