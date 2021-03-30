
## 걸러내기: filter
filter()를 이용해서 시퀀스가 생성한 데이터를 걸러낼 수 있다. filter()에 전달한 함수의 결과가 true인 데이터만 전달하고 false인 데이터는 발생하지 않는다. 다음은 1부터 10 사이의 숫자 중에서 2로 나눠 나머지가 0인 (즉 짝수인) 숫자만 걸러내는 예를 보여준다.


```
Flux.range(1, 10)

        .filter(num -> num % 2 == 0)

        .subscribe(x -> System.out.print(x + " -> "));
```


실행 결과는 다음과 같다.


```
2 -> 4 -> 6 -> 8 -> 10 -> 
```


## Reference
https://javacan.tistory.com/entry/Reactor-Start-4-tbasic-ransformation