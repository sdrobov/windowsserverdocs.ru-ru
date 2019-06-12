---
title: Новые возможности защиты учетных данных
description: Безопасность Windows Server
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-credential-protection
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b0b5180-f65a-43ac-8ef3-66014116f297
author: gitmichiko
ms.author: michikos
manager: dongill
ms.date: 03/06/2017
ms.openlocfilehash: 475b6a0b24b811008ee213c1604d98d9aa9eb092
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66447033"
---
# <a name="whats-new-in-credential-protection"></a>Новые возможности защиты учетных данных

## <a name="credential-guard-for-signed-in-user"></a>Credential Guard для выполнившего вход пользователя

Начиная с Windows 10 версии 1507, Kerberos и NTLM использовать безопасность на основе виртуализации для защиты секретов Kerberos и NTLM сеанса входа вошедшего в систему пользователя. 

Начиная с Windows 10 версии 1511, диспетчер учетных данных безопасности на основе виртуализации для защиты использует сохраненные учетные данные типа учетных данных домена. Учетные данные вошедшего в систему и домена сохраненные учетные данные не передаются на удаленном узле, с помощью удаленного рабочего стола. Credential Guard можно включить без блокировки UEFI.

Начиная с Windows 10 версии 1607, изолированный режим пользователя входит в состав Hyper-V, он больше не устанавливается отдельно для развертывания Credential Guard.

[Дополнительные сведения о Credential Guard](https://technet.microsoft.com/itpro/windows/keep-secure/credential-guard).


## <a name="remote-credential-guard-for-signed-in-user"></a>Удаленный Credential Guard для выполнившего вход пользователя

Начиная с Windows 10 версии 1607, удаленный Credential Guard защищает учетные данные пользователя, вошедшего в систему, при использовании удаленного рабочего стола, защищая секреты Kerberos и NTLM на клиентском устройстве. Для удаленного узла к сетевым ресурсам следует расценивать как пользователь запросы проверки подлинности требуется клиентское устройство, чтобы использовать секреты.

Начиная с Windows 10 версии 1703, удаленный Credential Guard позволяет защитить учетные данные пользователя при использовании удаленного рабочего стола.

[Дополнительные сведения о удаленный credential guard](https://technet.microsoft.com/itpro/windows/keep-secure/remote-credential-guard).

## <a name="domain-protections"></a>Функции защиты домена

Функции защиты домена требуется домен Active Directory.

### <a name="domain-joined-device-support-for-authentication-using-public-key"></a>Поддержка устройств, присоединенных к домену для проверки подлинности с помощью открытого ключа

Начиная с Windows 10 версии 1507 и Windows Server 2016, если сможет зарегистрировать его привязанного открытого ключа с помощью Windows Server 2016 с контроллера домена (DC) устройств, присоединенных к домену, затем устройство может проверять подлинность с помощью открытого ключа, с помощью Kerberos PKINIT Проверка подлинности к контроллеру домена Windows Server 2016.

Начиная с Windows Server 2016, KDC поддерживают проверку подлинности с помощью ключа доверия Kerberos.  

[Дополнительные сведения о поддержки открытого ключа для присоединенных к домену устройства и ключа доверия Kerberos](https://technet.microsoft.com/windows-server-docs/security/kerberos/whats-new-in-kerberos-authentication).

### <a name="pkinit-freshness-extension-support"></a>Поддержка расширения актуальность PKINIT

Начиная с Windows 10 версии 1507 и Windows Server 2016, Kerberos клиент попытается расширение актуальность PKInit открытого ключа на основе проверок. 

Начиная с Windows Server 2016, KDC может поддерживать актуальность PKInit расширения.  По умолчанию KDC не предоставит PKInit расширения их актуальность. 

[Дополнительные сведения о поддержке расширение актуальность PKINIT](https://technet.microsoft.com/windows-server-docs/security/kerberos/whats-new-in-kerberos-authentication).

### <a name="rolling-public-key-only-users-ntlm-secrets"></a>Последовательное открытого ключа только NTLM секретные данные пользователей

Начиная с Windows Server 2016 режим работы домена (DFL), контроллеры домена могут поддерживать последовательное открытого ключа только NTLM секретные данные пользователей. Этот компонент недоступен в нижнем DFLs.

> [!WARNING] 
> Добавление контроллера домена к домену с помощью последовательных секреты NTLM включена перед тем, как контроллер домена был дополнен по крайней мере 8 ноября 2016 года обслуживание выполняется риск аварийное завершение работы контроллера домена. 

Конфигурация: Для новых доменов эта функция включена по умолчанию. Для существующих доменов должно быть настроено в центре администрирования Active Directory: 

1. Из центра администрирования Active Directory, щелкните правой кнопкой мыши домен в левой панели и выберите **свойства**.

    ![Свойства домена](../media/Credentials-Protection-And-Management/domain-properties.png)

2. Выберите **развертыванию истекающим сроком действия NTLM секретов во время входа, для пользователей, которым необходимо использовать Microsoft Passport или смарт-карты для интерактивного входа**.

    ![Срок действия которых истекает NTLM секреты Autoroll](../media/Credentials-Protection-And-Management/autoroll-ntlm.png)

3. Нажмите кнопку **ОК**. 

### <a name="allowing-network-ntlm-when-user-is-restricted-to-specific-domain-joined-devices"></a>Разрешает сетевому NTLM в том случае, когда пользователь предназначен только для определенных устройств, присоединенных к домену

Начиная с Windows Server 2016 функциональный уровень домена (DFL), контроллеры домена может поддерживать допускающему сети NTLM, если пользователь не ограничены конкретных устройств, присоединенных к домену. Эта возможность недоступна в нижнем DFLs.

Конфигурация: Политики проверки подлинности, нажмите кнопку **разрешить сетевой проверки подлинности NTLM пользователь может выполнять только на выбранные устройства**. 

[Дополнительные сведения о политиках проверки подлинности](https://technet.microsoft.com/windows-server-docs/security/credentials-protection-and-management/authentication-policies-and-authentication-policy-silos).
