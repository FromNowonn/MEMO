# Stream?

기존의 Java에서 사용하는 `for` or `foreach` 가 아닌, 데이터의 흐름을 활용한 기법

## Why Stream?

`for` or `foreach` 를 사용할경우 로직이 복잡해질수록 코드가 길어지고 가독성이 떨어지게되며, 메소드가 나뉠 경우 루프또한 여러번 돌게 되는 현상이 발생.

Example
배열의 원소들을 리스트로 환원하는 간단한 입출력 예제이다.

//Stream 전
```java
int[] arr = {1,2,3,3,3,12,5,6,3,7,10,8,9};
List<Integer> list = new ArrayList<>();
for(int i=0;i<arr.length;i++){
    list.add(arr[i]);
}
System.out.println(list.toString());
```

//Stream 후
```java
int[] arr = {1,2,3,3,3,3,5,6,7,7,7,8,9};
List<Integer> list = new ArrayList<>();
System.out.println(Arrays.stream(arr).boxed().collect(Collectors.toList()));
```

간단한 예제인데도 불구하고 확연한 차이가 보인다. 

조금더 복잡한 예제로, 중복 제거를 한 후 역순 출력을 하는 입출력 예제를 구현해 보자.

//Stream 전
```java
int[] arr = {1,2,3,3,3,12,5,6,3,7,10,8,9};
Set<Integer> set = new HashSet<>();

for(int i=0;i<arr.length;i++){
    set.add(arr[i]);
}

List<Integer> list = new ArrayList<>(set);

list.sort(Comparator.reverseOrder());

System.out.println(list.toString());
```

//Stream 후

```java
System.out.println(Arrays.stream(arr).
                boxed().
                distinct().
                sorted(Comparator.reverseOrder()).
                collect(Collectors.toList()));
```

Stream 전엔 복잡한 자료형의 선언, 로직의 구현이 필요했다면, STREAM을 사용한 이후엔 단 한줄에 해결이 되었다.

그렇다면, 우리는 한번 더 생각 해 볼 수 있다. Lambda식과 Stream을 활용할 수 있는가?

바로 이부분이다. Stream의 압도적 편리함이.


Example

홀수를 List에 담아 출력하는 예제를 구현해보자.

//lambda, Stream 전
```java
List<Integer> list = new ArrayList<>();

Sum sumNum = new Sum() {
    @Override
    public int sum(int a, int b) {
        return a + b;
    }
};

for (int i=0; i<10; i++){
    list.add(sumNum.sum(i, i+1));
}

for (int i=0; i<10; i++){
    System.out.print(list.get(i) + " ");
}
```

//lambda, Stream 후

```java
List<Integer> list = new ArrayList<>();

for (int i = 0; i < 10; i++) {
  Sum sumNum2 = (a, b) -> a + b;
  list.add(sumNum2.sum(i, i + 1));
}

Stream<Integer> stream = list.stream();

stream.forEach((Integer i) -> {
  System.out.print(i+" ");
});
```

간단한 입출력 임에도 불구하고 코드의 가독성이 좋아진다.

프로그램의 규모가 커질수록 코드의 로직은 복잡해 질것이다.

lambda 와 Stream의 적절한 사용으로 효율과 가독성을 증대시킬 수 있다.
