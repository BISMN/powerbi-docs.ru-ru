---
title: Поддерживаемые источники данных для отчетов с разбивкой на страницы Power BI
description: В этой статье вы узнаете о поддерживаемых источниках данных для отчетов с разбивкой на страницы в службе Power BI и о подключении к источникам данных базы данных SQL Azure.
author: onegoodsausage
ms.author: andremi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 07/19/2019
ms.openlocfilehash: f055cd27f25af399b63336e66aaad526ed740de2
ms.sourcegitcommit: 8aa90f662afb7492ffcfc11ef142cdb0ccecc9aa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68462314"
---
# <a name="supported-data-sources-for-power-bi-paginated-reports"></a>Поддерживаемые источники данных для отчетов с разбивкой на страницы Power BI

Эта статья описывает поддерживаемые источники данных для отчетов с разбивкой на страницы в службе Power BI и подключение к источникам данных базы данных SQL Azure. Некоторые источники данных поддерживаются изначально. К другим вы можете подключиться с помощью шлюзов данных.

## <a name="natively-supported-data-sources"></a>Изначально поддерживаемые источники данных

Отчеты с разбивкой на страницы изначально поддерживают следующие источники данных:

| Источник данных | Authentication | Примечания |
| --- | --- | --- |
| База данных SQL Azure <br>Хранилище данных SQL Azure | Базовый, единый вход, OAuth2 |   |
| Azure Analysis Services | SSO, OAuth2 |   |
| Набор данных Power BI | Единый вход | Наборы данных Premium Power BI и отличные от них |
| Набор данных Premium Power BI (XMLA) | Единый вход |   |
| Ввод данных | Н/Д | Данные внедряются в отчет. |

Все источники данных, кроме базы данных SQL Azure, готовы к использованию после отправки отчета в службу Power BI. Источники данных по умолчанию используют единый вход (SSO), где это применимо. Для Azure Analysis Services можно изменить тип проверки подлинности на OAuth2.

Для источников данных базы данных SQL Azure нужно указать дополнительные сведения, как описано в разделе [Проверка подлинности базы данных SQL Azure](#azure-sql-database-authentication).

## <a name="other-data-sources"></a>Другие источники данных

Кроме указанных выше изначально поддерживаемых источников данных, можно получить доступ к следующим источникам данных с помощью [шлюза данных Power BI](service-gateway-onprem.md):

- SQL Server
- Службы SQL Server Analysis Services
- Oracle
- Teradata

Для отчетов с разбивкой на страницы доступ к базе данных SQL Azure и Azure Analysis Services через шлюз данных Power BI сейчас невозможен.

## <a name="azure-sql-database-authentication"></a>Проверка подлинности для базы данных SQL Azure

Для источников данных базы данных SQL Azure нужно указать тип проверки подлинности, прежде чем запускать отчет. Это применимо только при первом использовании источника данных в рабочей области. В первый раз выводится следующее сообщение:

![Идет публикация в Power BI](media/paginated-reports-data-sources/power-bi-paginated-publishing.png)

Если не указать учетные данные, при запуске отчета возникает ошибка. Нажмите кнопку **Продолжить**, чтобы перейти на страницу **Учетные данные источника данных** для только что отправленного отчета:

![Параметры для базы данных SQL Azure](media/paginated-reports-data-sources/power-bi-paginated-settings-azure-sql.png)

Щелкните ссылку **Изменить учетные данные** для заданного источника данных, чтобы открыть диалоговое окно **Настройка**:

![Настройка базы данных SQL Azure](media/paginated-reports-data-sources/power-bi-paginated-configure-azure-sql.png)

Ниже приведены поддерживаемые типы проверки подлинности для источников данных базы данных SQL Azure:

- Базовый (имя пользователя и пароль)
- Единый вход
- OAuth2 (сохраненный токен AAD)

Для правильной работы единого входа и OAuth2 на сервере базы данных SQL Azure, к которому подключается источник данных, должна быть включена [поддержка проверки подлинности AAD](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure). Для метода проверки подлинности OAuth2 AAD создает токен и сохраняет его для будущего обращения к источнику данных. Чтобы вместо этого использовать [метод проверки подлинности на базе единого входа](https://docs.microsoft.com/power-bi/service-azure-sql-database-with-direct-connect#single-sign-on), выберите расположенный ниже параметр единого входа **Конечные пользователи используют свои учетные данные OAuth2 при доступе к этому источнику данных через DirectQuery**.
  
## <a name="next-steps"></a>Дальнейшие действия

[Просмотр отчета с разбивкой на страницы в службе Power BI](paginated-reports-view-power-bi-service.md)

Появились дополнительные вопросы? [Ответы на них см. в сообществе Power BI.](http://community.powerbi.com/)
