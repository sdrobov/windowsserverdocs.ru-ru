---
ms.assetid: 399a8bbe-3375-4bb0-b55b-5f46e7050028
title: "Ошибка репликации 1396 входа в систему не произведен целевой учетная запись указана неверно"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 84799de26e1260f914d9b959357d5eed6fef62f6
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="replication-error-1396-logon-failure-the-target-account-name-is-incorrect"></a>Ошибка репликации 1396 входа в систему не произведен целевой учетная запись указана неверно

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012


<developerConceptualDocument xmlns="https://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="https://www.w3.org/1999/xlink" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="https://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>В этой статье описано, как следствие, причины и способы устранения репликации Active Directory, ошибка Win32 1396: «Ошибка входа в систему: неверное имя учетной записи целевой.» </para><list class="bullet"><listItem><para><link xlink:href="d3a01966-74c9-4c49-ba11-354b9acf7519#BKMK_Symptoms">Симптомы</link></para></listItem><listItem><para><link xlink:href="d3a01966-74c9-4c49-ba11-354b9acf7519#BKMK_Causes">вызывает</link></para></listItem><listItem><para><link xlink:href="d3a01966-74c9-4c49-ba11-354b9acf7519#BKMK_Resolutions">решения</link></para></listItem></list>
  </introduction>
  <section address="BKMK_Symptoms">
    <title>Проблема</title>
    <content>
      <para />
      <list class="ordered">
