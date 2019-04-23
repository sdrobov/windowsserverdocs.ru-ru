---
ms.assetid: 399a8bbe-3375-4bb0-b55b-5f46e7050028
title: 'Ошибка репликации 1396: вход в систему не произведен. Конечная учетная запись указана неверно'
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: ef3da06dd348b804f538d37cafbfabdd8bf45beb
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59844505"
---
# <a name="replication-error-1396-logon-failure-the-target-account-name-is-incorrect"></a>Ошибка репликации 1396: вход в систему не произведен. Конечная учетная запись указана неверно

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012


<developerConceptualDocument xmlns="https://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="https://www.w3.org/1999/xlink" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="https://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd"> <introduction>
    <para>В этой статье описываются симптомы, причины и способы устранения проблем репликации Active Directory, ошибка Win32 1396: «Ошибка входа в систему: Имя учетной записи целевой неверный». </para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="d3a01966-74c9-4c49-ba11-354b9acf7519#BKMK_Symptoms">Проблема</link>
        </para>
      </listItem> <listItem>
        <para>
          <link xlink:href="d3a01966-74c9-4c49-ba11-354b9acf7519#BKMK_Causes">Причины</link>
        </para>
      </listItem> <listItem>
        <para>
          <link xlink:href="d3a01966-74c9-4c49-ba11-354b9acf7519#BKMK_Resolutions">Способы их устранения</link>
        </para>
      </listItem>
    </list>
  </introduction>
  <section address="BKMK_Symptoms">
    <title>Проблема</title>
    <content>
      <para />
      <list class="ordered">
