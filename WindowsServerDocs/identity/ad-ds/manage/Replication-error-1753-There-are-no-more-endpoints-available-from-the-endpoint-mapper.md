---
ms.assetid: 0f21951c-b1bf-43bb-a329-bbb40c58c876
title: 'Ошибка репликации 1753: в системе отображения конечных точек не осталось доступных конечных точек'
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: a280d540d09c6fdcb7846d1cf545856869be1152
ms.sourcegitcommit: b190fac4bfa5599751a60d3fc3b4c4a64dd9afd7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66008964"
---
# <a name="replication-error-1753-there-are-no-more-endpoints-available-from-the-endpoint-mapper"></a>Ошибка репликации 1753: в системе отображения конечных точек не осталось доступных конечных точек

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012


<developerConceptualDocument xmlns="https://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="https://www.w3.org/1999/xlink" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="https://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd"> <introduction>
    <para>В этом разделе объясняется симптомы, причины и способы решения Active Directory репликации ошибка 8524 Операция DSA не может быть продолжена из-за ошибка поиска в DNS.</para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="f7022f0d-0099-410c-8178-c654e624bc42#BKMK_Symptoms">Проблема</link>
        </para>
      </listItem> <listItem>
        <para>
          <link xlink:href="f7022f0d-0099-410c-8178-c654e624bc42#BKMK_Cause">Причина</link>
        </para>
      </listItem> <listItem>
        <para>
          <link xlink:href="f7022f0d-0099-410c-8178-c654e624bc42#BKMK_Resolutions">Способы их устранения</link>
        </para>
      </listItem> <listItem>
        <para>
          <link xlink:href="f7022f0d-0099-410c-8178-c654e624bc42#BKMK_MoreInfo">Дополнительные сведения</link>
        </para>
      </listItem>
    </list>
  </introduction>
  <section address="BKMK_Symptoms">
    <title>Проблема</title>
    <content>
      <para>В этой статье описывается проблема, причина и решение пошаговые инструкции по с операциями Active Directory, завершающимися с ошибкой Win32 1753: «Имеются осталось доступных конечных точек.»</para>
      <list class="ordered">
        <listItem>
          <para>Отчеты DCDIAG, проверка подключения, тестирования репликации Active Directory или KnowsOfRoleHolders теста завершилось ошибкой 1753: «Имеются осталось доступных конечных точек.»</para>
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
<listItem><para>REPADMIN. EXE-файла сообщает, что попытка репликации не удалось с состоянием 1753 г.</para><para>Часто упоминаются 1753 г состояние включают, но не ограничиваются команды REPADMIN:</para><table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11"><tbody><tr><TD><list class="bullet"><listItem><para>REPADMIN/REPLSUM</para></listItem><listItem><para>REPADMIN /SHOWREPL</para></listItem></list></TD><TD><list class="bullet"><listItem><para>REPADMIN/SHOWREPS</para></listItem><listItem><para>REPADMIN/SYNCALL</para></listItem></list></TD></tr></tbody></table><para>Ниже приведен пример выходных данных из «REPADMIN/SHOWREPS» показывает входящая репликация с CONTOSO-DC2 для CONTOSO-DC1 сбой с ошибкой «доступ к репликации отвергнут»:</para><code>Default-First-Site-NameCONTOSO-DC1
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

