---
ms.assetid: a3f50046-5d48-43d3-b0f8-ac2346b15285
title: "Управление SSL-сертификатов в AD FS и WAP в Windows Server 2016"
description: "Управление SSL-сертификатов в AD FS и WAP в Windows Server 2016"
author: jenfieldmsft
ms.author: billmath
manager: samueld
ms.date: 10/02/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 5156b3ad357ab8edb5e08a89a459beaf9b8c9b1a
ms.sourcegitcommit: ca7dc3d56a33924ae5fe0e9ffb1274da6dc4e54d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2017
---
# <a name="managing-ssl-certificates-in-ad-fs-and-wap-in-windows-server-2016"></a>Управление SSL-сертификатов в AD FS и WAP в Windows Server 2016

>Область применения: Windows Server 2016

В этой статье описывается развертывание новый сертификат SSL для Служб федерации Active Directory и WAP серверов.

>[!NOTE]
>Чтобы заменить сертификат SSL для фермы AD FS в дальнейшем рекомендуется использовать Azure AD Connect.  Дополнительные сведения см. [обновить сертификат SSL для фермы служб федерации Active Directory (AD FS)](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectfed-ssl-update)

## <a name="obtaining-your-ssl-certificates"></a>Получение сертификатов SSL
Для ферм производственных Служб федерации Active Directory рекомендуется использовать открытый доверенный SSL-сертификат. Обычно получается путем отправки подписи запроса сертификата (CSR) третьим лицам, открытый сертификат поставщика. Существует множество способов создания представителем отдела обслуживания Клиентов, включая компьютер Windows 7 или более поздней версии. Ваш поставщик должен владеть документации для этого.

