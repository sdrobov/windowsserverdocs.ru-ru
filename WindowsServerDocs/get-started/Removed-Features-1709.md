---
title: Удаленные или подлежащие замене компоненты в Windows Server (версия 1709)
description: Компоненты и функции, удаленные или запланированные к удалению в выпусках.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: server-general
ms.tgt_pltfrm: na
ms.topic: article
ms.date: 06/05/2018
author: jaimeo
ms.author: jaimeo
manager: dougkim
ms.localizationpriority: medium
ms.openlocfilehash: 37970f3bee2070cffc77bff855a8f28641196b24
ms.sourcegitcommit: 48bb3e5c179dc520fa879b16c9afe09e07c87629
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66452858"
---
# <a name="features-removed-or-planned-for-replacement-starting-with-windows-server-version-1709"></a>Удаленные или подлежащие замене компоненты в Windows Server версии 1709

>Область применения. Windows Server версии 1709

В этой статье приведен список компонентов и возможностей в Windows Server версии 1709, которые уже удалены в этом выпуске или рассматриваются к замене в последующих выпусках. Он предназначен для ИТ-специалистов, выполняющих обновление операционных систем в коммерческих средах. **Этот список может быть изменена в последующих выпусках и могут не включать каждый затрагиваемый компонент или функциональные возможности.** 

## <a name="features-removed-from-windows-server-version-1709"></a>Компоненты, удаленные из Windows Server версии 1709
Windows Server версии 1709 содержит те же компоненты, что и Windows Server 2016. Тем не менее, этот выпуск не предоставляет различные варианты установки, доступные в Windows Server 2016:

- являясь выпуском Semi-Annual Channel, Windows Server версии 1709 предоставляет лишь вариант установки основных серверных компонентов. Дополнительные сведения см. в разделе [сравнение каналы обслуживания](../get-started-19/servicing-channels-19.md).
- Начиная с этого выпуска, сервер Nano Server недоступен в качестве готовой к установке серверной операционной системы. Вместо этого сервер Nano Server доступен в качестве операционной системы контейнера. См. раздел [Изменения сервера Nano Server в Windows Server версии 1709](nano-in-semi-annual-channel.md).
- Начиная с этого выпуска, Server Message Block (SMB) версии 1 больше не устанавливается по умолчанию. Дополнительные сведения см. в разделе [SMBv1 не устанавливается по умолчанию в Windows 10 Fall Creators Update и Windows Server, версии 1709 и более поздних версиях](https://support.microsoft.com/help/4034314/smbv1-is-not-installed-by-default-in-windows).


## <a name="features-being-considered-for-replacement-starting-with-subsequent-releases"></a>Компоненты, рассматриваемые к замене в последующих выпусках

Следующие компоненты и возможности рассматриваются к замене в следующих выпусках после Windows Server версии 1709. В конечном итоге они могут быть окончательно удалены из образа продукта для установки и заменены другими (или доступными для установки из других источников) компонентами или возможностями, но они по-прежнему доступны в этом выпуске, иногда с частично ограниченными возможностями. Рекомендуем заранее предусмотреть альтернативные варианты или дальнейшую замену для приложений, кода и режимов, зависимых от данных компонентов.

Если вы хотите оставить отзыв о предстоящей замене какого-либо из этих компонентов, воспользуйтесь приложением [Центр отзывов](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Несмотря на то, что это приложение выполняется в Windows 10, с его помощью можно также отправить нам отзыв о Windows Server и сопутствующей документации.

### <a name="iis-6-management-compatibility"></a>Совместимость управления IIS 6
Ниже приведены конкретные компоненты, рассматриваемые к замене.

- Совместимость метабазы IIS 6 (Web-Metabase)
- Консоль управления IIS 6 (Web-Lgcy-Mgmt-Console)
- Средства создания сценариев IIS 6 (Web-Lgcy-Scripting)
- Совместимость WMI IIS 6 (Web-WMI)

Вместо компонента "Совместимость метабазы IIS 6" (который выполняет роль уровня эмуляции между сценариями метабазы на основе IIS 6 и файловой конфигурацией, используемой в IIS 7 и более новых версиях) следует начать перенос сценариев управления непосредственно в целевую файловую конфигурацию IIS с помощью таких средств, как пространство имен Microsoft.Web.Administration.

Также следует начать переход с IIS 6.0 или более ранних версий на последнюю версию IIS, которая всегда доступна в самом свежем выпуске Windows Server.


### <a name="iis-digest-authentication"></a>Дайджест-проверка подлинности IIS
Этот способ проверки подлинности планируется заменить. Вместо него следует начать использовать другие способы аутентификации, такие как сопоставление сертификата клиента (см. раздел [Настройка сопоставлений сертификата клиента "один к одному"](https://docs.microsoft.com/iis/manage/configuring-security/configuring-one-to-one-client-certificate-mappings)) или аутентификация Windows (см. раздел [Параметры приложений](https://docs.microsoft.com/iis-administration/configuration/appsettings.json)).

### <a name="internet-storage-name-service-isns"></a>iSNS
Служба iSNS рассматривается к замене. Компонент SMB фактически предоставляет те же функции, а также дополнительные возможности. Общие сведения об этом компоненте см. в разделе [Общие сведения о протоколе SMB](https://technet.microsoft.com/library/hh831795(v=ws.11).aspx).

### <a name="rsaaes-encryption-for-iis"></a>Шифрование RSA/AES для IIS 
Этот метод шифрования считается для замены, так как руководителя Cryptography API: Метод Next Generation (CNG) уже доступна. Дополнительные сведения о шифровании CNG см. разделе [Описание CNG](https://msdn.microsoft.com/library/windows/desktop/aa375276(v=vs.85).aspx).

### <a name="windows-powershell-20"></a>Windows PowerShell 2.0
Эта ранняя версия Windows PowerShell заменена несколькими более поздними версиями. Для получения лучших компонентов и производительности следует перейти на Windows PowerShell 5.0 или более позднюю версию. Подробные сведения см. в разделе [Документация по PowerShell](https://docs.microsoft.com/powershell/index?view=powershell-5.1).

