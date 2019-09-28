---
title: Подтверждение аттестации защищенных узлов
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: 7485796b-b840-4678-9b33-89e9710fbbc7
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 02/05/2019
ms.openlocfilehash: bc047bbc23f4edfbbd77fb3e2d7258241d1f19d0
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386699"
---
# <a name="confirm-guarded-hosts-can-attest"></a>Подтверждение аттестации защищенных узлов 

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016


Администратор структуры должен подтвердить, что узлы Hyper-V могут работать как защищенные узлы. Выполните следующие действия по крайней мере на одном защищенном узле:

1.  Если вы еще не установили роль Hyper-V и службу защиты узла Hyper-V, установите их с помощью следующей команды:

        Install-WindowsFeature Hyper-V, HostGuardian -IncludeManagementTools -Restart

2.  Убедитесь, что узел Hyper-V может разрешить DNS-имя HGS и сетевое подключение, чтобы получить доступ к порту 80 (или 443, если вы настроили HTTPS) на сервере HGS.

2.  Настройте URL-адреса защиты ключа и аттестации узла:

    - **С помощью Windows PowerShell**: URL-адреса защиты ключа и аттестации можно настроить, выполнив следующую команду в консоли Windows PowerShell с повышенными привилегиями. Для @no__t 0FQDN @ no__t-1 используйте полное доменное имя кластера HGS (например, HGS. бастиона. local) или попросите администратора HGS запустить командлет **Get-HgsServer** на сервере HGS для получения URL-адресов.

        `Set-HgsClientConfiguration -AttestationServerUrl 'http://<FQDN>/Attestation' -KeyProtectionServerUrl 'http://<FQDN>/KeyProtection'`

        Чтобы настроить резервный сервер HGS, повторите эту команду и укажите резервные URL-адреса для служб защиты и аттестации ключей. Дополнительные сведения см. в разделе [резервная конфигурация](guarded-fabric-manage-branch-office.md#fallback-configuration). 

    - **Через VMM**: Если вы используете System Center 2016-Virtual Machine Manager (VMM), вы можете настроить URL-адреса аттестации и защиты ключей в VMM. Дополнительные сведения см. в статье [Настройка глобальных параметров HGS](https://technet.microsoft.com/system-center-docs/vmm/scenario/guarded-hosts#configure-global-hgs-settings) в разделе **подготавливать защищенные узлы в VMM**.
    
    >**Примечания**
    > - Если администратор HGS [включил протокол HTTPS на сервере HGS](guarded-fabric-configure-hgs-https.md), начните использовать URL-адреса с @no__t – 1.
    > - Если администратор HGS включил протокол HTTPS на сервере HGS и использовал самозаверяющий сертификат, необходимо импортировать сертификат в хранилище доверенных корневых центров сертификации на каждом узле. Для этого выполните следующую команду на каждом узле:<br>
        `Import-Certificate -FilePath "C:\temp\HttpsCertificate.cer" -CertStoreLocation Cert:\LocalMachine\Root`
    
3.  Чтобы инициировать попытку аттестации на узле и просмотреть состояние аттестации, выполните следующую команду:

        Get-HgsClientConfiguration

    Выходные данные команды указывают, прошел ли узел аттестацию, и теперь он защищен. Если `IsHostGuarded` не возвращает **значение true**, для изучения можно запустить средство диагностики HGS с помощью [Get-хгстраце](https://technet.microsoft.com/library/mt718831.aspx). Чтобы запустить диагностику, введите следующую команду в командной строке Windows PowerShell с повышенными привилегиями на узле:

        Get-HgsTrace -RunDiagnostics -Detailed

    > [!IMPORTANT]
    > Если вы используете Windows Server 2019 или Windows 10 версии 1809 и используете политики целостности кода, `Get-HgsTrace` возвращают ошибку для **активной диагностики политики целостности кода** .
    > Вы можете спокойно проигнорировать этот результат, если это единственный сбой диагностики.

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Развертывание экранированных виртуальных машин](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)

## <a name="see-also"></a>См. также

- [Развертывание службы защиты узла (HGS)](guarded-fabric-deploying-hgs-overview.md)
- [Развертывание экранированных виртуальных машин](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)

