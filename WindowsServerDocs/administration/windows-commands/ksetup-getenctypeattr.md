---
title: ksetup жетенктипеаттр
description: Справочный раздел по команде ksetup жетенктипеаттр, который получает атрибут типа шифрования для домена.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6c7ec002-355e-474d-bc27-27215049f1a8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2acead4ff1179002303c18d4feff262080203a28
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817704"
---
# <a name="ksetup-getenctypeattr"></a>ksetup жетенктипеаттр

Извлекает атрибут типа шифрования для домена. Сообщение о состоянии отображается при успешном или неудачном завершении.

Вы можете просмотреть тип шифрования для билета предоставления билета Kerberos (TGT) и ключ сеанса, выполнив команду **klist** и просмотрев выходные данные. Вы можете задать домен для подключения и использования, выполнив `ksetup /domain <domainname>` команду.

## <a name="syntax"></a>Синтаксис

```
ksetup /getenctypeattr <domainname>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<domainname>` | Имя домена, для которого требуется установить соединение. Используйте полное доменное имя или простую форму имени, например corp.contoso.com или contoso. |

### <a name="examples"></a>Примеры

Чтобы проверить атрибут типа шифрования для домена, введите:

```
ksetup /getenctypeattr mit.contoso.com
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда klist](klist.md)

- [Команда ksetup](ksetup.md)

- [Команда домена ksetup](ksetup-domain.md)

- [ksetup адденктипеаттр, команда](ksetup-addenctypeattr.md)

- [ksetup сетенктипеаттр, команда](ksetup-setenctypeattr.md)

- [ksetup деленктипеаттр, команда](ksetup-delenctypeattr.md)
