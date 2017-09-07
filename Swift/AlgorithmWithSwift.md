## Problem Solving Algorithm with Swift
- - -

Algorithm practicing for coding test

#### User Inputs

온라인 코딩 테스트를 위해서는 사용자로부터 input을 받아 알고리듬이 정상적으로 작동하는지 테스트한다.
Swift를 처음 알고리듬에 사용 했을 때, 기존 C나 Java 처럼 사용자로부터 Input을 받는 것이 생소했다.

다음 코드를 사용하면 사용자의 Input을 Line 단위로 받아올 수 있다.

```let input: String = readLine()!```

받아온 input의 타입은 String 이므로 Int로 사용할 때에는 Int() 로 형변환을 해줘야 한다.

주로 Int의 배열을 받아와야 하는데 다음 코드를 이용하면 Line 단위로 Int 배열을 만들 수 있다.

```let input: [Int] = readLine()!.characters.split(separator: " ").map{ Int(String($0))! }```

String.characters 프로퍼티를 사용하면 String의 각 문자에 접근할 수 있으며, 원하는 character로 split()을 할 수 있다.
그 이후에는 map을 통해 split한 String (원래 의도라면 알고리듬 테스트를 위한 Int형 숫자)를 Int()로 형변환까지 하면 input은 사용자가 입력한 Int 배열이 된다.
