---
ms.assetid: 9831b421-8fb7-4e15-ac27-c013cbca6d05
title: Требования к сертификатам для серверов федерации
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 9154e168fa03b08177dd0125fcbc1707d8e5594f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853217"
---
# <a name="certificate-requirements-for-federation-servers"></a>Требования к сертификатам для серверов федерации

В любом службы федерации Active Directory (AD FS) \(AD FS\) проектирования, для защиты связи и упрощения проверки подлинности пользователей между Интернетом и серверами федерации необходимо использовать различные сертификаты. Каждый сервер федерации должен иметь сертификат связи службы и маркер\-сертификат подписи, прежде чем он сможет участвовать в AD FS связи. В следующей таблице описаны типы сертификатов, связанные с сервером федерации.  
  
|Тип сертификата|Описание|  
|--------------------|---------------|  
|Сертификат для подписи\-токен|Маркер\-сертификата подписи — это сертификат X509. Серверы федерации используют связанные пары открытых\/закрытых ключей для цифровой подписи всех выдающихся маркеров безопасности. Сюда относится подписывание опубликованных метаданных федерации и запросов на разрешение артефактов.<p>Можно использовать несколько маркеров\-сертификатов подписи, настроенных в\-оснастки управления AD FS в, чтобы разрешить смену сертификатов, когда срок действия одного из сертификатов близок к истечению. По умолчанию все сертификаты в списке публикуются, но только основной маркер\-сертификат подписи используется AD FS для фактического подписывания маркеров. Все выбранные сертификаты должны иметь соответствующий закрытый ключ.<p>Дополнительные сведения см. в статьях [Сертификаты подписи токенов](Token-Signing-Certificates.md) и [Добавление сертификата подписи токенов](../../ad-fs/deployment/Add-a-Token-Signing-Certificate.md).|  
|Сертификат взаимодействия служб|Серверы федерации используют сертификат проверки подлинности сервера, который также называется связью службы для Windows Communication Foundation \(WCF\) безопасности сообщений. По умолчанию это тот же сертификат, который используется сервером федерации в качестве SSL \(сертификат SSL\) в службы IIS \(IIS\). **Примечание.** \-оснастки управления AD FS в относится к сертификатам проверки подлинности сервера для серверов федерации в качестве сертификатов связи служб.<p>Дополнительные сведения см. в разделе [сертификаты связи служб](Service-Communications-Certificates.md) и [Настройка сертификата связи службы](../../ad-fs/deployment/Set-a-Service-Communications-Certificate.md).<p>Так как сертификат связи служб должен быть доверенным для клиентских компьютеров, рекомендуется использовать сертификат, подписанный доверенным центром сертификации \(CA\). Все выбранные сертификаты должны иметь соответствующий закрытый ключ.|  
|SSL \(сертификат\) SSL|Серверы федерации используют сертификат SSL для обеспечения безопасности трафика веб-служб при обмене данными SSL с веб-клиентами и прокси-серверами федерации.<p>Поскольку сертификату SSL должны доверять клиентские компьютеры, рекомендуется использовать сертификат, подписанный доверенным центром сертификации. Все выбранные сертификаты должны иметь соответствующий закрытый ключ.|  
|Сертификат расшифровки токена\-|Этот сертификат используется для расшифровки токенов, полученных этим сервером федерации.<p>Можно использовать несколько сертификатов расшифровки. Это позволяет серверу федерации ресурсов расшифровывать маркеры, выпущенные с помощью старого сертификата, после того как новый сертификат будет установлен в качестве основного сертификата расшифровки. Для расшифровки можно использовать все сертификаты, но только основной маркер,\-расшифровку сертификата, фактически публикуется в метаданных федерации. Все выбранные сертификаты должны иметь соответствующий закрытый ключ.<p>Дополнительные сведения см. [в разделе Добавление сертификата для расшифровки маркера](../../ad-fs/deployment/Add-a-Token-Decrypting-Certificate.md).|  
  
