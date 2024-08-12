<h1> Отчёт по проекту Spring AOP</h1>
Данный проект демонстрирует пример использования Spring AOP для логирования операций в приложении, имитирующем управление пользователями и их заказами. 
Проект написан на `Java21` с использованием `Spring Boot 3`. Для работы требуется БД `PostgreSQL`.
<h2>
  Инструкция по запуску
</h2>
<h3>Запуск приложения</h3>
  Для запуска приложения необходимо перейти в корень проекта и выполнить команды 
  ```
  mvn install
  mvn spring-boot:run
  ```
<h3>Запуск базы данных</h3>

  В проекте используется база данных `PostgreSQL`. В файле `application.properties` необходимо указать url, имя пользователя и пароль. 
  Затем выполнить команду 
  ```
  docker-compose up
  ```
<h3>Запуск тестов</h3>
  Для запуска тестов выполните команду 
  ```
  mvn test
  ```
<h2>Логирование</h2>
  Для логирования используется библиотека `Log4j2`. Конфигурация описана в файле `log4j2.xml`.
  Используется базовая конфигурация для вывода логов в консоль
<h2>Примеры логирования</h2>
  Логирование вызова метода `createOrder()`
  ```
 main] com.example.demo.aspect.LoggingAspect    : Create method <<createOrder>> is running
  ```
  Логирование выброса исключения 
  ```
  main] com.example.demo.aspect.LoggingAspect    : Exception in createOrder method () - User does not exists
  ```
<h2>Примеры тестов</h2>
Тест создания пользователя 
```
@Test
    void testCreateUser() {
        User user = new User();
        when(userRepository.save(user)).thenReturn(user);

        User result = userService.createUser(user);
        assertNotNull(result);
        assertEquals(user, result);
    }
    ```
