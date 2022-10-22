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
