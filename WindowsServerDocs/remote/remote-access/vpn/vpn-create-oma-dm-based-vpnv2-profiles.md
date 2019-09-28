---
title: Создание профилей VPNv2 на основе OMA-DM на устройствах с Windows 10
description: 'Для создания профилей поддержка vpnv2 на основе OMA-DM можно использовать один из двух методов. '
services: active-directory
ms.prod: windows-server
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
ms.openlocfilehash: 67d8a66552f77a66e1689989f412a844ef527880
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404328"
---
# <a name="step-75-create-oma-dm-based-vpnv2-profiles-to-windows-10-devices"></a>Шаг 7.5. Создание профилей поддержка vpnv2 на основе OMA-DM на устройствах Windows 10

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows 10

- [**Прошлом** Шаг 7.4. Развертывание корневых сертификатов условного доступа в локальную службу AD @ no__t-0
- [**Очеред** Узнайте, как действует условный доступ для VPN @ no__t-0

На этом шаге можно создать профили поддержка vpnv2 на основе OMA-DM с помощью Intune, чтобы развернуть политику конфигурации VPN-устройства. Если вы хотите использовать скрипт SCCM или PowerShell для создания профилей поддержка vpnv2, см. Дополнительные сведения в разделе [Параметры поддержка VPNV2 CSP](https://docs.microsoft.com/windows/client-management/mdm/vpnv2-csp) . 

## <a name="managed-deployment-using-intune"></a>Управляемое развертывание с помощью Intune

Все, что обсуждалось в этом разделе, — это минимум, необходимый для обеспечения работы VPN с условным доступом. Он не охватывает разбиение туннелирования, использование WIP, создание настраиваемых профилей конфигурации устройств Intune для получения Аутовпн работы или единого входа. Интегрируйте приведенные ниже параметры в профиль VPN, созданный ранее в разделе [Step 5. Настройте клиентские Always On Windows 10 VPN-подключения @ no__t – 0.  В этом примере мы будем интегрировать их в [настройку VPN-клиента с помощью политики Intune](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune) . 

**Готовности к установке**

На клиентском компьютере с Windows 10 уже настроено VPN-подключение с помощью Intune.   


**PROCEDURE**

1. В портал Azure выберите **intune** > **Device Configuration** > **Профили** и выберите профиль VPN, созданный ранее в окне [Настройка VPN-клиента с помощью Intune](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune).
    
2. В редакторе политики выберите **свойства** > **Параметры** > **базовый VPN**. Расширение существующего **кода EAP XML** для включения фильтра, который предоставляет VPN-клиенту логику, которой требуется получить сертификат условного доступа AAD из хранилища сертификатов пользователя, а не выходить из него, чтобы позволить ему использовать первый сертификат. обнаружения.

    >[!NOTE]
    >Без этого VPN-клиент может получить сертификат пользователя, выданный из локального центра сертификации, что приведет к неисправному VPN-подключению.

    ![Портал Intune](../../media/Always-On-Vpn/intune-eap-xml.png)

3. Перейдите к разделу, который заканчивается на **\</акцептсервернаме > \</еаптипе >** и вставьте следующую строку между этими двумя значениями, чтобы предоставить VPN-клиенту логику для выбора сертификата условного доступа AAD:

    ```XML
    <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"><FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3"><EKUMapping><EKUMap><EKUName>AAD Conditional Access</EKUName><EKUOID>1.3.6.1.4.1.311.87</EKUOID></EKUMap></EKUMapping><ClientAuthEKUList Enabled="true"><EKUMapInList><EKUName>AAD Conditional Access</EKUName></EKUMapInList></ClientAuthEKUList></FilteringInfo></TLSExtensions>
    ```

4. Выберите колонку **Условный доступ** и тугле **Условный доступ для этого VPN-подключения** , чтобы **включить**его.
   
   При включении этого параметра изменяется параметр **\<DeviceCompliance > \<Enabled > true @ no__t-3/Enabled >** в XML-файле профиля поддержка vpnv2.

    ![Условный доступ для Always On VPN — свойства](../../media/Always-On-Vpn/vpn-conditional-access-azure-ad.png)

5. Нажмите кнопку **ОК**.

6. Выберите **назначения**, в разделе включить, выберите **выберите группы для включения**.

7. Выберите группу **VPN-пользователей** , которая получает эту политику, и нажмите кнопку **сохранить**.

    ![ОГРАНИЧЕНИЕ для автоматической VPN-пользователей — назначения](../../media/Always-On-Vpn/cap-for-auto-vpn-users-assignments.png)

## <a name="force-mdm-policy-sync-on-the-client"></a>Принудительная синхронизация политики MDM на клиенте

Если профиль VPN не отображается на клиентском устройстве, в разделе Settings @ no__t-0Network & Internet @ no__t-1VPN можно принудительно синхронизировать политику MDM.

1. Войдите на клиентский компьютер, присоединенный к домену, как член группы " **пользователи VPN** ".

2. В меню Пуск введите **Account**и нажмите клавишу ВВОД.

3. В области навигации слева выберите **доступ к рабочей или учебной заведению**.

4. В разделе доступ к рабочей или учебной заголовке выберите **Подключение к < \домаин > MDM**, а затем выберите **сведения**.

5. Выберите **синхронизировать** и убедитесь, что профиль VPN отображается в разделе Параметры @ No__t-1Network & Internet @ NO__T-2VPN.


## <a name="next-steps"></a>Следующие шаги

Вы завершили настройку профиля VPN для использования условного доступа Azure AD. 

|Если вы хотите...  |Затем см...  |
|---------|---------|
|Дополнительные сведения о том, как условный доступ работает с VPN  |[VPN и условный доступ](https://docs.microsoft.com/windows/access-protection/vpn/vpn-conditional-access): На этой странице содержатся дополнительные сведения о том, как условный доступ работает с VPN.      |
|Дополнительные сведения о дополнительных возможностях VPN  |[Дополнительные функции VPN](always-on-vpn/deploy/always-on-vpn-adv-options.md#advanced-vpn-features): На этой странице приводятся рекомендации по включению фильтров трафика VPN, настройке автоматических VPN-подключений с помощью триггеров приложений и настройке NPS для разрешения VPN-подключений только от клиентов, использующих сертификаты, выданные Azure AD.        |


## <a name="related-topics"></a>См. также

- [CSP поддержка vpnv2](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/vpnv2-csp):  В этом разделе представлен обзор CSP поддержка vpnv2. Поставщик службы настройки поддержка vpnv2 позволяет серверу управления мобильными устройствами (MDM) настраивать профиль VPN устройства.

- [Настройка клиента Windows 10 Always on VPN-подключений](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-client-vpn-connections): В этом разделе содержатся сведения о параметрах и схеме Профилексмл, а также о том, как создать Профилексмл VPN. После настройки серверной инфраструктуры необходимо настроить клиентские компьютеры Windows 10 для связи с этой инфраструктурой с помощью VPN-подключения. 

- [Настройте VPN-клиент с помощью Intune](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-client-vpn-connections#configure-the-vpn-client-by-using-intune): В этом разделе содержатся сведения о развертывании профилей VPN для удаленного доступа Windows 10 Always On. Теперь Intune использует группы Azure AD. Если Azure AD Connect синхронизирует группу "пользователи VPN" из локальной среды в Azure AD, нет необходимости настраивать VPN-клиент с помощью Intune.
