---
ms.assetid: 2a5d5271-6ac6-4c1b-b4ef-9b568932a55a
title: Обновлений схемы домена Active Directory
description: Изменений схемы на уровне домена, производимых adprep/domainprep, при повышении роли контроллера домена
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 10/29/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 20598431b9c2376051247fd7ba14e33af00968cc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59812325"
---
# <a name="domain-wide-schema-updates"></a>Обновления схемы домена

>Область применения. Windows Server

Вы можете просмотреть следующий набор изменений, которые помогут освоить и подготовка для обновления схемы, выполняет команду adprep/domainprep в Windows Server.

Начиная с Windows Server 2012, команды Adprep выполняются автоматически по мере необходимости во время установки AD DS. Они могут также выполняться отдельно до установки AD DS. Дополнительные сведения см. в разделе [Выполнение Adprep.exe](https://technet.microsoft.com/library/dd464018(v=ws.10).aspx).

Дополнительные сведения о том, как интерпретировать строки доступ элементов управления доступом, см. в разделе [строки ACE](https://msdn.microsoft.com/library/aa374928(VS.85).aspx). Дополнительные сведения об интерпретации строк ИД безопасности см. в разделе [строки SID](https://msdn.microsoft.com/library/aa379602(VS.85).aspx).

## <a name="windows-server-semi-annual-channel-domain-wide-updates"></a>Windows Server (полугодовой канал): Обновление на уровне домена

После выполнения операций, выполняемых **domainprep** в Windows Server 2016 (операция 89) завершения **редакции** атрибут для CN ActiveDirectoryUpdate, CN = = DomainUpdates, CN = System, DC = Объект Корневой_домен_леса присваивается **16**.

|Число операций и GUID|Описание|Разрешения|
|------------------------------|---------------|--------------|---------------|
|**Операция 89**: {A0C238BA-9E30-4EE6-80A6-43F731E9A5CD}|Удалите элемент управления ДОСТУПОМ, предоставив полный доступ к "Администраторы предприятия ключ" и добавьте запись ACE, предоставив Enterprise ключ "Администраторы" полный контроль над атрибут msdsKeyCredentialLink.|Удалить (A; НЕПРЕРЫВНАЯ ИНТЕГРАЦИЯ; RPWPCRLCLOCCDCRCWDWOSDDTSW;; "Администраторы предприятия ключа") <br /> <br />Add (OA;CI;RPWP;5b47d60f-6090-40b2-9f37-2a4de88f3063;;Enterprise Key Admins)|

## <a name="windows-server-2016-domain-wide-updates"></a>Windows Server 2016: Обновление на уровне домена

После выполнения операций, выполняемых **domainprep** в Windows Server 2016 (операций 82 88) завершения **редакции** атрибут для CN ActiveDirectoryUpdate, CN = = DomainUpdates, CN = System, DC = Корневой_домен_леса присваивается **15**.

|Число операций и GUID|Описание|Атрибуты|Разрешения|
|------------------------------|---------------|--------------|---------------|
|**Операция 82**: {83C53DA7-427E-47A4-A07A-A324598B88F7}|Создание CN = контейнер ключей в корне домена|-objectClass: контейнера<br />— Описание: Контейнер по умолчанию для объектов ключа учетных данных<br />- ShowInAdvancedViewOnly: TRUE|(A; НЕПРЕРЫВНАЯ ИНТЕГРАЦИЯ; RPWPCRLCLOCCDCRCWDWOSDDTSW;; EA)<br />(A;CI;RPWPCRLCLOCCDCRCWDWOSDDTSW;;;DA)<br />(A;CI;RPWPCRLCLOCCDCRCWDWOSDDTSW;;;SY)<br />(A; НЕПРЕРЫВНАЯ ИНТЕГРАЦИЯ; RPWPCRLCLOCCDCRCWDWOSDDTSW;; D D)<br />(A; НЕПРЕРЫВНАЯ ИНТЕГРАЦИЯ; RPWPCRLCLOCCDCRCWDWOSDDTSW;; ЭД)|
|**Операция 83**: {C81FC9CC-0130-4FD1-B272-634D74818133}|Добавить полный контроль разрешающие элементы ACE для CN = контейнер ключей для «domain\Key "Администраторы"» и «"rootdomain\Enterprise" Администраторы ключ».|Н/Д|(A;CI;RPWPCRLCLOCCDCRCWDWOSDDTSW;;;Key Admins)<br />(A; НЕПРЕРЫВНАЯ ИНТЕГРАЦИЯ; RPWPCRLCLOCCDCRCWDWOSDDTSW;; "Администраторы предприятия ключа")|
|**Операция 84**: {E5F9E791-D96D-4FC9-93C9-D53E1DC439BA}|Измените значение атрибута otherWellKnownObjects для CN = контейнер ключей.|-otherWellKnownObjects: B:32:683A24E2E8164BD3AF86AC3C2CF3F981:CN=Keys,%ws|Н/Д|
|**Операция 85**: {e6d5fd00-385d-4e65-b02d-9da3493ed850}|Изменить домен, контекст Именования для разрешения «"domain\Key" Администраторы» и «"rootdomain\Enterprise" Администраторы ключ» для изменения значения атрибута msds-KeyCredentialLink. |Н/Д|(OA;CI;RPWP;5b47d60f-6090-40b2-9f37-2a4de88f3063;;Key Admins)<br />(OA; НЕПРЕРЫВНАЯ ИНТЕГРАЦИЯ; RPWP; 5b47d60f-6090-40b2-9f37-2a4de88f3063; "Администраторы предприятия ключ" в корневом домене, но в доменах, отличного от root привело к фиктивный ACE относительно домена с Неразрешимый SID-527)|
|**Операция 86**: {3a6b3fbf-3168-4312-a10d-dd5b3393952d}|Предоставление машина доменных служб Active Directory-проверки-Write-Computer Создатель-владелец и самого себя|Н/Д|(OA; CIIO;SW;9b026da6-0d3c-465c-8bee-5199d7165cba;bf967a86-0de6-11D0-a285-00aa003049e2;PS)<br />(OA;CIIO;SW;9b026da6-0d3c-465c-8bee-5199d7165cba;bf967a86-0de6-11d0-a285-00aa003049e2;CO)|
|**Операция 87**: {7F950403-0AB3-47F9-9730-5D7B0269F9BD}|Удалить элемент управления ДОСТУПОМ, предоставляя полный доступ к группе "Администраторы предприятия ключ" неверный относительно домена и добавьте элемент управления ДОСТУПОМ, предоставляя полный доступ к группе "Администраторы предприятия ключ". |Н/Д|Удалить (A; НЕПРЕРЫВНАЯ ИНТЕГРАЦИЯ; RPWPCRLCLOCCDCRCWDWOSDDTSW;; "Администраторы предприятия ключа")<br /> <br />Добавить (A; НЕПРЕРЫВНАЯ ИНТЕГРАЦИЯ; RPWPCRLCLOCCDCRCWDWOSDDTSW;; "Администраторы предприятия ключа")|
|**Операция 88**: {434bb40d-dbc9-4fe7-81d4-d57229f7b080}|Добавьте «msDS-ExpirePasswordsOnSmartCardOnlyAccounts» в объекте контекста Именования домена и значение по умолчанию равно FALSE|Н/Д|Н/Д|

Группы "Администраторы предприятия ключ" и "Администраторы" ключа создаются только в том случае, после выдвижения контроллера домена Windows Server 2016 и берет на себя роль FSMO эмулятора основного контроллера домена.

## <a name="windows-server-2012-r2-domain-wide-updates"></a>Windows Server 2012 R2: Обновление на уровне домена

Несмотря на то, что операции не выполняются **domainprep** в Windows Server 2012 R2, после выполнения команды **редакции** атрибут для CN ActiveDirectoryUpdate, CN = = DomainUpdates, CN = System, DC = Корневой_домен_леса присваивается **10**.

## <a name="windows-server-2012-domain-wide-updates"></a>Windows Server 2012: Обновление на уровне домена

После выполнения операций, выполняемых **domainprep** в Windows Server 2012 (операции 78 "," 79 "," 80 "и" 81) завершения **редакции** атрибут для CN = ActiveDirectoryUpdate, CN = DomainUpdates, CN = System, DC = Корневой_домен_леса присваивается **9**.

|Число операций и GUID|Описание|Атрибуты|Разрешения|
|------------------------------|---------------|--------------|---------------|
|**Операция 78**: {c3c927a6-cc1d-47c0-966b-be8f9b63d991}|Создает новый объект CN = устройства доверенного платформенного МОДУЛЯ в разделе домена.|Объект класса: msTPM InformationObjectsContainer|Н/Д|
|**Операция 79**: {54afcfb9-637a-4251-9f47-4d50e7021211}|Создать запись управления доступом для службы доверенного платформенного МОДУЛЯ.|Н/Д|(OA;CIIO;WP;ea1b7b93-5e48-46d5-bc6c-4df4fda78a35;bf967a86-0de6-11d0-a285-00aa003049e2;PS)|
|**Операция 80**: {f4728883-84dd-483c-9897-274f2ebcf11e}|Предоставьте «Клонирование контроллера домена» Расширенное право **клонируемые контроллеры домена** группы|Н/Д|(OA; CR; 3e0f7e18-2c7a-4c10-ba82-4d926db99a3e; *SID домена*-522)|
|**Операция 81**: {ff4f9d27-7157-4cb0-80a9-5d6f2b14c8ff}|Предоставьте ms-DS-Allowed-To-Act-On-Behalf-Of-Other-Identity Self участника для всех объектов.|Н/Д|(OA;CIOI;RPWP;3f78c3e5-f79a-46bd-a0b8-9d18116ddc79;;PS)|
