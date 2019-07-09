---
title: Удаленные или подлежащие замене возможности в Windows Server (версия 1709)
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
ms.sourcegitcommit: 3743cf691a984e1d140a04d50924a3a0a19c3e5c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2019
ms.locfileid: "66452858"
---
# <a name="features-removed-or-planned-for-replacement-starting-with-windows-server-version-1709"></a>Удаленные или подлежащие замене возможности в Windows Server версии 1709

>Область применения. Windows Server версии 1709

Ниже приведен список функций и возможностей Windows Server версии 1709, которые либо удалены из продукта в этом выпуске, либо рассматриваются для возможной замены в последующих выпусках. Он предназначен для ИТ-специалистов, выполняющих обновление операционных систем в коммерческих средах. **Этот список не является исчерпывающим и может быть изменен в следующих выпусках.** 

## <a name="features-removed-from-windows-server-version-1709"></a>Возможности, удаленные из Windows Server версии 1709
Windows Server версии 1709 содержит те же возможности, что и Windows Server 2016. Однако в этом выпуске доступны другие варианты установки, чем в Windows Server 2016:

- Являясь полугодовым выпуском канала, Windows Server версии 1709 предоставляет только вариант установки основных серверных компонентов. Более подробную информацию см [Сравнение каналов обслуживания](../get-started-19/servicing-channels-19.md).
- Начиная с этого выпуска, Nano Server недоступен в качестве устанавливаемой операционной системы сервера. Вместо этого Nano Server доступен в качестве операционной системы контейнера. См. раздел [Изменения Nano Server в Windows Server версии 1709](nano-in-semi-annual-channel.md).
- Начиная с этого выпуска, Server Message Block (SMB) версии 1 больше не устанавливается по умолчанию. Дополнительные сведения см. в разделе [SMBv1 не устанавливается по умолчанию в Windows 10 Fall Creators Update и Windows Server, версии 1709 и более поздних версиях](https://support.microsoft.com/help/4034314/smbv1-is-not-installed-by-default-in-windows).


## <a name="features-being-considered-for-replacement-starting-with-subsequent-releases"></a>Возможности, рассматриваемые к замене в последующих выпусках

Следующие возможности и функции рассматриваются к замене в следующих выпусках после Windows Server версии 1709. В конечном итоге они могут быть окончательно удалены из образа продукта для установки и заменены другими (или доступными для установки из других источников) возможностями или функциями, но они по-прежнему доступны в этом выпуске, иногда с частично ограниченными возможностями. Рекомендуем заранее предусмотреть альтернативные варианты или дальнейшую замену для приложений, кода и режимов, зависимых от данных возможностей.

Если вы хотите оставить отзыв о предстоящей замене какой-либо из этих возможностей, воспользуйтесь приложением [Центр отзывов](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Несмотря на то, что это приложение работает в Windows 10, с его помощью можно также отправить отзыв о продукте Windows Server (и соответствующей документации).

### <a name="iis-6-management-compatibility"></a>Совместимость управления IIS 6.
Ниже приведены конкретные возможности, рассматриваемые к замене:

- совместимость метабазы IIS 6 (Web-Metabase);
- консоль управления IIS 6 (Web-Lgcy-Mgmt-Console);
- средства создания сценариев IIS 6 (Web-Lgcy-Scripting);
- совместимость WMI IIS 6 (Web-WMI).

Вместо возможности "Совместимость с метабазой IIS 6" (функционирующей как уровень эмуляции между сценариями метабазы на основе IIS 6 и файловой конфигурацией, используемой в IIS 7 или более поздних версиях), следует начать перенос сценариев управления непосредственно в целевую файловую конфигурацию IIS, используя такие средства, как пространство имен Microsoft.Web.Administration.

Также следует начать перенос с IIS 6.0 или более ранних версий и перейти на последнюю версию IIS, которая всегда доступна в самой последней версии Windows Server.


### <a name="iis-digest-authentication"></a>Дайджест-проверка подлинности IIS
Этот способ проверки подлинности планируется заменить. Вместо него следует начать использовать другие способы проверки подлинности, такие как сопоставление сертификата клиента (см. раздел [Настройка сопоставлений клиентских сертификатов «один-к-одному»](https://docs.microsoft.com/iis/manage/configuring-security/configuring-one-to-one-client-certificate-mappings)) или проверка подлинности Windows (см. раздел [Настройки приложения](https://docs.microsoft.com/iis-administration/configuration/appsettings.json)).

### <a name="internet-storage-name-service-isns"></a>iSNS
Служба iSNS рассматривается к замене. Возможность Server Message Block (SMB) предлагает практически те же функции, а также дополнительные возможности. Для получения дополнительных сведений об этой возможности см. раздел [Общие сведения о протоколе SMB](https://technet.microsoft.com/library/hh831795(v=ws.11).aspx).

### <a name="rsaaes-encryption-for-iis"></a>Шифрование RSA/AES для IIS 
Этот метод шифрования будет заменен на более совершенный способ на основе API-интерфейса: Метод шифрования нового поколения (CNG) уже доступен. Дополнительные сведения о шифровании CNG см. в разделе [Описание CNG](https://msdn.microsoft.com/library/windows/desktop/aa375276(v=vs.85).aspx).

### <a name="windows-powershell-20"></a>Windows PowerShell 2.0
Эта ранняя версия Windows PowerShell заменена несколькими более поздними версиями. Для обеспечения наилучших возможностей и производительности перейдите на Windows PowerShell 5.0 или более позднюю версию. Подробные сведения см. в разделе [Документация по PowerShell](https://docs.microsoft.com/powershell/index?view=powershell-5.1).

