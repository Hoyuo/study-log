# 6. Classes

## 45. What is class
- class를 배우면 oop -> object of programing
- class / instance class 붕어빵을 만드는 틀 instance, object 만들어지는 붕어빵
- 예) 테슬라 공장 = class / 각각의 만들어진 차들 = instance, object
- 코드 상으로 보았을 때, 테슬라를 만들려면 '공장'이 필요하다.

```Text
class Tesla {
//...
}
```

- 즉, 설계 도면을 class, 만들어진 것을 instance or object

## 46. Custom data type
- 이제까지 배웠던 data type과 새로 만들어 줄 custom data type 차이점.(class 차이점)
- int, double, string, bool, enum
- enum -> object와 비슷하다 int, double, string, bool -> Dart언어에서는 object
- custom data type이 필요할 때 class 키워드를 사용한다. 각각의 data type 기능이 다 다르기때문에 custom으로 만든 data들의 기능을 {}안에 명시해 준다.

## 47. Constructor in class
- class안에 있는 주문서를 constructor라고 하며, function과 함수의 일종이다. constructor를 통해 option 값을 전달해 줄 수 있다.

```Text
class Teslea {
    String color = "";
    
    Teslea(String selectedColor) {
        color = selectedColor;
    }
}
```

## 48. Omitted keyword for constructor
- new 키워드를 통해 생성자라고 표시하는데. Dart언어에서는 생략할 수 있기 때문에 안써줘도 된다.

## 49. Change properties in instance
- 지정해준 색이 아닌 다른 색으로 변경해 주기

```Text
myTesla.color = 'pink';
print(myTesla.color);
```

## 50. You can change any data in object
- String이 아닌, 다른 data 넣어보기.
- constructor를 통해 주문을 할 때는 값을 변경해 줄 수 없다.

```Text
print(myTesla.batterySize);
myTesla.batterySize = 200;
print(myTesla.batterySize);

class Tesla {
    String color = "white";
    int batterySize = 100;
}
```

- 다른 Data Type도 바꿔줄 수 있다.

## 51. Override to string function
- 각각의 모든 data는 object이다.
- object안에 어떤 class로 생성을 하든 기본적으로 들어가 있는 toString이라는 함수(function) -> 자동적으로 toString
- toString을 정확히 명시해주고 override를 해 줘야 한다.

```Text
@override
String toString() {
    return color;
}
```

## 52. Write a function in a class
- 세부적 기능을 적어줄 수 있고, 바디{} 안에 기능이 어떤 작업을 하는지 명시할 수 있다. 이러한 식으로 function을 작성하고 사용할 수 있다.

## 53. Constructor is function
- Constructor도 function의 일종이다.
- Constructor와 function의 다른 점은 function의 이름을 어떻게 짖느냐!이다.
- 다른 function의 이름들은 노란색으로 보이는데 constructor 이름은 class 명과 정확히 일치한다. 그러면 function 자체는 constructor가 됨. 앞에 return 값도 없어서 자동적으로 constructor를 실행한 후에 class instance를 생성해서 return을 해 준다.

## 54. Short constructor
- Constructor에서 생성된 instance 안(color)에 전달을 해 주어라.

```Text
class Tesla {
    String color = "white";
    int batterySize = 100;

    Tesla(this.color);
}
```

## 55. Named constructor
- 색을 항상 지정해줘야 하는데, 안해주고 누군가 주문했을 떄, 기본값으로 주문하게 하고 싶다.
    - 만약 다른 방식으로 주문서를 작성할 수 있게끔 만들어주고 싶다면? = named constructor가 있다.

```Text
Tesla.defaultOption() {
    color = "black";
    batterySize = 120;
}
```

## 56. Forward constructor
- 기본 값을 데이터 생성을 해 주면서 color와 batterySize를 지정해줬었는데, 기본값을 지워주고 변수만 생성해 주면 빨간줄이 생긴다.
- 왜냐하면 'this.color'로 색을 주어줬는데 중요한 것은 int라는 변수, batterySize가 int 뒤에 물음표가 없기 떄문에 null이 될 수 없다. 즉, 빈 변수로 생성될 수 없다는 것이다. = '?'를 사용하면 빨간 줄이 사라진다.
- 예를 들어, Null을 원하지 않고 데이터가 지정되어야 한다면,

```Text
class Tesla {
    String color;
    int batterySize;
}
```

아래와 같이 반드시 값을 지정해주어야 한다.

```Text
Tesla(this.color, this.batterySize);
```

