---
title: Сетевой контроллер безопасности
description: Можно использовать в этом разделе описывается настройка безопасности для весь обмен данными между сетевой контроллер и другое программное обеспечение и устройства.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-sdn
ms.topic: article
ms.assetid: bc625de9-ee31-40a4-9ad2-7448bfbfb6e6
ms.author: pashort
author: shortpatti
ms.openlocfilehash: ab04d3f528beb037988e6390fe85ad9af219266b
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="network-controller-security"></a>Сетевой контроллер безопасности

Можно использовать в этом разделе описывается настройка безопасности для весь обмен данными между сетевой контроллер и другое программное обеспечение и устройства. 

>[!NOTE]
>Обзор сетевой контроллер см. в разделе [сетевой контроллер](../technologies/network-controller/network-controller.md).

Пути взаимодействия, которые можно защитить включают Северный связи на плоскости управления кластера обмен данными между сетевой контроллер \(VMs\) виртуальных машин в кластере и Южный связи на информационной панели.

1. **Северный связи**. Сетевой контроллер взаимодействует в плоскости управления с поддержкой SDN\ программным обеспечением управления, таких как Windows PowerShell и \(SCVMM\) System Center Virtual Machine Manager. Эти средства управления предоставляют возможность определить политики сети и создания цели состояния сети, для которой можно сравнить конфигурацию на фактические сети Фактическая конфигурация в четности с состоянием цели.

2. **Сетевой контроллер кластеру**. При настройке три или более виртуальных машин в качестве узлов кластера сетевой контроллер эти узлы взаимодействовать друг с другом. Это взаимодействие может быть связана с синхронизации и репликации данных между узлами или определенные связи между службами сетевого контроллера.

3.  **Южный связи**. Сетевой контроллер взаимодействует на информационной панели с инфраструктурой SDN и другие устройства, такие как подсистемы балансировки нагрузки программного обеспечения, шлюзы и хост-компьютеров. Сетевой контроллер можно использовать для настройки и управления этими устройствами Южный, чтобы они поддерживать состояние цели, настроенную для сети.

## <a name="northbound-communication"></a>Северный связи

Сетевой контроллер поддерживает проверку подлинности, авторизации и шифрования для обмена данными Северный. Следующие разделы содержат сведения о настройке этих параметров безопасности.

**Проверка подлинности**

При настройке проверки подлинности для связи с Северный сетевого контроллера позволяет сетевой контроллер узлов кластера и управления клиентами для проверки удостоверения устройства, с которым они связываются.

Сетевой контроллер поддерживает следующих трех режимов проверки подлинности между управления клиентами и узлами сетевого контроллера.

>[!Note]
>Если вы собираетесь выполнять развертывание сетевого контроллера с помощью System Center Virtual Machine Manager, только **Kerberos** режим поддерживается.

1. **Kerberos**. Проверки подлинности Kerberos можно использовать, когда оба клиента управления, например компьютер под управлением SCVMM и на всех узлах кластера сетевого контроллера присоединены к домену Active Directory с учетными записями домена, используемый для проверки подлинности.

2. **X509**. X509 — проверка подлинности на основе certificate\. Можно использовать X509 проверки подлинности, если для управления клиентами не присоединены к домену Active Directory. Чтобы использовать X509, необходимо регистрировать сертификаты на всех узлах кластера сетевой контроллер и управления клиентами, а все узлы и клиенты управления должны доверять сертификаты других пользователей.

3. **Нет**. Если выбрать этот режим, нет проверки подлинности, выполняемые между управления клиентами и сетевого контроллера. Этот режим предоставляется только для целей тестирования и не рекомендуется для использования в рабочей среде. 

Режим проверки подлинности для Северный взаимодействия можно настроить с помощью команды Windows PowerShell **установки NetworkController** с **допустимый** параметра. 

Дополнительные сведения см. в следующих разделах. 

