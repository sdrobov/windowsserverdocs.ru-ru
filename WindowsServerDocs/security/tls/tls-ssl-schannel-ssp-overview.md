---
title: Обзор протоколов TLS/SSL (Schannel SSP)
description: Безопасность Windows Server
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-tls-ssl
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b7b0432-1bef-4912-8c9a-8989d47a4da9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 05/16/2018
ms.openlocfilehash: a6571e5e06e07fd62ad4cf39bab322b45c90a9f9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59848605"
---
# <a name="tlsssl-overview-schannel-ssp"></a>Обзор протоколов TLS/SSL (Schannel SSP)

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10

В этом разделе для ИТ-специалистов, рассматривается реализации протоколов TLS и SSL в Windows с использованием поставщика службы безопасности Schannel (SSP) и описаны варианты практического применения, изменения в реализации корпорации Майкрософт и требования к программному обеспечению, а также Дополнительные ресурсы по Windows Server 2012 и Windows 8.

## <a name="BKMK_OVER"></a>Описание
Канал SCHANNEL — это поставщик поддержки безопасности (SSP), в котором реализованы стандартные интернет-протоколы проверки подлинности SSL и TLS.

Интерфейс поставщика поддержки безопасности (SSPI) является интерфейсом API, используемым системами Windows для выполнения функций, связанных с безопасностью, включая проверку подлинности. Интерфейс SSPI работает как общий интерфейс для нескольких поставщиков общих служб, включая поставщика Schannel SSP.

TLS версии 1.0, 1.1 и 1.2, протокол SSL версий 2.0 и 3.0, а также датаграмм Transport Layer Security \(DTLS\) протокол версии 1.0 и транспорта Communications Private \(PCT\) на основе протокола шифрование с открытым ключом. Эти протоколы входят в набор протоколов проверки подлинности Schannel. Для всех протоколов канала SCHANNEL используется модель клиент-сервер.

## <a name="BKMK_APP"></a>Приложения
Одна из проблем при администрировании сети заключается в обеспечении безопасности данных, которые передаются между приложениями по сети без доверия. TLS и SSL можно использовать для проверки подлинности серверов и клиентских компьютеров, а затем использовать протокол для шифрования сообщений между проверенными сторонами.

Например, протоколы TLS и SSL позволяют реализовать следующие возможности.

-   Безопасные транзакции SSL c веб-сайтом электронной коммерции
-   Доступ клиента с проверкой подлинности к веб-сайту, защищенному протоколом SSL
-   Удаленный доступ.
-   Доступ к SQL
-   электронная почта

## <a name="BKMK_SOFT"></a>Требования к
Протоколы TLS и SSL используется модель клиент/сервер и основаны на проверке подлинности сертификата, который требует инфраструктуры открытого ключа.

## <a name="BKMK_INSTALL"></a>Сведения о диспетчере сервера
Никаких действий по настройке необходимы для реализации TLS, SSL или канала Schannel.

## <a name="see-also"></a>См. также ##

-   [Пакет безопасности Schannel](https://docs.microsoft.com/windows/desktop/com/schannel)
-   [Безопасный канал](https://docs.microsoft.com/windows/desktop/SecAuthN/secure-channel)
-   [Протокол TLS](https://docs.microsoft.com/windows/desktop/SecAuthN/transport-layer-security-protocol)
