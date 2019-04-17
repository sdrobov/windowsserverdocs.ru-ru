---
title: Подготовка среды для Windows Admin Center
description: Подготовка среды для Windows Admin Center (Project Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/19/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 598eeae64925d24ec6d97b59da9cae1e2d10585d
ms.sourcegitcommit: 9ed4c9fe04ebf3ef488170503c9a354c992b6fde
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2018
ms.locfileid: "4339592"
---
# Подготовка среды для Windows Admin Center

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Существует несколько версий Windows Server, которые требуют дополнительной подготовки, прежде чем ими можно будет управлять с помощью Windows Admin Center:

- [Windows Server 2012 и 2012 R2](#prepare-windows-server-2012-and-2012-r2)
- [Windows Server2008 R2](#prepare-windows-server-2008-r2)
- [Microsoft Hyper-V Server 2016](#prepare-microsoft-hyper-v-server-2016)
- [Microsoft Hyper-V Server 2012 R2](#prepare-microsoft-hyper-v-server-2012-r2)

## Подготовка Windows Server 2012 и 2012 R2

### Установка WMF версии 5.1 или более поздней версии

Для платформы Windows Admin Center нужны функции PowerShell, которые не входят в состав Windows Server 2012 и 2012 R2 по умолчанию. Для управления Windows Server 2012 или 2012 R2 с помощью Windows Admin Center необходимо установить WMF версии 5.1 или более поздней версии на эти серверы.

Введите `$PSVersiontable` в PowerShell, чтобы проверить, что платформа WMF установлена, и что используется версия 5.1 или более поздняя версия.

Если она не установлена, можно [скачать и установить WMF 5.1](https://docs.microsoft.com/powershell/wmf/5.1/install-configure).

## Подготовка Windows Server 2008 R2

### Установка WMF версии 5.1 или более поздней версии

Для платформы Windows Admin Center нужны функции PowerShell, которые не входят в состав Windows Server 2008 R2 по умолчанию. Для управления Windows Server 2008 R2 с помощью Windows Admin Center необходимо установить WMF версии 5.1 или более поздней версии на эти серверы. 

Убедитесь, что [.NET Framework 4.5.2 или более поздней версии](https://docs.microsoft.com/dotnet/framework/install/on-windows-7) уже установлено на компьютере.

Введите `$PSVersiontable` в PowerShell, чтобы убедиться, что платформа WMF установлена, и что используется версия 5.1 или более поздняя версия.

Если она не установлена, можно [скачать и установить WMF 5.1](https://docs.microsoft.com/powershell/wmf/5.1/install-configure).

Выполните команду `Enable-PSRemoting –force` в консоли PowerShell для включения удаленного подключения PowerShell. 

### Включение удаленного рабочего стола

Для использования удаленного рабочего стола в Windows Admin Center необходимо включить функцию "Удаленный рабочий стол" на сервере Windows Server 2008 R2.

В **Диспетчере серверов**выберите пункт **Настройка удаленного рабочего стола**. Включите для удаленного рабочего стола параметр "Разрешать подключения от компьютеров с любой версией удаленного рабочего стола".

## Подготовка Microsoft Hyper-V Server 2016

Чтобы можно было управлять Microsoft Hyper-V Server 2016 с помощью Windows Admin Center, необходимо включить некоторые роли Windows Server.

### Для управления Microsoft Hyper-V Server 2016 с помощью Windows Admin Center выполните следующие действия.

1. Включите удаленное управление.
2. Включите роль файлового сервера.
3. Включение модуль Hyper-V для PowerShell.

### **Шаг 1.** Включение удаленного управления

Для включения удаленного управления в Hyper-V Server выполните следующие действия.

1. Войдите в Hyper-V Server.
2. В средстве **Настройка сервера** (SCONFIG) введите **4**, чтобы настроить удаленное управление.
3. Введите **1**, чтобы включить удаленное управление.
4. Введите **4** для возврата в главное меню.

### **Шаг 2.** Включение роли файлового сервера

Чтобы включить роль файлового сервера для обеспечения базовых возможностей обмена файлами и удаленного управления, выполните следующие действия.

1. В меню **Сервис** выберите пункт **Роли и компоненты**.
2. В разделе **Роли и компоненты** найдите пункт **Файловые службы и службы хранилища** и установите флажки **Файловые службы и службы iSCSI** и **Файловый сервер**:

![](../media/prepare-environment/c6c30b812d96afcc1edcdb6f52f0e13c.png)

### **Шаг 3.** Включение модуля Hyper-V для PowerShell

Чтобы включить модуль Hyper-V для функций PowerShell, выполните следующие действия.

1. В меню **Сервис** выберите пункт **Роли и компоненты**.
2. В разделе **Роли и компоненты** найдите пункт **Средства удаленного администрирования сервера** и установите флажки **Средства администрирования ролей** и **Модуль Hyper-V для PowerShell**.

![](../media/prepare-environment/7ab0999602b7083733525bd0c1ba2747.png)

Сервер Microsoft Hyper-V Server 2016 готов для управления с помощью Windows Admin Center.

## Подготовка Microsoft Hyper-V Server 2012 R2

Чтобы можно было управлять Microsoft Hyper-V Server 2012 R2 с помощью Windows Admin Center, необходимо включить некоторые роли Windows Server.  Кроме того, необходимо установить WMF версии 5.1 или более поздней версии.

### Для управления Microsoft Hyper-V Server 2012 R2 с помощью Windows Admin Center выполните следующие действия.

1. Установите Windows Management Framework (WMF) версии 5.1 или более поздней версии
2. Включите удаленное управление
3. Включите роль файлового сервера
4. Включите модуль Hyper-V для PowerShell

### **Шаг 1.** Установка Windows Management Framework 5.1

Для платформы Windows Admin Center нужны функции PowerShell, которые не входят в состав Microsoft Hyper-V Server 2012 R2 по умолчанию. Для управления Microsoft Hyper-V Server 2012 R2 с помощью Windows Admin Center необходимо установить WMF версии 5.1 или более поздней версии.

Введите `$PSVersiontable` в PowerShell, чтобы убедиться, что платформа WMF установлена, и что используется версия 5.1 или более поздняя версия. 

Если она не установлена, вы можете [скачать WMF 5.1](https://docs.microsoft.com/powershell/wmf/5.1/install-configure).

### **Шаг 2.** Включение удаленного управления 

Для включения удаленного управления Hyper-V Server выполните следующие действия.

1. Войдите в Hyper-V Server.
2. В средстве **Настройка сервера** (SCONFIG) введите **4**, чтобы настроить удаленное управление.
3. Введите **1**, чтобы включить удаленное управление.
4. Введите **4** для возврата в главное меню.

### Шаг 3. Включение роли файлового сервера

Чтобы включить роль файлового сервера для обеспечения базовых возможностей обмена файлами и удаленного управления, выполните следующие действия.

1. В меню **Сервис** выберите пункт **Роли и компоненты**.
2. В разделе **Роли и компоненты** найдите пункт **Файловые службы и службы хранилища** и установите флажки **Файловые службы и службы iSCSI** и **Файловый сервер**:

![](../media/prepare-environment/c6c30b812d96afcc1edcdb6f52f0e13c.png)

### Шаг 4. Включение модуля Hyper-V для PowerShell ##

Чтобы включить модуль Hyper-V для функций PowerShell, выполните следующие действия.

1. В меню **Сервис** выберите пункт **Роли и компоненты**.
2. В разделе **Роли и компоненты** найдите пункт **Средства удаленного администрирования сервера** и установите флажки **Средства администрирования ролей** и **Модуль Hyper-V для PowerShell**.

![](../media/prepare-environment/7ab0999602b7083733525bd0c1ba2747.png)

Теперь сервером Microsoft Hyper-V Server 2012 R2 можно управлять с помощью Windows Admin Center.

> [!Tip]
> Готовы к установке Windows Admin Center? [Скачать](https://docs.microsoft.com/windows-server/manage/windows-admin-center/understand/windows-admin-center#download-now)