</code></listItem><listItem><para><ui>Проверка топологии репликации</ui> Возвращает команды в Active Directory — сайты и службы «Имеются осталось доступных конечных точек.»</para><para>Щелкните правой кнопкой мыши на объект соединения из исходного контроллера домена и выборе <ui>Проверка топологии репликации</ui> завершается ошибкой «Имеются осталось доступных конечных точек.» На экране ниже выводится сообщение об ошибке:</para><para>Текст заголовка диалогового окна: Проверка топологии репликации</para><para>Текст сообщения диалогового окна: </para><para>При попытке связаться с контроллером домена произошла следующая ошибка: Осталось доступных конечных точек.</para></listItem><listItem><para><ui>Реплицировать сейчас</ui> Возвращает команды в Active Directory — сайты и службы «имеются осталось доступных конечных точек.»</para><para>Щелкните правой кнопкой мыши на объект соединения из исходного контроллера домена и выборе <ui>Реплицировать сейчас</ui> завершается ошибкой «Имеются осталось доступных конечных точек.» На экране ниже выводится сообщение об ошибке:</para><para>Текст заголовка диалогового окна: Теперь репликация</para><para>Текст сообщения диалогового окна: Произошла следующая ошибка при попытке синхронизации контекста именования &lt;имя секции каталога %&gt; от контроллера домена &lt;исходный контроллер домена&gt; к контроллеру домена &lt;конечный контроллер домена&gt;:</para><para>

Осталось доступных конечных точек.</para><para>Операция не будет продолжена</para></listItem><listItem><para>NTDS KCC "," Общие NTDS "или" Microsoft-Windows-ActiveDirectory_DomainService с состоянием-2146893022 событий в журнале службы каталогов в средстве просмотра событий.</para><para>События Active Directory, которые часто упоминаются состояние-2146893022 включают, но не ограничиваются:</para><table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11"><thead><tr><TD><para>Идентификатор события</para></TD><TD><para>Источник события</para></TD><TD><para>Строка событий</para></TD></tr></thead><tbody><tr><TD><para>1655</para></TD><TD><para>NTDS Общие</para></TD><TD><para>Попытки обмена данными с помощью следующих глобального каталога Active Directory и попытки завершились с ошибкой.</para></TD></tr><tr><TD><para>1925</para></TD><TD><para>NTDS KCC</para></TD><TD><para>Не удалось установить связь репликации для следующего раздела каталога с возможностью записи.</para></TD></tr><tr><TD><para>1265</para></TD><TD><para>NTDS KCC</para></TD><TD><para>Проверки согласованности знаний (KCC) Добавление соглашения репликации для следующий каталог секции и исходный контроллер домена не удалось.</para></TD></tr></tbody></table></listItem>
</list>
    </content>
  </section>
  <section address="BKMK_Cause">
    <title>Причина</title>
    <content>
      <para>На следующей схеме показан рабочий процесс RPC, начиная с регистрации серверного приложения с помощью модуля сопоставления конечной точки RPC (EPM) на шаге 1, чтобы передавать данные от клиента RPC клиентскому приложению на шаге 7. </para>
      <para>&lt;ADDS_RPCWorkflow&gt;</para>
      <para>Шаги 1 – 7 карты для следующих операций:</para>
      <list class="ordered">
        <listItem>
          <para>Серверное приложение регистрирует ее конечных точек RPC Endpoint Mapper (EPM) </para>
        </listItem>
        <listItem>
          <para>Клиент отправляет вызов RPC (от имени пользователя, операционной системы или приложения инициировавшим операцию) </para>
        </listItem>
        <listItem>
          <para>RPC на стороне клиента связывается на конечных компьютерах EPM и задать для конечной точки для завершения этого клиентского вызова </para>
        </listItem>
        <listItem>
          <para>Машины Server EPM отвечает с конечной точкой </para>
        </listItem>
        <listItem>
          <para>Серверное приложение обращается к RPC на стороне клиента </para>
        </listItem>
        <listItem>
          <para>Серверное приложение выполняет вызов, возвращает результат клиенту RPC </para>
        </listItem>
        <listItem>
          <para>RPC на стороне клиента передает результат обратно в клиентское приложение</para>
        </listItem>
      </list>
      <para>Сбой между шагами #3 и #4 создается сбоя 1753 г. В частности ошибка 1753 означает, что клиенту RPC (контроллер домена назначения) не удалось связаться с RPC-сервер (исходного контроллера домена) через порт 135, но EPM на RPC-сервер (исходный контроллер домена) не удалось найти интересующими приложением RPC и вернул ошибку на стороне сервера 1753 г. Наличие ошибки 1753 указывает, что клиент RPC (контроллер домена назначения) получил ответа на ошибку на стороне сервера от RPC-сервер (репликации AD исходного контроллера домена) по сети. </para>
      <para>Корневой 1753 причины ошибки: </para>
      <list class="ordered">
        <listItem>
          <para>Серверное приложение не запускалось (т. е. шаг 1 в диаграмме «подробнее», расположенную над никогда не выполнялась).</para>
        </listItem>
        <listItem>
          <para>Запустить приложение сервера, но был какой-либо сбой во время инициализации, препятствующая регистрации конечных точек RPC (т. е. шаг 1 в приведенной выше схеме «подробнее» произошел сбой попытки).</para>
        </listItem>
        <listItem>
          <para>Серверное приложение к работе, но впоследствии умер. (т. е. шаг 1 в приведенной выше схеме «подробнее» выполнено успешно, но было отменено позже, так как сервер умер).</para>
        </listItem>
        <listItem>
          <para>Серверное приложение вручную отменять регистрацию конечных точек (как и 3, но намеренно. Но, вероятно, не включен для полноценного списка.)</para>
        </listItem>
        <listItem>
          <para>Клиент RPC (контроллер домена назначения) связаться с на другой сервер RPC, чем тот из-за имени в IP-адрес ошибки сопоставления в DNS, WINS или файл узла/Lmhosts.</para>
        </listItem>
      </list>
      <para>Ошибка 1753 не вызвано: </para>
      <list class="bullet">
        <listItem>
          <para>Отсутствие сетевого подключения между клиентом RPC (контроллер домена назначения) и RPC-сервер (исходного контроллера домена) через порт 135</para>
        </listItem>
        <listItem>
          <para>Отсутствие сетевого подключения между RPC-сервер (исходного контроллера домена) через порт 135 и клиент RPC (контроллер домена назначения) временных портов. </para>
        </listItem>
        <listItem>
          <para>Несоответствие паролей или невозможности с исходного контроллера домена для расшифровки зашифрованный пакет Kerberos </para>
        </listItem>
      </list>
      <para> </para>
    </content>
  </section>
  <section address="BKMK_Resolutions">
    <title>Способы их устранения</title>
    <content>
      <list class="ordered">
        <listItem>
          <para>
            <embeddedLabel>Проверьте, запущена служба регистрации его службы с помощью конечных точек ли</embeddedLabel>
          </para>
          <para>Для Windows 2000 и контроллеров домена Windows Server 2003: Убедитесь, что исходный контроллер домена загружается в обычном режиме. </para>
          <para>
