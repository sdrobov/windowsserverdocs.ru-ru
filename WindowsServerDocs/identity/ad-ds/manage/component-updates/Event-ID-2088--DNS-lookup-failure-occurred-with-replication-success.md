---
ms.assetid: 0fd7b6aa-3e50-45a3-a3a6-56982844363e
title: Событие с Идентификатором 2088 - репликация успех произошла ошибка поиска DNS
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: e0c5e838290a8ebf33f0f7891dc10f8b00e5bcba
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66442649"
---
# <a name="event-id-2088-dns-lookup-failure-occurred-with-replication-success"></a>Событие с Идентификатором 2088 Произошла ошибка поиска в DNS с успехом репликации

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

    
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

Недопустимая конфигурация DNS могут влиять на других важных операций на рядовых компьютерах, контроллерах домена или серверов приложений в этом лесу доменных служб Active Directory, включая проверку подлинности или доступ к сетевым ресурсам. 

Немедленно, следует устранить эту ошибку конфигурации DNS, контроллер домена мог разрешать IP-адрес исходного контроллера домена с помощью DNS. 

Имя альтернативного сервера: Имя узла DC1 сбоя DNS: 4a8717eb-8e58-456c-995a-c92e4add7e8e._msdcs.contoso.com 

ПРИМЕЧАНИЕ. По умолчанию до 10 ошибок DNS отображаются для любой заданной 12-часовой период, даже если более чем 10 сбоев.  Чтобы записывать все события отдельных сбоя, установите следующие диагностики реестра значение 1: 

Путь реестра: HKLM\System\CurrentControlSet\Services\NTDS\Diagnostics\22 DS RPC Client 

Действие пользователя: 

1) Если исходный контроллер домена не работает или операционной системы после переустановки с именем другого компьютера или NTDSDSA объект GUID, удалить метаданные исходного контроллера домена с помощью ntdsutil.exe, используя шаги, описанные в статье MSKB 216498. 

2) Убедитесь, что исходный контроллер домена работает Active Directory и доступен в сети, введя «net view \\ &lt;имя исходного контроллера домена&gt;"или «ping &lt;имя исходного контроллера домена&gt;«. 

3) Убедитесь, что исходный контроллер домена использует допустимый DNS-сервер для службы DNS, и что запись CNAME и записи узла исходного контроллера домена, правильно зарегистрирован, с помощью DNS улучшенной версии DCDIAG. EXE, доступная в <https://www.microsoft.com/dns> 

dcdiag /test:dns 

4) Убедитесь, что этот конечный контроллер домена использует допустимый DNS-сервер для службы DNS, запустив версию DCDIAG расширенного DNS. Команда exe-файла на консоли конечного контроллера домена, следующим образом: 

dcdiag /test:dns 

5) Для дальнейшего анализа сбоев ошибка DNS см. в статье базы Знаний 824449: <https://support.microsoft.com/?kbid=824449> 

Дополнительные данные: Значение ошибки: 11004 запрошенное имя допустимо, но данные запрошенного типа не найдены</code> </introduction>
  <section>
    <title>Диагностика</title>
    <content>
      <para>Не удалось разрешить имя исходного контроллера домена с помощью записи ресурса псевдонима (CNAME) в DNS может быть из-за неверных настроек DNS или задержки при распространении данных DNS.</para>
    </content>
  </section>
  <section>
    <title>Разрешение</title>
    <content>
      <para>Перейти к тестированию DNS, как описано в разделе &quot; <link xlink:href="85b1d179-f53e-4f95-b0b8-5b1c096a8076">2087 идентификатор события: Ошибка поиска в DNS причиной ошибки репликации</link>.&quot;</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>