<listItem><para>DCDIAG отчеты, которые тестирования репликации Active Directory завершилась с ошибкой 1396: Ошибка входа в систему: неверное имя учетной записи целевой.» </para><code>Testing server: &lt;Site name&gt;&lt;DC Name&gt;
Starting test: Replications
[Replications Check,&lt;DC Name&gt;] A recent replication attempt failed:
From &lt;source DC&gt; to &lt;destination DC&gt;
Naming Context: CN=&lt;DN path of naming context&gt;
<codeFeaturedElement>The replication generated an error (1396):
Logon Failure: The target account name is incorrect.</codeFeaturedElement>
The failure occurred at &lt;date&gt; &lt;time&gt;.
The last success occurred at &lt;date&gt; &lt;time&gt;.
XX failures have occurred since the last success</code></listItem><listItem><para>REPADMIN. EXE отчеты сбой с состоянием 1396 последней попытке репликации. </para><para>REPADMIN команды, которые обычно упоминаются состояние 1396 относятся, но не ограничена:</para><table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11"><tbody><tr><TD><list class="bullet"><listItem><para>REPADMIN/Add</para></listItem><listItem><para>REPADMIN/REPLSUM</para></listItem><listItem><para>REPADMIN /REHOST</para></listItem><listItem><para>REPADMIN /SHOWVECTOR /LATENCY</para></listItem></list></TD><TD><list class="bullet"><listItem><para>REPADMIN/SHOWREPS</para></listItem><listItem><para>REPADMIN /SHOWREPL</para></listItem><listItem><para>REPADMIN /SYNCALL</para></listItem></list></TD></tr></tbody></table><para>Пример выходных данных из «REPADMIN/SHOWREPS» показывает входящая репликация с CONTOSO DC2 CONTOSO-DC1 отказывать в «Ошибка входа в систему: неверное имя учетной записи целевой.» ошибка отображается под::</para><code>Default-First-Site-NameCONTOSO-DC1
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
</code></listItem><listItem><para><ui>Реплицировать сейчас</ui> возвращает команда в Active Directory — сайты и службы» Ошибка входа в систему: неверное имя учетной записи целевой.» </para><para>Правой кнопкой мыши на объекте подключения от исходного контроллера домена и выбрав <ui>Реплицировать сейчас</ui> завершается сбоем с «Ошибка входа в систему: неверное имя учетной записи целевой.» На экране сообщение об ошибке ниже:</para><para>текст заголовка диалоговое окно:</para><para>Реплицировать сейчас</para><para>текст сообщения диалоговое окно: </para><para>произошла ошибка при попытке синхронизации контекста именования &lt;путь к разделу DNS&gt; с контроллера домена &lt;исходного контроллера домена&gt; контроллер домена &lt;конечного контроллера домена&gt;: Ошибка входа в систему: неверное имя учетной записи целевой. Эта операция не будет. </para></listItem><listItem><para>События проверки Согласованности NTDS, общие NTDS или Microsoft-Windows-ActiveDirectory_DomainService с состоянием 1396 записываются в журнал службы каталогов в средстве просмотра событий. </para><para>События active Directory, которые обычно упоминаются состояние 1396 относятся, но не ограничена:</para><table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11"><thead><tr><TD><para>Код события</para></TD><TD><para>Источник события</para></TD><TD><para>Строка событий</para></TD></tr></thead><tbody><tr><TD><para>1125</para></TD><TD><para>Microsoft-Windows-ActiveDirectory_DomainService</para></TD><TD><para>Active Directory домена мастер установки служб (Dcpromo) не удалось установить подключение к следующему контроллеру домена.</para></TD></tr><tr><TD><para>1645</para><para>это событие перечислены имя участника-службы для трех частей.</para></TD><TD><para>NTDS репликации</para></TD><TD><para>Active Directory не удалось выполнить проверенный удаленный вызов процедуры (RPC) на другой контроллер домена, поскольку имя участника требуемой службы (SPN) для конечного контроллера домена не зарегистрировано на контроллере домена центра распространения ключей (KDC), которая разрешает имя участника-службы.</para></TD></tr><tr><TD><para>1655</para></TD><TD><para>Microsoft-Windows-ActiveDirectory_DomainService</para></TD><TD><para>Попытка обмениваться данными с следующие глобального каталога доменных служб Active Directory и были неудачных попыток.</para></TD></tr><tr><TD><para>2847</para></TD><TD><para>Microsoft-Windows-ActiveDirectory_DomainService</para></TD><TD><para>Средство проверки согласованности знаний находится подключение репликации для этот сервер службы каталогов только для чтения и предприняла попытку обновления удаленно на следующем экземпляр службы каталогов. Не удалось выполнить операцию. Он будет повторена.</para></TD></tr><tr><TD><para>1925</para></TD><TD><para>ПРИ ПРОВЕРКЕ СОГЛАСОВАННОСТИ ЗНАНИЙ NTDS</para></TD><TD><para>Не удалось установить связь репликации для следующего раздела каталога с возможностью записи.</para></TD></tr><tr><TD><para>1926</para></TD><TD><para>ПРИ ПРОВЕРКЕ СОГЛАСОВАННОСТИ ЗНАНИЙ NTDS</para></TD><TD><para>Попытка установления связи репликации на раздел каталога только для чтения с указанными ниже параметрами, которые не удалось.</para></TD></tr><tr><TD><para>5781</para></TD><TD><para>СЛУЖБЫ NETLOGON</para></TD><TD><para> Серверу не удается зарегистрировать свое имя в DNS.</para></TD></tr></tbody></table></listItem><listItem><para>DCPROMO происходит сбой с ошибкой на экране</para><para>текст заголовка диалоговое окно:</para><para>Active Directory не удалось установить</para><para>текстовое сообщение в диалоговом окне:</para><para>произошел сбой операции: служба каталогов не удалось создать объект-сервер для CN = NTDS Settings, CN ServerBeingPromoted, CN = Servers, CN = = Site, CN = Sites, CN = Configuration, DC = contoso, DC = com на сервере ReplicationSourceDC.contoso.com. </para><para>Убедитесь сетевые учетные данные для предоставленных иметь достаточных прав доступа для добавления реплики.</para><para> «Ошибка входа в систему: неверное имя учетной записи целевой.» </para><para>В этом случае событие с кодом 1645, 1168 и 1125 регистрируются на сервере, который выдвинут на роль. </para></listItem><listItem><para>Сопоставления диска с помощью <embeddedLabel>net используйте</embeddedLabel>:</para><code>C:&gt;net use z: &lt;server_name&gt;c$
System error 1396 has occurred.
Logon Failure: The target account name is incorrect.</code><para>в этом случае сервер может также ведения журналов 333 идентификатор события в журнале системных событий и использовать высокий объем виртуальной памяти для приложения, такие как SQL Server. </para></listItem><listItem><para>Неверное время контроллера домена. </para></listItem><listItem><para>Центра распространения КЛЮЧЕЙ не будут запускаться на RODC после восстановления учетной записи krbtgt для RODC, которая была удалена. Например после восстановления, отображается об ошибке 1396. </para><para>1645 ИД событий регистрируется в RODC. </para><para>Dcdiag также появляется сообщение об ошибке, не может обновить учетной записи krbtgt RODC.</para></listItem>
</list>
    </content>
  </section>
  <section address="BKMK_Causes">
    <title>вызывает</title>
    <content>
      <para />
      <list class="ordered">
        <listItem>
          <para>SPN не существует в глобальном каталоге поиск KDC от лица клиента, пытающегося пройти проверку подлинности Kerberos.</para>
          <para>в контексте репликации Active Directory, Kerberos клиент конечного контроллера домена, выполняя поиск имени участника-службы KDC, скорее всего, назначения самого контроллера домена, но может быть удаленного контроллера домена.</para>
        </listItem>
        <listItem>
          <para>учетной записи пользователя или службы, которая содержит службы, имя участника, поиск не существует в глобальном каталоге поиск KDC от имени конечного контроллера домена, попытка репликации.</para>
          <para>в контексте репликации Active Directory, источник учетной записи компьютера контроллера домена не существует в глобальном каталоге поиск контроллера домена от имени конечного контроллера домена выполнение входящей репликации.</para>
        </listItem>
        <listItem>
          <para>конечного контроллера домена отсутствует секрета LSA контроллеры домена в исходном домене.</para>
        </listItem>
        <listItem>
          <para>на другую учетную запись компьютера от исходного контроллера домена существует выполняется поиск имени участника-службы.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section address="BKMK_Resolutions">
    <title>Решения</title>
    <content>
      <list class="ordered">
        <listItem>
          <para>Проверьте журнал событий службы каталогов на конечного контроллера домена для репликации NTDS события 1645 и обратите внимание на следующее:</para>
          <para>имя конечного контроллера домена</para>
          <para>ищутся, имя участника-службы (E3514235-4B06-11D1-AB04-00C04FC2DCD2 или&lt;guid объекта параметров NTDS контроллеры доменов источника объекта&gt;/&lt;целевой домен&gt;.&lt; TLD&gt;@&lt;целевой домен&gt;. &lt;tld&gt;</para>
          <para>центра распространения КЛЮЧЕЙ, используемых для конечного контроллера домена</para>
        </listItem>
        <listItem>
          <para>из консоли KDC, указанный в шаге 1, введите: </para>
          <code>nltest /dsgetdc &lt;forest root DNS domain name &gt; /gc</code>
          <para>выполните тестирование обнаружения NLTEST сразу же после попытки репликации, завершается ошибкой 1396 на конечный контроллер домена. </para>
          <para>Это следует определить этот глобальный Каталог, осуществляющего поиск имени участника-службы от KDC. </para>
          <para>Искомых по KDC глобального Каталога может также записываться в событий Microsoft-Windows-ActiveDirectory_DomainService кодами 1655. </para>
        </listItem>
        <listItem>
          <para>Поиск имя участника-службы, обнаруженные в шаге 1 в глобальный каталог, обнаруженных на шаге 2. </para>
          <code>C:&gt;repadmin /showattr Server_Name DC=corp,DC=contoso,dc=com &lt;GC used by KDC&gt; &lt;DN path of forest root domain&gt; /filter:"(serviceprincipalname=&lt;SPN cited in the NTDS Replication event 1645&gt;)" /gc /subtree /atts:cn,serviceprincipalname</code>
          <para>Или</para>
          <code>C:&gt;dsquery * forestroot -scope subtree -filter "(serviceprincipalname=E3514235-4B06-11D1-AB04-00C04FC2DCD2/65cead9f-4949-46a3-a49a-f1fbfe13d2b3*)" -attr * -s Server_Name.europe.corp.contoso.com</code>
          <para>убедитесь, что существует объект узла для имя участника-службы. </para>
          <para>Проверьте путь DN для узла объекта в том числе ли объект является CNF или конфликт искажен или находится в контейнере Потерянные и найденные. </para>
          <para>Убедитесь, что источник контроллеров домена Active Directory репликация имя участника-службы зарегистрирован только на исходном контроллеры домена учетной записи компьютера. </para>
          <para>Если репликация имя участника-службы отсутствует, определить исходного контроллера домена была зарегистрирована ее имя участника-службы на себя и ли имя участника-службы отсутствует на сервере глобального Каталога, используемые центром распространения КЛЮЧЕЙ из-за задержки репликации простой или сбой репликации. </para>
        </listItem>
        <listItem>
          <para>Проверьте работоспособность безопасного канала и доверяете работоспособности.</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics>
    <externalLink>
      <linkText>операциями устранения неполадок Active Directory, завершающимися с ошибкой 1396: Ошибка входа в систему: неверное имя учетной записи целевой.</linkText>
      <linkUri>https://support.microsoft.com/kb/2183411/en-gb</linkUri>
    </externalLink>
  </relatedTopics>
</developerConceptualDocument>


