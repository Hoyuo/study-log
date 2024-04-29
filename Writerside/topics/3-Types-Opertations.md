# 3. Types &amp; Operations

## 11. Data types in dart
- String(글자), boolean(true or false), list(여러 개의 데이터가 array로 있는것), int(숫자)
- 한개의 데이터 타입을 다른 데이터 타입으로 변경하는 것 = conversion
- even number - 짝수
- odd number - 홀수
- Ceil - 올림
- Floor - 내림
 
## 12. How string works
- Unicode - 세계 모든 텍스트를 통일된 방법으로 표현함으로써 각 언어와 문자 체계에 따른 충동 해결.

## 13. String quote concat interpolation
- `""`안에 `''` & `''`안에 `""` 사용 가능.
    - 단, `''` 안에 `'` & `""`안에 `"`사용불가.
    - `\` 사용 가능.
- stringBuffer
    - `$` - String안에 변숫값 사용 시.
    - `${}`-String안에 statement 사용 시.
    - `${}`이것만 사용하게 되면 resource를 더 잡아먹기 때문에 사용하지 않아야 할 때는 중괄호{}를 빼고 사용하는 것이 좋다.

## 14. Multiline and special characters in string
- `\n` - 띄어쓰기
- `\u` - 유니코드 /숫자 4자리까지만 인식을 하기 때문에 숫자 4자리 이상의 코드는 중괄호{}를 넣어준다.
- 각각의 띄어쓰기를 해주고 싶은데 `\n`을 쓰기 싫을땐, 띄어쓰기를 포함한 텍스트를 하면 된다.
    - `"""`
    - `'''`

## 15. Object vs Dynamic
- 타입이 정해져 있지 않고 변경 가능 (데이터 타입 정해져 있지 않음)
    - `object`/`dynamic`
- `object` - 데이터 타입이 정해져 있지 않은 코드를 사용해야 한다? 그럼 그냥 `object` 사용하는 것이 좋다.
- `dynamic` - 타입이 아예 없음. 데이터 사용이 맞는지 확인 안함. 매우 위험.
- 정확한 코드 타입을 명시해 주고 코드 작성해 주는 것이 매우 중요!!
- `dynamic` 매우 위험. 어디서 에러가 났는지 모를 수 있다.
