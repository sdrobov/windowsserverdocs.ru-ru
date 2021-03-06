---
title: Регистрация сервера политики сети в домене Active Directory
description: Этот раздел можно использовать для регистрации сервера, на котором выполняется сервер политики сети, в Windows Server 2016 в домене по умолчанию NPS или в другом домене.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 2de954fd-a7d8-4cc6-85b1-b0c3c06f788f
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 63d630250b0b24937a3dfc01bcba7ec63faa3c3e
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80315962"
---
# <a name="register-an-nps-in-an-active-directory-domain"></a>Регистрация сервера политики сети в домене Active Directory

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Этот раздел можно использовать для регистрации сервера, на котором выполняется сервер политики сети, в Windows Server 2016 в домене по умолчанию NPS или в другом домене.

## <a name="register-an-nps-in-its-default-domain"></a>Регистрация сервера политики сети в домене по умолчанию

Эту процедуру можно использовать для регистрации NPS в домене, в котором сервер является членом домена. 

НПСС должен быть зарегистрирован в Active Directory, чтобы они имели разрешение на чтение свойств входящих звонков учетных записей пользователей в процессе авторизации. При регистрации NPS сервер добавляется в группу **Серверы RAS и IAS** в Active Directory.

Выполнить эти операции может только член группы **Администраторы** или пользователь с аналогичными правами.

### <a name="to-register-an-nps-in-its-default-domain"></a>Регистрация сервера политики сети в домене по умолчанию


1. На сервере политики сети в диспетчер сервера щелкните **средства**, а затем — **сервер политики сети**. Откроется консоль сервера политики сети.

2. Щелкните правой кнопкой мыши элемент **NPS (локальный)** и выберите пункт **зарегистрировать сервер в Active Directory**. Откроется диалоговое окно **Сервер политики сети**.

3. В диалоговом окне **Сервер политики сети** нажмите кнопку **OK** и затем еще раз нажмите кнопку **OK**.

## <a name="register-an-nps-in-another-domain"></a>Регистрация сервера политики сети в другом домене

Чтобы предоставить серверу политики сети разрешение на чтение свойств входящих звонков учетных записей пользователей в Active Directory, сервер политики сети должен быть зарегистрирован в домене, в котором находятся учетные записи.

Эту процедуру можно использовать для регистрации сервера политики сети в домене, который не является членом домена.

Выполнить эти операции может только член группы **Администраторы** или пользователь с аналогичными правами.

### <a name="to-register-an-nps-in-another-domain"></a>Регистрация сервера политики сети в другом домене

1. На контроллере домена в диспетчер сервера выберите **средства**, а затем **Active Directory пользователи и компьютеры**. Откроется консоль Active Directory пользователи и компьютеры.

2. В дереве консоли перейдите к домену, в котором NPS должен считывать данные учетной записи пользователя, а затем щелкните папку **Пользователи** . 

3. В области сведений щелкните правой кнопкой мыши **Серверы RAS и IAS**и выберите пункт **свойства**. Откроется диалоговое окно **свойства серверов RAS и IAS** .

4. В диалоговом окне **свойства серверов RAS и IAS** перейдите на вкладку **члены** , добавьте все НПСС, которые необходимо зарегистрировать в домене, а затем нажмите кнопку **ОК**.


### <a name="to-register-an-nps-in-another-domain-by-using-netsh-commands-for-nps"></a>Регистрация сервера политики сети в другом домене с помощью команд Netsh для NPS

1. Откройте командную строку или Windows PowerShell. 

2. В командной строке введите следующую команду: **netsh nps add registeredserver** &nbsp;*домен* &nbsp;*Server*, а затем нажмите клавишу ВВОД.

>[!NOTE]
>В предыдущей команде *domain* — это доменное имя DNS домена, в котором вы хотите зарегистрировать NPS, а *Server* — имя компьютера NPS.

