---
title: Древовидные диаграммы в Power BI
description: Древовидные диаграммы в Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4c28071917dbe5669e6e35bd416236ef7047eb24
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408707"
---
# <a name="treemaps-in-power-bi"></a>Древовидные диаграммы в Power BI

Диаграмма дерево отображает иерархические данные в виде набора вложенных прямоугольников. Каждый уровень иерархии представлен цветным прямоугольником (ветвь), содержащим прямоугольники меньшего размера (листья). Power BI задает размер пространства внутри каждого прямоугольника на основе измеренного значения. Прямоугольники упорядочиваются по размеру: от верхнего левого (самый большой) до нижнего правого (самый маленький).

![Снимок экрана: количество продуктов по категориям и диаграмма "дерево" изготовителей.](media/power-bi-visualization-treemaps/pbi-nancy-viz-treemap.png)

Например, при анализе продаж у вас могут быть ветки верхнего уровня для категорий одежды: **Urban** (Городской стиль), **Rural** (Деревенский стиль), **Youth** (Молодежный стиль) и **Mix** (Смешанный стиль). Power BI разделит прямоугольники вашей категории на листья для производителей одежды в этой категории. Размер и заливка этих мелких прямоугольников будут основываться на объемах продаж.

В ветви **Urban** продано много одежды **VanArsdel**. Меньше было продано одежды**Natura** и **Fama**. И лишь несколько вещей было продано марки **Leo**. Таким образом, ветвь **Urban** на дереве содержит:

* Самый большой прямоугольник с именем **VanArsdel** в левом верхнем углу.

* Меньшие по размеру прямоугольники с именами **Natura** и **Fama**.

* Много других прямоугольников, представляющих прочие категории.

* Мелкий прямоугольник с именем **Leo**.

Итак, мы можем сравнить количество проданных товаров в разных группах, сравнив размер и заливку каждого листового узла: чем больше размер прямоугольника и темнее заливка, тем больше значение.

Хотите сначала посмотреть демонстрацию создания диаграммы дерева? Перейдите к отметке 2:10 в этом видео, чтобы посмотреть, как Аманда создает диаграмму дерева.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-treemap"></a>Сферы применения диаграмм дерева

Диаграмма дерево отлично подходит:

* для отображения больших объемов иерархических данных;

* когда линейчатая диаграмма не может эффективно обрабатывать большое количество значений;

* для отображения пропорций между каждой частью и целым;

* для отображения шаблонов распределения показателя на каждом уровне категорий в иерархии;

* для отображения атрибутов путем кодирования по размеру и цвету;

* для выделения шаблонов, выбросов, наиболее важных участников и исключений.

## <a name="prerequisites"></a>Предварительные требования

* Служба Power BI или Power BI Desktop

* Пример отчета "Анализ розничной торговли"

## <a name="get-the-retail-analysis-sample-report"></a>Получение примера отчета "Анализ розничной торговли"

Здесь используется пример "Анализ розничной торговли". Чтобы создать визуализацию, требуются разрешения на изменение для набора данных и отчета. К счастью, все примеры Power BI можно редактировать. Если кто-то совместно с вами использует отчет, вы не сможете создавать визуализации в отчетах. Чтобы продолжить работу, получите [отчет примера "Анализ розничной торговли"](../sample-datasets.md).

После получения набора данных **примера "Анализ розничной торговли"** вы сможете приступить к работе.

## <a name="create-a-basic-treemap"></a>Создание простой диаграммы дерева

Вы создаете отчет и добавляете простую диаграмму "дерево".

1. В **Моей рабочей области** выберите **Наборы данных** > **Создать отчет**.

    ![Снимок экрана: "Набор данных > Создать отчет"](media/power-bi-visualization-treemaps/power-bi-create-a-report.png)

1. В области **Поля** выберите меру **Продажи** > **Продажи за прошлый год**.

   ![Снимок экрана: "Продажи > Продажи" за прошлый год и результирующий визуальный элемент.](media/power-bi-visualization-treemaps/treemapfirstvalue_new.png)

1. Выберите значок диаграммы "дерево" ![Снимок экрана: значок диаграммы "дерево"](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) для преобразования диаграммы в диаграмму "дерево".

   ![Снимок экрана: диаграмма "дерево" без конфигурации.](media/power-bi-visualization-treemaps/treemapconvertto_new.png)

1. Перетащите поле **Item** > **Category** (Элемент > Категория) в область **Группа**.

    Power BI создаст диаграмму дерева, в которой размер прямоугольников отражает общий объем продаж, а цвет представляет категорию. По существу, вы создали иерархию, которая визуально описывает относительный размер общего объема продаж по категориям. Категория мужской одежды **Men** имеет самый большой объем продаж, а категория трикотажа **Hosiery** — самый маленький.

    ![Снимок экрана: диаграмма "дерево" после конфигурации.](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. Перетащите поле **Store** > **Chain** (Магазин > Сеть) в область **Сведения**, чтобы завершить создание диаграммы. Теперь можно сравнить продажи за прошлый год по категориям и сетям магазинов.

   ![Снимок экрана: диаграмма "дерево" и мера Store > Chain ("Магазин > Сеть магазинов") в области Details (Сведения).](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > Параметры "Насыщенность цвета" и "Сведения" невозможно использовать одновременно.

1. Наведите указатель на заголовок **Chain** (Сеть магазинов), чтобы увидеть подсказку для этой части области **Category**(Категория).

    Например, при наведении курсора на **Fashions Direct** в прямоугольнике **090-Home** всплывает подсказка для части Fashion Direct категории Home.

   ![Снимок экрана: всплывающая подсказка Home (Главная страница).](media/power-bi-visualization-treemaps/treemaphoverdetail_new.png)

1. Добавьте диаграмму "дерево" как [плитку панели мониторинга (закрепите визуальный элемент)](../service-dashboard-tiles.md).

1. Сохраните [отчет](../service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Выделение и перекрестная фильтрация

Сведения об использовании области **Фильтры** см. в статье [Добавление фильтра в отчет](../power-bi-report-add-filter.md).

Выделите **Category** (Категория) или **Detail** (Сведения) в диаграмме "дерево" для перекрестной фильтрации и других визуализаций на странице отчета и наоборот. Чтобы продолжить, добавьте несколько визуальных элементов на эту же страницу либо скопируйте диаграмму "дерево" на одну из других страниц этого отчета.

1. На диаграмме "дерево" выберите **Category** (Категория) или **Chain** (Цепочка магазинов) в области **Category** (Категория). Это приведет к перекрестному выделению других визуализаций на странице. Например, при выборе категории **050-Shoes** видно, что продажи за последний год в категории "Обувь" составили **3 640 471 долл. США**, а доля продаж в категории**Fashions Direct** составила **2 174 185 долл. США**.

   ![Снимок экрана: отчет "Обзор продаж магазина" с перекрестной фильтрацией.](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. В круговой диаграмме **Last Year Sales by Chain** (Продажи за прошлый год по сети магазинов) выберите сектор **Fashions Direct**, чтобы перекрестно фильтровать диаграмму в виде дерева.
   ![GIF-демонстрация функции перекрестной фильтрации.](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. Подробности о настройке перекрестной фильтрации в диаграммах см. в статье [Visualization interactions in a Power BI report](../service-reports-visual-interactions.md) (Взаимодействия визуализаций в отчете Power BI).

## <a name="next-steps"></a>Дальнейшие действия

* [Каскадные диаграммы в Power BI](power-bi-visualization-waterfall-charts.md)

* [Типы визуализаций в Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
