# 4. Control Flow

## 16. boolean
- boolean - 맞는지 안맞는지에 대한 데이터 저장.
    - Keyword = bool(yesOrNo)
- 왜존재하냐?
    - 다른 데이터 타입 사용시 전세계 프로그래머의 코드가 통일되기 힘들다.
    - 예) 0 과 1사용 시, 0이 맞는가 틀린가? yes 인지 no 인지? 확실히 대답 불가능.

## 17. operator related to boolean
- ==, !=, <=, >=, <, >, &&, ||
- (or) ||은 둘 중에 하나만 true 가 나와도 true
- (and)&&은 둘 다 ture 일 때만 true

## 18. Use boolean operator with other data types
- String 에서는 크기 비교를 할 수 없다.
    - 따라서, >, <은 무조건 숫자(int,double,num)에 관련된 operator 이다.

## 19. if Statement
- if 괄호 () 안에 조건문 넣어주고 Body->{} 안에 if문()이 true 일 때 실행되는 코드를 넣어주면 되고 여러 줄을 넣어 줄 수 있다
- 반대로 false 일 때, 코드값 실행이 안 된다

## 20. If else
```Dart
if() {
} else {
}

if() {
} else if() {
}
```

- else if 문은 ()에 condition 을 넣어줄 수 있다.

## 21. Variable scope
- Variable 변수를 생성해 주는데, 중괄호{} 하니씩 사용할 때마다 박스가 하나씩 생성된다. 박스 안(main)에서 밖(global)으로 접근이 가능하지만, 밖 에서 안으로는 접근이 불가능하다.
- 중괄호{}를 기준점으로 그 안에서 생성된 Variable 은 그 안에서만 사용 가능하다. 예) void main 안에 if 문이 있는데 main 밖에서 if문을 사용하면 안된다.

```Dart
void main() {

}
if(true{

}

```

## 22. One line if else

If else 연장선을 줄여줄 것임. = (If else문을 한 줄로 만들어줄 수 있다.)

한 줄에 나타내 줄 수 있음.

```Dart
String message = (myHeight > 180)? 'I am tall': 'I am still tall';
```

단 `if-else` 문 만 가능. `if-else-if` 문 은 안된다!!

## 23. Switch

is else문을 switch문으로 생성해주기.

차이점 =

```Dart
switch() {
   case :
    print();
    break;

    default : 
      (만족하는 case가 없으면 default 부분 실행. (단 마지막에 넣어주기 때문에 break 생략 가능.)
}

```

```Dart
switch() {
  case :
    print();
    break;

  default:
    print('.....');
    break;
}

```

switch 키워드 -> 괄호() 안에 변수를 넣어주고 중괄호{} 사용해서 case 묶어줌. 각 케이스마다 : 사용. 콜롬이 만족할 때, 어떤 구문을 실행 해 줄지 실행구문 코딩 해 주면 된다. 마지막에 break 잊지 말기!

만약에 각 다른 case를 같은 결과 값으로 한 곳에 나타내고 싶을 때, 다음과 같이 나타낼 수 있다. 예)

```Dart
case 1:
  print('one');
  break;
case 2:
  print('two'):
  break;

.
.
.

case 1:
case 2:
  print('one or two');
  break;

```

## 24. Enumerate
- int, double, bool, String과 같은 데이터들은 우리가 따로 Declare 해줄 필요가 없다. 반면에 enum은 안에 들어가는 데이터가 무엇인지 개념 정리를 먼저 해 주어야 한다.
- enum 데이터 생성 - string, int, double, var과 같은 데이터
- EatChicken은 enum 타입의 생성자명. 중괄호{}를 통해 상태들을 나열해준다.

```Dart
enum EatChicken {
    findPhoneNumber,
}

```

```Dart
enum EatChicken {
    findPhoneNumber,
       .......,
      .........,
}

```

## 25. Enum n switch
- quick fix = command + .(Mac), Ctrl + . --> Add missing case clauses 클릭하면, 자동으로 모든 상태의 case들을 포함시킨다.
- EatChicken.none 상태에서 switch문 사용.
- 변수의 이름을 임의로 바꿔줄 때: VSCode에서 F2 누르면 관련된 모든 변수 이름을 자동으로 바꿔준다. (중요!)

