# 5. Function

## 35. Why use function
- fuction, method, 함수 다 같은 뜻이다. 구분하지 말아라.
- function이 왜 필요하고, 프로그래밍에서 중요하게 여기는가?
- 서로 다른 3종류의 차 엔진이 모두 같은 엔진이 들어간다고 가정.
- 서로 똑같은 엔진인데 라인을 3개 만들어 줬음.
- 엔진 결함이 발생해서 업그레이드해서 고쳐줬음.
- 어떤 엔진을 바꿀 때마다, 라인마다 한번씩 총 3번을 바꿔줌.
- 한번 더 업그레이드해서 고쳐줬음.
- 근데 문제는, 바꿔지는 과정에서 동일하게 바뀌어질지 모름. 버그가 발생할 수도 있음.
- 엔진을 만드는 과정 자체를 따로 띄어온다. 한곳으로. 그래서 한 곳에서 필요한 곳에 지원. = 한번만 바꿔주면 됨.
- function으로 바꿔주면, 한번, 두번 또는 여러번 사용되는 곳들이 있음.
- function을 만들어야 하는 가장 중요한 이유 중 하나이다.
- 따라서 이것 때문에 프로그래밍에서 function을 사용하는 것이다.

## 35-1. What is function

  ```Dart
  void main(){
  
  }
  ```

- void main(){} --> 이것 자체가 function.
- 입구 --> ()
- 바디 --> {}
- 출구 --> void
- 출구 쪽으로 내보내는 방법 = return으로 값을 내보낸다.
- 출구 값에 어떤 값이 나오는지 명시해줄 수 있다. int, double, string.
- 어떤 데이터가 나올껀지 미리 결정 해 줄 수 있다.

  ```Dart
  String myNameInSentence(){
  }
  ```

- 또한 입구(변수)에 어떤 데이터 값을 넣어줄 것인지 명시해 줄 수 있다.

  ```Dart
  String myNameInSentence(String name){
  }
  ```

- 입력값 String name
- void main()은 function 중에 입력 값이 없는 것도 있고 void는 입력.출력 값이 없어서 body{} 안에만 실행 해 주고 땡! = 따라서 return 할 게 없으면, void 해주던가, 아예 무시해줘도 된다.

## 36. Optional parameters in function
- parameter = function에 입력해주는 입력 값을 말한다.
- optional 값을 어떻게 해 줄까? parameter를 optional 값으로 변경해주는 방법이 있다. 마지막에 두고, 대괄호[]로 감싸주면 된다.
- null - 데이터가 없는 것을 표시. 옵션값이기 때문에 아무것도 안넣어줄 수 있는 null이 가능한데, int, double, string등의 키워드 모든 것들에 명시해 주면 null이 불가능하다. Data를 반드시 넣어줘야 한다. 그래서 null이 가능한 변수를 만들려면, ?를 넣어준다. 물음표가 포함된 키워드를 통해 생성된 변수는 null이 가능하다. 안에 아무 데이터가 없어도 된다.
- 왜 중요하냐? 어플리케이션을 사용하다가 앱이 멈추고 고장나면, 99%가 null 때문이다. 그래서 ?가 안들어간 것은 무조건 null 불가능하게 만들어! 라고 해줌. ?가 들어가야 옵션값 때문에 null이 가능하기 때문에 넣어줘야 한다.
- 옵션 값은 한 개 이상, 두 개도 가능하다.
- 물음표 때문에 옵션 값이 가능하여

  ```Dart
  String myNameInSenetence(String lastName, String givenName, [String? middelName])
  // []로 묶은 곳은 ? 옵셔널로 선언해서 안 넣으면 자동으로 null이 들어간다. 그렇기 때문에 항상 맨 마지막에 넣어야 한다
  ```

## 37. Named parameters in function
- 많은 옵션 값이 있다고 가정했을 때, 어디에 관련된 값인지 하나씩 세어볼 순 있지만 힘듬.
- 따라서 각각의 value들을 옵션 값이기도 하지만 name을 주어서 key value식으로 전달 해 줄 수도 있음. `[] 지우고 {} 사용.`
- last name, given name은 반드시 줘야 함. 중괄호{} 안에는 다 옵션값으로, 끝에 적어줘야 한다.

## 38. Format code in vscode
- 길게 나열 된 변수 끝에 `,`를 찍어준다. `,`가 찍혀진 상태에서 mac에서는 shift + option + F 입력시, 코드가 쫙 정리 됨. window에서는 shift + alt + F 이다.
- 나중에 vsc가 아닌, flutter 하실 때 vsc 또는 AndroidStudio 사용해도 되는데, vsc, android 각각 다른 format과 저장 코드가 따로 있다.

## 39. Default value for parameter
- 옵션 값 전달 시 null이 될 수 있는 변수를 생성하는 키워드를 ?와 함께 사용함.
- 기본 값(default)를 줄 수 있다. function을 사용 할 때, 값을 안주어줘도 기본으로 들어가는 값을 줄 수 있다.
- 기본값이 주어지기 때문에 null을 제거 할 수 있다. (제거 하지 않아도 된다)

## 40. Write a good function 1
- 원하지 않는 상황을 발생 시켰을 때, 부작용이 있는데 어떻게 하면 잘 피할 수 있을까?
- 받아온 return 값을 가지고 print해 주던, 무엇을 해 주든 할 수 있다.
- 기존에 만들어준 return 값을 준 후에, 값을 return 해줌.

## 41. Write a good function 2
- readability를 볼 때는 function 안에는 한 가지 작업만 하고, function의 이름을 이해하기 쉽게 작성해준다.

## 42. Anonymous function
- 변수를 생성할 때, 생성되는 변수의 Data Type 키워드를 사용하고, 변수의 명을 지정한 후 데이터를 저장해 준다. 저장된 데이터를 가지고 오기 위해 변수 명을 사용한다.

  ```Dart
  int someNumber = 10;
  ```

- someNumber를 통해 저장된 데이터를 가지고 올 수 있다. Function도 위와 같이 만들어줄 수 있다.
- anonymous = 이름이 없다.
- function의 이름을 없애고 addUp으로 function을 지정해 줄 수 있다.

  ```Dart
  Function(int, int) addUp = (int a, int b) {
      return a + b;
  };
  ```

## 43. Delcare anonymous function
- function 사용.
- ForEachCopy를 명시하고 사용한 부분. fnct를 declare한 부분(body가 있는 부분)을 어떻게 기능을 하는지?

  ```Dart
  void main(){
      forEachCopy((int number){
          print(number);
      });
  
  }
  
  void forEachCopy(Function(int) fnct){
      fnct(5);
  }
  ```

- forEachCopy(call_back)

## 44. Function in one line
- 바디{ }안에 있는 코드가 딱 한 줄만 있을 때 가능하다 `=>` (중괄호{} 지워주기!)