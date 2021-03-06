---
title: Создание квоты
description: В этой статье описывается процесс создания квоты на основе шаблона
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: b3513510ef00eec7ea78a3193cf44c25ddb17c7e
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85475221"
---
# <a name="create-a-quota"></a>Создание квоты

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

Квоты можно создать на основе шаблона или с помощью пользовательских свойств. Далее приведено описание процесса создания квоты на основе шаблона (рекомендуется). Если вам необходимо создать квоту с настраиваемыми свойствами, эти свойства можно сохранить в качестве шаблона для повторного использования в будущем.

При создании квоты необходимо выбрать путь квоты, представляющий собой том или папку, к которым применяется ограничение хранилища. Для выбранного пути квоты можно использовать шаблон, чтобы создать квоту одного из следующих типов.

-   Отдельная квота, которая ограничивает пространство для всего тома или папки.
-   Автоматически применяемая квота, которая назначает шаблон квоты папке или тому. Квоты на основе этого шаблона автоматически создаются и применяются ко всем вложенным папкам. Дополнительные сведения о создании автоматически применяемых квот см. в разделе [Создание автоматически применяемой квоты](create-auto-apply-quota.md).


> [!Note]
> Создавая квоты исключительно на основе шаблонов, можно централизованно управлять квотами путем обновления шаблонов вместо отдельных квот. Затем можно применить изменения ко всем квотам на основе измененного шаблона. Данная функция упрощает реализацию изменений политики хранения за счет возможности централизованного обновления.

## <a name="to-create-a-quota-that-is-based-on-a-template"></a>Создание квоты на основе шаблона

1.  В окне **Управление квотами** щелкните узел **Шаблоны квот**.

2.  На панели "Результаты" выберите шаблон, на основе которого будет создана новая квота.

3.  Щелкните правой кнопкой мыши шаблон и выберите **Создать квоту на основе шаблона** (или выберите действие **Создать квоту на основе шаблона** на панели **Действия**). Откроется диалоговое окно **Создание квоты** со списком свойств отображаемого шаблона квоты.

4.  В разделе **Путь квоты**введите путь или перейдите к папке, к которой будет применяться квота.

5.  Нажмите кнопку **Создать квоту для пути**. Обратите внимание, что свойства квоты будут применяться ко всей папке.

     > [!Note]
     > Для создания автоматически применяемой квоты нажмите кнопку **Автоматически применять шаблон для создания квот на существующих и новых вложенных папках**. Дополнительные сведения о создании автоматически применяемых квот см. в разделе [Создание автоматически применяемой квоты](create-auto-apply-quota.md).

6.  В разделе **Наследовать свойства из следующего шаблона квоты** шаблон, используемый в шаге 2 для создания новой квоты, будет предустановлен (или можно выбрать другой шаблон в списке). Обратите внимание, что свойства шаблона отображаются в разделе **Сводка свойств квоты**.

7.  Нажмите кнопку **Создать**.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Управление квотами](quota-management.md)
-   [Создание автоматически применяемой квоты](create-auto-apply-quota.md)
-   [Создание шаблона квоты](create-quota-template.md)


