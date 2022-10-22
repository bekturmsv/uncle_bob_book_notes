# clean_code_notes
Это заметки из книги Роберта Мартина "Чистый код".

# Оглавление
1. [Чистый код](#Чистый-код)
     - [Правило бойскаута](#Правило-бойскаута)
2. [Форматирование](#Форматирование)
3. [Имена](#Имена)
4. [Функции](#Функции)
5. [Комментарии](#Комментарии)
6. [Объекты и структуры данных](#Объекты-и-структуры-данных)
7. [Обработка ошибок](#Обработка-ошибок)
8. [Модульные тесты](#Модульные-тесты)
9. [Классы](#Классы)
10. [Системы](#Системы)

## Чистый код
### Правило бойскаута
Оставь место стоянки чище, чем оно было до твоего прихода.

### Форматирование
- Имя файла должно быть простым, но содержатель. Чтобы читатель мог легкой найти его и понимать, что он открыл нужный ему файл.
- Код читается слева направо и сверху вниз.
    - Код должен читаться как газетная статья.
    - Используйте отступы справа, чтобы у кода была иерархия для обозначения области видимости.
    - Каждая строка представляет выражение или условие, а каждая группа строк представляет законченную мысль.
    - Пустая строка нужна, чтобы показать начало новой мысли.
    - Строки не должны быть слишком длинными. Максимум 80-120 символов.
    - Используйте пробелы для горизонтального разделения.(Не let b=5, а let b = 5)
- Связанные между собой строки кода должны находиться рядом друг с другом.
    - Переменные и функции  стоит объявлять как можно ближе к месту их использования.
    - Переменные экземпляров объявляются в одном и том же месте. Обычно в самом начале.
- В каждом проекте должны быть до начала написания кода должны быть составлены правила форматирования и реализации функционала. Так как каждый разработчик может иметь разные стили и один и тот же функционал можно реализовывать по-разному.

## Имена
### Общие рекомендации:
- Придерживаться стиля именования переменных в проекте(cameCase, snake_case и т.д.).
- Использовать информативные имена для переменных, методов, объектов, классов и т.д., чтобы без труда любой человек даже вне проекта мог разобраться в коде и понять его. Имена на 90% определяют удобочитаемость кода.
- Используйте существующие термины из разных номенклатур(PI = 3.14). Имена имеющие специальный смысл.
- Не используйте: сокращения, акронимы, кодировки, каламбур. Короткие имена подходят только в маленьких блоках кода.
- Легко произносимые имена проще запоминаются.

### Переменные
- Имя должно описывать контекст в которой она применяется или хранящиеся данные.

### Классы
- Имя должно быть существительным.
- Имя должно быть описательным.(Customer, Account - ДА, Data, Info - НЕТ)

### Функции:
- Имя должно быть глаголом или глагольным словосочетанием.(send, sendPayment)

## Функции
### Общие рекомендации:
- Информативные имена, для улучшения понимания приветствуется использование длинных имен.
    - Унарная - получает один аргумент. Глагол + сущ(аргумент). Write(name).
    - Бинарная - получает два аргумента. Для имен аргументов нужно учитывать их последовательность.
- Функции должны быть короткими. Обычно не больше 10 строк, если больше, то нужно чистить.
- Одно действие - одна функция(SRP, OCP - SOLID).
- Не повторяйтесь(DRY). Выносите повторяющиеся операции в отдельную функцию и переиспользуйте везде.
    - Если есть другие операции(сравнение, запросы на сервер) внутри функции, то пробуем вынести их в отдельные функции, если получается, то выносим и вызываем уже внутри.
- KISS - выбирайте простое или готовое решение, а не новое и сложное. Сэкономит время и повысит выразительность кода.

### Аргументы:
- Не передавайте слишком длинный список аргументов. Максимум 4, в идеале ни одного.
    - Если нужно передать длинный список аргументов, то передайте используя объект.
- Старайтесь не использовать аргументы флаги такой код(convertArrayForSelectOptions(arr, true)) менее понятен.

### Тернарные функции
Функция, которая принемает 3 агрумента.
Есть жесткая привязка к порядку  передаваемых аргументов.
Усложняет читаемость и увеличивет риск ошибки.

### SWITCH
Одна команда SWITCH на весь проект. 
Нарушает SRP, OCP. Используйте полиморфизм или ПАТТЕРНЫ(Фабрика, Стратегия и т. д.).

## Комментарии
### Общие рекомендации:
- Код должен быть понятен без комментариев.
- Если для понимания кода нужны дополнительные комментарии, то нужен рефакторинг.
- Комментарии могут быть добавлены только в случае описания сложной логики или вычислений.
- Тесты к коду лучше комментариев. Код можно задокументировать при помощи тестов.

## Объекты и структуры данных
Доступ к переменным ограничивается, чтобы другие программисты не зависели от них.
И имели возможность менять тип или реализацию этих переменных.

### Абстракция данных
Используйте интерфейсы или абстрактные классы для скрытия реализации.
Так наши методы не будут зависеть от данных.
Для этого нужно будет все продумать.

### Антисимметрия данных/объектов
Со структурами данных применяют процедурное программирование. 
Структуры данных:
- имеют открытый доступ к своим данным.
- не имеют собственного поведения.
Упрощают добавление нового поведения, но затрудняют добавление новых структур данных в существующие функции.

Объекты применяют объектно-ориентированное программирование.
Объекты:
- скрывают свои данные
- предоставляют функции для работы с их данными.
Упрощают добавление новых типов объектов, не меняя имеющегося поведения.
Усложняют добавление новых функций к имеющимся объектам.

Каждый из подходов предпочтительнее в той или иной ситуации.
Структуры данных, когда нужно добавить новые функции.
Объекты, когда нужно добавить новые типы данных.

### Закон Деметры
Объект не должен раскрывать свои данные и методы объектам с которыми он никак не связан. ***Не разговаривай с незнакомцами!***

Метод *area* в классе Shape должен ограничиваться вызовом методов след объектов:
- Shape
- Объекты созданные классом Shape
- Объекты Shape переданные area в качестве аргумента
- Объекты хранящиеся в переменной экземпляре  Shape

### Крушение поезда
Цепочка модулей, которые знают слишком много о других модулях.

*Пример: модуль S использует O, модуль O использует L.* ->
```a.getO().getL().doIt()```

## Обработка ошибок
### Общие рекомендации:
- Возвращайте сообщение с ошибкой, а не код.
- Если возможно, то разделяйте логику и обработки ошибки.
    - Используйте блоки try-catch-finally для ловли ошибок.
    - Можно создать класс обертку для обработки определенных типов ошибок.
- Не возвращайте null.
    - Возвращайте исключение или объект обертки исключения.
- Не передавайте null в аргументах.
    - Можно, если используется стороннее API.

### Используйте непроверяемые исключения 
Непроверяемые исключения - те исключения, которые компилятор не ожидает.
Проверяемые исключения нарушают принцип открытости-закрытости и инкапсуляции.

*Пример:
Есть цепочка друг друга методов, которые вызывают друг друга: А->B->...->Z.
В метод R мы добавили проверку на исключения: “Файл не найден”.
Поэтому придется добавлять обработку этого исключения во все методы, которые вызывают метод R.*

## Границы
### Общие рекомендации:
- Если сторонний код используется много раз оборачивать в отдельный класс.
- Не передавать  сторонний код в качестве аргумента и не возвращать при вызове.
- Использовать учебные тесты для проверки работы стороннего кода. 
- Помогают убедиться, что сторонний код работает так, как мы ожидаем.
    - Учебные тесты - проверка стороннего кода с данными, которые похожи на реальные.
- Ваш код должен меньше знать о подробностях стороннего кода.
- Используйте паттерн Адаптер, чтобы разделить ваш код и сторонний.
- Иногда границы не определены.

## Модульные тесты
### Общие рекомендации:
- Тесты - это документация к коду. Поэтому все правила к обычному применимы и к тестам.
    - Помогает убедиться, что все работает.
    - Помогает убедиться, что после изменений ничего не сломалось. Поддерживание гибкости и удобства сопровождения.
    - Упрощает чтение кода.
- Некачественные тесты приводят к некачественному коду.
- Одна проверка на тест. Разбивайте длинные тесты.
- Изучите TDD(Test-driven development) - сначала пишутся тесты, а потом код.

### F.I.R.S.T. - Чистые тесты.
Чистые тесты должны обладать 5 характеристиками:
- ***Быстрота(FAST)*** - тесты должны выполняться быстро. Прогон все тестов должно занимать как можно меньше времени. Потому что тесты будете запускать после каждого внесения изменений.
- ***Независимость(Independent)*** - тесты не должны зависеть друг от друга. Тесты должны выполняться независимо и в любом порядке. Иначе отслеживание ошибок усложняется.
- ***Повторяемость(Repeatable)*** - тесты должны выдавать одинаковый результат в любой среде: тестовая среда, ваш ноутбук, продакшн.
- ***Очевидность(Self-Validating)*** - результатом выполнения теста должно быть булево значение(true/false). Тест либо прошел, либо не прошел.
- ***Своевременность(Timely)*** - тесты должны быть написаны своевременно. Внесли изменение, написали тест. Или можно использовать TDD.

## Классы
### Общие рекомендации:
- Имя класса должно описывать его ответственность.
    - Должно укладываться в 25 слов без “если”, “и”, “или”, “но”.
- Строение класса - по правилу понижения, код читается как газетная статья.
    - Переменные - статические константы -> приватные статические переменные -> приватные переменные экземпляров.
    - Приватные функции следуют за открытыми функциями, которые их вызывают.
- Классы должны быть компактными.
- Инкапсулируйте поля и методы.
- Помните о принципе единой ответственности. Один класс имеет одну ответственность.
    - Это поможет выделить более качественные абстракции.
- Помните о принципе открытости-закрытости. Класс открыт для расширения, но закрыт для изменения. Имеет только одну причину для изменения.
- Соблюдение этих принципов помогает формировать понятную структуру. Разработчик сможет легко ориентироваться по коду.
    - Лучше много маленьких классов, чем несколько больших. Но не переусердствуйте.
- Связность класса должна быть высокой. Высокая связность - что все методы и переменные класса используются друг другом.
- Используйте интерфейсы и абстрактные классы, чтобы уменьшить влияние подробностей на классы. Подробности меняются со временем, поэтому добавление нового и внесение изменений должно вызывать меньше проблем.
    - Используйте принцип инверсии зависимостей. Для того чтобы классы зависели от абстракций, а не от конкретных подробностей.
    - Упрощает тестирование.
