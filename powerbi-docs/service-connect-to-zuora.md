---
title: Подключение к Zuora с помощью Power BI
description: Zuora для Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 605cd2f135ff6d8626586abbd503bcb44687931d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61156988"
---
# <a name="connect-to-zuora-with-power-bi"></a>Подключение к Zuora с помощью Power BI
Zuora для Power BI позволяет визуализировать важные данные о доходах, выставлении счетов и подписках. Используйте панель мониторинга и отчеты по умолчанию для анализа тенденций использования, отслеживания отчетов и выплат, а также мониторинга постоянных доходов или их настройки в соответствии с уникальными требованиями к панели мониторинга и отчетам.

Подключитесь к [Zuora](https://app.powerbi.com/getdata/services/Zuora) для Power BI.

## <a name="how-to-connect"></a>Способы подключения
1. Нажмите кнопку **Получить данные** в нижней части левой панели навигации.

   ![](media/service-connect-to-zuora/getdata.png)
2. В поле **Службы** выберите **Получить**.

   ![](media/service-connect-to-zuora/services.png)
3. Выберите **Zuora** \> **Подключить**.

   ![](media/service-connect-to-zuora/zuora.png)
4. Укажите URL-адрес Zuora. Обычно это <https://www.zuora.com>. См. раздел [Поиск параметров](#FindingParams) ниже.

   ![](media/service-connect-to-zuora/params.png)
5. В качестве значения параметра **Проверка подлинности**выберите **Обычная** , укажите имя пользователя и пароль (регистр учитывается), а затем щелкните **Вход**.

    ![](media/service-connect-to-zuora/creds.png)
6. После утверждения процесс импорта начнется автоматически. После завершения в области навигации появятся новая панель мониторинга, отчет и модель. Выберите панель мониторинга, чтобы просмотреть импортированные данные.

     ![](media/service-connect-to-zuora/dashboard.png)

**Дальнейшие действия**

* Попробуйте [задать вопрос в поле "Вопросы и ответы"](consumer/end-user-q-and-a.md) в верхней части информационной панели.
* [Измените плитки](service-dashboard-edit-tile.md) на информационной панели.
* [Выберите плитку](consumer/end-user-tiles.md), чтобы открыть соответствующий отчет.
* Хотя набор данных будет обновляться ежедневно по расписанию, вы можете изменить график обновлений или попытаться выполнять обновления по запросу с помощью кнопки **Обновить сейчас**

## <a name="whats-included"></a>Содержимое
Пакет содержимого использует интерфейс API Zuora AQUA для извлечения следующих таблиц.

| Таблицы |  |  |
| --- | --- | --- |
| Account |InvoiceItemAdjustment |Refund |
| AccountingCode |Payment |RevenueSchedule |
| AccountingPeriod |PaymentMethod |RevenueScheduleItem |
| BillTo |Product |Subscription |
| DateDim |ProductRatePlan |TaxationItem |
| Invoice |ProductRatePlanCharge |Usage |
| InvoiceAdjustment |RatePlan | |
| InvoiceItem |RatePlanCharge | |

Он также включает в себя такие вычисляемые меры:

| Мера | Описание | Pseudo-Calculation |
| --- | --- | --- |
| Account: Payments |Общие суммы платежей за период времени, основанные на фактических датах платежей. |SUM (Payment.Amount) <br>WHERE<br>Payment.EffectiveDate =< TimePeriod.EndDate<br>AND    Payment.EffectiveDate >= TimePeriod.StartDate |
| Account: Возмещения |Общие суммы возмещений за период времени, основанные на датах возмещений. Сумма указывается как отрицательное число. |-1*SUM(Refund.Amount)<br>WHERE<br>Refund.RefundDate =< TimePeriod.EndDate<br>AND    Refund.RefundDate >= TimePeriod.StartDate |
| Account: Net Payments |Платежи учетной записи плюс возмещения учетной записи за период времени. |Account.Payments + Account.Refunds |
| Account: Active Accounts |Количество учетных записей, которые были активными за период времени. Подписки должны начаться до или непосредственно в дату начала периода времени. |COUNT (Account.AccountNumber)<br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    (Subscription.SubscriptionEndDate > TimePeriod.StartDate<br>OR<br>Subscription.SubscriptionEndDate = null) –evergreen subscription |
| Account: Average Recurring Revenue |Валовый MRR на активную учетную запись за период времени. |Gross MRR / Account.ActiveAccounts |
| Account: Cancelled Subscriptions |Число учетных записей, которые отменили подписку за период времени. |COUNT (Account.AccountNumber)<br>WHERE<br>Subscription.Status = "Cancelled"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    Subscription.CancelledDate >= TimePeriod.StartDate |
| Account: Payment Errors |Общее значение ошибок платежей. |SUM (Payment.Amount)<br>WHERE<br>Payment.Status = "Error" |
| Revenue Schedule Item: Recognized Revenue |Общий признанный доход за отчетный период. |SUM (RevenueScheduleItem.Amount)<br>WHERE<br>AccountingPeriod.StartDate = TimePeriod.StartDate |
| Подписка: New Subscriptions |Число новых подписок за период времени. |COUNT (Subscription.ID)<br>WHERE<br>Subscription.Version = "1"<br>AND    Subscription.CreatedDate <= TimePeriod.EndDate<br>AND    Subscription.CreatedDate >= TimePeriod.StartDate |
| Invoice: Позиции счетов |Общие суммы по позициям выставленных счетов за период времени. |SUM (InvoiceItem.ChargeAmount)<br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Invoice: Позиции налогов |Общие суммы налогов по позициям налогообложения за период времени. |SUM (TaxationItem.TaxAmount)<br>WHERE<br>Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Invoice: Корректировка позиций счетов |Общие суммы корректировки по позициям счетов за период времени. |SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceItemAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceItemAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Invoice: Корректировка счетов |Общие суммы корректировки счетов за период времени. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Invoice: Чистая сумма оплаты |Сумма позиций счетов, позиций налогообложения, корректировок по позициям счетов и корректировок счетов за период времени. |Invoice.InvoiceItems + Invoice.TaxationItems + Invoice.InvoiceItemAdjustments + Invoice.InvoiceAdjustments |
| Invoice: Invoice Aging Balance |Сумма балансов по учтенным счетам. |SUM (Invoice.Balance) <br>WHERE<br>    Invoice.Status = "Posted" |
| Invoice: Gross Billings |Сумма значений по позициям выставленных счетов для учтенных счетов за период времени. |SUM (InvoiceItem.ChargeAmount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Invoice: Total Adjustments |Сумма обработанных корректировок счетов и корректировок по позициям счетов, связанных с учтенными счетами. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.Status = "Processed"<br>+<br>SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    invoiceItemAdjustment.Status = "Processed" |
| Rate Plan Charge: Gross MRR |Сумма ежемесячных постоянных доходов от подписок за период времени. |SUM (RatePlanCharge.MRR) <br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    RatePlanCharge.EffectiveStartDate <= TimePeriod.StartDate<br>AND        RatePlanCharge.EffectiveEndDate > TimePeriod.StartDate<br>    OR    RatePlanCharge.EffectiveEndDate = null --evergreen subscription |

## <a name="system-requirements"></a>Требования к системе
Требуется доступ к API Zuora.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Поиск параметров
Укажите URL-адрес, который вы обычно используете для доступа к данным Zuora. Допустимые значения:  

* https://www.zuora.com  
* URL-адрес, соответствующий вашему экземпляру службы  

## <a name="troubleshooting"></a>Устранение неполадок
Пакет содержимого Zuora извлекает множество аспектов учетной записи Zuora. Если вы не используете определенные функции, соответствующие плитки или отчеты будут пустыми. Если у вас возникли проблемы при загрузке, обратитесь в службу поддержки Power BI.

## <a name="next-steps"></a>Дальнейшие действия
[Приступая к работе с Power BI](service-get-started.md)

[Получение данных в Power BI](service-get-data.md)
