---
ms.assetid: 0f21951c-b1bf-43bb-a329-bbb40c58c876
title: "Существует ошибка репликации 1753: нет доступных конечных точек конечных точек"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 0e7412f5edc6c206888551fdc250883b5c0ced3e
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="replication-error-1753-there-are-no-more-endpoints-available-from-the-endpoint-mapper"></a>Существует ошибка репликации 1753: нет доступных конечных точек конечных точек

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012


<developerConceptualDocument xmlns="https://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="https://www.w3.org/1999/xlink" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="https://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>В этом разделе объясняется признаки, причины и способы устранения Active Directory Ошибка репликации 8524 DSA операция не удается продолжить из-за ошибки поиска в DNS.</para>
    <list class="bullet">
      <listItem><para><link xlink:href="f7022f0d-0099-410c-8178-c654e624bc42#BKMK_Symptoms">Симптомы</link></para></listItem><listItem><para><link xlink:href="f7022f0d-0099-410c-8178-c654e624bc42#BKMK_Cause">Причина</link></para></listItem><listItem><para><link xlink:href="f7022f0d-0099-410c-8178-c654e624bc42#BKMK_Resolutions">решения</link></para></listItem><listItem><para><link xlink:href="f7022f0d-0099-410c-8178-c654e624bc42#BKMK_MoreInfo">Дополнительные сведения</link></para></listItem>
    </list>
  </introduction>
  <section address="BKMK_Symptoms">
    <title>Проблема</title>
    <content>
      <para>в этой статье описаны симптомы, причина и шаги решения для операций Active Directory, завершающимися с ошибкой Win32 1753: «Нет осталось доступных конечных точек.» </para>
      <list class="ordered">
        <listItem>
          <para>Отчетов DCDIAG, проверка подключения, тест репликации Active Directory или KnowsOfRoleHolders тестирования завершилась с ошибкой 1753: «Нет осталось доступных конечных точек.» </para>
          <code>Testing server: &lt;site&gt;&lt;DC Name&gt;
Starting test: Connectivity
* Active Directory LDAP Services Check
* Active Directory RPC Services Check
[&lt;DC Name&gt;] <codeFeaturedElement>DsBindWithSpnEx() failed with error 1753,
There are no more endpoints available from the endpoint mapper..</codeFeaturedElement>
Printing RPC Extended Error Info:
Error Record 1, ProcessID is &lt;process ID&gt; (DcDiag) 
System Time is: &lt;date&gt; &lt;time&gt;
Generating component is 2 (RPC runtime)
Status is 1753: There are no more endpoints available from the endpoint mapper. Detection location is 500
NumberOfParameters is 4
Unicode string: ncacn_ip_tcp
Unicode string: &lt;source DC object GUID&gt;._msdcs.contoso.com
Long val: -481213899
Long val: 65537
Error Record 2, ProcessID is 700 (DcDiag) 
System Time is: &lt;date&gt; &lt;time&gt;
Generating component is 2 (RPC runtime)
<codeFeaturedElement>Status is 1753: There are no more endpoints available from the endpoint mapper.</codeFeaturedElement>
NumberOfParameters is 1
Unicode string: 1025
[Replications Check,&lt;DC Name&gt;] A recent replication attempt failed:
From &lt;source DC&gt; to &lt;destination DC&gt;
Naming Context: &lt;DN path of directory partition&gt;
The replication generated an error <codeFeaturedElement>(1753):
There are no more endpoints available from the endpoint mapper.</codeFeaturedElement> 
The failure occurred at &lt;date&gt; &lt;time&gt;.
The last success occurred at &lt;date&gt; &lt;time&gt;.
3 failures have occurred since the last success.
The directory on &lt;DC name&gt; is in the process.
of starting up or shutting down, and is not available.
Verify machine is not hung during boot.
</code>
        </listItem>
