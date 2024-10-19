# java-calculator-precourse

## 기능 목록

1. 쉼표(,) 또는 콜론(:)을 구분자로 가지는 문자열을 전달하는 경우 구분자를 기준으로 분리한 각 숫자의 합을 반환한다.
    - 예: "" => 0, "1,2" => 3, "1,2,3" => 6, "1,2:3" => 6
2. 앞의 기본 구분자(쉼표, 콜론) 외에 커스텀 구분자를 지정할 수 있다. 커스텀 구분자는 문자열 앞부분의 "//"와 "\n" 사이에 위치하는 문자를 커스텀 구분자로 사용한다.
    - 예를 들어 "//;\n1;2;3"과 같이 값을 입력할 경우 커스텀 구분자는 세미콜론(;)이며, 결과 값은 6이 반환되어야 한다.
3. 사용자가 잘못된 값을 입력할 경우 `IllegalArgumentException`을 발생시킨 후 애플리케이션은 종료되어야 한다.

## 구현할 기능

- [ ]  쉼표와 콜론만을 구분자로 가지는 문자열의 합 계산
- [ ]  쉼표와 콜론만을 구분자로 가지는 문자열의 예외 처리
    - [ ]  잘못된 구분자가 들어온 경우
    - [ ]  구분자가 연속되게 나오는 경우
    - [ ]  문장 앞이나 뒤에 숫자가 존재하지 않는 경우
- [ ]  커스텀 구분자를 추가한 문자열이 들어오는 경우에 대한 합 계산
- [ ]  커스텀 구분자를 추가한 경우에 대한 예외 처리
    - [ ]  구분자 형식이 잘못된 경우
    - [ ]  이전 예외 처리와 동일한 예외 처리

## 구현할 Method

### 1. 구분자 확인 Method

**시그니처**

```java
char checkDelimiter(String input);
```

**입력**

- 구분자와 양수로 구성된 문자열

**출력**

- 구분자가 있는 경우: 구분자 반환
- 구분자가 없는 경우: `null` 반환

**로직**

1. 입력 string으로부터 구분자 탐색
2. 존재하면 반환
3. 없으면 `null` 반환

### 2. 숫자 분리 Method

**시그니처**

```java
List<String> splitByDelimiter(String input, List<Character> delimiter);
```

**입력**

- 양수로 구성된 문자열
- 기본 구분자와 커스텀 구분자

**출력**

- 구분자를 바탕으로 split된 수의 String List

**로직**

1. 문자열을 구분자를 바탕으로 split
2. 분리된 문자열 list 반환

### 3. 숫자 (String → Integer) 변환 Method

**시그니처**

```java
List<Integer> changeToInteger(List<String> numStrings);
```

**입력**

- 양수로 구성된 문자열 리스트

**출력**

- 리스트 각각의 문자를 Integer로 변환하여 반환

**로직**

1. 입력 문자들을 수로 변환 및 반환

### 4. 계산

**시그니처**

```java
Integer calculate(List<Integer> nums);
```

**입력**

- 양수 리스트

**출력**

- 리스트의 길이가 0이 아닌 경우: 숫자의 합 반환
- 리스트의 길이가 0인 경우: 0 반환

**로직**

1. 리스트의 숫자를 하나씩 방문하며 합 계산
2. 계산된 값 반환