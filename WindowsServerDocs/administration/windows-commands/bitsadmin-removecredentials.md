---
title: bitsadmin removecredentials
description: Раздел команд Windows для битсадмин **ремовекредентиалс**, который удаляет учетные данные из задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4a78ce9a-1feb-4811-a000-cce81287b22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 55ff7e2a813c7cc6b60e04d55ef63804a2aed796
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849847"
---
# <a name="bitsadmin-removecredentials"></a>bitsadmin removecredentials

Удаляет учетные данные из задания.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 1,2 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /removecredentials <job> <target> <scheme>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| target | Используйте либо **сервер** , либо **прокси**. |
| схема | Используйте один из следующих элементов:<ul><li>**основы.** Схема проверки подлинности, в которой имя пользователя и пароль отправляются открытым текстом на сервер или прокси.</li><li>**Дайджест-.** Схема проверки подлинности типа "запрос — ответ", которая использует определяемую сервером строку данных для запроса.</li><li>**NTLM.** Схема проверки подлинности "запрос — ответ", которая использует учетные данные пользователя для проверки подлинности в сетевой среде Windows.</li><li>**Negotiate (также называется простым и защищенным протоколом согласования).** Схема проверки подлинности "запрос — ответ", которая согласовывается с сервером или прокси, чтобы определить, какую схему использовать для проверки подлинности. Примерами являются протокол Kerberos и NTLM.</li><li>**Passport.** Централизованная служба проверки подлинности, предоставляемая корпорацией Майкрософт, предоставляющая единый вход для узлов участников.</li></ul> |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере удаляются учетные данные из задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /removecredentials myDownloadJob server basic
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)