Для Windows Server 2008 или Windows Server 2008 R2: из консоли исходного контроллера домена, запустите диспетчер служб (services.msc) и убедитесь, что <embeddedLabel>доменных служб Active Directory</embeddedLabel> служба запущена. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Проверьте этот клиент RPC (контроллер домена назначения), подключенных к нужному серверу RPC (исходный контроллер домена)</embeddedLabel>
          </para>
          <para>Все контроллеры домена в лесу Active Directory распространенных зарегистрировать контроллер домена запись CNAME в _msdcs. &lt;корневого домена леса&gt; зоны DNS, независимо от того, они находятся в пределах леса доменов. Контроллер домена запись CNAME является производным от <embeddedLabel>objectGUID</embeddedLabel> атрибута объекта параметров NTDS для каждого контроллера домена. </para>
          <para>При выполнении операции на основе репликации, контроллер домена назначения запрашивает источник контроллеры домена запись CNAME DNS. Запись CNAME содержит имя полного имени компьютера исходного контроллера домена, которое используется для получения источника контроллеры домена IP-адрес с помощью поиска в кэше клиента DNS, размещения / LMHost файл поиска узла A / AAAA записи в DNS или WINS. </para>
          <para>Устаревших объектов параметров NTDS и неверный сопоставлений имя IP-в DNS, WINS, узел и LMHOST файлов может вызвать клиент RPC (контроллер домена назначения) для подключения к серверу RPC не так (исходный контроллер домена). Кроме того неверный сопоставление имя IP-может привести к клиент RPC (контроллер домена назначения) для подключения к компьютеру, даже не поддерживает приложение сервера RPC интерес (роль Active Directory в данном случае) установлен. (Пример: запись устаревших узла для DC2 содержит IP-адрес DC3 или компьютере его члена). </para>
          <para>Проверяет соответствие objectGUID для исходного контроллера домена, который существует в месте назначения копирования контроллеров домена Active Directory objectGUID исходного контроллера домена, хранящиеся в источнике копии контроллеров домена Active Directory. Если есть несоответствие, используйте repadmin/showobjmeta на объекте параметров ntds, чтобы узнать, какой из них соответствует последней продвижение исходного контроллера домена (подсказка: сравнение отметки даты для объекта параметров NTDS создать дату из/showobjmeta от последней датой продвижения в исходный файл dcpromo.log контроллеров домена. Возможно создание Дата DCPROMO и использование последнее изменение. Сам файл ЖУРНАЛА). Если идентификаторы GUID объекта не совпадают, скорее всего контроллер домена назначения имеет устаревший объект параметров NTDS для исходного контроллера домена, записи CNAME подразумевается запись узла с неправильное имя для сопоставления IP-адрес. </para>
          <para>В контроллер домена назначения выполните команду IPCONFIG режиме, чтобы определить, какие DNS-серверы целевой контроллер домена, используемого для разрешения имен:</para>
          <code>c:&gt;ipconfig /all</code>
          <para>На контроллер домена назначения запустите команду NSLOOKUP в источнике запись CNAME контроллера домена с полным контроллеров домена:</para>
          <code>c:&gt;nslookup -type=cname &lt;fully qualified cname of source DC&gt; &lt;destination DCs primary DNS Server IP &gt;
