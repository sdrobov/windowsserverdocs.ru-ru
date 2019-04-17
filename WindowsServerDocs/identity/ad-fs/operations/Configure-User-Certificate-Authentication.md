---
ms.assetid: 1ea2e1be-874f-4df3-bc9a-eb215002da91
title: "Настройка поддержки AD FS для проверки подлинности сертификата пользователя"
description: 
author: jenfieldmsft
ms.author: billmath
manager: samueld
ms.date: 01/18/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.service: active-directory
ms.technology: identity-adfs
ms.openlocfilehash: 9941d4dd997e857874aceddc920ec7f9d8944a81
ms.sourcegitcommit: d351cdbb0bf2533d6db35626ebbc4924b3834309
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2018
---
# <a name="configuring-ad-fs-for-user-certificate-authentication"></a>Настройка AD FS для проверки подлинности сертификата пользователя

>Область применения: Windows Server 2016, Windows Server 2012 R2

Службы федерации Active Directory можно настроить для x509 с помощью одного из режимов проверки подлинности сертификата пользователя описано в [в этой статье](ad-fs-support-for-alternate-hostname-binding-for-certificate-authentication.md). Эта возможность может использоваться [с Azure Active Directory](https://blogs.msdn.microsoft.com/samueld/2016/07/19/adfs-certauth-aad-o365/) или самостоятельно, чтобы включить клиентов и устройств предоставлен сертификаты пользователей для доступа к AD FS ресурсы из интрасети или экстрасети.

## <a name="prerequisites"></a>Предварительные требования
- Убедитесь, что сертификатов пользователя являются доверенными для всех Служб федерации Active Directory и WAP серверов
- Убедитесь, что корневой сертификат цепочки сертификатов для сертификатов пользователей в хранилище NTAuth в Active Directory
- Если с помощью Служб федерации Active Directory в режим проверки подлинности альтернативный сертификат, убедитесь, что серверы Служб федерации Active Directory и WAP SSL-сертификаты, содержащие имя узла службы федерации Active Directory, начинающимся с «certauth», например «certauth.fs.contoso.com», и что с этим узлом-трафика через брандмауэр
- При использовании проверки подлинности сертификата из экстрасети, убедитесь, что по крайней мере один AIA и по крайней мере один CDP или OCSP расположение из списка, указанные в сертификатах доступны из Интернета.
- При настройке службы федерации Active Directory для проверки подлинности сертификата Azure AD, убедитесь, что вы настроили [параметры Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-certificate-based-authentication-get-started#step-2-configure-the-certificate-authorities) и [правил, необходимых для утверждений AD FS](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-certificate-based-authentication-ios#requirements) для сертификата издателя и серийный номер
- Также для проверки подлинности сертификата Azure AD для клиентов Exchange ActiveSync сертификата клиента должна иметь адрес маршрутизации электронной почты пользователей в Exchange online в имя субъекта или имя RFC822 значение альтернативное имя субъекта. (Azure Active Directory сопоставляет RFC822 значение атрибута адрес прокси-сервера в каталоге.)

## <a name="configure-ad-fs-for-user-certificate-authentication"></a>Настройка AD FS для проверки подлинности сертификата пользователя  
- Включение проверки подлинности сертификата пользователя как интрасети или экстрасети подлинности в AD FS, с помощью консоли управления AD FS или командлета PowerShell Set-AdfsGlobalAuthenticationPolicy
- Установить всю цепочку доверия, включая все промежуточные сертификаты на каждом сервере WAP и AD FS. Промежуточные сертификаты должны быть установлены в хранилище центров промежуточного центра сертификации на локальном компьютере, на серверах WAP и AD FS.
- Если вы хотите использовать утверждения на основе сертификата полей и расширений помимо EKU (типа утверждения https://schemas.microsoft.com/2012/12/certificatecontext/extension/eku), настройте дополнительные утверждения пропуска правил в отношении доверия поставщика утверждений Active Directory.  Полный список доступных сертификатов утверждений см. ниже.  
- [Необязательно] Настройка разрешенных выдающего центра сертификации для создания сертификатов клиентов, используя рекомендации в разделе «Управление доверенными издателями для проверки подлинности клиента» в [в этой статье](https://technet.microsoft.com/en-us/library/dn786429(v=ws.11).aspx).

## <a name="configure-seamless-certificate-authentication-for-chrome-browser-on-windows-desktops"></a>Настройка комплексной проверки подлинности сертификата для браузера Chrome на компьютерах с ОС Windows
При наличии на компьютере, которые удовлетворяют в целях проверки подлинности клиента несколько сертификатов пользователя (таких как сертификаты Wi-Fi) браузера Chrome на рабочем столе Windows выводит запрос для выбора правильного сертификата. Это может запутать пользователя. Для оптимизации, можно задать политику для Chrome для автоматического выбора правильного сертификата для улучшения взаимодействия с пользователем. Эту политику можно установить вручную, изменив реестр или настроены автоматически с помощью групповой Политики (Чтобы задать разделы реестра). Для этого требуется пользователя клиентских сертификатов проверки подлинности от Служб федерации Active Directory для отдельных издателей из других вариантов использования. 

Дополнительные сведения о настройке это для Chrome можно найти на этом [ссылку](http://www.chromium.org/administrators/policy-list-3#AutoSelectCertificateForUrls).  


## <a name="troubleshooting"></a>Устранение неполадок
- Если ответ HTTP 204 «Содержимое не из https://certauth.fs.contoso.com» не запросы проверки подлинности сертификата, убедитесь, что корневой и промежуточные сертификаты ЦС установлены, соответственно, для доверенного корневого ЦС и промежуточных ЦС сертификатов на всех серверах федерации.
- Если запросы на проверку подлинности сертификата не выполняются по неизвестным причинам, Экспорт сертификата клиента в CER-файл и выполните команду 

`certutil -f -urlfetch -verify certificatefilename.cer`

Убедитесь в любой и разностных CRL расположения resolve.  Обратите внимание, что обнаружены расположения разностного списка отзыва Сертификатов на основе содержимого базового списка отзыва сертификатов.

## <a name="reference-complete-list-of-user-certificate-claim-types-and-example-values"></a>Справка: Полный список сертификат пользователя утверждений типы и примеры значений

|Тип утверждения|Пример значения
|-----|-----
|https://schemas.microsoft.com/2012/12/certificatecontext/field/x509version | 3
|https://schemas.microsoft.com/2012/12/certificatecontext/field/signaturealgorithm | sha256RSA
|https://schemas.microsoft.com/2012/12/certificatecontext/field/issuer | CN = entca, DC = domain, DC = contoso, DC = com
|https://schemas.microsoft.com/2012/12/certificatecontext/field/issuername | CN = entca, DC = domain, DC = contoso, DC = com
|https://schemas.microsoft.com/2012/12/certificatecontext/field/notbefore | 12/05/2016 20:50:18
|https://schemas.microsoft.com/2012/12/certificatecontext/field/notafter | 12/05/2017 20:50:18
|https://schemas.microsoft.com/2012/12/certificatecontext/field/subject | E =user@contoso.com, CN = пользователь, CN = Users, DC = domain, DC = contoso, DC = com
|https://schemas.microsoft.com/2012/12/certificatecontext/field/subjectname | E =user@contoso.com, CN = пользователь, CN = Users, DC = domain, DC = contoso, DC = com
|https://schemas.microsoft.com/2012/12/certificatecontext/field/rawdata | {Данные в кодировке Base64 цифровой сертификат}
|https://schemas.microsoft.com/2012/12/certificatecontext/extension/keyusage | Биты DigitalSignature
|https://schemas.microsoft.com/2012/12/certificatecontext/extension/keyusage | KeyEncipherment
|https://schemas.microsoft.com/2012/12/certificatecontext/extension/subjectkeyidentifier | 9D11941EC06FACCCCB1B116B56AA97F3987D620A
|https://schemas.microsoft.com/2012/12/certificatecontext/extension/authoritykeyidentifier | Идентификатор ключа = d6 13 e3 6b bc e5 d8 15 52 0a fd 36 6a d5 0b 51 f3 0b 25 7f
|https://schemas.microsoft.com/2012/12/certificatecontext/extension/certificatetemplatename | Пользователь
|https://schemas.microsoft.com/2012/12/certificatecontext/extension/san | Другие имя: основное имя =user@contoso.com, имя RFC822 =user@contoso.com
|https://schemas.microsoft.com/2012/12/certificatecontext/extension/eku | 1.3.6.1.4.1.311.10.3.4


