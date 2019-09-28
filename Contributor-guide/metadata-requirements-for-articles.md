---
title: Добавление необходимых тегов метаданных в статью, связанную с Windows Server
description: Список сведений, которые необходимо добавить в качестве тегов метаданных, в начало статей, посвященных Windows Server. Необходимые теги могут изменяться в зависимости от требований к отчетности и команде.
author: eross-msft
ms.author: lizross
ms.date: 05/06/2019
ms.openlocfilehash: 9bedc7ec13aedab9cfaa655f537d5e431d20cccb
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363960"
---
# <a name="add-the-required-metadata-tags-to-your-windows-server-related-article"></a>Добавление необходимых тегов метаданных в статью, связанную с Windows Server

В начале каждой статьи есть определенные метаданные, которые необходимо включать в целях отслеживания и SEO. Необходимые теги могут быть изменены в зависимости от требований к отчетам. Однако если необходимо добавить или удалить какие-либо поля, необходимо получать уведомления.

Он должен выглядеть следующим образом, включая три дефиса (---) в верхней и нижней части:

```markdown

---
title: The title of the article should go here. This is used in SEO and search results.

description: A description for the article should go here. This is used in search results, to provide users with information about whether the article has the information they're looking for.

ms.prod: Use this specific text, windows-server-threshold

ms.reviewer: The Microsoft alias for the primary PM for the feature/functionality

author: Your GitHub alias

ms.author: Your Microsoft alias

manager: Your manager's Microsoft alias

ms.topic: Type of article, including article, landing-page, get-started-article, or reference

ms.date: Date of change (MM/DD/YYYY)

---

```

## <a name="example"></a>Пример

```markdown

---
title: What is Windows Admin Center?
description: Learn about the Windows Admin Center, a locally-deployed, browser-based management tool set that lets you manage your Windows Servers with no Azure or cloud dependency.
ms.prod: windows-server
ms.reviewer: alainch
author: danielle-github
ms.author: danielle
manager: alainch
ms.topic: article
ms.date: 07/06/2019
---

```