c:&gt;nslookup -type=cname &lt;fully qualified cname of source DC&gt; &lt;destination DCs secondary DNS Server IP&gt;</code>
          <para>Убедитесь, что IP-адрес, возвращенный NSLOOKUP «владеет» имя узла или идентификатор безопасности исходного контроллера домена:</para>
          <code>C:&gt;NBTSTAT -A &lt;IP address returned by NSLOOKUP in the step above&gt;</code>
          <para>или</para>
          <para>Войдите на консоль исходного контроллера домена, выполнить команду «IPCONFIG» в командной строке команду CMD и убедитесь, что исходный контроллер домена, которому принадлежит IP-адрес, возвращаемый выше команды NSLOOKUP</para>
          <para>Проверка для сопоставления IP-адресов в DNS узла устарел или повторяющиеся</para>
          <code>NSLOOKUP -type=hostname &lt;single label hostname of source DC&gt; &lt;primary DNS Server IP on destination DC&gt;
NSLOOKUP -type=hostname &lt;single label hostname of source DC&gt; &lt;secondary DNS Server IP on destination DC&gt;

NSLOOKUP -type=hostname &lt;fully qualified computer name of source DC&gt; &lt;primary DNS Server IP on destination DC&gt;
NSLOOKUP -type=hostname &lt;fully qualified computer name of source DC&gt; &lt;secondary DNS Server IP on dest. DC&gt;</code>
<para>Если в записи узла существует недопустимый IP-адресов, изучите ли очистку DNS включен и правильно настроен. </para><para>Если тесты выше или сетевой трассировки не отображается имя запроса, возвращающего недопустимый IP-адрес, рассмотрите возможность устаревшие записи в файлы узла, файлы LMHOSTS и WINS-серверы. Обратите внимание на то, что DNS-серверы также можно настроить для разрешения WINS отката.</para>
</listItem>
        <listItem>
          <para>
            <embeddedLabel>Убедитесь, что серверное приложение (Active Directory и т.п) был зарегистрирован Сопоставитель конечных точек на RPC-сервер (исходный контроллер домена)</embeddedLabel>
          </para>
          <para>Active Directory использует сочетание хорошо известного и динамически зарегистрированных портов. В этой таблице перечислены стандартные порты и протоколы, используемые контроллерами домена Active Directory.</para>
          <table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Приложения сервера RPC</para>
                </TD>
                <TD>
                  <para>Port</para>
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
                  <para>DNS-сервер</para>
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
                  <para>Сервер LDAP</para>
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
                  <para>Microsoft-доменных служб Active Directory</para>
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
          <para>Порты не зарегистрированы с помощью конечных точек. </para>
          <para>Active Directory и другие приложения также зарегистрировать службы, которые получают динамически назначаемые порты в диапазон временных портов RPC. Такие приложения сервера RPC назначаются динамически, TCP-портов от 1024 до 5000 на компьютерах с Windows 2000 и Windows Server 2003 и порта между 49152 и 65535 диапазона на компьютерах с Windows Server 2008 и Windows Server 2008 R2. RPC-порт, используемый при репликации могут быть жестко в реестре, выполняя действия, описанные в <externalLink> <linkText>статье базы Знаний 224196</linkText><linkUri>https://support.microsoft.com/kb/224196</linkUri></externalLink>. Active Directory продолжает регистрировать с EPM при настройке для использования жестко заданный порт. </para>
          <para>Убедитесь, что RPC-сервер приложения интерес зарегистрировался с помощью конечных точек RPC на сервере RPC (исходный контроллер домена в случае репликации AD). </para>
          <para>Существует ряд способов для выполнения этой задачи, но один — для установки и запуска PORTQRY в командной строке администратора привилегированных CMD на консоли исходного контроллера домена, используя синтаксис: </para>
          <code>c:\&gt;portquery -n &lt;source DC&gt; -e 135 &gt;file.txt</code>
          <para>В выходных данных portqry, обратите внимание, номера портов, динамически зарегистрированных «MS NT DRS интерфейса каталога» (UUID = 351...) для <embeddedLabel>протокола ncacn_ip_tcp</embeddedLabel>. В следующем фрагменте показано portquery пример выходных данных из контроллера домена Windows Server 2008 R2 и UUID / пары протокола, используемые службой каталогов Active Directory они выделены <embeddedLabel>полужирным</embeddedLabel>: </para>
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
          <para>Другие возможные способы устранения этой ошибки:</para>
          <list class="ordered">
            <listItem>
              <para>Убедитесь, что исходный контроллер домена загружается в обычном режиме и полностью начали роль операционной системы и контроллера домена на исходный контроллер домена.</para>
            </listItem>
            <listItem>
              <para>Убедитесь, что запущена служба домена Active Directory. Если служба остановлена или не была настроена со значениями по умолчанию запуска, восстановить значения по умолчанию запуска, перезагрузите измененные контроллер домена, затем повторите операцию.</para>
            </listItem>
            <listItem>
              <para>Проверьте состояние запуска значение и службы для службы RPC и локатора RPC для версии операционной системы клиент RPC (контроллер домена назначения) и RPC-сервер (исходный контроллер домена). Если служба остановлена или не была настроена со значениями по умолчанию запуска, восстановить значения по умолчанию запуска, перезагрузите измененные контроллер домена, затем повторите операцию.</para>
              <para>Кроме того убедитесь, что контекст службы соответствует по умолчанию параметры, перечисленные в следующей таблице.</para>
              <table xmlns:caps="https://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Обслуживание</para>
                    </TD>
                    <TD>
                      <para>Состояние по умолчанию (тип запуска) в Windows Server 2003 и более поздние версии </para>
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
                      <para>К работе (автоматический режим)</para>
                    </TD>
                    <TD>
                      <para>К работе (автоматический режим)</para>
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
                      <para>К работе (автоматический режим)</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </listItem>
            <listItem>
              <para>Убедитесь, что размер диапазона динамических портов не ограничено. Ниже приведен синтаксис Windows Server 2008 и Windows Server 2008 R2 NETSH для перечисления диапазон портов RPC:</para>
              <code>&gt;netsh int ipv4 show dynamicport tcp
