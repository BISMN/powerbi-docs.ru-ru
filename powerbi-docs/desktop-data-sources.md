---
title: Источники данных в Power BI Desktop
description: Источники данных в Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f045e9076cdd8552d6e35e72b9c5f6e2319add68
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65853459"
---
# <a name="data-sources-in-power-bi-desktop"></a>Источники данных в Power BI Desktop
Power BI Desktop позволяет подключаться к данным из многих разных источников. Полный список доступных источников данных представлен в нижней части этой страницы.

Для подключения к данным выберите **Получить данные** на ленте **Главная** . Если щелкнуть стрелку вниз или текст **Получить данные** на кнопке, откроется меню **Наиболее распространенные** с типами данных, как показано на следующем рисунке:

![Получение данных в Power BI Desktop](media/desktop-data-sources/data-sources_01.png)

Если щелкнуть **Еще...** в меню **Наиболее распространенные**, отобразится окно **Получить данные**. Чтобы открыть окно **Получить данные** (в обход меню **Наиболее распространенные** ), можно сразу щелкнуть **кнопку со значком** **Получить данные** .

![Кнопка "Получить данные"](media/desktop-data-sources/data-sources_02.png)

> [!NOTE]
> Команда разработчиков Power BI постоянно расширяет список источников данных, доступных для приложения **Power BI Desktop** и **службы Power BI**. Поэтому вы часто будете видеть ранние версии источников данных в процессе разработки с пометкой *Бета-версия* или *Предварительная версия*. Все источники данных с пометкой *Бета-версия* или *Предварительная версия* имеют ограниченную поддержку и функциональные возможности и не должны использоваться в рабочих средах.

## <a name="data-sources"></a>Источники данных
Типы данных разделены на следующие категории:

* Все
* Файл
* База данных
* Power BI
* Azure
* Интернет-службы
* Другие

Категория **Все** включает все типы подключений данных из всех категорий.

Категория **Файл** предоставляет следующие подключения к данным:

* Excel
* Text/CSV.
* XML
* JSON
* Папка
* PDF
* Папка SharePoint

На следующем рисунке показано окно **Получить данные** для категории **Файл**.

![Получение данных > Файл](media/desktop-data-sources/data-sources_03.png)

Категория **База данных** предоставляет следующие подключения к данным:

* База данных SQL Server
* База данных Access
* База данных SQL Server Analysis Services
* База данных Oracle
* База данных IBM DB2
* База данных IBM Informix (бета-версия)
* IBM Netezza
* База данных MySQL
* База данных PostgreSQL
* База данных Sybase
* База данных Teradata
* База данных SAP HANA
* Сервер приложений SAP Business Warehouse
* Сервер сообщений SAP Business Warehouse
* Amazon Redshift
* Impala
* Google BigQuery
* Vertica
* Снежинка
* Essbase
* Кубы AtScale (бета-версия)
* Соединитель BI
* Dremio
* Exasol
* Indexima (бета-версия)
* InterSystems IRIS (бета-версия)
* Jethro (бета-версия)
* Kyligence Enterprise (бета-версия)
* MarkLogic (бета-версия)

> [!NOTE]
> Некоторые соединители базы данных необходимо включить: выберите **Файл > Параметры и настройки > Параметры**, затем щелкните **Предварительная версия функций** и включите соединитель. Если некоторые из указанных выше соединителей не отображаются, а вы хотите их использовать, проверьте настройки параметра **Предварительная версия функций**. Также обратите внимание, что все источники данных с пометкой *Бета-версия* или *Предварительная версия* имеют ограниченную поддержку и функциональные возможности и не должны использоваться в рабочих средах.

На следующем рисунке показано окно **Получить данные** для категории **База данных**.

![Получение данных > Базы данных](media/desktop-data-sources/data-sources_04.png)

Категория **Power BI** предоставляет следующие подключения к данным:

* Наборы данных Power BI
* Потоки данных Power BI

На следующем рисунке показано окно **Получение данных** для **Power BI**.

![Получение данных > Power BI](media/desktop-data-sources/data-sources_05.png)

Категория **Azure** предоставляет следующие подключения к данным:

* База данных SQL Azure
* Хранилище данных SQL Azure
* База данных Azure Analysis Services
* Хранилище BLOB-объектов Azure
* Хранилище таблиц Azure
* Azure Cosmos DB (бета-версия)
* Поколение 1 хранилища Озера данных Azure
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight Interactive Query
* Обозреватель данных Azure (Kusto)
* Управление затратами Azure (бета-версия)

На следующем рисунке показано окно **Получить данные** для категории **Azure**.

