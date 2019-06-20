---
title: Линии диаграммы в Power BI
description: Линии диаграммы в Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0654dccf55b1e13f26d8ecaabee0349f0e56afc6
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65535797"
---
# <a name="line-charts-in-power-bi"></a>Линии диаграммы в Power BI
График представляет собой ряд точек данных, которые представляются точками и соединенных прямых линий. График может иметь один или несколько строк. Линейные диаграммы имеют X и оси Y. 

![простую линейную диаграмму](media/power-bi-line-charts/power-bi-line.png)

## <a name="create-a-line-chart"></a>Создайте график
Эти инструкции используйте продажи и маркетинг — пример приложения для создания графика, отображающую продажи за этот год по категориям. Для выполнения этой процедуры, получение примера приложения из appsource.com.

1. Начните с пустой страницы отчета. Если вы используете службу Power BI, нужно открыть отчет в [режиме правки](../service-interact-with-a-report-in-editing-view.md).

2. В области полей, выберите **SalesFact** \> **общее количество единиц**и выберите **даты** > **месяц**.  Power BI создаст гистограмму на холсте отчетов.

    ![Выберите в области полей](media/power-bi-line-charts/power-bi-step1.png)

4. Преобразуйте график, выбрав шаблон диаграммы из панели визуализации. 

    ![преобразование в график](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. Фильтровать ваш график для отображения данных за 2012 2014 года. Если на панели "фильтры" свернуто, разверните его. В области полей, выберите **даты** \> **год** и перетащите его на панель "фильтры". Поместите его под заголовком **фильтров на данный визуальный элемент**. 
     
    ![строки рядом с панели "поля"](media/power-bi-line-charts/power-bi-year-filter.png)

    Изменение **дополнительные фильтры** для **базовые фильтры** и выберите **2012**, **2013** и **2014**.

    ![Фильтр для года](media/power-bi-line-charts/power-bi-filter-year.png)

6. При необходимости [настройте размер и цвет текста диаграммы](power-bi-visualization-customize-title-background-and-legend.md). 

    ![Увеличение размера шрифта и измените Y axisfont](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>Добавьте дополнительные строки в диаграмму
Графики может иметь много различных строк. И в некоторых случаях, возможно, они не отображают вместе разные значения в строках. Давайте рассмотрим добавление дополнительных строк на текущие диаграммы и узнаете, как в формате нашу диаграмму значений, представленных строк существенно различаются. 

### <a name="add-additional-lines"></a>Добавьте дополнительные строки
Вместо рассмотрения общее количество единиц для всех регионов, как одинарные линии на диаграмме, Давай разделим out общее количество единиц по регионам. Добавьте дополнительные строки, перетащив **географически** > **регион** для формата условных обозначений.

   ![Одну строку для каждого региона](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>Используются две оси Y.
Что делать, если вы хотите рассмотрим общий объем продаж и общее количество единиц на одной диаграмме? Показатели продаж, гораздо выше, чем номера, становится недоступным график. На самом деле отображается красная линия для общее количество единиц должно быть равно нулю.

   ![высокой расходятся значения](media/power-bi-line-charts/power-bi-diverging.png)

Для отображения высокой расходящиеся значений на одной диаграмме, используйте в комбинированную диаграмму. Узнайте все о комбинированные диаграммы, путем чтения [комбинированные диаграммы в Power BI](power-bi-visualization-combo-chart.md). В приведенном ниже примере мы можем отобразить продаж и общего единиц вместе на одной диаграмме, добавив второй оси Y. 

   ![высокой расходятся значения](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="considerations-and-troubleshooting"></a>Рекомендации и устранение неполадок
* Один график не может иметь две оси Y.  Необходимо вместо этого используйте комбинированную диаграмму.
* В приведенных выше примерах диаграммы были оформлены в увеличение размера шрифта, изменить цвет шрифта, добавление заголовков осей, центральный заголовок диаграммы и условные обозначения, запустить обеим осям на ноль и многое другое. Панель форматирования (значок с изображением валика) имеет кажущейся бесконечной последовательности набор возможностей для выполнения того, который вы хотите его внешний вид вашей диаграммы. Чтобы открыть панель форматирования и изучить — лучший способ научиться.

## <a name="next-steps"></a>Дальнейшие действия

[Типы визуализаций в Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

