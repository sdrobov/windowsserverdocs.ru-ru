---
ms.assetid: 7671e0c9-faf0-40de-808a-62f54645f891
title: Обновление до AD FS в Windows Server 2016
description: ''
author: billmath
manager: femila
ms.date: 04/09/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 6f3cdc34ee03fab1a8fb1d42ebed2d2f76e2618d
ms.sourcegitcommit: ccc802338b163abdad2e53b55f39addcfea04603
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66687413"
---
# <a name="upgrading-to-ad-fs-in-windows-server-2016-using-a-wid-database"></a>Обновление до AD FS в Windows Server 2016 с помощью базы данных WID


> [!NOTE]  
> Только начинающиеся в определенный период времени, запланированные для завершения обновления. Не рекомендуется хранить AD FS в смешанном режиме в течение продолжительного периода времени, оставляя AD FS в смешанном режиме может вызвать проблемы с фермой.

## <a name="upgrading-a-windows-server-2012-r2-or-2016-ad-fs-farm-to-windows-server-2019"></a>Обновление до Windows Server 2019 Windows Server 2012 R2 или 2016 AD FS фермы
Следующий документ показывает, как для обновления фермы AD FS для AD FS в Windows Server 2019 при использовании Внутренней базой данных Windows.  

### <a name="ad-fs-farm-behavior-levels-fbl"></a>AD FS фермы поведение уровни (FBL)  
В AD FS для Windows Server 2016 появилась на уровне поведения фермы (FBL). Это параметр уровня фермы, который определяет, что можно использовать функции AD FS фермы.

В следующей таблице перечислены значения FBL версией Windows Server:

| Версия Windows Server  | FBL | Имя базы данных конфигурации AD FS |
| ------------- | ------------- | ------------- |
| 2012 R2  | 1  | AdfsConfiguration |
| 2016  | 3  | AdfsConfigurationV3 |
| 2019 г.  | 4  | AdfsConfigurationV4 |

> [!NOTE]  
> Обновление FBL создает новую базу данных конфигурации AD FS.  См. в таблице выше имена базы данных конфигурации для каждой версии Windows Server AD FS и FBL значение

### <a name="new-vs-upgraded-farms"></a>Цена новой подписки и обновлен ферм
По умолчанию FBL в новой ферме AD FS совпадает со значением для версии Windows Server для первого узла фермы установлен.  

Сервер AD FS более поздней версии может быть присоединен к ферме AD FS 2012 R2 или 2016 и фермы будет работать с тем же FBL как существующие узлы. При наличии нескольких версий Windows Server, работающие в одной и той же ферме значение FBL самую раннюю версию по, считается, что ферма быть «mixed». Тем не менее вы не сможете воспользоваться преимуществами возможностей этих более поздних версий, пока не возникает FBL. С помощью смешанных фермы:  

-   Администраторы могут добавлять новые серверы федерации Windows Server 2019 существующие Windows Server 2012 R2 или 2016 фермы. В результате ферма находится в «смешанный режим» и работает на том же уровне поведения фермы, что и исходная ферма. Для обеспечения согласованного поведения в ферме, нельзя настроить или использовать функции более новые версии Windows Server AD FS.  

- Перед FBL может возникнуть, администраторам необходимо удалить узлы из предыдущих версий Windows Server AD FS из фермы.  В случае ферме внутренней базы данных Windows Обратите внимание, что это один из новых tp серверов федерации Windows Server 2019 обновлен до роли основного узла в ферме.

-   Если все серверы федерации в ферме одну и ту же версию Windows Server, могут вызываться FBL.  Таким образом все новые функции AD FS Windows Server 2019 можно затем настроить и использовать.

Имейте в виду, что в режиме смешанной фермы фермы AD FS не может быть любой новые компоненты или функциональные возможности, представленные в AD FS в Windows Server 2019. Это означает, что организаций, которые хотят опробовать новые компоненты невозможно, пока не возникает FBL. Поэтому если организации требуется для тестирования новых функций до rasing FBL, необходимо будет развернуть отдельный ферму для этого.  

В оставшейся части является документе описываются действия по добавлению сервера федерации Windows Server 2019 Windows Server 2016 или в среде 2012 R2 и затем увеличивать их FBL для Windows Server 2019. Эти действия были выполнены в тестовой среде, описанные на следующей схеме архитектуры.  

