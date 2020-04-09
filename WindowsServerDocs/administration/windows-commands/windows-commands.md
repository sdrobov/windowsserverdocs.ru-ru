---
title: Команды Windows
description: Команды Windows
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c703d07c-8227-4e86-94a6-8ef390f94cdc
author: jasongerend
ms.author: jgerend
manager: dongill
ms.date: 06/26/2019
ms.prod: windows-server
ms.openlocfilehash: 9d68e2becbf9c6522be7e1ff6e6742d44f3a8247
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80829237"
---
# <a name="windows-commands"></a>Команды Windows

Все поддерживаемые версии Windows (сервер и клиент) имеют набор встроенных команд консоли Win32.

Этот набор документации описывает команды Windows, которые можно использовать для автоматизации задач с помощью скриптов или средств создания скриптов.

Чтобы найти сведения о конкретной команде, в следующем меню A-Z щелкните букву, с которой начинается команда, а затем щелкните имя команды.

[ |
](#a) [B](#b) | 
[C](#c) | 
[D](#d) | 
[E](#e) | 
[F](#f) | 
[G](#g) | 
[H](#h) | 
[I](#i) |
[J](#j) | 
[K](#k) | 
[L](#l) | 
[M](#m) | 
[N](#n) | 
[O](#o) | 
[P](#p) | 
[Q](#q) | 
[R](#r) | 
[S](#s) | 
[t](#t) | 
[U](#u) | 
[V](#v) | 
[W](#w) | 
[X](#x) | Y | Гармошкой

## <a name="prerequisites"></a>Предварительные требования

Сведения, содержащиеся в этом разделе, применимы к:

-   Windows Server 2019
-   Windows Server (Semi-Annual Channel)
-   Windows Server 2016
-   Windows Server 2012 R2
-   Windows Server 2012 
-   Windows Server 2008 R2
-   Windows Server 2008
-   Windows 10
-   Windows 8.1

### <a name="command-shell-overview"></a>Общие сведения о командной оболочке

Командная оболочка была первой оболочкой, встроенной в Windows, для автоматизации стандартных задач, таких как управление учетными записями пользователей или ночное резервное копирование с пакетными файлами (bat). С помощью сервера сценариев Windows можно выполнять более сложные сценарии в командной оболочке. Дополнительные сведения см. в разделе [cscript](cscript.md) или [Wscript](wscript.md). С помощью скриптов можно более эффективно выполнять операции, чем с помощью пользовательского интерфейса. Скрипты принимают все команды, доступные в командной строке.

Windows имеет две командные оболочки: Командная оболочка и [PowerShell](https://docs.microsoft.com/powershell/scripting/powershell-scripting?view=powershell-6). Каждая оболочка представляет собой программную программу, обеспечивающую прямой обмен данными между вами и операционной системой или приложением, предоставляя среду для автоматизации ИТ-операций.

PowerShell был разработан для расширения возможностей командной оболочки для выполнения команд PowerShell, называемых командлетами. Командлеты похожи на команды Windows, но предоставляют более расширяемый язык сценариев. Вы можете выполнять команды Windows и командлеты PowerShell в PowerShell, но Командная оболочка может выполнять только команды Windows, а не командлеты PowerShell.

Для наиболее надежной и последней версии службы автоматизации Windows рекомендуется использовать PowerShell вместо команд Windows или сервера сценариев Windows для службы автоматизации Windows. 
> [!NOTE]
>Вы также можете скачать и установить [PowerShell Core](https://docs.microsoft.com/powershell/scripting/whats-new/what-s-new-in-powershell-core-60?view=powershell-6), версию PowerShell с открытым исходным кодом. 

> [!CAUTION]
> Внесение неправильных изменений в реестр может нанести серьезный вред системе. Перед внесением следующих изменений в реестр следует создать резервную копию всех ценных данных на компьютере.

> [!NOTE]
> Чтобы включить или отключить завершение имен файлов и каталогов в командной оболочке на компьютере или в сеансе входа пользователя, запустите **программу regedit. exe** и задайте следующее **значение reg_DWOrd**:
> 
> HKEY_LOCAL_MACHINE \Софтваре\микрософт\комманд Процессор\комплетиончар\ reg_DWOrd
> 
> Чтобы задать значение **reg_DWOrd** , используйте шестнадцатеричное значение управляющего символа для конкретной функции (например, **0 9** — TAB, а **0 08** — Backspace). Заданные пользователем параметры имеют приоритет над параметрами компьютера, а параметры командной строки имеют приоритет над параметрами реестра.

## <a name="command-line-reference-a-z"></a>Справочник по командной строке A-Z

Чтобы найти сведения об определенной команде Windows, в следующем меню A-Z щелкните букву, с которой начинается команда, а затем щелкните имя команды.

[ |
](#a) [B](#b) | 
[C](#c) | 
[D](#d) | 
[E](#e) | 
[F](#f) | 
[G](#g) | 
[H](#h) | 
[I](#i) |
[J](#j) | 
[K](#k) | 
[L](#l) | 
[M](#m) | 
[N](#n) | 
[O](#o) | 
[P](#p) | 
[Q](#q) | 
[R](#r) | 
[S](#s) | 
[t](#t) | 
[U](#u) | 
[V](#v) | 
[W](#w) | 
[X](#x) | Y | Гармошкой

### <a name="a"></a>А
-   [append](append.md)
-   [arp](arp.md)
-   [assoc](assoc.md)
-   [at](at.md)
-   [atmadm](atmadm.md)
-   [attrib](attrib.md)
-   [auditpol](auditpol.md)
-   [autochk](autochk.md)
-   [autoconv](autoconv.md)
-   [autofmt](autofmt.md)

### <a name="b"></a>B
- [bcdboot](bcdboot.md)
- [bcdedit](bcdedit.md)
- [bdehdcfg](bdehdcfg.md)
- [bitsadmin](bitsadmin.md)
  -   [bitsadmin addfile](bitsadmin-addfile.md)
  -   [bitsadmin addfileset](bitsadmin-addfileset.md)
  -   [bitsadmin addfilewithranges](bitsadmin-addfilewithranges.md)
  -   [bitsadmin cancel](bitsadmin-cancel.md)
  -   [bitsadmin complete](bitsadmin-complete.md)
  -   [bitsadmin create](bitsadmin-create.md)
  -   [bitsadmin getaclflags](bitsadmin-getaclflags.md)
  -   [bitsadmin getbytestotal](bitsadmin-getbytestotal.md)
  -   [bitsadmin getbytestransferred](bitsadmin-getbytestransferred.md)
  -   [bitsadmin getcompletiontime](bitsadmin-getcompletiontime.md)
  -   [bitsadmin getcreationtime](bitsadmin-getcreationtime.md)
  -   [bitsadmin getdescription](bitsadmin-getdescription.md)
  -   [bitsadmin getdisplayname](bitsadmin-getdisplayname.md)
  -   [bitsadmin geterror](bitsadmin-geterror.md)
  -   [bitsadmin geterrorcount](bitsadmin-geterrorcount.md)
  -   [bitsadmin getfilestotal](bitsadmin-getfilestotal.md)
  -   [bitsadmin getfilestransferred](bitsadmin-getfilestransferred.md)
  -   [bitsadmin getminretrydelay](bitsadmin-getminretrydelay.md)
  -   [bitsadmin getmodificationtime](bitsadmin-getmodificationtime.md)
  -   [bitsadmin getnoprogresstimeout](bitsadmin-getnoprogresstimeout.md)
  -   [bitsadmin getnotifycmdline](bitsadmin-getnotifycmdline.md)
  -   [bitsadmin getnotifyflags](bitsadmin-getnotifyflags.md)
  -   [bitsadmin getnotifyinterface](bitsadmin-getnotifyinterface.md)
  -   [bitsadmin getowner](bitsadmin-getowner.md)
  -   [битсадмин получить приоритет](bitsadmin-getpriority.md)
  -   [bitsadmin getproxybypasslist](bitsadmin-getproxybypasslist.md)
  -   [bitsadmin getproxylist](bitsadmin-getproxylist.md)
  -   [bitsadmin getproxyusage](bitsadmin-getproxyusage.md)
  -   [bitsadmin getreplydata](bitsadmin-getreplydata.md)
  -   [bitsadmin getreplyfilename](bitsadmin-getreplyfilename.md)
  -   [bitsadmin getreplyprogress](bitsadmin-getreplyprogress.md)
  -   [bitsadmin getstate](bitsadmin-getstate.md)
  -   [bitsadmin gettype](bitsadmin-gettype.md)
  -   [bitsadmin help](bitsadmin-help.md)
  -   [bitsadmin info](bitsadmin-info.md)
  -   [bitsadmin list](bitsadmin-list.md)
  -   [bitsadmin listfiles](bitsadmin-listfiles.md)
  -   [bitsadmin monitor](bitsadmin-monitor.md)
  -   [bitsadmin nowrap](bitsadmin-nowrap.md)
  -   [bitsadmin rawreturn](bitsadmin-rawreturn.md)
  -   [bitsadmin removecredentials](bitsadmin-removecredentials.md)
  -   [bitsadmin replaceremoteprefix](bitsadmin-replaceremoteprefix.md)
  -   [bitsadmin reset](bitsadmin-reset.md)
  -   [bitsadmin resume](bitsadmin-resume.md)
  -   [bitsadmin setaclflag](bitsadmin-setaclflag.md)
  -   [bitsadmin setcredentials](bitsadmin-setcredentials.md)
  -   [bitsadmin setdescription](bitsadmin-setdescription.md)
  -   [bitsadmin setdisplayname](bitsadmin-setdisplayname.md)
  -   [bitsadmin setminretrydelay](bitsadmin-setminretrydelay.md)
  -   [bitsadmin setnoprogresstimeout](bitsadmin-setnoprogresstimeout.md)
  -   [bitsadmin setnotifycmdline](bitsadmin-setnotifycmdline.md)
  -   [bitsadmin setnotifyflags](bitsadmin-setnotifyflags.md)
  -   [bitsadmin setpriority](bitsadmin-setpriority.md)
  -   [bitsadmin setproxysettings](bitsadmin-setproxysettings.md)
  -   [bitsadmin setreplyfilename](bitsadmin-setreplyfilename.md)
  -   [bitsadmin suspend](bitsadmin-suspend.md)
  -   [bitsadmin takeownership](bitsadmin-takeownership.md)
  -   [Перенос битсадмин](bitsadmin-transfer.md)
  -   [bitsadmin util](bitsadmin-util.md)
  -   [bitsadmin wrap](bitsadmin-wrap.md)
- [bootcfg](bootcfg.md)
  -   [bootcfg addsw](bootcfg-addsw.md)
  -   [bootcfg copy](bootcfg-copy.md)
  -   [bootcfg dbg1394](bootcfg-dbg1394.md)
  -   [bootcfg debug](bootcfg-debug.md)  
  -   [bootcfg default](bootcfg-default.md)
  -   [bootcfg delete](bootcfg-delete.md)
  -   [bootcfg ems](bootcfg-ems.md)
  -   [bootcfg query](bootcfg-query.md)
  -   [bootcfg raw](bootcfg-raw.md)
  -   [bootcfg rmsw](bootcfg-rmsw.md)
  -   [bootcfg timeout](bootcfg-timeout.md)
- [break](break_1.md)

### <a name="c"></a>C
- [cacls](cacls_1.md)
- [call](call.md)
- [cd](cd.md)
- [certreq](certreq_1.md)
- [certutil](certutil.md)
- [change](change.md)
  -   [change logon](change-logon.md)
  -   [change port](change-port.md)
  -   [change user](change-user.md)
- [chcp](chcp.md)
- [chdir](chdir_1.md)
- [chglogon](chglogon.md)
- [chgport](chgport.md)
- [chgusr](chgusr.md)
- [chkdsk](chkdsk.md)
- [chkntfs](chkntfs.md)
- [choice](choice.md)
- [cipher](cipher.md)
- [cleanmgr](cleanmgr.md)
- [clip](clip.md)
- [cls](cls.md)
- [Cmd](Cmd.md)
- [cmdkey](cmdkey.md)
- [cmstp](cmstp.md)
- [color](color.md)
- [comp](comp.md)
- [compact](compact.md)
- [convert](convert.md)
- [copy](copy.md)
- [cprofile](cprofile.md)
- [cscript](cscript.md)

### <a name="d"></a>Г
-   [date](date.md)
-   [dcgpofix](dcgpofix.md)
-   [defrag](defrag.md)
-   [del](del.md)
-   [dfsrmig](dfsrmig.md)
-   [diantz](diantz.md)
-   [dir](dir.md)
-   [diskcomp](diskcomp.md)
-   [diskcopy](diskcopy.md)
-   [diskpart](diskpart.md)
-   [diskperf](diskperf.md)
-   [diskraid](diskraid.md)
-   [diskshadow](diskshadow.md)
-   [dispdiag](dispdiag.md)
-   [dnscmd](Dnscmd.md)
-   [doskey](doskey.md)
-   [driverquery](driverquery.md)

### <a name="e"></a>Д
-   [echo](echo.md)
-   [edit](edit.md)
-   [endlocal](endlocal.md)
-   [erase](erase.md)
-   [eventcreate](eventcreate.md)
-   [eventquery](eventquery.md)
-   [eventtriggers](eventtriggers.md)
-   [evntcmd](Evntcmd.md)
-   [exit](exit_2.md)
-   [expand](expand.md)
-   [extract](extract.md)

### <a name="f"></a>C
- [fc](fc.md)
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
  -   [fsutil 8dot3name](fsutil-8dot3name.md) 
  -   [fsutil behavior](fsutil-behavior.md) 
  -   [fsutil file](fsutil-file.md)
  -   [fsutil fsinfo](fsutil-fsinfo.md)
  -   [fsutil hardlink](fsutil-hardlink.md)
  -   [fsutil objectid](fsutil-objectid.md)
  -   [fsutil quota](fsutil-quota.md)
  -   [fsutil repair](fsutil-repair.md)
  -   [fsutil reparsepoint](fsutil-reparsepoint.md)
  -   [fsutil resource](fsutil-resource.md)
  -   [fsutil sparse](fsutil-sparse.md)
  -   [fsutil tiering](fsutil-tiering.md)
  -   [fsutil transaction](fsutil-transaction.md)
  -   [fsutil usn](fsutil-usn.md)
  -   [fsutil volume](fsutil-volume.md)
  -   [fsutil wim](fsutil-wim.md)
- [адресов](ftp.md)
- [ftype](ftype.md)
- [fveupdate](fveupdate.md)

### <a name="g"></a>G
-   [getmac](getmac.md)
-   [gettype](gettype.md)
-   [goto](goto.md)
-   [gpfixup](gpfixup.md)
-   [gpresult](gpresult.md)
-   [gpupdate](gpupdate.md)
-   [graftabl](graftabl.md)

### <a name="h"></a>H
-   [help](help.md)
-   [helpctr](helpctr.md)
-   [hostname](hostname.md)

### <a name="i"></a>I
-   [icacls](icacls.md)
-   [if](if.md)
-   [inuse](inuse.md)
-   [ipconfig](ipconfig.md)
-   [ipxroute](ipxroute.md)
-   [irftp](irftp.md)

### <a name="j"></a>J
-   [jetpack](jetpack.md)

### <a name="k"></a>K
- [klist](klist.md)
- [ksetup](ksetup.md)
  -   [ksetup: сетреалм](ksetup-setrealm.md)
  -   [ksetup: мапусер](ksetup-mapuser.md)
  -   [ksetup: аддкдк](ksetup-addkdc.md)
  -   [ksetup: делкдк](ksetup-delkdc.md)
  -   [ksetup: аддкпассвд](ksetup-addkpasswd.md)
  -   [ksetup: делкпассвд](ksetup-delkpasswd.md)
  -   [ksetup: сервер](ksetup-server.md)
  -   [ksetup: сеткомпутерпассворд](ksetup-setcomputerpassword.md)
  -   [ksetup: ремовереалм](ksetup-removerealm.md)
  -   [ksetup: домен](ksetup-domain.md)
  -   [ksetup: ChangePassword](ksetup-changepassword.md)
  -   [ksetup: листреалмфлагс](ksetup-listrealmflags.md)
  -   [ksetup: сетреалмфлагс](ksetup-setrealmflags.md)
  -   [ksetup: аддреалмфлагс](ksetup-addrealmflags.md)
  -   [ksetup: делреалмфлагс](ksetup-delrealmflags.md)
  -   [ksetup: думпстате](ksetup-dumpstate.md)
  -   [ksetup: аддхосттореалммап](ksetup-addhosttorealmmap.md)
  -   [ksetup: делхосттореалммап](ksetup-delhosttorealmmap.md)
  -   [ksetup: сетенктипеаттр](ksetup-setenctypeattr.md)
  -   [ksetup: жетенктипеаттр](ksetup-getenctypeattr.md)
  -   [ksetup: адденктипеаттр](ksetup-addenctypeattr.md)
  -   [ksetup: деленктипеаттр](ksetup-delenctypeattr.md) 
- [ktmutil](ktmutil.md)
- [ktpass](ktpass.md)

### <a name="l"></a>L
- [label](label.md)
- [lodctr](lodctr.md)
- [logman](logman.md)
  -   [logman create](logman-create.md)
  -   [logman query](logman-query.md)
  -   [Запуск Logman & 124; позиции](logman-start-stop.md)
  -   [logman delete](logman-delete.md)
  -   [logman update](logman-update.md)
  -   [Импорт & 124; программе](logman-import-export.md)
- [logoff](logoff.md)
- [lpq](lpq.md)
- [lpr](lpr.md)

### <a name="m"></a>M
- [macfile](macfile.md)
- [makecab](makecab.md)
- [manage-bde](manage-bde.md)
  -   [Manage-bde: Status](manage-bde-status.md)
  -   [Manage-bde: on](manage-bde-on.md)
  -   [Управление-BDE: выкл.](manage-bde-off.md)
  -   [Управление — BDE: Pause](manage-bde-pause.md)
  -   [Управление — BDE: Resume](manage-bde-resume.md)
  -   [Управление — BDE: Lock](manage-bde-lock.md)
  -   [Управление — BDE: Unlock](manage-bde-unlock.md)
  -   [Manage-bde: автоматическое разблокирование](manage-bde-autounlock.md)
  -   [Manage-bde: protectors](manage-bde-protectors.md)
  -   [Manage-bde: TPM](manage-bde-tpm.md)
  -   [Manage-bde: сетидентифиер](manage-bde-setidentifier.md)
  -   [Manage-bde: Форцерековери](manage-bde-forcerecovery.md)
  -   [Manage-bde: ChangePassword](manage-bde-changepassword.md)
  -   [Manage-bde: чанжепин](manage-bde-changepin.md)
  -   [Manage-bde: чанжекэй](manage-bde-changekey.md)
  -   [Manage-bde: Кэйпаккаже](manage-bde-keypackage.md)
  -   [Manage-bde: обновление](manage-bde-upgrade.md)
  -   [Manage-bde: Випефриспаце](manage-bde-wipefreespace.md)
- [mapadmin](mapadmin.md)
- [Md](Md.md)
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

### <a name="n"></a>В
- [nbtstat](nbtstat.md)
- [netcfg](netcfg.md)
- [netsh](netsh.md)
- [netstat](netstat.md)
- [Net print](net-print.md)
- [nfsadmin](nfsadmin.md)
- [nfsshare](nfsshare.md)
- [nfsstat](nfsstat.md)
- [nlbmgr](nlbmgr.md)
- [nslookup](nslookup.md)
  -   [Команда nslookup Exit](nslookup-exit-command.md)
  -   [Команда nslookup Finger](nslookup-finger-command.md)
  -   [nslookup help](nslookup-help.md)
  -   [nslookup ls](nslookup-ls.md)
  -   [nslookup lserver](nslookup-lserver.md)
  -   [nslookup root](nslookup-root.md)
  -   [nslookup server](nslookup-server.md)
  -   [nslookup set](nslookup-set.md)
  -   [nslookup set all](nslookup-set-all.md)
  -   [nslookup set class](nslookup-set-class.md)
  -   [nslookup set d2](nslookup-set-d2.md)
  -   [nslookup set debug](nslookup-set-debug.md)
  -   [nslookup set domain](nslookup-set-domain.md)
  -   [nslookup set port](nslookup-set-port.md)
  -   [nslookup set querytype](nslookup-set-querytype.md)
  -   [nslookup set recurse](nslookup-set-recurse.md)
  -   [nslookup set retry](nslookup-set-retry.md)
  -   [nslookup set root](nslookup-set-root.md)
  -   [nslookup set search](nslookup-set-search.md)
  -   [nslookup set srchlist](nslookup-set-srchlist.md)
  -   [nslookup set timeout](nslookup-set-timeout.md)
  -   [nslookup set type](nslookup-set-type.md)
  -   [nslookup set vc](nslookup-set-vc.md)
  -   [nslookup view](nslookup-view.md)
- [ntbackup](ntbackup.md)
- [ntcmdprompt](ntcmdprompt.md)
- [ntfrsutl](ntfrsutl.md)

### <a name="o"></a>O
-   [openfiles](openfiles.md)

### <a name="p"></a>P
-   [pagefileconfig](pagefileconfig.md)
-   [path](path.md)
-   [pathping](pathping.md)
-   [pause](pause.md)
-   [pbadmin](pbadmin.md)
-   [pentnt](pentnt.md)
-   [perfmon](perfmon.md)
-   [ping](ping.md)
-   [pnpunattend](pnpunattend.md)
-   [pnputil](pnputil.md)
-   [popd](popd.md)
-   [PowerShell](PowerShell.md)
-   [PowerShell_ise](PowerShell_ise.md)
-   [print](print.md)
-   [prncnfg](prncnfg.md)
-   [prndrvr](prndrvr.md)
-   [prnjobs](prnjobs.md)
-   [prnmngr](prnmngr.md)
-   [prnport](prnport.md)
-   [prnqctl](prnqctl.md)
-   [prompt](prompt.md)
-   [pubprn](pubprn.md)
-   [pushd](pushd.md)
-   [pushprinterconnections](pushprinterconnections.md)

### <a name="q"></a>Q
-   [qappsrv](qappsrv.md)
-   [qprocess](qprocess.md)
-   [запрос](query.md)
-   [quser](quser.md)
-   [qwinsta](qwinsta.md)

### <a name="r"></a>R
- [rcp](rcp.md)
- [rd](rd.md)
- [rdpsign](rdpsign.md)
- [recover](recover.md)
- [reg](reg.md)
  -   [Добавление reg](reg-add.md)
  -   [reg compare](reg-compare.md)
  -   [копирование reg](reg-copy.md)
  -   [удалить reg](reg-delete.md)
  -   [reg export](reg-export.md)
  -   [импорт реестра](reg-import.md)
  -   [Загрузить reg](reg-load.md)
  -   [запрос reg](reg-query.md)
  -   [Восстановление реестра](reg-restore.md)
  -   [сохранить reg](reg-save.md)
  -   [reg unload](reg-unload.md)
- [regini](regini.md)
- [regsvr32](regsvr32.md)
- [relog](relog.md)
- [rem](rem.md)
- [ren](ren.md)
- [rename](rename.md)
- [repair-bde](repair-bde.md)
- [replace](replace.md)
- [reset session](reset-session.md)
- [rexec](rexec.md)
- [risetup](risetup.md)
- [rmdir](rmdir.md)
- [Robocopy](robocopy.md)
- [route_ws2008](route_ws2008.md)
- [rpcinfo](rpcinfo.md)
- [rpcping](rpcping.md)
- [rsh](rsh.md)
- [rundll32](rundll32.md)
- [rwinsta](rwinsta.md)

### <a name="s"></a>С
- [schtasks](schtasks.md)
- [команду scwcmd](Scwcmd.md)
  -   [команду scwcmd: анализ](scwcmd-analyze.md)
  -   [команду scwcmd: Настройка](scwcmd-configure.md)
  -   [команду scwcmd: регистрация](scwcmd-register.md) 
  -   [команду scwcmd: откат](scwcmd-rollback.md) 
  -   [команду scwcmd: преобразование](scwcmd-transform.md) 
  -   [команду scwcmd: Просмотр](scwcmd-view.md) 
- [secedit](secedit.md)
  -   [Secedit: анализ](secedit-analyze.md)
  -   [Secedit: Настройка](secedit-configure.md)
  -   [Secedit: экспорт](secedit-export.md)
  -   [Secedit: женератероллбакк](secedit-generaterollback.md)
  -   [Secedit: импорт](secedit-import.md)
  -   [Secedit: Проверка](secedit-validate.md)
- [serverceipoptin](serverceipoptin.md)
- [Servermanagercmd](Servermanagercmd.md)
- [сервервероптин](serverweroptin.md)
- [set](set_1.md)
- [setlocal](setlocal.md)
- [setx](setx.md)
- [sfc](sfc.md)
- [shadow](shadow.md)
- [shift](shift.md)
- [showmount](showmount.md)
- [shutdown](shutdown.md)
- [sort](sort.md)
- [start](start.md)
- [subst](subst.md)
- [sxstrace](sxstrace.md)
- [sysocmgr](sysocmgr.md)
- [systeminfo](systeminfo.md)

### <a name="t"></a>T
-   [takeown](takeown.md)
-   [tapicfg](tapicfg.md)
-   [taskkill](taskkill.md)
-   [tasklist](tasklist.md)
-   [tcmsetup](tcmsetup.md)
-   [telnet](telnet.md)
-   [tftp](tftp.md)
-   [time](time.md)
-   [timeout](timeout_1.md)
-   [title](title_1.md)
-   [tlntadmn](tlntadmn.md)
-   [tpmvscmgr](tpmvscmgr.md)
-   [tracerpt](tracerpt_1.md)
-   [tracert](tracert.md)
-   [tree](tree.md)
-   [tscon](tscon.md)
-   [tsdiscon](tsdiscon.md)
-   [tsecimp](tsecimp_1.md)
-   [tskill](tskill.md)
-   [tsprof](tsprof.md)
-   [type](type.md)
-   [typeperf](typeperf.md)
-   [tzutil](tzutil.md)

### <a name="u"></a>U
-   [unlodctr](unlodctr_1.md)

### <a name="v"></a>V
-   [ver](ver.md)
-   [verifier](verifier.md)
-   [verify](verify_1.md)
-   [vol](vol.md)
-   [vssadmin](vssadmin.md)- 

### <a name="w"></a>W
- [waitfor](waitfor.md)
- [wbadmin](wbadmin.md)
  -   [Wbadmin включить резервное копирование](wbadmin-enable-backup.md)
  -   [Wbadmin отключить архивацию](wbadmin-disable-backup.md)
  -   [Wbadmin start backup](wbadmin-start-backup.md)
  -   [Wbadmin останавливает задание](wbadmin-stop-job.md)
  -   [Wbadmin get versions](wbadmin-get-versions.md)
  -   [Wbadmin get Items](wbadmin-get-items.md)
  -   [Wbadmin start Recovery](wbadmin-start-recovery.md)
  -   [Wbadmin get Status](wbadmin-get-status.md)
  -   [Wbadmin get Disks](wbadmin-get-disks.md)
  -   [Wbadmin start systemstaterecovery](wbadmin-start-systemstaterecovery.md)
  -   [Wbadmin start системстатебаккуп](wbadmin-start-systemstatebackup.md)
  -   [Wbadmin Delete системстатебаккуп](wbadmin-delete-systemstatebackup.md)
  -   [Wbadmin start сисрековери](wbadmin-start-sysrecovery.md)
  -   [Wbadmin Restore Catalog](wbadmin-restore-catalog.md)
  -   [Wbadmin Удаление каталога](wbadmin-delete-catalog.md)
- [wdsutil](wdsutil.md)
- [wecutil](wecutil.md)
- [wevtutil](wevtutil.md)
- [where](where_1.md)
- [whoami](whoami.md)
- [winnt](winnt.md)
- [winnt32](winnt32.md)
- [winpop](winpop.md)
- [winrs](winrs.md)
- [wmic](wmic.md)
- [wscript](wscript.md)

### <a name="x"></a>X
-   [xcopy](xcopy.md)
