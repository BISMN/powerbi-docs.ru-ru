---
title: Сценарии емкости Microsoft Power BI Premium
description: Описывает распространенные сценарии емкости Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 1d666a6702515a935d93549d026f207848f2bca8
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565355"
---
# <a name="premium-capacity-scenarios"></a>Сценарии емкости "премиум"

В этой статье описываются реальные сценарии, где были реализованы емкости Power BI premium. Общие вопросы и проблемы, описаны, также как определить проблемы и устранить их:

- [Обновление наборов данных](#keeping-datasets-up-to-date)
- [Выявление медленно реагирующих наборов данных](#identifying-slow-responding-datasets).
- [Определение причин для медленной реакции наборов данных](#identifying-causes-for-sporadically-slow-responding-datasets).
- [Определение наличия достаточного объема памяти](#determining-whether-there-is-enough-memory).
- [Определение наличия достаточного объема ЦП](#determining-whether-there-is-enough-cpu).

Приведены шаги, вместе с примерами диаграмма и таблица из **приложения метрики емкости Power BI Premium** у администратора Power BI доступ к.

## <a name="keeping-datasets-up-to-date"></a>Обновление наборов данных

Изучение этого сценария началось, когда пользователи стали жаловаться, что данные отчета иногда оказываются устаревшими.

В приложении администратор использует визуальный элемент **Обновления**, сортируя наборы данных по статистике **Максимальное время ожидания** в порядке убывания. Этот визуальный элемент помогает выявить наличие длинного времени ожидания, сгруппированные по имени рабочей области наборы данных.

![Обновления набора данных, отсортированные по убыванию максимального времени ожидания, сгруппированные по рабочей области](media/service-premium-capacity-scenarios/dataset-refreshes.png)

В **почасовой среднее обновить ожидания раз** визуальный элемент, он замечает, что время ожидания обновления пиковой нагрузки согласованно около 16: 00 каждый день.

![Периодическое резкое увеличение времени ожидания в 16:00](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Эти результаты обусловлены рядом возможных причин:

- Слишком много попыток обновления могут происходить в то же время, превышение лимита, определяется узел емкости. В данном случае шесть параллельных обновлений на P1 с выделением памяти по умолчанию.

- Наборы данных для обновления может быть слишком большим для помещаются в доступную память (требуется по крайней мере 2 x памяти, необходимый для полного обновления).
- Неэффективная логика Power Query может привести к максимальной загрузке памяти при обновлении набора данных. Занят мощности этой копилки иногда может достигать физическое ограничение, сбой обновления и потенциально влияющие на другие операции представление отчетов в емкости.
- Часто запрашиваемые наборы данных, которые должны оставаться в памяти может повлиять на возможность обновления из-за ограниченной памяти другими наборами данных.

Чтобы помочь исследовать, администратор Power BI могла искать:

- Недостаток доступной памяти во время данных обновляется, когда доступной памяти меньше, чем 2 x размер набора данных для обновления.
- Наборы данных, не обновляются и не в памяти перед обновлением, начавший для отображения интерактивных трафика периоды интенсивной обновления. Чтобы увидеть, какие наборы данных загружаются в память в любой момент времени, администратор Power BI может посмотреть области наборы данных **наборы данных** вкладку в приложении. Администратор затем выполнять перекрестную фильтрацию, на определенный момент времени, щелкнув один из столбцов в **почасовой загрузки набора данных подсчитывает**. Локальных копилки, показано на рисунке ниже, указывает час, когда несколько наборов данных были загружены в память, что может задержать запуск запланированного обновления.
- Принимая вытеснений Повышенная набора данных установите при планировании обновления данных для запуска. Вытеснений можно указать существует нехватка памяти вызвана обслуживает слишком много разных интерактивные отчеты до момента обновления. Визуальный элемент **Почасовые исключения наборов данных и использование памяти** может четко указывать на пики вытеснений.

На следующем рисунке показан локальный пик загруженных наборов данных, который предполагает выполнение интерактивных запросов с отложенным запуском обновлений. При выборе периода времени в визуальном элементе **Число наборов данных, загружаемых каждый час** будет выполняться перекрестная фильтрация визуального элемента **Размеры наборов данных**.

![Локальный пик в загруженных наборах данных предполагает, что из-за создания интерактивных запросов был отложен запуск обновлений.](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

Администратор Power BI может попытаться решить эту проблему, проверив наличие достаточного объема памяти для запуска обновления данных. Для этого он выполняет следующие действия:

- Обратиться к набору данных владельцы и попросив их, чтобы управлять временем и исключить данные расписания обновления.
- Уменьшение набора данных загрузку запросов путем удаления ненужных панелей мониторинга или панели мониторинга плитки, особенно тех, которые обеспечивают безопасность на уровне строк.
- Ускорение обновления данных, оптимизируя логики Power Query. Улучшить моделирования вычисляемые столбцы или таблицы. Уменьшить размер набора данных или настроить более крупных наборов данных для выполнения добавочных данных обновления.

## <a name="identifying-slow-responding-datasets"></a>Определение наборов данных отвечает медленно

В этом случае расследование проявилась, когда пользователи жаловался, что некоторые отчеты заняло слишком много времени, чтобы открыть и в некоторых случаях зависала.

В приложении администратор Power BI может использовать визуальный элемент **Длительность запросов**, чтобы определить наборы данных с наихудшими результатами, отсортировав наборы данных по убыванию **средней длительности**. В этих визуальных элементах также отображается количество запросов к набору данных, поэтому вы можете узнать, как часто они запрашиваются.

![Плохо работающих наборов данных](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

Администратор может ссылаться на **распространение длительности запроса** визуальный элемент, который показывает общее распределение производительность отдельных запросов (< = 30ms, 0-100 мс) за период времени, отфильтрованные. Как правило, большинство пользователей считает нормальным откликом для запросов длительность в одну секунду или меньше. Производительность запросов, которые занимают больше времени, как правило, считается неудовлетворительной.

Визуальный элемент **Почасовое распределение продолжительности выполнения запросов** позволяет администратору Power BI определять одночасовые периоды, когда производительность емкости могла восприниматься как низкая. Чем больше сегментов столбца, представляющих длительность запроса более одной секунды, тем выше риск низкой производительности.

Визуальный элемент является интерактивным, и когда выбран сегмент панели, в соответствующем визуальном элементе таблицы **Продолжительность запроса** на странице отчета выполняется перекрестная фильтрация для отображения наборов данных, которые он представляет. Такая перекрестная фильтрация позволяет администратору Power BI легко определить, какие наборы данных медленно реагируют.

На следующем рисунке показан визуальный элемент, отфильтрованный по **почасовому распределению продолжительности выполнения запросов** с акцентом на наборы данных с наихудшими показателями производительности в одночасовых сегментах. 

![Визуальный элемент с фильтрацией по почасовому распределению продолжительности выполнения запросов, отображающий наборы данных с наихудшими показателями производительности](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

После определения низкой производительностью набора данных в конкретный час на один интервал времени администратора Power BI можно выяснить, вызвана перегруженных емкости к снижению производительности или из-за неправильно разработан набор данных или отчет. Они могут ссылаться на **время ожидания запросов** визуальный элемент и наборы данных сортировки по убыванию запроса среднее время ожидания. Если большое количество запросов находится в состоянии ожидания, большое количество запросов для набора данных она может вызвать слишком много ожиданий запросов. Если время ожидания запроса среднее является существенным (> 100 мс), возможно, стоит просмотра набора данных и отчетов, чтобы увидеть, если можно выполнить оптимизацию. Например меньшее количество визуальных элементов на имеется страницы отчета или способ оптимизации выражение DAX.

![Визуальный элемент "Время ожидания запросов", помогающий выявить наборы данных с низкой производительностью](media/service-premium-capacity-scenarios/query-wait-times.png)

Существует несколько возможных причин для накопления время ожидания запроса в наборах данных:

- Конструктор не самые оптимальные модели, выражения мер или даже отчета макет - любых обстоятельствах, которые могут способствовать длительных запросов, использующих высокий уровень загрузки ЦП. Поэтому новые запросы помещаются в очередь, ожидая, пока потоки ЦП не станут доступными, и могут создавать эффект колонны (например, пробка), который обычно наблюдается в час пик. Страница **Ожидания запросов** будет основным ресурсом для определения наличия высокого значения среднего времени ожидания запроса в наборах данных.
- Большое количество пользователей емкости (от сотен до тысяч), одновременно использующих один и тот же отчет или набор данных. Даже хорошо спроектированные наборы данных могут иметь низкие показатели производительности за пределами порога параллелизма. Обычно это состояние обозначается один набор данных, содержащимся в нем значение значительно выше, запрос подсчитывает чем Показать другие наборы данных (например, 300 КБ запросы к одному набору данных по сравнению с < 30 КБ запросы для всех других наборов данных). В определенный момент в течение которого запрос ожидает для этого набора данных начнет управлять временем, которую можно увидеть в **длительность запроса** visual.
- Большое количество запрошенных одновременно разрозненных наборов данных приводит к пробуксовке памяти, так как наборы данных часто циклически загружались в память и удалялись из нее. Это приводит к снижению производительности при загрузке набора данных в память. Для подтверждения, администратор Power BI могут ссылаться на **почасовой вытеснений набора данных и потребление памяти** visual, которая может означать, что большое количество наборов данных загружен в память выполняется несколько раз прекращено.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Определение причины для нерегулярно медленно — отвечать на запросы наборов данных

В этом случае расследование проявилась, когда пользователи описано визуальных элементов отчетов были медленно отвечает на запросы или иногда может перестать отвечать на запросы, но в других случаях они были достаточно быстро реагирующих.

В приложении в разделе **Длительность запросов** можно выполнить поиск проблемных наборов данных следующим образом:

- В визуальном элементе **Длительность запросов** администратор выполнил фильтрацию по набору данных (начиная с первых запрошенных наборов данных) и изучил перекрестно отфильтрованные столбцы в визуальном элементе **почасового распределения времени ожидания запросов**.
- Когда одну линию один час показали значительные изменения соотношения между все группы длительность запроса и другим панелям один час для этого набора данных (например, отношение между цветами изменяет значительно), это означает, что этот набор данных показано нерегулярные изменения производительность.
- Одночасовые гистограммы, отображающие нерегулярную долю запросов с низкими показателями производительности, указывают временной интервал, на протяжении которого данный набор данных попал под влияние "шумных соседей", вызванное действиями других наборов данных.

На приведенном ниже рисунке показаны изменения, происшедшие за один час 30 января, когда произошел существенный спад в производительности набора данных, о чем свидетельствует размер сегмента продолжительности выполнения (3,10 с). Щелкнув этот одночасовой панель показывает все наборы данных загружаются в память в течение этого времени, отображая возможные наборы данных, вызывая эффект шумного соседа.

![Гистограмма, отображающая худшие показатели производительности](media/service-premium-capacity-scenarios/worst-performing-queries.png)

После проблемных timespan идентифицируется (например, во время января 30 на приведенном выше рисунке) администратора Power BI можно удалить все фильтры набора данных а затем фильтровать только по этот интервал времени, чтобы определить, какие наборы данных запрошены активно в течение этого времени. Причиной набора данных для эффекта шумного соседа обычно является верхней запрашиваемого набора данных или с наиболее длительным временем Средняя продолжительность запроса.

Решением этой проблемы может быть распределение проблемных наборов данных по разным рабочим областям в разных емкостях Premium или в общедоступной емкости при наличии необходимого размера набора данных и шаблонов обновления данных, а также соблюдении требований к потреблению.

Обратное также может быть верным. Администратор Power BI может определить случаи, когда производительность запросов к набору данных резко улучшается, а затем приступить к поиску причины. Если на этом этапе отсутствуют определенные сведения, это может указывать на причину проблемы.

## <a name="determining-whether-there-is-enough-memory"></a>Определение того, имеется ли достаточный объем памяти

Чтобы проверить, достаточно ли в емкости памяти для выполнения рабочих нагрузок, администратор Power BI может использовать визуальный элемент **Использование памяти (%)** на вкладке **Наборы данных** в приложении. **Вся** (общий объем) память представляет собой память, занятую наборами данных, загруженными в память, независимо от того, активно ли они запрашиваются или обрабатываются. **Активная** память представляет собой память, занятую наборами данных, которые активно обрабатываются.

В работоспособной емкости визуальный элемент будет выглядеть следующим образом, отображая промежуток между всей памятью (общим объемом) и активной памятью:

![Работоспособная емкость, отображающая промежуток между всей памятью (общим объемом) и активной памятью](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

Значение объема возникла нехватка памяти тот же визуальный ясно показывает, активной памяти и общий объем памяти, объединения, это означает, что вы не сможете затем загрузить дополнительные наборы данных в памяти. В этом случае администратор Power BI может щелкнуть **Перезапуск емкости** (в разделе **Расширенные параметры** в области параметров емкости портала администрирования). Перезапуск емкости приводит к удалению всех наборов данных из памяти, позволяя им перезагружаться в память по мере необходимости (путем выполнения запросов или обновления данных).

![Схождение **активной** памяти с **общей**](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Определить, является ли достаточное количество ЦП

Как правило, средняя загрузка процессора емкости не должна превышать 80 %. Превышение этого значения означает, что емкость приближается к перегрузке ЦП.

Последствия насыщенность ЦП выражаются операциями, длится дольше, чем следует, из-за емкость, выполнение количество переключений контекстов ЦП, так как он пытается обработать все операции. Емкость Premium с большое количество параллельных запросов это состояние обозначается времени ожидания большого количества запросов. Следствием длительного времени ожидания запросов является медленный отклик. Администратор Power BI может легко определить, насколько сильно загружен ЦП, просмотрев сведения, представленные в визуальном элементе **Почасовое распределение времени ожидания запросов**. Количество случаев периодического резкого увеличения времени ожидания запросов указывает на потенциальную перегрузку ЦП.

![Количество случаев периодического резкого увеличения времени ожидания запросов указывает на потенциальную перегрузку ЦП](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Иногда подобная картина может встречаться при выполнении фоновых операций, если они способствуют перегрузке ЦП. Во время обновления для конкретного набора данных, которое может указывать (возможно, из-за других обновление текущего набора данных и/или интерактивные запросы), насыщенность ЦП во время периодических пик можно найти администратором Power BI. В этом случае в представлении **Система** в приложении может отображаться (необязательно), что загрузка процессора составляет 100 %. В представлении **Система** отображаются среднечасовые средние значения, но ЦП может насыщаться в течение нескольких минут интенсивного выполнения операций, что проявляется как пик в значениях времени ожидания.

Существуют и другие причины перегрузки ЦП. В то время как количество ожидающих запросов важно, время ожидания запроса никогда не вызывает заметного снижения производительности. Некоторые наборы данных (с более длительным средним временем поступления запроса, указывающим на сложность или размер) более подвержены эффектам перегрузки ЦП, чем другие. Чтобы легко идентифицировать эти наборы данных, администратор Power BI может обратить внимание на изменения в цветовом составе гистограмм в визуальном элементе **почасового распределения времени ожидания**. После определения гистограммы выбросов администраторы могут искать наборы данных с ожидающим в течение всего этого времени запросом, а также сравнить среднее время ожидания запроса со средней продолжительностью запроса. Если эти две метрики имеют одинаковую величину, а рабочая нагрузка запроса для набора данных нетривиальна, вероятнее всего, на набор данных влияет недостаточная загрузка ЦП.

Этот эффект может быть особенно заметно при использовании набора данных в короткие вспышки высокая частота запросов несколькими пользователями (например, в сеансе обучения), что приводит к образованию ЦП во время каждого пакета. В этом случае может наблюдаться увеличение времени ожидания запроса для этого набора данных, а также влияние на другие наборы данных в емкости (эффект "шумного соседа").

В некоторых случаях администраторы Power BI могут потребовать, чтобы владельцы наборов данных создали менее энергозависимую рабочую нагрузку для запросов, создав вместо отчета панель мониторинга (которая периодически запрашивает любое обновление набора данных для кэшированных плиток). Это может помочь предотвратить пики в случае, когда панель мониторинга загружается. Это решение может оказаться невозможным при наличии некоторых бизнес-требований, однако оно может быть эффективным способом избежания перегрузки ЦП без изменения набора данных.

## <a name="acknowledgements"></a>Подтверждения

Эта статья написана, Питер Майерс, MVP платформы данных и независимых экспертом по бизнес-Аналитики с [побитового решения](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Монитор емкости "премиум" с приложением](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Монитор емкости на портале администрирования](service-admin-premium-monitor-portal.md)   

Появились дополнительные вопросы? [Попробуйте задать вопрос в сообществе Power BI.](https://community.powerbi.com/)

||||||