<listItem><para>Отчеты DCDIAG, Active Directory репликациями теста завершилось ошибкой 1396: Ошибка входа: Имя учетной записи целевой неверный».</para><code>Testing server: &lt;Site name&gt;&lt;DC Name&gt;
Starting test: Replications
[Replications Check,&lt;DC Name&gt;] A recent replication attempt failed:
From &lt;source DC&gt; to &lt;destination DC&gt;
Naming Context: CN=&lt;DN path of naming context&gt;
<codeFeaturedElement>The replication generated an error (1396):
Logon Failure: The target account name is incorrect.</codeFeaturedElement>
The failure occurred at &lt;date&gt; &lt;time&gt;.
The last success occurred at &lt;date&gt; &lt;time&gt;.
XX failures have occurred since the last success</code></listItem><listItem><para>REPADMIN. EXE-файла сообщает, что состояние 1396 вызвала последней попытке репликации.</para><para>Часто упоминаются 1396 состояние включают, но не ограничиваются команды REPADMIN:</para><table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11"><tbody><tr><TD><list class="bullet"><listItem><para>REPADMIN/ADD /</para></listItem><listItem><para>REPADMIN/REPLSUM</para></listItem><listItem><para>REPADMIN /REHOST</para></listItem><listItem><para>REPADMIN /SHOWVECTOR /LATENCY</para></listItem></list></TD><TD><list class="bullet"><listItem><para>REPADMIN/SHOWREPS</para></listItem><listItem><para>REPADMIN /SHOWREPL</para></listItem><listItem><para>REPADMIN/SYNCALL</para></listItem></list></TD></tr></tbody></table><para>Пример выходных данных из «REPADMIN/SHOWREPS» показывает входящая репликация с CONTOSO-DC2 для CONTOSO-DC1, выдающие «Ошибка входа в систему: Имя учетной записи целевой неверный». Ниже приведен ошибка::</para><code>Default-First-Site-NameCONTOSO-DC1
DSA Options: IS_GC 
Site Options: (none)
DSA object GUID: b6dc8589-7e00-4a5d-b688-045aef63ec01
DSA invocationID: b6dc8589-7e00-4a5d-b688-045aef63ec01
==== INBOUND NEIGHBORS ======================================
DC=contoso,DC=com
Default-First-Site-NameCONTOSO-DC2 via RPC
DSA object GUID: 74fbe06c-932c-46b5-831b-af9e31f496b2
Last attempt @ &lt;date&gt; &lt;time&gt; failed, <codeFeaturedElement>result 1396 (0x574):
Logon Failure: The target account name is incorrect.</codeFeaturedElement>
&lt;#&gt; consecutive failure(s).
Last success @ &lt;date&gt; &lt;time&gt;.
</code></listItem><listItem><para><ui>Реплицировать сейчас</ui> Возвращает команды в Active Directory — сайты и службы «Ошибка входа в систему: Имя учетной записи целевой неверный».</para><para>Щелкнув объект соединения из исходного контроллера домена и выбрав <ui>Реплицировать сейчас</ui> завершается ошибкой «Ошибка входа в систему: Имя учетной записи целевой неверный». На экране ниже выводится сообщение об ошибке:</para><para>Текст заголовка диалогового окна:</para><para>Теперь репликация</para><para>Текст сообщения диалогового окна: </para><para>Произошла следующая ошибка при попытке синхронизации контекста именования &lt;путь к разделу DNS&gt; от контроллера домена &lt;исходного контроллера домена&gt; к контроллеру домена &lt;контроллердоменаназначения&gt;: Ошибка входа: Указано неверное имя целевой учетной записи. Эта операция не будет продолжена. </para></listItem><listItem><para>NTDS KCC "," Общие NTDS "или" Microsoft-Windows-ActiveDirectory_DomainService с состоянием 1396 событий в журнале службы каталогов в средстве просмотра событий.</para><para>События Active Directory, которые часто упоминаются состояние 1396 включают, но не ограничиваются:</para><table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11"><thead><tr><TD><para>Идентификатор события</para></TD><TD><para>Источник события</para></TD><TD><para>Строка событий</para></TD></tr></thead><tbody><tr><TD><para>1125</para></TD><TD><para>Microsoft-Windows-ActiveDirectory_DomainService</para></TD><TD><para>Домен службы мастер установки Active Directory (Dcpromo) не удалось установить соединение со следующим контроллером домена.</para></TD></tr><tr><TD><para>1645</para><para>Это событие содержит список SPN трех частей.</para></TD><TD><para>NTDS репликации</para></TD><TD><para>Active Directory не удалось выполнить проверенный удаленный вызов процедуры на другом контроллере домена, поскольку имя участника требуемой службы для конечного контроллера домена не зарегистрировано на контроллере домена, являющемся центром распространения ключей и разрешающим данное имя участника-службы.</para></TD></tr><tr><TD><para>1655</para></TD><TD><para>Microsoft-Windows-ActiveDirectory_DomainService</para></TD><TD><para>Доменные службы Active Directory попытки обмена данными с помощью следующих глобального каталога и попытки завершились с ошибкой.</para></TD></tr><tr><TD><para>2847</para></TD><TD><para>Microsoft-Windows-ActiveDirectory_DomainService</para></TD><TD><para>Проверки согласованности знаний обнаружена подключения репликации для службы каталогов только для чтения и предпринята попытка обновить удаленно в следующем экземпляре службы каталогов. Сбой операции. Он будет повторена.</para></TD></tr><tr><TD><para>1925</para></TD><TD><para>NTDS KCC</para></TD><TD><para>Не удалось установить связь репликации для следующего раздела каталога с возможностью записи.</para></TD></tr><tr><TD><para>1926</para></TD><TD><para>NTDS KCC</para></TD><TD><para>Попытка установить связь репликации на раздел каталога только для чтения со следующими параметрами, которые не удалось.</para></TD></tr><tr><TD><para>5781</para></TD><TD><para>NETLOGON</para></TD><TD><para> Сервер не может зарегистрировать его имени в DNS.</para></TD></tr></tbody></table></listItem><listItem><para>DCPROMO завершается ошибкой на экране</para><para>Текст заголовка диалогового окна:</para><para>Не удалось установить Active Directory</para><para>Текст сообщения диалогового окна:</para><para>Не удалось выполнить операцию, так как: Службы каталогов не удалось создать объект сервера для CN = NTDS Settings, CN = ServerBeingPromoted, CN = Servers, CN = сайт, CN = Sites, CN = Configuration, DC = contoso, DC = com на сервере ReplicationSourceDC.contoso.com. </para><para>Убедитесь, что сетевые учетные данные имеют достаточные права доступа для добавления реплики. </para><para>
«Ошибка входа в систему: Указано неверное имя целевой учетной записи. "</para><para>В этом случае событие с кодом 1645 1168 и 1125 регистрируются на сервере, который, уровень которой повышается.</para></listItem><listItem><para>Сопоставьте диск при помощи <embeddedLabel>net используйте</embeddedLabel>:</para><code>C:&gt;net use z: &lt;server_name&gt;c$
System error 1396 has occurred.
Logon Failure: The target account name is incorrect.</code><para>В этом случае сервер может также ведение журнала 333 идентификатор события в журнале событий системы и использовать большой объем виртуальной памяти в приложении SQL Server.</para></listItem><listItem><para>Неверное время контроллера домена.</para></listItem><listItem><para>Центр распространения КЛЮЧЕЙ не будет запущена на контроллере RODC после восстановления учетной записи krbtgt для RODC, которая была удалена. Например после восстановления, ошибка 1396 отображается. </para><para>
Идентификатор события 1645 регистрируется на контроллере RODC. </para><para>
Dcdiag также сообщает об ошибке, что он не может обновить учетную запись krbtgt контроллера RODC. </para></listItem>
</list>
    </content>
  </section>
  <section address="BKMK_Causes">
    <title>Причины</title>
    <content>
      <para />
      <list class="ordered">
        <listItem>
          <para>Имя участника-службы не существует в глобальном каталоге поиск от имени клиента, пытающиеся выполнить проверку подлинности с помощью Kerberos KDC.</para>
          <para>В контексте репликации Active Directory клиент Kerberos конечный контроллер домена, на поиск имени участника-службы KDC, скорее всего является назначения самого контроллера домена, но может быть удаленный контроллер домена.</para>
        </listItem>
        <listItem>
          <para>Пользователя или учетной записи службы, которые должны содержать имя субъекта-службы, искомых не существует в глобальном каталоге поиск KDC от имени назначения попытки репликации контроллера домена.</para>
          <para>В контексте репликации Active Directory исходной учетной записи компьютера контроллера домена не существует на поиск контроллера домена от имени выполнение входящей репликации конечный контроллер домена глобального каталога.</para>
        </listItem>
        <listItem>
          <para>Контроллер домена назначения отсутствует секрет LSA для исходного домена контроллеры домена.</para>
        </listItem>
        <listItem>
          <para>Имя участника-службы, искомых существует на учетную запись на другом компьютере от исходного контроллера домена.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section address="BKMK_Resolutions">
    <title>Способы их устранения</title>
    <content>
      <list class="ordered">
        <listItem>
          <para>Проверьте журнал событий службы каталогов на контроллер домена назначения для событий репликации NTDS 1645 и обратите внимание на следующее:</para>
          <para>Имя целевого контроллера домена</para>
          <para>Имя участника-службы искомых (E3514235-4B06-11D1-AB04-00C04FC2DCD2 /&lt;guid для объекта параметров NTDS контроллеры домена источника объекта&gt;/&lt;целевой домен&gt;.&lt; TLD&gt;@&lt;целевой домен&gt;.&lt; домена верхнего уровня&gt;</para>
          <para>KDC, используется контроллер домена назначения</para>
        </listItem>
        <listItem>
          <para>В консоли центра распространения КЛЮЧЕЙ, определенных на шаге 1 введите следующее: </para>
          <code>nltest /dsgetdc &lt;forest root DNS domain name &gt; /gc</code>
          <para>Запустите тест локатора NLTEST сразу же после попытки репликации, завершается с ошибкой 1396 на контроллер домена назначения. </para>
          <para>Это необходимо определить этот глобальный Каталог, выполняющий поиск имени участника-службы по KDC. </para>
          <para>Искомым, KDC сборщик Мусора также может содержаться в событий Microsoft-Windows-ActiveDirectory_DomainService кодами 1655.</para>
        </listItem>
        <listItem>
          <para>Поиск имени участника-службы, обнаруженные в шаге 1 в глобальном каталоге, обнаруженных на шаге 2.</para>
          <code>C:&gt;repadmin /showattr Server_Name DC=corp,DC=contoso,dc=com &lt;GC used by KDC&gt; &lt;DN path of forest root domain&gt; /filter:"(serviceprincipalname=&lt;SPN cited in the NTDS Replication event 1645&gt;)" /gc /subtree /atts:cn,serviceprincipalname</code>
          <para>ИЛИ</para>
          <code>C:&gt;dsquery * forestroot -scope subtree -filter "(serviceprincipalname=E3514235-4B06-11D1-AB04-00C04FC2DCD2/65cead9f-4949-46a3-a49a-f1fbfe13d2b3*)" -attr * -s Server_Name.europe.corp.contoso.com</code>
          <para>Убедитесь, что существует объект узла для имени участника-службы.</para>
          <para>Проверьте путь различающееся имя для узла объекта в том числе ли объект является CNF / конфликта искажен или находится в контейнере Потерянные и найденные.</para>
          <para>Убедитесь, что источник контроллеры домена Active Directory репликации имени участника-службы зарегистрирован только в исходной учетной записи компьютера для контроллеров домена.</para>
          <para>Если отсутствует имя участника-службы репликации, определите, если исходный контроллер домена выполнена регистрация имени участника-службы с самим собой и ли имя участника-службы отсутствует на сборщик Мусора, используемые KDC, из-за задержки репликации простой или сбое репликации.</para>
        </listItem>
        <listItem>
          <para>Проверьте работоспособность безопасный канал и доверять работоспособности.</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics>
    <externalLink>
      <linkText>Устранение неполадок, связанных с операциями Active Directory, завершающимися с ошибкой 1396 Ошибка входа: Указано неверное имя целевой учетной записи.</linkText>
      <linkUri>https://support.microsoft.com/kb/2183411/en-gb</linkUri>
    </externalLink>
  </relatedTopics>
</developerConceptualDocument>


