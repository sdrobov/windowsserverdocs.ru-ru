---
title: Развертывание сертификатов сервера
description: Этот раздел входит руководство развертывание сервера сертификатов для развертывания беспроводных и проводных сетей 802.1 X
manager: brianlic
ms.topic: article
ms.assetid: 1ae4384b-f4e4-41e8-bc5f-9ac41953bca4
ms.prod: windows-server-threshold
ms.technology: networking
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 4a10a9bafa6a8c9fddecac799ec8e837bf339d0e
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="server-certificate-deployment"></a>Развертывание сертификатов сервера

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Выполните следующие действия для установки корневого центра сертификации (ЦС) предприятия и развертывание сертификатов сервера для использования с PEAP и EAP.  
  
> [!IMPORTANT]  
> Перед установкой служб сертификатов Active Directory необходимо имя компьютера, настройте статический IP-адрес компьютера и присоединения компьютера к домену. После установки служб AD CS, не может изменить имя компьютера или членства в домене, на компьютере, однако при необходимости можно изменить IP-адрес. Дополнительные сведения о выполнении этих задач см. в разделе Windows Server&reg; 2016 [руководство по основной сети](../../Core-Network-Guide.md).  

  
-   [Установка веб-сервера WEB1](../../../core-network-guide/cncg/server-certs/Install-the-Web-Server-WEB1.md)  
  
-   [Создание записи псевдонима (CNAME) в DNS для WEB1](../../../core-network-guide/cncg/server-certs/Create-an-Alias-CNAME-Record-in-DNS-for-WEB1.md)  
  
-   [Настройка WEB1 для распространения списков отзыва сертификатов (CRL)](../../../core-network-guide/cncg/server-certs/Configure-WEB1-to-Distribute-Certificate-Revocation-Lists.md)  
  
-   [Подготовка CAPolicy inf-файла](../../../core-network-guide/cncg/server-certs/Prepare-the-CAPolicy-inf-File.md)  
  
-   [Установка центра сертификации](../../../core-network-guide/cncg/server-certs/Install-the-Certification-Authority.md)  
  
-   [Настройка расширений CDP и AIA в CA1](../../../core-network-guide/cncg/server-certs/Configure-the-CDP-and-AIA-Extensions-on-CA1.md)  
  
-   [Скопируйте сертификат ЦС и списка отзыва Сертификатов в виртуальный каталог](../../../core-network-guide/cncg/server-certs/Copy-the-CA-Certificate-and-CRL-to-the-Virtual-Directory.md)  
  
-   [Настройка шаблона сертификата сервера](../../../core-network-guide/cncg/server-certs/Configure-the-Server-Certificate-Template.md)  
  
-   [Настройка автоматической регистрации сертификата сервера](../../../core-network-guide/cncg/server-certs/Configure-Server-Certificate-Autoenrollment.md)  
  
-   [Обновление групповой политики](../../../core-network-guide/cncg/server-certs/Refresh-Group-Policy.md)  
  
-   [Проверка регистрации сертификата сервера](../../../core-network-guide/cncg/server-certs/Verify-Server-Enrollment-of-a-Server-Certificate.md)  
  
> [!NOTE]  
> Процедуры, описанные в этом руководстве не содержатся инструкции для случаев, в котором **контроля учетных записей** откроется диалоговое окно, чтобы запросить разрешение на продолжение. Если это диалоговое окно выполнения процедуры, описанные в данном руководстве, а если диалогового окна в ответ на ваше действие, нажмите кнопку **Продолжить**.  
  