Вы можете запросить и установить SSL-сертификат или сертификат связи службы, запросив сертификат связи службы с помощью консоли управления (MMC) \(оснастку ММС\) привязать\-в для IIS. Дополнительные общие сведения об использовании SSL-сертификатов см. [в разделе iis 7,0: настройка SSL в iis 7,0](https://go.microsoft.com/fwlink/?LinkID=108544) и [IIS 7,0: Настройка сертификатов сервера в IIS 7,0](https://go.microsoft.com/fwlink/?LinkID=108545) .  
  
> [!NOTE]  
> В AD FS можно изменить \(алгоритм SHA\), используемый для цифровых подписей с помощью SHA\-1 или SHA\-256 \(более безопасным\). AD Фсдоес не поддерживает использование сертификатов с другими методами хэширования, например MD5 \(алгоритма хэширования по умолчанию, который используется с программой командной\-line программы Makecert. exe\). Для обеспечения безопасности рекомендуется использовать SHA\-256 \(который по умолчанию установлен в\) для всех подписей. SHA\-1 рекомендуется использовать только в сценариях, в которых необходимо взаимодействовать с продуктом, который не поддерживает обмен данными с помощью SHA\-256, например, не\-продукта Майкрософт или AD FS 1. *x*.  
  
## <a name="determining-your-ca-strategy"></a>Определение стратегии центра сертификации  
AD FS не требует, чтобы сертификаты выдавались центром сертификации. Однако SSL-сертификат \(сертификат, который также используется по умолчанию, так как сертификат взаимодействия служб\) должен быть доверенным для AD FS клиентов. Для этих типов сертификатов не рекомендуется использовать собственные сертификаты, подписанные\-.  
  
> [!IMPORTANT]  
> Использование собственной\-подписанных SSL-сертификатов в рабочей среде может позволить злоумышленнику в организации партнера по учетным записям осуществлять управление серверами федерации в организации партнера по ресурсам. Такая угроза безопасности существует потому, что\-самозаверяющие сертификаты являются корневыми сертификатами. Они должны быть добавлены в доверенное корневое хранилище другого сервера федерации \(например,\)сервера федерации ресурсов, который может оставить этот сервер уязвимым для атак.  
  
После получения сертификата из центра сертификации необходимо убедиться, что все сертификаты импортированы в хранилище личных сертификатов на локальном компьютере. Сертификаты можно импортировать в личное хранилище с помощью оснастки MMC "сертификаты"\-в.  
  
В качестве альтернативы привязке сертификатов\-в можно также импортировать SSL-сертификат с помощью оснастки «Диспетчер IIS»\-в во время назначения сертификата SSL веб сайту по умолчанию. Дополнительные сведения см. в разделе [Импорт сертификата проверки подлинности сервера на веб-сайт по умолчанию](../../ad-fs/deployment/Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md).  
  
> [!NOTE]  
> Перед установкой AD FS программного обеспечения на компьютер, который станет сервером федерации, убедитесь, что оба сертификата находятся в хранилище личных сертификатов локального компьютера и что сертификат SSL назначен веб-сайту по умолчанию. Дополнительные сведения о порядке задач, необходимых для настройки сервера федерации, см. в разделе [Контрольный список: Настройка сервера федерации](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server.md).  
  
В зависимости от требований безопасности и бюджетных ограничений необходимо тщательно продумать, какие из сертификатов будут присваиваться публичным или корпоративным центром сертификации. На рисунке ниже показаны рекомендованные издатели (центры сертификации) определенных типов сертификатов. Эта рекомендация отражает лучший\-подход к безопасности и затратам.  
  
![требования к сертификатам](media/adfs2_fedserver_certstory_1.png)  
  
## <a name="certificate-revocation-lists"></a>Списки отзыва сертификатов  
Если у какого-либо используемого сертификата есть списки отзыва сертификатов (CRL), сервер с настроенным сертификатом должен иметь возможность связаться с сервером, распространяющим CRL.  
  
## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
