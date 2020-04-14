---
title: Управление — TPM BDE
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 11a8530d-edd7-4fe3-ae81-b943766760fe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b6495bfbfedea7219ae175145f72fc12314ce7ae
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839767"
---
# <a name="manage-bde-tpm"></a>Manage-bde: TPM

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012
> 
> [!IMPORTANT]
> Эта команда не поддерживается для использования на компьютерах под управлением Windows 8, Windows Server 2012 или более поздних операционных систем. Для этих компьютеров можно использовать [командлеты управления TPM для Windows PowerShell](https://docs.microsoft.com/powershell/module/trustedplatformmodule/).
> Если эта команда используется на компьютере под Windows 7 или Windows Server 2008, можно по-прежнему настроить доверенный платформенный модуль (TPM) компьютера (TPM) с помощью этой команды. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).
> ## <a name="syntax"></a>Синтаксис
> ```
> manage-bde -tpm [-turnon] [-takeownership <OwnerPassword>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
> ```
> #### <a name="parameters"></a>Параметры
> 
> |    Параметр    |                                                                              Описание                                                                               |
> |-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
> |     -Турнон     |              Включает и активирует доверенный платформенный модуль, позволяя задать пароль владельца доверенного платформенного модуля. Можно также использовать **-t** в качестве сокращенной версии этой команды.              |
> | -такеовнершип  |                      Получает владение доверенным платформенным модулем, задавая пароль владельца. Можно также использовать параметр **-o** в качестве сокращенной версии этой команды.                       |
> | <OwnerPassword> |                                                      Представляет пароль владельца, указанный для доверенного платформенного модуля.                                                       |
> |  -ComputerName  | Указывает, что Manage-bde. exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды. |
> |     <Name>      |    Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.     |
> |    -? или/?     |                                                               Отображает краткую справку в командной строке.                                                               |
> |   -Help или-h   |                                                             Отображает полную справку в командной строке.                                                              |
> 
> ## <a name="examples"></a><a name=BKMK_Examples></a>Примеров
> В следующем примере показано использование команды **-TPM** для включения доверенного платформенного модуля.
> ```
> manage-bde  tpm -turnon
> ```
> В следующем примере показано использование команды **TPM** для смены владельца TPM и присвоения пароля владельца 0wnerP@ss.
> ```
> manage-bde  tpm  takeownership 0wnerP@ss
> ```
> ## <a name="additional-references"></a>Дополнительные материалы
> -   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
> -   [manage-bde](manage-bde.md)
