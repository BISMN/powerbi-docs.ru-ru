---
title: Передача параметра отчета в URL-адресе для отчета с разбивкой на страницы в Power BI (построитель отчетов Power BI)
description: Здесь приводятся сведения о передаче параметров отчета в отчет путем их включения в URL-адрес отчета с разбивкой на страницы.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: f7f1b777e7c4e54dbdcfb1757fe4df274624a580
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71075982"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Передача параметра отчета в URL-адресе для отчета с разбивкой на страницы в Power BI 

Вы можете передать параметры отчета в отчет, включив их в URL-адрес отчета с разбивкой на страницы. Все параметры запроса могут иметь соответствующие параметры отчета. Таким образом, параметр запроса передается в отчет путем передачи соответствующего параметра отчета. Чтобы служба Power BI смогла распознать имя параметра в URL-адресе, к имени необходимо добавить префикс `rp:`. 

Параметры отчета зависят от регистра. В них используются следующие специальные символы. 

- Пробел в части параметра URL-адреса заменяется знаком "плюс" (+).  Например: 

    ```rp:Holiday=Christmas+Day```

- Точка с запятой в любой части строки заменяется символами `%3A`.

Браузеры должны автоматически применять правильную кодировку URL-адресов. Кодировать символы вручную не требуется. 

Чтобы задать параметр отчета в URL-адресе, используйте следующий синтаксис: 

```
rp:parameter=value
```

Например, чтобы указать два параметра ("Salesperson" и "State"), определенных в отчете в области "Моя рабочая область", используйте следующий URL-адрес: 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Чтобы указать те же два параметра, которые определены в отчете в приложении, используйте следующий URL-адрес: 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&State=Utah 
```

Чтобы передать значение NULL для параметра, используйте следующий синтаксис: 

```
parameter:isnull=true
```

Например:

```
rp:SalesOrderNumber:isnull=true
```

Чтобы передать логическое значение, используйте 0 для параметра false и 1 для параметра true. Чтобы передать число с плавающей точкой, включите десятичный разделитель языкового стандарта сервера.

> [!NOTE]
> Если отчет содержит параметр отчета со значением по умолчанию, а свойству **Prompt** задано значение **false**, (то есть свойство **Prompt User** не задано в диспетчере отчетов), вы не можете передать значение для этого параметра отчета в URL-адресе. В этом случае администраторы могут запрещать пользователям добавлять или изменять значения определенных параметров отчета.

## <a name="additional-examples"></a>Дополнительные примеры 

Следующий пример URL-адреса содержит многозначный параметр "Salesperson". Формат многозначного параметра необходим, чтобы повторять имя параметра для каждого значения. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

В приведенном ниже примере URL-адреса передается один параметр SellStartDate со значением "7/1/2005" для сервера отчетов в основном режиме.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>Дальнейшие действия

- [Параметры URL-адреса в отчетах с разбивкой на страницы в Power BI](report-builder-url-parameters.md)
- [Сведения об отчетах с разбивкой на страницы в Power BI Premium](paginated-reports-report-builder-power-bi.md)
