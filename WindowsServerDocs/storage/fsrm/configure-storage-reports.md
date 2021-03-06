---
title: Настройка отчетов хранилища
description: В этой статье описывается процесс настройки параметров по умолчанию для отчетов хранилища
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 94d1b75bba4edac5ad8df80adb13d95a7b8dec39
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474161"
---
# <a name="configure-storage-reports"></a>Настройка отчетов хранилища

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

Для отчетов хранилища можно настраивать параметры по умолчанию. Эти параметры по умолчанию используются отчетами об инцидентах, которые создаются при возникновении события квоты или события фильтра блокировки файлов. Они также используются для отчетов по расписанию и по требованию, и при определении конкретных свойств этих отчетов параметры по умолчанию можно переопределить.

> [!Important]
> При изменении параметров по умолчанию для типа отчета изменения распространяются на все отчеты об инцидентах и любые существующие запланированные задачи отчетов, использующие эти параметры по умолчанию.

## <a name="to-configure-the-default-parameters-for-storage-reports"></a>Настройка параметров по умолчанию для отчетов хранилища

1. В древе консоли выберите **Диспетчер ресурсов файлового сервера** и выберите команду **Настроить параметры**. Откроется диалоговое окно **Параметры диспетчера ресурсов файлового сервера**.

2. На вкладке **Отчеты хранилища** в разделе **Настройка параметры по умолчанию** выберите тип отчета, который требуется изменить.

3. Нажмите кнопку **изменить параметры**.

4. В зависимости от выбранного типа отчета для редактирования будут доступны разные параметры отчета. Выполните все необходимые изменения и нажмите кнопку **ОК**, чтобы сохранить их в качестве параметров по умолчанию для выбранного типа отчета.

5.  Для всех редактируемых типов отчетов повторите шаги со 2 по 4.

6. Чтобы просмотреть список параметров по умолчанию для всех отчетов, нажмите **Просмотреть отчеты**. Затем нажмите кнопку **Закрыть**.

7.  Нажмите кнопку **ОК**.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Настройка параметров диспетчера ресурсов файлового сервера](setting-file-server-resource-manager-options.md)
-   [Управление отчетами хранилища](storage-reports-management.md)