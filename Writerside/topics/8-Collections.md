# 8. Collections

## 82. Collection intro
- **Lists**
    - 데이터를 한줄로 쫙 나열해 놓으셨다고 보시면 됩니다.
- **Sets**
    - Lists와 동일하게 데이터를 한줄로 쫙 나열하되 동일한 데이터가 여러개 존재할 수 없습니다.
- **Maps**
    - key-value 짝을 이루면서 데이터를 모아놓은 것.

## 83. Lists
- 동일한 구조의 데이터들을 모아 한줄로 쫙 나열한 것.
- 다른 언어에서는 `array`라고도 한다.
- 각 데이터에 순서데로 0부터 번호를 부여한다.
- 부여된 번호는 `index`라고 부른다.`index`를 통해 각 데이터를 가져올 수 있다.

```Text
var alphabets = [
'A',  // index 0 
'B',  // index 1 
'C',  // index 2 
'D',  // index 3 
'E',  // index 4 
'F',  // index 5 
'G',  // index 6 
'H',  // index 7 
'I',  // index 8 
'J',  // index 9 
'K',  // index 10
'L',  // index 11
'M',  // index 12
'N',  // index 13
'O',  // index 14
'P',  // index 15
'Q',  // index 16
'R',  // index 17
'S',  // index 18
'T',  // index 19
'U',  // index 20
'V',  // index 21
'W',  // index 22
'X',  // index 23
'Y',  // index 24
'Z'   // index 25
];
```

Dart는 자동으로 리스트 안에 데이터가 String이라는 것을 알고 alphabets리스트를 아래 데이터 키워드처럼 변수를 고정시킨다. 한번 고정된 변수는 변경할 수 없다.

```Text
List<String> alphabets = ['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z'];
```

```Text
var alphabets = [];
```

- 텅 빈 리스트, null 아님.
- Dart는 List안에 데이터가 어떤것인지 모름.
- dynamic으로 고정.
- **empty List를 생성시 아래처럼 생성하자.**

```Text
List<String> alphabets = [];
var alphabets = <String>[];
```

- **get the value in the index**

```Text
final third = alphabets[2];
print(third);
```

- **get an index of the value. it can be `null`**

```Text
final index = alphabets.indexOf('D');
final value = alphabets[index];
```

- **assign new value into an index**

```Text
alphabets[1] = 'ABC';
print(alphabets);
```

- **add an element to a list**

```Text
alphabets.add('this is all!!');
print(alphabets);
```

- **remove an element from the list**

```Text
alphabets.remove('A');
print(alphabets);
```

## 84. Unmodifiable List
- **새로운 `List`를 생성 후 변수에 assign할 수 있다.**

```Text
var alphabet = ['A', 'B', 'C', 'D'];
alphabet = [];
alphabet = ['A', 'B', 'C', 'D'];
```

- **`final Lists` 성격을 파헤쳐보자.**
    - 만약에 `var` 대신 `final`을 사용한다면, 에러가 발생한다.

        ```Text
        final alphabet = ['A', 'B', 'C', 'D'];
        alphabet = [];
        alphabet = ['A', 'B'];
        ```

    - 이는 alphabet이라는 `List`변수에 새로운 `List`를 생성해서 assign할 수 없다는 뜻이다. 다음 코드를 보자.

        ```Text
        final alphabet = ['A', 'B', 'C', 'D'];
        desserts.remove('A');// OK
        desserts.remove('B');// OK
        desserts.add('A');// OK
        
        ```

    - `final` 우리가 죽기전까지 살 마지막 집. 집은 변함이 없지만 집 안에 있는 가구나 살림은 언제든 변경이 가능하다.
- **모든 elements도 변경이 불가능하게 하고 싶다면??**

    ```Text
    const alphabet = ['A', 'B', 'C', 'D'];
    alphabet = [];// Error
    alphabet = ['A', 'B'];// Error
    desserts.remove('A');// Error
    desserts.add('A');// Error
    
    ```

- **`const`를 사용할 수 없는 상황에서는?**

    ```Text
    final alphabet = const ['A', 'B', 'C', 'D'];
    alphabet = [];// Error
    alphabet = ['A', 'B'];// Error
    desserts.remove('A');// Error
    desserts.add('A');// Error
    
    ```

- **immutable list를 원하지만 사용될때까지 값이 뭔지 모른다면?? `List.unmodifiable`를 사용하자.**

    ```Text
    final modifiableList = ['A'.toLowerCase(), 'B'.toLowerCase(), 'C'.toLowerCase()];
    final unmodifiableList = List.unmodifiable(modifiableList);
    ```

