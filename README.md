### Поправить .env  
### Собрать  
```docker-compose up --build -d --remove-orphans --force-recreate```


### Исправить разарешеия для хранения данных ES, graylog  
```chown -R 1000:1000 ${DATA_FOLDER_PATH}/elasticsearch```  
```chown -R 1100:1100  ${DATA_FOLDER_PATH}/graylog/journal```  


### Подключаться через web на адес ${GRAYLOG_WEB_ENDPOINT_URI}  
[Документация](https://docs.graylog.org/docs/docker)

### Логин и пароль  
Логин администратора  
```admin```  
Пароль администратора задается через его хеш.  
Для получения хеша выполнить  
```echo "$password"| sha256sum```  
Заменить полученным значением GRAYLOG_ROOT_PASSWORD_SHA2 в *.env-default*.  


### Создать Input (System\Inputs)  
- Выбрать Input (Syslog UDP), нажать Laun new input
- Отметить Global
- Ввести название (Syslog UDP)
- Задать порт для приема внутри контейнера (1514)
- Сохранить

### Отправить тестовое сообщение на graylog в формате syslog  
#### Test UDP syslog messages on port 514 with the following command:  
```echo "<14>Test UDP syslog message" >> /dev/udp/<target_hostname_or_ip_address>/514```
#### Test TCP syslog messages on port 514 with the following command:
```echo "<14>Test TCP syslog message" >> /dev/tcp/<target_hostname_or_ip_address>/514```





