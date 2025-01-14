---
title: Общие сведения о взаимодействии визуальных элементов в отчете
description: Документация для пользователей Power BI с описанием механизма взаимодействия визуальных элементов на странице отчета.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: b95df5c32d9058e4480d7af5e226a971ba581144
ms.sourcegitcommit: 02042995df12cc4e4b97eb8a369e62364eb5af36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256296"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Перекрестная фильтрация визуальных элементов в отчете Power BI
Одно из главных преимуществ Power BI заключается во взаимосвязи всех визуальных элементов на странице отчета. Когда вы выбираете точку данных на любом из визуальных элементов, с учетом этого изменяется содержимое всех остальных визуальных элементов на странице. 

![Видео о взаимодействии визуальных элементов](media/end-user-interactions/interactions.gif)

По умолчанию выбор точки данных в одной визуализации на странице отчета позволяет осуществлять перекрестную фильтрацию, перекрестное выделение и детализацию других визуализаций на странице. 

Это может быть удобно для того, чтобы определить, как одно значение в данных влияет на другое. Например, при выборе сегмента модерации на кольцевой диаграмме выделяется вклад из этого сегмента в каждый столбец на диаграмме общего количества единиц по месяцам, а также фильтруется график справа.

![изображение с взаимодействием визуальных элементов](media/end-user-interactions/power-bi-interactions.png)

См. раздел [Сведения о фильтрации и выделении](../power-bi-reports-filters-and-highlighting.md). 

Конкретные правила взаимодействия визуальных элементов на странице определяются *конструктором* отчета. Конструкторы могут включать и выключать средства взаимодействия, а также изменять настроенные по умолчанию поведения перекрестной фильтрации, перекрестного выделения и детализации. 
  
> [!NOTE]
> Термины *кроссфильтрация* и *перекрестное выделение* используются для отделения поведения, описанного здесь, от того, что происходит при использовании области **Фильтры** для фильтрации и выделения визуализаций.  

## <a name="considerations-and-troubleshooting"></a>Рекомендации и устранение неполадок
- Если отчет содержит визуализацию, которая поддерживает [детализацию](../power-bi-visualization-drill-down.md), детализация одной визуализации по умолчанию не оказывает влияния на другие визуализации на странице отчета.     
- Если вы используете визуальный элемент visualA для взаимодействия с визуальным элементом visualB, фильтры уровня визуальных элементов из visualA будут применены к visualB.

## <a name="next-steps"></a>Дальнейшие действия
[Использование фильтров отчетов](../power-bi-how-to-report-filter.md)
