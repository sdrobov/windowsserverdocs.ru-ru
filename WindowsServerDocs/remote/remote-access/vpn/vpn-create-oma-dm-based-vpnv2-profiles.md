---
title: Создание профилей VPNv2 на основе OMA-DM на устройствах с Windows 10
description: 'Можно использовать один из двух методов для создания OMA DM на основе VPNv2 профилей. '
services: active-directory
ms.prod: windows-server-threshold
ms.technology: networking-ras
documentationcenter: ''
ms.assetid: ''
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/13/2018
ms.author: pashort
author: shortpatti
ms.localizationpriority: medium
ms.reviewer: deverette
ms.openlocfilehash: 1ce20d09c304b26e3708429cc45da06d020e5809
ms.sourcegitcommit: 4147e092d77d9458696e6686bccefe3788c90508
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2019
ms.locfileid: "9031298"
---
# Шаг 7.5. Создание OMA DM на основе VPNv2 профилей для устройств с Windows 10

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows 10

& #171;  [ **Предыдущих:** шаг 7.4. Развертывание корневые сертификаты условного доступа к локальным AD](vpn-deploy-cond-access-root-cert-to-on-premise-ad.md)<br>
& #187; [ **Далее:** Узнайте, как условного доступа для VPN работает](https://docs.microsoft.com/windows/access-protection/vpn/vpn-conditional-access)

На этом этапе можно создать OMA DM на основе VPNv2 профили, с помощью Intune для развертывания политики конфигурации устройств VPN. Если вы хотите использовать сценарий SCCM или PowerShell для создания профилей VPNv2, см. в разделе [параметров VPNv2 CSP](https://docs.microsoft.com/windows/client-management/mdm/vpnv2-csp) для получения дополнительных сведений. 

## Управляемого развертывания, с помощью Intune

Все описанные в этом разделе было минимальным, необходимые для работы с условным доступом VPN. Он не рассматривается разделения туннелирования, с помощью WIP, создав пользовательские профили конфигурации устройства Intune для получения AutoVPN работе или единого входа. Интеграция настройкой в профиль VPN, которую вы создали ранее в разделе [Шаг 5. Настройка клиента Windows 10 всегда на VPN-подключений](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md).В этом примере мы интеграции их в политику [настроить VPN-клиент с помощью Intune](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune) . 

**Предварительное условие:**<p>
Windows 10 клиентский компьютер уже настроен с помощью VPN-подключения с помощью Intune.   


**Процедура:**

1. На портале Azure выберите **Intune** > **Конфигурацию устройства** > **профилей** и выберите профиль VPN ранее созданный [настроить VPN-клиент с помощью Intune](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune).
    
2. В редакторе политик Выбор **свойств** > **Параметры** > **Базового VPN**. Расширить существующий **EAP Xml** , включающий фильтр, который предоставляет VPN-клиент логику, он должен получить условного доступа AAD сертификат из хранилища сертификатов пользователя, а не оставлять его вероятность того, позволяя ему использовать первый сертификат обнаружены.

    >[!NOTE]
    >Без этого VPN-клиент, можно получить пользователя сертификат, выданный локальный центр сертификации, что сбой VPN-подключение.

    ![Портал Intune](../../media/Always-On-Vpn/intune-eap-xml.png)

3. Найдите раздел, который заканчивается **\</AcceptServerName>\</EapType>** и вставьте следующую строку между этими двумя значениями для предоставления VPN-клиент с логика для выбора сертификата AAD условного доступа:

    ```XML
    <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"><FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3"><EKUMapping><EKUMap><EKUName>AAD Conditional Access</EKUName><EKUOID>1.3.6.1.4.1.311.87</EKUOID></EKUMap></EKUMapping><ClientAuthEKUList Enabled="true"><EKUMapInList><EKUName>AAD Conditional Access</EKUName></EKUMapInList></ClientAuthEKUList></FilteringInfo></TLSExtensions>
    ```

4. Выберите колонке **Условного доступа** и toogle **условного доступа для VPN-подключения** к **включено**.<p>Включение этого параметра изменяется **\<DeviceCompliance>\<Enabled>true\</Enabled>** в XML-ФАЙЛ VPNv2 профиля.

    ![Условного доступа для всегда на VPN - свойства](../../media/Always-On-Vpn/vpn-conditional-access-azure-ad.png)

6. Нажмите кнопку **ОК**.

6. Выберите **назначения**, включить, щелкните **Выберите группы для включения**.

7. Выберите группу **Пользователей VPN** , который получает эту политику и нажмите кнопку **Сохранить**.

    ![Ограничение для пользователей VPN автоматически - назначения](../../media/Always-On-Vpn/cap-for-auto-vpn-users-assignments.png)

## Принудительно синхронизацию политики MDM на клиентском компьютере
Если VPN-профиль не отображаются на клиентском устройстве, в разделе Settings\\Network & Internet\\VPN, вы можете принудительно политики MDM для синхронизации.

1. Войдите в присоединенный к домену клиентский компьютер как член группы **Пользователей VPN** .

2. В меню "Пуск" введите **учетную запись**и нажмите клавишу ВВОД.

3.  В левой области навигации выберите **доступ к рабочей или учебной учетной записи**.

5.  В списке доступ к рабочей или учебной учетной записи выберите **подключен к <\domain> MDM** и нажмите кнопку **сведения**.

6.  Нажмите кнопку **синхронизации** и убедитесь, что VPN-профиля появляется в Settings\\Network & Internet\\VPN.


## Дальнейшие действия
Вы закончили настройке VPN-профиль для использования условного доступа Azure AD. 

|Если вы хотите …  |Затем см.  |
|---------|---------|
|Дополнительные сведения о том, как условного доступа работает с VPN  |[VPN и условный доступ](https://docs.microsoft.com/windows/access-protection/vpn/vpn-conditional-access): на этой странице приведены дополнительные сведения о том, как условного доступа работает с VPN.      |
|Дополнительные сведения о расширенных возможностях VPN  |[Дополнительные параметры VPN](always-on-vpn/deploy/always-on-vpn-adv-options.md#advanced-vpn-features): на этой странице приведены рекомендации по Включение фильтры трафика VPN, как настроить автоматическое VPN-подключений с помощью приложений-триггеров и настройка сервера политики сети, чтобы разрешить VPN-подключения только от клиентов, использующих сертификаты, выданные Azure РЕКЛАМА.        |


---

## Статьи по теме
- [VPNv2 CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/vpnv2-csp): в этом разделе вы найдете Обзор VPNv2 CSP. Поставщик служб конфигурации VPNv2 позволяет серверу мобильное устройство устройствами (MDM) для настройки VPN-профиля устройства.

- [Настройка Windows 10 клиента всегда на VPN-подключений](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-client-vpn-connections): в этом разделе представлены сведения о параметрах ProfileXML и схемы и способы создания ProfileXML VPN. После настройки серверной инфраструктуры, необходимо настроить клиентские компьютеры Windows10 для связи с ИТ-инфраструктуры с VPN-подключение. 

- [Настройка VPN-клиент с помощью Intune](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-client-vpn-connections#configure-the-vpn-client-by-using-intune): этот раздел содержит сведения о том, как развернуть профили Windows 10 удаленного доступа к VPN. Теперь Intune использует Azure AD группы. Если Azure AD Connect синхронизировать группу пользователей VPN из локальной к Azure AD, нет необходимости для настройки VPN-клиент с помощью Intune.

---
