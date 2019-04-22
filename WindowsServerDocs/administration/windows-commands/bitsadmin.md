---
title: bitsadmin
description: Раздел Windows команды для **bitsadmin** -bitsadmin является средством командной строки, которое можно использовать для создания, загрузки, или отправить задания и отслеживать ход их выполнения.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4853036e-1df8-45ad-8be6-cfb097b8dd27
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: da0f05ec716cffb7d7532ebac50a091729a6bb18
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821075"
---
# <a name="bitsadmin"></a>bitsadmin

> **Применяется к**: Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows 10

bitsadmin является средством командной строки, которое можно использовать для создания загрузки или отправки заданий и отслеживать ход их выполнения. Средство bitsadmin использует параметры для определения работы для выполнения.  Можно вызвать `bitsadmin /?` или `bitsadmin /HELP` для получения списка параметров.

Большинство коммутаторов требует \<задания\> параметр, который установлен для задания отображаемое имя или идентификатор GUID. Обратите внимание на то, что отображаемое имя задания могут быть неуникальными. **/ Create** и **/list** коммутаторы возвращают идентификатор GUID задания.

По умолчанию доступны сведения о пользовательских заданий. Для доступа к информации для задания другого пользователя, требуются права администратора. Если задание создано в состоянии с повышенными правами, затем необходимо запустить bitsadmin из окно с повышенными привилегиями; в противном случае будет иметь доступ только для чтения к заданию.

Многие параметры, соответствующие методам в [интерфейсы BITS](/windows/desktop/bits/bits-interfaces). Подробные сведения, которые можно применять с помощью ключа см. в разделе соответствующего метода.

Используйте перечисленные ниже параметры для создания задания, задание и получение свойств задания и отслеживать состояние задания. Примеры, показывающие, как использовать некоторые из этих параметров для выполнения задач, см. в разделе [bitsadmin примеры](bitsadmin-examples.md).

## <a name="switches"></a>Коммутаторы

