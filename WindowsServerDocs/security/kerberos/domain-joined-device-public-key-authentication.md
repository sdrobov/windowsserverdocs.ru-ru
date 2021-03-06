---
title: Проверка подлинности открытого ключа устройства, присоединенного к домену
ms.prod: windows-server
ms.topic: article
ms.assetid: 7bd17803-6e42-4a3b-803f-e47c74725813
manager: alanth
author: michikos
ms.technology: security-authentication
ms.date: 08/18/2017
ms.openlocfilehash: 450d3e64ff753a718c2e72e69cb60d51c8c18f78
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856337"
---
# <a name="domain-joined-device-public-key-authentication"></a>Проверка подлинности открытого ключа устройства, присоединенного к домену

>Область применения: Windows Server 2016, Windows 10

Добавлена поддержка устройств, присоединенных к домену, для входа с использованием сертификата, начиная с Windows Server 2012 и Windows 8. Это изменение позволяет сторонним поставщикам создавать решения для предоставления и инициализации сертификатов для устройств, присоединенных к домену, для использования при проверке подлинности домена. 

## <a name="automatic-public-key-provisioning"></a>Автоматическая подготовка открытого ключа

Начиная с Windows 10 версии 1507 и Windows Server 2016, присоединенные к домену устройства автоматически подготавливают связанный открытый ключ к контроллеру домена Windows Server 2016 (DC). После подготовки ключа Windows может использовать проверку подлинности с открытым ключом в домене.

### <a name="key-generation"></a>Создание ключей
Если на устройстве работает Credential Guard, то пара открытого и закрытого ключей создается с защитой Credential Guard. 

Если Credential Guard недоступен, а доверенный платформенный модуль —, то создается пара из открытого и закрытого ключей, защищенных доверенным платформенным модулем. 

Если ни один из них недоступен, пара ключей не создается и устройство может проходить проверку подлинности только с помощью пароля.

### <a name="provisioning-computer-account-public-key"></a>Открытый ключ подготовки учетной записи компьютера
При запуске Windows проверяет, подготовлен ли открытый ключ для учетной записи компьютера. В противном случае он создает связанный открытый ключ и настраивает его для своей учетной записи в AD с помощью контроллера домена Windows Server 2016 или более поздней версии. Если все контроллеры домена находятся в недоступном масштабе, ключ не подготавливается.

### <a name="configuring-device-to-only-use-public-key"></a>Настройка устройства для использования только открытого ключа
Если параметр групповая политика **для проверки подлинности устройства с помощью сертификата** имеет значение **Force**, то устройство должно найти контроллер домена под управлением Windows Server 2016 или более поздней версии для проверки подлинности. Этот параметр находится в разделе административные шаблоны > системы > Kerberos.

### <a name="configuring-device-to-only-use-password"></a>Настройка устройства для использования только пароля
Если параметр групповая политика **Поддержка проверки подлинности устройства с помощью сертификата** отключен, то всегда используется пароль. Этот параметр находится в разделе административные шаблоны > системы > Kerberos.

## <a name="domain-joined-device-authentication-using-public-key"></a>Проверка подлинности присоединенного к домену устройства с помощью открытого ключа
Если у Windows есть сертификат для устройства, присоединенного к домену, Kerberos сначала проверяет подлинность с помощью сертификата и при сбое пытается выполнить повторную попытку с паролем. Это позволяет устройству проходить проверку подлинности на контроллерах домена нижнего уровня.

Так как автоматически подготовленные открытые ключи имеют самозаверяющий сертификат, проверка сертификата завершается сбоем на контроллерах домена, которые не поддерживают сопоставление учетных записей доверия ключей. По умолчанию Windows повторяет проверку подлинности с использованием пароля домена устройства.


