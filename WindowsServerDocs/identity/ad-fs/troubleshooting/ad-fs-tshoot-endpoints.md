---
title: AD FS Устранение неполадок — конечных точек AD FS
description: В этом документе описывается устранение неполадок конечных точек AD FS
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/03/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 13b830c0317341280bd87499e3abd8dcd1a33fc2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59857565"
---
# <a name="ad-fs-troubleshooting---ad-fs-metadata-endpoints"></a>AD FS Устранение неполадок — конечные точки метаданных службы федерации Active Directory
Конечные точки обеспечивают доступ к функциям сервера федерации AD FS, таких как публикация метаданных федерации.  Чтобы убедиться, что сервер AD FS отвечает на веб-запросов, можно проверить информацию о конечных точках.


## <a name="federation-metadata-test"></a>Проверка метаданных федерации
Пассивной федерации относится к сценариям, где браузере перенаправлены на странице входа AD FS.  Тестирование конечной точки метаданных можно определить, отвечает ли сервер AD FS на веб-запросы в этих пассивных сценариях.  Используйте следующую процедуру для проверки конечной точки.

1.  С помощью веб-браузер, перейдите к конечной точке метаданных федерации AD FS.  Например:  https://sts.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
2. XML-файл необходимо загрузить локально на компьютер.
3. Откройте его и убедитесь, что он содержит сведения, подобные сведения ниже: ![Пассивный](media/ad-fs-tshoot-endpoints/meta2.png)

## <a name="ws-mex-test-active-test"></a>Проверка WS-MEX (Active test)
— Веб-службы протокол WS-MetaDataExchange и является частью стратегии WS-Federation.  Он использует сообщения SOAP для запроса метаданных.  Тестирование конечной точки можно определить, отвечает ли к запросам веб-сервера AD FS для WS-MetaDataExchange.  Используйте следующую процедуру для проверки конечной точки.
1.  С помощью веб-браузер, перейдите к конечной точке метаданных федерации AD FS.  Например:  https://sts.contoso.com/adfs/services/trust/mex
2. XML-файле должно автоматически отображаться в браузере.  Он должен выглядеть как на следующем рисунке:

![Активный](media/ad-fs-tshoot-endpoints/meta3.png)


## <a name="next-steps"></a>Следующие шаги

- [Устранение неполадок AD FS](ad-fs-tshoot-overview.md)