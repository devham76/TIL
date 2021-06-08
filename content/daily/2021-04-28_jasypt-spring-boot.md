
## Failed to bind properties under 'spring.datasource.password' to java.lang.String` 

- 문제 : Reason: either 'jasypt.encryptor.password' or one of ['jasypt.encryptor.private-key-string', 'jasypt.encryptor.private-key-location'] must be provided for Password-based or Asymmetric encryption

- 해결 : -Djasypt.encryptor.password={mypassword} 

- [참고](https://github.com/ulisesbocchio/jasypt-spring-boot/issues/154)