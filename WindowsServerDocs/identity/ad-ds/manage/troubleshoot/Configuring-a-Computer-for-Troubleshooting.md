---
ms.assetid: 155abe09-6360-4913-8dd9-7392d71ea4e6
title: "Настройка компьютера для устранения неполадок"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 915b8d1133b3bee050f5eedce9e7ac445f833048
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="configuring-a-computer-for-troubleshooting"></a>Настройка компьютера для устранения неполадок

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012


<developerConceptualDocument xmlns="https://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="https://www.w3.org/1999/xlink" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="https://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Прежде чем использовать дополнительные действия по устранению неполадок для выявления и устранения неполадок Active Directory, следует настройте компьютеры для устранения неполадок. Следует также иметь базовое представление о <token>nextref_longhorincludes > диагностики концепции, процедуры и средства. </para>
    <para>Сведения о мониторинге средства для Windows Server 2008 см. в разделе Step-by-Step руководство по производительности и надежности мониторинга в Windows Server 2008 (<externalLink><linkText>https://go.microsoft.com/fwlink/?LinkId=123737</linkText><linkUri>https://go.microsoft.com/fwlink/?LinkId=123737</linkUri></externalLink>).</para>
  </introduction>
  <section>
    <title>Задачи настройки для устранения неполадок</title>
    <content>
      <para>настроить компьютер для устранения неполадок доменных служб Active Directory (AD DS), выполните следующие задачи:</para>
      <para>
        <link xlink:href="#BKMK_2">установить средства удаленного администрирования сервера для службы AD DS</link>
      </para>
      <para>
        <link xlink:href="#BKMK_3">монитор производительности и стабильности Настройка</link>
      </para>
      <para>
        <link xlink:href="#BKMK_4">задавать уровни ведения журнала</link>
      </para>
    </content>
    <sections>
      <section address="BKMK_2">
        <title>Установка средств удаленного администрирования сервера для службы AD DS</title>
        <content>
          <para>при установке AD DS, чтобы создать контроллер домена, автоматически устанавливаются средства администрирования, которые можно использовать для управления AD DS. Если вы хотите управлять контроллеры домена удаленно с компьютера, который не является контроллером домена, можно установить средства администрирования на рядовом сервере, на котором выполняется <token>nextref_longhorincludes > или на компьютере, работающем под управлением Windows Vista с пакетом обновления 1 (SP1). На рядовых серверах, работающих под управлением <token>nextref_longhorincludes >, используется компонент средств удаленного администрирования сервера (RSAT) в диспетчере сервера для установки средства доменных служб Active Directory. Средства удаленного администрирования сервера заменяет средств поддержки Windows в Windows Server 2003. Также можно установить средства доменных служб Active Directory на компьютере, работающем под управлением Windows Vista с пакетом обновления 1 (SP1), скачайте инструменты для этого компьютера. </para>
          <para>сведения об установке RSAT см. в разделе <link xlink:href="610ba7d9-51b5-4e14-9232-0510a9091aba">Установка сервера средств удаленного администрирования для служб AD DS</link>.</para>
        </content>
      </section>
      <section address="BKMK_3">
        <title>Настройка монитор надежности и производительности</title>
        <content>
          <para>Windows Server 2008 включает надежность Windows и системный монитор, который представляет оснастку Microsoft Management Console (MMC), который объединяет функции предыдущих отдельных средств, включая журналы производительности и оповещений, Server Performance Advisor и системного монитора. Эта оснастка предоставляет графический пользовательский интерфейс (GUI) для настройки группы сборщиков данных и сеансов отслеживания событий. </para>
          <para>монитор надежности и производительности также включает монитор надежности, оснастка MMC, отслеживает изменения в систему и сравнивает их с изменениями в стабильности системы, предоставляя графическое представление их связь. </para>
        </content>
      </section>
      <section address="BKMK_4">
        <title>Настройка уровней ведения журнала</title>
        <content>
          <para>Если сведения, полученные в журнал службы каталогов в средстве просмотра событий недостаточно для устранения неполадок, поднять уровень ведения журнала с помощью записи реестра в <embeddedLabel>HKEY_LOCAL_MACHINESYSTEMCurrentControlSetServicesNTDSDiagnostics</embeddedLabel>. </para>
          <para>по умолчанию присвоено уровни ведения журнала для всех записей <embeddedLabel>0</embeddedLabel>, который обеспечивает минимальный объем информации. Самый высокий уровень ведения журнала — <embeddedLabel>5</embeddedLabel>. Повышение уровня для записи в результате дополнительные события записываются в журнал событий службы каталогов. </para>
          <para>можно использовать следующую процедуру для изменения уровня ведения журнала для диагностики записи. </para>
          <alert class="caution">
            <para>мы рекомендуем, что вы не изменять реестр напрямую, если нет других возможностей. Изменения в реестре не проверяются редактором реестра или операционной системой Windows, после чего они применяются в результате могут сохраниться неверные значения. Это может приведет к неустранимым ошибкам в системе. По возможности используйте групповую политику или других средств Windows, такие как оснастки MMC, для выполнения задач, а не редактирования реестра напрямую. Если необходимо изменить реестр, соблюдайте крайнюю осторожность. </para>
          </alert>
          <para>
            <embeddedLabel>требования</embeddedLabel>
          </para>
          <list class="bullet">
            <listItem>
              <para>членство в группе <embeddedLabel>"Администраторы домена"</embeddedLabel>, или в эквивалентной минимальным требованием для выполнения этой процедуры. <token>review_detailincludes></para>
            </listItem>
            <listItem>
              <para>средства: Regedit.exe</para>
            </listItem>
          </list>
          <procedure>
            <title>изменить уровень ведения журнала для диагностики записи</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>нажмите кнопку <ui>запустить</ui>, нажмите кнопку <ui>запуска</ui>, тип <userInput>regedit</userInput>, и нажмите кнопку <ui>OK</ui>.</para>
                </content>
              </step>
              <step>
                <content>
                  <para>перейдите к записи, для которого требуется установить ведения журналов в <embeddedLabel>HKEY_LOCAL_MACHINESYSTEMCurrentControlSetServicesNTDSDiagnostics</embeddedLabel>.</para>
                </content>
              </step>
              <step>
                <content>
                  <para>дважды щелкните запись и в <embeddedLabel>базового</embeddedLabel>, нажмите кнопку <embeddedLabel>десятичных</embeddedLabel>.</para>
                </content>
              </step>
              <step>
                <content>
                  <para>в <embeddedLabel>значение</embeddedLabel>, введите целое число от <embeddedLabel>0</embeddedLabel> через <embeddedLabel>5</embeddedLabel>, а затем нажмите кнопку <ui>OK</ui>.</para>
                </content>
              </step>
            </steps>
          </procedure>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerConceptualDocument>


