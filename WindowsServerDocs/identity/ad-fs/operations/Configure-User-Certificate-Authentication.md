---
ms.assetid: 1ea2e1be-874f-4df3-bc9a-eb215002da91
title: Настройка поддержки AD FS для проверки подлинности сертификата пользователя
description: ''
author: jenfieldmsft
ms.author: billmath
manager: samueld
ms.date: 01/18/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: c69192a4223379b896a57eb04a38e37863c1366e
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66444315"
---
# <a name="configuring-ad-fs-for-user-certificate-authentication"></a>Настройка служб AD FS для проверки подлинности сертификата пользователя


AD FS можно настроить для x509 описано в разделе с помощью одного из режимов проверки подлинности сертификата пользователя [в этой статье](ad-fs-support-for-alternate-hostname-binding-for-certificate-authentication.md). Эта возможность может использоваться [с Azure Active Directory](https://blogs.msdn.microsoft.com/samueld/2016/07/19/adfs-certauth-aad-o365/) или сам по себе, чтобы предоставить клиентам и устройствам подготовлены с помощью сертификатов пользователей для доступа к AD FS ресурсы из интрасети или экстрасети.

## <a name="prerequisites"></a>предварительные требования
- Убедитесь, что ваш пользователь доверяет все AD FS и WAP-серверы
- Убедитесь, что корневой сертификат цепочки доверия для сертификатов пользователей в хранилище NTAuth в Active Directory
- Если в режиме альтернативного сертификата проверки подлинности с помощью AD FS, убедитесь, что серверы AD FS и WAP SSL-сертификаты, которые содержат префикс «certauth», например «certauth.fs.contoso.com», имя узла службы федерации Active Directory, и этого трафика с этим узлом в брандмауэре
- При использовании проверки подлинности сертификата из экстрасети, убедитесь, что по крайней мере один AIA и по крайней мере один CDP или OCSP расположение из списка, указанного в хранилище сертификатов, доступны из Интернета.
- При настройке AD FS для проверки подлинности сертификата в Azure AD, убедитесь, что вы настроили [параметры Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started#step-2-configure-the-certificate-authorities) и [правил, необходимых утверждений AD FS](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-ios#requirements) для сертификата поставщика и серийный номер
- Также для проверки подлинности сертификата Azure AD, для клиентов Exchange ActiveSync, сертификат клиента должен быть адрес маршрутизации электронной почты пользователей в Exchange online в имя субъекта или имени RFC822 значение поля альтернативное имя субъекта. (Azure Active Directory сопоставляет значение RFC822 с атрибутом адрес прокси-сервера в каталоге).

## <a name="configure-ad-fs-for-user-certificate-authentication"></a>Настройка AD FS для проверки подлинности пользователя на основе сертификата  
- Включить проверку подлинности сертификата пользователя как интрасети или экстрасети аутентификацию в AD FS, с помощью консоли управления AD FS или командлета PowerShell Set-AdfsGlobalAuthenticationPolicy
- Убедитесь, что вся цепочка доверия, включая любые промежуточные сертификаты, установлен на каждом сервере AD FS и WAP. Промежуточные сертификаты должен быть установлен в хранилище центров промежуточного центра сертификации на локальном компьютере, на всех AD FS и WAP-серверах.
- Если вы хотите использовать утверждения на основе полей сертификата и расширений в дополнение к EKU (тип утверждения https://schemas.microsoft.com/2012/12/certificatecontext/extension/eku), настроить дополнительные утверждения проход правила доверия с поставщиком утверждений Active Directory.  Полный список доступных сертификатов утверждений см. ниже.  
- [Необязательно] Настройка разрешенных выдающий центров сертификации для сертификатов клиентов, в соответствии с указаниями в разделе «Управление доверенными издателями для проверки подлинности клиента» в [в этой статье](https://technet.microsoft.com/library/dn786429(v=ws.11).aspx).

## <a name="configure-seamless-certificate-authentication-for-chrome-browser-on-windows-desktops"></a>Настройка простой проверки подлинности сертификата для браузера Chrome на настольных системах Windows
При наличии нескольких сертификатов пользователей (таких как сертификаты Wi-Fi) на компьютере, который удовлетворяет в целях проверки подлинности клиента браузера Chrome на рабочем столе Windows предложит пользователю выбрать правильный сертификат. Это может быть с толку для конечного пользователя. Чтобы оптимизировать этот процесс, можно задать политику для Chrome на автоматический выбор правильного сертификата для удобства работы пользователя. Эту политику можно установить вручную, изменив реестр или настраивается автоматически, через объект групповой Политики (Чтобы задать разделы реестра). Для этого пользователя сертификатов клиента для проверки подлинности AD FS для различных издателей из других вариантов использования. 

Дополнительные сведения о настройке это для Chrome см. в [ссылку](http://www.chromium.org/administrators/policy-list-3#AutoSelectCertificateForUrls).  


## <a name="troubleshooting"></a>Устранение неполадок
- Если запросы на проверку подлинности сертификата завершится ошибкой и HTTP 204 «содержимое из https:\//certauth.fs.contoso.com» ответ, корневой и все промежуточные сертификаты ЦС установлены, соответственно, доверенным корневым ЦС и Промежуточный сертификат ЦС хранит на всех серверах федерации.
- Если по неизвестным причинам не выполняются запросы на проверку подлинности сертификата, Экспорт сертификата клиента в CER-файл и выполните команду 

`certutil -f -urlfetch -verify certificatefilename.cer`

Убедитесь, любой список отзыва Сертификатов и разностные CRL расположений resolve.  Обратите внимание на то, что обнаруживаются на основе содержимого базовый CRL расположений разностных CRL.

## <a name="reference-complete-list-of-user-certificate-claim-types-and-example-values"></a>Справочные материалы. Полный список сертификат пользователя дополнительные типы утверждений и примеры значений

|                                         Тип утверждения                                         |                              Пример значения                               |
|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------|
|         https://schemas.microsoft.com/2012/12/certificatecontext/field/x509version         |                                    3                                     |
|     https://schemas.microsoft.com/2012/12/certificatecontext/field/signaturealgorithm      |                                sha256RSA                                 |
|           https://schemas.microsoft.com/2012/12/certificatecontext/field/issuer            |                 CN = entca, DC = domain, DC = contoso, DC = com                  |
|         https://schemas.microsoft.com/2012/12/certificatecontext/field/issuername          |                 CN = entca, DC = domain, DC = contoso, DC = com                  |
|          https://schemas.microsoft.com/2012/12/certificatecontext/field/notbefore          |                           12/05/2016 20:50:18                            |
|          https://schemas.microsoft.com/2012/12/certificatecontext/field/notafter           |                           12/05/2017 20:50:18                            |
|           https://schemas.microsoft.com/2012/12/certificatecontext/field/subject           |   E =user@contoso.com, CN = пользователь, CN = Users, DC = domain, DC = contoso, DC = com   |
|         https://schemas.microsoft.com/2012/12/certificatecontext/field/subjectname         |   E =user@contoso.com, CN = пользователь, CN = Users, DC = domain, DC = contoso, DC = com   |
|           https://schemas.microsoft.com/2012/12/certificatecontext/field/rawdata           |                {Данные в кодировке Base64 цифрового сертификата}                 |
|        https://schemas.microsoft.com/2012/12/certificatecontext/extension/keyusage         |                             DigitalSignature                             |
|        https://schemas.microsoft.com/2012/12/certificatecontext/extension/keyusage         |                             KeyEncipherment                              |
|  https://schemas.microsoft.com/2012/12/certificatecontext/extension/subjectkeyidentifier   |                 9D11941EC06FACCCCB1B116B56AA97F3987D620A                 |
| https://schemas.microsoft.com/2012/12/certificatecontext/extension/authoritykeyidentifier  |    KeyID=d6 13 e3 6b bc e5 d8 15 52 0a fd 36 6a d5 0b 51 f3 0b 25 7f     |
| https://schemas.microsoft.com/2012/12/certificatecontext/extension/certificatetemplatename |                                   Пользовательская                                   |
|           https://schemas.microsoft.com/2012/12/certificatecontext/extension/san           | Другие имя: основное имя =user@contoso.com, имени RFC822 =user@contoso.com |
|           https://schemas.microsoft.com/2012/12/certificatecontext/extension/eku           |                          1.3.6.1.4.1.311.10.3.4                          |

