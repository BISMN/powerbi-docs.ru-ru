---
title: Рекомендации по потокам данных Power BI
description: Рекомендации по потокам данных Power BI
author: mohaali
manager: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: c499a83b87eb15031d75974084468f418a17804a
ms.sourcegitcommit: 200291eac5769549ba5c47ef3951e2f3d094426e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2019
ms.locfileid: "71142310"
---
# <a name="dataflows-best-practice"></a>Рекомендации по потокам данных

В этой статье приводятся рекомендации по проектированию потоков данных в Power BI. Это руководство можно использовать чтобы узнать, как создавать потоки данных, применять эти рекомендации к вашим собственным потокам данных.

> [!NOTE]
> Рекомендации этой статьи являются руководствами. Для каждой рекомендации этой статьи могут существовать законные основания отклоняться от этого руководства. 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>Разделение приема и преобразование для использования расширенного вычислительного ядра

При создании потоков данных у вас может возникнуть желание создать единый поток данных со всеми сущностями, преобразованиями, объединениями и улучшениями в одном месте. Для небольших наборов данных может быть эффективен один поток данных. Но при работе с большими объемами данных при выполнении объединений или определенных преобразований иногда могут возникать ограничения памяти или регулирование рабочей нагрузки. Для решения этих проблем было выпущено усовершенствованное ядро для пользователей Power BI Premium, которое масштабируется до гораздо больших объемов данных. Усовершенствованное ядро вычислений работает только со связанными или вычисляемыми сущностями, поэтому создание улучшенного ядра может дать преимущество созданию отдельного потока данных для приема и связанного потока данных для выполнения всех сложных слияний и преобразований.

Разделение потоков данных также полезно для диагностики и отладки проблем обновления, особенно при работе с источниками, имеющими границы регулирования количества запросов.

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>Выполнение действий, которые могут использовать расширенное ядро вычислений

Убедитесь, что вы используете расширенное ядро вычислений, гарантируя, что вы выполняете объединения и фильтруете преобразования сначала в вычисляемой сущности, прежде чем выполнять другие типы преобразований.

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>Разделение потоков данных при подключении к SharePoint

При работе с SharePoint и подключении к нескольким файлам вы можете заметить отдельные сбои. SharePoint регулирует запросы, чтобы обеспечить их надежность и оперативность. Как следствие, при подключении к файлам Excel из SharePoint вы можете быть склонны загружать все файлы в одном потоке данных. Если вы загружаете много файлов, более 20, создайте два или более потоков данных, чтобы разделить нагрузку обновления и обойти регулирование SharePoint.

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>Избегание планирования обновления для связанных сущностей в одной рабочей области

Если вы регулярно блокируетесь от своих потоков данных, которые содержат связанные сущности, это может быть результатом того, что соответствующие зависимые потоки данных внутри одной и той же рабочей области заблокированы во время обновления потока данных. Такая блокировка обеспечивает транзакционную точность и успешное обновление обоих потоков данных, но может блокировать редактирование. 

Если вы настроите отдельное расписание для связанного потока данных, потоки данных могут обновляться без необходимости и блокировать вас от редактирования потока данных. Существуют две рекомендации, позволяющие избежать этой проблемы: 

* избегайте установки расписания обновления для связанного потока данных в той же рабочей области, что и исходный поток данных;
* если вы хотите настроить расписание обновления отдельно и избежать блокировки, выделите поток данных в отдельной рабочей области.

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>Создание отдельной рабочей области для приема данных, преобразования

Чтобы обеспечить доступ к базовым данным потока данных для многих пользователей, не предоставляя доступ к необработанным данным базовой исходной системы, создайте отдельную рабочую область, в которой есть все данные, которыми вы хотите поделиться, и назначьте разрешения. Отдельные разрешения потока данных в настоящее время не поддерживаются.

### <a name="ensure-capacity-is-in-the-same-region"></a>Убедитесь, что емкость находится в том же регионе

В настоящее время потоки данных не поддерживают несколько географических регионов. Емкость Premium должна быть в том же регионе, что и ваш клиент Power BI.

### <a name="separate-on-premises-sources-from-cloud-sources"></a>Отделение локальных источников от облачных

В дополнение к ранее описанным рекомендациям вы можете создать отдельный поток данных для каждого типа источника, например локального, облачного, SQL Server, Spark, Dynamics и др. Настоятельно рекомендуется разделить ваш поток данных по типу источника данных. Такое разделение по типу источника облегчает быстрое устранение неполадок и позволяет избежать внутренних ограничений при обновлении ваших потоков данных.

### <a name="separate-dataflows-into-a-separate-capacity"></a>Отделение потоков данных в отдельную емкость

Если вы столкнулись с ограничениями регулирования или видите регулярные сбои для потоков данных из-за ограничений памяти на вашей емкости, рассмотрите возможность разделения потоков данных или увеличения емкости Premium для дополнительной памяти.

## <a name="next-steps"></a>Дальнейшие действия

В этой статье предоставлена информация о рекомендациях для потоков данных. Дополнительные сведения о потоках данных вы можете получить в следующих статьях.

* [Self-service data prep in Power BI (Preview)](service-dataflows-overview.md) (Самостоятельная подготовка данных в Power BI (предварительная версия))
* [Creating and using dataflows in Power BI (Preview)](service-dataflows-create-use.md) (Создание и использование потоков данных в Power BI (предварительная версия))
* [Использование вычисляемых сущностей в Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Использование потоков данных с локальными источниками данных](service-dataflows-on-premises-gateways.md)

Руководства и информационные материалы о разработке CDM:
* [Что такое модель общих данных?](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Папки CDM](https://go.microsoft.com/fwlink/?linkid=2045304)
* [The metadata file (model.json) for the Common Data Model](https://go.microsoft.com/fwlink/?linkid=2045521) (Файл метаданных (model.json) для модели общих данных)


Дополнительные сведения о Power Query и обновлении по расписанию содержатся в следующих статьях:
* [Общие сведения о запросах в Power BI Desktop](desktop-query-overview.md)
* [Настройка запланированного обновления](refresh-scheduled-refresh.md)
