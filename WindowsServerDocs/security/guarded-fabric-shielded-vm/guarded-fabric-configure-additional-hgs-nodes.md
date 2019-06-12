---
title: Настройка дополнительных узлов HGS
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 227f723b-acb2-42a7-bbe3-44e82f930e35
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 10/22/2018
ms.openlocfilehash: c0741845bdbd8bfbea00df21d1fe810a27fc6a3b
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66443860"
---
# <a name="configure-additional-hgs-nodes"></a>Настройка дополнительных узлов HGS

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

В производственной среде HGS должны настраиваться в высокодоступном кластере чтобы убедиться, что экранированные виртуальные машины можно быть включен, даже если это узел HGS выходит из строя. Для тестовых сред не требуются дополнительные узлы HGS.

Используйте один из этих методов для добавления узлов HGS, как лучше всего подходит для вашей среды.

|                |                         |                              | 
|----------------|-------------------------|------------------------------|
|Новый лес HGS  | [С помощью PFX-файлы](#dedicated-hgs-forest-with-pfx-certificates) | [С использованием отпечатков сертификатов](#dedicated-hgs-forest-with-certificate-thumbprints) |
|Существующий лес бастиона |  [С помощью PFX-файлы](#existing-bastion-forest-with-pfx-certificates) | [С использованием отпечатков сертификатов](#existing-bastion-forest-with-certificate-thumbprints) |

## <a name="prerequisites"></a>Предварительные требования

Убедитесь, что каждый дополнительный узел: 
- С той же конфигурацией оборудования и программного обеспечения, что и основной узел 
- Подключается к той же сети, что и другие серверы HGS
- Можно разрешить другие серверы HGS, их DNS-имена

## <a name="dedicated-hgs-forest-with-pfx-certificates"></a>Выделенный лес HGS с PFX-сертификатов

1. Повысить уровень HGS узла до контроллера домена
2. Инициализировать сервер HGS

### <a name="promote-the-hgs-node-to-a-domain-controller"></a>Повысить уровень HGS узла до контроллера домена

[!INCLUDE [Promote to a domain controller](../../../includes/guarded-fabric-promote-domain-controller.md)] 

### <a name="initialize-the-hgs-server"></a>Инициализировать сервер HGS

[!INCLUDE [Initialize the HGS server](../../../includes/guarded-fabric-initialize-hgs-on-the-node.md)] 

## <a name="dedicated-hgs-forest-with-certificate-thumbprints"></a>Выделенный лес HGS с отпечатки сертификатов
 
1. Повысить уровень HGS узла до контроллера домена
2. Инициализировать сервер HGS
3. Установка закрытых ключей сертификатов

### <a name="promote-the-hgs-node-to-a-domain-controller"></a>Повысить уровень HGS узла до контроллера домена

[!INCLUDE [Promote to a domain controller](../../../includes/guarded-fabric-promote-domain-controller.md)] 

### <a name="initialize-the-hgs-server"></a>Инициализировать сервер HGS

[!INCLUDE [Initialize the HGS server](../../../includes/guarded-fabric-initialize-hgs-on-the-node.md)] 

### <a name="install-the-private-keys-for-the-certificates"></a>Установка закрытых ключей сертификатов

[!INCLUDE [Install private keys](../../../includes/guarded-fabric-install-private-keys.md)]

## <a name="existing-bastion-forest-with-pfx-certificates"></a>Существующий лес бастиона с PFX-сертификатов

1. Присоединения узла к существующему домену
2. Предоставить права компьютера для получения пароля групповой управляемой учетной записи и запустите Install-ADServiceAccount
3. Инициализировать сервер HGS

### <a name="join-the-node-to-the-existing-domain"></a>Присоединения узла к существующему домену

1. Убедитесь, что по крайней мере один сетевой Адаптер на узле настроена на использование DNS-сервера на первый сервер HGS.
2. Присоедините новый узел HGS к тому же домену, что ваш первый узел HGS. 

### <a name="grant-the-machine-rights-to-retrieve-gmsa-password-and-run-install-adserviceaccount"></a>Предоставить права компьютера для получения пароля групповой управляемой учетной записи и запустите Install-ADServiceAccount

[!INCLUDE [Grant the machine rights to retrieve the group MSA](../../../includes/guarded-fabric-grant-machine-rights-to-retrieve-gmsa.md)] 

### <a name="initialize-the-hgs-server"></a>Инициализировать сервер HGS

[!INCLUDE [Initialize the HGS server](../../../includes/guarded-fabric-initialize-hgs-on-the-node.md)] 

## <a name="existing-bastion-forest-with-certificate-thumbprints"></a>Существующий лес бастиона с отпечатки сертификатов

1. Присоединения узла к существующему домену
2. Предоставить права компьютера для получения пароля групповой управляемой учетной записи и запустите Install-ADServiceAccount
3. Инициализировать сервер HGS
4. Установка закрытых ключей сертификатов

### <a name="join-the-node-to-the-existing-domain"></a>Присоединения узла к существующему домену

1. Убедитесь, что по крайней мере один сетевой Адаптер на узле настроена на использование DNS-сервера на первый сервер HGS.
2. Присоедините новый узел HGS к тому же домену, что ваш первый узел HGS. 

### <a name="grant-the-machine-rights-to-retrieve-gmsa-password-and-run-install-adserviceaccount"></a>Предоставить права компьютера для получения пароля групповой управляемой учетной записи и запустите Install-ADServiceAccount

[!INCLUDE [Grant the machine rights to retrieve the group MSA](../../../includes/guarded-fabric-grant-machine-rights-to-retrieve-gmsa.md)] 

### <a name="initialize-the-hgs-server"></a>Инициализировать сервер HGS

[!INCLUDE [Initialize the HGS server](../../../includes/guarded-fabric-initialize-hgs-on-the-node.md)] 

Может занять до 10 минут для шифрования и подписывания сертификатов на первом сервере HGS для репликации на этом узле.

### <a name="install-the-private-keys-for-the-certificates"></a>Установка закрытых ключей сертификатов

[!INCLUDE [Install private keys](../../../includes/guarded-fabric-install-private-keys.md)]

## <a name="configure-hgs-for-https-communications"></a>Настройка HGS связь по протоколу HTTPS

Если вы хотите защитить HGS конечных точек с помощью SSL-сертификат, необходимо настроить SSL-сертификата на этот узел, а также всех остальных узлов в кластере HGS.
SSL-сертификаты *не* реплицируется с HGS и не обязательно должны использовать те же ключи для каждого узла (т. е. может иметь разные сертификаты SSL для каждого узла).

При запросе сертификат SSL, убедиться, что полное доменное имя кластера (как показано в выходных данных `Get-HgsServer`) является либо общее имя субъекта сертификата или включены в качестве альтернативного имени субъекта DNS.
После получения сертификата от центра сертификации можно настроить HGS на работу с [HgsServer набора](https://technet.microsoft.com/itpro/powershell/windows/hgsserver/set-hgsserver).

```powershell
$sslPassword = Read-Host -AsSecureString -Prompt "SSL Certificate Password"
Set-HgsServer -Http -Https -HttpsCertificatePath 'C:\temp\HgsSSLCertificate.pfx' -HttpsCertificatePassword $sslPassword
```

Если вы уже установлен сертификат в локальном хранилище сертификатов и ссылка на него по отпечатку, выполните следующую команду:

```powershell
Set-HgsServer -Http -Https -HttpsCertificateThumbprint 'A1B2C3D4E5F6...'
```

HGS всегда будет предоставлять портов HTTP и HTTPS для связи.
Он не поддерживается для удаления привязки HTTP в IIS, однако вы можете использовать брандмауэр Windows или другие технологии брандмауэра сети для заблокируйте обмен данными через порт 80.

## <a name="decommission-an-hgs-node"></a>Списание узлом HGS

Чтобы списать узлом HGS:

1. [Очистить конфигурацию HGS](guarded-fabric-manage-hgs.md#clearing-the-hgs-configuration).

   Это удаляет узел из кластера и удаляет аттестации и защиты ключей. 
   Если это последний узел в кластере, - Force необходим для обозначения того, вы хотите удалить последний узел и удалите кластер в Active Directory. 
   
   Если HGS развертывается в лесу-бастионе (по умолчанию), который является единственным шагом. 
   При необходимости, можно отсоединить компьютер из домена, а также удаление групповой управляемой учетной записи из Active Directory.

1. Если HGS создали свой собственный домен, необходимо также [удаление HGS](guarded-fabric-manage-hgs.md#clearing-the-hgs-configuration) исключении из домена и понижение роли контроллера домена.



## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Проверка конфигурации HGS](guarded-fabric-verify-hgs-configuration.md)

