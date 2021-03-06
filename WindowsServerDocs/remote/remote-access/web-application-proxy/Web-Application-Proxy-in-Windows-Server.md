---
ms.assetid: 0b3587b2-219f-43d8-88b4-1254eaa8b910
title: Прокси-служба веб-приложения в Windows Server
ms.prod: windows-server
ms.technology: web-app-proxy
ms.topic: article
ms.author: kgremban
author: eross-msft
ms.openlocfilehash: 84c2c735ee3e6b19816acaa8810c297c487f5250
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86961456"
---
# <a name="web-application-proxy-in-windows-server"></a>Прокси-служба веб-приложения в Windows Server

>Область применения: Windows Server&reg; 2016

**Это содержимое относится к локальной версии прокси веб-приложения. Чтобы обеспечить безопасный доступ к локальным приложениям в облаке, ознакомьтесь с [содержимым AD application proxy Azure](/azure/active-directory/manage-apps/application-proxy).**  
  
В этом разделе описано, что нового и изменено в прокси веб-приложения для Windows Server 2016. Новые функции и изменения, перечисленные здесь, скорее всего, оказывают наибольшее влияние на работу с предварительной версией.  
  
## <a name="web-application-proxy-new-features"></a>Новые возможности прокси веб-приложения  
  
- Предварительная проверка подлинности при публикации приложений HTTP Basic  
  
  HTTP Basic — это протокол авторизации, используемый многими протоколами, включая ActiveSync, для подключения полнофункциональных клиентов, включая смартфоны, с почтовым ящиком Exchange. Прокси веб-приложения обычно взаимодействует с AD FS с использованием перенаправлений, которые не поддерживаются клиентами ActiveSync. Эта новая версия прокси веб-приложения обеспечивает поддержку публикации приложения с помощью HTTP Basic, позволяя приложению HTTP получить отношение доверия с проверяющей стороной, не относящейся к утверждениям, для приложения с служба федерации.  
  
  Дополнительные сведения о публикации HTTP Basic см. в статье [Публикация приложений с помощью AD FS Предварительная проверка подлинности](../web-application-proxy/../web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication.md) .  
  
- Доменная публикация приложений с подстановочными знаками  
  
  Для поддержки таких сценариев, как SharePoint 2013, внешний URL-адрес приложения теперь может содержать подстановочный знак, позволяющий публиковать несколько приложений в определенном домене, например https://*. SP-Apps. contoso. com. Это упростит публикацию приложений SharePoint.  
  
- Перенаправление трафика HTTP в HTTPS  
  
  Чтобы пользователи могли получить доступ к приложению, даже если в URL-адресе не введено значение HTTPS, прокси веб-приложения теперь поддерживает перенаправление HTTP в HTTPS.  
  
- Публикация HTTP  
  
  Теперь можно опубликовать приложения HTTP, используя сквозную предварительную проверку подлинности.  
  
- Публикация приложений шлюза удаленный рабочий стол  
  
  Дополнительные сведения о RDG в прокси веб-приложения см. в статье [Публикация приложений с помощью SharePoint, Exchange и RDG](../web-application-proxy/Publishing-Applications-with-SharePoint,-Exchange-and-RDG.md) .  
  
- Новый журнал отладки для улучшения устранения неполадок и Улучшенный журнал службы для полного аудита и улучшенной обработки ошибок  
  
  Дополнительные сведения об устранении неполадок см. в разделе [Устранение неполадок прокси веб-приложения](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn770156(v=ws.11)) .  
  
- Улучшения пользовательского интерфейса консоль администратора  
  
- Распространение IP-адреса клиента в серверные приложения  
  
## <a name="see-also"></a>См. также  
  
-   [Что нового в Windows Server 2016?](../../../get-started/whats-new-in-windows-server-2016.md)  
  
-   [Публикация приложений с использованием предварительной проверки подлинности AD FS](../web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication.md)  
  
-   [Диагностика прокси-службы веб-приложения](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn770156(v=ws.11))  
  
