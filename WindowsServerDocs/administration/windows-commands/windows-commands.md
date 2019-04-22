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
ms.openlocfilehash: 4cc9bc5c288eb063f333fa598dbb3511f7be5966
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59820475"
---
# <a name="windows-commands"></a>Команды Windows

Всех поддерживаемых версий Windows (сервер и клиент) имеют набор встроенных команд консоли Win32.

Этот набор документации описаны команды Windows, можно использовать для автоматизации задач с помощью скриптов или средств работы со сценариями.

Чтобы найти сведения о конкретной команде, в следующем окне A-Z, выберите имя команды, затем нажмите кнопку имя команды.

[ОБЪЕКТ](#BKMK_a) |
[B](#BKMK_b) | 
[C](#BKMK_c) | 
[D](#BKMK_d) | 
[E](#BKMK_e)  | 
 [F](#BKMK_f) | 
[G](#BKMK_g) | 
[H](#BKMK_h) | 
[Я](#BKMK_i)  |
 [J](#BKMK_j) | 
[K](#BKMK_k) | 
[L](#BKMK_l) | 
[M](#BKMK_m) | 
[N](#BKMK_n)  | 
 [O](#BKMK_o) | 
[P](#BKMK_p) | 
[Q](#BKMK_q) | 
[R](#BKMK_r)  | 
 [S](#BKMK_s) | 
[T](#BKMK_t) | 
[U](#BKMK_u) | 
[V](#BKMK_v)  | 
 [W](#BKMK_w) | 
[X](#BKMK_x) | 
[Y](#BKMK_y) | 
[Z](#BKMK_z)

## <a name="BKMK_PREREQ"></a>Предварительные требования
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

### <a name="BKMK_OVR"></a>Командная оболочка: Обзор
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

## <a name="BKMK_CmdRef"></a>Справочник по командной строке, A – Z
Чтобы найти сведения о конкретной команде Windows, в следующем окне A-Z, выберите имя команды, затем нажмите кнопку имя команды.

[ОБЪЕКТ](#BKMK_a) |
[B](#BKMK_b) | 
[C](#BKMK_c) | 
[D](#BKMK_d) | 
[E](#BKMK_e)  | 
 [F](#BKMK_f) | 
[G](#BKMK_g) | 
[H](#BKMK_h) | 
[Я](#BKMK_i)  |
 [J](#BKMK_j) | 
[K](#BKMK_k) | 
[L](#BKMK_l) | 
[M](#BKMK_m) | 
[N](#BKMK_n)  | 
 [O](#BKMK_o) | 
[P](#BKMK_p) | 
[Q](#BKMK_q) | 
[R](#BKMK_r)  | 
 [S](#BKMK_s) | 
[T](#BKMK_t) | 
[U](#BKMK_u) | 
[V](#BKMK_v)  | 
 [W](#BKMK_w) | 
[X](#BKMK_x) | 
[Y](#BKMK_y) | 
[Z](#BKMK_z)

### <a name="BKMK_a"></a>ОБЪЕКТ
-   [добавить](append.md)
-   [ARP](arp.md)
-   [ASSOC](assoc.md)
-   [в](at.md)
-   [atmadm](atmadm.md)
-   [Attrib](attrib.md)
-   [auditpol](auditpol.md)
-   [Autochk](autochk.md)
-   [autoconv](autoconv.md)
-   [autofmt](autofmt.md)

### <a name="BKMK_b"></a>B
-   [BCDboot](bcdboot.md)
-   [bcdedit](bcdedit.md)
-   [Bdehdcfg](bdehdcfg.md)
-   [bitsadmin](bitsadmin.md)
  -   [bitsadmin addfile](bitsadmin-addfile.md)
  -   [bitsadmin addfileset](bitsadmin-addfileset.md)
  -   [bitsadmin addfilewithranges](bitsadmin-addfilewithranges.md)
  -   [Отмена bitsadmin](bitsadmin-cancel.md)
  -   [Полный bitsadmin](bitsadmin-complete.md)
  -   [Создание bitsadmin](bitsadmin-create.md)
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
  -   [bitsadmin справки](bitsadmin-help.md)
  -   [сведения о bitsadmin](bitsadmin-info.md)
  -   [Список bitsadmin](bitsadmin-list.md)
  -   [bitsadmin listfiles](bitsadmin-listfiles.md)
  -   [монитор bitsadmin](bitsadmin-monitor.md)
  -   [bitsadmin nowrap](bitsadmin-nowrap.md)
  -   [bitsadmin rawreturn](bitsadmin-rawreturn.md)
  -   [bitsadmin removecredentials](bitsadmin-removecredentials.md)
  -   [bitsadmin replaceremoteprefix](bitsadmin-replaceremoteprefix.md)
  -   [Сброс bitsadmin](bitsadmin-reset.md)
  -   [Возобновление bitsadmin](bitsadmin-resume.md)
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
  -   [Приостановка bitsadmin](bitsadmin-suspend.md)
  -   [bitsadmin takeownership](bitsadmin-takeownership.md)
  -   [bitsadmin передачи](bitsadmin-transfer.md)
  -   [bitsadmin util](bitsadmin-util.md)
  -   [bitsadmin переноса по словам](bitsadmin-wrap.md)
-   [bootcfg](bootcfg.md)
  -   [bootcfg addsw](bootcfg-addsw.md)
  -   [bootcfg копирования](bootcfg-copy.md)
  -   [bootcfg dbg1394](bootcfg-dbg1394.md)
  -   [bootcfg отладки](bootcfg-debug.md)  
  -   [по умолчанию bootcfg](bootcfg-default.md)
  -   [bootcfg delete](bootcfg-delete.md)
  -   [bootcfg ems](bootcfg-ems.md)
  -   [bootcfg запроса](bootcfg-query.md)
  -   [необработанные bootcfg](bootcfg-raw.md)
  -   [bootcfg rmsw](bootcfg-rmsw.md)
  -   [время ожидания bootcfg](bootcfg-timeout.md)
-   [break](break_1.md)

### <a name="BKMK_c"></a>C
-   [CACLS](cacls_1.md)
-   [Вызов](call.md)
-   [cd](cd.md)
-   [certreq](certreq_1.md)
-   [Certutil](certutil.md)
-   [Изменение](change.md)
  -   [изменить входа](change-logon.md)
  -   [Изменение порта](change-port.md)
  -   [изменить пользователя](change-user.md)
-   [chcp](chcp.md)
-   [ChDir](chdir_1.md)
-   [chglogon](chglogon.md)
-   [chgport](chgport.md)
-   [chgusr](chgusr.md)
-   [CHKDSK](chkdsk.md)
-   [chkntfs](chkntfs.md)
-   [Выбор](choice.md)
-   [Шифра](cipher.md)
-   [Клипов](clip.md)
-   [CLS](cls.md)
-   [cmd](Cmd.md)
-   [Программа cmdkey](cmdkey.md)
-   [cmstp](cmstp.md)
-   [Цвет](color.md)
-   [Зап.](comp.md)
-   [Compact](compact.md)
-   [Преобразовать](convert.md)
-   [копирование](copy.md)
-   [cprofile](cprofile.md)
-   [Cscript](cscript.md)

### <a name="BKMK_d"></a>D
-   [date](date.md)
-   [dcgpofix](dcgpofix.md)
-   [дефрагментации](defrag.md)
-   [DEL](del.md)
-   [DFSRMIG](dfsrmig.md)
-   [diantz](diantz.md)
-   [dir](dir.md)
-   [экран будет](diskcomp.md)
-   [diskcopy](diskcopy.md)
-   [DiskPart](diskpart.md)
-   [diskperf](diskperf.md)
-   [Diskraid](diskraid.md)
-   [DiskShadow](diskshadow.md)
-   [dispdiag](dispdiag.md)
-   [dnscmd](Dnscmd.md)
-   [Doskey](doskey.md)
-   [Неправильный](driverquery.md)

### <a name="BKMK_e"></a>E
-   [echo](echo.md)
-   [Изменить](edit.md)
-   [endlocal](endlocal.md)
-   [Стирание](erase.md)
-   [eventcreate](eventcreate.md)
-   [eventquery](eventquery.md)
-   [Eventtriggers](eventtriggers.md)
-   [evntcmd](Evntcmd.md)
-   [Выход](exit_2.md)
-   [Разверните узел](expand.md)
-   [извлечь](extract.md)

### <a name="BKMK_f"></a>F
-   [fc](fc.md)
-   [найти](find.md)
-   [findstr](findstr.md)
-   [пальцем](finger.md)
-   [flattemp](flattemp.md)
-   [fondue](fondue.md)
-   [для](for.md)
-   [forfiles](forfiles.md)
-   [Формат](format.md)
-   [freedisk](freedisk.md)
-   [fsutil](fsutil.md)
  -   [fsutil 8dot3name](fsutil-8dot3name.md) 
  -   [поведение fsutil](fsutil-behavior.md) 
  -   [файл fsutil](fsutil-file.md)
  -   [fsutil fsinfo](fsutil-fsinfo.md)
  -   [fsutil hardlink](fsutil-hardlink.md)
  -   [fsutil objectid](fsutil-objectid.md)
  -   [Квота fsutil](fsutil-quota.md)
  -   [fsutil repair](fsutil-repair.md)
  -   [fsutil reparsepoint](fsutil-reparsepoint.md)
  -   [fsutil ресурсов](fsutil-resource.md)
  -   [разреженных файлах fsutil](fsutil-sparse.md)
  -   [Распределение по уровням fsutil](fsutil-tiering.md)
  -   [транзакции fsutil](fsutil-transaction.md)
  -   [fsutil usn](fsutil-usn.md)
  -   [тома fsutil](fsutil-volume.md)
  -   [fsutil wim](fsutil-wim.md)
-   [FTP](ftp.md)
-   [ftype](ftype.md)
-   [fveupdate](fveupdate.md)

### <a name="BKMK_g"></a>G
-   [GETMAC](getmac.md)
-   [GetType](gettype.md)
-   [Оператор GoTo](goto.md)
-   [gpfixup](gpfixup.md)
-   [Gpresult](gpresult.md)
-   [gpupdate](gpupdate.md)
-   [graftabl](graftabl.md)

### <a name="BKMK_h"></a>H
-   [Справка](help.md)
-   [Команда helpctr](helpctr.md)
-   [Имя узла](hostname.md)

### <a name="BKMK_i"></a>Я
-   [icacls](icacls.md)
-   [If](if.md)
-   [может быть каталогом](inuse.md)
-   [ipconfig](ipconfig.md)
-   [ipxroute](ipxroute.md)
-   [irftp](irftp.md)

### <a name="BKMK_j"></a>J
-   [Jetpack](jetpack.md)

### <a name="BKMK_k"></a>K
-   [klist](klist.md)
-   [Ksetup](ksetup.md)
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
-   [KTMUTIL](ktmutil.md)
-   [ktpass](ktpass.md)

### <a name="BKMK_l"></a>L
-   [Метка](label.md)
-   [lodctr](lodctr.md)
-   [Logman](logman.md)
  -   [Создание Logman](logman-create.md)
  -   [Logman запроса](logman-query.md)
  -   [Logman start & 124; остановить](logman-start-stop.md)
  -   [Logman delete](logman-delete.md)
  -   [Logman update](logman-update.md)
  -   [Logman import & 124; Экспорт](logman-import-export.md)
-   [Выход из системы](logoff.md)
-   [lpq](lpq.md)
-   [LPR](lpr.md)

### <a name="BKMK_m"></a>M
-   [MacFile](macfile.md)
-   [makecab](makecab.md)
-   [Готов](manage-bde.md)
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
-   [MD](Md.md)
-   [mkdir](mkdir.md)
-   [mklink](mklink.md)
-   [MMC](mmc.md)
-   [mode](mode.md)
-   [Дополнительные](more.md)
-   [подключить](mount.md)
-   [mountvol](mountvol.md)
-   [Перемещение](move.md)
-   [Mqbkup](mqbkup.md)
-   [mqsvc](mqsvc.md)
-   [mqtgsvc](mqtgsvc.md)
-   [технической поддержки от Майкрософт](msdt.md)
-   [msg](msg.md)
-   [msiexec](msiexec.md)
-   [msinfo32](msinfo32.md)
-   [mstsc](mstsc.md)

### <a name="BKMK_n"></a>N
-   [nbtstat](nbtstat.md)
-   [netcfg](netcfg.md)
-   [netsh](netsh.md)
-   [netstat](netstat.md)
-   [NET печати](net-print.md)
-   [NFSAdmin](nfsadmin.md)
-   [nfsshare](nfsshare.md)
-   [nfsstat](nfsstat.md)
-   [nlbmgr](nlbmgr.md)
-   [Nslookup](nslookup.md)
  -   [выход команды nslookup](nslookup-exit-command.md)
  -   [Команда nslookup пальцем](nslookup-finger-command.md)
  -   [Nslookup справки](nslookup-help.md)
  -   [nslookup ls](nslookup-ls.md)
  -   [Nslookup lserver](nslookup-lserver.md)
  -   [корневой nslookup](nslookup-root.md)
  -   [nslookup server](nslookup-server.md)
  -   [набор nslookup](nslookup-set.md)
  -   [Nslookup, установить все](nslookup-set-all.md)
  -   [Класс set nslookup](nslookup-set-class.md)
  -   [nslookup set d2](nslookup-set-d2.md)
  -   [значение параметра debug nslookup](nslookup-set-debug.md)
  -   [Nslookup задайте домен](nslookup-set-domain.md)
  -   [Nslookup задать номер порта](nslookup-set-port.md)
  -   [nslookup set querytype](nslookup-set-querytype.md)
  -   [recurse набора nslookup](nslookup-set-recurse.md)
  -   [Nslookup набор повтора](nslookup-set-retry.md)
  -   [Nslookup задать корень](nslookup-set-root.md)
  -   [Поиск набора nslookup](nslookup-set-search.md)
  -   [nslookup set srchlist используется](nslookup-set-srchlist.md)
  -   [задать время ожидания nslookup](nslookup-set-timeout.md)
  -   [Тип набора nslookup](nslookup-set-type.md)
  -   [nslookup set vc](nslookup-set-vc.md)
  -   [представление nslookup](nslookup-view.md)
-   [Программа Ntbackup](ntbackup.md)
-   [ntcmdprompt](ntcmdprompt.md)
-   [ntfrsutl](ntfrsutl.md)

### <a name="BKMK_o"></a>O
-   [Openfiles](openfiles.md)

### <a name="BKMK_p"></a>P
-   [pagefileconfig](pagefileconfig.md)
-   [path](path.md)
-   [Pathping](pathping.md)
-   [Приостановка](pause.md)
-   [pbadmin](pbadmin.md)
-   [PENTNT](pentnt.md)
-   [Системный монитор](perfmon.md)
-   [Проверка связи](ping.md)
-   [pnpunattend](pnpunattend.md)
-   [PnPUtil](pnputil.md)
-   [popd](popd.md)
-   [PowerShell](PowerShell.md)
-   [PowerShell_ise](PowerShell_ise.md)
-   [Печать](print.md)
-   [prncnfg](prncnfg.md)
-   [prndrvr](prndrvr.md)
-   [prnjobs](prnjobs.md)
-   [prnmngr](prnmngr.md)
-   [prnport](prnport.md)
-   [prnqctl](prnqctl.md)
-   [Запрос](prompt.md)
-   [Pubprn](pubprn.md)
-   [PUSHD](pushd.md)
-   [PushPrinterConnections](pushprinterconnections.md)

### <a name="BKMK_q"></a>ВОПРОС:
-   [qappsrv](qappsrv.md)
-   [qprocess](qprocess.md)
-   [запрос](query.md)
-   [quser](quser.md)
-   [qwinsta](qwinsta.md)

### <a name="BKMK_r"></a>R
-   [rcp](rcp.md)
-   [к удаленному рабочему столу](rd.md)
-   [rdpsign](rdpsign.md)
-   [Восстановление](recover.md)
-   [REG](reg.md)
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
-   [REGINI](regini.md)
-   [regsvr32](regsvr32.md)
-   [повторной регистрации](relog.md)
-   [REM](rem.md)
-   [ren](ren.md)
-   [Переименование](rename.md)
-   [Repair-bde](repair-bde.md)
-   [Замените](replace.md)
-   [сбросить настройки сеанса](reset-session.md)
-   [rexec](rexec.md)
-   [Risetup](risetup.md)
-   [RmDir](rmdir.md)
-   [Robocopy](robocopy.md)
-   [route_ws2008](route_ws2008.md)
-   [rpcinfo](rpcinfo.md)
-   [RPCPing](rpcping.md)
-   [rsh](rsh.md)
-   [rundll32](rundll32.md)
-   [rwinsta](rwinsta.md)

### <a name="BKMK_s"></a>S
-   [SchTasks](schtasks.md)
-   [Scwcmd](Scwcmd.md)
  -   [Scwcmd: анализ](scwcmd-analyze.md)
  -   [Scwcmd: Настройка](scwcmd-configure.md)
  -   [Scwcmd: регистрация](scwcmd-register.md) 
  -   [Scwcmd: отката](scwcmd-rollback.md) 
  -   [Scwcmd: преобразование](scwcmd-transform.md) 
  -   [Scwcmd: представление](scwcmd-view.md) 
-   [Secedit](secedit.md)
  -   [Secedit: анализ](secedit-analyze.md)
  -   [Secedit: Настройка](secedit-configure.md)
  -   [Secedit:Export](secedit-export.md)
  -   [Secedit:generaterollback](secedit-generaterollback.md)
  -   [Secedit:import](secedit-import.md)
  -   [Secedit: проверка](secedit-validate.md)
-   [serverceipoptin](serverceipoptin.md)
-   [ServerManagerCmd](Servermanagercmd.md)
-   [serverweroptin](serverweroptin.md)
-   [Набор](set_1.md)
-   [SETLOCAL](setlocal.md)
-   [Setx](setx.md)
-   [Sfc](sfc.md)
-   [Тень](shadow.md)
-   [SHIFT](shift.md)
-   [showmount](showmount.md)
-   [Завершение работы](shutdown.md)
-   [Сортировка](sort.md)
-   [Запуск](start.md)
-   [SUBST](subst.md)
-   [sxstrace](sxstrace.md)
-   [команды sysocmgr](sysocmgr.md)
-   [SYSTEMINFO](systeminfo.md)

### <a name="BKMK_t"></a>T
-   [TAKEOWN](takeown.md)
-   [Tapicfg](tapicfg.md)
-   [Taskkill](taskkill.md)
-   [Список задач](tasklist.md)
-   [tcmsetup](tcmsetup.md)
-   [telnet](telnet.md)
-   [TFTP](tftp.md)
-   [время](time.md)
-   [время ожидания](timeout_1.md)
-   [Заголовок](title_1.md)
-   [tlntadmn](tlntadmn.md)
-   [tpmvscmgr](tpmvscmgr.md)
-   [Tracerpt](tracerpt_1.md)
-   [Tracert](tracert.md)
-   [Дерево](tree.md)
-   [tscon](tscon.md)
-   [tsdiscon](tsdiscon.md)
-   [Tsecimp](tsecimp_1.md)
-   [tskill](tskill.md)
-   [tsprof](tsprof.md)
-   [Тип](type.md)
-   [команды Typeperf](typeperf.md)
-   [tzutil](tzutil.md)

### <a name="BKMK_u"></a>U
-   [Unlodctr](unlodctr_1.md)

### <a name="BKMK_v"></a>V
-   [ver](ver.md)
-   [Средство проверки](verifier.md)
-   [Проверка](verify_1.md)
-   [VOL](vol.md)
-   [vssadmin](vssadmin.md)- 

### <a name="BKMK_w"></a>W
-   [WAITFOR](waitfor.md)
-   [WBADMIN](wbadmin.md)
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
-   [WDSUtil](wdsutil.md)
-   [wecutil](wecutil.md)
-   [wevtutil](wevtutil.md)
-   [where](where_1.md)
-   [whoami](whoami.md)
-   [Winnt](winnt.md)
-   [Winnt32](winnt32.md)
-   [winpop](winpop.md)
-   [Winrs](winrs.md)
-   [WLBS](wlbs_1.md)
-   [WMIC](wmic.md)
-   [WScript](wscript.md)

### <a name="BKMK_x"></a>X
-   [xcopy](xcopy.md)
