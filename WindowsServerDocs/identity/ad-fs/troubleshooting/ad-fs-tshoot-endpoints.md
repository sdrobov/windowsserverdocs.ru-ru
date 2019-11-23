---
title: Устранение неполадок AD FS AD FS конечных точек
description: В этом документе описывается устранение неполадок конечных точек AD FS
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/03/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 807b5c5de14bf6a43419d0b9d2d3a4e6953d0075
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71366220"
---
# <a name="ad-fs-troubleshooting---ad-fs-metadata-endpoints"></a>Устранение неполадок AD FS AD FS конечных точек метаданных
Конечные точки предоставляют доступ к функциональным возможностям сервера федерации AD FS, например публикации метаданных федерации.  Чтобы убедиться, что сервер AD FS отвечает на веб-запросы, можно проверить различные конечные точки.


## <a name="federation-metadata-test"></a>Проверка метаданных федерации
Пассивная федерация относится к сценариям, в которых браузер перенаправляется на страницу входа AD FS.  Проверив конечную точку метаданных, можно определить, отвечает ли сервер AD FS на веб-запросы в этих пассивных сценариях.  Для проверки конечной точки используйте следующую процедуру.

1.  С помощью веб-браузера перейдите к конечной точке метаданных федерации AD FS.  Например: https://sts.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
2. XML-файл должен загружаться локально на компьютер.
3. Откройте его и убедитесь, что он содержит сведения, аналогичные приведенным ниже описано: ![passive](media/ad-fs-tshoot-endpoints/meta2.png)

## <a name="ws-mex-test-active-test"></a>Проверка WS-MEX (активный тест)
WS-MetaDataExchange является протоколом веб-служб и является частью плана WS-Federation.  Он использует сообщение SOAP для запроса метаданных.  Проверив конечную точку, можно определить, отвечает ли сервер AD FS на веб-запросы WS-MetaDataExchange.  Для проверки конечной точки используйте следующую процедуру.
1.  С помощью веб-браузера перейдите к конечной точке метаданных федерации AD FS.  Например: https://sts.contoso.com/adfs/services/trust/mex
2. XML-файл должен отображаться в браузере автоматически.  Оно должно выглядеть, как показано ниже:

![Активный](media/ad-fs-tshoot-endpoints/meta3.png)


## <a name="next-steps"></a>Дальнейшие действия

- [Устранение неполадок в AD FS](ad-fs-tshoot-overview.md)