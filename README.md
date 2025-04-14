# Многомодульный проект на Gradle

Для закрепления лекционного материала попрактикуемся, как создавать проекты.

Стандартный многомодульный проект имеет составляющие по функционалу:

db - модуль работы с базой данных

api - модуль работы с web

service - слой сервисов.

## Реализация

Для начала создайте одномодульный проект - как это делали на занятии.

После создаем 3 папки в директории проекта: db, api, service.

В каждой из директории создаем *build.gradle* c содержимым:

 ```java
 plugins {
    id 'java'
}

group 'ru.netology'
version '1.0-SNAPSHOT'

repositories {
    mavenCentral()
}

dependencies {

} 
 ```

Чтобы подключить новые модули к проекту, добавляем в корне проекта в settings.gradle новые созданные модули:

```java
include 'db'
include 'service'
include 'api'
```

После создания многомодульного проекта подключим связанные модули между собой.

Для подключения модуля db в модуль service добавим зависимость:

```java
dependencies {
    implementation project(":db")
}
```
Для подключения модуля service в модуль api добавим зависимость:

```java
dependencies {
    implementation project(":db")
    implementation project(":service")
}
```
Теперь можно собрать проект, выполнив команду:

*gradle build*
