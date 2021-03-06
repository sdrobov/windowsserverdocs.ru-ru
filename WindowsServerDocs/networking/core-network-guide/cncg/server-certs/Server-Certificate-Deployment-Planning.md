---
title: Планирование развертывания сертификата сервера
description: Эта статья является частью руководств по развертыванию сертификатов сервера для беспроводных и беспроводных развертываний 802.1 X.
manager: brianlic
ms.topic: article
ms.assetid: 7eb746e0-1046-4123-b532-77d5683ded44
ms.prod: windows-server
ms.technology: networking
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 131fb7d51e703abfdfb3f3e07790b52daa1b7b82
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87518519"
---
# <a name="server-certificate-deployment-planning"></a>Планирование развертывания сертификата сервера

>Применяется к: Windows Server (Semi-Annual Channel), Windows Server 2016

Перед развертыванием сертификатов сервера необходимо спланировать следующие элементы.

- [Планирование базовой конфигурации сервера](#bkmk_basic)

- [Планирование доступа к домену](#bkmk_domain)

- [Планирование расположения и имени виртуального каталога на веб-сервере](#bkmk_virtual)

- [Планирование записи псевдонима DNS (CNAME) для веб-сервера](#bkmk_cname)

- [Настройка плана для файла CAPolicy. INF](#bkmk_capolicy)

- [Планирование конфигурации CDP и AIA в CA1](#bkmk_cdp)

- [Планирование операции копирования между ЦС и веб-сервером](#bkmk_copy)

- [Планирование конфигурации шаблона сертификата сервера в центре сертификации](#bkmk_template)

## <a name="plan-basic-server-configuration"></a><a name="bkmk_basic"></a>Планирование базовой конфигурации сервера
После установки Windows Server 2016 на компьютерах, которые планируется использовать в качестве центра сертификации и веб-сервера, необходимо переименовать компьютер и назначить и настроить статический IP-адрес для локального компьютера.

Дополнительные сведения см. в разделе [Сетевое руководством](../../../core-network-guide/Core-Network-Guide.md)по Windows Server 2016 Core.

## <a name="plan-domain-access"></a><a name="bkmk_domain"></a>Планирование доступа к домену
Для входа в домен компьютер должен быть членом домена, а в доменных службах Active Directory необходимо создать учетную запись пользователя. Кроме того, для большинства процедур в этом пошаговом окне требуется, чтобы учетная запись пользователя была членом групп "Администраторы предприятия" или "Администраторы домена" в Active Directory пользователи и компьютеры, поэтому необходимо войти в центр сертификации с помощью учетной записи, имеющей соответствующее членство в группе.

Дополнительные сведения см. в разделе [Сетевое руководством](../../../core-network-guide/Core-Network-Guide.md)по Windows Server 2016 Core.

## <a name="plan-the-location-and-name-of-the-virtual-directory-on-your-web-server"></a><a name="bkmk_virtual"></a>Планирование расположения и имени виртуального каталога на веб-сервере
Чтобы предоставить доступ к списку отзыва сертификатов и сертификату ЦС другим компьютерам, эти элементы необходимо хранить в виртуальном каталоге на веб-сервере. В этом пошаговом окне виртуальный каталог расположен на веб-сервере WEB1. Эта папка находится на диске C: и называется PKI. Виртуальный каталог на веб-сервере можно разместить в любом расположении папки, подходящем для вашего развертывания.

## <a name="plan-a-dns-alias-cname-record-for-your-web-server"></a><a name="bkmk_cname"></a>Планирование записи псевдонима DNS (CNAME) для веб-сервера
Записи ресурсов псевдонима (CNAME) также иногда называются каноническими записями ресурсов имен. С помощью этих записей можно указать несколько имен для указания на один узел, что упрощает выполнение таких операций, как размещение сервера протокол FTP (FTP) и веб-сервера на одном компьютере. Например, хорошо известные имена серверов (FTP, www) регистрируются с помощью записей ресурсов псевдонима (CNAME), которые сопоставляются с именем узла системы доменных имен (DNS), например WEB1, для сервера, на котором размещены эти службы.

Это краткое описание содержит инструкции по настройке веб-сервера для размещения списка отзыва сертификатов (CRL) для вашего центра сертификации (ЦС). Поскольку вы также можете использовать веб-сервер для других целей, например для размещения FTP или веб-сайта, рекомендуется создать запись ресурса псевдонима в DNS для веб-сервера. В этом пошаговом окне запись CNAME называется "PKI", но можно выбрать имя, подходящее для развертывания.

## <a name="plan-configuration-of-capolicyinf"></a><a name="bkmk_capolicy"></a>Настройка плана для файла CAPolicy. INF
Перед установкой AD CS необходимо настроить файл CAPolicy. INF в центре сертификации, указав в нем сведения, правильные для развертывания. Файл CAPolicy. inf содержит следующие сведения:

```
[Version]
Signature="$Windows NT$"
[PolicyStatementExtension]
Policies=InternalPolicy
[InternalPolicy]
OID=1.2.3.4.1455.67.89.5
Notice="Legal Policy Statement"
URL=https://pki.corp.contoso.com/pki/cps.txt
[Certsrv_Server]
RenewalKeyLength=2048
RenewalValidityPeriod=Years
RenewalValidityPeriodUnits=5
CRLPeriod=weeks
CRLPeriodUnits=1
LoadDefaultTemplates=0
AlternateSignatureAlgorithm=1
```

Для этого файла необходимо запланировать следующие элементы:

- **URL-адрес**. Пример файла CAPolicy. INF имеет значение URL-адреса **https://pki.corp.contoso.com/pki/cps.txt** . Это связано с тем, что веб-сервер в этом каталоге называется WEB1 и имеет запись ресурса DNS CNAME. Веб-сервер также присоединен к домену corp.contoso.com. Кроме того, на веб-сервере имеется виртуальный каталог с именем PKI, в котором хранится список отзыва сертификатов. Убедитесь, что значение, указываемое для URL-адреса в файле CAPolicy. INF, указывает на виртуальный каталог на веб-сервере в вашем домене.

- **Реневалкэйленгс**. Длина ключа продления по умолчанию для AD CS в Windows Server 2012 — 2048. Выбранная длина ключа должна быть максимально допустимой, а также обеспечивать совместимость с приложениями, которые предполагается использовать.

- **Реневалвалидитипериодунитс**. В примере файла CAPolicy. INF Реневалвалидитипериодунитс значение 5 лет. Это связано с тем, что ожидаемый срок существования ЦС составляет около десяти лет. Значение параметра Реневалвалидитипериодунитс должно отражать общий срок действия ЦС или наибольшее число лет, для которого требуется ввести регистрацию.

- **Крлпериодунитс**. Пример файла CAPolicy. INF имеет значение Крлпериодунитс, равное 1. Это связано с тем, что пример интервала обновления списка отзыва сертификатов в этом руководством составляет 1 неделю. В значении интервала, указанном с помощью этого параметра, необходимо опубликовать список отзыва сертификатов в ЦС в виртуальном каталоге веб-сервера, где хранится список отзыва сертификатов, и предоставить доступ к нему для компьютеров, которые находятся в процессе проверки подлинности.

- **Алтернатесигнатуреалгорисм**. В этом файле CAPolicy. INF реализован улучшенный механизм обеспечения безопасности путем реализации альтернативных форматов сигнатур. Не следует реализовывать этот параметр, если у вас по-прежнему есть клиенты Windows XP, которым требуются сертификаты из этого ЦС.

Если вы не планируете добавлять подчиненные ЦС в инфраструктуру открытых ключей позднее и вы хотите предотвратить добавление подчиненных ЦС, можно добавить ключ PathLength в файл CAPolicy. inf со значением 0. Чтобы добавить этот ключ, скопируйте и вставьте в файл следующий код:

```
[BasicConstraintsExtension]
PathLength=0
Critical=Yes
```

> [!IMPORTANT]
> Не рекомендуется изменять другие параметры в файле CAPolicy. INF, если у вас нет конкретной причины для этого.

## <a name="plan-configuration-of-the-cdp-and-aia-extensions-on-ca1"></a><a name="bkmk_cdp"></a>Планирование конфигурации CDP и AIA в CA1
При настройке точки распространения списка отзыва сертификатов (CDP) и параметров доступа к информации о центре сертификации (AIA) в CA1 вам потребуется имя веб-сервера и доменное имя. Кроме того, вам потребуется имя виртуального каталога, созданного на веб-сервере, где хранятся список отзыва сертификатов (CRL) и сертификат центра сертификации.

Расположение CDP, которое необходимо ввести во время этого шага развертывания, имеет следующий формат:

`http:\/\/*DNSAlias\(CNAME\)RecordName*.*Domain*.com\/*VirtualDirectoryName*\/<CaName><CRLNameSuffix><DeltaCRLAllowed>.crl.`

Например, если веб-сервер называется WEB1, а запись CNAME псевдонима DNS для веб-сервера — "PKI", домен находится в corp.contoso.com, а виртуальный каталог называется PKI, расположением CDP является:

`http:\/\/pki.corp.contoso.com\/pki\/<CaName><CRLNameSuffix><DeltaCRLAllowed>.crl`

Расположение AIA, которое необходимо ввести, имеет формат:

`http:\/\/*DNSAlias\(CNAME\)RecordName*.*Domain*.com\/*VirtualDirectoryName*\/<ServerDNSName>\_<CaName><CertificateName>.crt.`

Например, если веб-сервер называется WEB1, а запись CNAME псевдонима DNS для веб-сервера — "PKI", домен находится в corp.contoso.com, а виртуальный каталог называется PKI, расположение AIA:

`http:\/\/pki.corp.contoso.com\/pki\/<ServerDNSName>\_<CaName><CertificateName>.crt`

## <a name="plan-the-copy-operation-between-the-ca-and-the-web-server"></a><a name="bkmk_copy"></a>Планирование операции копирования между ЦС и веб-сервером
Чтобы опубликовать список отзыва сертификатов и сертификат ЦС из ЦС в виртуальный каталог веб-сервера, можно выполнить команду certutil-CRL после настройки расположений CDP и AIA в центре сертификации. Перед выполнением этой команды убедитесь в правильности путей на вкладке **расширения** свойств ЦС, следуя инструкциям в этом разделе. Кроме того, чтобы скопировать сертификат ЦС предприятия на веб-сервер, необходимо создать виртуальный каталог на веб-сервере и настроить папку как общую папку.

## <a name="plan-the-configuration-of-the-server-certificate-template-on-the-ca"></a><a name="bkmk_template"></a>Планирование конфигурации шаблона сертификата сервера в центре сертификации
Чтобы развернуть сертификаты сервера с автоматической регистрацией, необходимо скопировать шаблон сертификата **RAS и IAS Server**. По умолчанию эта копия называется **Копия RAS и IAS-сервера**. Если вы хотите переименовать эту копию шаблона, запланируйте имя, которое вы хотите использовать на этом шаге развертывания.

> [!NOTE]
> В последних трех разделах, посвященных развертыванию, которые позволяют настроить автоматическую регистрацию сертификата сервера, обновить групповая политика на серверах и убедиться, что серверы получили действительный сертификат сервера от центра сертификации — не требуются дополнительные этапы планирования.
