---
title: Использование очистки диска на Windows Server
description: Узнайте, как использовать параметры командной строки для настройки средства очистки диска (Cleanmgr.exe), чтобы автоматически удалять определенные файлы.
ms.prod: windows-server
ms.reviewer: cosmosdarwin
author: iangpgh
ms.author: jgerend
manager: daveba
ms.technology: storage-spaces
ms.date: 06/20/2019
ms.openlocfilehash: bb93ec15fd138ee65797c9d27413552c3a1759a6
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2020
ms.locfileid: "75949672"
---
# <a name="using-disk-cleanup-on-windows-server"></a>Использование очистки диска на Windows Server

> Применяется к: Windows Server 2019, Windows Server 2016, Windows Server 2016 R2, Windows Server 2012, Windows Server 2012 R2

Средство очистки диска удаляет ненужные файлы в среде Windows Server. Это средство доступно по умолчанию в Windows Server 2019 и Windows Server 2016, но в более ранних версиях Windows Server могут потребоваться дополнительные действия вручную для его включения.

Чтобы запустить средство очистки диска, выполните команду cleanmgr.exe или последовательно выберите **Пуск**, **Средства администрирования Windows**, **Очистка диска**.

Кроме того, средство очистки диска можно запустить командой Windows [cleanmgr](../../administration/windows-commands/cleanmgr.md), указав в параметрах командной строки параметры для удаления определенных файлов.

## <a name="enable-disk-cleanup-on-an-earlier-version-of-windows-server-by-installing-the-desktop-experience"></a>Включение очистки диска в более ранней версии Windows Server с помощью установки возможности рабочего стола

Выполните описанные ниже действия, чтобы использовать мастер добавления ролей и компонентов для установки возможностей рабочего стола на сервере под управлением Windows Server 2012 R2 или более ранней версии, в составе которых устанавливается и средство очистки диска.

1. Если диспетчер серверов уже открыт, переходите к следующему шагу. Если диспетчер серверов еще не открыт, откройте его одним из следующих способов.

   - На рабочем столе Windows запустите диспетчер серверов, щелкнув **Диспетчер серверов** на панели задач Windows.

   - Откройте **Начальный экран** и щелкните плитку "Диспетчер сервера".

1. В меню **Управление** выберите **добавление ролей и компонентов**.

1. На странице **Прежде чем приступить к работе** проверьте готовность конечного сервера и сетевого окружения к установке нужного компонента. Выберите **Далее**.

1. На странице **Выбор типа установки** выберите **Установка ролей или компонентов**, чтобы установить все компоненты для отдельного сервера. Выберите **Далее**.

1. На странице **Выбор целевого сервера** выберите сервер из пула серверов или автономный виртуальный жесткий диск. Выберите **Далее**.

1. На странице **Выбор ролей сервера** щелкните **Далее**.

1. На странице **Выбор компонентов** выберите элемент **Пользовательский интерфейс и инфраструктура**, а затем — **Возможности рабочего стола**.

1. В диалоговом окне **Добавление компонентов, необходимых для возможностей рабочего стола** щелкните элемент **Добавить компоненты**.

1. Продолжите установку, затем перезагрузите систему.

1. Убедитесь, что в диалоговом окне "Свойства" появилась кнопка **Очистка диска**.

   ![Диалоговое окно "Свойства диска" с параметром "Очистка диска"](media/diskpropswcleanup.png)

## <a name="manually-add-disk-cleanup-to-an-earlier-version-of-windows-server"></a>Добавление средства очистки диска вручную на более ранних версиях Windows Server

Средство очистки диска (Cleanmgr.exe) отсутствует в Windows Server 2012 R2 и более ранних версиях, если не установлен дополнительный компонент "Возможности рабочего стола".

Чтобы использовать программу cleanmgr.exe, установите возможности рабочего стола, как описано выше, или скопируйте два файла cleanmgr.exe и cleanmgr.exe.mui, которые уже имеются на сервере. С помощью следующей таблицы выберите нужные файлы для используемой операционной системы.

| Операционная система  | Архитектура  | Расположение файла  |
| ----------------- | -------------- | --------------- |
| Windows Server 2008 R2 | 64-разрядная | C:\Windows\winsxs\amd64_microsoft-windows-cleanmgr_31bf3856ad364e35_6.1.7600.16385_none_c9392808773cd7da\cleanmgr.exe 
| Windows Server 2008 R2 | 64-разрядная | C:\Windows\winsxs\amd64_microsoft-windows-cleanmgr.resources_31bf3856ad364e35_6.1.7600.16385_en-us_b9cb6194b257cc63\cleanmgr.exe.mui |

Найдите файл cleanmgr.exe и переместите его в папку **%systemroot%\System32**.

Найдите файл cleanmgr.exe.mui и переместите его в папку **%systemroot%\System32\en-US**.

Теперь вы можете запустить средство очистки диска, выполнив команду Cleanmgr.exe из командной строки, или открыв **начальный экран** и набрав строку **Cleanmgr** на панели поиска.

Чтобы в диалоговом окне "Свойства" для диска появилась кнопка "Очистка диска", необходимо установить компонент "Возможности рабочего стола".

## <a name="additional-references"></a>Дополнительная справка

[Освобождение места на диске в Windows 10](https://support.microsoft.com/help/12425/windows-10-free-up-drive-space)

[cleanmgr](../../administration/windows-commands/cleanmgr.md)
