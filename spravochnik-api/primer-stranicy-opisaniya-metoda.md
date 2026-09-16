---
order: 0.5
title: get Пример страницы описания метода
---

Взято из яндекса [get | Яндекс Директ API](https://yandex.ru/dev/direct/doc/ru/turbopages/get)

Возвращает параметры Турбо-страниц.

## **Ограничения**

Метод возвращает не более 10 000 объектов.

Метод возвращает только опубликованные Турбо-страницы.

## **Запрос**

Структура запроса в формате JSON:

```
{
  "method": "get",
  "params": { /* params */
    "SelectionCriteria": { /* IdsCriteria */
      "Ids": [(long), ... ],
      "BoundWithHrefs": [(string), ...]
    },
    "FieldNames": [( "Id" | "Name" | "Href" | "PreviewHref" | "TurboSiteHref" | "BoundWithHref" ), ... ], /* required */
    "Page": {  /* LimitOffset */
      "Limit": (long),
      "Offset": (long)
    }
  }
}
```

<table header="row">
<tr>
<td>

**Параметр**

</td>
<td>

**Тип**

</td>
<td>

**Описание**

</td>
<td>

**Обязательный**

</td>
</tr>
<tr>
<td>

**Структура params (для JSON) / GetRequest (для SOAP)**

</td>
<td>



</td>
<td>



</td>
<td>



</td>
</tr>
<tr>
<td>

`SelectionCriteria`

</td>
<td>

IdsCriteria

</td>
<td>

Критерии отбора Турбо-страниц.

Чтобы получить все опубликованные Турбо-страницы пользователя, не указывайте `SelectionCriteria`.

</td>
<td>

Нет

</td>
</tr>
<tr>
<td>

`FieldNames`

</td>
<td>

array of TurboPageFieldEnum

</td>
<td>

Имена параметров верхнего уровня, которые требуется получить.

</td>
<td>

Да

</td>
</tr>
<tr>
<td>

`Page`

</td>
<td>

[LimitOffset](https://yandex.ru/dev/direct/doc/dg/best-practice/get.html#LimitOffset)

</td>
<td>

Структура, задающая страницу при [постраничной выборке](https://yandex.ru/dev/direct/doc/dg/best-practice/get.html) данных.

</td>
<td>

Нет

</td>
</tr>
<tr>
<td>

**Структура IdsCriteria**

</td>
<td>



</td>
<td>



</td>
<td>



</td>
</tr>
<tr>
<td>

`Ids`

</td>
<td>

array of long

</td>
<td>

Отбирать Турбо-страницы с указанными идентификаторами. От 1 до 10 000 элементов в массиве.

</td>
<td>

Нет

</td>
</tr>
<tr>
<td>

`BoundWithHrefs`

</td>
<td>

array of string

</td>
<td>

Отбирать Турбо-страницы с указанными ссылками.

</td>
<td>

Нет

</td>
</tr>
</table>

## **Ответ**

Структура ответа в формате JSON:

```
{
  "result": { /* result */
    "TurboPages": [{ /* TurboPageGetItem */
      "Id": (long),
      "Name": (string),
      "Href": (string),
      "PreviewHref": (string),
      "TurboSiteHref": (string),
      "BoundWithHref": (string)
    }, ... ],
    "LimitedBy": (long)
  }
}
```

| **Параметр**                                             | **Тип**                   | **Описание**                                                                                                                                                                                                                      |
|----------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Структура result (для JSON) / GetResponse (для SOAP)** |                           |                                                                                                                                                                                                                                   |
| `TurboPages`                                             | array of TurboPageGetItem | Параметры Турбо-страницы.                                                                                                                                                                                                         |
| `LimitedBy`                                              | long                      | Порядковый номер последнего возвращенного объекта. Передается в случае, если количество объектов в ответе было ограничено лимитом. См. раздел [Постраничная выборка](https://yandex.ru/dev/direct/doc/dg/best-practice/get.html). |
| **Структура TurboPageGetItem**                           |                           |                                                                                                                                                                                                                                   |
| `Id`                                                     | long                      | Идентификатор Турбо-страницы.                                                                                                                                                                                                     |
| `Name`                                                   | string                    | Название Турбо-страницы.                                                                                                                                                                                                          |
| `Href`                                                   | string                    | Ссылка на опубликованную Турбо-страницу.                                                                                                                                                                                          |
| `PreviewHref`                                            | string                    | Ссылка для предварительного просмотра Турбо-страницы.                                                                                                                                                                             |
| `TurboSiteHref`                                          | string                    | Ссылка вида [`имя.turbo.site`](http://имя.turbo.site). Если такая ссылка не привязана к Турбо-странице, значение будет пустым.                                                                                                    |
| `BoundWithHref`                                          | string                    | Ссылка, по которой была найдена Турбо-страница (соответствует ссылке из параметров запроса, без выравнивания регистра и нормализации).                                                                                            |