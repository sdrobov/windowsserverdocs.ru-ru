---
title: Совместимость Windows Server 2019 и серверных приложений Майкрософт
description: Таблица совместимости Windows Server 2019 и серверных приложений корпорации Майкрософт.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: server-general
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2afe7c32-1fda-4441-989b-4115dabdcd34
author: coreyp
ms.author: coreyp-at-msft
manager: jasgroce
ms.localizationpriority: medium
ms.openlocfilehash: 8dcaff6ab8a296790158f59035bd4a5c1a093cbd
ms.sourcegitcommit: 3743cf691a984e1d140a04d50924a3a0a19c3e5c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2019
ms.locfileid: "66442368"
---
# <a name="windows-server-2019-and-microsoft-server-application-compatibility"></a>Совместимость Windows Server 2019 и серверных приложений Майкрософт

>Область применения. Windows Server 2019

В этой таблице перечислены серверные приложения Майкрософт, поддерживающие установку и работу в Windows Server 2019. Эти сведения приведены для справки и не предназначены для замены отдельных спецификаций, требований, объявлений или заявлений общего характера для каждого из серверных приложений. Полноценное описание совместимости и параметров см. в официальной документации по каждому продукту.

Если вы являетесь партнером-поставщиком программного обеспечения, которому нужны дополнительные сведения о совместимости Windows Server с приложениями сторонних разработчиков, посетите [портал сертификации коммерческих приложений](https://commercialappcertification.microsoft.com/).

| **Продукт**                                                  | **Поддерживается основными серверными компонентами**             |   | **Поддерживается на сервере с возможностями рабочего стола** | **Выпущен?** |   | **Веб-ссылка на продукт**                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|--------------------------------------------------------------|------------------------------------------|---|-------------------------------------------------|---------------|---|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange Server 2019                                         | Да                                      |   | Да                                             | Да           |   | [Требования к системе для Exchange Server](https://docs.microsoft.com/Exchange/plan-and-deploy/system-requirements?view=exchserver-2019)                                                                        |
| Host Integration Server 2016 с накопительным обновлением 3 (CU3)                            | Да                                      |   | Да                                             | Да            |   | [Требования к системе для Host Integration Server](https://docs.microsoft.com/host-integration-server/install-and-config-guides/system-requirements)                                                            |
| Visual Studio Team Foundation Server 2017                    | Да\*                                    |   | Да                                             | Да           |   | [Team Foundation Server 2017](https://docs.microsoft.com/tfs/server/requirements?view=vsts)                                                                                                                |
| Visual Studio Team Foundation Server 2018                    | Да\*                                    |   | Да                                             | Да           |   | [Team Foundation Server 2018](https://docs.microsoft.com/tfs/server/requirements?view=vsts)                                                                                                                  |
| Microsoft SQL Server 2014                                    | Да\*                                    |   | Да                                             | Да           |   | [Требования к аппаратному и программному обеспечению для установки SQL Server 2014](https://docs.microsoft.com/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2014)   |
| Microsoft SQL Server 2016                                    | Да\*                                    |   | Да                                             | Да           |   | [Требования к аппаратному и программному обеспечению для установки SQL Server 2016](https://docs.microsoft.com/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2016)   |
| Microsoft SQL Server 2017                                    | Да\*                                    |   | Да                                             | Да           |   | [Требования к аппаратному и программному обеспечению для установки SQL Server 2017](https://docs.microsoft.com/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2017) |
| Microsoft System Center Configuration Manager (версия 1806) | Да, если это управляемый клиент; нет, если это сервер сайта. |   | Да, если это управляемый клиент; нет, если это сервер сайта.        | Да           |   | [Новые возможности версии 1806 System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-in-version-1806)                                                    |
| Microsoft System Center Operations Manager 2019              | Да\*                                    |   | Да                                             | Да           |   | [Системные требования для System Center Operations Manager](https://docs.microsoft.com/system-center/scom/plan-system-requirements)                                                                                                      |
| Microsoft System Center Virtual Machine Manager 2019         | Да\*                                    |   | Да                                             | Да           |   | [Системные требования для System Center Virtual Machine Manager](https://docs.microsoft.com/system-center/vmm/system-requirements)                                                                                                      |
| Microsoft System Center Data Protection Manager 2019         | Нет                                       |   | Да                                             | Да           |   | [Подготовка среды для System Center Data Protection Manager](https://docs.microsoft.com/system-center/dpm/prepare-environment-for-dpm?view=sc-dpm-2019)                                                                                                      |
| SharePoint Server 2016                                       | Нет                                       |   | Да                                             | Да           |   | [Требования к аппаратному и программному обеспечению для SharePoint Server 2016](https://docs.microsoft.com/SharePoint/install/hardware-and-software-requirements)                                                                |
| SharePoint Server 2019                                       | Нет                                       |   | Да                                             | Да           |   | [Требования к аппаратному и программному обеспечению для SharePoint Server 2019](https://docs.microsoft.com/sharepoint/install/hardware-and-software-requirements-2019)                                                       |
| Project Server 2016                                          | Нет                                       |   | Да                                             | Да           |   | [Требования к программному обеспечению для Project Server 2016](https://docs.microsoft.com/project/software-requirements-for-project-server-2016)                                                                                |
| Project Server 2019                                          | Нет                                       |   | Да                                             | Да           |   | [Требования к программному обеспечению для Project Server 2019](https://docs.microsoft.com/project/software-requirements-for-project-server-2019)                                                                          |
| Skype для бизнеса 2019                                      | Нет                                       |   | Да                                             | Да           |   | [Установка необходимых компонентов для Skype для бизнеса Server](https://docs.microsoft.com/skypeforbusiness/deploy/install/install-prerequisites)                                                                          |

\*Могут действовать ограничения или может потребоваться [функция совместимости приложений основных серверных компонентов по требованию (FOD)](install-fod-19.md).
Обратитесь к документации по конкретному продукту или FOD.
