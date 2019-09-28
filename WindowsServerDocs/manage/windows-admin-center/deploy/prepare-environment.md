---
title: Подготовка среды для Windows Admin Center
description: Подготовка среды для Windows Admin Center (Project Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 06/07/2019
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 72e71ce2d1427f392aa02d32597f92d031f9a5c9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407001"
---
# <a name="prepare-your-environment-for-windows-admin-center"></a>Подготовка среды для Windows Admin Center

> Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Существует несколько версий Windows Server, которые требуют дополнительной подготовки, прежде чем ими можно будет управлять с помощью Windows Admin Center:

- [Windows Server 2012 и 2012 R2](#prepare-windows-server-2012-and-2012-r2)
- [Windows Server 2008 R2](#prepare-windows-server-2008-r2)
- [Microsoft Hyper-V Server 2016](#prepare-microsoft-hyper-v-server-2016)
- [Microsoft Hyper-V Server 2012 R2](#prepare-microsoft-hyper-v-server-2012-r2)

Существуют также некоторые сценарии, в которых [конфигурацию портов на целевом сервере](#port-configuration-on-the-target-server) может потребоваться изменить перед управлением с помощью центра администрирования Windows.

## <a name="prepare-windows-server-2012-and-2012-r2"></a>Подготовка Windows Server 2012 и 2012 R2

### <a name="install-wmf-version-51-or-higher"></a>Установка WMF версии 5.1 или более поздней версии

Для платформы Windows Admin Center нужны функции PowerShell, которые не входят в состав Windows Server 2012 и 2012 R2 по умолчанию. Для управления Windows Server 2012 или 2012 R2 с помощью Windows Admin Center необходимо установить WMF версии 5.1 или более поздней версии на эти серверы.

Введите `$PSVersiontable` в PowerShell, чтобы проверить, что платформа WMF установлена, и что используется версия 5.1 или более поздняя версия.

Если она не установлена, можно [скачать и установить WMF 5.1](https://docs.microsoft.com/powershell/wmf/setup/install-configure).

## <a name="prepare-windows-server-2008-r2"></a>Подготовка Windows Server 2008 R2

### <a name="install-wmf-version-51-or-higher"></a>Установка WMF версии 5.1 или более поздней версии

Для платформы Windows Admin Center нужны функции PowerShell, которые не входят в состав Windows Server 2008 R2 по умолчанию. Для управления Windows Server 2008 R2 с помощью Windows Admin Center необходимо установить WMF версии 5.1 или более поздней версии на эти серверы. 

Убедитесь, что на компьютере уже установлен [.NET Framework 4.5.2 или более поздней версии](https://docs.microsoft.com/dotnet/framework/install/on-windows-7) .

Введите `$PSVersiontable` в PowerShell, чтобы проверить, что платформа WMF установлена, и что используется версия 5.1 или более поздняя версия.

Если она не установлена, можно [скачать и установить WMF 5.1](https://docs.microsoft.com/powershell/wmf/setup/install-configure).

Выполните команду `Enable-PSRemoting –force` в консоли PowerShell для включения удаленного подключения PowerShell. 

### <a name="enable-remote-desktop"></a>Включение удаленного рабочего стола

Для использования удаленного рабочего стола в Windows Admin Center необходимо включить функцию "Удаленный рабочий стол" на сервере Windows Server 2008 R2.

В **Диспетчере серверов**выберите пункт **Настройка удаленного рабочего стола**. Включите для удаленного рабочего стола параметр "Разрешать подключения от компьютеров с любой версией удаленного рабочего стола".

## <a name="prepare-microsoft-hyper-v-server-2016"></a>Подготовка Microsoft Hyper-V Server 2016

Чтобы можно было управлять Microsoft Hyper-V Server 2016 с помощью Windows Admin Center, необходимо включить некоторые роли Windows Server.

### <a name="to-manage-microsoft-hyper-v-server-2016-with-windows-admin-center"></a>Для управления Microsoft Hyper-V Server 2016 с помощью Windows Admin Center выполните следующие действия.

1. Включите удаленное управление.
2. Включите роль файлового сервера.
3. Включение модуль Hyper-V для PowerShell.

### <a name="step-1-enable-remote-management"></a>**Шаг 1.** Включите удаленное управление

Для включения удаленного управления в Hyper-V Server выполните следующие действия.

1. Войдите в Hyper-V Server.
2. В средстве **Настройка сервера** (SCONFIG) введите **4**, чтобы настроить удаленное управление.
3. Введите **1**, чтобы включить удаленное управление.
4. Введите **4** для возврата в главное меню.

### <a name="step-2-enable-file-server-role"></a>**Шаг 2.** Включите роль файлового сервера

Чтобы включить роль файлового сервера для обеспечения базовых возможностей обмена файлами и удаленного управления, выполните следующие действия.

1. В меню **Сервис** выберите пункт **Роли и компоненты**.
2. В разделе **Роли и компоненты** найдите пункт **Файловые службы и службы хранилища** и установите флажки **Файловые службы и службы iSCSI** и **Файловый сервер**:

![Снимок экрана: роли и компоненты, отображающие выбранный файл и роль служб iSCSI](../media/prepare-environment/c6c30b812d96afcc1edcdb6f52f0e13c.png)

### <a name="step-3-enable-hyper-v-module-for-powershell"></a>**Шаг 3.** Включите модуль Hyper-V для PowerShell

Чтобы включить модуль Hyper-V для функций PowerShell, выполните следующие действия.

1. В меню **Сервис** выберите пункт **Роли и компоненты**.
2. В разделе **Роли и компоненты** найдите пункт **Средства удаленного администрирования сервера** и установите флажки **Средства администрирования ролей** и **Модуль Hyper-V для PowerShell**.

![Снимок экрана ролей и компонентов, в которых выбраны роли Hyper-V](../media/prepare-environment/7ab0999602b7083733525bd0c1ba2747.png)

Сервер Microsoft Hyper-V Server 2016 готов для управления с помощью Windows Admin Center.

## <a name="prepare-microsoft-hyper-v-server-2012-r2"></a>Подготовка Microsoft Hyper-V Server 2012 R2

Чтобы можно было управлять Microsoft Hyper-V Server 2012 R2 с помощью Windows Admin Center, необходимо включить некоторые роли Windows Server.  Кроме того, необходимо установить WMF версии 5.1 или более поздней версии.

### <a name="to-manage-microsoft-hyper-v-server-2012-r2-with-windows-admin-center"></a>Для управления Microsoft Hyper-V Server 2012 R2 с помощью Windows Admin Center выполните следующие действия.

1. Установите Windows Management Framework (WMF) версии 5.1 или более поздней версии
2. Включите удаленное управление
3. Включите роль файлового сервера
4. Включите модуль Hyper-V для PowerShell

### <a name="step-1-install-windows-management-framework-51"></a>Шаг 1. Установка Windows Management Framework 5,1

Для платформы Windows Admin Center нужны функции PowerShell, которые не входят в состав Microsoft Hyper-V Server 2012 R2 по умолчанию. Для управления Microsoft Hyper-V Server 2012 R2 с помощью Windows Admin Center необходимо установить WMF версии 5.1 или более поздней версии.

Введите `$PSVersiontable` в PowerShell, чтобы проверить, что платформа WMF установлена, и что используется версия 5.1 или более поздняя версия. 

Если она не установлена, вы можете [скачать WMF 5.1](https://docs.microsoft.com/powershell/wmf/setup/install-configure).

### <a name="step-2-enable-remote-management"></a>Шаг 2. Включите удаленное управление

Для включения удаленного управления Hyper-V Server выполните следующие действия.

1. Войдите в Hyper-V Server.
2. В средстве **Настройка сервера** (SCONFIG) введите **4**, чтобы настроить удаленное управление.
3. Введите **1**, чтобы включить удаленное управление.
4. Введите **4** для возврата в главное меню.

### <a name="step-3-enable-file-server-role"></a>Шаг 3. Включите роль файлового сервера

Чтобы включить роль файлового сервера для обеспечения базовых возможностей обмена файлами и удаленного управления, выполните следующие действия.

1. В меню **Сервис** выберите пункт **Роли и компоненты**.
2. В разделе **Роли и компоненты** найдите пункт **Файловые службы и службы хранилища** и установите флажки **Файловые службы и службы iSCSI** и **Файловый сервер**:

![Снимок экрана: роли и компоненты, отображающие выбранный файл и роль служб iSCSI](../media/prepare-environment/c6c30b812d96afcc1edcdb6f52f0e13c.png)

### <a name="step-4-enable-hyper-v-module-for-powershell"></a>Шаг 4. Включите модуль Hyper-V для PowerShell

Чтобы включить модуль Hyper-V для функций PowerShell, выполните следующие действия.

1. В меню **Сервис** выберите пункт **Роли и компоненты**.
2. В разделе **Роли и компоненты** найдите пункт **Средства удаленного администрирования сервера** и установите флажки **Средства администрирования ролей** и **Модуль Hyper-V для PowerShell**.

![Снимок экрана ролей и компонентов, в которых отображаются выбранные средства удаленного администрирования сервера Hyper-V](../media/prepare-environment/7ab0999602b7083733525bd0c1ba2747.png)

Теперь сервером Microsoft Hyper-V Server 2012 R2 можно управлять с помощью Windows Admin Center.

## <a name="port-configuration-on-the-target-server"></a>Конфигурация порта на целевом сервере

Центр администрирования Windows использует протокол общего доступа к файлам SMB для некоторых задач копирования файлов, например при импорте сертификата на удаленном сервере. Для успешности этих операций копирования файлов брандмауэр на удаленном сервере должен разрешать входящие подключения через порт 445.  Вы можете использовать средство брандмауэра в центре администрирования Windows, чтобы убедиться, что для входящего правила "удаленное управление файловым сервером (SMB-in)" задано разрешение доступа через этот порт.

> [!Tip]
> Готовы к установке Windows Admin Center? [Скачать](https://docs.microsoft.com/windows-server/manage/windows-admin-center/understand/windows-admin-center#download-now)