## 85. List Properties

```Text
const alphabets = ['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z'];
```

- **Access first and last elements**

    ```Text
    print(alphabets.first);
    print(alphabets.last);
    ```

- **the List contains any elements**

    ```Text
    print(alphabets.isEmpty);
    print(alphabets.isNotEmpty);
    ```

- **the List contains any elements**

    ```Text
    print(alphabets.contains('a'));
    ```

- **the List length**

    ```Text
    print(alphabets.length);
    print(alphabets.length == 0);
    print(alphabets.length > 0);
    ```

## 86. Loop list

```Text
for (var alphabet in alphabets) {
    print(alphabet);
}

alphabets.forEach((alphabet) => print(alphabet));
```

- **output of `forEach` is same as input of `print`**

    ```Text
    alphabets.forEach(print);
    ```

## 87. Useful operators for lists
- **Spread operator**

    ```Text
    const kia = ['k3', 'k5', 'sorento'];
    const hyundai = ['sonata', 'avante', 'palisade'];
    
    const koreanCars = ['rexton', ...kia, ...hyundai];
    print(koreanCars);
    ```

- **`null` spread operator**

    ```Text
    const kia = ['k3', 'k5', 'sorento'];
    const hyundai = ['sonata', 'avante', 'palisade'];
    List<String>? deawoo;
    
    List<String> koreanCars = ['rexton', ...?deawoo, ...kia, ...hyundai];
    print(koreanCars);
    ```

- **collection if**

    ```Text
    const kids = true;
    
    const sandwich = [
      'lettuce',
      'pickles',
      if (!kids)'jalapeno',
      'ham',
      'chicken',
      'cheese',
    ];
    print(sandwich);
    ```

- **collection for**

    ```Text
    const spices = ['jalapeno', 'wasabi'];
    
    List<String> sandwich = [
      'LETTUCE',
      'PICKLES',
      'HAM',
      for (var spice in spices) spice.toUpperCase(),
      'CHICKEN',
      'CHEESE',
    ];
    print(sandwich);
    ```

## 88. Challenge lists
- **Quiz 1. 1월부터 12월까지 영어로 된 리스트를 생성해보자.**

    ```Text
    List<String> months = ['JAN', 'FEB', 'MAR', 'APR', 'MAY', 'JUN', 'JUL', 'AUG', 'SEP', 'OCT', 'NOV', 'DEC'];
    ```

- **Quiz 2. 생성된 리스트를 싹 비우자.**

    ```Text
    months.clear();
    ```

- **Quiz 3. 리스트를 다시 1월부터 6월까지 영어로 `add`메소드를 사용해 채워보자.**

    ```Text
    months.add('JAN');
    months.add('FEB');
    // ... 
    months.add('JUN');
    ```

- **Quiz 4. 7월부터 12월까지는 `for loop`을 사용해 채워보자.**

    ```Text
    List<String> temp = ['JUL', 'AUG', 'SEP', 'OCT', 'NOV', 'DEC'];
    for(var month in temp) {
        months.add(month);
    }
    ```

- **Quiz 5. 전부 소문자/대문자로 변경해보자.**

    ```Text
    for(int i=0; i<months.length; i++) {
        months[i] = months[i].toLowerCase();
                            = months[i].toUpperCase();
    }
    ```

## 89. Sets
- `Lists`와 많은 부분이 동일, 다른 부분만 말하는게 쉽겠다.
- `index`가 없다.동일한 element를 반복할 수 없다.
- **Creating a set**

    ```Text
    final Set<int> someSet = {};
    final someSet = <int>{};
    ```

- **prove no duplicates**

    ```Text
    final anotherSet = {1, 2, 3, 1};
    print(anotherSet);
    ```

## 90. Operations on a set
- **Contains**

    ```Text
    Set<String> alphabets = {'A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z'};
    print(alphabets.contains('A'));// true
    print(alphabets.contains('AB'));// false
    ```

- **Adding single elements**

    ```Text
    final alphabets = <String>{};
    alphabets.add('A');
    alphabets.add('B');
    alphabets.add('C');
    print(alphabets);
    ```

- **Removing elements**

    ```Text
    final alphabets = <String>{};
    print(alphabets.remove('A'));
    print(alphabets);
    ```

