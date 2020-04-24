---
title: Перенос ролей и компонентов
description: Сведения о том, как перенести роли и компоненты в более новую версию Windows Server.
ms.prod: windows-server
ms.date: 08/28/2019
ms.technology: server-general
ms.topic: article
ms.assetid: 0f78ef4c-dd12-4b1b-8c6e-251dd803c5d1
author: jasongerend
ms.author: jgerend
manager: dougkim
ms.localizationpriority: medium
ms.openlocfilehash: 33c1aa654e4c660b4fe2f3305bfaf78b5191220a
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2020
ms.locfileid: "70119202"
---
# <a name="migrating-roles-and-features-in-windows-server"></a>Миграция ролей и компонентов в Windows Server

> Применяется к: Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Эта страница содержит ссылки на информацию и инструменты, которые помогут вам в процессе переноса ролей и компонентов в более новую версию Windows Server. Вы можете перенести файловые серверы и хранилище с помощью [службы миграции хранилища](../storage/storage-migration-service/overview.md), в то время как многие другие роли и компоненты можно перенести с помощью средств миграции Windows Server. Это набор командлетов PowerShell, которые были введены в Windows Server 2008 R2 для переноса ролей и компонентов.

Руководства по миграции охватывают перенос определенных ролей и компонентов с одного сервера на другой (не обновление на месте). Если в руководствах не указано иное, поддерживается перенос между физическими и виртуальными компьютерами, а также между серверами Windows Server, для которых была выполнена полная установка, и серверами, для которых была выполнена только установка основных серверных компонентов.

## <a name="before-you-begin"></a>Перед началом работы

Перед началом переноса ролей и компонентов убедитесь, что исходный и целевой серверы работают под управлением операционных систем с последними пакетами обновления, которые для них доступны. 

