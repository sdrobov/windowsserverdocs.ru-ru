---
title: TLS (Schannel SSP)
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: ebd3c40c-b4c0-4f6d-a00c-f90eda4691df
manager: alanth
author: justinha
ms.technology: security-authentication
ms.date: 05/16/2018
ms.openlocfilehash: 030fd81e0c6ba0423f1fa73e680006766cf2b180
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59890775"
---
# <a name="tls-schannel-ssp-changes-in-windows-10-and-windows-server-2016"></a>Изменения TLS (Schannel SSP) в Windows 10 и Windows Server 2016

>Область применения. Windows Server (полугодовой канал), Windows Server 2016 и Windows 10

## <a name="cipher-suite-changes"></a>Изменения cipher Suite

Windows 10, версия 1511 и Windows Server 2016 добавлена поддержка конфигурации с помощью управления мобильными устройствами (MDM) порядок комплектов шифров.

Для изменения порядка приоритета suite шифра, см. в разделе [шифров в Schannel](https://msdn.microsoft.com/library/windows/desktop/aa374757.aspx).

Добавлена поддержка следующих комплектов шифров:

- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 (RFC 5289) в Windows 10 версии 1507 и Windows Server 2016
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 (RFC 5289) в Windows 10 версии 1507 и Windows Server 2016

DisabledByDefault изменить следующие комплекты шифров:

- TLS_DHE_DSS_WITH_AES_256_CBC_SHA256 (RFC 5246) в Windows 10 версии 1703
- TLS_DHE_DSS_WITH_AES_128_CBC_SHA256 (RFC 5246) в Windows 10 версии 1703
- TLS_DHE_DSS_WITH_AES_256_CBC_SHA (RFC 5246) в Windows 10 версии 1703
- TLS_DHE_DSS_WITH_AES_128_CBC_SHA (RFC 5246) в Windows 10 версии 1703
- TLS_DHE_DSS_WITH_3DES_EDE_CBC_SHA (RFC 5246) в Windows 10 версии 1703
- TLS_RSA_WITH_RC4_128_SHA в Windows 10 версии 1709
- TLS_RSA_WITH_RC4_128_MD5 в Windows 10 версии 1709

Начиная с Windows 10 версии 1507 и Windows Server 2016, сертификаты SHA-512 поддерживаются по умолчанию.

### <a name="rsa-key-changes"></a>Изменения ключа RSA

Windows 10 версии 1507 и Windows Server 2016 добавить параметры конфигурации реестра для размеры ключей RSA клиента.

Дополнительные сведения см. в разделе [KeyExchangeAlgorithm - размеры ключей RSA клиента](tls-registry-settings.md#keyexchangealgorithm---client-rsa-key-sizes).

### <a name="diffie-hellman-key-changes"></a>Изменения ключей Диффи-Хелмана

Windows 10 версии 1507 и Windows Server 2016 добавить параметры конфигурации реестра для размеры ключей Диффи-Хеллмана.

Дополнительные сведения см. в разделе [KeyExchangeAlgorithm - размеры ключей Диффи-Хелмана](tls-registry-settings.md#keyexchangealgorithm---diffie-hellman-key-sizes).

### <a name="schusestrongcrypto-option-changes"></a>Изменения параметров SCH_USE_STRONG_CRYPTO

С Windows 10 версии 1507 и Windows Server 2016 [SCH_USE_STRONG_CRYPTO](https://msdn.microsoft.com/library/windows/desktop/aa379810.aspx) параметра теперь NULL, MD5, DES и экспортировать шифры.

## <a name="elliptical-curve-changes"></a>Изменяет эллиптической кривой

Windows 10 версии 1507 и Windows Server 2016 добавить конфигурацию групповой политики для рисования эллиптической кривых Конфигурация компьютера > Административные шаблоны > сеть > Параметры настройки SSL. Список заказов кривая ECC указывает порядок, в котором эллиптической кривых являются предпочтительными, а также позволяет поддерживаемых кривых, которые не включены. 
 
Добавлена поддержка следующих эллиптической кривых:

- BrainpoolP256r1 (RFC 7027) в Windows 10 версии 1507 и Windows Server 2016
- BrainpoolP384r1 (RFC 7027) в Windows 10 версии 1507 и Windows Server 2016 
- BrainpoolP512r1 (RFC 7027) в Windows 10 версии 1507 и Windows Server 2016
- Curve25519 (RFC draft-ietf-tls-curve25519) в Windows 10, версия 1607 и Windows Server 2016

## <a name="dispatch-level-support-for-sealmessage--unsealmessage"></a>Поддержку уровня диспетчеризации для SealMessage & UnsealMessage

Windows 10 версии 1507 и Windows Server 2016 добавлена поддержка SealMessage/UnsealMessage на уровне диспетчеризации.

## <a name="dtls-12"></a>ПРОТОКОЛ DTLS ВЕРСИИ 1.2

Windows 10, версия 1607 и Windows Server 2016 добавлена поддержка 1.2 DTLS (RFC 6347).

## <a name="httpsys-thread-pool"></a>HTTP. Пул потоков SYS 

Windows 10, версия 1607 и Windows Server 2016 добавить конфигурацию реестра размера пула потоков, используемый для обработки подтверждений TLS для протокола HTTP. SYS.

Путь реестра: 

HKLM\SYSTEM\CurrentControlSet\Control\LSA

Чтобы задать размер пула потоков на каждое ядро ЦП, создайте **MaxAsyncWorkerThreadsPerCpu** запись. Эта запись не существует в реестре по умолчанию. После создания этой записи измените значение DWORD до нужного размера. Если не задан, максимальный — 2 потока на ядро ЦП.

## <a name="next-protocol-negotiation-npn-support"></a>Далее поддержки протокола согласования (NPN)

Начиная с Windows 10 версии 1703, далее согласования протокола (NPN) был удален и больше не поддерживается.

## <a name="pre-shared-key-psk"></a>Общий ключ (PSK)

Windows 10, версия 1607 и Windows Server 2016 добавлена поддержка алгоритм обмена ключами PSK (RFC 4279).

Добавлена поддержка следующих комплектов шифров PSK:

- TLS_PSK_WITH_AES_128_CBC_SHA256 (RFC 5487) в Windows 10, версия 1607 и Windows Server 2016
- TLS_PSK_WITH_AES_256_CBC_SHA384(RFC 5487) в Windows 10, версия 1607 и Windows Server 2016
- TLS_PSK_WITH_NULL_SHA256 (RFC 5487) в Windows 10, версия 1607 и Windows Server 2016
- TLS_PSK_WITH_NULL_SHA384 (RFC 5487) в Windows 10, версия 1607 и Windows Server 2016
- TLS_PSK_WITH_AES_128_GCM_SHA256 (RFC 5487) в Windows 10, версия 1607 и Windows Server 2016
- TLS_PSK_WITH_AES_256_GCM_SHA384 (RFC 5487) в Windows 10, версия 1607 и Windows Server 2016

## <a name="session-resumption-without-server-side-state-server-side-performance-improvements"></a>Возобновление сеанса без улучшения производительности на стороне сервера состояния на стороне сервера

Windows 10 версии 1507 и Windows Server 2016 предоставляют возобновления сеанса на 30% больше, в секунду с билеты сеанса, по сравнению с Windows Server 2012.

## <a name="session-hash-and-extended-master-secret-extension"></a>Хэш-код сеанса и расширенные главный секрет расширения

Windows 10 версии 1507 и Windows Server 2016 добавлена поддержка RFC 7627: Передачи хэша сеанса слоя Security (TLS) и расширенные главный секрет расширения.

Из-за этого изменения, Windows 10 и Windows Server 2016 требует третьей стороной [поставщика CNG SSL](https://msdn.microsoft.com/library/windows/desktop/ff468652.aspx) обновления для поддержки NCRYPT_SSL_INTERFACE_VERSION_3, а также для описания этот новый интерфейс.


## <a name="ssl-support"></a>Поддержка SSL

Начиная с версии Windows 10, версия 1607 и Windows Server 2016, TLS клиент и сервер SSL 3.0 отключен по умолчанию. Это означает, что если приложение или служба специально запрашивает SSL 3.0 с помощью SSPI, клиент никогда не предлагают и принимать SSL 3.0 и сервер никогда не будет выбирать SSL 3.0.

Начиная с Windows 10 версии 1607 и Windows Server 2016, SSL 2.0 был удален и больше не поддерживается.

## <a name="changes-to-windows-tls-adherence-to-tls-12-requirements-for-connections-with-non-compliant-tls-clients"></a>Изменения в Windows TLS соблюдение требования к TLS 1.2 для соединения с клиентами несовместимые TLS

В TLS 1.2, клиент использует [расширение «signature_algorithms»](https://tools.ietf.org/html/rfc5246#section-7.4.1.4.1) для указания на сервер, на какие пары подписи или хэш-алгоритм можно использовать в цифровых подписей (т. е. сертификаты сервера и сервера обмена ключами). TLS 1.2 RFC также требует, что сообщение сертификата сервера учитывает расширение «signature_algorithms»:

«Если клиент расширение «signature_algorithms», затем все сертификаты, предоставленные сервером должен быть подписан пару алгоритм/подпись хэша, которая отображается в этом расширении.»

На практике некоторые сторонние клиенты TLS не соответствовать TLS 1.2 RFC и не сможет включить все подписи и хэш-алгоритм пары, они готовы понести в расширении «signature_algorithms» или вообще не указывать расширение (второй случай показывает для сервер, что клиент поддерживает только SHA1 RSA, DSA и ECDSA).

Сервер TLS часто достаточно одного сертификата, настроенного на конечную точку, это означает, что сервер всегда не может предоставить сертификат, отвечающий требованиям клиента.

Перед Windows 10 и Windows Server 2016, Windows TLS стека строго придерживается TLS 1.2 требованиям RFC, приводит к сбоев подключения RFC несоответствующих клиентов TLS и взаимодействия. В Windows 10 и Windows Server 2016 ограничения отменяются, и сервер может отправить сертификат, который не соответствует требованиям TLS 1.2 RFC, если это единственный параметр сервера. Клиент затем может продолжить или завершить подтверждение.

При проверке сертификатов клиента и сервера, стек Windows TLS строго соответствует TLS 1.2 RFC и разрешает только согласованного подпись и хэш-алгоритмы в сертификаты сервера и клиента.


