---
title: Настройте перенаправление запросов DNS и доверия домена
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 3f9083d749ba9251ba47ecb64b7cb3d7c6290f1d
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66443768"
---
# <a name="configure-dns-forwarding-in-the-hgs-domain-and-a-one-way-trust-with-the-fabric-domain"></a>Настроить переадресацию DNS в домене HGS и одностороннее отношение доверия с доменом fabric

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

>[!IMPORTANT]
>Режим AD является устаревшим, начиная с Windows Server 2019. Для сред, где аттестацию доверенного платформенного МОДУЛЯ не поддерживается, Настройка [размещения Аттестация ключей](guarded-fabric-initialize-hgs-key-mode.md). Аттестация ключей узла обеспечивает аналогичный уверенность в режим AD и проще в настройке. 

Настроить перенаправление запросов DNS и установите одностороннее отношение доверия с доменом fabric, следуйте инструкциям ниже. Эти шаги позволяют HGS, чтобы найти структуре контроллеров домена и проверки членства в группе узлов Hyper-V.

1.  Выполните следующую команду в сеанс PowerShell с повышенными правами для настройки перенаправления DNS. Замените на имя структуры домена fabrikam.com и введите IP-адреса DNS-серверов в домене fabric. Для повышения уровня доступности укажите более одного DNS-сервера.

    ```powershell
    Add-DnsServerConditionalForwarderZone -Name "fabrikam.com" -ReplicationScope "Forest" -MasterServers <DNSserverAddress1>, <DNSserverAddress2>
    ```

2.  Создание доверия леса односторонней, выполните следующую команду в командной строке с повышенными правами:

    Замените `bastion.local` с именем домена HGS и `fabrikam.com` с именем fabric домена. Введите пароль для администратора домена fabric.

        netdom trust bastion.local /domain:fabrikam.com /userD:fabrikam.com\Administrator /passwordD:<password> /add

## <a name="next-step"></a>Дальнейшие действия 

> [!div class="nextstepaction"]
> [Настройка HTTPS](guarded-fabric-configure-hgs-https.md)
