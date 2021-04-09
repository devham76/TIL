## Response 가져오기

### retrieve()
- 바로 Body를 가지고옴
- `.bodyToMono(String.class)` 형태로 바로 사용 가능 : bodyToFlux 도 사용가능

```
WebClient.create().get()
	.retrieve()
	.onStatus(HttpStatus::is4xxClientError, clientResponse -> Mono.error(RuntimeException::new))
	.onStatus(HttpStatus::is5xxServerError, clientResponse -> Mono.error(RuntimeException::new))
	.bodyToMono(String.class);
```

### exchange()
- 상태값, Header 등을 가지고옴
- ClientResponse
```
WebClient.create().get()
	.exchange()
	.flatMap(clientResponse -> {

		if (clientResponse.statusCode().is4xxClientError()) {
			return Mono.error(new RuntimeException("4xx exception"));
		} else if (clientResponse.statusCode().is5xxServerError()) {
			return Mono.error(new RuntimeException("5xx exception"));
		}

		return Mono.just(clientResponse);
	});
```

---
### Reference
- https://akageun.github.io/2019/06/23/spring-webflux-4-webclient.html
- http://wonwoo.ml/index.php/post/2364