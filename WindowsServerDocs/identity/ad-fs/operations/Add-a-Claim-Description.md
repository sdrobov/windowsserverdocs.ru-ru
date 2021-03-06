---
ms.assetid: 7d230527-f4fe-4572-8838-0b354ee0b06b
title: Добавление описания утверждения
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: a022ec618c7255021cd424120330671e007a658a
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86962706"
---
# <a name="add-a-claim-description"></a>Добавление описания утверждения


В организации партнера по учетным записям администраторы создают утверждения, представляющие членство пользователя в группе или роли или представляющие некоторые данные о пользователе, например идентификационный номер сотрудника пользователя.

В организации партнера по ресурсам администраторы создают соответствующие утверждения для представления групп и пользователей, которые могут быть распознаны как пользователи ресурсов. Поскольку исходящие утверждения в организации партнера по учетным записям сопоставляются с входящими утверждениями в организации партнера по ресурсам, партнер по ресурсам может принять учетные данные, предоставляемые партнером по учетным записям. 

Для добавления утверждения можно использовать следующую процедуру.

Для выполнения этой процедуры требуется членство в группе **Администраторы** или в эквивалентной группе на локальном компьютере.  Просмотрите сведения об использовании соответствующих учетных записей и членстве в группах в [локальной среде и группах домена по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).

## <a name="to-add-a-claim-description"></a>Добавление описания утверждения

1. В диспетчере сервера щелкните **Средства** и выберите **Управление AD FS**. 

2. Разверните узел **Служба** и справа щелкните **Добавить заявку описание**.
   ![добавить описание утверждения](media/Add-a-Claim-Description/claimdesc1.png)

3. В диалоговом окне Добавление описания утверждения в поле **Отображаемое имя**введите уникальное имя, идентифицирующее группу или роль для этого утверждения.

4. Добавьте **короткое имя**.

5. В поле **идентификатор утверждения**введите URI, связанный с группой или ролью утверждения, которое будет использоваться.

6. В поле **Описание**введите текст, который лучше описывает назначение этого утверждения.

7. В зависимости от потребностей Организации установите один из следующих флажков, чтобы опубликовать это утверждение в метаданных федерации:


~~~
- To publish this claim to make partners aware that this server can accept this claim, click **Publish this claim in federation metadata as a claim type that this Federation Service can accept**.
- To publish this claim to make partners aware that this server can issue this claim, click **Publish this claim in federation metadata as a claim type that this Federation Service can send**.
~~~

8. Нажмите кнопку **ОК**.

![добавить описание утверждения](media/Add-a-Claim-Description/claimdesc2.png)


## <a name="see-also"></a>См. также:  
[Операции AD FS](../ad-fs-operations.md) 
