# 9. Advanced Classes

## 98. Extend class

```Text
class Car{
    Car(int doors, int wheels) : _doors = doors, _wheels = wheels;
    int _doors;
    int _wheels;
    
    @override
    String toString() {
        return 'doors: $_doors, wheels: $_wheels';
    }
}
```

- 기본 class를 이용해서 파생해서 여러 class를 만들 수 있다

```Text
class HyundaiCars extends Car {
  HyundaiCars(super.doors, super.wheels, this._hyundaiBadgeColor);
  int _hyundaiBadgeColor;
}
```

## 99. Override

`override` 다시 작성한다. 부모 클래스의 있는 메서드를 다시 정의한다

모든 class는 Object class를 extends한다

## 100. Super

부모 클래스를 지칭하는 키워드이다

## 101. Multilevel hierarchy

상속 레벨이 같은것을 형제 관계로 하고 위아래 관계로는 부모 자식이라고 한다.

현제끼리는 서로 모르지만, 부모 자식은 서로 알고 있다.

## 102. Using hierarchy

상속관계에서 많은것들이 다 영향을 끼치기 때문에 너무 많은 값을 하지 않도록 조심해야한다.

## 103. Extends class challenge
1. class 이름을 Food이라고 만들자. int 타입의 calorie가 안에 있고, printCalorie메소드를 통해 calorie값을 print해보자

    ```Text
    class Food {
      int _calorie;
    
      Food(int calorie) : _calorie = calorie;
    
      void printCalorie() {
        print('$_calorie');
      }
    }
    
    ```

2. Food의 subClass를 만들어보자. 이름은 KoreanFood, 또 KoreanFood의 subClass로 Kimchi, Bulgogi, Galbitang을 만들자

    ```Text
    class KoreanFood extends Food {
      KoreanFood(super.calorie);
    }
    
    class Kimchi extends KoreanFood {
      Kimchi(super.calorie);
    }
    
    class Bulgogi extends KoreanFood {
      Bulgogi(super.calorie);
    }
    
    class Galbitang extends KoreanFood {
      Galbitang(super.calorie);
    }
    ```

3. Kimchi, Bulgogi, Galbitang에 printCalorie를 override해서 다른 결과를 보여주자.

## 104. Abstract class
- Car 처럼 너무 일반적인 속성을 가진 class를 abstract class로 선언한다
- ex) Food, Person…..
- body가 없는 함수를 선언해서 extends하는 곳에서 구현해야 한다.

## 105. Interface
- Interface는 사용하는 사람들 사이의 계약서이다. 예를 들어 두 사람 사이에 통화는 한 사람이 다른 사람의 전화번호를 전화연결 한다.

## 106. Extends vs Implement
- extends : 기존에 구현되어 있는 메서드/변수 사용 가능하다.
- implement : 기존에 구현되어 있는 메서드/변수 사용 불가능하다.

## 106-1. Instantiate abstract class

```Text
abstract class DataRepository {
    factory DataRepository.webSocket() => WebSocket();
    
    void printAnyThing() {
        print('abstact DataRepository');
    }
}

class WebSocket implements DataRepository {
    @override
    void printAnyThing() {
        print('WebSocket');
    }
}
```

## 107. Interface challenge
1. Camera 인터페이스 생성. shoot 메소드 포함

    ```Text
    abstract class Camera {
      void shoot();
    }
    ```

2. DigitalCamera 클래스를 Camera를 implement 해서 생성, “png image file”라는 문구를 shoot메서드를 통해 출력

    ```Text
    class DigitalCamera implements Camera {
        @override
      void shoot() {
        print('png image file');
      }
    }
    ```

3. Camera에 DigitalCamera를 return하는 factory constructor를 생성

    ```Text
    abstract class Camera {
      factory Camera() => DigitalCamera();
    
      void shoot();
    }
    ```

4. main 메소드 안에 DigitalCamera인스턴스를 Camera factory constructor를 사용해 생성 후. shoot 메소드를 실행

    ```Text
    void main(List<String> arguments) async {
      final camera = Camera();
      camera.shoot();
    }
    ```

## 108. Mixins
- extends와 implement의 문제점에서 나온 해결점이다.

```Text
abstract class Bird {
    void fly();
    void layEggs();
}

class Pigeon extends Bird {
    @override
    void fly() {
        print("푸드득~~~");
    }
    
    @override
    void layEggs() {
        print('비둘기알 탄생');
    }
}

class Ostrich extends Bird {
    @override
    void fly() {
        print("불가능");
    }
    
    @override
    void layEggs() {
        print('타조알 탄생');
    }
}
```

- 비둘기는 날 수 있다. 알을 낳을 수 있다. 타조는 날 수 없다. 알을 낳을 수 있다. 둘다 조류 이다.
- 파리는 날 수 있다. 알을 낳을 수 있다. 그러나 조류가 아니다.
- Flyer, EggLayer등 여러개 인터페이스로 나누면?? 이럴때 나온것이 Mixins이다.

## 109. Mixin in code

```Text
class Pigeon with EggLayer, Flyer { } // <- 재사용한다

class Oscritch implements EggLyaer {
    @overrid
    void layEggs() {
        // TO-DO
    }
}

mixin EggLayer { // class 키워드를 사용해도 된다
    void layEggs() {
        print('알을 낳는다');
    }
}

mixin Flyer {
    void fly() {
        print('날아올라 푸드드드득~!');
    }
}
```