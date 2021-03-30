## AllArgsConstructor
staticName이라는 옵션을 사용하여 생성자를 private으로 생성하고, private 생성자를 감싸고 있는 static factory 메소드를 추가할 수 있다.

// 롬복코드
@AllArgsConstructor(staticName = "of")
public class TestDTO {
    private int price;
    private int discount;
    private final int amount;
}

https://irerin07.tistory.com/150