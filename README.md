# Задача 1 по лекции «JVM. Организация памяти, сборщики мусора, VisualVM»
## Loaders
Класс JvmComprehension был загружен с помощью ApplicationClassLoader, классы Object, Integer, System с помощью BootStrapClassLoader.
## Память
### Stack
В stack будут храниться переменные методов: main(String[] args) и (Object o, int i, Integer ii) класса JvmComprehension, println(String s) класса System.out, toString() класса Object.
#### Содержимое Stsck:
##### main(String[] args)
int i = 1;
Object o - ссылка на экземпляр Object (он хранится в heap)
Integer ii - ссылка на экземпляр Integer (он хранится в heap)
##### printAll(Object o, int i, Integer ii)
Переменные-аргументы метода:
Object o - ссылка на экземпляр Object (он хранится в heap)
int i - значение хранится здесь в Stack
Integer ii - ссылка на экземпляр Integer() (он хранится в heap)
Переменные:
Integer uselessVar - ссылка на экземпляр Integer() (он хранится в heap)
##### println(String s) и toString()
Тоже их переменные лежат в Stack, но их переменные мне неизвестны.
### Heap
В heap будут лежать экземпляры Object, а также экземпляры прочих используемых классов. Экземпляры Integer и String(из System.out.println(String s) тоже лежат heap, но они так же как String хранятся в готовых значениях и при создании переменной выдается готовая ссылка (т. е 
String x = "1";
String y = "1";
x == y; вернет true)
### Metaspace
В Metaspace будут храниться классы используемые в программе. Object.class и Integer.class, System.out и прочие системные классы.
## Сборщик мусора
Сборщик мусора удаляет экземпляры из heap, на которые не осталось ссылок. В данной программе сборщик мусора не вызывался, так как не было потеряно ссылок на экземпляры.
