---
title: Превращение книги Excel в привлекательный отчет в службе Power BI
description: В этой статье показано, как быстро создать привлекательный отчет из книги Excel.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: ed4bc9d10e3e1512aba559d77ba8729a39cb8a84
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "68995054"
---
# <a name="from-excel-workbook-to-stunning-report-in-the-power-bi-service"></a>Превращение книги Excel в привлекательный отчет в службе Power BI
Ваш руководитель требует отчет по последним результатам продаж и ваши впечатления о последней кампании к концу дня. При этом последние данные хранятся в различных сторонних системах и в файлах на вашем ноутбуке. Раньше создание визуальных элементов и форматирование отчета занимало несколько часов и заставляло понервничать.

Не волнуйтесь. В Power BI превосходный отчет можно создать практически мгновенно.

В этом примере мы отправим файл Excel из локальной системы, создадим отчет и предоставим к нему доступ коллегам — и все это в Power BI.

## <a name="prepare-your-data"></a>Подготовка данных
Для примера возьмем простой файл Excel. 

1. Прежде чем отправлять файл Excel в Power BI, необходимо упорядочить данные в виде таблицы с одноуровневой адресацией. В плоской таблице каждый столбец содержит данные одного типа: текст, даты, цифры, валюты и т. д. Таблица должна содержать строку заголовков, но не должна включать столбцы или строки с итогами.

   ![Упорядоченные данные в Excel](media/service-from-excel-to-stunning-report/pbi_excel_file.png)

2. Теперь отформатируем данные в виде таблицы. В группе **Стили** на вкладке **Главная** в Excel выберите **Форматирование таблицы**. 

3. Выберите стиль таблицы, который нужно применить к листу. 

   Теперь лист Excel готов к отправке в Power BI.

   ![Форматирование данных в виде таблицы](media/service-from-excel-to-stunning-report/pbi_excel_table.png)

## <a name="upload-your-excel-file-to-the-power-bi-service"></a>Отправка файла Excel в службу Power BI
Служба Power BI подключается к нескольким источникам данных, включая файлы Excel на вашем компьютере. 

 > [!NOTE] 
 > Далее в этом руководстве описана работа с [книгой, содержащей пример финансовых данных](sample-financial-download.md).