- Убедитесь, что сертификат соответствует [AD FS и SSL прокси-сервера приложений Web требований к сертификатам](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-fs/overview/AD-FS-2016-Requirements#BKMK_1)

### <a name="how-many-certificates-are-needed"></a>Сколько сертификаты потребуются
Рекомендуется использовать общие SSL-сертификата на серверах все службы федерации Active Directory и прокси веб-приложения. Подробные требования см. документ [AD FS и SSL прокси-сервера приложений Web требований к сертификатам](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-fs/overview/AD-FS-2016-Requirements#BKMK_1)

### <a name="ssl-certificate-requirements"></a>Требования сертификатов SSL
Требования к, включая именования, корень доверия и расширения см. в документе [AD FS и SSL прокси-сервера приложений Web требований к сертификатам](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-fs/overview/AD-FS-2016-Requirements#BKMK_1)

## <a name="replacing-the-ssl-certificate-for-ad-fs"></a>Замена SSL-сертификата для AD FS
> [!NOTE]
> AD FS SSL-сертификата не совпадает с сертификатом связи со службой AD FS, найти в оснастке управления AD FS. Чтобы изменить сертификат AD FS SSL, необходимо будет использовать PowerShell.

Во-первых, определить, какой сертификат режиме привязки серверов Служб федерации Active Directory: привязка проверки подлинности сертификата по умолчанию или режим привязки альтернативного клиента TLS.

### <a name="replacing-the-ssl-certificate-for-ad-fs-running-in-default-certificate-authentication-binding-mode"></a>Замена SSL-сертификата для AD FS под управлением по умолчанию режим привязки сертификата проверки подлинности
AD FS по умолчанию выполняет проверку подлинности сертификата устройства через порт 443 и проверку подлинности сертификата через порт 49443 (или настраиваемые порт, который не является 443).
В этом режиме используйте командлет powershell Set-AdfsSslCertificate управление SSL-сертификат.

Выполните следующие действия:

1. Во-первых необходимо получить новый сертификат. Обычно это делается, передавая подписи запроса сертификата (CSR) третьим лицам, открытый сертификат поставщика. Существует множество способов создания представителем отдела обслуживания Клиентов, включая компьютер Windows 7 или более поздней версии. Ваш поставщик должен владеть документации для этого.

    * Убедитесь, что сертификат соответствует [AD FS и SSL прокси-сервера приложений Web требований к сертификатам](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-fs/overview/AD-FS-2016-Requirements#BKMK_1)

1. После получения ответа от поставщика сертификата, импортируйте его в хранилище локального компьютера на каждом сервере Служб федерации Active Directory и прокси веб-приложения.

1. На **основной** сервера AD FS, используйте следующий командлет, чтобы установить новый сертификат SSL

```powershell
Set-AdfsSslCertificate -Thumbprint '<thumbprint of new cert>'
```

Отпечаток сертификата можно найти с помощью этой команды:

```powershell
dir Cert:\LocalMachine\My\
```

#### <a name="additional-notes"></a>Дополнительные замечания

* Командлет Set-AdfsSslCertificate — это командлет несколькими узлами; Это означает, что у него есть только для запуска с сервера-источника, и будет обновлено все узлы в ферме. Это новая в Server 2016. В Server 2012 R2 необходимо было выполнить набор AdfsSslCertificate на каждом сервере.
* Командлет Set-AdfsSslCertificate должен быть запущен только на основном сервере. Основной сервер должен работать под управлением Server 2016 и на уровне фермы поведение должен быть повышен до 2016.
* Командлет Set-AdfsSslCertificate будет использовать удаленное взаимодействие PowerShell для настройки других серверов Служб федерации Active Directory, убедитесь, что открыт порт 5985 (TCP) на других узлах.
* Командлет Set-AdfsSslCertificate будет предоставить adfssrv участника разрешения на чтение к закрытым ключам SSL-сертификата. Этот участник представляет службу AD FS. Нет необходимости предоставить учетной записи службы AD FS чтения доступа к закрытым ключам SSL-сертификат.

### <a name="replacing-the-ssl-certificate-for-ad-fs-running-in-alternate-tls-binding-mode"></a>Замена SSL-сертификата для AD FS, работающий в режиме привязки альтернативного TLS
При настройке в другой клиент режим привязки TLS, AD FS выполняет проверку подлинности сертификата устройства через порт 443 и проверку подлинности сертификата на порте 443, а также на различных имени узла. Имя узла сертификата пользователя является пред ожидающей имени узла службы федерации Active Directory с «certauth», например «certauth.fs.contoso.com».
В этом режиме используйте командлет powershell Set-AdfsAlternateTlsClientBinding управление SSL-сертификат. Это будет управлять не только привязку протоколы TLS, но все привязки, на которых службы AD FS задают также SSL-сертификат.

Выполните следующие действия:

1. Во-первых необходимо получить новый сертификат. Обычно это делается, передавая подписи запроса сертификата (CSR) третьим лицам, открытый сертификат поставщика. Существует множество способов создания представителем отдела обслуживания Клиентов, включая компьютер Windows 7 или более поздней версии. Ваш поставщик должен владеть документации для этого.

    * Убедитесь, что сертификат соответствует [AD FS и SSL прокси-сервера приложений Web требований к сертификатам](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-fs/overview/AD-FS-2016-Requirements#BKMK_1)

1. После получения ответа от поставщика сертификата, импортируйте его в хранилище локального компьютера на каждом сервере Служб федерации Active Directory и прокси веб-приложения.

1. На **основной** сервера AD FS, используйте следующий командлет, чтобы установить новый сертификат SSL

```powershell
Set-AdfsAlternateTlsClientBinding -Thumbprint '<thumbprint of new cert>'
```

Отпечаток сертификата можно найти с помощью этой команды:

```powershell
dir Cert:\LocalMachine\My\
```

#### <a name="additional-notes"></a>Дополнительные замечания

* Командлет Set-AdfsAlternateTlsClientBinding — это командлет несколькими узлами; Это означает, что у него есть только для запуска с сервера-источника, и будет обновлено все узлы в ферме.
* Командлет Set-AdfsAlternateTlsClientBinding должен быть запущен только на основном сервере. Основной сервер должен работать под управлением Server 2016 и на уровне фермы поведение должен быть повышен до 2016.
* Командлет Set-AdfsAlternateTlsClientBinding будет использовать удаленное взаимодействие PowerShell для настройки других серверов Служб федерации Active Directory, убедитесь, что открыт порт 5985 (TCP) на других узлах.
* Командлет Set-AdfsAlternateTlsClientBinding будет предоставить adfssrv участника разрешения на чтение к закрытым ключам SSL-сертификата. Этот участник представляет службу AD FS. Нет необходимости предоставить учетной записи службы AD FS чтения доступа к закрытым ключам SSL-сертификат.

## <a name="replacing-the-ssl-certificate-for-the-web-application-proxy"></a>Замена SSL-сертификат для прокси веб-приложения
Для настройки и привязка проверки подлинности сертификата по умолчанию, или режим привязки альтернативного клиента TLS на WAP можно использовать командлет Set-WebApplicationProxySslCertificate.
Чтобы заменить сертификат SSL прокси-сервера приложений Web на **каждого** сервера прокси веб-приложения используйте следующий командлет, чтобы установить новый сертификат SSL:

```powershell
Set-WebApplicationProxySslCertificate '<thumbprint of new cert>'
```

Если выше командлет завершается с ошибкой, поскольку старого сертификата уже истек, перенастройте прокси-сервера, используя следующие командлеты:

```powershell
$cred = Get-Credential
```

Введите учетные данные пользователя домена, являющегося локальным администратором на сервере AD FS

```powershell
Install-WebApplicationProxy -FederationServiceTrustCredential $cred -CertificateThumbprint '<thumbprint of new cert>' -FederationServiceName 'fs.contoso.com'
```

## <a name="additional-references"></a>Дополнительные ссылки  
* [Поддержка привязки альтернативного имени узла для проверки подлинности сертификата в AD FS](../operations/AD-FS-support-for-alternate-hostname-binding-for-certificate-authentication.md)
* [Службы федерации Active Directory и сертификат KeySpec свойства сведения](../technical-reference/AD-FS-and-KeySpec-Property.md)
