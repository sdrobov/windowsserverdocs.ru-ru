---
ms.assetid: 5b9fc9c1-5d12-4ad4-8ddc-3b8a6d45b217
title: "Создание отношений доверия с проверяющей стороной"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 14e1cc732ed60b7f05a9a4a9aac9037c48b702f2
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="create-a-relying-party-trust"></a>Создание отношений доверия с проверяющей стороной

>Область применения: Windows Server 2016, Windows Server 2012 R2

Следующий документ предоставляет сведения о создании доверия с проверяющей стороной вручную и с использованием метаданных федерации.
  
## <a name="to-create-a-claims-aware-relying-party-trust-manually"></a>Создание утверждений доверия учитывать проверяющей стороной вручную 

Чтобы добавить новое отношение доверия проверяющей стороны с помощью управления AD FS оснастка и вручную настроить параметры, выполните следующую процедуру на сервере федерации.  

Членство в группе **Администраторы**, или эквивалентной группе на локальном компьютере минимальным требованием для выполнения этой процедуры.  Подробные сведения об использовании соответствующих учетных записей и членстве в группах в [локальные и доменные группы по умолчанию ](https://go.microsoft.com/fwlink/?LinkId=83477).
  
1. В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS **.  
  
2.  В разделе **действия**, нажмите кнопку **добавить доверия с проверяющей стороной **.  
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust1.PNG)   

3.  На **приветствия** выберите **заявками** и нажмите кнопку **запустить **.  
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust2.PNG) 
  
4.  На **Выбор источника данных** щелкните **ввод данных о проверяющей стороне вручную**, а затем нажмите кнопку **Далее **.  
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust3.PNG) 
  
5.  На **указание отображаемого имени** введите имя в **отображаемое имя**в разделе **заметки** введите описание этого отношения доверия с проверяющей стороной, а затем нажмите кнопку **Далее **.  
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust4.PNG) 

6. На **Настройка сертификата** страницы, если у вас есть сертификат дополнительного шифрования маркера, нажмите кнопку **Обзор** найти файл сертификата и нажмите кнопку **Далее **.  
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust5.PNG) 

7.  На **настроить URL-адрес** выполните одно или оба следующих действия, нажмите кнопку **Далее**, а затем перейдите к шагу 8:  
  
    -   Выберите **включить поддержку наличия WS-Federation passive** флажок. В разделе **проверяющей стороной наличия WS-Federation Passive URL-адрес протокола**, введите URL-адрес для этого отношения доверия с проверяющей стороной и нажмите кнопку **Далее **.  
  
    -   Выберите **включить поддержку протокола SAML 2.0 WebSSO** флажок. В разделе **URL-адрес службы единого входа SAML 2.0 проверяющей стороной**, введите Security Assertion Markup Language \(SAML\) службы endpoint URL-адрес для этого отношения доверия с проверяющей стороной и нажмите кнопку **Далее **.  
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust6.PNG)   

8. На **Настройка идентификаторов** укажите один или несколько идентификаторов этой проверяющей стороны, нажмите кнопку **добавить** добавить их в список и нажмите кнопку **Далее**.  
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust8.PNG)
  
9.  На **выберите политики управления доступом** выберите политику и нажмите кнопку **Далее**.  Дополнительные сведения о политики управления доступом см. в разделе [политики управления доступом в AD FS](Access-Control-Policies-in-AD-FS.md). 
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust9.PNG)

10. На **все готово для добавления отношения доверия** страницы, проверьте параметры и нажмите кнопку **Далее** сохранить проверяющей стороной сведения об отношениях доверия.  
   ![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust10.PNG) 
11. На **Готово** щелкните **закрыть**. Это действие автоматически отображает **изменение правил для утверждений** диалоговое окно.  
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust11.PNG) 

## <a name="to-create-a-claims-aware-relying-party-trust-using-federation-metadata"></a>Создание утверждений учитывать проверяющей стороной отношений доверия с использованием метаданных федерации

Добавление нового доверия с проверяющей стороной, используя оснастку управления AD FS путем автоматического импорта данных конфигурации о партнере из метаданных федерации, опубликованных партнером в локальной сети или к Интернету, выполните следующую процедуру на сервере федерации в организации партнера по учетным записям.

>[!NOTE]
>Хотя он давно общепринятой практикой использовать сертификаты с коротким именем узла, например https://myserver, эти сертификаты не значения безопасности и позволяют злоумышленнику выдать за службу федерации, которая публикует метаданные федерации. Таким образом при выполнении запросов метаданных федерации, следует только использовать полное доменное имя, например https://myserver.contoso.com.

Членство в группе **Администраторы**, или эквивалентной группе на локальном компьютере минимальным требованием для выполнения этой процедуры.  Подробные сведения об использовании соответствующих учетных записей и членстве в группах в [локальные и доменные группы по умолчанию ](https://go.microsoft.com/fwlink/?LinkId=83477).


1. В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS **.  
  
2.  В разделе **действия**, нажмите кнопку **добавить доверия с проверяющей стороной **.  
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust1.PNG)   

3.  На **приветствия** выберите **заявками** и нажмите кнопку **запустить **.  
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust2.PNG) 
  
4.  На **Выбор источника данных** щелкните **Импорт данных о проверяющей стороне опубликованных в Интернете или локальной сети*. В **адрес метаданных федерации (имя узла или URL-адрес)**, введите федерации метаданных URL-адрес или имя узла для партнера и нажмите кнопку **Далее**.  
![проверяющая сторона](media/Create-a-Relying-Party-Trust/addtrust12.PNG) 

5.  На странице "Укажите отображаемое имя" введите имя в **отображаемое имя**, в разделе примечаний введите описание этого отношения доверия с проверяющей стороной и нажмите кнопку **Далее**.

6.  На странице Выбор правил авторизации выдачи выберите **разрешить всем пользователям доступ к этой проверяющей стороне** или **запретить всем пользователям доступ к этой проверяющей стороне**, а затем нажмите кнопку **Далее**.

7.  На все готово для добавления отношения доверия страницы, проверьте параметры и нажмите кнопку **Далее** сохранить проверяющей стороной сведения об отношениях доверия.

8.  На странице "Готово", нажмите кнопку **закрыть**. Это действие автоматически откроется диалоговое окно Изменение правил для утверждений. Дополнительные сведения о том, как продолжить добавление правил для утверждений для этого отношения доверия с проверяющей стороной см. Дополнительные ссылки.




## <a name="see-also"></a>См. также:  
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md) 