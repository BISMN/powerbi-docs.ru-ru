---
title: Что такое Сервер отчетов Power BI?
description: Общие сведения о Сервере отчетов Power BI и его взаимодействии со службой SQL Server Reporting Services (SSRS) и остальными компонентами Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 05/22/2019
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: 59913e5d17d15dad8729cd5c96582d09f708c30a
ms.sourcegitcommit: 1789815c87e306b1427a5838655d30d3b9ba1d29
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67791834"
---
# <a name="what-is-power-bi-report-server"></a>Что такое Сервер отчетов Power BI?

Сервер отчетов Power BI — это локальный сервер отчетов с веб-порталом, на котором можно просматривать отчеты и ключевые показатели эффективности и управлять ими. Он включает инструменты, позволяющие создавать отчеты Power BI, отчеты с разбивкой на страницы, мобильные отчеты и ключевые показатели эффективности. У пользователей есть несколько вариантов доступа к этим отчетам: просмотр в веб-браузере, просмотр на мобильном устройстве, получение в виде сообщения электронной почты.

![Веб-портал сервера отчетов Power BI](media/get-started/power-bi-report-server-overview.png)

## <a name="comparing-power-bi-report-server"></a>Сравнительный анализ Сервера отчетов Power BI 
Функции Сервера отчетов Power BI похожи на функции SQL Server Reporting Services и веб-службы Power BI. Как и служба Power BI, Сервер отчетов Power BI позволяет размещать отчеты Power BI (PBIX), файлы Excel и отчеты с разбиением на страницы (RDL). Как и служба Reporting Services, Сервер отчетов Power BI размещается локально. Функции Сервера отчетов Power BI являются надмножеством служб Reporting Services. Это означает, что вы можете выполнять в нем любые функции Reporting Services, а также работать с отчетами Power BI. См. дополнительные сведения о [сравнении Сервера отчетов Power BI и службы Power BI](compare-report-server-service.md).

## <a name="licensing-power-bi-report-server"></a>Лицензирование Сервера отчетов Power BI
Сервер отчетов Power BI можно использовать с двумя разными лицензиями: [Power BI Premium](../service-premium-what-is.md) или [SQL Server Enterprise Edition](https://www.microsoft.com/sql-server/sql-server-2017-editions) по программе Software Assurance. Лицензия Power BI Premium позволяет создавать гибридные развертывания, сочетающие облачные и локальные технологии.  

> [!NOTE]
> Для Power BI Premium Сервер отчетов Power BI доступен только в SKU серии P. Он не входит в SKU серии EM.

## <a name="web-portal"></a>Веб-портал
Основной точкой взаимодействия с Сервером отчетов Power BI является защищенный веб-портал, который можно просматривать в любом современном браузере. Здесь вам доступны все отчеты и ключевые показатели эффективности. Содержимое веб-портала организовано в традиционную иерархию папок. В папках содержимое группируются по типу: отчеты Power BI, мобильные отчеты, отчеты с разбивкой на страницы, ключевые показатели эффективности и книги Excel. Общие наборы данных и общие источники данных находятся в собственных папках и используются в качестве стандартных блоков для отчетов. Вы можете отмечать избранные элементы, чтобы просматривать их в отдельной папке. Можно также создавать ключевые показатели эффективности прямо на веб-портале. 

![Веб-портал сервера отчетов Power BI](media/get-started/web-portal.png)

Вы можете управлять содержимым веб-портала в зависимости от предоставленных вам разрешений. Вы можете планировать обработку отчетов, открывать отчет по требованию и (или) подписываться на регулярно публикуемые отчеты. Также вы можете применять к веб-порталу оформление с [фирменной символикой](https://docs.microsoft.com/sql/reporting-services/branding-the-web-portal). 

См. дополнительные сведения о [веб-портале (основной режим служб SSRS)](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode).

## <a name="power-bi-reports"></a>Отчеты Power BI
Версия Power BI Desktop, оптимизированная для сервера отчетов, позволяет создавать отчеты Power BI (.PBIX). Вы можете опубликовать и просматривать их на веб-портале в созданной вами среде.

![Отчеты Power BI на Сервере отчетов Power BI](media/get-started/powerbi-reports.png)

Отчет Power BI — это разностороннее представление модели данных на основе визуализаций, которые отображают разные результаты и сведения о выбранной модели данных.  В отчете может быть одна визуализация или несколько страниц, заполненных визуализациями. В зависимости от назначенной вам роли, вы можете читать и изучать отчеты или создавать новые отчеты для других пользователей.

Изучите [процесс установки Microsoft Power BI Desktop](install-powerbi-desktop.md).

## <a name="paginated-reports"></a>Отчеты с разбивкой на страницы
Отчеты с разбивкой на страницы (.RDL) — это отчеты в формате документа с визуализациями, позволяющие расширять таблицы горизонтально и (или) вертикально на несколько страниц, чтобы поместить все необходимые данные. Они отлично подходят для создания документов с фиксированным макетом и разрешением, оптимизированных для печати, например файлов в формате PDF и Word. 

![Отчеты с разбивкой на страницы на Сервере отчетов Power BI](media/get-started/paginated-reports.png)

Для создания этих отчетов с разбиением на страницы используется [построитель отчетов](https://docs.microsoft.com/sql/reporting-services/report-builder/report-builder-in-sql-server-2016) или конструктор отчетов в [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt).

## <a name="reporting-services-mobile-reports"></a>Мобильные отчеты Reporting Services
Мобильные отчеты подключаются к локальным источникам данных и имеют удобный макет, который адаптируется к разным типам, форматам и ориентациям устройств. Для создания таких отчетов применяется издатель мобильных отчетов для SQL Server.

См. дополнительные сведения о [мобильных отчетах Reporting Services](https://docs.microsoft.com/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher). 

## <a name="report-server-programming-features"></a>Функции программирования сервера отчетов
Воспользуйтесь преимуществами функций программирования сервера отчетов Power BI, чтобы расширять и настраивать отчеты с помощью API-интерфейсов для интеграции или расширения данных и обработки отчетов в пользовательских приложениях.

См. дополнительные сведения в [документации разработчика сервера отчетов](https://docs.microsoft.com/sql/reporting-services/reporting-services-developer-documentation).

## <a name="next-steps"></a>Дальнейшие действия
[Установка сервера отчетов Power BI](install-report-server.md)  
[Загрузка построителя отчетов](https://www.microsoft.com/download/details.aspx?id=53613)  

Появились дополнительные вопросы? [Попробуйте задать вопрос в сообществе Power BI.](https://community.powerbi.com/)


