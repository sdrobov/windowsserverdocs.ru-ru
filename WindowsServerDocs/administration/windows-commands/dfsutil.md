---
title: Dfsutil
description: Справочная статья по команде Dfsutil, которая управляет пространствами имен, серверами и клиентами DFS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ef5093a4-0d24-4b21-9d04-59933ad98e2c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cfb3d221e275a688f5c18a960681257077fb4f7f
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86958376"
---
# <a name="dfsutil"></a>Dfsutil

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Команда Dfsutil управляет пространствами имен, серверами и клиентами DFS.

## <a name="functionality-available-in-powershell"></a>Функциональные возможности, доступные в PowerShell

Модуль PowerShell [дфсн](/powershell/module/dfsn/?view=win10-ps) предоставляет эквивалентные функции для следующих параметров Dfsutil.

| Параметр | Описание |
| --------- | ----------- |
| root | Отображает, создает, удаляет, импортирует и экспортирует корни пространства имен. |
| link | Отображает, создает, удаляет или перемещает папки (ссылки). |
| target | Отображает, создает, удаляет целевой объект папки или сервер пространства имен. |
| свойство; | Отображает или изменяет целевой объект папки или сервер пространства имен. |
| server | Отображает или изменяет конфигурацию пространства имен. |
| домен | Отображает все пространства имен на основе домена в домене. |

## <a name="functionality-available-only-in-dfsutil"></a>Функциональные возможности, доступные только в Dfsutil

Следующие функциональные возможности доступны только в качестве параметров Dfsutil:

| Параметр | Описание |
| --------- | ----------- |
| клиент | Отображает или изменяет сведения о клиенте или разделы реестра. |
| диагностик | Выполните диагностику или просмотрите дфсдирс/дфспас. |
| cache | Отображает или очищает кэш клиента. |

Чтобы получить дополнительные сведения о каждой из этих команд, откройте командную строку на сервере с установленными средствами управления пространствами имен DFS и введите `dfsutil client /?` , `dfsutil diag /?` или `dfsutil cache /?` .

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
