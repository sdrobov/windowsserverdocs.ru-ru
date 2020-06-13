---
title: Команды Windows
description: Справочник
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c703d07c-8227-4e86-94a6-8ef390f94cdc
author: jasongerend
ms.author: jgerend
manager: dongill
ms.date: 06/09/2020
ms.prod: windows-server
ms.openlocfilehash: 66de80652f764840af70e88dfd39df2398ae495c
ms.sourcegitcommit: 99d548141428c964facf666c10b6709d80fbb215
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2020
ms.locfileid: "84721120"
---
# <a name="windows-commands"></a>Команды Windows

Все поддерживаемые версии Windows (сервер и клиент) имеют набор встроенных команд консоли Win32.

Этот набор документации описывает команды Windows, которые можно использовать для автоматизации задач с помощью скриптов или средств создания скриптов.

Чтобы найти сведения о конкретной команде, в следующем меню A-Z щелкните букву, с которой начинается команда, а затем щелкните имя команды.

[Объект](#a)  |
 [Б](#b)  |
 [C](#c)  |
 [Г](#d)  |
 [Д](#e)  |
 [F](#f)  |
 [Ж](#g)  |
 [З](#h)  |
 [Я](#i)  |
 [J](#j)  |
 [Л](#k)  |
 [L](#l)  |
 [М](#m)  |
 [N](#n)  |
 [O](#o)  |
 [P](#p)  |
 [Вопросы и ответы](#q)  |
 Язык [R](#r)  |
 [С](#s)  |
 [T](#t)  |
 [U](#u)  |
 [Версия](#v)  |
 [Н](#w)  |
 [X](#x) | Y | Гармошкой

## <a name="prerequisites"></a>Предварительные требования

Сведения, содержащиеся в этом разделе, применимы к:

- Windows Server 2019
- Windows Server (Semi-Annual Channel)
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2
- Windows Server 2008
- Windows 10
- Windows 8.1

### <a name="command-shell-overview"></a>Общие сведения о командной оболочке

Командная оболочка была первой оболочкой, встроенной в Windows, для автоматизации стандартных задач, таких как управление учетными записями пользователей или ночное резервное копирование с пакетными файлами (bat). С помощью сервера сценариев Windows можно выполнять более сложные сценарии в командной оболочке. Дополнительные сведения см. в разделе [cscript](cscript.md) или [Wscript](wscript.md). С помощью скриптов можно более эффективно выполнять операции, чем с помощью пользовательского интерфейса. Скрипты принимают все команды, доступные в командной строке.

Windows имеет две командные оболочки: Командная оболочка и [PowerShell](https://docs.microsoft.com/powershell/scripting/powershell-scripting?view=powershell-6). Каждая оболочка представляет собой программную программу, обеспечивающую прямой обмен данными между вами и операционной системой или приложением, предоставляя среду для автоматизации ИТ-операций.

PowerShell был разработан для расширения возможностей командной оболочки для выполнения команд PowerShell, называемых командлетами. Командлеты похожи на команды Windows, но предоставляют более расширяемый язык сценариев. Вы можете выполнять команды Windows и командлеты PowerShell в PowerShell, но Командная оболочка может выполнять только команды Windows, а не командлеты PowerShell.

Для наиболее надежной и последней версии службы автоматизации Windows рекомендуется использовать PowerShell вместо команд Windows или сервера сценариев Windows для службы автоматизации Windows.

> [!NOTE]
>Вы также можете скачать и установить [PowerShell Core](https://docs.microsoft.com/powershell/scripting/whats-new/what-s-new-in-powershell-core-60?view=powershell-6), версию PowerShell с открытым исходным кодом.

> [!CAUTION]
> Неправильное изменение реестра может серьезно повредить систему. Перед внесением следующих изменений в реестр следует создать резервную копию всех ценных данных на компьютере.

> [!NOTE]
> Чтобы включить или отключить завершение имен файлов и каталогов в командной оболочке на компьютере или в сеансе входа пользователя, запустите **regedit.exe** и задайте следующее **значение reg_DWOrd**:
>
> HKEY_LOCAL_MACHINE \Софтваре\микрософт\комманд Процессор\комплетиончар\ reg_DWOrd
>
> Чтобы задать значение **reg_DWOrd** , используйте шестнадцатеричное значение управляющего символа для конкретной функции (например, **0 9** — TAB, а **0 08** — Backspace). Заданные пользователем параметры имеют приоритет над параметрами компьютера, а параметры командной строки имеют приоритет над параметрами реестра.

## <a name="command-line-reference-a-z"></a>Справочник по командной строке A-Z

Чтобы найти сведения об определенной команде Windows, в следующем меню A-Z щелкните букву, с которой начинается команда, а затем щелкните имя команды.

[Объект](#a)  |
 [Б](#b)  |
 [C](#c)  |
 [Г](#d)  |
 [Д](#e)  |
 [F](#f)  |
 [Ж](#g)  |
 [З](#h)  |
 [Я](#i)  |
 [J](#j)  |
 [Л](#k)  |
 [L](#l)  |
 [М](#m)  |
 [N](#n)  |
 [O](#o)  |
 [P](#p)  |
 [Вопросы и ответы](#q)  |
 Язык [R](#r)  |
 [С](#s)  |
 [T](#t)  |
 [U](#u)  |
 [Версия](#v)  |
 [Н](#w)  |
 [X](#x) | Y | Гармошкой

### <a name="a"></a>Объект

- [active](active.md)
- [add](add.md)
- [add alias](add-alias.md)
- [add volume](add-volume.md)
- [append](append.md)
- [arp](arp.md)
- [assign](assign.md)
- [assoc](assoc.md)
- [at](at.md)
- [atmadm](atmadm.md)
- [attach-vdisk](attach-vdisk.md)
- [attrib](attrib.md)
- [attributes](attributes.md)
  - [attributes disk](attributes-disk.md)
  - [attributes volume](attributes-volume.md)
- [auditpol](auditpol.md)
  - [auditpol backup](auditpol-backup.md)
  - [auditpol clear](auditpol-clear.md)
  - [auditpol get](auditpol-get.md)
  - [auditpol list](auditpol-list.md)
  - [auditpol remove](auditpol-remove.md)
  - [auditpol resourcesacl](auditpol-resourcesacl.md)
  - [auditpol restore](auditpol-restore.md)
  - [auditpol set](auditpol-set.md)
- [autochk](autochk.md)
- [autoconv](autoconv.md)
- [autofmt](autofmt.md)
- [automount](automount.md)

### <a name="b"></a>B

- [bcdboot](bcdboot.md)
- [bcdedit](bcdedit.md)
- [bdehdcfg](bdehdcfg.md)
  - [bdehdcfg driveinfo](bdehdcfg-driveinfo.md)
  - [bdehdcfg newdriveletter](bdehdcfg-newdriveletter.md)
  - [bdehdcfg quiet](bdehdcfg-quiet.md)
  - [bdehdcfg restart](bdehdcfg-restart.md)
  - [bdehdcfg size](bdehdcfg-size.md)
  - [bdehdcfg target](bdehdcfg-target.md)
- [begin backup](begin-backup.md)
- [begin restore](begin-restore.md)
- [bitsadmin](bitsadmin.md)
  - [bitsadmin addfile](bitsadmin-addfile.md)
  - [bitsadmin addfileset](bitsadmin-addfileset.md)
  - [bitsadmin addfilewithranges](bitsadmin-addfilewithranges.md)
  - [bitsadmin cache](bitsadmin-cache.md)
    - [bitsadmin cache и delete](bitsadmin-cache-and-delete.md)
    - [bitsadmin cache и deleteurl](bitsadmin-cache-and-deleteurl.md)
    - [bitsadmin cache и getexpirationtime](bitsadmin-cache-and-getexpirationtime.md)
    - [bitsadmin cache и getlimit](bitsadmin-cache-and-getlimit.md)
    - [bitsadmin cache и help](bitsadmin-cache-and-help.md)
    - [bitsadmin cache и info](bitsadmin-cache-and-info.md)
    - [bitsadmin cache и list](bitsadmin-cache-and-list.md)
    - [bitsadmin cache и setexpirationtime](bitsadmin-cache-and-setexpirationtime.md)
    - [bitsadmin cache и setlimit](bitsadmin-cache-and-setlimit.md)
    - [bitsadmin cache и clear](bitsadmin-cache-clear.md)
  - [bitsadmin cancel](bitsadmin-cancel.md)
  - [bitsadmin complete](bitsadmin-complete.md)
  - [bitsadmin create](bitsadmin-create.md)
  - [bitsadmin examples](bitsadmin-examples.md)
  - [bitsadmin getaclflags](bitsadmin-getaclflags.md)
  - [bitsadmin getbytestotal](bitsadmin-getbytestotal.md)
  - [bitsadmin getbytestransferred](bitsadmin-getbytestransferred.md)
  - [bitsadmin getclientcertificate](bitsadmin-getclientcertificate.md)
  - [bitsadmin getcompletiontime](bitsadmin-getcompletiontime.md)
  - [bitsadmin getcreationtime](bitsadmin-getcreationtime.md)
  - [bitsadmin getcustomheaders](bitsadmin-getcustomheaders.md)
  - [bitsadmin getdescription](bitsadmin-getdescription.md)
  - [bitsadmin getdisplayname](bitsadmin-getdisplayname.md)
  - [bitsadmin geterror](bitsadmin-geterror.md)
  - [bitsadmin geterrorcount](bitsadmin-geterrorcount.md)
  - [bitsadmin getfilestotal](bitsadmin-getfilestotal.md)
  - [bitsadmin getfilestransferred](bitsadmin-getfilestransferred.md)
  - [bitsadmin gethelpertokenflags](bitsadmin-gethelpertokenflags.md)
  - [bitsadmin gethelpertokensid](bitsadmin-gethelpertokensid.md)
  - [bitsadmin gethttpmethod](bitsadmin-gethttpmethod.md)
  - [bitsadmin getmaxdownloadtime](bitsadmin-getmaxdownloadtime.md)
  - [bitsadmin getminretrydelay](bitsadmin-getminretrydelay.md)
  - [bitsadmin getmodificationtime](bitsadmin-getmodificationtime.md)
  - [bitsadmin getnoprogresstimeout](bitsadmin-getnoprogresstimeout.md)
  - [bitsadmin getnotifycmdline](bitsadmin-getnotifycmdline.md)
  - [bitsadmin getnotifyflags](bitsadmin-getnotifyflags.md)
  - [bitsadmin getnotifyinterface](bitsadmin-getnotifyinterface.md)
  - [bitsadmin getowner](bitsadmin-getowner.md)
  - [bitsadmin getpeercachingflags](bitsadmin-getpeercachingflags.md)
  - [bitsadmin getpriority](bitsadmin-getpriority.md)
  - [bitsadmin getproxybypasslist](bitsadmin-getproxybypasslist.md)
  - [bitsadmin getproxylist](bitsadmin-getproxylist.md)
  - [bitsadmin getproxyusage](bitsadmin-getproxyusage.md)
  - [bitsadmin getreplydata](bitsadmin-getreplydata.md)
  - [bitsadmin getreplyfilename](bitsadmin-getreplyfilename.md)
  - [bitsadmin getreplyprogress](bitsadmin-getreplyprogress.md)
  - [bitsadmin getsecurityflags](bitsadmin-getsecurityflags.md)
  - [bitsadmin getstate](bitsadmin-getstate.md)
  - [bitsadmin gettemporaryname](bitsadmin-gettemporaryname.md)
  - [bitsadmin gettype](bitsadmin-gettype.md)
  - [bitsadmin getvalidationstate](bitsadmin-getvalidationstate.md)
  - [bitsadmin help](bitsadmin-help.md)
  - [bitsadmin info](bitsadmin-info.md)
  - [bitsadmin list](bitsadmin-list.md)
  - [bitsadmin listfiles](bitsadmin-listfiles.md)
  - [bitsadmin makecustomheaderswriteonly](bitsadmin-makecustomheaderswriteonly.md)
  - [bitsadmin monitor](bitsadmin-monitor.md)
  - [bitsadmin nowrap](bitsadmin-nowrap.md)
  - [bitsadmin peercaching](bitsadmin-peercaching.md)
    - [bitsadmin peercaching и getconfigurationflags](bitsadmin-peercaching-and-getconfigurationflags.md)
    - [bitsadmin peercaching и help](bitsadmin-peercaching-and-help.md)
    - [bitsadmin peercaching и getconfigurationflags](bitsadmin-peercaching-and-setconfigurationflags.md)
  - [bitsadmin peers](bitsadmin-peers.md)
    - [bitsadmin peers и clear](bitsadmin-peers-and-clear.md)
    - [bitsadmin peers и discover](bitsadmin-peers-and-discover.md)
    - [bitsadmin peers и help](bitsadmin-peers-and-help.md)
    - [bitsadmin peers и list](bitsadmin-peers-and-list.md)
  - [bitsadmin rawreturn](bitsadmin-rawreturn.md)
  - [bitsadmin removeclientcertificate](bitsadmin-removeclientcertificate.md)
  - [bitsadmin removecredentials](bitsadmin-removecredentials.md)
  - [bitsadmin replaceremoteprefix](bitsadmin-replaceremoteprefix.md)
  - [bitsadmin reset](bitsadmin-reset.md)
  - [bitsadmin resume](bitsadmin-resume.md)
  - [bitsadmin setaclflag](bitsadmin-setaclflag.md)
  - [bitsadmin setclientcertificatebyid](bitsadmin-setclientcertificatebyid.md)
  - [bitsadmin setclientcertificatebyname](bitsadmin-setclientcertificatebyname.md)
  - [bitsadmin setcredentials](bitsadmin-setcredentials.md)
  - [bitsadmin setcustomheaders](bitsadmin-setcustomheaders.md)
  - [bitsadmin setdescription](bitsadmin-setdescription.md)
  - [bitsadmin setdisplayname](bitsadmin-setdisplayname.md)
  - [bitsadmin sethelpertoken](bitsadmin-sethelpertoken.md)
  - [bitsadmin sethelpertokenflags](bitsadmin-sethelpertokenflags.md)
  - [bitsadmin sethttpmethod](bitsadmin-sethttpmethod.md)
  - [bitsadmin setmaxdownloadtime](bitsadmin-setmaxdownloadtime.md)
  - [bitsadmin setminretrydelay](bitsadmin-setminretrydelay.md)
  - [bitsadmin setnoprogresstimeout](bitsadmin-setnoprogresstimeout.md)
  - [bitsadmin setnotifycmdline](bitsadmin-setnotifycmdline.md)
  - [bitsadmin setnotifyflags](bitsadmin-setnotifyflags.md)
  - [bitsadmin setpeercachingflags](bitsadmin-setpeercachingflags.md)
  - [bitsadmin setpriority](bitsadmin-setpriority.md)
  - [bitsadmin setproxysettings](bitsadmin-setproxysettings.md)
  - [bitsadmin setreplyfilename](bitsadmin-setreplyfilename.md)
  - [bitsadmin setsecurityflags](bitsadmin-setsecurityflags.md)
  - [bitsadmin setvalidationstate](bitsadmin-setvalidationstate.md)
  - [bitsadmin suspend](bitsadmin-suspend.md)
  - [bitsadmin takeownership](bitsadmin-takeownership.md)
  - [bitsadmin transfer](bitsadmin-transfer.md)
  - [bitsadmin util](bitsadmin-util.md)
    - [bitsadmin util и enableanalyticchannel](bitsadmin-util-and-enableanalyticchannel.md)
    - [bitsadmin util и getieproxy](bitsadmin-util-and-getieproxy.md)
    - [bitsadmin util и help](bitsadmin-util-and-help.md)
    - [bitsadmin util и repairservice](bitsadmin-util-and-repairservice.md)
    - [bitsadmin util и setieproxy](bitsadmin-util-and-setieproxy.md)
    - [bitsadmin util и version](bitsadmin-util-and-version.md)
  - [bitsadmin wrap](bitsadmin-wrap.md)
- [bootcfg](bootcfg.md)
  - [bootcfg addsw](bootcfg-addsw.md)
  - [bootcfg copy](bootcfg-copy.md)
  - [bootcfg dbg1394](bootcfg-dbg1394.md)
  - [bootcfg debug](bootcfg-debug.md)
  - [bootcfg default](bootcfg-default.md)
  - [bootcfg delete](bootcfg-delete.md)
  - [bootcfg ems](bootcfg-ems.md)
  - [bootcfg query](bootcfg-query.md)
  - [bootcfg raw](bootcfg-raw.md)
  - [bootcfg rmsw](bootcfg-rmsw.md)
  - [bootcfg timeout](bootcfg-timeout.md)
- [break](break_1.md)

### <a name="c"></a>C

- [cacls](cacls.md)
- [call](call.md)
- [cd](cd.md)
- [certreq](certreq_1.md)
- [certutil](certutil.md)
- [change](change.md)
  - [change logon](change-logon.md)
  - [change port](change-port.md)
  - [change user](change-user.md)
- [chcp](chcp.md)
- [chdir](chdir.md)
- [chglogon](chglogon.md)
- [chgport](chgport.md)
- [chgusr](chgusr.md)
- [chkdsk](chkdsk.md)
- [chkntfs](chkntfs.md)
- [choice](choice.md)
- [cipher](cipher.md)
- [clean](clean.md)
- [cleanmgr](cleanmgr.md)
- [clip](clip.md)
- [cls](cls.md)
- [cmd](Cmd.md)
- [cmdkey](cmdkey.md)
- [cmstp](cmstp.md)
- [color](color.md)
- [comp](comp.md)
- [compact](compact.md)
- [Compact VDISK](compact-vdisk.md)
- [convert](convert.md)
  - [convert basic](convert-basic.md)
  - [преобразовать динамический](convert-dynamic.md)
  - [convert gpt](convert-gpt.md)
  - [convert mbr](convert-mbr.md)
- [copy](copy.md)
- [cprofile](cprofile.md)
- [создание](create.md)
  - [создать секцию EFI](create-partition-efi.md)
  - [создать [секцию расширена](create-partition-extended.md)
  - [создать логический раздел](create-partition-logical.md)
  - [создать секцию MSR](create-partition-msr.md)
  - [создать секцию PRIMARY](create-partition-primary.md)
  - [создать зеркало тома](create-volume-mirror.md)
  - [Создание тома RAID](create-volume-raid.md)
  - [создать простой том](create-volume-simple.md)
  - [Создание чередования томов](create-volume-stripe.md)
- [cscript](cscript.md)

### <a name="d"></a>D

- [date](date.md)
- [dcgpofix](dcgpofix.md)
- [defrag](defrag.md)
- [del](del.md)
- [delete](delete.md)
  - [удалить диск](delete-disk.md)
  - [удалить секцию](delete-partition.md)
  - [удалить тени](delete-shadows.md)
  - [delete volume](delete-volume.md)
- [отсоединить виртуальный диск](detach-vdisk.md)
- [налог](detail.md)
  - [диск сведений](detail-disk.md)
  - [подробное секционирование](detail-partition.md)
  - [подробные сведения VDISK](detail-vdisk.md)
  - [подробный том](detail-volume.md)
- [дфсдиаг](dfsdiag.md)
  - [дфсдиаг тестдкс](dfsdiag-testdcs.md)
  - [дфсдиаг тестдфсконфиг](dfsdiag-testdfsconfig.md)
  - [дфсдиаг тестдфсинтегрити](dfsdiag-testdfsintegrity.md)
  - [дфсдиаг тестреферрал](dfsdiag-testreferral.md)
  - [дфсдиаг тестситес](dfsdiag-testsites.md)
- [dfsrmig](dfsrmig.md)
- [diantz](diantz.md)
- [dir](dir.md)
- [diskcomp](diskcomp.md)
- [diskcopy](diskcopy.md)
- [diskpart](diskpart.md)
- [diskperf](diskperf.md)
- [diskraid](diskraid.md)
- [diskshadow](diskshadow.md)
- [dispdiag](dispdiag.md)
- [dnscmd](dnscmd.md)
- [doskey](doskey.md)
- [driverquery](driverquery.md)

### <a name="e"></a>E

- [echo](echo.md)
- [edit](edit.md)
- [endlocal](endlocal.md)
- [завершить восстановление](end-restore.md)
- [erase](erase.md)
- [eventcreate](eventcreate.md)
- [eventquery](eventquery.md)
- [eventtriggers](eventtriggers.md)
- [Evntcmd](evntcmd.md)
- [Exec](exec.md)
- [exit](exit_2.md)
- [expand](expand.md)
- [развернуть виртуальный диск](expand-vdisk.md)
- [представлены](expose.md)
- [расширений](extend.md)
- [extract](extract.md)

### <a name="f"></a>C

- [fc](fc.md)
- [filesystems](filesystems.md)
- [find](find.md)
- [findstr](findstr.md)
- [finger](finger.md)
- [flattemp](flattemp.md)
- [fondue](fondue.md)
- [for](for.md)
- [forfiles](forfiles.md)
- [format](format.md)
- [freedisk](freedisk.md)
- [fsutil](fsutil.md)
  - [fsutil 8dot3name](fsutil-8dot3name.md)
  - [fsutil behavior](fsutil-behavior.md)
  - [fsutil dirty](fsutil-dirty.md)
  - [fsutil file](fsutil-file.md)
  - [fsutil fsinfo](fsutil-fsinfo.md)
  - [fsutil hardlink](fsutil-hardlink.md)
  - [fsutil objectid](fsutil-objectid.md)
  - [fsutil quota](fsutil-quota.md)
  - [fsutil repair](fsutil-repair.md)
  - [fsutil reparsepoint](fsutil-reparsepoint.md)
  - [fsutil resource](fsutil-resource.md)
  - [fsutil sparse](fsutil-sparse.md)
  - [fsutil tiering](fsutil-tiering.md)
  - [fsutil transaction](fsutil-transaction.md)
  - [fsutil usn](fsutil-usn.md)
  - [fsutil volume](fsutil-volume.md)
  - [fsutil wim](fsutil-wim.md)
- [ftp](ftp.md)
  - [ftp append](ftp-append.md)
  - [ftp ascii](ftp-ascii.md)
  - [ftp bell](ftp-bell_1.md)
  - [ftp binary](ftp-binary.md)
  - [ftp bye](ftp-bye.md)
  - [ftp cd](ftp-cd.md)
  - [ftp close](ftp-close_1.md)
  - [ftp debug](ftp-debug.md)
  - [ftp delete](ftp-delete.md)
  - [ftp dir](ftp-dir.md)
  - [ftp disconnect](ftp-disconnect_1.md)
  - [ftp get](ftp-get.md)
  - [ftp glob](ftp-glob_1.md)
  - [ftp hash](ftp-hash_1.md)
  - [ftp lcd](ftp-lcd.md)
  - [ftp literal](ftp-literal_1.md)
  - [ftp ls](ftp-ls_1.md)
  - [ftp mget](ftp-mget.md)
  - [ftp mkdir](ftp-mkdir.md)
  - [ftp mls](ftp-mls_1.md)
  - [ftp mput](ftp-mput_1.md)
  - [ftp open](ftp-open_1.md)
  - [ftp prompt](ftp-prompt_1.md)
  - [ftp put](ftp-put.md)
  - [ftp pwd](ftp-pwd_1.md)
  - [ftp quit](ftp-quit.md)
  - [ftp quote](ftp-quote.md)
  - [ftp recv](ftp-recv.md)
  - [ftp remotehelp](ftp-remotehelp_1.md)
  - [ftp rename](ftp-rename.md)
  - [ftp rmdir](ftp-rmdir.md)
  - [ftp send](ftp-send_1.md)
  - [ftp status](ftp-status.md)
  - [ftp trace](ftp-trace_1.md)
  - [ftp type](ftp-type.md)
  - [ftp user](ftp-user.md)
  - [ftp verbose](ftp-verbose_1.md)
  - [ftp mdelete](ftp-.mdelete_1.md)
  - [ftp mdir](ftp.mdir.md)
- [ftype](ftype.md)
- [fveupdate](fveupdate.md)

### <a name="g"></a>G.

- [getmac](getmac.md)
- [gettype](gettype.md)
- [goto](goto.md)
- [gpfixup](gpfixup.md)
- [gpresult](gpresult.md)
- [gpt](gpt.md)
- [gpupdate](gpupdate.md)
- [graftabl](graftabl.md)

### <a name="h"></a>H

- [help](help.md)
- [helpctr](helpctr.md)
- [hostname](hostname.md)

### <a name="i"></a>I

- [icacls](icacls.md)
- [if](if.md)
- [Импорт (шадовдиск)](import.md)
- [Импорт (DiskPart)](import_1.md)
- [inactive](inactive.md)
- [inuse](inuse.md)
- [ipconfig](ipconfig.md)
- [ipxroute](ipxroute.md)
- [irftp](irftp.md)

### <a name="j"></a>J

- [jetpack](jetpack.md)

### <a name="k"></a>K

- [klist](klist.md)
- [ksetup](ksetup.md)
  - [ksetup addenctypeattr](ksetup-addenctypeattr.md)
  - [ksetup addhosttorealmmap](ksetup-addhosttorealmmap.md)
  - [ksetup addkdc](ksetup-addkdc.md)
  - [ksetup addkpasswd](ksetup-addkpasswd.md)
  - [ksetup addrealmflags](ksetup-addrealmflags.md)
  - [ksetup changepassword](ksetup-changepassword.md)
  - [ksetup delenctypeattr](ksetup-delenctypeattr.md)
  - [ksetup delhosttorealmmap](ksetup-delhosttorealmmap.md)
  - [ksetup delkdc](ksetup-delkdc.md)
  - [ksetup delkpasswd](ksetup-delkpasswd.md)
  - [ksetup delrealmflags](ksetup-delrealmflags.md)
  - [ksetup domain](ksetup-domain.md)
  - [ksetup dumpstate](ksetup-dumpstate.md)
  - [ksetup getenctypeattr](ksetup-getenctypeattr.md)
  - [ksetup listrealmflags](ksetup-listrealmflags.md)
  - [ksetup mapuser](ksetup-mapuser.md)
  - [ksetup removerealm](ksetup-removerealm.md)
  - [ksetup server](ksetup-server.md)
  - [ksetup setcomputerpassword](ksetup-setcomputerpassword.md)
  - [ksetup setenctypeattr](ksetup-setenctypeattr.md)
  - [ksetup setrealm](ksetup-setrealm.md)
  - [ksetup setrealmflags](ksetup-setrealmflags.md)
- [ktmutil](ktmutil.md)
- [ktpass](ktpass.md)

### <a name="l"></a>L

- [label](label.md)
- [list](list.md)
  - [список поставщиков](list-providers.md)
  - [перечислить тени](list-shadows.md)
  - [модули записи списка](list-writers.md)
- [загрузить метаданные](load-metadata.md)
- [lodctr](lodctr.md)
- [logman](logman.md)
  - [logman create](logman-create.md)
  - [создать оповещение Logman](logman-create-alert.md)
  - [Создание API Logman](logman-create-api.md)
  - [Logman Create cfg](logman-create-cfg.md)
  - [переlogman создать счетчик](logman-create-counter.md)
  - [создать трассировку Logman](logman-create-trace.md)
  - [logman delete](logman-delete.md)
  - [Программа Logman Import и Logman Export](logman-import-export.md)
  - [logman query](logman-query.md)
  - [останавливаются запуск и Logman](logman-start-stop.md)
  - [logman update](logman-update.md)
  - [оповещение об обновлении Logman](logman-update-alert.md)
  - [API обновления Logman](logman-update-api.md)
  - [Logman Update cfg](logman-update-cfg.md)
  - [Счетчик обновлений Logman](logman-update-counter.md)
  - [Трассировка обновления Logman](logman-update-trace.md)
- [logoff](logoff.md)
- [lpq](lpq.md)
- [lpr](lpr.md)

### <a name="m"></a>M

- [macfile](macfile.md)
- [makecab](makecab.md)
- [Управление BDE](manage-bde.md)
  - [Управление состоянием BDE](manage-bde-status.md)
  - [Управление BDE на](manage-bde-on.md)
  - [Управление BDE отключено](manage-bde-off.md)
  - [управление приостановкой BDE](manage-bde-pause.md)
  - [Управление возобновлением BDE](manage-bde-resume.md)
  - [Управление блокировкой BDE](manage-bde-lock.md)
  - [Управление разблокированием BDE](manage-bde-unlock.md)
  - [Управление разблокированием BDE](manage-bde-autounlock.md)
  - [Управление предохранителями BDE](manage-bde-protectors.md)
  - [Управление TPM BDE](manage-bde-tpm.md)
  - [Управление BDE сетидентифиер](manage-bde-setidentifier.md)
  - [Управление BDE форцерековери](manage-bde-forcerecovery.md)
  - [Управление BDE ChangePassword](manage-bde-changepassword.md)
  - [Управление BDE чанжепин](manage-bde-changepin.md)
  - [Управление BDE чанжекэй](manage-bde-changekey.md)
  - [Управление BDE кэйпаккаже](manage-bde-keypackage.md)
  - [Управление обновлением BDE](manage-bde-upgrade.md)
  - [Управление BDE випефриспаце](manage-bde-wipefreespace.md)
- [mapadmin](mapadmin.md)
- [md](md.md)
- [Слияние VDISK](merge-vdisk.md)
- [mkdir](mkdir.md)
- [mklink](mklink.md)
- [mmc](mmc.md)
- [mode](mode.md)
- [more](more.md)
- [mount](mount.md)
- [mountvol](mountvol.md)
- [move](move.md)
- [mqbkup](mqbkup.md)
- [mqsvc](mqsvc.md)
- [mqtgsvc](mqtgsvc.md)
- [msdt](msdt.md)
- [msg](msg.md)
- [msiexec](msiexec.md)
- [msinfo32](msinfo32.md)
- [mstsc](mstsc.md)

### <a name="n"></a>Нет

- [nbtstat](nbtstat.md)
- [netcfg](netcfg.md)
- [NET Print](net-print.md)
- [netsh](netsh.md)
- [netstat](netstat.md)
- [nfsadmin](nfsadmin.md)
- [nfsshare](nfsshare.md)
- [nfsstat](nfsstat.md)
- [nlbmgr](nlbmgr.md)
- [nslookup](nslookup.md)
  - [nslookup exit Command](nslookup-exit-command.md)
  - [nslookup finger Command](nslookup-finger-command.md)
  - [nslookup help](nslookup-help.md)
  - [nslookup ls](nslookup-ls.md)
  - [nslookup lserver](nslookup-lserver.md)
  - [nslookup root](nslookup-root.md)
  - [nslookup server](nslookup-server.md)
  - [nslookup set](nslookup-set.md)
  - [nslookup set all](nslookup-set-all.md)
  - [nslookup set class](nslookup-set-class.md)
  - [nslookup set d2](nslookup-set-d2.md)
  - [nslookup set debug](nslookup-set-debug.md)
  - [nslookup set domain](nslookup-set-domain.md)
  - [nslookup set port](nslookup-set-port.md)
  - [nslookup set querytype](nslookup-set-querytype.md)
  - [nslookup set recurse](nslookup-set-recurse.md)
  - [nslookup set retry](nslookup-set-retry.md)
  - [nslookup set root](nslookup-set-root.md)
  - [nslookup set search](nslookup-set-search.md)
  - [nslookup set srchlist](nslookup-set-srchlist.md)
  - [nslookup set timeout](nslookup-set-timeout.md)
  - [nslookup set type](nslookup-set-type.md)
  - [nslookup set vc](nslookup-set-vc.md)
  - [nslookup view](nslookup-view.md)
- [ntbackup](ntbackup.md)
- [ntcmdprompt](ntcmdprompt.md)
- [ntfrsutl](ntfrsutl.md)

### <a name="o"></a>O

- [работа](offline.md)
  - [автономный диск](offline-disk.md)
  - [автономный том](offline-volume.md)
- [Онлайн](online.md)
  - [оперативный диск](online-disk.md)
  - [оперативный том](online-volume.md)
- [openfiles](openfiles.md)

### <a name="p"></a>P

- [pagefileconfig](pagefileconfig.md)
- [path](path.md)
- [pathping](pathping.md)
- [pause](pause.md)
- [pbadmin](pbadmin.md)
- [pentnt](pentnt.md)
- [perfmon](perfmon.md)
- [ping](ping.md)
- [pnpunattend](pnpunattend.md)
- [pnputil](pnputil.md)
- [popd](popd.md)
- [оболочк](powershell.md)
- [Интегрированная среда сценариев PowerShell](powershell_ise.md)
- [print](print.md)
- [prncnfg](prncnfg.md)
- [prndrvr](prndrvr.md)
- [prnjobs](prnjobs.md)
- [prnmngr](prnmngr.md)
- [prnport](prnport.md)
- [prnqctl](prnqctl.md)
- [prompt](prompt.md)
- [pubprn](pubprn.md)
- [pushd](pushd.md)
- [pushprinterconnections](pushprinterconnections.md)
- [пвлаунчер](pwlauncher.md)

### <a name="q"></a>Q

- [qappsrv](qappsrv.md)
- [qprocess](qprocess.md)
- [запрос](query.md)
  - [обработка запросов](query-process.md)
  - [сеанс запроса](query-session.md)
  - [термсервер запросов](query-termserver.md)
  - [запрос пользователя](query-user.md)
- [quser](quser.md)
- [qwinsta](qwinsta.md)

### <a name="r"></a>R

- [rcp](rcp.md)
- [rd](rd.md)
- [rdpsign](rdpsign.md)
- [recover](recover.md)
- [восстановить группу дисков](recover_1.md)
- [reg](reg.md)
  - [Добавление reg](reg-add.md)
  - [reg compare](reg-compare.md)
  - [копирование reg](reg-copy.md)
  - [удалить reg](reg-delete.md)
  - [reg export](reg-export.md)
  - [импорт реестра](reg-import.md)
  - [Загрузить reg](reg-load.md)
  - [запрос reg](reg-query.md)
  - [Восстановление реестра](reg-restore.md)
  - [сохранить reg](reg-save.md)
  - [reg unload](reg-unload.md)
- [regini](regini.md)
- [regsvr32](regsvr32.md)
- [relog](relog.md)
- [REM Пакетный файл](rem.md)
- [Скрипт REM](rem_1.md)
- [remove](remove.md)
- [ren](ren.md)
- [rename](rename.md)
- [восстановление.](repair.md)
  - [Восстановление BDE](repair-bde.md)
- [replace](replace.md)
- [Повторное сканирование](rescan.md)
- [reset](reset.md);
  - [reset session](reset-session.md)
- [удержание](retain.md)
- [Верните](revert.md)
- [rexec](rexec.md)
- [risetup](risetup.md)
- [rmdir](rmdir.md)
- [robocopy](robocopy.md)
- [маршрут WS2008](route_ws2008.md)
- [rpcinfo](rpcinfo.md)
- [rpcping](rpcping.md)
- [rsh](rsh.md)
- [rundll32](rundll32.md)
- [rundll32 PRINTUI](rundll32-printui.md)
- [rwinsta](rwinsta.md)

### <a name="s"></a>S

- [San](san.md)
- [Настройка SC](sc-config.md)
- [SC CREATE](sc-create.md)
- [SC Delete](sc-delete.md)
- [запрос SC](sc-query.md)
- [schtasks](schtasks.md)
- [команду scwcmd](scwcmd.md)
  - [анализ команду scwcmd](scwcmd-analyze.md)
  - [Настройка команду scwcmd](scwcmd-configure.md)
  - [команду scwcmd регистр](scwcmd-register.md)
  - [откат команду scwcmd](scwcmd-rollback.md)
  - [Преобразование команду scwcmd](scwcmd-transform.md)
  - [команду scwcmd, представление](scwcmd-view.md)
- [secedit](secedit.md)
  - [Secedit Analyze](secedit-analyze.md)
  - [Настройка Secedit](secedit-configure.md)
  - [экспорт Secedit](secedit-export.md)
  - [Secedit женератероллбакк](secedit-generaterollback.md)
  - [Импорт Secedit](secedit-import.md)
  - [Secedit проверить](secedit-validate.md)
- [select](select.md)
  - [select disk](select-disk.md)
  - [выбор Секции](select-partition.md)
  - [выбрать виртуальный диск](select-vdisk.md)
  - [select volume](select-volume.md)
- [serverceipoptin](serverceipoptin.md)
- [программу](servermanagercmd.md)
- [сервервероптин](serverweroptin.md)
- [Установка переменных среды](set_1.md)
- [Задание теневого копирования](set_2.md)
  - [задать контекст](set-context.md)
  - [Идентификатор набора](set-id.md)
  - [setlocal](setlocal.md)
  - [Задание метаданных](set-metadata.md)
  - [Параметр Set](set-option.md)
  - [задать verbose](set-verbose.md)
- [setx](setx.md)
- [sfc](sfc.md)
- [shadow](shadow.md)
- [shift](shift.md)
- [showmount](showmount.md)
- [shrink](shrink.md)
- [shutdown](shutdown.md)
- [имитировать восстановление](simulate-restore.md)
- [sort](sort.md)
- [start](start.md)
- [набор подкоманд для устройства](subcommand-set-device.md)
- [подкоманда Set дриверграуп](subcommand-set-drivergroup.md)
- [подкоманда Set дриверграупфилтер](subcommand-set-drivergroupfilter.md)
- [подкоманда Set дриверпаккаже](subcommand-set-driverpackage.md)
- [образ набора подкоманд](subcommand-set-image.md)
- [подкоманда Set имажеграуп](subcommand-set-imagegroup.md)
- [сервер набора подкоманд](subcommand-set-server.md)
- [подкоманда Set транспортсервер](subcommand-set-transportserver.md)
- [подкоманда Set мултикасттрансмиссион](subcommand-start-multicasttransmission.md)
- [пространство имен для запуска подкоманды](subcommand-start-namespace.md)
- [подкоманда "запустить сервер"](subcommand-start-server.md)
- [подкоманда Start транспортсервер](subcommand-start-transportserver.md)
- [конец сервера подкоманды](subcommand-stop-server.md)
- [подкоманда, завершение транспортсервер](subcommand-stop-transportserver.md)
- [subst](subst.md)
- [sxstrace](sxstrace.md)
- [sysocmgr](sysocmgr.md)
- [systeminfo](systeminfo.md)


### <a name="t"></a>T

- [takeown](takeown.md)
- [tapicfg](tapicfg.md)
- [taskkill](taskkill.md)
- [tasklist](tasklist.md)
- [tcmsetup](tcmsetup.md)
- [telnet](telnet.md)
  - [закрыть Telnet](telnet-close.md)
  - [Отображение Telnet](telnet-display.md)
  - [открыть Telnet](telnet-open.md)
  - [Завершение работы Telnet](telnet-quit.md)
  - [Отправка Telnet](telnet-send.md)
  - [набор Telnet](telnet-set.md)
  - [состояние Telnet](telnet-status.md)
  - [Telnet не определено](telnet-unset.md)
- [tftp](tftp.md)
- [time](time.md)
- [timeout](timeout_1.md)
- [title](title_1.md)
- [tlntadmn](tlntadmn.md)
- [тпмтул](tpmtool.md)
- [tpmvscmgr](tpmvscmgr.md)
- [tracerpt](tracerpt_1.md)
- [tracert](tracert.md)
- [tree](tree.md)
- [tscon](tscon.md)
- [tsdiscon](tsdiscon.md)
- [tsecimp](tsecimp_1.md)
- [tskill](tskill.md)
- [tsprof](tsprof.md)
- [type](type.md)
- [typeperf](typeperf.md)
- [tzutil](tzutil.md)

### <a name="u"></a>U

- [Unexpose](unexpose.md)
- [UniqueID](uniqueid.md)
- [unlodctr](unlodctr_1.md)

### <a name="v"></a>V

- [ver](ver.md)
- [verifier](verifier.md)
- [verify](verify_1.md)
- [vol](vol.md)
- [vssadmin](vssadmin.md)
  - [vssadmin delete shadows](vssadmin-delete-shadows.md)
  - [vssadmin list shadows](vssadmin-list-shadows.md)
  - [vssadmin list writers](vssadmin-list-writers.md)
  - [vssadmin resize shadowstorage](vssadmin-resize-shadowstorage.md)

### <a name="w"></a>W

- [waitfor](waitfor.md)
- [wbadmin](wbadmin.md)
  - [Wbadmin Удаление каталога](wbadmin-delete-catalog.md)
  - [Wbadmin Delete системстатебаккуп](wbadmin-delete-systemstatebackup.md)
  - [Wbadmin отключить архивацию](wbadmin-disable-backup.md)
  - [Wbadmin включить резервное копирование](wbadmin-enable-backup.md)
  - [Wbadmin get Disks](wbadmin-get-disks.md)
  - [Wbadmin get Items](wbadmin-get-items.md)
  - [Wbadmin get Status](wbadmin-get-status.md)
  - [Wbadmin get versions](wbadmin-get-versions.md)
  - [Wbadmin Restore Catalog](wbadmin-restore-catalog.md)
  - [Wbadmin start backup](wbadmin-start-backup.md)
  - [Wbadmin start Recovery](wbadmin-start-recovery.md)
  - [Wbadmin start сисрековери](wbadmin-start-sysrecovery.md)
  - [Wbadmin start системстатебаккуп](wbadmin-start-systemstatebackup.md)
  - [Wbadmin start systemstaterecovery](wbadmin-start-systemstaterecovery.md)
  - [Wbadmin останавливает задание](wbadmin-stop-job.md)
- [wdsutil](wdsutil.md)
- [wecutil](wecutil.md)
- [wevtutil](wevtutil.md)
- [where](where_1.md)
- [whoami](whoami.md)
- [winnt](winnt.md)
- [winnt32](winnt32.md)
- [winpop](winpop.md)
- [winrs](winrs.md)
- [MEM в WinSAT](winsat-mem.md)
- [мфмедиа WinSAT](winsat-mfmedia.md)
- [wmic](wmic.md)
- [средство](writer.md)
- [wscript](wscript.md)

### <a name="x"></a>X

- [xcopy](xcopy.md)
