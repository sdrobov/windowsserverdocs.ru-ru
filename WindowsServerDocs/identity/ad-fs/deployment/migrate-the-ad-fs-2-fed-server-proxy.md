---
title: Перенос прокси-сервера AD FS 2.0 федерации
description: Сведения о миграции прокси-сервера федерации AD FS в Windows Server 2012.
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: eddb0d3432c69ecff4542ff1b8f2204b96ce0820
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66445660"
---
# <a name="migrate-the-ad-fs-20-federation-server-proxy"></a>Перенос прокси-сервера AD FS 2.0 федерации
Этот документ содержит подробные сведения о миграции с AD FS 2.0 federation прокси-сервером в Windows Server 2012.

## <a name="migrate-the-proxy"></a>Перенос прокси-сервера

Чтобы перенести прокси AD FS 2.0 federation server в Windows Server 2012, выполните следующую процедуру.  
  
1.  Для каждого прокси-сервера федерации, которую планируется перенести в Windows Server 2012, просмотрите и выполните процедуры, описанные в [Подготовка к миграции AD FS 2.0 Federation Server Proxy](prepare-to-migrate-ad-fs-fed-proxy.md).  
  
2.  Удалите прокси-сервер федерации из подсистемы балансировки нагрузки.  
  
3.  Выполните обновление на месте операционной системы на этом сервере с Windows Server 2008 R2 или Windows Server 2008 до Windows Server 2012. Дополнительные сведения см. в разделе [Установка Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx).  
  
> [!IMPORTANT]
>  В результате обновления ОС конфигурация прокси AD FS на этом сервере утрачивается, а роль сервера AD FS 2.0 — удаляется. Вместо этого установить роль сервера Windows Server 2012 AD FS, но она не настроена. Вы должны вручную создать исходную конфигурацию прокси AD FS и восстановить остальные параметры прокси AD FS, чтобы завершить миграцию прокси-сервера федерации.  
  
4. Создайте исходную конфигурацию прокси AD FS с помощью **мастера конфигурации прокси-сервера федерации AD FS**. Дополнительные сведения см. в разделе [Configure a Computer for the Federation Server Proxy Role](configure-a-computer-for-the-federation-server-proxy-role.md). При выполнении мастера используйте сведения, собранные в разделе «Подготовка к миграции прокси-сервера федерации AD FS 2.0» следующим образом.  
  
 
|**Входной параметр мастера прокси-сервера федерации**|**Используйте следующее значение**|
|-----|-----|  
|**Имя службы федерации**|Введите значение BaseHostName из файла proxyproperties.txt|  
|Флажок **Использовать прокси-сервер HTTP при отправке запросов в эту службу федерации**|Установите этот флажок, если файл proxyproperties.txt содержит значение для свойства ForwardProxyUrl|  
|**Адрес прокси-сервера HTTP**|Введите значение ForwardProxyUrl из файла proxyproperties.txt|  
|Запрос учетных данных|Введите учетные данные учетной записи администратора сервера федерации AD FS или учетной записи службы, от имени которой выполняется служба федерации AD FS.|  
  
5. Обновите веб-страницы AD FS на этом сервере. Если вы резервное копирование настроенных веб-страниц AD FS прокси-сервера при подготовке к миграции прокси сервера федерации, воспользуйтесь резервными данными для перезаписи веб-страниц AD FS, которые были созданы по умолчанию в по умолчанию **%systemdrive%\inetpub\adfs\ls** каталог, в результате конфигурации прокси-сервера AD FS в Windows Server 2012.  
  
6. Добавьте этот сервер в подсистему балансировки нагрузки.  
  
7. Если нужно выполнить миграцию и других прокси-серверов федерации AD FS 2.0, повторите шаги 2 – 6 для остальных компьютеров прокси-сервера федерации.  
  
  
## <a name="next-steps"></a>Следующие шаги
 [Подготовка к миграции сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к миграции прокси-сервера AD FS 2.0 Federation](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенос сервера AD FS 2.0 Federation](migrate-the-ad-fs-fed-server.md)   
 [Перенос прокси-сервера AD FS 2.0 Federation](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)