> [!NOTE]
> При миграции или обновлении до любой версии Windows Server следует просмотреть и понять [политику сроков поддержки](https://support.microsoft.com/lifecycle) и период времени для этой версии и плана соответственно. Вы можете [найти информацию о сроках](https://support.microsoft.com/lifecycle) для определенного выпуска Windows Server, который вас интересуют.

## <a name="windows-server-2019"></a>Windows Server 2019

Для переноса файловых серверов и хранилища на Windows Server 2019 или Windows Server 2016 рекомендуется использовать [службу миграции хранилища](../storage/storage-migration-service/overview.md). Сведения о переносе других ролей приведены в руководстве по Windows Server 2016 и Windows Server 2012 R2.

## <a name="windows-server-2016"></a>Windows Server 2016

Ниже приведены руководства по миграции для Windows Server 2016. Обратите внимание на то, что во многих случаях можно также использовать руководства по миграции для Windows Server 2012 R2.

- [Службы удаленных рабочих столов](https://technet.microsoft.com/windows-server-docs/compute/remote-desktop-services/migrate-rds-role-services)
- [Веб-сервер (IIS)](https://www.iis.net/downloads/microsoft/web-deploy)
- [Службы Windows Server Update Services](https://technet.microsoft.com/library/hh852339.aspx)
- [Службы MultiPoint](https://technet.microsoft.com/windows-server-docs/compute/remote-desktop-services/multipoint-services/multipoint-services-migrate)

Для переноса файловых серверов в Windows Server 2019 или Windows Server 2016 рекомендуется использовать [службу миграции хранилища](../storage/storage-migration-service/overview.md).

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

Следуйте инструкциям в этих руководствах для переноса ролей и компонентов с серверов под управлением Windows Server 2003, Windows Server 2008, Windows Server 2008 R2, Windows Server 2012 или Windows Server 2012 R2 на Windows Server 2012 R2. Средства миграции Windows Server в Windows Server 2012 R2 поддерживают перенос между различными подсетями.

- [Установка, использование и удаление средств миграции Windows Server](https://technet.microsoft.com/library/jj134202.aspx)
- [Руководство по переносу служб сертификатов Active Directory для Windows Server 2012 R2](https://technet.microsoft.com/library/dn486797.aspx)
- [Перенос службы роли служб федерации Active Directory в Windows Server 2012 R2](https://technet.microsoft.com/library/dn486815.aspx)
- [Руководство по обновлению и переносу служб управления правами Active Directory](https://technet.microsoft.com/library/cc754277.aspx)
- [Перенос файловых служб и служб хранилища в Windows Server 2012 R2](https://technet.microsoft.com/library/dn479292.aspx)
- [Перенос Hyper-V в Windows Server 2012 R2 с Windows Server 2012](https://technet.microsoft.com/library/dn486799.aspx)
- [Перенос сервера политики сети в Windows Server 2012](https://technet.microsoft.com/library/hh831652)
- [Перенос служб удаленных рабочих столов в Windows Server 2012 R2](https://technet.microsoft.com/library/dn479239.aspx)
- [Перенос служб обновления Windows Server Update Services в Windows Server 2012 R2](https://technet.microsoft.com/library/hh852339.aspx)
- [Перенос кластерных ролей в Windows Server 2012 R2](https://technet.microsoft.com/library/dn530779.aspx)
- [Перенос DHCP-сервера в Windows Server 2012 R2](https://technet.microsoft.com/library/dn495425.aspx)

Теперь доступна электронная книга руководства по миграции Windows Server 2012 R2 и Windows Server 2012. Чтобы получить дополнительные сведения и скачать электронную книгу, ознакомьтесь с [коллекцией электронных книг по технологиям Майкрософт](https://social.technet.microsoft.com/wiki/contents/articles/11608.e-book-gallery-for-microsoft-technologies.aspx#MigrateRoles).

## <a name="windows-server-2012"></a>Windows Server 2012

Следуйте инструкциям в этих руководствах для переноса ролей и компонентов с серверов под управлением Windows Server 2003, Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012 на Windows Server 2012. Средства миграции Windows Server в Windows Server 2012 поддерживают перенос между различными подсетями.

- [Установка, использование и удаление средств миграции Windows Server](https://technet.microsoft.com/library/jj134202)
- [Перенос служб ролей для служб федерации Active Directory в Windows Server 2012](https://technet.microsoft.com/library/jj647765)
- [Перенос центра регистрации работоспособности в Windows Server 2012](https://technet.microsoft.com/library/hh831513)
- [Перенос Hyper-V на Windows Server 2012 с Windows Server 2008 R2](https://technet.microsoft.com/library/jj574113)
- [Перенос IP-конфигурации в Windows Server 2012](https://technet.microsoft.com/library/jj574133)
- [Перенос сервера политики сети в Windows Server 2012](https://technet.microsoft.com/library/hh831652)
- [Перенос служб печати и документов в Windows Server 2012](https://technet.microsoft.com/library/jj134150)
- [Перенос удаленного доступа в Windows Server 2012](https://technet.microsoft.com/library/hh831423)
- [Перенос служб обновления Windows Server Update Services в Windows Server 2012](https://technet.microsoft.com/library/hh852339)
- [Обновление контроллеров домена Active Directory до Windows Server 2012](https://technet.microsoft.com/library/hh994618.aspx)
- [Перенос кластеризованных служб и приложений в Windows Server 2012](https://technet.microsoft.com/library/dn486790.aspx)
 

Для получения дополнительных материалов по миграции ознакомьтесь с разделом [Перенос ролей и компонентов на Windows Server](https://technet.microsoft.com/library/jj134039).

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

Следуйте инструкциям в этих руководствах для переноса ролей и компонентов с серверов под управлением Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2 на Windows Server 2008 R2. Средства миграции Windows Server в Windows Server 2008 R2 не поддерживают перенос между различными подсетями.

- [Установка средств миграции Windows Server, доступ к ним и удаление](https://technet.microsoft.com/library/dd379545)
- [Руководство по переносу служб сертификатов Active Directory](https://technet.microsoft.com/library/ee126170)
- [Руководство по переносу служб домена Active Directory и DNS-сервера](https://technet.microsoft.com/library/dd379558)
- [Руководство по переносу BranchCache](https://technet.microsoft.com/library/dd548365)
- [Руководство по переносу DHCP-сервера](https://technet.microsoft.com/library/dd379535)
- [Руководство по переносу файловых служб](https://technet.microsoft.com/library/dd379487)
- [Руководство по переносу HRA](https://technet.microsoft.com/library/ee791829)
- [Руководство по переносу Hyper-V](https://technet.microsoft.com/library/ee849855)
- [Руководство по переносу IP-конфигурации](https://technet.microsoft.com/library/dd379537)
- [Руководство по переносу группы и локальных пользователей](https://technet.microsoft.com/library/dd379531)
- [Руководство по переносу NPS](https://technet.microsoft.com/library/ee791849)
- [Руководство по переносу служб печати](https://technet.microsoft.com/library/dd379488)
- [Руководство по переносу служб удаленных рабочих столов](https://technet.microsoft.com/library/ff849223)
- [Руководство по переносу RRAS](https://technet.microsoft.com/library/ee822825)
- [Общие сведения и задачи миграции Windows Server](https://technet.microsoft.com/library/ff400258)
- [Руководство по переносу служб Windows Server Update 3.0 с пакетом обновления 2 (SP2)](https://technet.microsoft.com/library/ee822826)
 
Для получения дополнительных материалов по миграции ознакомьтесь с разделом [Migrate Server Roles to Windows Server 2008 R2](https://technet.microsoft.com/library/dd365353) (Перенос ролей и компонентов в Windows Server 2008 R2).
