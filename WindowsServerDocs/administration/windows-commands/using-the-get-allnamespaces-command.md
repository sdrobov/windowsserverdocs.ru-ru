---
title: С помощью команды get-AllNamespaces
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8fe896d-a69a-4180-923b-9f18185f5941
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8b77bb80238ee63cc0d71d88592d75850720e33b
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440521"
---
# <a name="using-the-get-allnamespaces-command"></a>С помощью команды get-AllNamespaces

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о всех пространств имен на сервере.
## <a name="syntax"></a>Синтаксис
Приложение.
```
wdsutil /Get-AllNamespaces [/Server:<Server name>] [/ContentProvider:<name>] [/Show:Clients] [/ExcludedeletePending]
```
Windows Server 2008 R2:
```
wdsutil /Get-AllNamespaces [/Server:<Server name>] [/ContentProvider:<name>] [/details:Clients] [/ExcludedeletePending]
```
## <a name="parameters"></a>Параметры

|         Параметр         |                                                                               Windows Server 2008                                                                               | Windows Server 2008 R2 |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------|
|  [/ Server:<Server name>]  | Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер. |                        |
| [/ Поставщик содержимого:<name>] |                                                        Отображение пространств имен для указанного поставщика содержимого только.                                                         |                        |
|      [/ Show: клиенты]      |                            Поддерживается только для Windows Server 2008. Отображает сведения о клиентских компьютерах, подключенных к пространству имен.                             |                        |
|    [/ сведения: клиенты]     |                           Поддерживается только для Windows Server 2008 R2. Отображает сведения о клиентских компьютерах, подключенных к пространству имен.                           |                        |
|  [/ExcludedeletePending]  |                                                              Исключает все деактивированные передачи данных из списка.                                                              |                        |

## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть все пространства имен, введите следующую команду:
```
wdsutil /Get-AllNamespaces
```
Чтобы просмотреть все пространства имен, кроме тех, которые становятся неактивными, введите следующую команду:
- Windows Server 2008
  ```
  wdsutil /Get-AllNamespaces /Server:MyWDSServer /ContentProvider:"MyContentProv" /Show:Clients /ExcludedeletePending
  ```
- Windows Server 2008 R2
  ```
  wdsutil /Get-AllNamespaces /Server:MyWDSServer /ContentProvider:"MyContentProv" /details:Clients /ExcludedeletePending
  ```
  #### <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса команд](command-line-syntax-key.md)
  [с помощью команды новое пространство имен](using-the-new-namespace-command.md)
  [с помощью команды remove-Namespace](using-the-remove-namespace-command.md) 
   [ Подкоманда: start-пространство имен](subcommand-start-namespace.md)