<listItem><para>REPADMIN. EXE сообщает, что репликация не выполнена с состоянием 1753. </para><para>REPADMIN команды, которые обычно упоминаются состояние 1753 относятся, но не ограничена:</para><table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11"><tbody><tr><TD><list class="bullet"><listItem><para>REPADMIN/REPLSUM</para></listItem><listItem><para>REPADMIN /SHOWREPL</para></listItem></list></TD><TD><list class="bullet"><listItem><para>REPADMIN/SHOWREPS</para></listItem><listItem><para>REPADMIN /SYNCALL</para></listItem></list></TD></tr></tbody></table><para>Пример выходных данных из «REPADMIN/SHOWREPS» показывает входящая репликация с CONTOSO DC2 сбоя CONTOSO-DC1 с ошибкой «доступ к репликации отвергнут» приведено ниже:</para><code>Default-First-Site-NameCONTOSO-DC1
DSA Options: IS_GC 
Site Options: (none)
DSA object GUID: b6dc8589-7e00-4a5d-b688-045aef63ec01
DSA invocationID: b6dc8589-7e00-4a5d-b688-045aef63ec01
==== INBOUND NEIGHBORS ======================================
DC=contoso,DC=com
Default-First-Site-NameCONTOSO-DC2 via RPC
DSA object GUID: 74fbe06c-932c-46b5-831b-af9e31f496b2
Last attempt @ &lt;date&gt; &lt;time&gt; failed, <codeFeaturedElement>result 1753 (0x6d9):
There are no more endpoints available from the endpoint mapper.</codeFeaturedElement>
&lt;#&gt; consecutive failure(s).
Last success @ &lt;date&gt; &lt;time&gt;.

</code></listItem><listItem><para><ui>Проверка топологии репликации</ui> возвращает команда в Active Directory — сайты и службы «Нет осталось доступных конечных точек.» </para><para>Правой кнопкой мыши на объекте подключения от исходного контроллера домена и выбрав <ui>Проверка топологии репликации</ui> завершается сбоем с «Нет осталось доступных конечных точек.» На экране сообщение об ошибке ниже:</para><para>текст заголовка диалоговое окно: Проверка топологии репликации</para><para>текст сообщения диалоговое окно: </para><para>произошла ошибка при попытке связаться с контроллером домена: нет несколько конечных точек конечных точек. </para></listItem><listItem><para><ui>Реплицировать сейчас</ui> возвращает команда в Active Directory — сайты и службы «нет осталось доступных конечных точек.» </para><para>Правой кнопкой мыши на объекте подключения от исходного контроллера домена и выбрав <ui>Реплицировать сейчас</ui> завершается сбоем с «Нет осталось доступных конечных точек.» На экране сообщение об ошибке ниже:</para><para>текст заголовка диалоговое окно: Реплицировать сейчас</para><para>текст сообщения диалоговое окно: произошла ошибка при попытке синхронизации контекста именования &lt;имя раздела каталога %&gt; с контроллера домена &lt;исходный контроллер домена&gt; контроллер домена &lt;контроллер домена назначения&gt;:</para><para>

