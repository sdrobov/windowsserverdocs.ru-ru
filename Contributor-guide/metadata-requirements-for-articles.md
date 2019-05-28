---
title: Добавьте теги необходимые метаданные для вашей статьи о Windows Server
description: Список сведений, необходимо добавить как теги метаданных в верхнюю часть вашей статьи на тему Windows Server. Требуемые теги могут меняться, в соответствии с требованиями отчетов и группы.
author: eross-msft
ms.author: lizross
ms.date: 05/06/2019
ms.openlocfilehash: f7c514def1353d44386b1bc53c8cabffe1e31fda
ms.sourcegitcommit: 7e54a1bcd31cd2c6b18fd1f21b03f5cfb6165bf3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461643"
---
# <a name="add-the-required-metadata-tags-to-your-windows-server-related-article"></a>Добавьте теги необходимые метаданные для вашей статьи о Windows Server

В верхней части каждой статьи не существует определенных метаданных, который должен быть включен для отслеживания и оптимизации поисковой системы. Требуемые теги могут меняться, зависимости от требования к отчетности. Тем не менее вы должны уведомление, если вам нужно добавить или удалить все поля.

Он должен выглядеть следующим образом, включая тремя дефисами (-) в верхней и нижней частях:

```markdown

---
title: The title of the article should go here. This is used in SEO and search results.

description: A description for the article should go here. This is used in search results, to provide users with information about whether the article has the information they’re looking for.

ms.prod: Use this specific text, windows-server-threshold

ms.reviewer: The Microsoft alias for the primary PM for the feature/functionality

author: Your GitHub alias

ms.author: Your Microsoft alias

manager: Your manager’s Microsoft alias

ms.topic: Type of article, including article, landing-page, get-started-article, or reference

ms.date: Date of change (MM/DD/YYYY)

---

```

## <a name="example"></a>Пример

```markdown

---
title: What is Windows Admin Center?
description: Learn about the Windows Admin Center, a locally-deployed, browser-based management tool set that lets you manage your Windows Servers with no Azure or cloud dependency.
ms.prod: windows-server-threshold
ms.reviewer: alainch
author: danielle-github
ms.author: danielle
manager: alainch
ms.topic: article
ms.date: 07/06/2019
---

```