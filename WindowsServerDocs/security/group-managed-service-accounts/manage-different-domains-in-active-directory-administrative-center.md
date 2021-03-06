---
title: Управление различными доменами в центр администрирования Active Directory
description: Безопасность Windows Server
ms.prod: windows-server
ms.assetid: 166351c3-4076-48be-aa8f-797adf1e9d68
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 6690ffbc558db4026c3fe67168907ca953ad4081
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856987"
---
# <a name="manage-different-domains-in-active-directory-administrative-center"></a>Управление различными доменами в центр администрирования Active Directory

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

  При открытии Active Directory администрирования домен, на котором вы выполнили вход на этом компьютере \(локальный домен\) отображается в области навигации центр администрирования Active Directory \(левой панели\). В зависимости от прав текущего набора учетных данных для входа вы можете просматривать Active Directory объекты в этом локальном домене или управлять ими.

 Можно также использовать один и тот же набор учетных данных для входа и один и тот же экземпляр центр администрирования Active Directory для просмотра и управления Active Directoryными объектами в любом другом домене в том же лесу, или домен в другом лесу, имеющий установленное отношение доверия с локальным доменом. Одновременно поддерживаются как один, так\-способ доверия, так и два\-отношения доверия.

> [!NOTE]
>  Если существует один\-способ отношения доверия между доменом A и доменом B, через который пользователи в домене A могут получить доступ к ресурсам в домене б, но пользователи в домене б не могут получить доступ к ресурсам в домене а, центр администрирования Active Directory Если на компьютере а домен A является локальным доменом, то можно подключиться к домену B с текущим набором учетных данных для входа и в том же центр администрирования Active Directory экземпляре Но если вы используете центр администрирования Active Directory на компьютере, где домен B является локальным доменом, вы не сможете подключиться к домену A с тем же набором учетных данных в том же экземпляре центр администрирования Active Directory.

 Для выполнения этой процедуры отсутствуют минимальные требования к членству в группах.

### <a name="windows-server-2012-to-manage-a-foreign-domain-in-the-selected-instance-of-active-directory-administrative-center-using-the-current-set-of-logon-credentials"></a>Windows Server 2012: для управления внешним доменом в выбранном экземпляре центр администрирования Active Directory с использованием текущего набора учетных данных для входа

1.  Чтобы открыть центр администрирования Active Directory, в **Диспетчер сервера**выберите **Сервис**, а затем — **центр администрирования Active Directory**.

    > [!NOTE]
    >  Другой способ открыть центр администрирования Active Directory — нажать кнопку **Пуск**, а затем ввести **дсак. exe**.

2.  Чтобы открыть окно **Добавление узлов навигации**, щелкните **Управление**, а затем — **Добавить узлы перехода** , как показано на следующем рисунке.

     ![Снимок экрана: * * Добавление узлов навигации * * пользовательский интерфейс](media/ADDS_ADACAddNavNode.gif)

3.  В области **Добавить узлы навигации**щелкните **подключиться к другим доменам** , как показано на следующем рисунке.

     ![Снимок экрана: * * Добавление узлов навигации * * пользовательский интерфейс](media/ADDS_ADACConnectToDomain.gif)

4.  В поле **Подключение к**введите имя внешнего домена, которым требуется управлять \(например, **contoso.com**\), а затем нажмите кнопку **ОК**.

5.  После успешного подключения к инородному домену просмотрите столбцы в окне **Добавление узлов навигации** , выберите контейнер или контейнеры для добавления в область навигации центр администрирования Active Directory и нажмите кнопку **ОК**.

### <a name="windows-server-2008-r2-to-manage-a-foreign-domain-in-the-selected-instance-of-active-directory-administrative-center-using-the-current-set-of-logon-credentials"></a>Windows Server 2008 R2: для управления внешним доменом в выбранном экземпляре центр администрирования Active Directory с использованием текущего набора учетных данных для входа

1. Чтобы открыть центр администрирования Active Directory, нажмите кнопку **Пуск**, выберите пункт **Администрирование**, а затем щелкните **центр администрирования Active Directory**.

   > [!NOTE]
   >  Другой способ открыть центр администрирования Active Directory — нажать кнопку **Пуск**, выбрать пункт **выполнить**, а затем ввести **дсак. exe**.

2. Чтобы открыть окно " **Добавить узлы навигации**", в верхней части окна центр администрирования Active Directory щелкните **Добавить узлы навигации** , как показано на следующем рисунке.

    ![Снимок экрана: * * Добавление узлов навигации * * пользовательский интерфейс](media/click_add_nav_nodes.gif)

   > [!NOTE]
   >  Чтобы открыть окно **Добавление узлов навигации** , щелкните правой кнопкой мыши\-щелкните в любом месте пустого пространства в области навигации центр администрирования Active Directory, а затем щелкните **Добавить узлы перехода**.

3. В области **Добавить узлы навигации**щелкните **подключиться к другим доменам** , как показано на следующем рисунке.

    ![Снимок экрана: * * Добавление узлов навигации * * * * подключение к другим доменам * * пользовательский интерфейс](media/add_nav_nodes.gif)

4. В поле **Подключение к**введите имя внешнего домена, которым требуется управлять \(например, **contoso.com**\), а затем нажмите кнопку **ОК**.

5. После успешного подключения к инородному домену просмотрите столбцы в окне **Добавление узлов навигации** , выберите контейнер или контейнеры для добавления в область навигации центр администрирования Active Directory и нажмите кнопку **ОК**.

   Дополнительные сведения о настройке области навигации центр администрирования Active Directory см. в разделе [настройка центр администрирования Active Directory панели навигации](customize-the-active-directory-administrative-center-navigation-pane.md).

   Можно также открыть центр администрирования Active Directory, используя набор учетных данных для входа, который отличается от текущего набора учетных данных для входа. Команда в следующей процедуре может быть полезной, если вы выполнили вход на компьютер, на котором выполняется центр администрирования Active Directory с обычными учетными данными пользователя, но вы хотите использовать центр администрирования Active Directory на этом компьютере для управления локальным доменом от имени администратора. \(эта команда также может быть полезной, если вы хотите использовать центр администрирования Active Directory для удаленного управления внешним доменом, который отличается от учетных данных, отличающихся текущим набором учетных данных для входа. Однако внешний домен должен иметь установленное отношение доверия с локальным доменом.\)

   Для выполнения этой процедуры отсутствуют минимальные требования к членству в группах.

### <a name="to-manage-a-domain-using-logon-credentials-that-are-different-from-the-current-set-of-logon-credentials"></a>Управление доменом с использованием учетных данных входа, отличных от текущего набора учетных данных

1.  Чтобы открыть центр администрирования Active Directory, в командной строке введите следующую команду и нажмите клавишу ВВОД:

     `runas /user:<domain\user> dsac`

     Где `<domain\user>` — это набор учетных данных, которые необходимо открыть центр администрирования Active Directory с помощью, а `dsac` — центр администрирования Active Directory имя исполняемого файла \(Дсак. exe\).

     Например, введите следующую команду и нажмите клавишу ВВОД:

     `runas /user:contoso\administrator dsac`

2.  Когда центр администрирования Active Directory открыт, просмотрите область навигации, чтобы просмотреть домен Active Directory или управлять им.

  