- [Установка NetworkController](https://technet.microsoft.com/itpro/powershell/windows/network-controller/install-networkcontroller)
- [SET-NetworkController](https://technet.microsoft.com/itpro/powershell/windows/network-controller/set-networkcontroller)

**Авторизация**

При настройке авторизации для обмена данными Северный сетевого контроллера позволяет сетевой контроллер узлов кластера и управления клиентами, чтобы убедиться, что устройство, с которым они связываются является доверенным и имеет разрешение на участие в связи.

Для каждого режима проверки подлинности, поддерживаемых сетевой контроллер используются следующие методы авторизации.

1.  **Kerberos**. При использовании метода проверки подлинности Kerberos, необходимо определить пользователей и компьютеров, в которые разрешен обмен данными с сетевым контроллером, создание группы безопасности в Active Directory, а затем добавив авторизованные пользователи и компьютеры в группу. Вы можете настроить сетевого контроллера для использования группы безопасности для проверки подлинности с помощью **ClientSecurityGroup** параметр **установки NetworkController** команды Windows PowerShell. После установки сетевого контроллера можно изменить группу безопасности с помощью [набор NetworkController](https://technet.microsoft.com/itpro/powershell/windows/network-controller/set-networkcontroller) команду с параметром **- ClientSecurityGroup**. Если вы используете SCVMM, необходимо указать группы безопасности в качестве параметра во время развертывания.

2.  **X509**. При использовании X509 метода проверки подлинности, сетевой контроллер принимает только запросы от известные отпечатки сертификатов, для которого сетевой контроллер управления клиентами. Можно настроить с помощью этих отпечатки **ClientCertificateThumbprint** параметр **установки NetworkController** команды Windows PowerShell. Можно добавить другие отпечатки клиента в любое время с помощью **набор NetworkController** команды.

3.  **Нет**. Если выбрать этот режим, существует, авторизация не выполняется для попытки связи между управления клиентами и узлами сетевого контроллера. Этот режим предоставляется только для целей тестирования и не рекомендуется для использования в рабочей среде. 

Дополнительные сведения см. в следующих разделах. 

- [Установка NetworkController](https://technet.microsoft.com/itpro/powershell/windows/network-controller/install-networkcontroller)
- [SET-NetworkController](https://technet.microsoft.com/itpro/powershell/windows/network-controller/set-networkcontroller)

**Шифрование**

Северный используетсяя \(SSL\) протокола SSL для создания зашифрованного канала между управления клиентами и узлами сетевого контроллера. Шифрование SSL для взаимодействия Северный включает следующие требования.

- Все узлы сетевой контроллер должен иметь одинаковые сертификат, который в целях проверки подлинности сервера и клиента в расширениях \(EKU\) расширенного использования ключа. 

- URI, используется управление клиентами для обмена данными с сетевым контроллером должен быть имени субъекта сертификата. Имя субъекта сертификата должно содержать полное доменное имя (FQDN) или IP-адрес конечной точки REST сетевого контроллера.

- Сетевой контроллер узлов, находящихся в разных подсетях, имя субъекта свои сертификаты должны совпадать с значение, которое используется для **RestName** параметр в **установки NetworkController** команды Windows PowerShell. 

- SSL-сертификат должен быть доверенным все клиенты управления.

### <a name="ssl-certificate-enrollment-and-configuration"></a>Регистрация сертификатов SSL и конфигурации

Необходимо вручную зарегистрировать сертификат SSL на узлах сетевого контроллера.

После установки сертификата, можно настроить сетевого контроллера для использования сертификата с **- сертификата сервера** параметр **установки NetworkController** команды Windows PowerShell. Если вы уже установили сетевой контроллер, можно обновить конфигурацию в любое время с помощью **набор NetworkController** команды.

>[!NOTE]
>Если вы используете SCVMM, необходимо добавить сертификат как ресурс библиотеки. Дополнительные сведения см. в разделе [Настройка SDN сетевого контроллера в структуре VMM](https://technet.microsoft.com/system-center-docs/vmm/scenario/sdn-network-controller).

## <a name="network-controller-cluster-communication"></a>Сетевой контроллер кластеру.

Сетевой контроллер поддерживает проверку подлинности, авторизации и шифрования для обмена данными между узлами сетевого контроллера. Обмен данными превышает [Windows Communication Foundation](https://msdn.microsoft.com/library/ms731082.aspx) \(WCF\) и TCP.

Вы можете настроить этот режим с **ClusterAuthentication** параметр **установки NetworkControllerCluster** команды Windows PowerShell. 

Дополнительные сведения см. в разделе [установки NetworkControllerCluster](https://technet.microsoft.com/itpro/powershell/windows/network-controller/install-networkcontrollercluster).

**Проверка подлинности**

При настройке проверки подлинности для взаимодействия с кластером сетевого контроллера позволяет сетевой контроллер узлов кластера для проверки удостоверения других узлов, с которыми они связываются.

Сетевой контроллер поддерживает следующих трех режимов проверки подлинности между узлами сетевого контроллера.

>[!NOTE]
>Если развертывание сетевого контроллера с помощью SCVMM только **Kerberos** режим поддерживается.

1. **Kerberos**. После присоединения к домену Active Directory на всех узлах кластера сетевого контроллера с учетными записями домена, используемый для проверки подлинности, можно использовать проверку подлинности Kerberos.

2. **X509**. X509 — проверка подлинности на основе certificate\. Можно использовать X509 проверки подлинности, когда узлы кластера сетевой контроллер не присоединены к домену Active Directory. Чтобы использовать X509, необходимо регистрировать сертификаты на все узлы кластера сетевого контроллера, и все узлы должны доверять сертификатам. Кроме того имя субъекта сертификатов, зарегистрированных на каждом узле должен быть так же, как DNS-имя узла.

3. **Нет**. Если выбрать этот режим, нет выполнять между узлами сетевой контроллер проверки подлинности. Этот режим предоставляется только для целей тестирования и не рекомендуется для использования в рабочей среде.

**Авторизация**

При настройке авторизации для взаимодействия с кластером сетевого контроллера позволяет сетевой контроллер узлов кластера, убедитесь, что доверенных узлов, с которыми они обмениваются данными и иметь разрешение на участие в связи.

Для каждого режима проверки подлинности, поддерживаемых сетевой контроллер используются следующие методы авторизации.

1. **Kerberos**. Сетевой контроллер узлов принимать запросы связи только с других учетных записей компьютера сетевого контроллера. Можно настроить эти учетные записи, при развертывании сетевого контроллера с помощью **имя** параметр [New-NetworkControllerNodeObject](https://technet.microsoft.com/itpro/powershell/windows/network-controller/new-networkcontrollernodeobject) команды Windows PowerShell.

2. **X509**. Сетевой контроллер узлов принимать запросы связи только с других учетных записей компьютера сетевого контроллера. Можно настроить эти учетные записи, при развертывании сетевого контроллера с помощью **имя** параметр [New-NetworkControllerNodeObject](https://technet.microsoft.com/itpro/powershell/windows/network-controller/new-networkcontrollernodeobject) команды Windows PowerShell.

3. **Нет**. Если выбрать этот режим, существует, авторизация не выполняется между узлами сетевого контроллера. Этот режим предоставляется только для целей тестирования и не рекомендуется для использования в рабочей среде.

**Шифрование**

Связь между узлами сетевой контроллер зашифрован с использованием шифрование на уровне транспорта WCF. Эта форма шифрования используется в том случае, когда методы проверки подлинности и авторизации, Kerberos или X509 сертификаты. Дополнительные сведения см. в следующих разделах.

- [Как: защиты службы с учетными данными Windows](https://msdn.microsoft.com/library/ms734673.aspx)
- [Как: защиты службы с сертификатами X.509](https://msdn.microsoft.com/library/ms788968.aspx).

## <a name="southbound-communication"></a>Южный связи

Сетевой контроллер взаимодействует с различными типами устройств для Южный связи. Эти взаимодействия использовать разные протоколы. По этой причине существуют различные требования для проверки подлинности, авторизации и шифрования, в зависимости от типа устройства и протокол, используемый сетевым контроллером для связи с устройством.

Ниже приведены сведения о взаимодействии сетевого контроллера с различных устройств Южный.

| Южный устройства или службы | Протокол              | Проверки подлинности    |
|---------------------------|-----------------------|------------------------|
| Балансировка нагрузки программного обеспечения    | WCF (Мультиплексирование) TCP (узел) | Сертификаты           |
| Брандмауэр                  | OVSDB                 | Сертификаты           |
| Шлюз                   | WinRM                 | Kerberos, сертификаты |
| Виртуальные сети        | OVSDB WCF            | Сертификаты           |
| Определенные пользователем маршрутизации      | OVSDB                 | Сертификаты           |

Для каждого из этих протоколов в следующем разделе описывается механизм обмена данными.

**Проверка подлинности**

Южный связи используются следующие протоколы и методы проверки подлинности.

1. **WCF/TCP/OVSDB**. Для этих протоколов проверки подлинности выполняется с помощью X509 сертификаты. Сетевой контроллер и балансировку нагрузки программного обеспечения \(SLB\) одноранговый элемент Multiplexer \ (MUX\) или хост-компьютеры представить свои сертификаты друг с другом для взаимной проверки подлинности. Каждый из сертификатов должны доверять удаленным компьютером.

    Для Южный проверки подлинности можно использовать один и тот же сертификат SSL, настроенный для шифрования обмена данными с клиентами Северный. Также необходимо настроить сертификат на SLB MUX и узла устройств. Имя субъекта сертификата должно быть такой же, как DNS-имя устройства.

2. **WinRM**. Для этого протокола проверки подлинности выполняется с помощью Kerberos \ (для machines\ присоединен к домену) и с помощью сертификатов \ (для объединенных machines\ не входящих в домен).

**Авторизация**

Южный связи используются следующие протоколы и методы авторизации.

1. **TCP-порт WCF**. Для этих протоколов авторизации основана на имя субъекта объекта однорангового элемента. Сетевой контроллер хранит DNS-имя устройства однорангового элемента и использует его для авторизации. Этот DNS-имя должно соответствовать имени субъекта устройства в сертификате. Аналогичным образом сетевой контроллер сертификата должно совпадать с именем сетевой контроллер DNS, хранятся на устройстве однорангового элемента.

2. **WinRM**. Если используется Kerberos, учетной записи клиента WinRM должен присутствовать в предопределенной группе в Active Directory или в группе локальных администраторов на сервере. Если используются сертификаты, клиент предоставляет сертификат, чтобы сервер, на авторизацию сервера с помощью имени субъекта и издателя, и сервер использует учетную запись пользователя, сопоставленный для выполнения проверки подлинности.

3.  **OVSDB**. Отсутствует авторизация не предоставляется для этого протокола.

**Шифрование**

Южный связи для протоколов используются следующие методы шифрования.

1. **WCF/TCP/OVSDB**. Для этих протоколов шифрование выполняется с помощью сертификата, который регистрируется на клиенте или сервере.

2. **WinRM**. WinRM трафик будет шифроваться по умолчанию с помощью поставщика поддержки безопасности Kerberos \(SSP\). Можно настроить дополнительное шифрование в виде SSL на сервере WinRM.