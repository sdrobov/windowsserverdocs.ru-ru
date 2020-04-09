---
title: Обзор TLS/SSL (поставщик общих служб Schannel)
description: Безопасность Windows Server
ms.prod: windows-server
ms.technology: security-tls-ssl
ms.topic: article
ms.assetid: 1b7b0432-1bef-4912-8c9a-8989d47a4da9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 05/16/2018
ms.openlocfilehash: e0045edf1d04feabac2354d47132b86e6d27ad2d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853627"
---
# <a name="tlsssl-overview-schannel-ssp"></a>Обзор TLS/SSL (поставщик общих служб Schannel)

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows 10

В этом разделе для ИТ-специалистов представлены реализации TLS и SSL в Windows с помощью поставщика услуг безопасности SChannel (SSP), описывающие практические приложения, изменения в реализации Майкрософт и требования к программному обеспечению, а также дополнительные ресурсы для Windows Server 2012 и Windows 8.

## <a name="description"></a><a name="BKMK_OVER"></a>Nописание
Канал SCHANNEL — это поставщик поддержки безопасности (SSP), в котором реализованы стандартные интернет-протоколы проверки подлинности SSL и TLS.

Интерфейс поставщика поддержки безопасности (SSPI) является интерфейсом API, используемым системами Windows для выполнения функций, связанных с безопасностью, включая проверку подлинности. SSPI выступает в качестве общего интерфейса для нескольких SSP, включая поставщика общих служб SChannel.

Протоколы TLS версий 1,0, 1,1 и 1,2, SSL-версии 2,0 и 3,0, а также датаграмма транспорта транспортного уровня \(DTLS\) протокола версии 1,0, а частный обмен данными \(PCT\) Protocol основаны на криптографии с открытым ключом. Эти протоколы входят в набор протоколов проверки подлинности Schannel. Для всех протоколов канала SCHANNEL используется модель клиент-сервер.

## <a name="applications"></a><a name="BKMK_APP"></a>Приложений
Одна из проблем при администрировании сети заключается в обеспечении безопасности данных, которые передаются между приложениями по сети без доверия. Вы можете использовать TLS и SSL для проверки подлинности серверов и клиентских компьютеров, а затем использовать протокол для шифрования сообщений между сторонами проверки подлинности.

Например, протоколы TLS и SSL позволяют реализовать следующие возможности.

-   Безопасные транзакции SSL c веб-сайтом электронной коммерции
-   Доступ клиента с проверкой подлинности к веб-сайту, защищенному протоколом SSL
-   Удаленный доступ.
-   Доступ к SQL
-   Электронная почта

## <a name="requirements"></a><a name="BKMK_SOFT"></a>Необходимость
Протоколы TLS и SSL используют модель "клиент-сервер" и основаны на проверке подлинности на основе сертификата, для которой требуется инфраструктура открытых ключей.

## <a name="server-manager-information"></a><a name="BKMK_INSTALL"></a>Сведения о диспетчер сервера
Для реализации TLS, SSL или SChannel не требуется никаких действий по настройке.

## <a name="see-also"></a>См. также: ##

-   [Пакет безопасности SChannel](https://docs.microsoft.com/windows/desktop/com/schannel)
-   [Безопасный канал](https://docs.microsoft.com/windows/desktop/SecAuthN/secure-channel)
-   [Протокол безопасности транспортного уровня](https://docs.microsoft.com/windows/desktop/SecAuthN/transport-layer-security-protocol)
