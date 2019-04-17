---
ms.assetid: 0fd7b6aa-3e50-45a3-a3a6-56982844363e
title: "Событие c Идентификатором 2088 - произошла ошибка поиска в DNS успешной репликации"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 4f223f075775f942f83a1962da28a77e85e89aa0
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="event-id-2088-dns-lookup-failure-occurred-with-replication-success"></a>Событие c Идентификатором 2088: Произошла ошибка поиска в DNS, успешной репликации

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

    
    <developerConceptualDocument xmlns="https://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="https://www.w3.org/1999/xlink" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="https://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
      <introduction>
    <para>When a destination domain controller running Windows Server 2003 with Service Pack 1 (SP1) receives Event ID 2088 in the Directory Service event log, attempts to resolve the globally unique identifier (GUID) in the alias (CNAME) resource record to an IP address for the source domain controller failed. However, the destination domain controller tried other means to resolve the name and succeeded by using either the fully qualified domain name (FQDN) or the NetBIOS name of the source domain controller. Although replication was successful, the Domain Name System (DNS) problem should be diagnosed and resolved. </para>
    <para>The following is an example of the event text: </para>
    <code>Log Name: Directory Service

    Source: Microsoft-Windows-ActiveDirectory_DomainService
    Date: 3/15/2008  9:20:11 AM
    Event ID: 2088
    Task Category: DS RPC Client 
    Level: Warning
    Keywords: Classic
    User: ANONYMOUS LOGON
    Computer: DC3.contoso.com
    Description:
    Active Directory could not use DNS to resolve the IP address of the 
    source domain controller listed below. To maintain the consistency 
    of Security groups, group policy, users and computers and their passwords, 
    Active Directory Domain Services successfully replicated using the NetBIOS 
    or fully qualified computer name of the source domain controller. 

Недопустимая конфигурация DNS могут затрагивать других основных операций на компьютерах-членах, контроллеры домена или серверы приложений в этом лесу доменных служб Active Directory, включая проверку подлинности или доступ к сетевым ресурсам. 

Эта конфигурация DNS — ошибка исчезнет немедленно, чтобы этот контроллер домена может разрешить IP-адрес исходного контроллера домена с помощью DNS. 

Имя альтернативного сервера: имя узла DNS сбой DC1: 4a8717eb 8e58-456 c-995a-c92e4add7e8e._msdcs. contoso.com 

Примечание: По умолчанию до 10 сбоев DNS-сервера отображаются для любой данной 12-часовой период даже при возникновении сбоев более чем 10.  Для регистрации всех событий в отдельных сбоя, установите следующие диагностики значение реестра значение 1: 

Путь в реестре: Клиент RPC доменных служб Active Directory HKLM\System\CurrentControlSet\Services\NTDS\Diagnostics\22 

Действие пользователя: 

1) Если исходный контроллер домена больше не повторной установки операционной системы работает, или его с именем другого компьютера или NTDSDSA объект GUID, удалить метаданные исходного контроллера домена с помощью ntdsutil.exe, как описано в статье MSKB 216498. 

2) Убедитесь, что исходный контроллер домена Active Directory работает и доступен в сети, введя «net view \\&lt;имя исходного контроллера домена&gt;» или «ping &lt;имя исходного контроллера домена&gt;». 

3) Убедитесь, что исходный контроллер домена использует допустимого DNS-сервера для службы DNS и что запись CNAME и записи узла исходного контроллера домена правильно зарегистрировано, с помощью версии DCDIAG.EXE на https://www.microsoft.com/dns 

DCDiag//test: DNS-сервера 

4) Убедитесь, что этот конечный контроллер домена использует допустимого DNS-сервера для службы DNS, выполнив версии DNS расширенный DCDIAG.EXE команд на консоли на конечный контроллер домена следующим образом: 

DCDiag//test: DNS-сервера 

5) Для дальнейшего анализа DNS сбоев ошибки в разделе КБ 824449: https://support.microsoft.com/?kbid=824449 

Дополнительные данные: значение ошибки: 11004 запрошенным именем действительна, но не данные запрошенного типа не найдены</code>
  </introduction>
  <section>
    <title>Диагностика</title>
    <content>
      <para>не удалось разрешить имя исходного контроллера домена с помощью записи ресурса псевдонима (CNAME) в DNS может быть из-за ошибки в конфигурации DNS-сервера или задержек при распространении данных DNS.</para>
    </content>
  </section>
  <section>
    <title>Разрешение</title>
    <content>
      <para>продолжить тестирование DNS, как описано в разделе «<link xlink:href="85b1d179-f53e-4f95-b0b8-5b1c096a8076">событие c Идентификатором 2087: сбой репликации из-за ошибки поиска в DNS</link>.»</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>


