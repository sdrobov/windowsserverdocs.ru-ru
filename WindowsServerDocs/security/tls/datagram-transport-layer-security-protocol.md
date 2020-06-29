---
title: Протокол DTLS
description: Безопасность Windows Server
ms.prod: windows-server
ms.technology: security-tls-ssl
ms.topic: article
ms.assetid: 57b8873a-ad9c-4f2c-93e0-a2af352c6965
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 05/16/2018
ms.openlocfilehash: 79477aa441b82854852fe35a9b45bafdee664532
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85475271"
---
# <a name="datagram-transport-layer-security-protocol"></a>Протокол DTLS

Windows Server (Semi-Annual Channel), Windows Server 2016, Windows 10

В этом справочном разделе по ИТ-специалисту описан протокол датаграммы Transport Layer Security (DTLS), который входит в состав поставщика поддержки безопасности SChannel (SSP).

## <a name="BKMK_DTLS"></a>
Протокол DTLS, представленный в общепринятом поставщике услуг Schannel в Windows Server 2012 и Windows 8, обеспечивает конфиденциальность обмена данными для протоколов датаграмм. Сведения о том, какая версия DTLS поддерживается в версиях Windows, см. в разделе [протоколы в TLS/SSL (Schannel SSP)](https://msdn.microsoft.com/library/windows/desktop/mt808159(v=vs.85).aspx). Данный протокол позволяет клиентским и серверным приложениям взаимодействовать способом, обеспечивающим защиту от перехвата, взлома или подделки сообщений. Протокол DTLS основывается на протоколе TLS и предоставляет аналогичные гарантии безопасности, которые сокращают потребность в использовании IPsec или разработке пользовательского протокола безопасности на уровне приложений.

Датаграммы обычно используются в потоковых носителях, например в играх или в защищенных видеоконференциях. Разработчики могут разрабатывать приложения для использования протокола DTLS в контексте модели с интерфейсом проверки подлинности Windows (SSPI) для защиты обмена данными между клиентами и серверами. Протокол DTLS построен на основе протокола UDP. DTLS разрабатывается так же, как и протокол TLS, чтобы максимально увеличить безопасность Invention и повысить уровень повторного использования кода и инфраструктуры.

Комплекты шифров, доступные для конфигурации, обрабатываются после того, как вы можете настроить TLS. RC4 не разрешен. SChannel использует шифрование следующего поколения (CNG). Это использует преимущества сертификации FIPS 140, которая появилась в Windows Vista.

## <a name="additional-references"></a>Дополнительные ссылки

[Безопасность транспортного уровня в стандарте IETF RFC 4347](http://tools.ietf.org/html/rfc4347)


