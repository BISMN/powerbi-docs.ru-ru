---
title: Локальный шлюз данных
description: Это обзор локального шлюза данных для Power BI. С его помощью можно работать с источниками данных DirectQuery. Кроме того, этот шлюз можно использовать для обновления облачных наборов данных с локальными данными.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 06/05/2018
ms.openlocfilehash: 7e2e0e7a980c72f203f93baf552685dce6f43bbd
ms.sourcegitcommit: 8dee40f07d284ec84a8afa0100359f146e1dd88b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67418813"
---
# <a name="on-premises-data-gateway"></a>Локальный шлюз данных

Локальный шлюз данных служит мостом, обеспечивая быструю и безопасную передачу данных между локальной системой (данными, которые не находятся в облаке) и службами Power BI, Microsoft Flow, Logic Apps и PowerApps.

Один шлюз можно использовать для работы с разными службами одновременно. Если вы используете и Power BI, и PowerApps, с помощью одного шлюза можно работать с обеими этими службами. Достаточно просто войти с нужной учетной записью.

> [!NOTE]
> Локальный шлюз данных реализует сжатие данных и шифрование транспорта во всех режимах.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-requirements-include.md)]

### <a name="limitations-of-analysis-services-live-connections"></a>Ограничения для динамических подключений к службам Analysis Services

С помощью динамического подключения можно работать с табличными и с многомерными экземплярами.

| **Версия сервера** | **Требуемый номер SKU** |
| --- | --- |
| 2012 SP1 CU4 или более поздняя версия |Бизнес-аналитика и SKU категории "корпоративный" |
| 2014 |Бизнес-аналитика и SKU категории "корпоративный" |
| 2016 |SKU категории "стандартный" или старшая версия |

* Функции форматирования на уровне ячеек и перевода не поддерживаются.
* Из Power BI недоступны действия и именованные наборы, но вы можете подключаться к многомерным кубам, которые их содержат, и создавать визуальные элементы и отчеты.

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="download-and-install-the-on-premises-data-gateway"></a>Скачать и установить локальный шлюз данных

Чтобы скачать шлюз, выберите **Шлюз данных** в меню "Загрузки". Скачайте [локальный шлюз данных](http://go.microsoft.com/fwlink/?LinkID=820925).

Чтобы обновить шлюз, его необходимо установить повторно, как описано в этом разделе. Во время установки новой версии шлюза существующие параметры сохраняются. Установка той же версии воспринимается как полная переустановка, во время которой параметры не сохраняются.

![](media/service-gateway-onprem/powerbi-download-data-gateway.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-install-include](./includes/gateway-onprem-install-include.md)]

## <a name="install-the-gateway-in-personal-mode"></a>Установка шлюза в личном режиме

> [!NOTE]
> Личная версия шлюза работает только с Power BI.

После установки личного шлюза вам потребуется запустить **мастер настройки шлюза Power BI Gateway - Personal**.

![](media/service-gateway-onprem/personal-gateway-launch-configuration.png)

Затем вам потребуется войти в Power BI, чтобы зарегистрировать шлюз в облачной службе.

![](media/service-gateway-onprem/personal-gateway-signin.png)

Вам также понадобится указать имя пользователя и пароль Windows, с которыми будет работать служба Windows. Эти имя и пароль могут не совпадать с вашими учетными данными Windows. Служба шлюза будет запущена с помощью этой учетной записи.

![](media/service-gateway-onprem/personal-gateway-windows-service.png)

После завершения установки вам потребуется открыть свои наборы данных в Power BI и указать учетные данные для своих локальных источников.

<a name="credentials"></a>

## <a name="storing-encrypted-credentials-in-the-cloud"></a>Хранение зашифрованных учетных данных в облаке

