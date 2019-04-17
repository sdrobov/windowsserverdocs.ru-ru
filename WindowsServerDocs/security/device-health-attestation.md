---
title: "Аттестация работоспособности устройства"
H1: na
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.technology:
- techgroup-security
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e7b77a4-1c6a-4c21-8844-0df89b63f68d
author: brianlic-msft
ms.date: 10/12/2016
ms.openlocfilehash: d304ee3456f8db1e5b202c1d9221d1374a5251be
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="device-health-attestation"></a>Аттестация работоспособности устройства

>Область применения: Windows Server 2016

В Windows 10 версии 1507 аттестации работоспособности устройства (DHA) появилось следующее:

-   Интеграция с платформой управления мобильными устройствами (MDM) Windows 10 с соблюдением [стандартов Open Mobile Alliance (OMA)](http://openmobilealliance.org/).

-   Поддержка устройств, имеющих доверенный платформенный модуль (TPM) в встроенном по или отдельно.

-   Обеспечивает повышение безопасности организации на оборудование отслеживания и подтверждения безопасности с минимальными или без существенного роста эксплуатационных расходов.

Начиная с Windows Server 2016, можно теперь запускать службу DHA в роли сервера в вашей организации. Используйте этот раздел, чтобы узнать, как установить и настроить роль сервера аттестации работоспособности устройства.

## <a name="overview"></a>Обзор

DHA можно использовать для оценки состояния устройства для:
  
-   Устройства Windows 10 и Windows 10 Mobile, которые поддерживают TPM 1.2 или 2.0.  
-   Локальные устройства, управление которыми осуществляется с помощью Active Directory с доступом в Интернет, устройств, управляемых с помощью Active Directory без подключения к Интернету, устройства, управляемые с Azure Active Directory или гибридного развертывания, с помощью Active Directory и Azure Active Directory.


### <a name="dha-service"></a>Служба DHA

Служба DHA проверяет для устройства журналы доверенного платформенного МОДУЛЯ и PCR, а затем составляет по ним отчет DHA. Корпорация Майкрософт предлагает три варианта службы DHA.

- **Облачная служба DHA** корпорацией Майкрософт управляемая служба DHA предоставляется бесплатно, оснащена географической балансировкой нагрузки и оптимизирована для доступа из разных регионов мира.

- **DHA локальная служба** новой роли сервера, начиная с Windows Server 2016. Он доступен бесплатно всем клиентам с лицензией Windows Server 2016.

- **Облачная служба DHA Azure** на виртуальном узле в Microsoft Azure. Для этого нужен виртуальный узел и лицензии для локальной службы DHA.

Служба DHA интегрируется с решениями MDM и предоставляет следующие возможности: 

-   Объединение данных, полученных от устройства (с помощью существующих управления каналов устройством) с отчетом DHA
-   Повышение надежности и безопасности решений на основе подтверждении и защите данных

Вот пример, в котором показано, как использовать DHA для надежной защиты активов вашей организации.

1. Создайте политику, которая проверяет такие конфигурации и атрибуты загрузки:
  - Безопасная загрузка
  - BitLocker
  - ELAM
2. Решение MDM применяет эту политику и запускает действия по исправлению на основании данных отчета DHA.  Например можно проверить следующее:
  - Включена безопасная загрузка, в устройство загружен доверенный код, и загрузчик Windows не подвергался изменениям.
  - Доверенный загрузчик успешно проверил цифровую подпись ядра Windows и компонентов, которые были загружены при запуске устройства.
  - Процесс измеряемой загрузки создал отчет аудита, защищенный доверенным платформенным Модулем, который можно проверить удаленно.
  - Отключить BitLocker был включен и защищал данные, пока устройство было отключено.
  - ELAM был включен на ранних этапах загрузки и контролировал среды выполнения.
  
#### <a name="dha-cloud-service"></a>Облачная служба DHA

Облачная служба DHA предоставляет следующие преимущества:

-   Просматривает TCG и PCR журналы загрузки устройства, полученные от устройства, зарегистрированного в решении MDM; 
-   Создает защищенный и устойчивый очевидно, что отчет (отчет DHA) о процессе запуска устройства на основе данных, собранных и защищены микросхемой TPM устройства. 
-   Сервер MDM, который запрашивал отчета в защищенный коммуникационный канал доставляет отчет DHA.

#### <a name="dha-on-premises-service"></a>Локальная служба DHA

Локальная служба DHA предоставляет все возможности, предоставляемые в облачной службе DHA.  Он также позволяет пользователям:

 - Оптимизирует производительность, как служба DHA работает в собственном центре обработки данных
 - Убедитесь, что отчет DHA не выходит за пределы сети

#### <a name="dha-azure-cloud-service"></a>Облачная служба DHA Azure

Эта служба предоставляет те же функции локальную службу DHA, за исключением того, что облачная служба DHA Azure выполняется в виде виртуального узла в Microsoft Azure.

### <a name="dha-validation-modes"></a>Режимы проверки DHA

Локальная служба DHA можно настроить для работы в режиме проверки EKCert или AIKCert. Служба DHA создает отчет, указывает, если он выдан в режиме проверки AIKCert или EKCert. EKCert режимы проверки AIKCert и обеспечивают же безопасность до тех пор, пока поддерживается актуальность цепочки сертификатов ekcert.

#### <a name="ekcert-validation-mode"></a>Режим проверки EKCert

Режим проверки EKCert оптимизирован для устройств в организации, которые не подключены к Интернету. Устройства, подключаемые к службе DHA, работающей в режиме проверки EKCert **не** иметь прямой доступ к Интернету.

Когда DHA работает в режиме проверки EKCert, она основывается на цепочке доверия, необходимо периодически обновлять (примерно 5 – 10 раз в год). 

Корпорация Майкрософт публикует объединенные пакеты доверенных корневых и промежуточных ЦС всех авторизованных производителей TPM (как они становятся доступны) в архиве общедоступного CAB-архива. Необходимо загрузить этот поток, проверить его целостность и установить его на сервер подтверждения работоспособности устройства.

Является архивом пример [https://tpmsec.microsoft.com/OnPremisesDHA/TrustedTPM.cab](https://tpmsec.microsoft.com/OnPremisesDHA/TrustedTPM.cab).

#### <a name="aikcert-validation-mode"></a>Режим проверки AIKCert

Режим проверки AIKCert оптимизирован для производственных сред, которые имеют доступ к Интернету. Устройства, подключаемые к службе DHA, работающей в режиме проверки AIKCert, должны иметь прямой доступ к Интернету и возможность получить сертификат AIK от корпорации Майкрософт. 

## <a name="install-and-configure-the-dha-service-on-windows-server-2016"></a>Установка и настройка службы DHA в ОС Windows Server 2016

Используйте следующие разделы для получения DHA устанавливается и настраивается на Windows Server 2016.

### <a name="prerequisites"></a>Предварительные требования

Чтобы настроить и проверить локальную службу DHA, вы должны:

- Сервер под управлением Windows Server 2016.
- Создать один (или более) Windows 10 клиентских устройств с доверенным платформенным Модулем (1.2 или 2.0) находится в состоянии готовности, под управлением последних программы предварительной оценки Windows.
- Решите, если вы собираетесь запустить в режиме проверки EKCert или AIKCert.
- Такие сертификаты:
  - **SSL-сертификат DHA** SSL-сертификат x.509, который связан доверенным корневым экспортируемым закрытым ключом. Этот сертификат защищает данные dha в том числе при передаче сервера на сервер (служба DHA и сервер MDM) и сервера к клиенту (служба DHA и устройство с Windows 10).
  - **Сертификат подписи DHA** сертификат x.509, который связан доверенным корневым экспортируемым закрытым ключом. Служба DHA использует этот сертификат для цифрового подписывания. 
  - **Сертификат шифрования DHA** сертификат x.509, который связан доверенным корневым экспортируемым закрытым ключом. Служба DHA использует этот сертификат для шифрования. 


### <a name="install-windows-server-2016"></a>Установка Windows Server 2016

Установите Windows Server 2016 любым удобным для вас способом, например служб развертывания Windows, или запустив установщик на загрузочном носителе, USB-накопитель или в локальной файловой системе. Если это первый раз, вы настраиваете локальную службу DHA, устанавливайте Windows Server 2016 с помощью **возможности рабочего стола** вариант установки.

### <a name="add-the-device-health-attestation-server-role"></a>Добавление роли сервера для подтверждения работоспособности устройства

С помощью диспетчера сервера можно установить роль сервера аттестации работоспособности устройства и его зависимостей. 

После установки Windows Server 2016 устройство перезапускается и открывает диспетчер сервера. Если диспетчер сервера не запускается автоматически, нажмите кнопку **запустить**, а затем нажмите кнопку **диспетчера сервера**.

1.  Нажмите кнопку **Добавить роли и компоненты**.
2.  На **перед началом** щелкните **Далее**.
3.  На **Выбор типа установки** щелкните **Установка на основе ролей или компонентов**, а затем нажмите кнопку **Далее**.
4.  На **Выбор целевого сервера** щелкните **выберите сервер из пула серверов**, выберите сервер и нажмите кнопку **Далее**.
5.  На **Выбор ролей сервера** выберите **аттестации работоспособности устройства** флажок.
6.  Нажмите кнопку **добавить компоненты** Чтобы установить другие необходимые службы ролей и компоненты.
7.  Нажмите кнопку **Далее**.
8.  На **выберите компоненты** щелкните **Далее**.
9.  На **роль веб-сервера (IIS)** щелкните **Далее**.
10. На **Выбор служб ролей** щелкните **Далее**.
11. На **службе аттестации работоспособности устройства** щелкните **Далее**.
12. На **подтверждение выбранных элементов для установки** щелкните **установить**.
13. По завершении установки нажмите кнопку **закрыть**.

### <a name="install-the-signing-and-encryption-certificates"></a>Установка сертификатов подписи и шифрования

Используйте следующий сценарий Windows PowerShell для установки сертификатов подписи и шифрования. Дополнительные сведения о отпечаток см. в разделе [как: Извлеките отпечаток сертификата](https://msdn.microsoft.com/library/ms734695.aspx).

```
$key = Get-ChildItem Cert:\LocalMachine\My | Where-Object {$_.Thumbprint -like "<thumbprint>"}
$keyname = $key.PrivateKey.CspKeyContainerInfo.UniqueKeyContainerName
$keypath = $env:ProgramData + "\Microsoft\Crypto\RSA\MachineKeys\" + $keyname
icacls $keypath /grant <username>`:R
  
#<thumbprint>: Certificate thumbprint for encryption certificate or signing certificate
#<username>: Username for web service app pool, by default IIS_IUSRS
```

### <a name="install-the-trusted-tpm-roots-certificate-package"></a>Устанавливать пакет сертификатов доверенных корневых ЦС доверенного платформенного МОДУЛЯ

Для установки пакета сертификата корни доверенного платформенного МОДУЛЯ, необходимо извлечь его, удалите все цепочки сертификатов, которые не являются доверенными для вашей организации и запустите команду setup.cmd.

#### <a name="download-the-trusted-tpm-roots-certificate-package"></a>Загрузка пакета сертификата корни доверенного платформенного МОДУЛЯ

Прежде чем устанавливать пакет сертификатов, вы можете скачать самый свежий список корневых ЦС для доверенного платформенного МОДУЛЯ из [https://tpmsec.microsoft.com/OnPremisesDHA/TrustedTPM.cab](https://tpmsec.microsoft.com/OnPremisesDHA/TrustedTPM.cab).

> **Важно:** перед установкой пакета проверьте цифровую подпись Майкрософт.

#### <a name="extract-the-trusted-certificate-package"></a>Чтобы извлечь пакет доверенных сертификатов
Извлечение пакет доверенных сертификатов, выполнив следующие команды.
```
mkdir .\TrustedTpm
expand -F:* .\TrustedTpm.cab .\TrustedTpm
```

#### <a name="remove-the-trust-chains-for-tpm-vendors-that-are-not-trusted-by-your-organization-optional"></a>Удалите цепочки доверия тех поставщиков доверенных Платформенных модулей, которые являются *не* доверенными для вашей организации (необязательно)

Удалите папки любых поставщика цепочек доверия, не являются доверенными для вашей организации.

> **Примечание:** в режиме сертификата AIK требуется папка Microsoft для проверки сертификатов AIK, выданных корпорацией Майкрософт.

#### <a name="install-the-trusted-certificate-package"></a>Установка пакета доверенных сертификатов
Для установки пакета доверенных сертификатов запустите сценарий установки из CAB-файла.

```
.\setup.cmd
```

### <a name="configure-the-device-health-attestation-service"></a>Настройка службы подтверждения работоспособности устройств

Windows PowerShell можно использовать для настройки локальной службы DHA.

```
Install-DeviceHealthAttestation -EncryptionCertificateThumbprint <encryption> -SigningCertificateThumbprint <signing> -SslCertificateStoreName My -SslCertificateThumbprint <ssl> -SupportedAuthenticationSchema "<schema>"

#<encryption>: Thumbprint of the encryption certificate
#<signing>: Thumbprint of the signing certificate
#<ssl>: Thumbprint of the SSL certificate
#<schema>: Comma-delimited list of supported schemas including AikCertificate, EkCertificate, and AikPub
```

### <a name="configure-the-certificate-chain-policy"></a>Чтобы настроить политику цепочки сертификатов

Настройка политики цепочки сертификатов, выполнив следующий сценарий Windows PowerShell.

```
$policy = Get-DHASCertificateChainPolicy
$policy.RevocationMode = "NoCheck"
Set-DHASCertificateChainPolicy -CertificateChainPolicy $policy
```

## <a name="dha-management-commands"></a>Команды управления DHA

Ниже приведены некоторые командлеты Windows PowerShell, которые помогут вам управлять службой DHA.

### <a name="configure-the-dha-service-for-the-first-time"></a>Настройка службы DHA в первый раз

```
Install-DeviceHealthAttestation -SigningCertificateThumbprint "<HEX>" -EncryptionCertificateThumbprint "<HEX>" -SslCertificateThumbprint "<HEX>" -Force
```

### <a name="remove-the-dha-service-configuration"></a>Удаление конфигурации службы DHA

```
Uninstall-DeviceHealthAttestation -RemoveSslBinding -Force
```
### <a name="get-the-active-signing-certificate"></a>Получение активного сертификата подписи

```
Get-DHASActiveSigningCertificate
```
### <a name="set-the-active-signing-certificate"></a>Установка активного сертификата подписи

```
Set-DHASActiveSigningCertificate -Thumbprint "<hex>" -Force
```

> **Примечание:** этот сертификат должен быть развернут на сервере с запущенной службой DHA **LocalMachine\My** хранилище сертификатов. Если задана активного сертификата подписи, бывший активный сертификат подписи перемещается в список неактивных сертификатов подписи.

### <a name="list-the-inactive-signing-certificates"></a>Получение списка неактивных сертификатов подписи
```
Get-DHASInactiveSigningCertificates
```

### <a name="remove-any-inactive-signing-certificates"></a>Удаление неактивных сертификатов подписи
```
Remove-DHASInactiveSigningCertificates -Force
Remove-DHASInactiveSigningCertificates  -Thumbprint "<hex>" -Force
```

> **Примечание:** только *один* в службе может существовать неактивный сертификата (любого типа) в любое время. Сертификаты следует удалять из списка неактивных сертификатов, когда они больше не требуются.

### <a name="get-the-active-encryption-certificate"></a>Получение активного сертификата шифрования

```
Get-DHASActiveEncryptionCertificate
```

### <a name="set-the-active-encryption-certificate"></a>Задайте активного сертификата шифрования

```
Set-DHASActiveEncryptionCertificate -Thumbprint "<hex>" -Force
```

Этот сертификат должен быть развернут на устройстве в **LocalMachine\My** хранилище сертификатов. 

Если задана активный сертификат шифрования, существующие активный сертификат шифрования перемещается в список неактивных сертификатов шифрования.

### <a name="list-the-inactive-encryption-certificates"></a>Список неактивных сертификатов шифрования

```
Get-DHASInactiveEncryptionCertificates
```
### <a name="remove-any-inactive-encryption-certificates"></a>Удаление неактивных сертификатов шифрования

```
Remove-DHASInactiveEncryptionCertificates -Force
Remove-DHASInactiveEncryptionCertificates -Thumbprint "<hex>" -Force 
```

### <a name="get-the-x509chainpolicy-configuration"></a>Получение конфигурации X509ChainPolicy 

```
Get-DHASCertificateChainPolicy
```
### <a name="change-the-x509chainpolicy-configuration"></a>Изменение конфигурации X509ChainPolicy

```
$certificateChainPolicy = Get-DHASInactiveEncryptionCertificates
$certificateChainPolicy.RevocationFlag = <X509RevocationFlag>
$certificateChainPolicy.RevocationMode = <X509RevocationMode>
$certificateChainPolicy.VerificationFlags = <X509VerificationFlags>
$certificateChainPolicy.UrlRetrievalTimeout = <TimeSpan>
Set-DHASCertificateChainPolicy = $certificateChainPolicy
```

## <a name="dha-service-reporting"></a>Создание отчетов в службе DHA

Ниже приводится список сообщений, которые были зарегистрированы службой DHA в решение MDM. 

- **200** ОК HTTP. Сертификат возвращен.
- **400** Ошибочный запрос. Недопустимый формат запроса, недопустимый сертификат работоспособности, подписи сертификата не поддерживает соответствие, недопустимый BLOB-объект подтверждения работоспособности или недопустимый двоичный состояние. Ответ также содержит сообщение, как описано в схеме ответа, содержащее код ошибки и сообщение об ошибке, которые можно использовать для диагностики.
- **500** Внутренняя ошибка сервера. Это может произойти, если возникают проблемы, которые предотвращают выдачу сертификатов службы.
- **503** система регулирования отклоняет запросы, чтобы предотвратить перегрузку сервера. 