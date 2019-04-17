---
title: "Новые возможности защиты учетных данных"
description: "Безопасность Windows Server"
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
ms.openlocfilehash: 0556c606b987a69eae663b0196467f532d5a307a
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="whats-new-in-credential-protection"></a>Новые возможности защиты учетных данных

## <a name="credential-guard-for-signed-in-user"></a>Credential Guard для пользователя в систему

Начиная с Windows 10 версии 1507 Kerberos и NTLM использовать безопасность на основе виртуализации для защиты секретов Kerberos и NTLM сеанса входа в систему пользователя. 

Начиная с Windows 10 версии 1511, диспетчер учетных данных использует безопасности на основе виртуализации для защиты сохраненные учетные данные типа учетных данных домена. Вход в систему и домена сохраненные учетные данные не будут передаваться удаленному узлу с помощью удаленного рабочего стола. Credential Guard можно включить без блокировки UEFI.

Начиная с Windows 10 версии 1607 компонент режима изолированного пользователя входит в состав Hyper-V, он больше не устанавливается отдельно для развертывания Credential Guard.

[Дополнительные сведения о Credential Guard](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/credential-guard).


## <a name="remote-credential-guard-for-signed-in-user"></a>Remote Credential Guard для пользователя в систему

Начиная с Windows 10 версии 1607, удаленный Credential Guard защищает учетные данные пользователя в систему, при использовании удаленного рабочего стола, защищая секреты Kerberos и NTLM на клиентском устройстве. Для удаленного узла для оценки сетевым ресурсам от имени пользователя все запросы проверки подлинности требуется устройства клиента на использование секреты.

Начиная с Windows 10 версии 1703 Remote Credential Guard защищает учетные данные пользователя, при использовании удаленного рабочего стола.

[Дополнительные сведения о удаленный credential guard](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/remote-credential-guard).

## <a name="domain-protections"></a>Средства защиты домена

Средства защиты домена требуется домена Active Directory.

### <a name="domain-joined-device-support-for-authentication-using-public-key"></a>Поддержка устройств, присоединенных к домену для проверки подлинности с помощью открытого ключа

Начиная с Windows 10 версии 1507 и Windows Server 2016, если сможет зарегистрировать свой привязаны к открытый ключ с контроллером домена Windows Server 2016 (DC) устройств, присоединенных к домену, затем устройство можно выполнить проверку подлинности с помощью открытого ключа, с помощью проверки подлинности Kerberos PKINIT на контроллер домена Windows Server 2016.

Начиная с Windows Server 2016, KDC поддерживает проверку подлинности с помощью ключа доверия Kerberos.  

[Дополнительные сведения о поддержки открытого ключа для устройств, присоединенных к домену и ключа доверия Kerberos](https://technet.microsoft.com/en-us/windows-server-docs/security/kerberos/whats-new-in-kerberos-authentication).

### <a name="pkinit-freshness-extension-support"></a>Поддержка расширения актуальности PKINIT

Начиная с Windows 10 версии 1507 и Windows Server 2016, клиент Kerberos попытается расширение актуальности PKInit открытого ключа на основе входа надстроек. 

Начиная с Windows Server 2016, центров распространения ключей могут поддерживать расширение актуальности PKInit.  По умолчанию центров распространения ключей не предоставит расширение актуальности PKInit. 

[Узнайте больше о поддержке расширений актуальности PKINIT](https://technet.microsoft.com/en-us/windows-server-docs/security/kerberos/whats-new-in-kerberos-authentication).

### <a name="rolling-public-key-only-users-ntlm-secrets"></a>Последовательное секреты NTLM открытого ключа только пользователя

Начиная с Windows Server 2016 режима работы домена (DFL), контроллеры домена могут поддерживать последовательное секреты открытого ключа только пользователя NTLM. Этот компонент недоступен в нижнем DFLs.

> [!WARNING] 
> Добавление контроллера домена в домен с помощью последовательного секреты NTLM включена перед тем, как контроллер домена был обновлен с помощью по крайней мере от 8 ноября 2016 г обслуживания выполняется риск сбоя контроллера домена. 

Конфигурация: Для новых доменов, эта функция включена по умолчанию. Для существующих доменов его необходимо настроить в центре администрирования Active Directory: 

1. В центре администрирования Active Directory, щелкните правой кнопкой мыши домен в левой панели и выберите **свойства**.

    ![Свойства домена](../media/Credentials-Protection-And-Management/domain-properties.png)
    
2. Выберите **включить последовательное секретов NTLM истекающим сроком действия во время входа, для пользователей, которые требуются для использования Microsoft Passport или смарт-карты для интерактивного входа в систему**.

    ![Окончание срока действия NTLM секреты Autoroll](../media/Credentials-Protection-And-Management/autoroll-ntlm.png)

3. Нажмите кнопку **ОК**. 

### <a name="allowing-network-ntlm-when-user-is-restricted-to-specific-domain-joined-devices"></a>Когда пользователь ограничено только с определенных устройств, присоединенных к домену, что позволяет сети NTLM

Начиная с Windows Server 2016 режим работы домена (DFL), контроллеры домена может поддерживать позволяют сети NTLM, если пользователь не ограничивается определенных устройств, присоединенных к домену. Эта функция не работает в нижнем DFLs.

Конфигурация: Политика проверки подлинности щелкните **разрешить сетевой проверки подлинности NTLM пользователь ограничен выбранного устройства**. 

[Дополнительные сведения о политиках проверки подлинности](https://technet.microsoft.com/en-us/windows-server-docs/security/credentials-protection-and-management/authentication-policies-and-authentication-policy-silos).
