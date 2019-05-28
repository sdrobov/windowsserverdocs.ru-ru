---
ms.assetid: a3f50046-5d48-43d3-b0f8-ac2346b15285
title: Управление SSL-сертификатами в AD FS и WAP в Windows Server 2016
description: Управление SSL-сертификатами в AD FS и WAP в Windows Server 2016
author: jenfieldmsft
ms.author: billmath
manager: samueld
ms.date: 10/02/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 9bae831da9d247c423c2874a5928b7f811ef65dc
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66188708"
---
# <a name="managing-ssl-certificates-in-ad-fs-and-wap-in-windows-server-2016"></a>Управление SSL-сертификатами в AD FS и WAP в Windows Server 2016



В этой статье описывается развертывание нового SSL-сертификата на серверах AD FS и WAP.

>[!NOTE]
>Для замены SSL-сертификат, в дальнейшем для фермы AD FS рекомендуется использовать Azure AD Connect.  Дополнительные сведения см. в разделе [обновление SSL-сертификата для фермы служб федерации Active Directory (AD FS)](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectfed-ssl-update)

## <a name="obtaining-your-ssl-certificates"></a>Получение SSL-сертификаты
Для фермы AD FS рабочей среде рекомендуется использовать общедоступный доверенный SSL-сертификат. Это обычно получается путем отправки подписи запроса сертификата (CSR) третьим лицам, общедоступный поставщик сертификатов. Существует множество способов создания CSR-файла, в том числе с Windows 7 или более поздней версии ПК. Поставщик должен иметь документации для этого.