&gt;netsh int ipv4 show dynamicport udp
&gt;netsh int ipv6 show dynamicport tcp
&gt;netsh int ipv6 show dynamicport udp</code>
            </listItem>
            <listItem>
              <para>Убедитесь, что определения жестко заданный порт, определенные в статье базы Знаний 224196 попадает в диапазон динамических портов для контроллеров доменов ОС версии источника.</para>
              <para>Просмотрите <externalLink> <linkText>статье базы Знаний 224196</linkText> <linkUri> https://support.microsoft.com/kb/224196 </linkUri> </externalLink> и убедитесь, что жестко заданный порт попадает в диапазон временных портов для версии операционной системы исходного контроллера домена.</para>
            </listItem>
            <listItem>
              <para>Убедитесь, что существует в группе HKLM\Software\Microsoft\Rpc разделе ClientProtocols и содержит следующие значения по умолчанию 5:</para>
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
        <embeddedLabel>Пример неправильное имя IP-адрес, сопоставление вызывает ошибки RPC 1753 и-2146893022: указано неверное имя целевого участника</embeddedLabel>
      </para>
      <para>Домен contoso.com состоит из DC1 и DC2 с x.x.1.1 адресов IP и x.x.1.2. Узел «A» и «AAAA» записи для DC2 зарегистрированы правильно на всех DNS-серверов, настроенных для DC1. Кроме того в файл HOSTS на DC1 содержит сопоставление DC2s полное доменное имя узла с IP-адрес адрес x.x.1.2 запись. Позже соединяется DC2 изменения IP-адреса из X.X.1.2 X.X.1.3 и новый компьютер, входящий в домен с помощью x.x.1.2 адрес IP-адрес. Репликации AD инициируется попыток <ui>Реплицировать сейчас</ui> команда оснастки Active Directory — сайты и службы завершается с ошибкой 1753 г., как показано в трассировке ниже:</para>
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
      <para>В кадре <embeddedLabel>10</embeddedLabel>, контроллер домена назначения запрашивает конечных точек контроллеры домена источника через порт 135 для класса службы репликации Active Directory UUID E351... </para>
      <para>В кадре <embeddedLabel>11</embeddedLabel>, исходный контроллер домена, в этом случае компьютера-члена, который еще не размещена роль контроллера домена и поэтому не зарегистрирован E351... UUID для службы репликации с его локальной EPM отвечает символические ошибка EP_S_NOT_REGISTERED, которой сопоставляется десятичное ошибка 1753, hex ошибка 0x6d9 и сообщением об ошибке «имеются осталось доступных конечных точек».</para>
      <para>Более поздней версии с x.x.1.2 адрес IP-адрес компьютера-члена возвращает повышены до объектов реплики «MayberryDC» в домене contoso.com. Опять же <ui>Реплицировать сейчас</ui> команда используется для запуска репликации, но сейчас произойдет на экране ошибка «имя участника целевого неверный». Компьютер, сетевой адаптер назначается IP-адрес адрес x.x.1.2 <placeholder>является</placeholder> контроллером домена, в данный момент загружается в обычном режиме и зарегистрировал E351... Служба репликации UUID с его локальной EPM, но он не является владельцем имени или безопасности удостоверение DC2 и не может расшифровать запросе Kerberos от DC1, поэтому запрос теперь завершается ошибкой «имя участника целевого неверный». Ошибка сопоставляется десятичное ошибка-2146893022 / hex ошибка 0x80090322. </para>
      <para>Такие недопустимые сопоставления узла с IP-может быть вызвано устаревших записей в узле / файлы lmhost host A / AAAA регистрации в DNS или WINS. </para>
      <para>Сводка. В этом примере не удалось, так как контроллер домена назначения для разрешения «источник» контроллера домена, не было в доменных службах Active Directory, служба запущена (или даже установлены на то пошло) таким образом репликация вызвало Недопустимое сопоставление в-IP-адрес узла (в файле узла в данном случае) Имя участника-службы еще не зарегистрирован, и исходный контроллер домена вернул ошибку 1753 г. Во втором случае Недопустимое сопоставление в-IP-адрес узла (в файле узла) вызвала контроллер домена для подключения к контроллеру домена, которое зарегистрировано E351 назначения... репликация имени участника-службы, но этот источник имел другое удостоверение имени узла и безопасности чем предполагаемого исходного контроллера домена, неудачных попыток с ошибкой-2146893022: Указано неверное имя целевого участника.</para>
    </content>
  </section>
  <relatedTopics>
    <externalLink>
      <linkText>Устранение неполадок, связанных с операциями Active Directory, завершающимися с ошибкой 1753 г. Осталось доступных конечных точек. </linkText> 
      <linkUri> https://support.microsoft.com/kb/2089874 </linkUri> 
    </externalLink> 