Нет осталось доступных конечных точек. </para><para>Операция не будет продолжена</para></listItem><listItem><para>события проверки Согласованности NTDS, общие NTDS или Microsoft-Windows-ActiveDirectory_DomainService с состоянием-2146893022: главное записываются в журнал службы каталогов в средстве просмотра событий. </para><para>События active Directory, которые обычно упоминаются состояние-2146893022: главное относятся, но не ограничиваясь:</para><table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11"><thead><tr><TD><para>Код события</para></TD><TD><para>Источник события</para></TD><TD><para>Строка событий</para></TD></tr></thead><tbody><tr><TD><para>1655</para></TD><TD><para>NTDS Общие</para></TD><TD><para>Попытка обмениваться данными с следующие глобального каталога Active Directory и были неудачных попыток.</para></TD></tr><tr><TD><para>1925</para></TD><TD><para>ПРИ ПРОВЕРКЕ СОГЛАСОВАННОСТИ ЗНАНИЙ NTDS</para></TD><TD><para>Не удалось установить связь репликации для следующего раздела каталога с возможностью записи.</para></TD></tr><tr><TD><para>1265</para></TD><TD><para>ПРИ ПРОВЕРКЕ СОГЛАСОВАННОСТИ ЗНАНИЙ NTDS</para></TD><TD><para>Средство проверки согласованности знаний (KCC) для добавления соглашения репликации для следующих каталогов раздел и исходного контроллера домена не удалось.</para></TD></tr></tbody></table></listItem>
</list>
    </content>
  </section>
  <section address="BKMK_Cause">
    <title>Причина</title>
    <content>
      <para>на схеме ниже показан рабочий процесс RPC, начиная с регистрации для серверных приложений с сопоставления конечных точек RPC (EPM) на шаге 1 для передачи данных от клиента RPC клиентскому приложению на шаге 7. </para>
      <para>&lt;ADDS_RPCWorkflow&gt;</para>
      <para>шаги с 1 по 7 карты для следующих операций:</para>
      <list class="ordered">
        <listItem>
          <para>приложение Server регистрирует конечных точек с помощью сопоставления конечных точек RPC (EPM) </para>
        </listItem>
        <listItem>
          <para>клиент делает вызов RPC (от имени пользователя, операционная система или приложение инициируется операция) </para>
        </listItem>
        <listItem>
          <para>клиента параллельной контактов RPC EPM целевых компьютеров и попросите для конечной точки завершить вызов клиента </para>
        </listItem>
        <listItem>
          <para>EPM машины сервер отвечает с конечной точкой </para>
        </listItem>
        <listItem>
          <para>на стороне клиента RPC обращается приложение server </para>
        </listItem>
        <listItem>
          <para>приложения сервер выполняет вызов, возвращает результат клиенту RPC </para>
        </listItem>
        <listItem>
          <para>на стороне клиента RPC передает результат обратно в клиентское приложение</para>
        </listItem>
      </list>
      <para>сбой 1753 создается при сбое между шаги #3 и #4. В частности ошибка 1753 означает, что RPC-клиенту (конечного контроллера домена) не удалось связаться с сервером RPC (источника постоянного ТОКА) через порт 135, но EPM на RPC-сервер (источника постоянного ТОКА) не удалось найти приложение RPC, интересов и возвращается ошибки 1753 со стороны сервера. Наличие ошибки 1753 означает, что RPC-клиенту (конечного контроллера домена) получает ответ на ошибку стороне сервера с сервера RPC (репликации AD исходного контроллера домена) по сети. </para>
      <para>Включают конкретных причин ошибки 1753: </para>
      <list class="ordered">
        <listItem>
          <para>сервера приложение никогда не запущена (т. е. шаг 1 # схеме «подробнее», расположенную над никогда не предпринята попытка). </para>
        </listItem>
        <listItem>
          <para>Сервера приложение запущено, но был сбой во время инициализации, препятствующая регистрации конечных точек RPC (т. е. шаг 1 на схеме выше «сведения» не удается). </para>
        </listItem>
        <listItem>
          <para>Приложение server запущены, но впоследствии перестала работать. (т. е. шаг 1 на схеме выше «подробнее» успешно завершена, но она была отменена позже, поскольку сервер перестала). </para>
        </listItem>
        <listItem>
          <para>Приложение server вручную отменять регистрацию конечных точек (аналогично 3, но преднамеренно. Но, вероятно, не включен для полноты.) </para>
        </listItem>
        <listItem>
          <para>Отличается от предполагаемого один из-за имя ошибке сопоставления IP в DNS, WINS или узла или Lmhosts файл сервера RPC связаться с RPC клиента (конечного контроллера домена). </para>
        </listItem>
      </list>
      <para>1753 ошибка не является причиной возникновения: </para>
      <list class="bullet">
        <listItem>
          <para>отсутствие сетевого подключения между RPC-клиенту (конечного контроллера домена) и RPC-сервер (источника постоянного ТОКА) через порт 135</para>
        </listItem>
        <listItem>
          <para>отсутствие сетевого подключения между сервером RPC (источника постоянного ТОКА) с помощью порт 135 и RPC-клиенту (конечного контроллера домена) через временных портов. </para>
        </listItem>
        <listItem>
          <para>Происходит несоответствие паролей или невозможность с исходного контроллера домена для расшифровки зашифрованного пакета Kerberos</para>
        </listItem>
      </list>
      <para></para>
    </content>
  </section>
  <section address="BKMK_Resolutions">
    <title>Решения</title>
    <content>
      <list class="ordered">
        <listItem>
          <para>
            <embeddedLabel>убедитесь, что служба регистрации свою службу с конечных точек была запущена</embeddedLabel>
          </para>
          <para>для Windows 2000 и контроллеры домена Windows Server 2003: Убедитесь, что исходный контроллер домена загружается в обычном режиме. </para>
          <para>Для Windows Server 2008 или Windows Server 2008 R2: из консоли исходного контроллера домена, запустите (services.msc) диспетчер служб и убедитесь, что <embeddedLabel>доменных служб Active Directory</embeddedLabel> служба запущена. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Убедитесь, что RPC-клиенту (конечного контроллера домена) подключен предполагаемого RPC-сервер (источника постоянного ТОКА)</embeddedLabel>
          </para>
          <para>всех контроллеров домена в общих register леса Active Directory, запись CNAME контроллера домена в дочерний домен _msdcs. &lt;корневого домена леса&gt; зоны DNS, независимо от того, какие домена, они находятся в пределах леса. Запись CNAME контроллера домена является производным от <embeddedLabel>objectGUID</embeddedLabel> атрибута объекта параметров NTDS для каждого контроллера домена. </para>
          <para>При выполнении операций на основе репликации конечного контроллера домена запрашивает DNS запись CNAME контроллеры доменов источника. Запись CNAME содержит имя полного имени компьютера исходного контроллера домена, которое используется для формирования DCs IP-адрес источника через поиск кэша клиента в DNS, размещения / LMHost файл просмотра узла A или AAAA записи в DNS или WINS. </para>
          <para>Объектов устаревших параметров NTDS и поврежденных имя - to-IP сопоставления в DNS, WINS, узлов и LMHOST файлов может привести к RPC-клиенту (конечного контроллера домена) для подключения к неправильной RPC-сервер (исходный контроллер домена). Кроме того сопоставление to-IP поврежденных имя - может привести к RPC-клиенту (конечного контроллера домена) для подключения к компьютеру, даже не серверное приложение RPC интересов (роли Active Directory в данном случае) установлен. (Пример: запись устаревших узла для DC2 содержит IP-адрес DC3 или компьютер). </para>
          <para>Убедитесь, что для исходного контроллера домена, который существует в конечном копии контроллеров домена Active Directory objectGUID соответствует objectGUID исходного контроллера домена, хранящихся в исходной копии контроллеров домена Active Directory. В случае расхождений использовать repadmin /showobjmeta на объекте параметров ntds, чтобы узнать, какой из них соответствует последней повышения роли исходного контроллера домена (подсказка: сравнение отметки даты объект параметров NTDS, создать даты с /showobjmeta по дате последнего повышения роли в исходном файле dcpromo.log контроллеров домена. Может потребоваться использовать последнее изменение / create Дата DCPROMO.LOG ЖУРНАЛА). Если объект идентификаторы GUID не совпадают, конечного контроллера домена вероятно имеет устаревших объект параметров NTDS для исходного контроллера домена, запись CNAME относится запись узла с неправильным именем сопоставление IP. </para>
          <para>На конечный контроллер домена, выполните IPCONFIG//ALL следует определить, какие разрешения имен DNS-серверов, использующий для конечного контроллера домена:</para>
          <code>c:&gt;ipconfig /all</code>
          <para>на конечный контроллер домена, выполните NSLOOKUP относительно источника контроллеры домена полное имя контроллера домена запись CNAME:</para>
          <code>c:&gt;nslookup -type=cname &lt;fully qualified cname of source DC&gt; &lt;destination DCs primary DNS Server IP &gt;
c:&gt;nslookup -type=cname &lt;fully qualified cname of source DC&gt; &lt;destination DCs secondary DNS Server IP&gt;</code>
          <para>убедитесь, что IP-адрес, возвращаемый NSLOOKUP «владеющий» имя узла и идентификаторов безопасности исходного контроллера домена:</para>

          <code>C:&gt;NBTSTAT -A &lt;IP address returned by NSLOOKUP in the step above&gt;</code>
          <para>или</para>
          <para>вход на консоли исходного контроллера домена, выполните команду «IPCONFIG» в ОКНЕ командной строки и убедитесь, что исходный контроллер домена, которому принадлежит IP-адрес, возвращаемый указанной выше команды NSLOOKUP</para>
          <para>проверьте для устаревших / повторяющиеся узла для сопоставления IP-адресов в DNS</para>
          <code>NSLOOKUP -type=hostname &lt;single label hostname of source DC&gt; &lt;primary DNS Server IP on destination DC&gt;
NSLOOKUP -type=hostname &lt;single label hostname of source DC&gt; &lt;secondary DNS Server IP on destination DC&gt;

NSLOOKUP -type=hostname &lt;fully qualified computer name of source DC&gt; &lt;primary DNS Server IP on destination DC&gt;
NSLOOKUP -type=hostname &lt;fully qualified computer name of source DC&gt; &lt;secondary DNS Server IP on dest. DC&gt;</code>
<para>Если в записи узла существует недопустимый IP-адресов, проанализируйте ли уборку DNS включен и правильно настроен. </para><para>Если тесты выше или сетевой трассировки не отображается запрос возвращает недопустимый IP-адреса, рассмотрите возможность устаревших записей в узле файлов LMHOSTS и WINS-серверы. Обратите внимание, что DNS-серверов можно также настроить выполнять разрешение резервной имен WINS. </para>
</listItem>
        <listItem>
          <para>
            <embeddedLabel>Убедитесь, что серверное приложение (Active Directory и др) была зарегистрирована на конечных точек RPC-сервера (источника постоянного ТОКА)</embeddedLabel>
          </para>
          <para>Active Directory использует сочетание хорошо известных и динамически зарегистрированных портов. В этой таблице перечислены хорошо известных порты и протоколы, используемые контроллерами домена Active Directory.</para>
          <table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>RPC сервера приложений</para>
                </TD>
                <TD>
                  <para>Порт</para>
                </TD>
                <TD>
                  <para>TCP</para>
                </TD>
                <TD>
                  <para>UDP</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>DNS-сервера</para>
                </TD>
                <TD>
                  <para>53</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Kerberos</para>
                </TD>
                <TD>
                  <para>88</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Для LDAP-сервера</para>
                </TD>
                <TD>
                  <para>389</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Службы Каталогов Microsoft</para>
                </TD>
                <TD>
                  <para>445</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>LDAP SSL</para>
                </TD>
                <TD>
                  <para>636</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Сервер глобального каталога</para>
                </TD>
                <TD>
                  <para>3268</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
                <TD>
                  <para />
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Сервер глобального каталога</para>
                </TD>
                <TD>
                  <para>3269</para>
                </TD>
                <TD>
                  <para>X</para>
                </TD>
                <TD>
                  <para />
                </TD>
              </tr>
            </tbody>
          </table>
          <para>Сопоставитель конечных точек известные порты не зарегистрированы. </para>
          <para>Active Directory и другие приложения также зарегистрировать служб, получающим динамически назначаемых портов в диапазоне временных портов RPC. Такие приложения сервера RPC динамически назначены TCP-портов от 1024 до 5000 на компьютерах с Windows 2000 и Windows Server 2003 и порта между 49152 и 65535 диапазон на компьютерах с Windows Server 2008 и Windows Server 2008 R2. RPC-порт, используемый при репликации может быть жестко в реестре, выполняя действия, описанные в <externalLink><linkText>статье БАЗЫ знаний 224196</linkText><linkUri>https://support.microsoft.com/kb/224196</linkUri></externalLink>. Active Directory продолжает зарегистрироваться EPM при настройке на использование жестко порта. </para>
          <para>Убедитесь, что приложение RPC-сервер интерес зарегистрировался с конечных точек RPC на RPC-сервер (исходный контроллер домена в случае репликации AD). </para>
          <para>Существует несколько способов для выполнения этой задачи, но одна — установить и запустить PORTQRY из привилегированных CMD строке с правами администратора в консоли исходного контроллера домена, с помощью синтаксиса: </para>
          <code>c:\&gt;portquery -n &lt;source DC&gt; -e 135 &gt;file.txt</code>
          <para>в выходных данных portqry, обратите внимание, номера портов, динамически регистрируемых интерфейсом «MS NT Directory DRS» (UUID = 351...) для <embeddedLabel>протокола ncacn_ip_tcp</embeddedLabel>. В следующем фрагменте показан пример выходных данных portquery из контроллера домена Windows Server 2008 R2 и UUID / выделены пары протокола, в частности используемых Active Directory <embeddedLabel>полужирным шрифтом</embeddedLabel>: </para>
          <code>UUID: e3514235-4b06-11d1-ab04-00c04fc2dcd2 MS NT Directory DRS Interface
ncacn_np:CONTOSO-DC01[\pipe\lsass] 
UUID: e3514235-4b06-11d1-ab04-00c04fc2dcd2 MS NT Directory DRS Interface
ncacn_np:CONTOSO-DC01[\PIPE\protected_storage] 
<codeFeaturedElement>UUID: e3514235-4b06-11d1-ab04-00c04fc2dcd2 MS NT Directory DRS Interface
ncacn_ip_tcp:CONTOSO-DC01[49156]</codeFeaturedElement> 
UUID: e3514235-4b06-11d1-ab04-00c04fc2dcd2 MS NT Directory DRS Interface
ncacn_http:CONTOSO-DC01[49157] 
UUID: e3514235-4b06-11d1-ab04-00c04fc2dcd2 MS NT Directory DRS Interface
ncacn_http:CONTOSO-DC01[6004]</code>
          <para />
        </listItem>
        <listItem>
          <para>другие возможные способы устранения этой ошибки:</para>
          <list class="ordered">
            <listItem>
              <para>убедитесь, что исходный контроллер домена загружается в обычном режиме и полностью запустили роль операционной системы и контроллера домена на исходном контроллере домена. </para>
            </listItem>
            <listItem>
              <para>Убедитесь, что выполняется доменной службы Active Directory. Если служба остановлена или не были настроены со значениями по умолчанию запуска, восстановить значения по умолчанию запуска, перезагрузите измененные контроллера домена, затем повторите операцию. </para>
            </listItem>
            <listItem>
              <para>Проверьте правильность состояния значение и служба запуска для службы RPC и локатора RPC для версии операционной системы сервера RPC (исходный контроллер домена) и RPC-клиенту (конечного контроллера домена). Если служба остановлена или не были настроены со значениями по умолчанию запуска, восстановить значения по умолчанию запуска, перезагрузите измененные контроллера домена, затем повторите операцию. </para>
              <para>Кроме того, убедитесь, что контекст службы соответствует по умолчанию параметры, перечисленные в следующей таблице.</para>
              <table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Службы</para>
                    </TD>
                    <TD>
                      <para>Состояние по умолчанию (тип запуска) в Windows Server 2003 и более поздних версий </para>
                    </TD>
                    <TD>
                      <para>Состояние по умолчанию (тип запуска) в Windows Server 2000</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Удаленный вызов процедур</para>
                    </TD>
                    <TD>
                      <para>Запущена (автоматически)</para>
                    </TD>
                    <TD>
                      <para>Запущена (автоматически)</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Локатор удаленного вызова процедур</para>
                    </TD>
                    <TD>
                      <para>Значение NULL или остановлена (вручную)</para>
                    </TD>
                    <TD>
                      <para>Запущена (автоматически)</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </listItem>
            <listItem>
              <para>Убедитесь, что размер динамический диапазон портов не ограничена. Ниже показан синтаксис Windows Server 2008 и Windows Server 2008 R2 NETSH для перечисления диапазон портов RPC:</para>
              <code>&gt;netsh int ipv4 show dynamicport tcp
&gt;netsh int ipv4 show dynamicport udp
&gt;netsh int ipv6 show dynamicport tcp
&gt;netsh int ipv6 show dynamicport udp</code>
            </listItem>
            <listItem>
              <para>убедитесь, что определения жестко порт, определенные в КБ 224196 подпадающих динамический диапазон портов для исходной версии ОС контроллеров домена. </para>
              <para>Проверки <externalLink><linkText>статье БАЗЫ знаний 224196</linkText><linkUri>https://support.microsoft.com/kb/224196</linkUri></externalLink> и убедитесь, что жестко порт находится в диапазоне временных портов для версии операционной системы исходного контроллера домена. </para>
            </listItem>
            <listItem>
              <para>Убедитесь, что ключ ClientProtocols под HKLM\Software\Microsoft\Rpc существует и содержит следующие значения по умолчанию 5:</para>
              <code>ncacn_http REG_SZ rpcrt4.dll
ncacn_ip_tcp REG_SZ rpcrt4.dll
<codeFeaturedElement>ncacn_nb_tcp REG_SZ rpcrt4.dll</codeFeaturedElement>
ncacn_np REG_SZ rpcrt4.dll
ncacn_ip_udp REG_SZ rpcrt4.dll</code>
            </listItem>
          </list>
        </listItem>
      </list>
    </content>
  </section>
  <section address="BKMK_MoreInfo">
    <title>Дополнительные сведения</title>
    <content>
      <para>
        <embeddedLabel>пример неверное имя для IP-адреса, из-за которой ошибка RPC 1753 сравнение-2146893022: главное сопоставления: неверное имя участника целевой</embeddedLabel>
      </para>
      <para>contoso.com домена состоит из DC1 и DC2 с IP-адреса, x.x.1.1 и x.x.1.2. Узел «A» или «AAAA» записей для DC2 зарегистрированы правильно на всех DNS-серверов, настроенных для DC1. Кроме того в файл HOSTS на компьютере DC1 содержит запись сопоставляется IP адрес x.x.1.2 DC2s полное доменное имя узла. Более поздней версии DC2 изменения IP-адреса из X.X.1.2 X.X.1.3 и новый компьютер, входящий присоединен к домену с x.x.1.2 IP адрес. Репликации AD активируемых попыток <ui>Реплицировать сейчас</ui> оснастки Active Directory — сайты и службы произойдет сбой команды с ошибкой 1753 показанных ниже трассировки:</para>
      <code>F# SRC    DEST    Operation 
1 x.x.1.1 x.x.1.2 ARP:Request, x.x.1.1 asks for x.x.1.2
2 x.x.1.2 x.x.1.1 ARP:Response, x.x.1.2 at 00-13-72-28-C8-5E
3 x.x.1.1 x.x.1.2 TCP:Flags=......S., SrcPort=50206, DstPort=DCE endpoint resolution(135)
4 x.x.1.2 x.x.1.1 ARP:Request, x.x.1.2 asks for x.x.1.1
5 x.x.1.1 x.x.1.2 ARP:Response, x.x.1.1 at 00-15-5D-42-2E-00
6 x.x.1.2 x.x.1.1 TCP:Flags=...A..S., SrcPort=DCE endpoint resolution(135)
7 x.x.1.1 x.x.1.2 TCP:Flags=...A...., SrcPort=50206, DstPort=DCE endpoint resolution(135)
8 x.x.1.1 x.x.1.2 MSRPC:c/o Bind: UUID{E1AF8308-5D1F-11C9-91A4-08002B14A0FA} EPT(EPMP) 
9 x.x.1.2 x.x.1.1 MSRPC:c/o Bind Ack: Call=0x2 Assoc Grp=0x5E68 Xmit=0x16D0 Recv=0x16D0 
<codeFeaturedElement>10</codeFeaturedElement> x.x.1.1 x.x.1.2 EPM:Request: ept_map: NDR, DRSR(DRSR) {E3514235-4B06-11D1-AB04-00C04FC2DCD2} [DCE endpoint resolution(135)]
<codeFeaturedElement>11</codeFeaturedElement> x.x.1.2 x.x.1.1 EPM:Response: ept_map: 0x16C9A0D6 - EP_S_NOT_REGISTERED
</code>
      <para>в кадре <embeddedLabel>10</embeddedLabel>, конечного контроллера домена запрашивает сопоставителя конечных точек источника контроллеры домена через порт 135 для класса службы репликации Active Directory UUID E351... </para>
      <para>В кадре <embeddedLabel>11</embeddedLabel>, исходного контроллера домена, в этом случае компьютер, пока не размещена роль контроллера домена и поэтому не была зарегистрирована E351... UUID для службы репликации с его локальной EPM отвечает символических ошибка EP_S_NOT_REGISTERED сопоставляющей десятичных ошибка 1753, шестнадцатеричное ошибка 0x6d9 и сообщением об ошибке «существует осталось доступных конечных точек». </para>
      <para>Более поздней версии, компьютер член с x.x.1.2 IP адрес получает переходит в качестве реплики «MayberryDC» в домене contoso.com. Еще раз <ui>Реплицировать сейчас</ui> команда используется для запуска репликации, но сейчас завершается сбоем на экране ошибка «конечное имя неверное.» Компьютер, назначенный IP-адресов, сетевой адаптер адресов x.x.1.2 <placeholder>—</placeholder> контроллер домена в настоящее время загружается в обычном режиме и зарегистрирован E351... службы репликации UUID с его локальной EPM, но он не имеет имя или безопасности удостоверение DC2 и не удается расшифровать запрос Kerberos с DC1, поэтому запрос теперь завершается ошибкой «неверное конечное имя». Ошибка сопоставляется с ошибки в десятичном формате-2146893022: главное / шестнадцатеричный ошибка 0x80090322. </para>
      <para>Такие сопоставления to-IP недопустимый хост - может быть вызвано устаревших записей в узле / файлы lmhost узла A или AAAA регистрации в DNS или WINS. </para>
      <para>Сводка: в этом примере не удалось, так как сопоставление to-IP недопустимый хост-(в файле узла в данном случае) вызвал конечного контроллера домена для репликации, не еще зарегистрировано имя участника-службы и исходный контроллер домена, возвращена ошибка 1753 так устранения для контроллера домена, но не имеют доменных служб Active Directory, служба запущена (или даже установлены решением) «источник». Во втором случае недопустимый узла to-IP сопоставления (еще раз в файле узла) причиной конечного контроллера домена для подключения к контроллеру домена, который зарегистрирован E351... репликации имя участника-службы, но, источник имеет другое имя узла и безопасности удостоверение чем предполагаемого исходного контроллера домена, попыток завершилась ошибкой-2146893022: главное: конечное имя неверен.</para>
    </content>
  </section>
  <relatedTopics>
    <externalLink>
      <linkText>Устранение неполадок с операциями Active Directory, завершающимися с ошибкой 1753: нет несколько конечных точек конечных точек. </linkText>
      <linkUri>https://support.microsoft.com/kb/2089874</linkUri>
    </externalLink>
<externalLink><linkText>КБ статьи 839880 Устранение неполадок Сопоставитель конечных точек RPC ошибок, с помощью средств поддержки Windows Server 2003 с компакт-диска продукта</linkText><linkUri>https://support.microsoft.com/kb/839880</linkUri></externalLink>
<externalLink><linkText>КБ статья Общие сведения о службе 832017 и требования к сетевым портам для системы Windows Server</linkText><linkUri>https://support.microsoft.com/kb/832017/</linkUri></externalLink>
<externalLink><linkText>трафика репликации КБ статьи 224196 ограничение Active Directory и клиент RPC-трафик, к определенному порту</linkText><linkUri>https://support.microsoft.com/kb/224196/</linkUri></externalLink>
<externalLink><linkText>статья БАЗЫ знаний 154596 Настройка RPC динамического назначения портов для взаимодействия с брандмауэром</linkText><linkUri>https://support.microsoft.com/kb/154596</linkUri></externalLink><externalLink><linkText>RPC принцип</linkText><linkUri>https://msdn.microsoft.com/library/aa373935(VS.85).aspx</linkUri></externalLink><externalLink><linkText>Как сервер выполняет подготовку для подключения</linkText><linkUri>https://msdn.microsoft.com/library/aa373938(VS.85).aspx</linkUri></externalLink>
<externalLink><linkText>как клиент устанавливает соединение</linkText><linkUri>https://msdn.microsoft.com/library/aa373937(VS.85).aspx</linkUri></externalLink><externalLink><linkText>регистрации интерфейса</linkText><linkUri>https://msdn.microsoft.com/library/aa375357(VS.85).aspx</linkUri></externalLink><externalLink><linkText>доступность сервера в сети</linkText><linkUri>https://msdn.microsoft.com/library/aa373974(VS.85).aspx</linkUri></externalLink><externalLink><linkText>конечные точки регистрации</linkText><linkUri>https://msdn.microsoft.com/library/aa375255(VS.85).aspx</linkUri></externalLink><externalLink><linkText>прослушивание клиент вызывает</linkText><linkUri>https://msdn.microsoft.com/library/aa373966(VS.85).aspx</linkUri></externalLink><externalLink><linkText>как клиент устанавливает соединение</linkText><linkUri>https://msdn.microsoft.com/library/aa373937(VS.85).aspx</linkUri></externalLink><externalLink><linkText> Ограничение Active Directory трафика репликации и клиент RPC-трафик, к определенному порту</linkText><linkUri>https://support.microsoft.com/kb/224196</linkUri></externalLink><externalLink><linkText>участника-службы для целевой контроллер домена в Доменных службах Active Directory</linkText><linkUri>https://msdn.microsoft.com/library/dd207688(PROT.13).aspx</linkUri></externalLink></relatedTopics>
</developerConceptualDocument>


