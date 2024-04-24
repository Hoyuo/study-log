# 7. Nullability

## 75. Null overview
- **null이란, "no value" "value가 없다"라는 뜻이다. 어떤 상황에서는 이 데이터가 상당히 유용할 때가 있다.**
- 간단한 예로 전화번호를 저장하는 `variable`이 있다. `String phone`이런 데이터 저장공간에 다음처럼 전화번호를 저장한다.

  ```Dart
  String phone = "01055555555";
  ```

- 그런데 만약에 전화번호가 없다면??? 물론 전화번호가 없을 땐, 우리가 원하는 데이터로 전화번호가 없다는 것을 다음처럼 표시할 수 있다.

  ```Dart
  String phone = "none";
  ```

- 문제는 다음과 같은 데이터를 다른 프로그래머가 자연스럽게 받아들이기보단, 프로그래머들 사이의 소통에 의해서 정확하게 이해 후 사용해야 한다. 만약에 `null`을 사용한다면, 이런 문제점이 말끔히 사라진다.

  ```Dart
  String phone = null;
  ```

- 여기에서 이런 에러를 볼 수 있다.

  ```
  A value of type 'Null' can't be assigned to a variable of type 'String'.
  ```

- `Dart 2.12`부터는 Sound Null Safety룰을 사용한다. 간단히 말하면, `null`이 가능한 데이터는 키워드를 사용할 때 이미 알 수 있다. 왜 이렇게 유용한 `null`을 막 사용할 수 없게 막아 놓았을까? 이유는 우리가 제작하는 프로그램에서 발생하는 대부분의 에러가 `null`때문이다. 유용하지만 이런 이유에서 `null`을 조심해서 사용할 수 있게 언어가 업그레이드 되었다. 다음 예를 통해 `null`의 에러 발생 상황을 보자.

  ```Dart
  class Car {
    int totalDistance = null;
  
    int getCurrentTotalDistance(){
      int thisTripDistance = 32;
      return totalDistance + thisTripDistance;
    }
  }
  ```

- 현재 `totalDistance`의 값이 없다. 이것과 `thisTripDistance`의 값을 더하게 되면... ㅎㅎ 에러발생!!
- 위 코드를 Visual Studio Code에 넣어보면 아래처럼 에러가 보인다.

!https://media.githubusercontent.com/media/thecodingpapa/Dart-Master-Course/master/pic/075/null.png?token=ALQMZVXIUFIQJMWP7PM6TODCZTW3I

- `Null`이 `int`값에 저장이 될 수 없다고 말한다.

## 76. Nullable
- Variable에 널 저장이 가능하게 할 수 있다.

  ```Dart
  int? postCode = null;
  String? name = null;
  double? myHeight = null;
  bool? haveMoney = null;
  User? user = null;
  ```

## 77. Handling nullable types

  ```Dart
  String? name;
  print(name.length);
  ```

위 코드를 에러때문에 실행시킬 수 없지만 그래도 실행시키면 아래와 같은 에러 메세지를 받는다.

  ```
  : Error: Property 'length' cannot be accessed on 'String?' because it is potentially null.
  bin/first_project.dart:5
  Try accessing using ?. instead.
  print(name.length);
             ^^^^^^
  ```

`null`인 값을 `String`처럼 사용한다고 에러메세지를 보여주고 있다. `Dart`언어에서 어떻게 `null`을 사용하는지 알아보자.

먼저 위와같은 경우는 아래처럼 고쳐서, `Compile-error`는 방지할 수 있다.

  ```Dart
  String? name;
  name = 'Victor';
  print(name.length);
  ```

`if-else`를 통해 `null`값을 체크할 수 있다.

  ```Dart
  bool isPositive(int? anInteger) {
    if (anInteger == null) {
      return false;
    }
    return !anInteger.isNegative;
  }
  ```

위 코드를 보면, `return !anInteger.isNegative;` 여기선 이미 `null`걱정은 안해도 된다.

## 78-1. Null aware operators 1
- If-null operator (??)

    ```Dart
    String? message;
    final text = message ?? 'Error';
      
    String text;
    if (message == null) {
      text = 'Error';
    } else {
      text = message;
    }
    ```

- Null-aware assignment operator (??=)

    ```Dart
    int? volume;
      
    volume = volume ?? 5;
      
    x = x + 1;
    x += 1;
      
    volume ??= 5;
    ```

- Null-aware access operator (?.)

    ```Dart
    int? age;
    print(age?.isNegative);
    ```

- Null-aware method invocation operator (?.)

    ```Dart
    int? age;
    print(age?.isNegative);
      
    print(age?.toDouble());
    ```

- Null assertion operator (!)

    ```Dart
    String nonNullableString = myNullableString!;
      
    bool? isBeautiful(String? item) {
      if (item == 'flower') {
        return true;
      } else if (item == 'garbage') {
        return false;
      }
      return null;
    }
      
    bool flowerIsBeautiful = isBeautiful('flower');
    bool flowerIsBeautiful = isBeautiful('flower')!;
    bool flowerIsBeautiful = isBeautiful('flower') as bool;
    bool flowerIsBeautiful = isBeautiful('flower') ?? true;
    ```

