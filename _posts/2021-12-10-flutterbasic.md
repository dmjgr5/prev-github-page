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

#### Const 와 Final 의 차이점
- Cont 변수 : 컴파일 시 상수가 된다. 런타임 시에도 변하지 않는다. (Compile-time Constant)
- Final 변수 : 런타임 시 상수가 된다. 변경 시, reBuild 되어야 한다. (Run-time Constant)


#### 자료구조 종류

- List, Set

#### Thread
- 프로세스 내에서 실행되는 흐름의 단위
- `Dart` 는 싱글스레드로 운영되는 언어


#### Future, Async, await
- Future 클래스는 비동기 작업을 할 때 사용
- Future 는 일정 소요시간 후에 실제 데이터나 에러를 반환
- async 클래스는 await 메서드를 가지고 있음
  - await 로 선언된 메서드는 응답이 처리될 때까지 대기
- 예제
```python
import 'dart:io';

void main() {
  showData();
}

void showData() async {
  startTask();
  String account = await accessData();
  fetchData(account);
}

void startTask() {
  String info1 = '요청수행 시작';
  print(info1);
}

Future<String> accessData() async {
  String account = '';

  Duration time = Duration(seconds: 3);

  if (time.inSeconds > 2) {
    // sleep(time);
    await Future.delayed(time, () {
      account = '8500만원';
      print(account);
    });
  } else {
    String info2 = '데이터를 가져왔습니다';
    print(info2);
  }
  return account;
}

void fetchData(String account) {
  String info3 = '잔액은 $account 원입니다..';
  print(info3);
}

```

`출력`
```bash
요청수행 시작
8500만원
잔액은 8500만원 원입니다..
```




### 주요 예제



#### 기본 레이아웃

![example](/assets/images/flutterex1.png)

```python

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

```python
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

```python
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

```python
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
```python

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
```python
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
```python
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
```python
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



#### 스낵바 표시 및 스낵바 버튼 페이지 이동

![example](/assets/images/flutterex6.png)

```python
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      theme: ThemeData(primarySwatch: Colors.blue),
      home: MyPage(),
    );
  }
}

class MyPage extends StatelessWidget {
  const MyPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Scaffold Messenaer')),
      body: HomeBody(),
      floatingActionButton: FloatingActionButton(
        onPressed: () {
          ScaffoldMessenger.of(context).showSnackBar(SnackBar(
            content: Text('Like a new snalckslfdsf'),
            duration: Duration(seconds: 5),
            action: SnackBarAction(
              label: 'Undo',
              onPressed: () {
                Navigator.push(context,
                    MaterialPageRoute(builder: (context) => ThirdPage()));
              },
            ),
          ));
        },
        child: Icon(Icons.thumb_up),
      ),
    );
  }
}

class HomeBody extends StatelessWidget {
  const HomeBody({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Center(
      child: ElevatedButton(
        child: Text('Go to second page'),
        onPressed: () {
          Navigator.push(
              context, MaterialPageRoute(builder: (context) => SecondPage()));
        },
      ),
    );
  }
}

class SecondPage extends StatelessWidget {
  const SecondPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(title: Text('Second Page')),
        body: Center(
          child: Text(
            "종하요가 추가되었습니다",
            style: TextStyle(fontSize: 20.0, color: Colors.redAccent),
          ),
        ));
  }
}

class ThirdPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return ScaffoldMessenger(
      child: Scaffold(
          appBar: AppBar(title: Text('third Page')),
          body: Builder(builder: (context) {
            return Center(
              child: Column(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Text(
                    "종하요를 취소하시겠습니다.?",
                    style: TextStyle(fontSize: 20.0, color: Colors.yellow),
                  ),
                  ElevatedButton(
                      onPressed: () {
                        ScaffoldMessenger.of(context).showSnackBar(SnackBar(
                          content: Text("좋아요가 취소되었습니다."),
                          duration: Duration(seconds: 3),
                        ));
                      },
                      child: Text("취소하기"))
                ],
              ),
            );
          })),
    );
  }
}

```

