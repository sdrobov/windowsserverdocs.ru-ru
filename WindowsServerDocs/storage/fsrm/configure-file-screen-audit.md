---
title: Настройка аудита фильтра блокировки файлов
description: В этой статье описывается процесс настройки аудита фильтра блокировки файлов для создания отчета аудита фильтра блокировки файлов
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: cf1824e514c34ee89870daa6d15190bffd822a8b
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85475321"
---
# <a name="configure-file-screen-audit"></a>Настройка аудита фильтра блокировки файлов

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

С помощью диспетчера ресурсов файлового сервера можно записывать действия фильтра блокировки файлов в базу данных аудита. Данные, хранящиеся в этой базе данных, используются для создания отчета аудита фильтра блокировки файлов.

> [!Important]
> Если флажок **Запись действий фильтра блокировки файлов в базу данных аудита** снят, отчеты аудита фильтра блокировки файлов не будут содержать никакие данные.

## <a name="to-configure-file-screen-audit"></a>Настройка аудита фильтра блокировки файлов

1.  В древе консоли выберите **Диспетчер ресурсов файлового сервера** и выберите команду **Настроить параметры**. Откроется диалоговое окно **Параметры диспетчера ресурсов файлового сервера**.

2.  На вкладке **Аудит фильтра блокировки файлов** установите флажок **Запись действий фильтра блокировки файлов в базу данных аудита**.

3.  Нажмите кнопку **ОК**. Все действия фильтра блокировки файлов будут сохраняться в базе данных аудита, и их можно будет просмотреть, сформировав отчет аудита фильтра блокировки файлов.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Настройка параметров диспетчера ресурсов файлового сервера](setting-file-server-resource-manager-options.md)
-   [Управление отчетами хранилища](storage-reports-management.md)