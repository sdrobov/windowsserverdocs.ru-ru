---
title: Настройка пересылки DNS и доверия домена
ms.custom: na
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 5d8ffe82065caeee27c5d13f5243f13addc6c325
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386738"
---
# <a name="configure-dns-forwarding-in-the-hgs-domain-and-a-one-way-trust-with-the-fabric-domain"></a>Настройка пересылки DNS в домене HGS и одностороннее отношение доверия с доменом структуры

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

>[!IMPORTANT]
>Режим AD является устаревшим, начиная с Windows Server 2019. Для сред, в которых невозможно подтвердить аттестацию доверенного платформенного модуля, настройте [аттестацию ключа узла](guarded-fabric-initialize-hgs-key-mode.md). Аттестация ключа узла обеспечивает аналогичные гарантии в режиме AD и проще в настройке. 

Выполните следующие действия, чтобы настроить пересылку DNS и установить одностороннее отношение доверия с доменом структуры. Эти действия позволяют службе HGS размещать контроллеры домена структуры и проверять членство в группе узлов Hyper-V.

1.  Выполните следующую команду в сеансе PowerShell с повышенными привилегиями, чтобы настроить пересылку DNS. Замените fabrikam.com именем домена структуры и введите IP-адреса DNS-серверов в домене Fabric. Для повышения доступности наведите указатель на более одного DNS-сервера.

    ```powershell
    Add-DnsServerConditionalForwarderZone -Name "fabrikam.com" -ReplicationScope "Forest" -MasterServers <DNSserverAddress1>, <DNSserverAddress2>
    ```

2.  Чтобы создать одностороннее доверие лесов, выполните следующую команду в командной строке с повышенными привилегиями:

    Замените `bastion.local` именем домена HGS и `fabrikam.com` именем домена структуры. Укажите пароль администратора домена структуры.

        netdom trust bastion.local /domain:fabrikam.com /userD:fabrikam.com\Administrator /passwordD:<password> /add

## <a name="next-step"></a>Дальнейшие действия 

> [!div class="nextstepaction"]
> [Настройка HTTPS](guarded-fabric-configure-hgs-https.md)
