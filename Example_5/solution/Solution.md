### Содержание
- [Задание 1](#задание-1)
- [Задание 2](#задание-2)
- [Задание 3](#задание-3)

## Задание 1

<table style="width:100%">
  <tr>
    <th>Тип</th>
    <th>Название</th>
    <th>Обязательность</th>
    <th>Дефолт</th>
    <th>Описание</th>
  </tr>
  <tr>
    <td>int</td>
    <td>afterDays</td>
    <td>-</td>
    <td>7</td>
    <td>Конец выборки от текущего дня. Например:
        <ul>
            <li><code>afterDays = 0</code> — через 7 дней;</li>
            <li><code>afterDays = N</code> — через N дней.</li>
        </ul>
    Невозможно поставить такое значение, чтоб вернулось только за вчера
    </td>
  </tr>
  <tr>
    <td>int</td>
    <td>tfDays</td>
    <td>-</td>
    <td>1</td>
    <td>Начало выборки от текущего дня. Например:
        <ul>
            <li><code>tfDays = -1</code> — вчера;</li>
            <li><code>tfDays = 0, 1, 2</code> — завтра;</li>
            <li><code>tfDays = N > 3</code> — через (N-1) дней от сегодня.</li>
        </ul>
    </td>
    </td>
  </tr>
</table>

Чтобы вернуть все события за:
<ul>
    <li>вчера — передайте <code>tfDays = -1</code>;</li>
    <li>промежуток с завтра до (сегодня + 7 дней) — передайте <code>afterDays = 7</code>, <code>tfDays = 1</code>;</li>
    <li>сегодня — эндпоинт не позволяет выполнить данное действие.</li>
</ul>

По реализованной логике происходит вычитание дня. Библиотека C# либо вычтет ровно 24 часа из текущего времени либо кастанет к началу дня. Потом выполяентя операция <code>e.Start - datetime</code> и сравнивается с текущим значением. Исходя из этого и получаем дату.

## Задание 2

1. <code>GET http://domain.com/Events?isArchive=true&type=0</code> — возвращает все события согласно фильтрам с событиями из архива и всеми типами событий.
    ````
    GET /login HTTP/1.0
    Host: http://domain.com/Events
    Content-Type: application/x-www-form-urlencoded; charset=utf-8
    Content-Length: 21
    isArchive=true&type=0
    ````
2. <code>GET http://domain.com/Events?isArchive=false&type=1</code> — возвращает все события согласно фильтрам без событий из архива и с типом событий “Личное”.
    ````
    GET /login HTTP/1.0
    Host: http://domain.com/Events
    Content-Type: application/x-www-form-urlencoded; charset=utf-8
    Content-Length: 22
    isArchive=false&type=1
    ````
3. <code>POST http://domain.com/Events?Start=&Name=someName&Note=someNote&Type=4</code> — добавляет событие с текущей датой начала с названием someName, с описанием someNote и типом события “Нет типа”. Вообще POST запрос не принято отправлять с query, вопрос секьюрности даже - query попадают всегда в url строку браузера. Но для примера оставлю, так как в задании было указано, что можно написать на чем угодно
    ````
    POST /login HTTP/1.0
    Host: http://domain.com/Events
    Content-Type: application/x-www-form-urlencoded; charset=utf-8
    Content-Length: 40
    Start=&Name=someName&Note=someNote&Type=4
    ````

## Задание 3

````
SELECT COUNT(id) FROM users WHERE lastName = 'Иванов' OR lastName = 'Иванова'
````