<externalLink> <linkText>Статья 839880 ошибок Устранение неполадок конечных точек RPC, с помощью средств поддержки Windows Server 2003 с компакт-диска продукта</linkText> <linkUri> https://support.microsoft.com/kb/839880 </linkUri> </externalLink> 
<externalLink> <linkText>Статья 832017 службы Обзор и сетевых требованиях к портам для системы Windows Server</linkText> <linkUri> https://support.microsoft.com/kb/832017/ </linkUri> </externalLink> 
<externalLink> <linkText>Статья 224196 трафик репликации ограничение Active Directory и клиентского трафика RPC к конкретному порту</linkText> <linkUri> https://support.microsoft.com/kb/224196/ </linkUri> </externalLink> 
<externalLink> <linkText>Статье базы Знаний 154596 Настройка динамического выделения портов RPC для работы с брандмауэром</linkText> <linkUri> https://support.microsoft.com/kb/154596 </linkUri> </externalLink> <externalLink> <linkText>Принцип работы RPC</linkText><linkUri>https://msdn.microsoft.com/library/aa373935(VS.85).aspx</linkUri></externalLink><externalLink><linkText>как подготавливает сервер для подключения</linkText> <linkUri> https://msdn.microsoft.com/library/aa373938(VS.85).aspx </linkUri> </externalLink> 
<externalLink> <linkText>Как клиент устанавливает соединение</linkText> <linkUri> https://msdn.microsoft.com/library/aa373937(VS.85).aspx </linkUri> </externalLink> <externalLink> <linkText>Регистрации интерфейса</linkText><linkUri>https://msdn.microsoft.com/library/aa375357(VS.85).aspx</linkUri></externalLink><externalLink><linkText>делая его Доступен в сети</linkText><linkUri>https://msdn.microsoft.com/library/aa373974(VS.85).aspx</linkUri></externalLink><externalLink><linkText>регистрации конечных точек</linkText> <linkUri> https://msdn.microsoft.com/library/aa375255(VS.85).aspx </linkUri> </externalLink> <externalLink> <linkText>Прослушивание клиентских вызовов</linkText> <linkUri> https://msdn.microsoft.com/library/aa373966(VS.85).aspx </linkUri> </externalLink> <externalLink> <linkText>Как клиент устанавливает соединение</linkText><linkUri>https://msdn.microsoft.com/library/aa373937(VS.85).aspx</linkUri></externalLink><externalLink><linkText>ограничение Active Directory трафик репликации и клиент RPC трафика к определенному порту</linkText><linkUri>https://support.microsoft.com/kb/224196</linkUri></externalLink><externalLink><linkText>имени участника-службы для целевого контроллера домена в AD DS</linkText><linkUri>https://msdn.microsoft.com/library/dd207688(PROT.13).aspx</linkUri></externalLink></relatedTopics>
</developerConceptualDocument>


