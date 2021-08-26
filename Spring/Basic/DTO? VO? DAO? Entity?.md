# DTO VO DAO Entity

DTO -> 가변의 성격(Getter / Setter) 둘다 가능

```java
@Getter
@NoArgsConstructor
public class RegistrationDto {
    private String title;
    private String contents;
    private String author;

    @Builder
    public RegistrationDto(String title, String contents, String author) {
        this.title = title;
        this.contents = contents;
        this.author = author;
    }

    public Board toEntity(){
        return Board.builder()
                .title(title)
                .contents(contents)
                .author(author)
                .build();
    }

}

```

DAO -> DB에 직접 접근하여 CRUD 가능 -> DB접근 로직과 비지니스 로직을 분리하기 위하여 사용
ex) Mybatis 

Entity -> 실제 DB테이블과 1:1로 매핑 -> 즉, DB의 테이블 내에 존재하는 컬럼만 속성으로 가져야함

```java
@NoArgsConstructor
@Entity
@Getter
public class Board extends BaseEntity{
//GenveratedValue => 기본키(primary key) 매핑에 사용 직접 할당시에는 @Id만 사용, 자동으로 사용시 GeneratedValue 사용
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long boardId;

    @Column(length = 500, nullable = false)
    private String title;

    @Column(columnDefinition = "TEXT",nullable = true)
    private String contents;

    private String author;

    @Builder
    public Board(String title, String contents, String author) {
        this.title = title;
        this.contents = contents;
        this.author = author;
    }
    public void update(String title, String contents){
        this.title = title;
        this.contents = contents;
    }
}
```

Entity / DTO를 분리하는 이유 -> DB계층과 View 계층을 나누기 위하여



