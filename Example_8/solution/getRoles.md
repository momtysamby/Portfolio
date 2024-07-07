# Метод GET GetRoles

Получение всех ролей пользователя в организации.

#### Адрес

*URL*/getRoles

#### Тело запроса

| Тип    | Имя          | Описание          |
|--------|--------------|-------------------|
| *Guid* | user         | Guid пользователя |
| *Guid* | organization | Guid организации  |


#### Ответ

В ответе вернутся данные о занимаемых должностях сотрудника (<code>RoleType</code>, <code>RoleResponse</code>), где:
1. <code>RoleType</code> — тип занимаемой должности. Возможные значения:
   1. head — руководитель;
   2. ChiefAccountant — главный бухгалтер;
   3. Sender — уполномоченный представитель (отправитель);
   4. Ip — индивидуальный предприниматель.
2. <code>RoleResponse</code> — занимаемая должность сотрудника в формате "{[Person](/Example_8/solution/PersonProps.md)}/{[Position](/Example_8/solution/Position.md)}".