```Dart
switch() {
  case:
    print();
    break;
  case;
    print();
    break;
}

```

if else / switch / if else if 문도 사용 가능.

## 26. While loop
- 반복문 베우기 -> while
- syntax 구조는 if문과 같다. (if else 말고)
- 변수 안에 true false 조건물을 넣어 준 다음에 그 조건문이 만족을 하냐, 안하냐에 따라서 ture면 body를 실행하고 false면 빠져나온다.

## 27. Do while
- while = while 문에서 비교한 후에 만족 하냐, 안하냐 따지고 중괄호{}안에 실행을 해주는지 안해주는 지 판단해줬다. do while = 일단 실행 후 while(조건문)를 통해서 비교 후에 만족을 하면 다시 실행.

```Dart
do {

} while();
```

## 28. Break in loop
- while 문을 사용해서 loop 사용 가능.
- loop이 평생 돌아가게 실수를 할 수도 있음.
- (조심)loop을 빠져나오게 하고 싶을 떄, if문 사용 가능.

```Dart
do {
  number++;
  if(number > 7) {
    break;
   }
} while(true);

```

## 29. Rock Scissors Paper

코드 넣어주기!!!!!!!!!!!!!!!! 꼭!!!!!!!

- `import ‘dart:math’;`
- switch와 enum 문을 이용하여 가위, 바위, 보 게임 하기
- import 'dart:math'; - 수학 관련 수식을 가지고 온다
- Random().nextInt(3); // 0~2 사이의 숫자 중 하나의 정수를 int로 가져온다.

```Dart
while(number != 2) {
    number = Random().nextInt(3);
    print(number);
}

print('The End - $number');

```

## 30. For loop
- while이랑 비슷하지만 loop할 때 가장 많이 쓰는 부분(반드시 이해)
- 천천히 자세하게 볼 수 있는 방법 = Debugging (Break point) 왼쪽 끝에 빨간색 표시가 되는데 VSC 뿐만 아니라 대부분의 아이디가 실행 가능하다.
- Breakpoint = 코드가 실행되다가 빨간 불 있는 곳에서 코드 멈춤.
- Continue F5를 누르면 Break point를 벗어나서 계속 코드 진행 한다.

```Dart
for(int i=0; i<10; i++) {
}
```

- 문제: for 문을 while loop으로 만들어주기. (1부터 10까지 더해서 55가 나오도록!)

## 31. Interupt for loop
- 빼고자 하는 수를 제외한 나머지 정수를 나타내고자 할 때, continue를 사용해 주면 된다.
- while문에서 사용한 break를 사용하면, 지정한 정수 이후의 수를 나타나지 않게 할 수 있다.

## 32. For in loop
- for(var char) 코드는 각각의 캐릭터를 말해준다. 예) Rainbow - R, a, i, n ... 각각이 모여 한개의 String을 이루고 있다. 유니코드를 통해 코드를 전달해 준다.

```Dart
String str = 'abcdef';
for(var ch in str) {
}
```

- list data를 생성할 때, 대괄호[]를 사용한다.

## 33. For each

```Dart
for(var number in list) {
    print(number);
}
```

- for in loop을 간단하게 만들어 준다.
- 1~10까지의 수를 55로 프린트할 수 있게끔 만들어주기.

```Dart
void main() {
    var list = [1,2,3,4,5,6,7,8,9,10];
    int result = 0;
    list.forEach((number) {
        result += number;
        print(number);
    });

    print(result);
}

```

## 34. For loop in single line
- 만약 for loop을 한 줄로 만들어주고 싶다면, statement 실행해주는 액션 부분이 딱 한줄만 있어야 하고 `;, {}` 없애주고 `=>` 무조건 있어야 한다.
- for loop을 한 줄로 만들어주고 싶을 때, statement(실행해 주는 action 부분)가 딱 한 줄만 있어야 한다. 만약 loop을 실행하는데 한 줄 이상이라면, 한 줄로 해결 가능한 방법이 현재로선 없다

```Dart
list.forEach((number) => result += number);
```