


OkHttpClient() 생성자의 내부를 따라가다보면 ConnectionPool() 이라는 객체
이 Client 객체를 사용하여 여러 REST API에 요청을 보내면 5개의 Connection Pool을 만들어 관리한다. 같은 주소로의 요청은 새로운 커넥션을 맺지 않고 ConnectionPool에 유지되어 있는 커넥션을 사용하게 된다. 


ConnectionPool(5, 5L, TimeUnit.MINUTES) 생성자의 첫 번째 인자는 최대 몇 개의 커넥션을 유지할 것인지를 의미한다. 두 번째 인자는 얼마동안 커넥션을 유지할 것인지에 대한 내용이다. 마지막 인자는 두 번째 인자의 단위를 의미한다. 위에서 본 예제에서는 5분(TimeUnit.MINUTES)을 의미한다.

