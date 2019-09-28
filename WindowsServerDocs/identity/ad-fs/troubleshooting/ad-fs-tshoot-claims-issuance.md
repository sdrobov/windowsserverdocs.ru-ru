---
title: Устранение неполадок AD FS — выдача утверждений
description: В этом документе описывается устранение проблем с выдачей маркеров с помощью AD FS
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/03/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: ea0e6112f00f9cace6a0c580661a5319b5adaea5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71366240"
---
# <a name="ad-fs-troubleshooting---claims-issuance"></a>Устранение неполадок AD FS — выдача утверждений
Утверждение — это оператор, который один субъект делает о себе или другой теме.  Утверждения выдаются проверяющей стороной и получают одно или несколько значений, а затем упаковываются в маркеры безопасности, выданные сервером AD FS.  Так как в этом процессе имеется несколько движущихся частей, выдача заявок может быть разбита на эти ключевые части.

>[!NOTE]  
>[Клаимсксрай](https://adfshelp.microsoft.com/ClaimsXray/TokenRequest) можно использовать на [справочном сайте ADFS](https://adfshelp.microsoft.com) для помощи в устранении проблем с утверждениями.   

## <a name="token-request"></a>Запрос токена
При переходе к проверяющей стороне она перенаправит вас на AD FS с запросом маркера.  При запросе могут возникнуть проблемы.  Особенно важно:

### <a name="the-request-formatting-with-3rd-parties-particularly-saml"></a>Форматирование запросов с третьими сторонами (в частности SAML)

### <a name="pre-formated-urls-that-have-typos"></a>Предварительно отформатированные URL-адреса с опечатками
При выдаче маркера от проверяющих сторон WS-Федераион, когда запрос маркера поступает в параметры строки запроса URL-адреса.  Если проверяющая сторона не укажет правильные параметры в этом URL-адресе при перенаправлении AD FS то это может привести к возникновению проблемы с запросом.


Чтобы проверить формат маркера, можно использовать средство веб-отладчика.


## <a name="token-response"></a>Ответ токена

## <a name="authentication"></a>Проверка подлинности

## <a name="claim-rule-processing"></a>Обработка правил заявок