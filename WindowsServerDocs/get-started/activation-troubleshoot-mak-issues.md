---
title: 'Активация с помощью MAK: известные проблемы'
description: Описываются распространенные проблемы, которые могут возникнуть во время активации с помощью MAK, а также приводятся рекомендации по их устранению.
ms.topic: article
ms.date: 10/3/2019
ms.technology: server-general
ms.assetid: ''
author: Teresa-Motiv
ms.author: v-tea
manager: dcscontentpm
ms.localizationpriority: medium
ms.openlocfilehash: 25fa6d32571597136580afe062aa8d9c7e2d82b7
ms.sourcegitcommit: 9855d6b59b1f8722f39ae74ad373ce1530da0ccf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71962990"
---
# <a name="mak-activation-known-issues"></a>Активация с помощью MAK: известные проблемы

В этой статье описаны распространенные проблемы, которые могут возникать при активации с помощью ключа многократной активации (MAK), и приведены рекомендации по их устранению.

## <a name="how-can-i-tell-whether-my-computer-is-activated"></a>Как узнать, активирован ли мой компьютер?

На компьютере откройте панель управления **Система** и найдите сообщение **Активация Windows выполнена**. Кроме того, можно запустить Slmgr.vbs и указать параметр командной строки **/dli**.

## <a name="the-computer-does-not-activate-over-the-internet"></a>Компьютер не активируется через Интернет

Убедитесь, что необходимые порты не заблокированы в брандмауэре. Список портов приведен в [руководстве по развертыванию активации корпоративных лицензий](http://go.microsoft.com/fwlink/?linkid=150083).

## <a name="internet-and-telephone-activation-fail"></a>Сбой активации через Интернет и по телефону

Обратитесь в местный центр активации лицензий Майкрософт. Номера телефонов центров активации лицензий Майкрософт по всему миру приведены в разделе [Телефонные номера центров активации лицензий Майкрософт](https://www.microsoft.com/Licensing/existing-customer/activation-centers). При обращении обязательно предоставьте данные соглашения о корпоративном лицензировании и подтверждение покупки.

## <a name="slmgrvbs-ato-returns-an-error-code"></a>Slmgr.vbs /ato возвращает код ошибки

Если Slmgr.vbs возвращает шестнадцатеричный код ошибки, получите соответствующее сообщение об ошибке, выполнив следующий сценарий.

```cmd
slui.exe 0x2a 0x <ErrorCode>
```

Дополнительные сведения о конкретных кодах ошибок и способах их устранения см. в разделе [Устранение ошибок активации](activation-error-codes.md).
