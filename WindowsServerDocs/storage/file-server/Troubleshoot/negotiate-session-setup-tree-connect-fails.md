---
title: Согласование, Настройка сеанса и сбои при подключении к дереву
description: В этой статье содержатся сведения об устранении неполадок при сбоях подключения, установки сеанса и дерева.
author: Deland-Han
manager: dcscontentpm
audience: ITPro
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: 0ccd8d882060432dcfc27ee47b82d0c61e3aad4d
ms.sourcegitcommit: 8cf04db0bc44fd98f4321dca334e38c6573fae6c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654375"
---
# <a name="negotiate-session-setup-and-tree-connect-failures"></a>Согласование, Настройка сеанса и сбои при подключении к дереву

В этой статье описывается, как устранить неполадки, возникающие при выполнении запроса на подключение к SMB, установка сеанса и соединение дерева.

## <a name="negotiate-fails"></a>Сбой согласования

SMB Server получает запрос на СОГЛАСОВАНие SMB от клиента SMB. Время ожидания соединения истекло и сбрасывается через 60 секунд. После около 200 микросекунд может появиться сообщение с ПОДТВЕРЖДЕНИЕм.

Чаще всего эта проблема возникает из-за антивирусной программы.

Если вы используете Windows Server 2008 R2, существуют исправления этой проблемы. Убедитесь, что клиент SMB и сервер SMB обновлены.

## <a name="session-setup-fails"></a>Сбой установки сеанса

SMB-сервер получает сеанс SMB\_запрос установки от клиента SMB, но не смог ответить.

Если полное доменное имя (FQDN) или сетевое имя системы ввода-вывода (NetBIOS) сервера используется в UNC-пути, Windows будет использовать Kerberos для проверки подлинности.

После получения ответа на согласование будет предпринята попытка получить билет Kerberos для имени участника-службы (SPN) Common Internet File System (CIFS) сервера. Просмотрите трафик Kerberos через TCP-порт 88, чтобы убедиться в отсутствии ошибок Kerberos при получении клиентом SMB маркера.

> [!NOTE]
> Ошибки, возникающие при предварительной проверке подлинности Kerberos, являются нормальными. Ошибки, возникающие после предварительной проверки подлинности Kerberos (экземпляры, в которых проверка подлинности не работают), являются ошибками, вызвавшими проблему с SMB.

Кроме того, выполните следующие проверки:

- Просмотрите большой двоичный объект безопасности в запросе SMB\_SETUP, чтобы обеспечить отправку правильных учетных данных.

- Попробуйте отключить усиление защиты имени SMB-сервера (**смбсервернамехарденинглевел = 0**).

- Убедитесь, что сервер SMB имеет имя участника-службы при доступе к нему через запись DNS CNAME.

- Убедитесь, что подписывание SMB работает. (Это особенно важно для старых устройств сторонних производителей.)

## <a name="tree-connect-fails"></a>Сбой подключения к дереву

Убедитесь, что учетные данные учетной записи пользователя имеют разрешения "общий доступ" и "NT File System" (NTFS) для папки.

Причину распространенных ошибок подключения к дереву можно найти в [3.3.5.7 получении дерева SMB2\_запроса на подключение](https://docs.microsoft.com/openspecs/windows_protocols/ms-smb2/652e0c14-5014-4470-999d-b174d7b2da87). Ниже приведены решения для двух распространенных кодов состояния.

СОСТОЯНИЕ \[\_\_сети\_неправильное имя\]

Убедитесь, что общая папка существует на сервере и правильно написана в запросе SMB-клиента.

\[состояние\_доступ\_запрещен\]

Убедитесь, что диск и папка, используемые общей папкой, существуют и доступны.

Если вы используете SMBv3 или более поздней версии, проверьте, требуется ли шифрование сервера и общего ресурса, но клиент не поддерживает шифрование. Для этого вам нужно выполнить следующие действия.

- Проверьте сервер, выполнив следующую команду.

  ```PowerShell
  Get-SmbServerConfiguration | select Encrypt*
  ```

  Если EncryptData и Режектуненкриптедакцесс имеют значение true, сервер требует шифрования.

- Проверьте общий ресурс, выполнив следующую команду:

  ```PowerShell
  Get-SmbShare | select name, EncryptData  
  ```

  Если EncryptData имеет значение true для общей папки, а Режектуненкриптедакцесс имеет значение true на сервере, то для общей папки требуется шифрование.

При устранении неполадок следуйте приведенным ниже рекомендациям.

- Windows 8, Windows Server 2012 и более поздних версий Windows поддерживают шифрование на стороне клиента (SMBv3 и более поздние версии).

- Windows 7, Windows Server 2008 R2 и более ранние версии Windows не поддерживают шифрование на стороне клиента.

- Samba и сторонние устройства могут не поддерживать шифрование. Для получения дополнительных сведений может потребоваться обратиться к документации по продукту.

## <a name="references"></a>Ссылок

Дополнительные сведения см. в следующих руководствах.

[3.3.5.4 получение запроса на СОГЛАСОВАНие SMB2](https://docs.microsoft.com/openspecs/windows_protocols/ms-smb2/b39f253e-4963-40df-8dff-2f9040ebbeb1)

[3.3.5.5 Получение сеанса SMB2\_установки](https://docs.microsoft.com/openspecs/windows_protocols/ms-smb2/e545352b-9f2b-4c5e-9350-db46e4f6755e)

[3.3.5.7 получение дерева SMB2\_запроса на подключение](https://docs.microsoft.com/openspecs/windows_protocols/ms-smb2/652e0c14-5014-4470-999d-b174d7b2da87?redirectedfrom=MSDN)