---
title: Команды Windows
description: Команды Windows
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c703d07c-8227-4e86-94a6-8ef390f94cdc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 05/22/2018
ms.prod: windows-server-threshold
ms.openlocfilehash: 5c8df2abd826df2745e10ed773ef50d6cf45c60b
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66192691"
---
# <a name="windows-commands"></a>Команды Windows

Всех поддерживаемых версий Windows (сервер и клиент) имеют набор встроенных команд консоли Win32.

Этот набор документации описаны команды Windows, можно использовать для автоматизации задач с помощью скриптов или средств работы со сценариями.

Чтобы найти сведения о конкретной команде, в следующем окне A-Z, выберите имя команды, затем нажмите кнопку имя команды.

[ОБЪЕКТ](#a) |
[B](#b) | 
[C](#c) | 
[D](#d) | 
[E](#e)  | 
 [F](#f) | 
[G](#g) | 
[H](#h) | 
[Я](#i)  |
 [J](#j) | 
[K](#k) | 
[L](#l) | 
[M](#m) | 
[N](#n)  | 
 [O](#o) | 
[P](#p) | 
[Q](#q) | 
[R](#r)  | 
 [S](#s) | 
[T](#t) | 
[U](#u) | 
[V](#v)  | 
 [W](#w) | 
[X](#x) | Y | Z

## <a name="prerequisites"></a>предварительные требования
Информация, содержащаяся в этот PDF-ФАЙЛ, относится к:

-   Windows Server 2019
-   Windows Server (Semi-Annual Channel)
-   Windows Server 2016
-   Windows Server 2012 R2
-   Windows Server 2012 
-   Windows Server 2008 R2
-   Windows Server 2008
-   Windows 10
-   Windows 8.1

### <a name="command-shell-overview"></a>Командная оболочка: Обзор
Интерпретатор команд был первый оболочки, встроенные в Windows для автоматизации обычных задач, таких как управление учетными записями пользователей или еженощное резервное копирование с файлами пакетный (BAT). С помощью сервера сценариев Windows можно выполнить более сложные сценарии в командной оболочке. Дополнительные сведения см. в разделе [cscript](cscript.md) или [wscript](wscript.md). Можно более эффективно выполнять операции с помощью сценариев, чем с помощью пользовательского интерфейса. Сценарии принять все команды, доступные в командной строке.

Windows состоит из двух командных оболочках. Командная оболочка и [PowerShell](https://docs.microsoft.com/powershell/scripting/powershell-scripting?view=powershell-6). Каждой оболочки — это программа, которая обеспечивает прямую связь между пользователем и операционной системы или приложения, предоставляющий среду для автоматизации ИТ-операций.

PowerShell была разработана для расширения возможностей командной оболочки для выполнения команд PowerShell, называющихся командлетами. Командлеты похожи на команды Windows, но обеспечивают большую гибкость, язык сценариев. Команды Windows и командлеты PowerShell можно запустить в Powershell, но командная оболочка может выполняться только в том случае, команды Windows и не командлеты PowerShell.

Для наиболее надежной, актуальные Windows автоматизации рекомендуется использовать PowerShell вместо команды Windows или Windows скрипт узла для Windows автоматизации. 
> [!NOTE]
>Можно также загрузить и установить [PowerShell Core](https://docs.microsoft.com/powershell/scripting/whats-new/what-s-new-in-powershell-core-60?view=powershell-6), открытым исходным кодом версии PowerShell. 

> [!CAUTION]
> Неправильное изменение реестра может серьезно повредить систему. Прежде чем вносить следующие изменения в реестр, сделайте резервные копии всех важных данных на компьютере.

> [!NOTE]
> Чтобы включить или отключить завершения файлов и папок имя в командной оболочке в сеансе входа в систему компьютера или пользователя, выполните **regedit.exe** и задайте следующее **значение reg_DWOrd**:
> 
> HKEY_LOCAL_MACHINE\Software\Microsoft\Command Processor\completionChar\reg_DWOrd
> 
> Для задания **reg_DWOrd** значение, используйте шестнадцатеричное значение управляющего символа для определенной функции (например, **0-9** — это вкладка и **0 08** является Backspace). Пользовательские настройки имеют приоритет над параметрами компьютера и параметры командной строки имеют приоритет над параметрами реестра.

## <a name="command-line-reference-a-z"></a>Справочник по командной строке, A – Z
Чтобы найти сведения о конкретной команде Windows, в следующем окне A-Z, выберите имя команды, затем нажмите кнопку имя команды.

[ОБЪЕКТ](#a) |
[B](#b) | 
[C](#c) | 
[D](#d) | 
[E](#e)  | 
 [F](#f) | 
[G](#g) | 
[H](#h) | 
[Я](#i)  |
 [J](#j) | 
[K](#k) | 
[L](#l) | 
[M](#m) | 
[N](#n)  | 
 [O](#o) | 
[P](#p) | 
[Q](#q) | 
[R](#r)  | 
 [S](#s) | 
[T](#t) | 
[U](#u) | 
[V](#v)  | 
 [W](#w) | 
[X](#x) | Y | Z)

### <a name="a"></a>Объект
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
-   [bcdboot](bcdboot.md)
-   [bcdedit](bcdedit.md)
-   [bdehdcfg](bdehdcfg.md)
-   [bitsadmin](bitsadmin.md)
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
  -   [приоритет bitsadmin get](bitsadmin-getpriority.md)
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
  -   [bitsadmin передачи](bitsadmin-transfer.md)
  -   [bitsadmin util](bitsadmin-util.md)
  -   [bitsadmin wrap](bitsadmin-wrap.md)
-   [bootcfg](bootcfg.md)
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
-   [break](break_1.md)

### <a name="c"></a>C
-   [cacls](cacls_1.md)
-   [call](call.md)
-   [cd](cd.md)
-   [certreq](certreq_1.md)
-   [certutil](certutil.md)
-   [change](change.md)
  -   [change logon](change-logon.md)
  -   [change port](change-port.md)
  -   [change user](change-user.md)
-   [chcp](chcp.md)
-   [chdir](chdir_1.md)
-   [chglogon](chglogon.md)
-   [chgport](chgport.md)
-   [chgusr](chgusr.md)
-   [chkdsk](chkdsk.md)
-   [chkntfs](chkntfs.md)
-   [choice](choice.md)
-   [cipher](cipher.md)
-   [clip](clip.md)
-   [cls](cls.md)
-   [Cmd](Cmd.md)
-   [cmdkey](cmdkey.md)
-   [cmstp](cmstp.md)
-   [color](color.md)
-   [comp](comp.md)
-   [compact](compact.md)
-   [convert](convert.md)
-   [copy](copy.md)
-   [cprofile](cprofile.md)
-   [cscript](cscript.md)

### <a name="d"></a>D
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

### <a name="e"></a>E
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

### <a name="f"></a>F
-   [fc](fc.md)
-   [find](find.md)
-   [findstr](findstr.md)
-   [finger](finger.md)
-   [flattemp](flattemp.md)
-   [fondue](fondue.md)
-   [for](for.md)
-   [forfiles](forfiles.md)
-   [format](format.md)
-   [freedisk](freedisk.md)
-   [fsutil](fsutil.md)
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
-   [FTP](ftp.md)
-   [ftype](ftype.md)
-   [fveupdate](fveupdate.md)

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
-   [klist](klist.md)
-   [ksetup](ksetup.md)
  -   [ksetup:setrealm](ksetup-setrealm.md)
  -   [ksetup:mapuser](ksetup-mapuser.md)
  -   [ksetup:addkdc](ksetup-addkdc.md)
  -   [ksetup:delkdc](ksetup-delkdc.md)
  -   [ksetup:addkpasswd](ksetup-addkpasswd.md)
  -   [ksetup:delkpasswd](ksetup-delkpasswd.md)
  -   [ksetup:Server](ksetup-server.md)
  -   [ksetup:setcomputerpassword](ksetup-setcomputerpassword.md)
  -   [ksetup:removerealm](ksetup-removerealm.md)
  -   [ksetup:domain](ksetup-domain.md)
  -   [ksetup:ChangePassword](ksetup-changepassword.md)
  -   [ksetup:listrealmflags](ksetup-listrealmflags.md)
  -   [ksetup:setrealmflags](ksetup-setrealmflags.md)
  -   [ksetup:addrealmflags](ksetup-addrealmflags.md)
  -   [ksetup:delrealmflags](ksetup-delrealmflags.md)
  -   [ksetup:dumpstate](ksetup-dumpstate.md)
  -   [ksetup:addhosttorealmmap](ksetup-addhosttorealmmap.md)
  -   [ksetup:delhosttorealmmap](ksetup-delhosttorealmmap.md)
  -   [ksetup:setenctypeattr](ksetup-setenctypeattr.md)
  -   [ksetup:getenctypeattr](ksetup-getenctypeattr.md)
  -   [ksetup:addenctypeattr](ksetup-addenctypeattr.md)
  -   [ksetup:delenctypeattr](ksetup-delenctypeattr.md) 
-   [ktmutil](ktmutil.md)
-   [ktpass](ktpass.md)

### <a name="l"></a>L
-   [label](label.md)
-   [lodctr](lodctr.md)
-   [logman](logman.md)
  -   [logman create](logman-create.md)
  -   [logman query](logman-query.md)
  -   [Logman start & 124; остановить](logman-start-stop.md)
  -   [logman delete](logman-delete.md)
  -   [logman update](logman-update.md)
  -   [Logman import & 124; Экспорт](logman-import-export.md)
-   [logoff](logoff.md)
-   [lpq](lpq.md)
-   [lpr](lpr.md)

### <a name="m"></a>M
-   [macfile](macfile.md)
-   [makecab](makecab.md)
-   [manage-bde](manage-bde.md)
  -   [готов: состояние](manage-bde-status.md)
  -   [готов: на](manage-bde-on.md)
  -   [готов: off](manage-bde-off.md)
  -   [готов: Приостановка](manage-bde-pause.md)
  -   [готов: возобновление](manage-bde-resume.md)
  -   [готов: блокировки](manage-bde-lock.md)
  -   [готов: разблокировки](manage-bde-unlock.md)
  -   [готов: автоматическое разблокирование диска](manage-bde-autounlock.md)
  -   [готов: предохранители](manage-bde-protectors.md)
  -   [готов: доверенного платформенного модуля](manage-bde-tpm.md)
  -   [готов: setidentifier](manage-bde-setidentifier.md)
  -   [готов: ForceRecovery](manage-bde-forcerecovery.md)
  -   [готов: изменение пароля](manage-bde-changepassword.md)
  -   [готов: changepin](manage-bde-changepin.md)
  -   [готов: changekey](manage-bde-changekey.md)
  -   [готов: KeyPackage](manage-bde-keypackage.md)
  -   [готов: обновление](manage-bde-upgrade.md)
  -   [готов: WipeFreeSpace](manage-bde-wipefreespace.md)
-   [mapadmin](mapadmin.md)
-   [Md](Md.md)
-   [mkdir](mkdir.md)
-   [mklink](mklink.md)
-   [mmc](mmc.md)
-   [mode](mode.md)
-   [more](more.md)
-   [mount](mount.md)
-   [mountvol](mountvol.md)
-   [move](move.md)
-   [mqbkup](mqbkup.md)
-   [mqsvc](mqsvc.md)
-   [mqtgsvc](mqtgsvc.md)
-   [msdt](msdt.md)
-   [msg](msg.md)
-   [msiexec](msiexec.md)
-   [msinfo32](msinfo32.md)
-   [mstsc](mstsc.md)

### <a name="n"></a>N
-   [nbtstat](nbtstat.md)
-   [netcfg](netcfg.md)
-   [netsh](netsh.md)
-   [netstat](netstat.md)
-   [Net print](net-print.md)
-   [nfsadmin](nfsadmin.md)
-   [nfsshare](nfsshare.md)
-   [nfsstat](nfsstat.md)
-   [nlbmgr](nlbmgr.md)
-   [nslookup](nslookup.md)
  -   [выход команды nslookup](nslookup-exit-command.md)
  -   [Команда nslookup пальцем](nslookup-finger-command.md)
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
-   [ntbackup](ntbackup.md)
-   [ntcmdprompt](ntcmdprompt.md)
-   [ntfrsutl](ntfrsutl.md)

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
-   [rcp](rcp.md)
-   [rd](rd.md)
-   [rdpsign](rdpsign.md)
-   [recover](recover.md)
-   [reg](reg.md)
  -   [Добавление REG](reg-add.md)
  -   [Сравнение REG](reg-compare.md)
  -   [Копировать REG](reg-copy.md)
  -   [reg delete](reg-delete.md)
  -   [reg export](reg-export.md)
  -   [reg import](reg-import.md)
  -   [REG нагрузки](reg-load.md)
  -   [reg query](reg-query.md)
  -   [Восстановление REG](reg-restore.md)
  -   [REG сохранить](reg-save.md)
  -   [reg unload](reg-unload.md)
-   [regini](regini.md)
-   [regsvr32](regsvr32.md)
-   [relog](relog.md)
-   [rem](rem.md)
-   [ren](ren.md)
-   [rename](rename.md)
-   [repair-bde](repair-bde.md)
-   [replace](replace.md)
-   [reset session](reset-session.md)
-   [rexec](rexec.md)
-   [risetup](risetup.md)
-   [rmdir](rmdir.md)
-   [robocopy](robocopy.md)
-   [route_ws2008](route_ws2008.md)
-   [rpcinfo](rpcinfo.md)
-   [rpcping](rpcping.md)
-   [rsh](rsh.md)
-   [rundll32](rundll32.md)
-   [rwinsta](rwinsta.md)

### <a name="s"></a>S
-   [schtasks](schtasks.md)
-   [Scwcmd](Scwcmd.md)
  -   [Scwcmd: анализ](scwcmd-analyze.md)
  -   [Scwcmd: Настройка](scwcmd-configure.md)
  -   [Scwcmd: регистрация](scwcmd-register.md) 
  -   [Scwcmd: отката](scwcmd-rollback.md) 
  -   [Scwcmd: преобразование](scwcmd-transform.md) 
  -   [Scwcmd: представление](scwcmd-view.md) 
-   [secedit](secedit.md)
  -   [Secedit: анализ](secedit-analyze.md)
  -   [Secedit: Настройка](secedit-configure.md)
  -   [Secedit:Export](secedit-export.md)
  -   [Secedit:generaterollback](secedit-generaterollback.md)
  -   [Secedit:import](secedit-import.md)
  -   [Secedit: проверка](secedit-validate.md)
-   [serverceipoptin](serverceipoptin.md)
-   [Servermanagercmd](Servermanagercmd.md)
-   [serverweroptin](serverweroptin.md)
-   [set](set_1.md)
-   [setlocal](setlocal.md)
-   [setx](setx.md)
-   [sfc](sfc.md)
-   [shadow](shadow.md)
-   [shift](shift.md)
-   [showmount](showmount.md)
-   [shutdown](shutdown.md)
-   [sort](sort.md)
-   [start](start.md)
-   [subst](subst.md)
-   [sxstrace](sxstrace.md)
-   [sysocmgr](sysocmgr.md)
-   [systeminfo](systeminfo.md)

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
-   [waitfor](waitfor.md)
-   [wbadmin](wbadmin.md)
  -   [Wbadmin enable backup](wbadmin-enable-backup.md)
  -   [Отключите WBADMIN резервное копирование](wbadmin-disable-backup.md)
  -   [начало архивации WBADMIN](wbadmin-start-backup.md)
  -   [WBADMIN остановка задания](wbadmin-stop-job.md)
  -   [WBADMIN get версий](wbadmin-get-versions.md)
  -   [WBADMIN get элементов](wbadmin-get-items.md)
  -   [Wbadmin start восстановления](wbadmin-start-recovery.md)
  -   [состояние WBADMIN get](wbadmin-get-status.md)
  -   [WBADMIN get дисков](wbadmin-get-disks.md)
  -   [Wbadmin start systemstaterecovery](wbadmin-start-systemstaterecovery.md)
  -   [Wbadmin start systemstatebackup](wbadmin-start-systemstatebackup.md)
  -   [WBADMIN delete systemstatebackup](wbadmin-delete-systemstatebackup.md)
  -   [Wbadmin start sysrecovery](wbadmin-start-sysrecovery.md)
  -   [WBADMIN восстановления каталога](wbadmin-restore-catalog.md)
  -   [WBADMIN delete каталога](wbadmin-delete-catalog.md)
-   [wdsutil](wdsutil.md)
-   [wecutil](wecutil.md)
-   [wevtutil](wevtutil.md)
-   [where](where_1.md)
-   [whoami](whoami.md)
-   [winnt](winnt.md)
-   [winnt32](winnt32.md)
-   [winpop](winpop.md)
-   [winrs](winrs.md)
-   [WLBS](wlbs_1.md)
-   [wmic](wmic.md)
-   [wscript](wscript.md)

### <a name="x"></a>X
-   [xcopy](xcopy.md)
