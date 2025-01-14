---
title: Где расположен мой клиент Power BI?
description: Узнайте, где расположен ваш клиент Power BI и как происходит выбор места расположения. Это важно знать, так как место расположения клиента может влиять на качество обмена данными со службой.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 621b15d682cf2992559f76fa9f8f18bfe68ac93b
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074158"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Где расположен мой клиент Power BI?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Узнайте, где расположен ваш клиент Power BI и как происходит выбор места расположения. Это важно знать, так как расположение клиента может влиять на взаимодействие со службой.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Как определить, где расположен ваш клиент Power BI

Чтобы найти регион, в котором расположен ваш клиент, выполните следующие действия.

1. В службе Power BI в верхнем меню выберите справку (**?**) и **О Power BI**.

1. Посмотрите, какой регион указан после текста **Ваши данные сохранены в**. Это регион, в котором расположен ваш клиент. Кроме того, это значение указывает на регион, где хранятся ваши данные, если только вы не используете для своих рабочих областей выделенные емкости в разных регионах.

    ![Область данных](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Как происходит выбор региона

Регион для хранения данных зависит от страны, которая была выбрана при создании клиента. Это относится к регистрации в Office 365 и Power BI, так как эта информация является общей для указанных служб. Если это новый клиент, выберите нужную страну в списке при регистрации.

![Выбор страны](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Power BI выбирает регион, наиболее близкий к выбранному варианту, определяя, где будут храниться данные для вашего клиента.

> [!IMPORTANT]
> Этот выбор нельзя будет изменить после создания клиента.

Появились дополнительные вопросы? [Ответы на них см. в сообществе Power BI.](http://community.powerbi.com/)