При добавлении в шлюз источника данных необходимо указать учетные данные для доступа к этому источнику. Все запросы к источнику данных будут выполняться с использованием этих учетных данных. Учетные данные надежно шифруются с применением симметричного шифрования и не могут быть расшифрованы в облаке перед сохранением в облако. Учетные данные отправляются на локальный компьютер со шлюзом и расшифровываются при обращении к источникам данных.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

<!-- How the gateway works -->
[!INCLUDE [gateway-onprem-how-it-works-include](./includes/gateway-onprem-how-it-works-include.md)]

## <a name="limitations-and-considerations"></a>Рекомендации и ограничения

* [Azure Information Protection](https://docs.microsoft.com/microsoft-365/enterprise/protect-files-with-aip
) сейчас не поддерживается.
* [Access Online](https://products.office.com/access) сейчас не поддерживается.
* Скрипты R поддерживаются только при запуске шлюза в персональном режиме.

## <a name="tenant-level-administration"></a>Администрирование уровня клиента

Как администратор клиента вы можете просматривать все локальные шлюзы данных, установленные в клиенте, и управлять ими. Эта возможность сейчас находится на этапе общедоступной предварительной версии. Дополнительные сведения см. в [документации по центру администрирования платформы Power](/power-platform/admin/onpremises-data-gateway-management).

Кроме того, если вы являетесь администратором клиента, попросите пользователей в вашей организации добавлять вас в качестве администратора для каждого шлюза, который они устанавливают. Это позволяет управлять всеми шлюзами в вашей организации на странице настройки шлюза или посредством [команд PowerShell](service-gateway-high-availability-clusters.md#powershell-support-for-gateway-clusters). 

## <a name="enabling-outbound-azure-connections"></a>Включение исходящих подключений Azure

Локальный шлюз данных использует служебную шину Azure для подключения к облаку и устанавливает надлежащие исходящие подключения к соответствующему региону Azure. По умолчанию это расположение вашего клиента Power BI. См. статью [Где расположен мой клиент Power BI?](https://powerbi.microsoft.com/documentation/powerbi-admin-where-is-my-tenant-located/)
Если брандмауэр блокирует исходящие подключения, необходимо настроить его так, чтобы разрешить исходящие подключения от локального шлюза данных к соответствующему региону Azure. Подробные сведения о диапазонах IP-адресов каждого центра данных Azure см. на странице [Диапазоны IP-адресов центров данных Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653).
> [!NOTE]
> Диапазоны IP-адресов могут со временем меняться, поэтому необходимо регулярно скачивать актуальные сведения. 

## <a name="troubleshooting"></a>Устранение неполадок

Если при установке и настройке шлюза возникают проблемы, см. статью [Устранение неполадок с локальным шлюзом данных](service-gateway-onprem-tshoot.md). Если у вас проблемы с брандмауэром, см. раздел статьи об устранении неполадок, посвященный [брандмауэру или прокси-серверу](service-gateway-onprem-tshoot.md#firewall-or-proxy).

Если для шлюза возникли проблемы с прокси-сервером, см. статью о [настройке параметров прокси-сервера для шлюзов Power BI](service-gateway-proxy.md).

## <a name="next-steps"></a>Дальнейшие действия

[Управление своим источником данных — службы Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Управление своим источником данных — SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Управление своим источником данных — SQL Server](service-gateway-enterprise-manage-sql.md)  
[Управление своим источником данных — Oracle](service-gateway-onprem-manage-oracle.md)  
[Управление источником данных — импорт или запланированное обновление](service-gateway-enterprise-manage-scheduled-refresh.md)  
[Локальный шлюз данных во всех подробностях](service-gateway-onprem-indepth.md)  
[Локальный шлюз данных (персональный режим) — новая версия личного шлюза](service-gateway-personal-mode.md)  
[Настройка параметров прокси-сервера для локального шлюза данных](service-gateway-proxy.md)  

Появились дополнительные вопросы? [Ответы на них см. в сообществе Power BI.](http://community.powerbi.com/)