- Убедитесь, что сертификат соответствует [требований к сертификатам AD FS и Интернет-приложения прокси-сервера, протокола SSL](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/overview/AD-FS-2016-Requirements#BKMK_1)

### <a name="how-many-certificates-are-needed"></a>Сколько сертификатов необходимы
Рекомендуется использовать общие SSL-сертификата на серверах все AD FS и прокси веб-приложения. Подробные сведения о требованиях к см. на [требований к сертификатам AD FS и Интернет-приложения прокси-сервера, протокола SSL](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/overview/AD-FS-2016-Requirements#BKMK_1)

### <a name="ssl-certificate-requirements"></a>Требования сертификатов SSL
Требования, включая именования, корневого доверия и расширений см. в документе [требований к сертификатам AD FS и Интернет-приложения прокси-сервера, протокола SSL](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/overview/AD-FS-2016-Requirements#BKMK_1)

## <a name="replacing-the-ssl-certificate-for-ad-fs"></a>Замена SSL-сертификата для AD FS
> [!NOTE]
> AD FS SSL-сертификат не является таким же, как обнаруженный в оснастке управления AD FS communications сертификат службы AD FS. Чтобы изменить сертификат AD FS SSL, необходимо использовать PowerShell.

Сначала определите, какой сертификат режим привязки серверы AD FS работают под: по умолчанию сертификат проверки подлинности привязки или режим привязки TLS другой клиент.

### <a name="replacing-the-ssl-certificate-for-ad-fs-running-in-default-certificate-authentication-binding-mode"></a>Замена SSL-сертификата для AD FS, работающие в основной режим привязки сертификата проверки подлинности
AD FS по умолчанию выполняет проверку подлинности сертификата устройства на порт 443 и проверка подлинности сертификата пользователя через порт 49443 (или можно настроить порт, который не 443).
В этом режиме используйте командлет powershell Set-AdfsSslCertificate управление SSL-сертификат.

Выполните инструкции ниже.

1. Во-первых необходимо получить новый сертификат. Обычно это делается путем отправки подписи запроса сертификата (CSR) третьим лицам, общедоступный поставщик сертификатов. Существует множество способов создания CSR-файла, в том числе с Windows 7 или более поздней версии ПК. Поставщик должен иметь документации для этого.

    * Убедитесь, что сертификат соответствует [требований к сертификатам AD FS и Интернет-приложения прокси-сервера, протокола SSL](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/overview/AD-FS-2016-Requirements#BKMK_1)

1. После получения ответа от поставщика сертификата, он импортируется в хранилище локального компьютера на каждом сервере AD FS и прокси веб-приложения.

1. На **основной** сервера AD FS, используйте следующий командлет для установки нового SSL-сертификата

```powershell
Set-AdfsSslCertificate -Thumbprint '<thumbprint of new cert>'
```

Отпечаток сертификата можно найти, выполнив следующую команду:

```powershell
dir Cert:\LocalMachine\My\
```

#### <a name="additional-notes"></a>Дополнительные замечания

* Командлет Set-AdfsSslCertificate — это командлет несколькими узлами; Это означает, что только должно запускаться с сервера-источника и будут обновлены все узлы в ферме. Это является новым в Server 2016. На Server 2012 R2 необходимо было выполнить Set-AdfsSslCertificate на каждом сервере.
* Командлет Set-AdfsSslCertificate должен быть запущен только на сервере-источнике. Основной сервер должен работать под управлением Server 2016 и на уровне поведения фермы должен быть повышен до 2016.
* Командлет Set-AdfsSslCertificate будет использовать удаленное взаимодействие PowerShell для настройки других серверов AD FS, убедитесь, что порт 5985 (TCP) открыт на других узлах.
* Командлет Set-AdfsSslCertificate предоставит adfssrv участника разрешения на чтение к закрытым ключам SSL-сертификата. Этот участник представляет службу AD FS. Не бывает необходимо предоставить доступ чтение учетной записи службы AD FS к закрытым ключам SSL-сертификата.

### <a name="replacing-the-ssl-certificate-for-ad-fs-running-in-alternate-tls-binding-mode"></a>Замена SSL-сертификата для AD FS, работающие в режиме чередования привязки TLS
Если это настроено в другой клиент режим привязки TLS, AD FS выполняет проверку подлинности сертификата устройства на порт 443 и проверка подлинности сертификата пользователя через порт 443, различных имени узла. Имя узла сертификата пользователя добавляется AD FS имя узла с «certauth», например «certauth.fs.contoso.com».
В этом режиме используйте командлет powershell Set-AdfsAlternateTlsClientBinding управление SSL-сертификат. Это будет управлять не только привязки TLS альтернативные клиента, но все привязки, на которых службы AD FS задают также SSL-сертификат.

Выполните инструкции ниже.

1. Во-первых необходимо получить новый сертификат. Обычно это делается путем отправки подписи запроса сертификата (CSR) третьим лицам, общедоступный поставщик сертификатов. Существует множество способов создания CSR-файла, в том числе с Windows 7 или более поздней версии ПК. Поставщик должен иметь документации для этого.

    * Убедитесь, что сертификат соответствует [требований к сертификатам AD FS и Интернет-приложения прокси-сервера, протокола SSL](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/overview/AD-FS-2016-Requirements#BKMK_1)

1. После получения ответа от поставщика сертификата, он импортируется в хранилище локального компьютера на каждом сервере AD FS и прокси веб-приложения.

1. На **основной** сервера AD FS, используйте следующий командлет для установки нового SSL-сертификата

```powershell
Set-AdfsAlternateTlsClientBinding -Thumbprint '<thumbprint of new cert>'
```

Отпечаток сертификата можно найти, выполнив следующую команду:

```powershell
dir Cert:\LocalMachine\My\
```

#### <a name="additional-notes"></a>Дополнительные замечания

* Командлет Set-AdfsAlternateTlsClientBinding — это командлет несколькими узлами; Это означает, что только должно запускаться с сервера-источника и будут обновлены все узлы в ферме.
* Командлет Set-AdfsAlternateTlsClientBinding должен быть запущен только на сервере-источнике. Основной сервер должен работать под управлением Server 2016 и на уровне поведения фермы должен быть повышен до 2016.
* Командлет Set-AdfsAlternateTlsClientBinding будет использовать удаленное взаимодействие PowerShell для настройки других серверов AD FS, убедитесь, что порт 5985 (TCP) открыт на других узлах.
* Командлет Set-AdfsAlternateTlsClientBinding предоставит adfssrv участника разрешения на чтение к закрытым ключам SSL-сертификата. Этот участник представляет службу AD FS. Не бывает необходимо предоставить доступ чтение учетной записи службы AD FS к закрытым ключам SSL-сертификата.

## <a name="replacing-the-ssl-certificate-for-the-web-application-proxy"></a>Замена SSL-сертификат для прокси веб-приложения
Для настройки привязки проверки подлинности сертификата по умолчанию, и в режиме привязки TLS другой клиент на WAP мы используем командлет Set-WebApplicationProxySslCertificate.
Для замены веб приложение прокси, SSL-сертификат, на **каждого** server прокси веб-приложения используйте следующий командлет, чтобы установить новый SSL-сертификат:

```powershell
Set-WebApplicationProxySslCertificate '<thumbprint of new cert>'
```

Если указанный выше командлет завершается сбоем из-за истечения срока действия старого сертификата, перенастройте прокси с помощью следующих командлетов:

```powershell
$cred = Get-Credential
```

Введите учетные данные пользователя домена, являющийся локальным администратором на сервере AD FS

```powershell
Install-WebApplicationProxy -FederationServiceTrustCredential $cred -CertificateThumbprint '<thumbprint of new cert>' -FederationServiceName 'fs.contoso.com'
```

## <a name="additional-references"></a>Дополнительная справка  
* [Поддержка привязки альтернативного имени узла для аутентификации сертификата в AD FS](../operations/AD-FS-support-for-alternate-hostname-binding-for-certificate-authentication.md)
* [Службы федерации Active Directory и сертификат свойства KeySpec сведения](../technical-reference/AD-FS-and-KeySpec-Property.md)
