---
title: Развертывание сертификата сервера
description: Этот раздел является частью руководства развертывание сервера сертификатов для развертывания беспроводных и проводных сетей 802.1 X
manager: brianlic
ms.topic: article
ms.assetid: 1ae4384b-f4e4-41e8-bc5f-9ac41953bca4
ms.prod: windows-server-threshold
ms.technology: networking
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 751c5c5958b3d06ae0f4b701e4d6e10a7fef19dc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858495"
---
# <a name="server-certificate-deployment"></a>Развертывание сертификата сервера

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Выполните следующие действия для установки корневого центра сертификации (ЦС) предприятия и развертывание сертификатов сервера для использования с PEAP и EAP.  
  
> [!IMPORTANT]  
> Перед установкой служб сертификатов Active Directory, необходимо имя компьютера, настройте компьютер для статического IP-адреса и присоединить компьютер к домену. После установки служб AD CS, нельзя изменить имя компьютера или членства в домене на компьютере, однако при необходимости можно изменить IP-адрес. Дополнительные сведения о выполнении этих задач см. в разделе Windows Server&reg; 2016 [руководство по основной сети](../../Core-Network-Guide.md).  

  
-   [Установить Web Server WEB1](../../../core-network-guide/cncg/server-certs/Install-the-Web-Server-WEB1.md)  
  
-   [Создайте запись псевдонима (CNAME) в DNS для WEB1](../../../core-network-guide/cncg/server-certs/Create-an-Alias-CNAME-Record-in-DNS-for-WEB1.md)  
  
-   [Настройка WEB1 для распространения списков отзыва сертификатов (CRL)](../../../core-network-guide/cncg/server-certs/Configure-WEB1-to-Distribute-Certificate-Revocation-Lists.md)  
  
-   [Подготовка CAPolicy inf-файла](../../../core-network-guide/cncg/server-certs/Prepare-the-CAPolicy-inf-File.md)  
  
-   [Установка центра сертификации](../../../core-network-guide/cncg/server-certs/Install-the-Certification-Authority.md)  
  
-   [Настройка расширений CDP и AIA на CA1](../../../core-network-guide/cncg/server-certs/Configure-the-CDP-and-AIA-Extensions-on-CA1.md)  
  
-   [Скопируйте сертификат ЦС и списка отзыва Сертификатов в виртуальный каталог](../../../core-network-guide/cncg/server-certs/Copy-the-CA-Certificate-and-CRL-to-the-Virtual-Directory.md)  
  
-   [Настройка шаблона сертификата сервера](../../../core-network-guide/cncg/server-certs/Configure-the-Server-Certificate-Template.md)  
  
-   [Настройка автоматической регистрации сертификатов сервера](../../../core-network-guide/cncg/server-certs/Configure-Server-Certificate-Autoenrollment.md)  
  
-   [Обновление групповой политики](../../../core-network-guide/cncg/server-certs/Refresh-Group-Policy.md)  
  
-   [Проверка регистрации сервера сертификат сервера](../../../core-network-guide/cncg/server-certs/Verify-Server-Enrollment-of-a-Server-Certificate.md)  
  
> [!NOTE]  
> Процедуры, описанные в этом руководстве не содержатся инструкции для случаев, в котором **контроль учетных записей пользователей** откроется диалоговое окно, запрашивающее разрешение продолжать. Если во время выполнения процедур, описанных в данном руководстве, отображается это диалоговое окно, и если оно отображается в ответ на ваше действие, нажмите кнопку **Продолжить**.  
  


