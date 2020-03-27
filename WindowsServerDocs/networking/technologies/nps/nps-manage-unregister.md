---
title: Отмена регистрации сервера политики сети в домене Active Directory
description: Этот раздел можно использовать для регистрации сервера, на котором выполняется сервер политики сети, в Windows Server 2016 в домене по умолчанию NPS или в другом домене.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 68a94616-3c29-45bd-bd33-e4c578f119e1
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 366e3e7eef6ac1e8682dd3064e0d133f21d1a8da
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80315896"
---
# <a name="unregister-an-nps-from-an-active-directory-domain"></a>Отмена регистрации сервера политики сети в домене Active Directory

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В процессе управления развертыванием NPS может оказаться полезным переместить сервер политики сети в другой домен, заменить NPS или снять с учета NPS. 

При перемещении или списании NPS можно отменить регистрацию сервера политики сети в доменах Active Directory, в которых NPS имеет разрешение на чтение свойств учетных записей пользователей в Active Directory.

Выполнить эти операции может только член группы **Администраторы** или пользователь с аналогичными правами.

## <a name="to-unregister-an-nps"></a>Отмена регистрации сервера политики сети

1. На контроллере домена в диспетчер сервера выберите **средства**, а затем **Active Directory пользователи и компьютеры**. Откроется консоль Active Directory пользователи и компьютеры.

2. Щелкните **Пользователи**, а затем дважды щелкните **Серверы RAS и IAS**.

3. Перейдите на вкладку **члены** , а затем выберите NPS, для которого требуется отменить регистрацию.

4. Нажмите кнопку **Удалить**, выберите **Да**, а затем нажмите кнопку **ОК**.

