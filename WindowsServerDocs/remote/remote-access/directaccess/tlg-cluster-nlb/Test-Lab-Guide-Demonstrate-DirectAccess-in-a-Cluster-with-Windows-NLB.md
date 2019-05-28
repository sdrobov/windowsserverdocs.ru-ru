---
title: 'Руководство по лаборатории тестирования: демонстрация DirectAccess в кластере с балансировкой сетевой Нагрузки Windows'
description: Этот раздел входит руководство по лаборатории тестирования — продемонстрировать DirectAccess в кластере с помощью Windows NLB для Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: db15dcf5-4d64-48d7-818a-06c2839e1289
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 910afa78553c828aff954f7677869569068198aa
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59869525"
---
# <a name="test-lab-guide-demonstrate-directaccess-in-a-cluster-with-windows-nlb"></a>Руководство по лаборатории тестирования: Демонстрация DirectAccess в кластере с балансировкой сетевой Нагрузки Windows

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Удаленный доступ — это роль сервера в Windows Server 2016, Windows Server 2012 R2 и Windows Server 2012 операционных систем, позволяющая удаленным пользователям безопасный доступ к внутренним сетевым ресурсам с помощью DirectAccess или RRAS VPN. В этом руководстве содержатся пошаговые инструкции по расширению [руководство по лаборатории тестирования: Демонстрация настройки одного сервера DirectAccess в смешанной IPv4 и IPv6](https://go.microsoft.com/fwlink/p/?LinkId=237004) для демонстрации балансировки сетевой нагрузки DirectAccess и конфигурации кластера.  
  
## <a name="about-this-guide"></a>Об этом руководстве  
В этом руководстве приводятся инструкции по настройке и демонстрации удаленного доступа с использованием шести серверов и двух клиентских компьютеров. Завершенная лаборатория тестирования удаленного доступа с балансировкой сетевой нагрузки имитирует интрасеть, Интернет и домашнюю сеть, а также демонстрирует функциональные возможности удаленного доступа в различных сценариях подключения к Интернету.  
  
> [!IMPORTANT]  
> Эта лаборатория является экспериментом, в котором используется минимальное количество компьютеров. Конфигурация, используемая в этом руководстве, приводится только для целей лаборатории тестирования, она не предназначена для использования в рабочей среде.  
  
## <a name="KnownIssues"></a>Известные проблемы  
Ниже приводятся известные проблемы, возникающие при настройке сценария кластера.  
  
-   После настройки DirectAccess в развертывании с поддержкой только IPv4 с одним сетевым адаптером и после автоматической настройки в сетевом адаптере DNS64 по умолчанию (IPv6-адрес, который содержит «: 3333::») попытка включить балансировку нагрузки в консоли управления удаленным доступом приводит к запросу на ввод DIP IPv6. Если указать DIP IPv6, после нажатия кнопки **Зафиксировать** возникает ошибка: Неверный параметр.  
  
    Чтобы решить эту проблему, выполните указанные ниже действия.  
  
    1.  Скачайте сценарии резервного копирования и восстановления из раздела [Настройка резервного копирования и восстановления конфигурации удаленного доступа](https://gallery.technet.microsoft.com/Back-up-and-Restore-Remote-e157e6a6).  
  
    2.  Резервное копирование объектов групповой политики удаленного доступа с помощью загруженного сценария Backup-RemoteAccess.ps1  
  
    3.  Попытайтесь включить балансировку нагрузки, пока не возникнет ошибка. В диалоговом окне "Включение балансировки нагрузки" разверните область сведений, щелкните ее правой кнопкой мыши и выберите команду **Копировать сценарий**.  
  
    4.  Откройте Блокнот и вставьте содержимое буфера обмена. Пример:  
  
        ```  
        Set-RemoteAccessLoadBalancer -InternetDedicatedIPAddress @('10.244.4.19/255.255.255.0','fdc4:29bd:abde:3333::2/128') -InternetVirtualIPAddress @('fdc4:29bd:abde:3333::1/128', '10.244.4.21/255.255.255.0') -ComputerName 'DA1.domain1.corp.contoso.com' -Verbose  
        ```  
  
    5.  Закройте все открытые диалоговые окна удаленного доступа и закройте консоль управления удаленным доступом.  
  
    6.  Измените вставленный текст и удалите IPv6-адреса. Пример:  
  
        ```  
        Set-RemoteAccessLoadBalancer -InternetDedicatedIPAddress @('10.244.4.19/255.255.255.0') -InternetVirtualIPAddress @('10.244.4.21/255.255.255.0') -ComputerName 'DA1.domain1.corp.contoso.com' -Verbose  
        ```  
  
    7.  В окне PowerShell с повышенными привилегиями выполните команду из предыдущего шага.  
  
    8.  Если командлет завершается с ошибкой (ошибка при выполнении, а не из-за неправильных входных значений), выполните команду Restore-RemoteAccess.ps1 и следуйте инструкциям, чтобы убедиться, что целостность исходной конфигурации не нарушена.  
  
    9. Теперь снова откройте консоль управления удаленным доступом.  
  

