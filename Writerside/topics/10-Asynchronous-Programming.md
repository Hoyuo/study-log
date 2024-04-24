# 10. Asynchronous Programming

## 110. Async in dart
Dart → 단일 Thread

  - 60fps → 16ms
  - Main에서 오래 걸리는 작업을 처리하는 것이 아니라 보조 적인 곳에서 처리한 후 결과값만 받아와서 처리 한다

## 110-1. Introduction to future
- `Future` 받아올 것 → Data, Error
    - 데이터가 아직 해결이 안된 상태
    - Task가 끝났는데 Erro인 상태
    - Task가 끝나서 성공적인 상태 Data

## 111. Understand future in code

```Text
Future weatherFuture = getWeaterData();

weatherFuture
.then((weatherData) {
    // success
})
.catchError((error){
    // error
});
```

## 112. Using future 1

```Text
Future<int> myFuture = Future<int>.delayed)
    Duration(seconds: 1),
    () => 42,
);
```

## 113. Async await

```Text
void main() async {
    final myFuture = await getWeatherData();
    print(myFuture);
}

Future<int> getWeatherData() async {
    final futureValue = await Future<int>.delayed)
        Duration(seconds: 1),
        () => 42,
    );
    
    return futureValue;
}
```

## 114. Try catch

```Text
try {
    final myFuture = getWeatherData();
    
    myFuture
        .then((value) => print('$value')
        .catchError((onError) => print('$onError')); // <- Future에서 애러가 발생할 경우 
} catch(error) {
    // <- 시스템상 발생하는 애러가 발생할 때
} finally {

}
```

## 115. Use dart package

[DummyJSON - Fake REST API of JSON data for development](https://dummyjson.com/)

qutoe를 이용해서 진행해 봅시다

```bash
$dart pug get http
```

## 116. http request

quote_model을 만들어 봅시다

```Text
class Quote {
  int? id;
  String? quote;
  String? author;

  Quote({this.id, this.quote, this.author});

  Quote.fromJson(Map<String, dynamic> json) {
    id = json['id'];
    quote = json['quote'];
    author = json['author'];
  }

  Map<String, dynamic> toJson() {
    final Map<String, dynamic> data = <String, dynamic>{};
    data['id'] = id;
    data['quote'] = quote;
    data['author'] = author;
    return data;
  }
}
```

```Text
void main(List<String> arguments) {
  getQuote();
}

Future<void> getQuote() async {
  final url = Uri.parse('https://dummyjson.com/quotes/1');
  final response = await http.get(url);
  if (response.statusCode == 200) {
    final quote = Quote.fromJson(jsonDecode(response.body));
    print('Quote: ${quote.quote}');
    print('Author: ${quote.author}');
  } else {
    print('Failed to fetch a quote. Status code: ${response.statusCode}');
  }
}
```

## 117. Handling exceptions

```Text
Future<void> getQuote() async {
  try {
    final url = Uri.parse('https://dummyjson.com/quotes/1');
    final response = await http.get(url);
    if (response.statusCode == 200) {
      final quote = Quote.fromJson(jsonDecode(response.body));
      print('Quote: ${quote.quote}');
      print('Author: ${quote.author}');
    } else {
      print('Failed to fetch a quote. Status code: ${response.statusCode}');
    }
  } on SocketException catch (error) { // <- 필요한 애러 부분을 별도로 적어주는 것이 좋다
    print(error);
  } catch (error) {
    print(error);
  }
}
```

## 118. Stream

흐름이다 데이터가 한번 오는것이 아니라 계속 오는 흐름이다.

쉽게 생각하면 유투브 영상이라고 보면 된다. 한번에 다 받아오는것이 아니라 필요한 부분들을 받으면서 영상을 처리 하고 있다.

## 119. Stream in code

```Text
import 'dart:io';
import 'dart:convert';

void main(List<String> arguments) async {
  final file = File('assets/fairytale.txt');
  final stream = file.openRead();

  int i = 0;

  stream.listen((data) {  // <- stream은 listen을 이용해서 데이터를 처리한다.
    i++;
    final text = utf8.decode(data, allowMalformed: true);
    print("$i - ${text}");
  });
}
```

## 120. Chunk data in stream

```Text
출력된 곳에서 1 - , 2 - 를 찾아보면 진짜로 데이터가 읽은 단위별로 전송 되어서 보내진다
```

## 121. Stream transformer

```Text
stream.transform(utf8.decoder).listen((data) {
  print("${i++} - $data");
});

// 번역해서 데이터를 가져올수도 있고
// where 통해서 필요한 데이터간 filter도 가능하고
// 여러번 transform도 가능하다
```

## 122. Create stream
- 직접 만들어서 사용하는 경우는 거의 없지만 일단 배워둔다

    ```Text
    Stream<int> numbering() async* {
        for(int i=0; i<60; i++) {
            await Future.delayed(Duration(seconds: 1));
            yield i; // <- stream에서 return 방식이라고 생각하면 된다
        }
    }
    ```

## 123. Stream subscription

```Text
void main(List<String> arguments) async {
  late StreamSubscription<int> subscription;
  subscription = numbering().listen((event) {
    print('event: $event');
    if (event == 7) {
      subscription.cancel();  // <- 구독을 관리해서 취소를 시켜줄 수 있다.
    }
  });
}

subscription.pause(Future.delayed(Duration(seconds: 2)); // <- 기다리게도 할 수 있다
```