1. Чтобы начать работу, войдите в службу Power BI. Если вы еще не зарегистрировались, [это можно сделать бесплатно](https://powerbi.com).

2. Создайте новую панель мониторинга. Откройте **Моя рабочая область** и выберите значок **Создать**.

   ![значок "Создать"](media/service-from-excel-to-stunning-report/power-bi-new-dash.png)

3. Выберите **Панель мониторинга**, введите имя и выберите **Создать**. 

   Новая панель мониторинга отображается без данных.

   ![создание раскрывающегося списка](media/service-from-excel-to-stunning-report/power-bi-create-dash.png)

4. В нижней части левой области навигации выберите **Получить данные**. 

5. В разделе **Создать новый контент** страницы **Получить данные** в поле **Файлы** выберите **Получить**.

   ![Получение данных из файлов](media/service-from-excel-to-stunning-report/pbi_get_files.png)

6. На странице **Файлы** выберите **Локальный файл**. Перейдите к файлу книги Excel на компьютере и выберите **Открыть**, чтобы отправить его в службу Power BI. 

   ![окно "Получить данные" > Файлы](media/service-from-excel-to-stunning-report/pbi_local_file.png)

7. На странице **Локальный файл** выберите **Импорт**.


## <a name="build-your-report"></a>Создание отчета
После того как служба Power BI импортирует файл Excel, приступайте к созданию отчета. 

1. Когда появится сообщение **Your dataset is ready** (Набор данных готов), выберите **Просмотреть набор данных**.  

   Power BI откроется в режиме редактирования и отобразит холст отчета. Справа находятся панели **Визуализации**, **Фильтры** и **Поля**. Данные из таблицы Excel отображаются на панели **Поля**. Заголовки столбцов перечисляются под названием таблицы как отдельные поля.

   ![Как выглядят данные Excel на панели "Поля"](media/service-from-excel-to-stunning-report/pbi_report_fields.png)

2. Теперь можно приступать к созданию визуализации. Предположим, ваш руководитель хочет увидеть прибыли за определенный период. Перетащите поле **Прибыль** с панели **Поля** на холст отчета. 

   По умолчанию в Power BI отображается линейчатая диаграмма. 

3. Перетащите на холст отчета поле **Дата**. 

   Power BI обновит линейчатую диаграмму и покажет прибыль по датам.

   ![Гистограмма в редакторе отчетов](media/service-from-excel-to-stunning-report/pbi_report_pin-new.png)

   > [!TIP]
   > Если диаграмма выглядит не так, как вы ожидали, проверьте агрегированные значения. Например, в области **Значение** щелкните правой кнопкой мыши только что добавленное поле и убедитесь, что вычисление данных выполняется надлежащим образом. В нашем примере используется **суммирование**.
   > 

Ваш руководитель хочет знать, какие страны оказались наиболее прибыльными. Произведите на него впечатление, добавив визуализацию карты. 

1. Выберите пустую область на холсте отчета. 

2. Перетащите поля **Страна** и **Прибыль** с панели **Поля** на холст отчета.

   Power BI создаст визуализацию карты с пузырьками, представляющими относительную прибыль в каждом регионе.

   ![Визуальный элемент "Карта" в редакторе отчетов](media/service-from-excel-to-stunning-report/pbi_report_map-new.png)

А что насчет визуального представления продаж по продуктам и сегментам рынка? Это легко. 

1. На панели **Поля** выберите поля **Продажи**, **Продукт** и **Сегмент**. 
   
   Power BI мгновенно создаст линейчатую диаграмму. 

2. Измените тип диаграммы, выбрав один из значков в меню **Визуализации**. Например, вы можете преобразовать ее в **гистограмму с накоплением**. 

3. Чтобы отсортировать данные на диаграмме, щелкните многоточие (...) и выберите **Сортировка**.

   ![Гистограмма с накоплением в редакторе отчетов](media/service-from-excel-to-stunning-report/pbi_barchart-new.png)

Закрепите все визуальные элементы на панели мониторинга. Теперь их можно сделать доступными для коллег.

   ![Панель мониторинга с тремя закрепленными визуальными элементами](media/service-from-excel-to-stunning-report/pbi_report.png)

## <a name="share-your-dashboard"></a>Предоставление доступа к панели мониторинга
Допустим, вы хотите предоставить доступ к панели мониторинга своему руководителю. Доступ к панели мониторинга и соответствующему отчету можно предоставить коллегам, у которых есть учетная запись Power BI. Они смогут работать с отчетом, но не смогут сохранять изменения в нем.

1. Чтобы предоставить доступ к отчету, в верхней части панели мониторинга выберите элемент **Поделиться**.

   ![Значок "Предоставить общий доступ"](media/service-from-excel-to-stunning-report/power-bi-share.png)

   В Power BI откроется страница **Общий доступ к панели мониторинга**. 

2. Введите адреса электронной почты получателей в поле **Введите адреса электронной почты** и добавьте сообщение в поле ниже. 

3. Чтобы разрешить получателям предоставлять общий доступ к панели мониторинга другим пользователям, установите флажок **Разрешить получателям предоставлять доступ к этой панели мониторинга**. Выберите **Общий доступ**.

   ![Окно общего доступа к панели мониторинга](media/service-from-excel-to-stunning-report/power-bi-share-dash-new.png)

## <a name="next-steps"></a>Дальнейшие действия

* [Приступая к работе со службой Power BI](service-get-started.md)
* [Начало работы с Power BI Desktop](desktop-getting-started.md)
* [Основные понятия для разработчиков в службе Power BI](service-basic-concepts.md)

Появились дополнительные вопросы? [Ответы на них см. в сообществе Power BI](http://community.powerbi.com/).