> [!NOTE]  
> Прежде чем можно переместить в AD FS в Windows Server 2019 FBL, необходимо удалить все из Windows Server 2016 и 2012 R2 узлов. Невозможно просто обновление Windows Server 2016 или 2012 R2 ОС до Windows Server 2019 и его становятся узлами 2019 г. Необходимо будет удалить его и замените его на новый узел 2019 г.



##### <a name="to-upgrade-your-ad-fs-farm-to-windows-server-2019-farm-behavior-level"></a>Для обновления фермы AD FS на уровне поведения фермы сервера Windows Server 2019 г.  

1.  С помощью диспетчера сервера, установите роль служб федерации Active Directory на 2019 г. Windows Server

2.  С помощью мастера настройки AD FS, присоедините новый сервер Windows Server 2019 в существующую ферму AD FS.  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_1.png)  

3.  На сервере федерации Windows Server 2019 откройте оснастку управления AD FS. Обратите внимание на то, что возможности управления недоступны, так как этому серверу федерации не является основным сервером.  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_3.png)  

4.  На сервере Windows Server 2019 откройте командное окно PowerShell с повышенными правами и выполните следующий командлет: `Set-AdfsSyncProperties -Role PrimaryComputer`

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_4.png)  

5.  На сервере AD FS, который ранее был настроен в качестве основного откройте командное окно PowerShell с повышенными правами и выполните следующий командлет: `Set-AdfsSyncProperties -Role SecondaryComputer -PrimaryComputerName {FQDN} `

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_5.png)  

6.  Теперь на сервере федерации Windows Server 2016 откройте оснастку управления AD FS. Обратите внимание, что теперь все возможности администрирования отображаются, поскольку основная роль была передана на этот сервер.  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_6.png)  

7.  Если при обновлении фермы AD FS 2012 R2 до 2016 или 2019 г., обновление фермы требуется схема AD быть минимум на уровне 85.  Чтобы обновить схему, установочный носитель с Windows Server 2016, откройте командную строку и перейдите в каталог support\adprep. Используйте следующую команду:  `adprep /forestprep`

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_7.png)  

    После выполнения `adprep/domainprep`
    >[!NOTE]
    >Перед запуском следующий шаг, убедитесь, что Windows Server является текущей, запустив из параметров обновления Windows. Продолжайте этот процесс, пока не перестанут требоваться обновления.
    >

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_8.png)  

8. Теперь на сервере Windows Server 2016 откройте PowerShell и выполните следующий командлет:
    >[!NOTE]
    > Все серверы 2012 R2 необходимо удалить из фермы перед выполнением следующего шага.

    `Invoke-AdfsFarmBehaviorLevelRaise`  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_9.png)  

9. Когда появится запрос, введите Y. После этого начнется повышение уровня. После завершения проверки вы сообщили успешно FBL.  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_10.png)  

10. Теперь если перейти на управление AD FS, вы увидите что были добавлены новые возможности для более поздней версии AD FS

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_12.png)  

11. Аналогичным образом, можно использовать командлет PowerShell: `Get-AdfsFarmInformation` показать текущее FBL.  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_13.png)  

12. Для обновления серверов WAP на последний уровень, на каждом прокси веб-приложения, перенастройте WAP, выполнив следующую команду PowerShell в окне с повышенными привилегиями:  
    ```powershell
    $trustcred = Get-Credential -Message "Enter Domain Administrator credentials"
    Install-WebApplicationProxy -CertificateThumbprint {SSLCert} -fsname fsname -FederationServiceTrustCredential $trustcred  
    ```
    Удалить старые серверы из кластера и сохранить только WAP серверы под управлением последней версии сервера, которые были перенастроены выше, выполнив следующий командлет Powershell.
    ```powershell
    Set-WebApplicationProxyConfiguration -ConnectedServersName WAPServerName1, WAPServerName2
    ```
    Проверьте конфигурацию WAP, выполнив Get-WebApplicationProxyConfiguration commmandlet. ConnectedServersName будет отражать сервера выполнять с помощью предыдущей команды.
    ```powershell
    Get-WebApplicationProxyConfiguration
    ```
    Чтобы обновить ConfigurationVersion WAP-серверы, запустите следующую команду Powershell.
    ```powershell
    Set-WebApplicationProxyConfiguration -UpgradeConfigurationVersion
    ```
    Это завершит обновление серверов WAP.
