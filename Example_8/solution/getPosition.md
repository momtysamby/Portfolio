# Метод GET GetPosition

Получение должности сотрудника в организации.

#### Адрес

*URL*/getPosition

#### Тело запроса

| Тип    | Имя          | Описание          |
|--------|--------------|-------------------|
| *Guid* | user         | Guid пользователя |
| *Guid* | person       | Guid сотрудника   |
| *Guid* | organization | Guid организации  |


#### Ответ

В ответе вернется значение <code>Position</code> с занимаемой должностью сотрудника в организации.

*string* [Position](/Example_8/solution/Position.md) = "O{[Organization](/Example_8/solution/Organization.md)}<->P{[Person](/Example_8/solution/PersonProps.md)}: {Title}"