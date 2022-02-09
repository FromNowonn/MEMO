# Lambda

람다 함수는 프로그래밍 언어에서 사용되는 개념으로 익명 함수(Anonymous functions)를 지칭하는 용어이다.

### 익명 함수란?
`식별자없이 실행가능한 함수` 즉, 함수인데 함수를 따로 만들지 않고 코드한줄에 함수를 써서 그것을 호출하는 방식

## EX

```java
interface cal{
        public int calc(int a,int b);
}
  
```

### 기존
```java
 cal cll = new cal() {
            @Override
            public int calc(int a, int b) {
                return a + b;
            }
        };
        System.out.println(cll.calc(3,5));
}
```

### 람다식

```java

        cal Cal = (a, b) -> a+b;
        System.out.println(Cal.calc(3, 5));
```