[bitsadmin addfile](bitsadmin-addfile.md)  
[bitsadmin addfileset](bitsadmin-addfileset.md)  
[bitsadmin addfilewithranges](bitsadmin-addfilewithranges.md)  
[bitsadmin кэша](bitsadmin-cache.md)  
[Отмена bitsadmin](bitsadmin-cancel.md)  
[Полный bitsadmin](bitsadmin-complete.md)  
[Создание bitsadmin](bitsadmin-create.md)  
[bitsadmin getaclflags](bitsadmin-getaclflags.md)  
[bitsadmin getbytestotal](bitsadmin-getbytestotal.md)  
[bitsadmin getbytestransferred](bitsadmin-getbytestransferred.md)  
[bitsadmin getclientcertificate](bitsadmin-getclientcertificate.md)  
[bitsadmin getcompletiontime](bitsadmin-getcompletiontime.md)  
[bitsadmin getcreationtime](bitsadmin-getcreationtime.md)  
[bitsadmin getcustomheaders](bitsadmin-getcustomheaders.md)  
[bitsadmin getdescription](bitsadmin-getdescription.md)  
[bitsadmin getdisplayname](bitsadmin-getdisplayname.md)  
[bitsadmin geterror](bitsadmin-geterror.md)  
[bitsadmin geterrorcount](bitsadmin-geterrorcount.md)  
[bitsadmin getfilestotal](bitsadmin-getfilestotal.md)  
[bitsadmin getfilestransferred](bitsadmin-getfilestransferred.md)  
[bitsadmin gethelpertokenflags](bitsadmin-gethelpertokenflags.md)  
[bitsadmin gethelpertokensid](bitsadmin-gethelpertokensid.md)  
[bitsadmin gethttpmethod](bitsadmin-gethttpmethod.md)
[bitsadmin getmaxdownloadtime](bitsadmin-getmaxdownloadtime.md)  
[bitsadmin getminretrydelay](bitsadmin-getminretrydelay.md)  
[bitsadmin getmodificationtime](bitsadmin-getmodificationtime.md)  
[bitsadmin getnoprogresstimeout](bitsadmin-getnoprogresstimeout.md)  
[bitsadmin getnotifycmdline](bitsadmin-getnotifycmdline.md)  
[bitsadmin getnotifyflags](bitsadmin-getnotifyflags.md)  
[bitsadmin getnotifyinterface](bitsadmin-getnotifyinterface.md)  
[bitsadmin getowner](bitsadmin-getowner.md)  
[bitsadmin getpeercachingflags](bitsadmin-getpeercachingflags.md)  
[bitsadmin getpriority](bitsadmin-getpriority.md)  
[bitsadmin getproxybypasslist](bitsadmin-getproxybypasslist.md)  
[bitsadmin getproxylist](bitsadmin-getproxylist.md)  
[bitsadmin getproxyusage](bitsadmin-getproxyusage.md)  
[bitsadmin getreplydata](bitsadmin-getreplydata.md)  
[bitsadmin getreplyfilename](bitsadmin-getreplyfilename.md)  
[bitsadmin getreplyprogress](bitsadmin-getreplyprogress.md)  
[bitsadmin getsecurityflags](bitsadmin-getsecurityflags.md)  
[bitsadmin getstate](bitsadmin-getstate.md)  
[bitsadmin gettemporaryname](bitsadmin-gettemporaryname.md)  
[bitsadmin gettype](bitsadmin-gettype.md)  
[bitsadmin getvalidationstate](bitsadmin-getvalidationstate.md)  
[bitsadmin справки](bitsadmin-help.md)  
[сведения о bitsadmin](bitsadmin-info.md)  
[Список bitsadmin](bitsadmin-list.md)  
[bitsadmin listfiles](bitsadmin-listfiles.md)  
[bitsadmin makecustomheaderswriteonly](bitsadmin-makecustomheaderswriteonly.md)
[bitsadmin монитора](bitsadmin-monitor.md)  
[bitsadmin nowrap](bitsadmin-nowrap.md)  
[bitsadmin кэширования](bitsadmin-peercaching.md)  
[одноранговые узлы bitsadmin](bitsadmin-peers.md)  
[bitsadmin rawreturn](bitsadmin-rawreturn.md)  
[bitsadmin removeclientcertificate](bitsadmin-removeclientcertificate.md)  
[bitsadmin removecredentials](bitsadmin-removecredentials.md)  
[bitsadmin replaceremoteprefix](bitsadmin-replaceremoteprefix.md)  
[Сброс bitsadmin](bitsadmin-reset.md)  
[Возобновление bitsadmin](bitsadmin-resume.md)  
[bitsadmin setaclflag](bitsadmin-setaclflag.md)  
[bitsadmin setclientcertificatebyid](bitsadmin-setclientcertificatebyid.md)  
[bitsadmin setclientcertificatebyname](bitsadmin-setclientcertificatebyname.md)  
[bitsadmin setcredentials](bitsadmin-setcredentials.md)  
[bitsadmin setcustomheaders](bitsadmin-setcustomheaders.md)  
[bitsadmin setdescription](bitsadmin-setdescription.md)  
[bitsadmin setdisplayname](bitsadmin-setdisplayname.md)  
[bitsadmin sethelpertoken](bitsadmin-sethelpertoken.md)  
[bitsadmin sethelpertokenflags](bitsadmin-sethelpertokenflags.md)  
[bitsadmin sethttpmethod](bitsadmin-sethttpmethod.md)
[bitsadmin setmaxdownloadtime](bitsadmin-setmaxdownloadtime.md)  
[bitsadmin setminretrydelay](bitsadmin-setminretrydelay.md)  
[bitsadmin setnoprogresstimeout](bitsadmin-setnoprogresstimeout.md)  
[bitsadmin setnotifycmdline](bitsadmin-setnotifycmdline.md)  
[bitsadmin setnotifyflags](bitsadmin-setnotifyflags.md)  
[bitsadmin setpeercachingflags](bitsadmin-setpeercachingflags.md)  
[bitsadmin setpriority](bitsadmin-setpriority.md)  
[bitsadmin setproxysettings](bitsadmin-setproxysettings.md)  
[bitsadmin setreplyfilename](bitsadmin-setreplyfilename.md)  
[bitsadmin setsecurityflags](bitsadmin-setsecurityflags.md)  
[bitsadmin setvalidationstate](bitsadmin-setvalidationstate.md)  
[Приостановка bitsadmin](bitsadmin-suspend.md)  
[bitsadmin takeownership](bitsadmin-takeownership.md)  
[Передача bitsadmin](bitsadmin-transfer.md)  
[bitsadmin util](bitsadmin-util.md)  
[bitsadmin переноса по словам](bitsadmin-wrap.md)  
