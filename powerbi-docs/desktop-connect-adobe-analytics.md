---
title: "Подключение к Adobe Analytics в Power BI Desktop (предварительная версия)"
description: "Простое и удобное использование Adobe Analytics в Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/09/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: efd6d066e2f98f86248730917c2f4aa0c8a39983
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="connect-to-adobe-analytics-in-power-bi-desktop-preview"></a>Подключение к Adobe Analytics в Power BI Desktop (предварительная версия)
В **Power BI Desktop** вы можете подключиться к **Adobe Analytics** и использовать его так же, как и любой другой источник данных в Power BI Desktop. 

![Получение данных из Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

## <a name="enable-the-adobe-analytics-connector-preview"></a>Включение предварительной версии соединителя Adobe Analytics 
Так как соединитель **Adobe Analytics** находится на этапе предварительной версии, вам нужно включить эту предварительную версию функции, чтобы соединитель был доступен в окне **Получение данных**. Чтобы включить эту предварительную версию соединителя, выберите **Файл > Параметры и настройки > Параметры > Предварительная версия функций** в Power BI Desktop и установите флажок рядом с пунктом **Закладки**. 

![Включение предварительной версии соединителя Adobe Analytics в разделе "Параметры"](media/desktop-connect-adobe-analytics/connect-adobe-analytics_02.png)

После включения предварительной версии соединителя Adobe Analytics нужно перезапустить приложение **Power BI Desktop**.

## <a name="connect-to-adobe-analytics-data"></a>Подключение к данным Adobe Analytics
Для подключения к данным **Adobe Analytics** на вкладке **Главная** на ленте в Power BI Desktop выберите **Получение данных**. Выберите слева категорию **Веб-службы**. В списке справа вы увидите **Соединитель Adobe Analytics**.

![Получение данных из Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

В появившемся окне **Adobe Analytics** нажмите кнопку **Войти** и введите учетные данные для входа в свою учетную запись Adobe Analytics. Появляется окно входа Adobe, как показано на рисунке ниже.

![Вход в Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_03.png)

При появлении запроса укажите имя пользователя и пароль. После установки соединения вы можете просмотреть и выбрать несколько измерений и мер в диалоговом окне **Навигатор** Power BI для создания единичного табличного вывода. Можно также указать все необходимые входные параметры для выбранных компонентов. 

![Выбор данных с помощью навигатора](media/desktop-connect-adobe-analytics/connect-adobe-analytics_04.png)

Вы можете **загрузить** выбранную таблицу, после чего таблица будет целиком перемещена в **Power BI Desktop**. Или же можно **изменить** запрос — в таком случае откроется **редактор запросов**, с помощью которого можно отфильтровать и уточнить набор нужных вам данных, а затем загрузить уточненный набор данных в **Power BI Desktop**.

![Загрузка или изменение данных в навигаторе](media/desktop-connect-adobe-analytics/connect-adobe-analytics_05.png)


## <a name="next-steps"></a>Дальнейшие действия
В Power BI Desktop можно подключаться к данным самых разных видов. Дополнительные сведения об источниках данных см. в перечисленных ниже статьях.

* [Начало работы с Power BI Desktop](desktop-getting-started.md)
* [Источники данных в Power BI Desktop](desktop-data-sources.md)
* [Формирование и объединение данных в Power BI Desktop](desktop-shape-and-combine-data.md)
* [Подключение к данным Excel в Power BI Desktop](desktop-connect-excel.md)   
* [Ввод данных непосредственно в Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
