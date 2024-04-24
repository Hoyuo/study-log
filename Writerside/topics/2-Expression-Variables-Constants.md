# 2. Expression, Variables, Constants

## 02. Comment
- `Comment` Compiler는 이 부분을 무시하고 어플리케이션에 포함 시키지 않는다. 코드 작성 시 혼자 혹은 다른 사람이랑 같이 작업을 할 때 comment를 남겨줘야 할 때가있다.
- `//` VSCODE에서 초록색으로 나타나며 어플리케이션 작동 시, 문제없다.
- 박스가 쳐지듯, 여러 줄로 코멘트 가능. 어떤 코드인지 설명해 주는 텍스트.

    ```Dart
    /**
    
    */
    ```

- 내용 작성하고 마지막에 `*/` 입력. 박스 자체가 코멘트 이다.

    ```Dart
    /* */
    ```

## 03. Where dart start
- 다트 언어 시작되는 부분 `main`함수
- `main`이라는 함수가 꼭 있어야 Dart 언어 실행된다.
 
## 04. Print N read doc
- `print` 함수인데 함수를 실행하는 것.
- `print` 함수 : print() 안에 String이라는 Data Type을 전달해 String Type을 Console에 Printing해주는것.
- 함수가 어디에 어떻게 작동하는지 아는방법
    - MacOS->Command+클릭
    - Window->Control+클릭

## 05. Math operators
- `+`, `-`, `*`*, `/`, `%`,`~/`*
    - print(6+3); = 9
    - print(6-3); = 3
    - print(6*3); = 18
    - print(6/4); = 1.5
    - print(7/3);= 2.3333...
    - print(7%5);= 나머지2
    - print(7%3);= 나머지1
- 소수점빼고'2'만보여주고싶다면,~/사용
    - 7~/3=2(소수점없음)

## 06. Declare variable(number)
- 숫자 관련 변수 생성 키워드
    - int - 정수
    - double - 실수 소수점숫자
    - num - 모든수
    - `int someNumber = 10;`
- `num` 키워드는 number의 약자로 숫자 관련 데이터 타입을 모두 저장 가능한 데이터 타입. 즉, num은 int, double 데이터 모두 저장 할 수 있다.
- `var`를 사용한 변수에는 모든 데이터 타입을 저장할 수 있는 변수다.
- `num`은 키워드를 사용해서 생성한 변수, 저장 공간 안에 데이터, 종류들이 있다.
- Int = 3 / double = 3.0 (같은 수이지만 데이터 상으로 다르다고 본다.) 따라서 데이터상으로 다른 숫자로 보고 다르게 저장한다.
- `num`은 int와 double 다 가질 수 있는 데이터.
- `var`(variable) - 변수
    - `var`를 사용한 변수에는 String, 숫자, boolean, custom data type도 넣어 줄 수 있다.

## 07. Final const
- `const`/`final`비슷한점
    - 한번 고정된 변수는 고칠 수 없다.
- `const`/`final`차이점
    - `const`코드가 compiler될 때 이미 잠김.
    - `final`run time(앱이 돌아가고 있는 시점)에 잠김.
- 앱 실행전 변수의 값이 뭔지 알면 const 사용.
- 앱 실행 후 runtime에 값이 뭔지 알게 되면 final 사용.

## 08. Naming variable
- naming을 정할 때, 그냥 정하는 것이 아니라 나와 동료가 이해할 수 있게 끔 코드를 작성해 주는 것이 좋다.
- variable name을 정해 줄 때 lowerCamelCase로 작성해 준다.
- 단어가 하나일 경우, 소문자로 작성해 준다.
- variable을 생성하고 naming을 정할 때, 그냥 정하는 것이 아니라 나와 동료가 이해할 수 있게 끔 코드를 작성해주는 것이 좋다.
- 프로그래밍 언어에 프로그래머들이 사용하는 룰이 있다. variable의 이름을 정해줄때, lowerCamelCase를 사용.
- variable name이 어떻게 정해져야 하나면, 다른 코딩을 하고 나서 다시 돌아왔을 때, 어떤 variable인지 한번에 확인 가능 해야 한다.
- variable = lowerCamelCase

## 09. Math operators
- counter = couter + 1; 를 짧게 표현 방법
    - counter+=1;
    - counter++;
- counter = couter - 1; 를 짧게 표현 방법
    - counter-=1;
    - counter--;

## 10. Quiz variable

```Dart
void main() {
    counter = 10;
    print(counter++);
}

// 애러를 찾고, 실행 결과를 보여주세요
```