color 혹은 batterySize를 주문서마다 반드시 지정해주어야 한다고 했을 때. 위 코드와 같이 만들어준다.

option 값일 때는 option 값으로 주되, 기본 값을 넣어줄 수 있다. (함수를 다룰 때 다 했었다. option 값에 '=' 을 넣어준다. )

```Text
Tesla(this.color, [this.batterySize]);
```

## 57. Required named parameter
- function 안에 parameter 넣어주기. function이니까 option 값으로도 넣어줄 수 있고, named parameter로 넣어줄 수 있다.
    - named parameter로 바꿔주니까 값이, color라는 변수 자체가 null 값을 받아들일 수 없음.
    - 따라서, named parameter를 반드시 넣어줘야하는 것으로 바꿔주고 싶을 때, required라는 키워드를 생성할 변수 앞에 넣어주면 된다.

    ```Text
    class Tesla {
        String color;
        Tesla({required this.color});
    }
    ```

## 58. Default value for option params in constructor
- Q1. function을 할 때, parameter option 값이랑 named parameter를 해줬을 때, 기본값인 default 값을 지정해주는 방법이 있었는데 풀어보기.

```Text
class Tesla {
    String color;
    
    Tesla({this.color = "White"})
    Tesla.defaultOption() : Tesla();
}
```

## 59. Separate code into files
- 코딩을 하면서 한 파일 안에 모든 코드를 다 넣지 않고, 여러 파일에 나누어서 넣는다.
- 파일을 하나 생성해보자.
    - bin 안에 user.dart 파일 생성
- main function 안에 body가 있고 그 안에 user class instance를 생성해서 사용하고 있다. user class를 복사 + 잘라넣기하여 새로 생성한 파일 안에 넣어준다.
- first_project.dart 파일에서는 user class가 안보여서 찾고 있는데 user class가 user.dart파일에 있다고 알려줘야 한다. import를 해서 user file 위치를 알려준다. file를 작성하는 해당 파일을 기준으로 import를 작성한다.

```Text
import 'tesla.dart';
```

## 60. Private variable
- 변수 명을 지어줄 때, 앞에 변수를 `_`를 줄 수 있다. Dart 언어에서 *`_`* 는 private 키워드와 똑같은 기능을 한다. = '_name'
- 변수 명과 `_`를 준 변수명의 차이점은? user instance를 생성 해 주고, 그 안에 있는 값을 접근해 주려고 보니까 user 값(name)이 있었는데 .을 찍어도 보이지 않음. *`_`* 을 주면 name 값이 사라지고, `_`를 안주면 보인다. = 또한 *`_`*는 다른 파일에서 접근할 수 없게 만든다. class 안에서만 접근할 수 있게 만드는 것이 아니라, 다른 파일에서 접근을 못하도록 만들었다.

```Text
class User {
    String _name;
}
```

## 61. Initializer
- private 변수를 어떻게 constructor에서 생성해 줄 수 있을까?
- 받아온 name을 body가 실행되기 전에 '_name'에 지정해 주는 것이다.
- :(콜롬)을 찍어주고 '_name' 변수에 값을 지정해 줄 것이다.
    - name이라는 값을 _name에다가 지정.

```Text
User({String name = "Victor"}) : _name = name;
```

## 62. Initializer in depth
- name, isFemle 값을 생성자의 parameter 부분을 통해 받아온다. 전달이 되어서 받아 오면 victor가 아니라, 받아온 값으로. true가 아닌 받아온 값이 된다.

```Text
User({String name = "Victor", bool ifFemale = true})
```

```Text
User({String name = "받아온 값", bool ifFemale = 받아온 값})
```

## 63. Assertion

```Text
class User {
    String _name;
    String _isFemale;
    
    User({String name = "Victor", bool isFemale = true, int age = 0})
        : assert(name.isNotEmpty), assert(age > 0), _name = name, _isFemale = isFemale;
```

- 생성할때 규칙을 정할 수 있다.
- `assert` 키워드를 통해서 필요한 조건을 넣는다. `true`가 되지 않으면 생성이 되지 않는다

## 64. Const constructor
- `const` 키워드는 컴파일을 하면서 값이 정해진다.
- 생성자에 `const` 키워드가 있을 때는 컴파일 할 때 검사하기 때문에 코드 작성시 막을 수 있다.
- 인스턴스를 고정해 버리는 역활을 한다.

