---
title: Подключение к comScore Digital Analytix с помощью Power BI
description: comScore Digital Analytix для Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: aab2d62265300787f99116aade7ec16aaf1b0f86
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185591"
---
# <a name="connect-to-comscore-digital-analytix-with-power-bi"></a>Подключение к comScore Digital Analytix с помощью Power BI
Визуальное представление и исследование данных comScore Digital Analytix в Power BI с помощью пакета содержимого для Power BI. Данные автоматически обновляются раз в день.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Подключитесь к [пакету содержимого comScore для Power BI.](https://app.powerbi.com/getdata/services/comscore)

>[!NOTE]
>Для подключения к пакету содержимого требуется учетная запись пользователя comScore DAx и доступ к comScore API. Дополнительные [сведения](#Requirements) см. ниже.

## <a name="how-to-connect"></a>Способы подключения
1. Выберите "Получить данные" в нижней части левой панели навигации.
   
   ![](media/service-connect-to-connect-to/getdata.png)
2. В поле **Службы** выберите **Получить**.
   
   ![](media/service-connect-to-connect-to/services.png)
3. Выберите **comScore Digital Analytix** \> **Получить**.
   
   ![](media/service-connect-to-connect-to/comscore.png)
4. Укажите центр обработки данных, идентификатор клиента comScore и сайт, к которому вы хотите подключиться. Дополнительные сведения о том, как найти эти значения, см. в разделе [Как найти параметры comScore](#FindingParams) ниже.
   
   ![](media/service-connect-to-connect-to/parameters.png)
5. Укажите имя пользователя comScore и пароль для подключения. Дополнительные сведения о том, как найти это значение, см. ниже.
   
   ![](media/service-connect-to-connect-to/creds.png)
6. Процесс импорта начнется автоматически. После завершения в области навигации появятся новая панель мониторинга, отчет и модель. Выберите панель мониторинга, чтобы просмотреть импортированные данные.

**Дальнейшие действия**

* Попробуйте [задать вопрос в поле "Вопросы и ответы"](consumer/end-user-q-and-a.md) в верхней части информационной панели.
* [Измените плитки](service-dashboard-edit-tile.md) на информационной панели.
* [Выберите плитку](consumer/end-user-tiles.md), чтобы открыть соответствующий отчет.
* Хотя набор данных будет обновляться ежедневно по расписанию, вы можете изменить график обновлений или попытаться выполнять обновления по запросу с помощью кнопки **Обновить сейчас**

<a name="Requirements"></a>

## <a name="system-requirements"></a>Требования к системе
Для подключения требуется учетная запись пользователя comScore DAx и доступ к API comScore DAx. Обратитесь к администратору comScore DAx для подтверждения вашей учетной записи.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Поиск параметров
Сведения о том, как найти все параметры comScore, приведены ниже.

**Центр обработки данных**

Центр обработки данных, к которому вы подключаетесь, определяется по URL-адресу, по которому вы переходите в comScore.

![](media/service-connect-to-connect-to/comscore_url.png) 

**Клиент**

В качестве клиента необходимо указать то же имя, которое вы указываете при входе в comScore DAx.

![](media/service-connect-to-connect-to/comscore_signin.png) 

**Сайт**

Сайт comScore определяет сайт, из которого вы будете просматривать данные. Список сайтов можно найти в вашей учетной записи comScore.

![](media/service-connect-to-connect-to/comscore_sites.png)

## <a name="next-steps"></a>Дальнейшие действия
[Приступая к работе с Power BI](service-get-started.md)

[Получение данных в Power BI](service-get-data.md)

