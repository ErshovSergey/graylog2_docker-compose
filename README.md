Собрать  
```docker-compose up --build -d --remove-orphans --force-recreate```

Подключаться через web на адес ${GRAYLOG_WEB_ENDPOINT_URI}  
[Документация](https://docs.graylog.org/docs/docker)

### Логин и пароль  
Логин администратора  
```admin```  
Пароль администратора задается через его хеш.  
Для получения хеша выполнить  
```echo "$password"| sha256sum```  
Заменить полученным значением GRAYLOG_ROOT_PASSWORD_SHA2 в *.env-default*.  

### Отправить тестовое сообщение на graylog в формате syslog  
#### Test UDP syslog messages on port 514 with the following command:  
```echo "<14>Test UDP syslog message" >> /dev/udp/<target_hostname_or_ip_address>/514```
#### Test TCP syslog messages on port 514 with the following command:
```echo "<14>Test TCP syslog message" >> /dev/tcp/<target_hostname_or_ip_address>/514```
