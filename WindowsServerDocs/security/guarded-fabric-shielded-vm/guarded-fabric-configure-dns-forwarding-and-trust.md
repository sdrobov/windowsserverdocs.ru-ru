---
title: Настройка пересылки DNS и доверия домена
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: e8ecabe9f98bda1442fb127198be665b693c853e
ms.sourcegitcommit: acfdb7b2ad283d74f526972b47c371de903d2a3d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2020
ms.locfileid: "87769281"
---
# <a name="configure-dns-forwarding-in-the-hgs-domain-and-a-one-way-trust-with-the-fabric-domain"></a>Настройка пересылки DNS в домене HGS и одностороннее отношение доверия с доменом структуры

>Применяется к: Windows Server (Semi-Annual Channel), Windows Server 2016

>[!IMPORTANT]
>Режим AD является устаревшим, начиная с Windows Server 2019. Для сред, в которых невозможно подтвердить аттестацию доверенного платформенного модуля, настройте [аттестацию ключа узла](guarded-fabric-initialize-hgs-key-mode.md). Аттестация ключа узла обеспечивает аналогичные гарантии в режиме AD и проще в настройке.

Выполните следующие действия, чтобы настроить пересылку DNS и установить одностороннее отношение доверия с доменом структуры. Эти действия позволяют службе HGS размещать контроллеры домена структуры и проверять членство в группе узлов Hyper-V.

1.  Выполните следующую команду в сеансе PowerShell с повышенными привилегиями, чтобы настроить пересылку DNS. Замените fabrikam.com именем домена структуры и введите IP-адреса DNS-серверов в домене Fabric. Для повышения доступности наведите указатель на более одного DNS-сервера.

    ```powershell
    Add-DnsServerConditionalForwarderZone -Name "fabrikam.com" -ReplicationScope "Forest" -MasterServers <DNSserverAddress1>, <DNSserverAddress2>
    ```

2.  Чтобы создать одностороннее доверие лесов, выполните следующую команду в командной строке с повышенными привилегиями:

    Замените `bastion.local` именем домена HGS и `fabrikam.com` именем домена структуры. Укажите пароль администратора домена структуры.

    ```powershell
    netdom trust bastion.local /domain:fabrikam.com /userD:fabrikam.com\Administrator /passwordD:<password> /add
    ```

## <a name="next-step"></a>Следующий шаг

> [!div class="nextstepaction"]
> [Настройка HTTPS](guarded-fabric-configure-hgs-https.md)