- Null-aware cascade operator (?..)

    ```Dart
    class User {
      String? name;
      int? id;
    }
    User user = User()
      ..name = 'Ray'
      ..id = 42;
    User? user;
    user
      ?..name = 'Ray'
      ..id = 42;
    //similar toString? lengthString = user?.name?.length.toString();
    ```

- Null-aware index operator (?[])

    ```Dart
    List<int>? myList = [1, 2, 3];
    myList = null;
    int? myItem = myList?[2];
    ```

## 79. Init non nullable

```Dart
class User {
  String name;
}

//Using initializers
class User {
  String name = 'anonymous';
}

//Using initializing formals
class User {
  User(this.name);
  String name;
}

//Using an initializer list
class User {
  User(String name)
    : _name = name;
  String _name;
}

//Using default parameter values
class User {
  User({this.name = 'anonymous'});
  String name;
}
class User {
  User([this.name = 'anonymous']);
  String name;
}

//Required named parameters
class User {
  User({required this.name});
  String name;
}
```

## 80. Nullable scope

  ```Dart
  class User {
    User({this.name});
    String? name;
  }
  ```

  - **No promotion for non-local variables**

  ```Dart
  //첫째코드
  bool isLong(String? text) {
    if (text == null) {
      return false;
    }
    return text.length > 100;
  }
  
  //둘째코드
  class TextWidget {
    String? text;
  
    bool isLong() {
      if (text == null) {
        return false;
      }
      return text.length > 100;// error
    }
  }
  ```

이 코드는 아래 에러를 발생한다.

  ```
  The property 'length' can't be unconditionally accessed because the receiver can be 'null'.
  ```

맨 위에 코드는 괜찮았는데, 왜일까??? 이유는 첫째코드의 `text`는 local variable이고, 둘째 코드의 `text`는 instance variable이다. 즉 둘째 코드의 `text`는 `isLong()`메소드 이외에 다른 장소에서도 변경이 가능하기 때문에 `text`값을 확인한 직후에 어떤 일이 벌어질지 모른다. 그래서 컴파일러는 에러를 표시해준다. 단지, 프로그래머 입장에서 보면 다른곳에는 사용되는 부분이 없기 때문에 계속 진행해도 될것같다. 이럴때 사용하는것이 바로 `!`이다.

  ```Dart
  //둘째코드 고친것
  class TextWidget {
    String? text;
  
    bool isLong() {
      if (text == null) {
        return false;
      }
      return text!.length > 100;// fixed
    }
  }
  ```

또 다른 방법으로는 local `text` variable을 만들어주고 변경이 가능하지 않게 한다.

  ```Dart
  //둘째코드 고친것
  class TextWidget {
    String? text;
  
    bool isLong() {
      final text = this.text;// shadowing
      if (text == null) {
        return false;
      }
      return text.length > 100;// fixed
    }
  }
  
  ```

## 81. Late keyword

  ```Dart
  class User {
    User(this.name);
  
    final String name;
    final int _secretNumber = _calculateSecret();
  
    int _calculateSecret() {
      return name.length + 42;
    }
  }
  ```

다음과 같은 에러가 발생한다.

  ```
  The instance member '_calculateSecret' can't be accessed in an initializer.
  ```

`late`키워드를 사용하면, 해결이 가능하다.

  ```Dart
  late final int _secretNumber = _calculateSecret();
  
  //또는class User {
    User(this.name) {
      _secretNumber = _calculateSecret();
    }
    late final int _secretNumber;
  // ...
  }
  ```

Dart에서 `late`키워드를 사용시 해당 데이터는 바로 생성되지 않고, 데이터에 처음으로 접근하기 바로 전에 생성된다.

  - **`late`키워드 사용시 주의할 점.**

프로그래머가 컴파일러한테, "나만 믿어 절대 생성되기 이전에는 사용 안할거야!" 이렇게 말해놓고, 해당 데이터가 생성되기도 전에 사용하면 안된다!

  ```Dart
  class User {
    late String name;
  }
  
  final user = User();
  print(user.name);
  ```

  - **`late`키워드 사용시 좋은 점.**

무거운 계산을 사용할지 안할지도 모르는데 미리 계산을 한 후에 기다리면 사용 안했을 땐, 리소스의 낭비이다. 이를 방지하기 위해 해당 계산결과가 사용되기 바로 전에 계산을 진행한다. 이를 코딩에서는 `lazy`라고 부른다. 결과값이 필요할때까지 기다렸다가 막판에서야 부랴부랴 계산을 진행한다.

  ```Dart
  class SomeClass {
    late String? value = doHeavyCalculation();
    String? doHeavyCalculation() {
  // do heavy calculation
    }
  }
  ```