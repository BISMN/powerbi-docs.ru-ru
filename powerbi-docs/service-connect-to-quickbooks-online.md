---
title: Подключение к QuickBooks Online с помощью Power BI
description: QuickBooks Online для Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: ec13f396ea1a322a79263320a169330f24a2e5f0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61151276"
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>Подключение к QuickBooks Online с помощью Power BI
При подключении к данным QuickBooks Online из Power BI вы немедленно получаете панель мониторинга и отчеты Power BI, предоставляющие информацию о денежном потоке, прибыльности, клиентах и многом другом. Используйте стандартные панели мониторинга и отчеты или настройте их так, чтобы выделить информацию, которая наиболее важна для вас. Данные автоматически обновляются раз в день.

Подключите [пакет содержимого QuickBooks Online](https://dxt.powerbi.com/getdata/services/quickbooks-online) для Power BI.

>[!NOTE]
>Для импорта данных QuickBooks Online в Power BI необходимо быть администратором учетной записи QuickBooks Online и выполнить вход с использованием учетных данных администратора. Этот соединитель нельзя использовать с программным обеспечением QuickBooks Desktop. 

## <a name="how-to-connect"></a>Способы подключения
1. Нажмите кнопку **Получить данные** в нижней части левой панели навигации.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getdata.png) 
2. В поле **Службы** выберите **Получить**.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getservices.png) 
3. Выберите **QuickBooks Online**, а затем **Получить**.
   
   ![](media/service-connect-to-quickbooks-online/qbo.png)
4. В качестве метода аутентификации выберите **oAuth2** и щелкните **Войти**. 
5. При появлении запроса введите учетные данные QuickBooks Online и пройдите проверку подлинности QuickBooks Online. Если вы уже выполнил вход в QuickBooks Online в браузере, учетные данные могут не запрашиваться.
   >[!NOTE]
   >Вам необходимы учетные данные администратора для учетной записи QuickBooks Online.
6. Выберите компанию, которые требуется подключить к Power BI, на следующем экране.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)
7. Выберите **Авторизовать** на следующем экране, чтобы начать импорт. Это может занять несколько минут в зависимости от размера данных компании. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
   После импорта данных в Power BI в области навигации слева появятся новая панель мониторинга, отчет и набор данных. Новые элементы отмечены желтой звездочкой \*.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_leftnavnew.png)
8. Выберите панель мониторинга QuickBooks Online. Служба Power BI создает ее автоматически для отображения импортированных данных. Вы можете изменить эту панель мониторинга для отображения данных любым нужным образом. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_dash.png)

**Дальнейшие действия**

* Попробуйте [задать вопрос в поле "Вопросы и ответы"](consumer/end-user-q-and-a.md) в верхней части информационной панели.
* [Измените плитки](service-dashboard-edit-tile.md) на информационной панели.
* [Выберите плитку](consumer/end-user-tiles.md), чтобы открыть соответствующий отчет.
* Хотя набор данных будет обновляться ежедневно по расписанию, вы можете изменить график обновлений или попытаться выполнять обновления по запросу с помощью кнопки **Обновить сейчас**

## <a name="troubleshooting"></a>Устранение неполадок
**"! Произошла ошибка".**

Если это сообщение отображается после того, как вы выбрали команду **Авторизовать**:

"Ой. Произошла ошибка". Закройте это окно и повторите попытку.

Другой пользователь уже подписался на это приложение для этой компании. Обратитесь по адресу [электронный адрес администратора] для изменения этой подписки".

![](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

... это означает, что другой администратор в вашей компании уже подключился к данным компании с помощью Power BI. Попросите этого администратору предоставить вам доступ к панели мониторинга. В настоящее время только один администратор может подключить набор данных QuickBooks Online определенной компании к Power BI. Когда Power BI создаст панель мониторинга, администратор может предоставить к ней общий доступ для нескольких сотрудников в тех же клиентах Power BI.

**"Это приложение не разрешает подключения из вашей страны".**

В настоящее время Power BI поддерживает только выпуски QuickBooks Online для США. 

![](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>Дальнейшие действия
[Что такое Power BI?](power-bi-overview.md)

[Power BI — основные понятия](consumer/end-user-basic-concepts.md)