## 65. Factory Constructor
- generative vs factory constructor
- Must use `return` keyword in factory constructor.
- More flexible compare to named constructor(named constructor can only use assert to check. factory constructor can do all the check and also manipulate the value)
- generative constructor only can create new instance of the class itself. However, factory constructors can return existing instances of the class, or even subclasses of it.
- why do we need factory constructor? defensive coding. not a must but useful to maintain. because factory constructor can not be forwarded.

```Text
void main() {
  Car.display = Car();
}

class Car {

  String color;

  static Car? display;

  Car({this.color = 'white'});

  Car.named(String? clr):assert(clr != null), color = clr!;

  factory Car.factory(String? clr) {
    if(clr == 'black' || clr == 'white') {
      return Car();
    }
    return Car();
  }

  factory Car.truck() {
    return Truck();
  }

  factory Car.displayIfAvailable() {
    return display??Car();
  }
}

class Truck extends Car {
  Truck();
}

```

## 66. Object
- object는 instace가 저장되어있는 저장 공간의 주소를 가진 레퍼런스이다.

## 67. Getter setter

```Text
class Car {
    int _wheels = 4;
    
    int get wheels {
        return _wheels;
    }
    
    set wheels(int wheels) {
        _wheels = wheels;
    }
}
```

## 68. Static members
- static 키워드 사용시 해당 멤버는 instance의 멤버라기 보단 class의 멤버이다.

```Text
class Car {
    static String weather = 'hot';
    static void todayWeather() {
        print(weather);
    }

    int runDistance = 1300;
}
```

- 자동차 공장이 class 자동차가 instance. 요즘 자동차들은 계기판에 날씨도 나온다. 계기판에 나오는 값중에 날씨와 해당 차량 운행거리가 나온다.
- 날씨는 static으로 저장. 운행거리는 instace멤버로 저장.

## 69. Variable types
- 네가지 상태의 variable이 있다.
    - global variable

        ```Text
        class 바깥에 위치한 어디서나 접근 가능한 variable, static 사용할 필요 없음. 접근성은 class variable과 같음
        ```

    - class variable

        ```Text
        class Car {
            static String weather = 'hot'; // <- class
        }
        ```

    - instance variable

        ```Text
        class Car {
            int runDistance = 1300; // <- instance
        }
        ```

    - local variable

        ```Text
        class Car {
            int runDistance = 1300;
            
            int totalDistance() {
                int thisTrip = 45; // <- local
                return runDistance + thisTrip;
            }
        }
        ```

## 70. Static const

```Text
class Car {
    static const numberOfWheels = 4;
}
```

## 71. Singleton
- class의 instace가 오직 하나만 생성된다.

```Text
class MySingleton {
  MySingleton._internal();
  static final MySingleton instance = MySingleton._internal();
}

final mySingleton = MySingleton.instance;
```

```Text
class MySingleton {
  MySingleton._internal();
  static final MySingleton _instance = MySingleton._internal();
  factory MySingleton() => _instance;
}

var mySingleton = MySingleton();
```

위 두가지중에 어떤게 더 낫다보다는 차이점을 알고 사용하자. 첫번째는 singleton패턴이라는것을 안다. 두번째는 singleton패턴이라는것을 모른다.

## 72. Static methods
- 많이 사용되는 용도는 utility. instance와는 교류가 전혀 없는 메소드.

```Text
class Car {
    static int distance = 1300;
    static int totalDistance(int thisTripDistance) {
        return distance + thisTripDistance;
    }
}
```

## 73. Static method vs Factory constructor
- Factory constructor는 static method와 비슷한 점이 많지만 차이점을 알면 유용하다.
- factory constructor는 class type이나 subclass만 리턴이 가능하고, static method는 아무거나 가능.
- factory constructor는 이름이 필요없다. 반면에 static method는 반드시 이름이 필요하다.

```Text
class MySingleton {
  MySingleton._internal();
  static final MySingleton _instance = MySingleton._internal();
  factory MySingleton() => _instance;
}

var mySingleton = MySingleton();
```

## 74. Challenge class
- `Student` class를 만들고 `name`, `grade`변수를 constructor를 통해 설정해주자.
- `Student` instance를 로그창에 예쁘게 print해주는 method도 만들어 보자.

```Text
class Student {
    final String _name;
    int _grade;
    
    Student({String name, int grade}) : _name = name, _grade = grade;
    
    set newGrade(int grade) => _grade = grade;
    
    void printStudent() {
        print('name : $_name, grade : $_grade');
    }
}
```