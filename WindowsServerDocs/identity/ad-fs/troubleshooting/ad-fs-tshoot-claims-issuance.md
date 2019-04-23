---
title: AD FS Устранение неполадок — утверждений выдачи
description: В этом документе описывается устранение неполадок выдачи маркеров в AD FS
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/03/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: fdf8851fe9b35f82191458ba3313fda2dc3ee4cf
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59839665"
---
# <a name="ad-fs-troubleshooting---claims-issuance"></a>AD FS Устранение неполадок — утверждений выдачи
Утверждение является оператором, отдельный субъект делает в отношении себя или другого субъекта.  Заявки опубликованы проверяющей стороной, и их получает одно или несколько значений и затем упакованных в маркерах безопасности, выдаваемых сервера AD FS.  Так как в этом процессе есть несколько перемещаемых частей, выдачи утверждений можно разделить на следующие ключевые элементы.

>[!NOTE]  
>Можно использовать [ClaimsXRay](https://adfshelp.microsoft.com/ClaimsXray/TokenRequest) на [служб федерации Active Directory помогают](https://adfshelp.microsoft.com) сайта, чтобы помочь в диагностике утверждений проблемы.   

## <a name="token-request"></a>Запрос маркера
При переходе к проверяющей стороне вы будете перенаправлены к AD FS с помощью запроса маркера.  Проблемы могут возникнуть с запросом.  Прежде всего:

### <a name="the-request-formatting-with-3rd-parties-particularly-saml"></a>Запрос форматирования с помощью сторонних производителей (особенно SAML)

### <a name="pre-formated-urls-that-have-typos"></a>Pre оповещением URL-адреса, опечатки
При выдаче токена из проверяющих сторон WS-Federaion этого запроса маркера сталкивается с параметрами строки запроса URL-адрес.  Если не указать правильные параметры в этот URL-адрес проверяющей, не перенаправления AD FS, то это может привести к проблеме с запросом.


Чтобы verifiy формат маркера можно использовать отладчик веб-инструмент


## <a name="token-response"></a>Ответ на токен

## <a name="authentication"></a>Проверка подлинности

## <a name="claim-rule-processing"></a>Обработка правил утверждений