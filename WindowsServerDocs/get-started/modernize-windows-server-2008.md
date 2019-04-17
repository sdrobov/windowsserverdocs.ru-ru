---
title: Обновление Windows Server 2008 и Windows Server 2008 R2
description: Поддержка Windows Server 2008 и 2008 R2 будет прекращена. Узнайте, как выполнить обновление в локальной среде или разместить их в Azure.
ms.prod: windows-server-threshold
ms.mktglfcycl: manage
ms.sitesec: library
author: mikeblodge
ms.author: mikeblodge
ms.date: 07/12/2018
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.localizationpriority: high
ms.openlocfilehash: 4127eab613abb429a200f513a11b944e05da0f76
ms.sourcegitcommit: 9ed4c9fe04ebf3ef488170503c9a354c992b6fde
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2018
ms.locfileid: "4339372"
---
# Обновление Windows Server 2008 и Windows Server 2008 R2

Расширенная поддержка для Windows Server 2008 и Windows Server 2008 R2 закончится 14 января 2020 г. Существует два пути модернизации: обновление в локальной среде или перенос путем повторного размещения в Azure. **При повторном размещении в Azure можно перенести имеющиеся образы Server бесплатно.**

![Блок-схема с описанием путей обновления Windows Server 2008](media/WS08_upgrade_paths.png)


## Локальное обновление
Если требуется оставить серверы в локальной среде и если вы используете Windows Server 2008 или Windows Server 2008 R2, необходимо будет выполнить [обновление до Windows Server 2012/2012 R2](installation-and-upgrade.md#upgrading-to-windows-server-2012-r2), прежде чем вы сможете выполнить [обновление до Windows Server 2016](installation-and-upgrade.md#upgrading-to-windows-server-2016). В ходе обновления у вас останется возможность выполнить перенос в Azure путем повторного размещения.

Дополнительные сведения о вариантах локального обновления см. в разделе [Обновление с Windows Server 2008 R2 или Windows Server 2008](installation-and-upgrade.md#upgrading-from-windows-server-2008-r2-or-windows-server-2008).

Если вы используете Windows Server 2003, необходимо выполнить [обновление до Windows Server 2008](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff972408(v%3dws.10)). Дополнительные сведения о вариантах локального обновления см. в разделе [Пути обновления для Windows Server 2008](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd979563(v=ws.10)).


## Перенос в Azure
Можно выполнить перенос локальных серверов Windows Server 2008 и Windows Server 2008 R2 в Azure и продолжить использовать их на виртуальных машинах. В Azure вы сохраните соответствие нормативным требованиям, повысите уровень защиты и сможете использовать в своей работе преимущества облачных технологий. Преимущества переноса в Azure.

- Обновления системы безопасности в Azure.
- В течение трех дополнительных лет вы будете получать важные обновления системы безопасности для Windows Server 2008 R2 или 2008 без дополнительной платы. 
- Бесплатные обновления в Azure.
- Внедрение дополнительных облачных служб по мере готовности.
- При переносе SQL Server в управляемые экземпляры Azure или на виртуальные машины в течение трех дополнительных лет вы будете получать важные обновления системы безопасности для Windows Server 2008 R2 или 2008 без дополнительной платы. 
- Используйте имеющиеся лицензии на SQL Server и Windows Server для экономии на облачных ресурсах только при использовании Azure.

<a href="uploading-specialized-WS08-image-to-azure.md"><img src="media/WS08-image-banner-small.png"></a>

Чтобы приступить к переносу, см. раздел [Отправка специализированного образа Windows Server 2008 или 2008 R2 в Azure](uploading-specialized-WS08-image-to-azure.md).

Чтобы понять, как анализировать имеющиеся ИТ-ресурсы, оценить то, что у вас уже есть, выделить преимущества переноса конкретных служб и приложений в облако по сравнению с сохранением рабочих нагрузок в локальной среде, а также понять, какую выгоду вы получите от обновления до последней версии Windows Server, см. раздел [Руководство по переносу для Windows Server](https://go.microsoft.com/fwlink/?linkid=872689).


## Обновление SQL Server 2008 или 2008 R2 параллельно с серверами Windows Server

![Логотип SQL Server](media/sqlr2.jpg)

Если вы используете SQL Server 2008 или 2008 R2, вы можете выполнить обновление до SQL Server [2016](https://docs.microsoft.com/sql/sql-server/sql-server-technical-documentation?view=sql-server-2016) или [2017](https://docs.microsoft.com/sql/sql-server/sql-server-technical-documentation?view=sql-server-2017).


## Дополнительные ресурсы
[Платформа Microsoft Azure](https://docs.microsoft.com/azure/#pivot=products)