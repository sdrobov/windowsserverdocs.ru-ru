---
title: Управление — BDE форцерековери
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: eecae37c-c9a3-46c5-b615-a0ace1f1d778
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1213eb583099a575fd118b1ade5d2c9b82c6dea7
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820684"
---
# <a name="manage-bde-forcerecovery"></a>Manage-bde: форцерековери



Принудительное перезагрузку диска, защищенного с помощью BitLocker, в режим восстановления. Эта команда удаляет из диска все предохранители ключа, связанные с доверенный платформенный модуль (TPM) (TPM). При перезапуске компьютера для разблокировки диска можно использовать только пароль восстановления или ключ восстановления.

## <a name="syntax"></a>Синтаксис

```
manage-bde –forcerecovery <Drive> [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<> диска|Представляет букву диска, за которой следует двоеточие.|
|-ComputerName|Указывает, что Manage-bde. exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды.|
|\<Name>|Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или/?|Отображает краткую справку в командной строке.|
|-Help или-h|Отображает полную справку в командной строке.|

## <a name="examples"></a>Примеры

Чтобы проиллюстрировано использование команды **-форцерековери** для запуска BitLocker в режиме восстановления на диске C.
```
manage-bde –forcerecovery C:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Управление — BDE](manage-bde.md)