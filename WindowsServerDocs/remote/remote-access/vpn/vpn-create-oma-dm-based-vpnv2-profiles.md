---
title: Создание профилей VPNv2 на основе OMA-DM на устройствах с Windows 10
description: 'Можно использовать один из двух методов для создания OMA-DM на основе профилей VPNv2. '
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59816485"
---
# <a name="step-75-create-oma-dm-based-vpnv2-profiles-to-windows-10-devices"></a>Шаг 7.5. Создание OMA-DM на основе VPNv2 профилей на устройствах Windows 10

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows 10

&#171;  [**Предыдущих:** Шаг 7.4. Развертывание сертификатов корневого условного доступа к локальным AD](vpn-deploy-cond-access-root-cert-to-on-premise-ad.md)<br>
&#187; [ **Next:** Узнайте, как условный доступ для VPN works](https://docs.microsoft.com/windows/access-protection/vpn/vpn-conditional-access)

На этом этапе можно создать OMA-DM на основе профилей VPNv2, с помощью Intune для развертывания политики конфигурации VPN-устройства. Если вы хотите использовать SCCM или скрипт PowerShell для создания профилей VPNv2, см. в разделе [VPNv2 CSP параметры](https://docs.microsoft.com/windows/client-management/mdm/vpnv2-csp) для получения дополнительных сведений. 

## <a name="managed-deployment-using-intune"></a>Управляемое развертывание с помощью Intune

Все, что в этом разделе рассматриваются является минимальным, необходимые для работы с условным доступом VPN. Он не распространяется на раздельное туннелирование, с помощью WIP, создание пользовательских профилей конфигурации устройств Intune для получения AutoVPN работа или единого входа. Интеграция настройкой в профиль VPN, созданный ранее в разделе [шаг 5. Настройка клиента Windows 10 AlwaysOn VPN-подключений](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md).  В этом примере мы при интеграции их в [настроить VPN-клиента с помощью Intune](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune) политики. 

**Предварительные требования.**<p>
Windows 10 клиентский компьютер уже настроен с помощью VPN-подключение с помощью Intune.   


**Процедура.**

1. На портале Azure щелкните **Intune** > **конфигурации устройства** > **профили** и выберите профиль VPN, созданный ранее в [ Настройка VPN-клиента с помощью Intune](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune).
    
2. В редакторе политик, выберите **свойства** > **параметры** > **базовая VPN**. Расширения существующих **XML-файл EAP** включать фильтр, который предоставляет логику для VPN-клиента необходимо получить из хранилища сертификатов пользователя вместо использования для вероятность того, что позволяет использовать первый сертификат условного доступа AAD Обнаружен сертификат.

    >[!NOTE]
    >Без этого VPN-клиента удалось получить доступ к пользователя сертификат, выданный центром сертификации на предприятии, приводит к сбою подключения VPN.

    ![Портал Intune](../../media/Always-On-Vpn/intune-eap-xml.png)

3. Найдите раздел, в котором заканчивается  **\</AcceptServerName >\</EapType >** и вставьте следующую строку между этими двумя значениями, чтобы предоставить логику для выбора AAD условные VPN-клиента Сертификат доступа:

    ```XML
    <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"><FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3"><EKUMapping><EKUMap><EKUName>AAD Conditional Access</EKUName><EKUOID>1.3.6.1.4.1.311.87</EKUOID></EKUMap></EKUMapping><ClientAuthEKUList Enabled="true"><EKUMapInList><EKUName>AAD Conditional Access</EKUName></EKUMapInList></ClientAuthEKUList></FilteringInfo></TLSExtensions>
    ```

4. Выберите **условного доступа** колонке и toogle **условного доступа для этого VPN-подключения** для **включено**.<p>Включение этого изменения параметра  **\<DeviceCompliance >\<включено > значение true,\<и включения >** в XML-файле профиля VPNv2.

    ![Условный доступ для Always On VPN - свойства](../../media/Always-On-Vpn/vpn-conditional-access-azure-ad.png)

6. Нажмите кнопку **ОК**.

6. Выберите **назначения**, в списке Include, нажмите кнопку **выбрать группы для включения**.

7. Выберите **пользователей VPN** группу, получающую политики и нажмите кнопку **Сохранить**.

    ![Ограничение для пользователей автоматическое VPN - назначения](../../media/Always-On-Vpn/cap-for-auto-vpn-users-assignments.png)

## <a name="force-mdm-policy-sync-on-the-client"></a>Принудительной синхронизации политики управления мобильными Устройствами на стороне клиента
Если профиль VPN не отображается на клиентском устройстве, в параметрах\\сеть и Интернет\\VPN, вы можете принудительно политики управления мобильными Устройствами для синхронизации.

1. Войдите на присоединенных к домену клиентский компьютер является членом **пользователей VPN** группы.

2. В меню «Пуск» введите **учетной записи**, и нажмите клавишу ВВОД.

3.  В области навигации слева щелкните **доступ к рабочей или учебной**.

5.  Списке доступа к рабочей или учебной **подключен к < \domain > MDM** и нажмите кнопку **Info**.

6.  Нажмите кнопку **синхронизации** и проверьте профиль VPN отобразится в разделе параметров\\сеть и Интернет\\VPN.


## <a name="next-step"></a>Дальнейшие действия
После настройки профиля VPN, чтобы использовать условный доступ Azure AD. 

|Если вы хотите...  |Затем просмотрите...  |
|---------|---------|
|Дополнительные сведения о принципах работы условного доступа в виртуальных частных сетей  |[VPN и условный доступ](https://docs.microsoft.com/windows/access-protection/vpn/vpn-conditional-access): Эта страница содержит дополнительные сведения о том, как условный доступ работает виртуальных частных сетей.      |
|Дополнительные сведения о дополнительных возможностях VPN  |[Дополнительные функции VPN](always-on-vpn/deploy/always-on-vpn-adv-options.md#advanced-vpn-features): Эта статья содержит рекомендации о Включение фильтров трафика VPN, как настроить автоматическое VPN-подключений, с помощью триггеров приложения и способы настройки сервера политики сети, чтобы разрешить VPN-подключений только от клиентов, использующих сертификаты, выданные Azure AD.        |


---

## <a name="related-topics"></a>См. также
- [VPNv2 CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/vpnv2-csp):  Этот раздел содержит общие сведения о VPNv2 CSP. Поставщик службы конфигурации VPNv2 позволяет серверу management (MDM) мобильных устройств, настройте профиль VPN устройства.

- [Настройка клиента Windows 10 AlwaysOn VPN-подключений](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-client-vpn-connections): Данный раздел содержит сведения о параметрах ProfileXML и схемы и как создать VPN-Подключение ProfileXML. После установки инфраструктуры сервера, необходимо настроить клиентские компьютеры Windows 10 для взаимодействия с этой инфраструктурой с помощью VPN-подключения. 

- [Настройка VPN-клиента с помощью Intune](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-client-vpn-connections#configure-the-vpn-client-by-using-intune): В этом разделе сведения о развертывании Windows 10 удаленного доступа профили AlwaysOn VPN. Теперь Intune использует группы Azure AD. Если Azure AD Connect синхронизированы в группу пользователей VPN из локальной в Azure AD, нет необходимости для настройки VPN-клиента с помощью Intune.

---