![Получение данных > Azure](media/desktop-data-sources/data-sources_06.png)

Категория **Интернет-службы** предоставляет следующие подключения к данным:

* Список SharePoint Online
* Microsoft Exchange Online
* Dynamics 365 (в сети)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (локальный)
* Common Data Service для приложений (бета-версия)
* Microsoft Azure Consumption Insights (бета-версия)
* Azure DevOps (бета-версия)
* Azure DevOps Server (бета-версия)
* Объекты SalesForce
* Отчеты SalesForce
* Google Analytics
* Adobe Analytics
* appFigures (бета-версия)
* Data.World — получение набора данных (бета-версия)
* Facebook
* GitHub (бета-версия)
* MailChimp (бета-версия)
* Merketo (бета-версия)
* Mixpanel (бета-версия)
* Planview Enterprise One — PRM (бета-версия)
* Planview Projectplace (бета-версия)
* QuickBooks Online (бета-версия)
* Smartsheet (бета-версия)
* SparkPost (бета-версия)
* Stripe (бета-версия)
* SweetIQ (бета-версия)
* Planview Enterprise One — CMT (бета-версия)
* Twilio (бета-версия)
* tyGraph (бета-версия)
* Webtrends (бета-версия)
* ZenDesk (бета-версия)
* Источник данных Emigo (бета-версия)
* IndustrialAppStore (бета-версия)
* Microsoft Graph Security (бета-версия)
* TeamDesk (бета-версия)

На следующем рисунке показано окно **Получение данных** для категории **Интернет-службы**.

![Получить данные > Веб-службы](media/desktop-data-sources/data-sources_07.png)

Категория **Другие** предоставляет следующие подключения к данным:

* Веб-приложение
* Список SharePoint
* Веб-канал OData
* Active Directory
* Microsoft Exchange
* Файл Hadoop (HDFS)
* Spark
* Сценарий R
* Скрипт Python
* ODBC
* OLE DB
* BI360 - бюджетирования & финансовой отчетности (бета-версия)
* Denado
* Сведения о сетке (бета-версия)
* Paxata 
* QubolePresto (бета-версия)
* Quick Base (бета-версия)
* Roamler (бета-версия)
* SurveyMonkey (бета-версия)
* Tenforce (бета-версия)
* Workforce Dimensions (бета-версия)
* Пустой запрос

На следующем рисунке показано окно **Получение данных** для категории **Другие**.

![Получение данных > Другое](media/desktop-data-sources/data-sources_08.png)

> [!NOTE]
> Подключение к пользовательским источникам данных, полученным с помощью Azure Active Directory, сейчас не работает.

## <a name="connecting-to-a-data-source"></a>Подключение к источнику данных
Чтобы подключиться к источнику данных, выберите его в окне **Получение данных** и нажмите кнопку **Подключить**. На следующем рисунке выбран источник **Интернет** из категории подключения к данным **Другие** .

![Подключение к Интернету](media/desktop-data-sources/data-sources_08.png)

Отображается окно подключения, зависящее от типа подключения к данным. Если необходимы учетные данные, вам будет предложено ввести их. На следующем рисунке показан ввод URL-адреса для подключения к интернет-источнику данных.

![Ввод URL-адреса](media/desktop-data-sources/datasources_fromwebbox.png)

После ввода URL-адреса или сведений о подключении ресурса нажмите кнопку **ОК**. Power BI Desktop устанавливает подключение к источнику данных и представляет доступные источники данных в области **Навигатор**.

![Экран "Навигатор"](media/desktop-data-sources/datasources_fromnavigatordialog.png)

Для загрузки данных можно нажать кнопку **Загрузить** внизу области **Навигатор** или редактировать запрос перед загрузкой данных, нажав кнопку **Изменить** .

Это вся информация о подключении к источникам данных в Power BI Desktop. Попробуйте подключиться к данным из нашего растущего списка источников данных и следите за новостями — список постоянно пополняется.

## <a name="next-steps"></a>Дальнейшие действия
Power BI Desktop предоставляет широкие возможности. Дополнительные сведения об этих возможностях см. в следующих ресурсах.

* [Что такое Power BI Desktop?](desktop-what-is-desktop.md)
* [Общие сведения о запросах в Power BI Desktop](desktop-query-overview.md)
* [Типы данных в Power BI Desktop](desktop-data-types.md)
* [Формирование и объединение данных в Power BI Desktop](desktop-shape-and-combine-data.md)
* [Общие задачи с запросами в Power BI Desktop](desktop-common-query-tasks.md)    
