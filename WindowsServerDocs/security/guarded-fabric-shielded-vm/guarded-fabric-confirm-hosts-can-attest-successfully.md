---
title: Подтвердите подтвердят защищенных узлов
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 7485796b-b840-4678-9b33-89e9710fbbc7
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 02/05/2019
ms.openlocfilehash: 87878eba785c0e1cc50454a74b2af4a159e88e12
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66443660"
---
# <a name="confirm-guarded-hosts-can-attest"></a>Подтвердите подтвердят защищенных узлов 

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016


Администратор структуры необходимо убедиться, что узлы Hyper-V можно выполнить как защищенных узлов. Выполните следующие действия на по крайней мере один защищенный узел.

1.  Если вы еще не установили роль Hyper-V и компонент поддержку защиты узла Hyper-V, установите их с помощью следующей команды:

        Install-WindowsFeature Hyper-V, HostGuardian -IncludeManagementTools -Restart

2.  Убедитесь, что на узле Hyper-V, можно разрешить имя HGS DNS и имеет сетевое подключение к порту 80 (или 443, если вы настроили HTTPS) на сервер HGS.

2.  Настройка защиты ведущего приложения и URL-адреса аттестации:

    - **С помощью Windows PowerShell**: Можно настроить защиту ключа и URL-адреса аттестации, выполнив следующую команду в консоль Windows PowerShell с повышенными привилегиями. Для &lt;полное доменное имя&gt;, используйте полное доменное имя (FQDN) кластера HGS (например, hgs.bastion.local или попросите администратора HGS для запуска **Get HgsServer** командлет на сервере HGS, чтобы получить URL-адреса).

        `Set-HgsClientConfiguration -AttestationServerUrl 'http://<FQDN>/Attestation' -KeyProtectionServerUrl 'http://<FQDN>/KeyProtection'`

        Чтобы настроить резервный сервер HGS, повторите эту команду и укажите резервные URL-адреса для защиты ключа и аттестации. Дополнительные сведения см. в разделе [конфигурация резервирования](guarded-fabric-manage-branch-office.md#fallback-configuration). 

    - **С помощью VMM**: Если вы используете System Center 2016 — Virtual Machine Manager (VMM) в VMM можно настроить аттестации и URL-адреса для защиты ключа. Дополнительные сведения см. в разделе [Настройка глобальных параметров HGS](https://technet.microsoft.com/system-center-docs/vmm/scenario/guarded-hosts#configure-global-hgs-settings) в **Подготовка защищенных узлов в VMM**.
    
    >**Примечания**
    > - Если администратор HGS [включения протокола HTTPS на сервере HGS](guarded-fabric-configure-hgs-https.md), начать URL-адресов с `https://`.
    > - Если администратор HGS включить HTTPS на сервере HGS и использовать самозаверяющий сертификат, необходимо импортировать сертификат в хранилище доверенных корневых центров сертификации на каждом узле. Чтобы сделать это, выполните следующую команду на каждом узле:<br>
        `Import-Certificate -FilePath "C:\temp\HttpsCertificate.cer" -CertStoreLocation Cert:\LocalMachine\Root`
    
3.  Чтобы инициировать попытки аттестации на узле и просматривать состояние аттестации, выполните следующую команду:

        Get-HgsClientConfiguration

    Выходные данные команды указывает ли узел передан аттестации и теперь защищены. Если `IsHostGuarded` не возвращает **True**, вы можете запустить средство диагностики HGS [Get-HgsTrace](https://technet.microsoft.com/library/mt718831.aspx), для расследования. Чтобы запустить диагностику, введите следующую команду в строке с повышенными привилегиями Windows PowerShell на узле:

        Get-HgsTrace -RunDiagnostics -Detailed

    > [!IMPORTANT]
    > Если вы используете Windows Server 2019 или Windows 10, версия 1809 и при использовании политики целостности кода, `Get-HgsTrace` возвращает ошибку для **Active политики целостности кода** диагностики.
    > Этот результат можно игнорировать при только сбои диагностики.

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Развертывание экранированных виртуальных машин](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)

## <a name="see-also"></a>См. также

- [Развертывание службы защиты узла (HGS)](guarded-fabric-deploying-hgs-overview.md)
- [Развертывание экранированных виртуальных машин](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)