- **Adding multiple elements**

    ```Text
    final alphabets = <String>{};
    alphabets.addAll(['D', 'E', 'F']);
    print(alphabets);
    ```

- **Intersections**

    ```Text
    Set<String> aSet = {'A','B','C','D','E','F'};
    Set<String> bSet = {'A','B','W','X','Y','Z'};
    final intersection = aSet.intersection(bSet);
    print(intersection);
    ```

- **Unions**

    ```Text
    Set<String> aSet = {'A','B','C','D','E','F'};
    Set<String> bSet = {'A','B','W','X','Y','Z'};
    final union = aSet.union(bSet);
    print(union);
    ```

- **other operation**
    - collection `if`
    - collection `for`
    - `for-in` loops
    - `forEach` loops
    - spread operators

## 91. Maps 1
- **key-value pairs**
- key를 통해 value를 찾을 수 있는 구조이다.순서가 없다.key는 유니크해야 한다.
- **create a Map**

    ```Text
    final Map<String, int> emptyMap = {};
    final emptyMap = <String, int>{};
    ```

  Maps and Sets 다 `{}`를 사용한다. 아래는 Map일까? Set일까?

    ```Text
    final mapOrSet = {};
    ```

  mapOrSet은 `Map<dynamic, dynamic>'이다. 왜냐하면, Maps가 Sets보다 Dart언어에서 먼저 생성이 되어서라고 한다.

- **Initialize a Map with values**

    ```Text
    final foods = {
      'cakes': 2,
      'eggs': 6,
      'drinks': 7,
      'cookies': 12,
    };
    final digitToWord = {
      1: 'one',
      2: 'two',
      3: 'three',
      4: 'four',
      5: 'five',
    };
    print(foods);
    print(digitToWord);
    ```

- **Key는 반드시 Unique해야한다.**

    ```Text
    //not works
    final foods = {
      'eggs': 2,
      'eggs': 6,
      'drinks': 7,
      'cookies': 12,
    };
    //works
    final foods = {
      'cakes': 2,
      'eggs': 2,
      'drinks': 2,
      'cookies': 2,
    };
    ```

## 92. Operations on a map_1
- **Access a element**

    ```Text
    final foods = {
      'cakes': 2,
      'eggs': 6,
      'drinks': 7,
      'cookies': 12,
    };
    print(foods['cakes']);
    print(foods['butter']);
    ```

- **?.**

    ```Text
    final numOfButter = foods['butter'];
    print(numOfButter?.isEven);
    ```

- **add new element**

    ```Text
    foods['butter'] = 3;
    print(foods);
    ```

- **update a value**

    ```Text
    print(foods['eggs']);
    foods['eggs'] = 3;
    print(foods['eggs']);
    ```

- **remove an element**

    ```Text
    foods.remove['eggs'];
    print(foods);
    ```

- **Map properties**

    ```Text
    foods.isEmpty// false
    foods.isNotEmpty// true
    foods.length
    print(foods.keys);
    print(foods.values);
    print(foods.containsKey('eggs'));
    print(foods.containsValue(12));
    ```

## 92. Loop through map_2
- **looping through a map**

    ```Text
    for (var item in foods.keys) {
      print(foods[item]);
    }
    
    foods.forEach((key, value) => print('$key -> $value'));
    
    for (final entry in inventory.entries) {
      print('${entry.key} -> ${entry.value}');
    }
    ```

## 93. Challenge map
- **개인 신상정보 Map으로 생성하기.**
    - name, profession, country, city등등.

        ```Text
        final profile = {
            'name': 'victor',
            'profession': 'programmer',
            'country': 'Korea',
            'city': 'seoul'
          };
        ```

- **갑자기 한국에서 미국 new york으로 이사를 갔다.**
    - country와 city를 변경해보자.

        ```Text
        profile['country'] = 'united state';
        profile['city'] = 'new york';
        ```

- **loop을 사용해 map을 log에 나타내자.**

    ```Text
    profile.forEach((key, value) => print('$key : $value\n'));
    ```

## 94. Higher order methods_1
- **List.map()**
    - collection을 map메소드를 이용해서 새로운 Iterable<>을 생성할 수 있다.
    - `forEach`와 비슷하지만 다르다.

        ```Text
        final alphabets = ['a', 'b', 'c', 'd', 'e'];
        final upAlphabets = alphabets.map((alphabet)=>alphabet.toUpperCase());
        
        print(upAlphabets.runtimeType);
        ```

    - 결과는 `MappedListIterable<String, String>` 이름이 길지만, `Iterable`이라는 것은 확실하다. `Iterable`은 Lists와 비슷한 것이라고 보면 된다. Lists가 기능은 더 많다.

        ```Text
        print(upAlphabets);
        ```

    - 이 결과물을 보면 `(A, B, C, D, E)` 이렇게 표시된다. 이를 Lists로 변경해서 사용할 수 있다. `toList()`를 사용하면 된다.

        ```Text
        final list = upAlphabets.toList();
        print(list);
        ```

    - 이 결과물을 보면 `[A, B, C, D, E]` 이렇게 표시된다. Sets로도 변경이 가능하다.

        ```Text
        final sets = upAlphabets.toSet();
        print(sets);
        ```

    - `{A, B, C, D, E}` 이렇게 표시된다.
- **`forEach()` VS `map()`**
    - 다른 점만 분명히 알면 된다.
    - `map()`은 각각의 값을 변경후 `Iterable`안에 하나씩 넣어주고 `Iterable`을 return한다. 반면에 `forEach()`는 각각의 값을 가져와서 action을 취하고 끝!

    ```Text
    final alphabets = ['a', 'b', 'c', 'd', 'e'];
    final upAlphabets = alphabets.map((alphabet)=>alphabet.toUpperCase());
    alphabets.forEach((alphabet)=>print(alphabet.toUpperCase()));
    
    //map
    Iterable<T> map<T>(T toElement(E e)) => MappedIterable<E, T>(this, toElement);
    
    //forEach
    void forEach(void action(E element)) {
        for (E element in this) action(element);
    }
    ```

## 94. Higher order methods_2
- **Filter by `where()`**

    ```Text
    final numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];
    final evens = numbers.where((number) => number.isEven);
    print(evens);
    ```

- **Consolidating a collection by `reduce()`**

    ```Text
    final numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];
    final total = numbers.reduce((sum, number) => sum + number);
    print(total);
    
    final alphabets = ['a', 'b', 'c', 'd', 'e'];
    final allAlphabets = alphabets.reduce((all, alphabet) => all+alphabet);
    print(allAlphabets);
    ```

- **`fold()` instead of `reduce()`**
    - `reduce()`를 사용할때, lists가 empty이면 에러를 발생한다. 이를 방지하기 위해 `fold()`를 사용할 수 있다.

    ```Text
    final numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];
    final total = numbers.fold(0,(int sum, number) => sum + number);
    print(total);
    
    final alphabets = ['a', 'b', 'c', 'd', 'e'];
    final allAlphabets = alphabets.fold('', (String all, alphabet) => all+alphabet);
    print(allAlphabets);
    ```

## 95. Higher order methods
- **`sort()`**

```Text
final alphabets = ['p','a','q','e','w','r','o','t','y','u','i','s','l','d','f','g','h','k','z','x','j','c','v','b','n','m'];
alphabets.sort();
```

- **`reversed`**

```Text
var alphabets = ['p','a','q','e','w','r','o','t','y','u','i','s','l','d','f','g','h','k','z','x','j','c','v','b','n','m'];
alphabets.sort();
print(alphabets);
final reversedAlphabets = alphabets.reversed;
print(reversedAlphabets);
```

- **custom sorting**

```Text
final numbers = [6,3,5,4,7,2,9,1,8,10];
numbers.sort((int d1, int d2) => d1.compareTo(d2));
print(numbers);
```

- **Using multiple methods**

```Text
final numbers = [6, 3, 5, 4, 7, 2, 9, 1, 8, 10];
var newSets = numbers
    .where((number) => number.isEven)
    .map((number) => number * number)
    .toList()
  ..sort((int d1, int d2) => d1.compareTo(d2));
print(newSets);
```

## 96. When to use them
- List
    - 순서가 중요할때
    - 되도록 끝에 새로운 아이템을 추가할 것
    - 리스트가 크면 검색이 어려움
- Set
    - 아이템의 그룹에 포함 여부만 확인할 때
- Map
    - 자주 아이템을 key를 통해 검색하고 사용할 때

## 97. Chanllenges collections

```Text
String paragragh = '컴퓨터와 인터넷 코딩 스킬만 가지고 여러분들이 상상하는 크레이지 한 것들을 만들 수 있습니다. 그런데 코딩 스킬을 배우는 방법이 여러 가지가 있어요. 이 중에서 정답은 없습니다.';
var list = paragragh.split(' ');
```