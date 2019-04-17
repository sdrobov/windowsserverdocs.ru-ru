---
title: Windows Server 2019 и Microsoft Server совместимости приложений
description: Таблица совместимости серверных приложений Майкрософт и Windows Server 2019
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
ms.openlocfilehash: e8bb8cda003ca151216e3b86d5884dfd05e73e6d
ms.sourcegitcommit: 5d55c3ebd1ceee7229ea9a9989c69cf93757ed88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2019
ms.locfileid: "9256947"
---
# Windows Server 2019 и Microsoft Server совместимости приложений

>Область применения: Windows Server 2019

В этой таблице перечислены серверные приложения корпорации Майкрософт, поддерживающие установку и работу в Window Server 2019. Эти сведения приведены для справки и не предназначены для замены отдельных спецификаций, требований, объявлений или заявлений общего характера для каждого из серверных приложений. Полноценное описание совместимости и параметров см. в официальной документации по каждому продукту.

Если вы являетесь партнером поставщика программного обеспечения, которым нужны дополнительные сведения о совместимости Windows Server с приложениями сторонних разработчиков, посетите [портал сертификации приложений для коммерческих](https://commercialappcertification.microsoft.com/).
| **Продукт**                                                  | **Поддерживается в Server Core**             |   | **Поддерживается на сервер с возможностями рабочего стола** | **Выпущено?** |   | **Веб-ссылки с продукта**                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|--------------------------------------------------------------|------------------------------------------|---|-------------------------------------------------|---------------|---|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Сервер Exchange Server 2019 г.                                         | Да                                      |   | Да                                             | Да           |   | [Требования к системе для сервера Exchange Server](https://docs.microsoft.com/Exchange/plan-and-deploy/system-requirements?view=exchserver-2019)                                                                        |
| Host Integration Server 2016 CU3                            | Да                                      |   | Да                                             | Нет            |   | [Требования к системе сервера интеграции узла](https://docs.microsoft.com/host-integration-server/install-and-config-guides/system-requirements)                                                            |
| Visual Studio Team Foundation Server2017                    | Yes\ *                                    |   | Да                                             | Да           |   | [Team Foundation Server2017](https://docs.microsoft.com/tfs/server/requirements?view=vsts)                                                                                                                |
| Visual Studio Team Foundation Server 2018 г.                    | Yes\ *                                    |   | Да                                             | Да           |   | [Team Foundation Server 2018 г.](https://docs.microsoft.com/tfs/server/requirements?view=vsts)                                                                                                                  |
| Microsoft SQL Server 2014                                    | Yes\ *                                    |   | Да                                             | Да           |   | [Требования к оборудованию и программному обеспечению для установки SQL Server2014](https://docs.microsoft.com/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2014)   |
| Microsoft SQL Server2016                                    | Yes\ *                                    |   | Да                                             | Да           |   | [Оборудованию и программному обеспечению для установки SQL Server 2016](https://docs.microsoft.com/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2016)   |
| Microsoft SQL Server 2017 г.                                    | Yes\ *                                    |   | Да                                             | Да           |   | [Оборудованию и программному обеспечению для установки SQL Server 2017 г.](https://docs.microsoft.com/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2017) |
| Microsoft System Center Configuration Manager (версия 1806) | Да, как управляемый клиент, не в качестве сервера сайта |   | Да, как управляемый клиент, не в качестве сервера сайта        | Да           |   | [Новые возможности в версии 1806 System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-in-version-1806)                                                    |
| Microsoft System Center Operations Manager 2019 г.              | Yes\ *                                    |   | Да                                             | Да           |   | [Требования к системе для System Center Operations Manager](https://docs.microsoft.com/system-center/scom/plan-system-requirements)                                                                                                      |
| Microsoft System Center Virtual Machine Manager 2019 г.         | Yes\ *                                    |   | Да                                             | Да           |   | [Требования к системе для диспетчера виртуальных машин System Center](https://docs.microsoft.com/system-center/vmm/system-requirements)                                                                                                      |
| Microsoft System Center Data Protection Manager 2019 г.         | Нет                                       |   | Да                                             | Да           |   | [Подготовка среды для System Center Data Protection Manager](https://docs.microsoft.com/system-center/dpm/prepare-environment-for-dpm?view=sc-dpm-2019)                                                                                                      |
| SharePoint Server2016                                       | Нет                                       |   | Да                                             | Да           |   | [Требования к оборудованию и программному обеспечению для SharePoint Server2016](https://docs.microsoft.com/SharePoint/install/hardware-and-software-requirements)                                                                |
| SharePoint Server 2019                                       | Нет                                       |   | Да                                             | Да           |   | [Требования к оборудованию и программному обеспечению для SharePoint Server 2019](https://docs.microsoft.com/sharepoint/install/hardware-and-software-requirements-2019)                                                       |
| Project Server2016                                          | Нет                                       |   | Да                                             | Да           |   | [Требования к программному обеспечению для Project Server2016](https://docs.microsoft.com/project/software-requirements-for-project-server-2016)                                                                                |
| Project Server 2019 г.                                          | Нет                                       |   | Да                                             | Да           |   | [Требования к программному обеспечению для Project Server 2019](https://docs.microsoft.com/project/software-requirements-for-project-server-2019)                                                                          |
| Скайп для бизнеса 2019 г.                                      | Нет                                       |   | Да                                             | Да           |   | [Установка необходимых компонентов для Скайп для бизнеса Server](https://docs.microsoft.com/skypeforbusiness/deploy/install/install-prerequisites)                                                                          |

\*May могут иметь ограничения или требовать [Server Core приложение совместимость компонентов по требованию (FOD). ](install-fod-19.md)
Обратитесь к документации FOD или конкретного продукта.
