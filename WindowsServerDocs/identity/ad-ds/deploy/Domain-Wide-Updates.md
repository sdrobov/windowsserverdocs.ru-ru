---
ms.assetid: 2a5d5271-6ac6-4c1b-b4ef-9b568932a55a
title: "Обновление схемы домена Active Directory"
description: "Обновления схемы на уровне домена, выполняемые adprep /domainprep при повышении роли контроллера домена"
author: MicrosoftGuyJFlo
ms.author: joflore
manager: femila
ms.date: 07/14/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 59efb7c854b7f3693776bf9a1a371f98c2206d60
ms.sourcegitcommit: 79c1359232bece2e5c3ee5507f1e4bf19b44f487
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2018
---
# <a name="domain-wide-schema-updates"></a>Обновление схемы домена

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Вы можете просмотреть следующий набор изменений, чтобы помочь понять и подготовки для обновления схемы, выполняемых adprep /domainprep в Windows Server. 

Начиная с Windows Server 2012, команды Adprep выполняются автоматически по мере необходимости во время установки AD DS. Они могут также выполняться отдельно до установки AD DS. Дополнительные сведения см. в разделе [Выполнение Adprep.exe](https://technet.microsoft.com/library/dd464018(v=ws.10).aspx).

Дополнительные сведения об интерпретации строк доступа управления доступом см. в разделе [строки ACE](https://msdn.microsoft.com/library/aa374928(VS.85).aspx). Дополнительные сведения о том, как интерпретировать строки ИД безопасности см. в разделе [строк SID](https://msdn.microsoft.com/library/aa379602(VS.85).aspx).

## <a name="windows-server-semi-annual-channel-domain-wide-updates"></a>Windows Server (канал точками годовой): Обновление домена

После операции, выполняемые **domainprep** в Windows Server 2016 (операция 89) завершения **версия** для CN атрибут ActiveDirectoryUpdate, CN = DomainUpdates, CN = System, DC = = Корневой_домен_леса Объект настроен для **16**.

|Количество операций и GUID|Описание|Разрешения|
|------------------------------|---------------|--------------|---------------|
|**Операция 89**: {A0C238BA-9E30-4EE6-80A6-43F731E9A5CD}|Удалите запись ACE, предоставление полного доступа для администраторов предприятия ключа и добавить запись ACE, предоставление корпоративного ключа Администраторы полный контроль над атрибут msdsKeyCredentialLink.|Delete (A; CI; RPWPCRLCLOCCDCRCWDWOSDDTSW;; Администраторы предприятия ключа) <br /> <br />Добавление (OA; CI; RPWP; 5b47d60f-6090-40b2-9f37-2a4de88f3063; Администраторы предприятия ключа)|

## <a name="windows-server-2016-domain-wide-updates"></a>Windows Server 2016: Обновление на уровне домена

После операции, выполняемые **domainprep** в Windows Server 2016 (операций 82 88) завершения **версия** для CN атрибут ActiveDirectoryUpdate, CN = DomainUpdates, CN = System, DC = = Корневой_домен_леса объект настроен для **15**.

|Количество операций и GUID|Описание|Атрибуты|Разрешения|
|------------------------------|---------------|--------------|---------------|
|**Операция 82**: {83C53DA7-427E-47A4-A07A-A324598B88F7}|Создание CN = контейнера ключей в корне домена|-objectClass: контейнера<br />-Описание: контейнер по умолчанию для объектов ключа учетных данных<br />-ShowInAdvancedViewOnly: TRUE|(A; CI; RPWPCRLCLOCCDCRCWDWOSDDTSW;; EA)<br />(A; CI; RPWPCRLCLOCCDCRCWDWOSDDTSW;; D A)<br />(A; CI; RPWPCRLCLOCCDCRCWDWOSDDTSW;; SY)<br />(A; CI; RPWPCRLCLOCCDCRCWDWOSDDTSW;; D D)<br />(A; CI; RPWPCRLCLOCCDCRCWDWOSDDTSW;; ЕВГЕНИЙ)|
|**Операция 83**: {C81FC9CC-0130-4FD1-B272-634D74818133}|Добавьте полный разрешить записи ACE CN = контейнера ключей для «domain\Key Администраторы» и «rootdomain\Enterprise ключа Администраторы».|Н/Д|(A; CI; RPWPCRLCLOCCDCRCWDWOSDDTSW;; Администраторы ключа)<br />(A; CI; RPWPCRLCLOCCDCRCWDWOSDDTSW;; Администраторы предприятия ключа)|
|**Операция 84**: {E5F9E791-D96D-4FC9-93C9-D53E1DC439BA}|Изменение атрибута otherWellKnownObjects для указания CN = контейнера ключей.|-otherWellKnownObjects: B:32:683A24E2E8164BD3AF86AC3C2CF3F981:CN = ключи %ws|Н/Д|
|**Операция 85**: {e6d5fd00-385d-4e65-b02d-9da3493ed850}|Изменение домена NC разрешить «domain\Key Администраторы» и «rootdomain\Enterprise ключа Администраторы» измените атрибут msds-KeyCredentialLink. |Н/Д|(OA; CI; RPWP; 5b47d60f-6090-40b2-9f37-2a4de88f3063; Администраторы ключа)<br />(OA; CI; RPWP; 5b47d60f-6090-40b2-9f37-2a4de88f3063; Администраторы предприятия ключ корневого домена, но не являющиеся корневыми доменами привело к созданию поддельное ACE относительно домена с ИД безопасности разрешаемое-527)|
|**Операция 86**: {3a6b3fbf-3168-4312-a10d-dd5b3393952d}|Предоставление АВТОМОБИЛЯ доменных служб Active Directory-проверен-Write-Computer Создатель-владелец и самообслуживания|Н/Д|(OA; CIIO;SW;9b026da6-0d3c-465c-8bee-5199d7165cba;bf967a86-0de6-11D0-a285-00aa003049e2;PS)<br />(OA; CIIO;SW;9b026da6-0d3c-465c-8bee-5199d7165cba;bf967a86-0de6-11D0-a285-00aa003049e2;CO)|
|**Операция 87**: {7F950403-0AB3-47F9-9730-5D7B0269F9BD}|Удалить элемент управления ДОСТУПОМ, предоставляя полный доступ в группе администраторов предприятия ключ неправильный относительно домена и добавить запись ACE, предоставляя полный доступ к группе администраторов предприятия ключа. |Н/Д|Delete (A; CI; RPWPCRLCLOCCDCRCWDWOSDDTSW;; Администраторы предприятия ключа)<br /> <br />Добавление (A; CI; RPWPCRLCLOCCDCRCWDWOSDDTSW;; Администраторы предприятия ключа)|
|**Операция 88**: {434bb40d-dbc9-4fe7-81d4-d57229f7b080}|Добавьте «msDS-ExpirePasswordsOnSmartCardOnlyAccounts» в объекте контекста Именования домена и задайте значение по умолчанию FALSE|Н/Д|Н/Д|

Администраторы предприятия ключ и ключ группы создаются только после того как контроллер домена Windows Server 2016 повышается и берет на себя роль FSMO эмулятора PDC.

## <a name="windows-server-2012-r2-domain-wide-updates"></a>Windows Server 2012 R2: Обновление домена

Несмотря на то, что операции не выполняются **domainprep** в Windows Server 2012 R2, после завершения команды **версия** для CN атрибут ActiveDirectoryUpdate, CN = DomainUpdates, CN = System, DC = = Корневой_домен_леса объект настроен для **10**.

## <a name="windows-server-2012-domain-wide-updates"></a>Windows Server 2012: Обновление на уровне домена

После операции, выполняемые **domainprep** в Windows Server 2012 (операций 78, 79, 80 и 81) завершения **версия** для CN атрибут ActiveDirectoryUpdate, CN = DomainUpdates, CN = System, DC = = Корневой_домен_леса объект настроен для **9**.

|Количество операций и GUID|Описание|Атрибуты|Разрешения|
|------------------------------|---------------|--------------|---------------|
|**Операция 78**: {c3c927a6-cc1d-47c0-966b-be8f9b63d991}|Создайте новый объект CN = устройства доверенного платформенного МОДУЛЯ в разделе домена.|Класса объектов: msTPM InformationObjectsContainer|Н/Д|
|**Операция 79**: {54afcfb9-637a-4251-9f47-4d50e7021211}|Создать запись управления доступом для службы доверенного платформенного МОДУЛЯ.|Н/Д|(OA; CIIO; WP;ea1b7b93-5e48-46d5-bc6c-4df4fda78a35;bf967a86-0de6-11D0-a285-00aa003049e2;PS)|
|**Операция 80**: {f4728883-84dd-483c-9897-274f2ebcf11e}|Предоставьте «Клонированного контроллера домена» Расширенное право **клонируемые контроллеры домена** группы|Н/Д|(OA; CR; 3e0f7e18-2c7a-4c10-ba82-4d926db99a3e; *SID домена*-522)|
|**Операция 81**: {ff4f9d27-7157-4cb0-80a9-5d6f2b14c8ff}|Предоставить ms-DS-Allowed-To-Act-On-Behalf-Of-Other-Identity Principal Self для всех объектов.|Н/Д|(OA; CIOI; RPWP; 3f78c3e5-f79a-46bd-a0b8-9d18116ddc79; PS).|
