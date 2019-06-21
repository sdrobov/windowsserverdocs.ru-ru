---
title: DirectAccess
description: Можно использовать в этом разделе представлен краткий обзор DirectAccess в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b71d18e-1939-4fc0-bb42-29e0e5ffc8da
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 11c5aa093ddd5aa4777e88c536195bb70bd846db
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67281925"
---
# <a name="directaccess"></a>DirectAccess

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Можно использовать в этом разделе представлен краткий обзор DirectAccess, включая сервер и клиентские операционные системы, которые поддерживают DirectAccess, и ссылки на дополнительную документацию DirectAccess для Windows Server 2016.  
  
> [!NOTE]  
> Дополнение к данному разделу доступна следующая документация по DirectAccess.  
>   
> -   [Возможности развертывания DirectAccess в Windows Server](DirectAccess-Deployment-Paths-in-Windows-Server.md)  
> -   [Предварительные требования для развертывания DirectAccess](Prerequisites-for-Deploying-DirectAccess.md)  
> -   [Неподдерживаемые конфигурации DirectAccess](DirectAccess-Unsupported-Configurations.md)  
> -   [Руководства по лаборатории тестирования DirectAccess](DirectAccess-Test-Lab-Guides.md)  
> -   [DirectAccess — известные проблемы](DirectAccess-Known-Issues.md)  
> -   [Планирование загрузки DirectAccess](DirectAccess-Capacity-Planning.md) 
> -   [Присоединение к домену в автономном режиме DirectAccess](DirectAccess-Offline-Domain-Join.md)  
> -   [Диагностика DirectAccess](Troubleshooting-DirectAccess.md)  
> -   [Развертывание одиночного сервера DirectAccess с помощью мастера начальной настройки](single-server-wizard/Deploy-a-Single-DirectAccess-Server-Using-the-Getting-Started-Wizard.md)  
> -   [Развертывание одного сервера DirectAccess с расширенными параметрами](single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md)  
> -   [Добавление DirectAccess в существующее развертывание удаленного доступа (VPN)](add-to-existing-vpn/Add-DirectAccess-to-an-Existing-Remote-Access-VPN-Deployment.md)  
  
DirectAccess обеспечивает подключение для удаленных пользователей к ресурсам сети организации без использования традиционных подключений виртуальной частной сети (VPN). С помощью подключений DirectAccess удаленные клиентские компьютеры всегда подключены к вашей организации — нет необходимости, чтобы удаленные пользователи могли запускать и останавливать подключения, так как требуется VPN-подключения. Кроме того ИТ-администраторам управлять клиентскими компьютерами DirectAccess всякий раз, когда они выполняются, и Интернет.

>[!IMPORTANT]
>Не пытайтесь развертывание удаленного доступа на виртуальной машине \(виртуальной Машины\) в Microsoft Azure. С помощью удаленного доступа в Microsoft Azure не поддерживается. Нельзя использовать удаленный доступ на виртуальной Машине Azure, чтобы развернуть VPN, DirectAccess или средство удаленного доступа в Windows Server 2016 или более ранних версиях Windows Server. Дополнительные сведения см. в разделе [поддержка серверного программного обеспечения Майкрософт для виртуальных машин Microsoft Azure](https://support.microsoft.com/help/2721672/microsoft-server-software-support-for-microsoft-azure-virtual-machines).
  
DirectAccess обеспечивает поддержку только для клиентов, присоединенных к домену, которые включают поддержку операционной системы для DirectAccess.  
  
Поддерживают следующие операционные системы сервера DirectAccess.  
  
-   Вы можете развернуть все версии Windows Server 2016, как клиент DirectAccess или сервера DirectAccess.  
  
-   Вы можете развернуть все версии Windows Server 2012 R2, как клиент DirectAccess или сервера DirectAccess.  
  
-   Вы можете развернуть все версии Windows Server 2012, как клиент DirectAccess или сервера DirectAccess.  
  
-   Вы можете развернуть все версии Windows Server 2008 R2, как клиент DirectAccess или сервера DirectAccess.  
  
Следующие клиентские операционные системы поддерживают DirectAccess.  
  
-   Windows 10 Корпоративная  
  
-   Enterprise 2015 долгосрочной перспективе Windows 10 Servicing Branch (LTSB)  
  
-   Windows 8 и 8.1 Enterprise  
  
-   Windows 7 Максимальная  
  
-   Windows 7 Корпоративная
