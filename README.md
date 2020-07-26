## Задача №2 (необязательная) - "@CsvFileSource"

Важно: данная задача не является обязательной! Её не выполнение не влияет на получение зачёта по ДЗ.

### Легенда

Мы с вами на лекции разобрали аннотацию `@CsvSource`, внутри которой можно писать строки в формате CSV.

Писать значения прямо в аннотации неплохо, но если их будет штук 50 - то, наверное, ничего хорошего из этого не выйдет.

Поэтому неплохо бы воспользоваться возможностями JUnit и аннотации `@CsvFileSource`.

Вам необходимо взять [проект с лекции](https://github.com/netology-code/javaqa-code/tree/master/2.4_params/bonus-calculator) и дописать оставшиеся непроверенными сценарии таким образом, чтобы данные читались из файла формата CSV.

Сам файл необходимо положить в каталог `resources` (каталог `resources` тоже нужно создать) следующим образом:

![](https://github.com/netology-code/javaqa-homeworks/raw/master/params/pic/test-resources.png)

Быстро это сделать можно вот так: `Alt + Insert` на каталоге `test` выбираете `New File` и дальше вводите имя файла вместе с именем каталога:

![](https://github.com/netology-code/javaqa-homeworks/raw/master/params/pic/fast-creation.png)

IDEA сама за вас создаст и каталог, и файл.

После чего в боковой панельке следует сделать reimport Maven-проекта:

![](https://github.com/netology-code/javaqa-homeworks/raw/master/params/pic/reimport.png)

И IDEA поставит вам красивую иконочку на ресурсы для тестов:

![](https://github.com/netology-code/javaqa-homeworks/raw/master/params/pic/test-resources-imported.png)

Сам файл вы можете редактировать прямо в IDEA (это обычный текстовый файл, но подчиняющийся правилам CSV).

При этом обратите внимание, что кодировка файла UTF8:

![](https://github.com/netology-code/javaqa-homeworks/raw/master/params/pic/encoding.png)

Если это не так - кликните на указанном поле и выберите UTF8:

![](https://github.com/netology-code/javaqa-homeworks/raw/master/params/pic/utf8.png)

Вам нужно: загрузить исходные коды для этой аннотации (делается через IDEA), прочитать комментарии к элементам аннотации и использовать только те, которые нужны.

Переделанный проект нобходимо загрузить на GitHub (предварительно удостоверьтесь, что ваши тесты работают).

Итого: у вас должен быть репозиторий на GitHub, в котором расположен ваш Java-код и автотесты к нему.

Важно: путь к файлу нужно будет указывать вот так: `/data.csv` - это будет означать, что ищем в каталоге `resources`.

Важно: когда элемент аннотации требует массив, но вы передаёте всего один элемент, то можно не писать фигурные скобки.

Например, на лекции было (`value` требовал массив):
```java
  @CsvSource(
      value={
          "'registered user, bonus under limit',100060,true,30",
          "'registered user, bonus over limit',100000060,true,500"
      }
  )
```

Если элемент в массиве только один, то полная запись:
```java
  @CsvSource(
      value={
          "'registered user, bonus under limit',100060,true,30"
      }
  )
```

Сокращённая (работает только с одним элементом):
```java
  @CsvSource(value="'registered user, bonus under limit',100060,true,30")
```

А если вы везунчик и элемент ещё и называется `value`, то:
```java
  @CsvSource("'registered user, bonus under limit',100060,true,30")
```

<details>
  <summary>Подсказка</summary>
  
  Использованная аннотация должна выглядеть следующим образом:
  ```java
  @CsvFileSource(resources = "/data.csv")
  ```
</details>
