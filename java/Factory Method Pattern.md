# 팩토리 메소드 패턴

## Factory Method Pattern이란?

>객체를 만들어내는 부분을 서브 클래스에 위임하는 패턴으로  객체를 생성, 합성하는 방법이나 객체의 표현방법을 시스템과 분리하는 방식이다.

## Example

---
## 기존 Java Code

```java

public class Book {

    public String getBook(String kindsOfBook) {
        switch (kindsOfBook) {
            case "comic":
                return "This is Comic Book";
            case "novel":
                return "This is Novel Book";
            case "autobiography":
                return "This is Autobiography Book";
            default:
                System.out.println("책장에 없는 책입니다.");
                return null;
        }
    }
}
```

### Book Class의 getBook method안에 3가지의 기능이 종속되어 결합도가 높은 상태이다.

## How to Solve This Problem??

---

## Factory Method Pattern

`BookFactory 클래스`

```java
public class BookFactory {

    public BookShelf getBook(String kindsOfBook) {
        switch (kindsOfBook) {
            case "comic":
                return new Comic();
            case "novel":
                return new Novel();
            case "autobiography":
                return new Autobiography();
            default:
                System.out.println("책장에 없는 책입니다.");
                return null;
        }
    }
}

```
---
`BookShelf 인터페이스`
```java
public interface BookShelf {
    String getBook(String book);
}

```
---

`Novel 클래스`
```java
public class Novel implements BookShelf {

    @Override
    public String getBook(String kindsOfBook) {
        return "This is Novel Book";
    }
}
```

`Comic 클래스`
```java
public class Comic implements BookShelf {

    @Override
    public String getBook(String kindsOfBook) {
        return "This is Comic Book";
    }
}
```

`Autobiography 클래스`
```java
public class Autobiography implements BookShelf {

    @Override
    public String getBook(String kindsOfBook) {
        return "This is Autobiography Book";
    }
}
```


`Book Test`
```java 
public class BookMain {
    public static void main(String[] args) {
        Book book = new Book();
        System.out.println("Existing Book : " + book.getBook("comic"));
        System.out.println("Existing Book : " + book.getBook("novel"));
        System.out.println("Existing Book : " + book.getBook("autobiography"));

        BookFactory bookFactory = new BookFactory();
        System.out.println("Factory Book : " + bookFactory.getBook("comic"));
        System.out.println("Factory Book : " + bookFactory.getBook("novel"));
        System.out.println("Factory Book : " + bookFactory.getBook("autobiography"));
    }
}
```
---
`출력`

![image](https://user-images.githubusercontent.com/51487025/150316932-dfaea6c0-06fe-4e65-bf3c-86167f9f2673.png)



### 이와같이 팩토리 메소드 패턴을 사용하는 이유는 클래스간의 결합도를 낮추기 위한것이다.
### 팩토리 메소드 패턴을 사용하는 경우 직접 객체를 생성해 사용하는 것을 방지하고 서브 클래스에 위임함으로써 보다 효율적인 코드 제어를 할 수 있고 의존성을 느슨하게 할 수 있다.
### 이처럼 의존성을 제거하게 되면 각각의 서브클래스만의 로직에 집중할 수 있는 장점이 생긴다.
   