#### 버튼 종류 및 표현

![example](/assets/images/flutterex7.png)

```python
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      theme: ThemeData(primarySwatch: Colors.blue),
      home: MyButtons(),
    );
  }
}

class MyButtons extends StatelessWidget {
  const MyButtons({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Buttons'),
        centerTitle: true,
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            TextButton(
              // onPressed: () {
              //   print("text button clicked");
              // },
              onLongPress: () {
                print("text button clicked");
              },
              child: Text('TextButton', style: TextStyle(fontSize: 20.0)),
              style: TextButton.styleFrom(
                primary: Colors.red,
                // backgroundColor: Colors.blue
              ),
              onPressed: () {},
            ),
            ElevatedButton(
              onPressed: null,
              child: Text('ElevatedButton'),
              style: ElevatedButton.styleFrom(
                  primary: Colors.orangeAccent,
                  shape: RoundedRectangleBorder(
                    borderRadius: BorderRadius.circular(15.0),
                  ),
                  elevation: 0.0),
            ),
            OutlinedButton(
              onPressed: () {
                print('OutLIned Button');
              },
              child: Text('OutLinedButton'),
              style: OutlinedButton.styleFrom(
                  primary: Colors.green,
                  side: BorderSide(color: Colors.black87, width: 2.0)),
            ),
            TextButton.icon(
              onPressed: () {
                print('Icon Button');
              },
              icon: Icon(
                Icons.home,
              ),
              label: Text('Go to Home'),
              style: OutlinedButton.styleFrom(
                  primary: Colors.black),
            ),
            ButtonBar(
              alignment: MainAxisAlignment.center,
              buttonPadding: EdgeInsets.all(20),
              children: [
                TextButton(onPressed: (){},
                    child: Text('Text Button')),
                ElevatedButton(onPressed: (){},
                    child: Text('ElevatedButton'))
              ],
            )
          ],
        ),
      ),
    );
  }
}

```


#### 예제) Dice Game

![example](/assets/images/flutterex8.png)

![example](/assets/images/flutterex9.png)

