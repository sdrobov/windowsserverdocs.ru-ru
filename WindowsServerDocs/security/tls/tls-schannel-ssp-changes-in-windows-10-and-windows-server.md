---
title: TLS (Schannel SSP)
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: ebd3c40c-b4c0-4f6d-a00c-f90eda4691df
manager: alanth
author: justinha
ms.technology: security-authentication
ms.date: 11/09/2016
ms.openlocfilehash: 6e1a229bfc7063597f8994c71bbaec5637d084a4
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="tls-schannel-ssp-changes-in-windows-10-and-windows-server-2016"></a>Изменения TLS (Schannel SSP) в Windows 10 и Windows Server 2016

>Область применения: Windows Server 2016 и Windows 10

## <a name="cipher-suite-changes"></a>Изменения шифрования Suite

Windows 10 версии 1511 и Windows Server 2016 добавить поддержку для настройки порядок комплектов шифров, с помощью управления мобильными устройствами (MDM).

Для изменения порядка Приоритет suite шифров, в разделе [комплекты шифров в Schannel](https://msdn.microsoft.com/library/windows/desktop/aa374757.aspx).

Добавлена поддержка следующих комплектов шифров:

- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 (RFC 5289) в Windows 10 версии 1507 и Windows Server 2016
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 (RFC 5289) в Windows 10 версии 1507 и Windows Server 2016

DisabledByDefault изменить для следующих комплектов шифров:

- TLS_DHE_DSS_WITH_AES_256_CBC_SHA256 (RFC 5246) в Windows 10 версии 1703
- TLS_DHE_DSS_WITH_AES_128_CBC_SHA256 (RFC 5246) в Windows 10 версии 1703
- TLS_DHE_DSS_WITH_AES_256_CBC_SHA (RFC 5246) в Windows 10 версии 1703
- TLS_DHE_DSS_WITH_AES_128_CBC_SHA (RFC 5246) в Windows 10 версии 1703
- TLS_DHE_DSS_WITH_3DES_EDE_CBC_SHA (RFC 5246) в Windows 10 версии 1703
- TLS_RSA_WITH_RC4_128_SHA в Windows 10, версия 1709
- TLS_RSA_WITH_RC4_128_MD5 в Windows 10, версия 1709

Начиная с Windows 10 версии 1507 и Windows Server 2016, SHA-512 сертификаты поддерживаются по умолчанию.

### <a name="rsa-key-changes"></a>Изменения ключей RSA

Windows 10 версии 1507 и Windows Server 2016 добавьте параметры конфигурации реестра для размеры ключей RSA клиента.

Дополнительные сведения см. в разделе [KeyExchangeAlgorithm - размеры ключей RSA клиента](tls-registry-settings.md#keyexchangealgorithm---client-rsa-key-sizes).

### <a name="diffie-hellman-key-changes"></a>Группы Диффи-Хелмана основные изменения

Windows 10 версии 1507 и Windows Server 2016 добавьте параметры конфигурации реестра для размеры ключа Диффи-Хелмана.

Дополнительные сведения см. в разделе [KeyExchangeAlgorithm - размеры ключа Диффи-Хелмана](tls-registry-settings.md#keyexchangealgorithm---diffie-hellman-key-sizes).

### <a name="schusestrongcrypto-option-changes"></a>Изменения параметров SCH_USE_STRONG_CRYPTO

С Windows 10 версии 1507 и Windows Server 2016 [SCH_USE_STRONG_CRYPTO](https://msdn.microsoft.com/library/windows/desktop/aa379810.aspx) вариант теперь отключает NULL, MD5, DES и экспортировать шифров.

## <a name="elliptical-curve-changes"></a>Изменяет эллиптических кривых

Windows 10 версии 1507 и Windows Server 2016 добавить конфигурацию групповой политики для эллиптических кривых в разделе Конфигурация компьютера > Административные шаблоны > сеть > Параметры настройки SSL. Список заказов кривой ECC определяет порядок, в котором эллиптических кривых являются предпочтительными, а также позволяет поддерживаемых кривых, которые не включены. 
 
Добавлена поддержка следующих эллиптических кривых:

- BrainpoolP256r1 (RFC 7027) в Windows 10 версии 1507 и Windows Server 2016
- BrainpoolP384r1 (RFC 7027) в Windows 10 версии 1507 и Windows Server 2016 
- BrainpoolP512r1 (RFC 7027) в Windows 10 версии 1507 и Windows Server 2016
- Curve25519 (RFC черновик ietf-tls-curve25519) в Windows 10 версии 1607 и Windows Server 2016

## <a name="dispatch-level-support-for-sealmessage--unsealmessage"></a>Поддержка уровня отправки для SealMessage & UnsealMessage

Windows 10 версии 1507 и Windows Server 2016 добавить поддержку SealMessage или UnsealMessage на уровне отправки.

## <a name="dtls-12"></a>ПРОТОКОЛ DTLS ВЕРСИИ 1.2

Windows 10 версии 1607 и Windows Server 2016 добавить поддержку 1.2 DTLS (RFC 6347).

## <a name="httpsys-thread-pool"></a>HTTP.SYS 

Windows 10 версии 1607 и Windows Server 2016 добавить конфигурацию реестра от размера пула потоков для обработки подтверждений TLS для HTTP.SYS.

Путь в реестре: 

HKLM\SYSTEM\CurrentControlSet\Control\LSA

Чтобы задать размер пула потоков максимальное на каждое ядро Процессора, создать **MaxAsyncWorkerThreadsPerCpu** запись. Эта запись не существует в реестре по умолчанию. После создания записи измените значение DWORD до нужного размера. Если не настроена, максимальное — 2 потоках на каждое ядро Процессора.

## <a name="next-protocol-negotiation-npn-support"></a>Далее поддержки согласования протокола (NPN)

Начиная с Windows 10 версии 1703 Далее согласование протокола (NPN) были удалены и больше не поддерживается.

## <a name="pre-shared-key-psk"></a>Общим ключом (PSK)

Windows 10 версии 1607 и Windows Server 2016 добавить поддержку алгоритм обмена ключами PSK (RFC 4279).

Добавлена поддержка следующих PSK шифров:

- TLS_PSK_WITH_AES_128_CBC_SHA256 (RFC 5487) в Windows 10 версии 1607 и Windows Server 2016
- TLS_PSK_WITH_AES_256_CBC_SHA384(RFC 5487) в Windows 10 версии 1607 и Windows Server 2016
- TLS_PSK_WITH_NULL_SHA256 (RFC 5487) в Windows 10 версии 1607 и Windows Server 2016
- TLS_PSK_WITH_NULL_SHA384 (RFC 5487) в Windows 10 версии 1607 и Windows Server 2016
- TLS_PSK_WITH_AES_128_GCM_SHA256 (RFC 5487) в Windows 10 версии 1607 и Windows Server 2016
- TLS_PSK_WITH_AES_256_GCM_SHA384 (RFC 5487) в Windows 10 версии 1607 и Windows Server 2016

## <a name="session-resumption-without-server-side-state-server-side-performance-improvements"></a>Возобновление сеанса без повышение производительности на стороне сервера состояния на стороне сервера

Windows 10 версии 1507 и Windows Server 2016 предоставить билеты сеанса, по сравнению с Windows Server 2012 30% больше resumptions сеанса в секунду.

## <a name="session-hash-and-extended-master-secret-extension"></a>Хэш-код сеанса и расширенные главный секрет расширения

Windows 10 версии 1507 и Windows Server 2016 добавить поддержку RFC 7627: хэш сеанса безопасности TLS (Transport Layer) и расширенных расширение главный секрет.

Из-за этого изменения Windows 10 и Windows Server 2016 требует сторонние [поставщика CNG SSL](https://msdn.microsoft.com/library/windows/desktop/ff468652.aspx) обновления для поддержки NCRYPT_SSL_INTERFACE_VERSION_3 и описывается новый интерфейс.


## <a name="ssl-support"></a>Поддержка протокола SSL

Начиная с версии Windows 10 версии 1607 и Windows Server 2016, сервере клиент TLS и SSL 3.0 отключен по умолчанию. Это означает, что если приложение или службу, в частности, запрашивает SSL 3.0 через интерфейс SSPI, клиент никогда не будет предлагать или принимать SSL 3.0 и сервер никогда не выберет SSL 3.0.

SSL 2.0, начиная с Windows 10 версии 1607 и Windows Server 2016 были удалены и больше не поддерживается.

## <a name="changes-to-windows-tls-adherence-to-tls-12-requirements-for-connections-with-non-compliant-tls-clients"></a>Изменения Windows TLS соблюдение требований TLS 1.2 для соединений с помощью несовместимых клиентов TLS

В TLS 1.2, клиент использует [расширение «signature_algorithms»](https://tools.ietf.org/html/rfc5246#section-7.4.1.4.1) для указания на сервер, какие пары алгоритма подписи/хеширования может использоваться в цифровой подписи (т. е. сертификаты сервера и сервера обмена ключами). TLS 1.2 RFC также требуется, что сообщение сертификат сервера соблюдать расширение «signature_algorithms»:

«Если клиент расширение «signature_algorithms», затем все сертификаты, предоставленные сервером должно подписываться пару алгоритм хэша или подписи, которая отображается в данное расширение.»

На практике некоторые клиенты сторонних TLS не соответствовать TLS 1.2 RFC и fail включают все подпись и хэш-алгоритм пары они готовы принять в расширением «signature_algorithms» или полностью опускать расширение (последний указывает серверу клиент поддерживает только SHA1 RSA, DSA и ECDSA).

Сервер TLS имеет часто только один сертификат, настроенный на конечную точку, это означает, что сервер не может предоставить всегда сертификата, удовлетворяющего требованиям клиента.

До появления Windows 10 и Windows Server 2016 стека Windows TLS строго придерживается TLS 1.2 требования RFC, из-за которой сбоев подключения с RFC несовместимых клиентов TLS и проблем взаимодействия. В Windows 10 и Windows Server 2016 освобождаются ограничения, и сервер может отправить сертификат, который не отвечает требованиям TLS 1.2 RFC, если это единственный вариант сервера. Клиент может затем продолжить или прекратить подтверждение.

При проверке сервера и клиентских сертификатов, стека Windows TLS строго стандарту TLS 1.2 RFC и только позволяет согласованного подпись и хэш-алгоритмов в серверных и клиентских сертификатов.