`main.dart`
```python
import 'package:flutter/material.dart';
import 'dice.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Dice game',
      home: LogIn(),
    );
  }
}

class LogIn extends StatefulWidget {
  @override
  State<LogIn> createState() => _LogInState();
}

class _LogInState extends State<LogIn> {
  TextEditingController controller = TextEditingController();
  TextEditingController controller2 = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Log in'),
        backgroundColor: Colors.redAccent,
        centerTitle: true,
        leading: IconButton(icon: Icon(Icons.menu), onPressed: () {}),
        actions: <Widget>[
          IconButton(icon: Icon(Icons.search), onPressed: () {})
        ],
      ),
      body: Builder(
        builder: (context) {
          return GestureDetector(
            onTap: () {
              FocusScope.of(context).unfocus();
            },
            child: SingleChildScrollView(
              child: Column(
                children: [
                  Padding(padding: EdgeInsets.only(top: 50)),
                  Center(
                    child: Image(
                        image: AssetImage('image/chef.gif'),
                        width: 170.0,
                        height: 190.0),
                  ),
                  Form(
                      child: Theme(
                          data: ThemeData(
                              primaryColor: Colors.teal,
                              inputDecorationTheme: InputDecorationTheme(
                                  labelStyle: TextStyle(
                                      color: Colors.teal, fontSize: 15.0))),
                          child: Container(
                            padding: EdgeInsets.all(40.0),
                            child: Column(
                              children: [
                                TextField(
                                  controller: controller,
                                  decoration: InputDecoration(
                                      labelText: 'Enter "dice"'),
                                  keyboardType: TextInputType.emailAddress,
                                ),
                                TextField(
                                  controller: controller2,
                                  decoration: InputDecoration(
                                      labelText: 'Enter Password'),
                                  keyboardType: TextInputType.text,
                                  obscureText: true,
                                ),
                                SizedBox(height: 40.0),
                                ButtonTheme(
                                    minWidth: 100.0,
                                    height: 50.0,
                                    child: RaisedButton(
                                        color: Colors.orangeAccent,
                                        child: Icon(Icons.arrow_forward,
                                            color: Colors.white, size: 35.0),
                                        onPressed: () {
                                          if (controller.text == 'dice' &&
                                              controller2.text == '1234') {
                                            Navigator.push(
                                                context,
                                                MaterialPageRoute(
                                                    builder: (BuildContext
                                                            context) =>
                                                        Dice()));
                                          } else if (controller.text ==
                                                  'dice' &&
                                              controller2.text != '1234') {
                                            showSnackBar2(context);
                                          } else if (controller.text !=
                                                  'dice' &&
                                              controller2.text == '1234') {
                                            showSnackBar3(context);
                                          } else {
                                            showSnackBar(context);
                                          }
                                        }))
                              ],
                            ),
                          )))
                ],
              ),
            ),
          );
        },
      ),
    );
  }
}

void showSnackBar(BuildContext context) {
  Scaffold.of(context).showSnackBar(SnackBar(
    content: Text(
      '로그인 정보를 다시 확인하세요',
      textAlign: TextAlign.center,
    ),
    duration: Duration(seconds: 2),
    backgroundColor: Colors.blue,
  ));
}

void showSnackBar2(BuildContext context) {
  Scaffold.of(context).showSnackBar(SnackBar(
    content: Text(
      '비밀번호가 일치항ㄶ음',
      textAlign: TextAlign.center,
    ),
    duration: Duration(seconds: 2),
    backgroundColor: Colors.blue,
  ));
}

void showSnackBar3(BuildContext context) {
  Scaffold.of(context).showSnackBar(SnackBar(
    content: Text(
      'dice 정보 확인',
      textAlign: TextAlign.center,
    ),
    duration: Duration(seconds: 2),
    backgroundColor: Colors.blue,
  ));
}

```

`dice.dart`
```python
import 'package:flutter/material.dart';
import 'dart:math';
import 'package:fluttertoast/fluttertoast.dart';

class Dice extends StatefulWidget {
  const Dice({Key? key}) : super(key: key);

  @override
  State<Dice> createState() => _DiceState();
}

class _DiceState extends State<Dice> {
  int leftDice = 1;
  int rightDice = 1;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.redAccent,
      appBar: AppBar(
        backgroundColor: Colors.redAccent,
        title: Text('Dice Game'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Padding(
              padding: EdgeInsets.all(32.0),
              child: Row(
                children: [
                  Expanded(child: Image.asset('image/dice$leftDice.png')),
                  SizedBox(width: 20.0),
                  Expanded(child: Image.asset('image/dice$rightDice.png')),
                ],
              ),
            ),
            SizedBox(height: 60.0),
            ButtonTheme(
              minWidth: 100.0,
              height: 60.0,
              child: RaisedButton(
                child: Icon(
                  Icons.play_arrow,
                  color: Colors.white,
                  size: 50.0,
                ),
                onPressed: () {
                  setState(() {
                    leftDice = Random().nextInt(6) + 1;
                    rightDice = Random().nextInt(6) + 1;
                  });
                  showToast(
                      "Left Dice : {$leftDice} , Right Dice : {$rightDice}");
                },
                color: Colors.orangeAccent,
              ),
            )
          ],
        ),
      ),
    );
  }
}

void showToast(String message) {
  Fluttertoast.showToast(
      msg: message,
      backgroundColor: Colors.white,
      textColor: Colors.black,
      toastLength: Toast.LENGTH_SHORT,
      gravity: ToastGravity.BOTTOM);
}
```


코딩셰프 조금 매운맛 13강부터 시작하기
