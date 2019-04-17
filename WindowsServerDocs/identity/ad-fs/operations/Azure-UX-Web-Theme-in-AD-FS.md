---
title: "Взаимодействие с Пользователем Azure AD веб-тему в AD FS"
description: "Следующем документе описывается изменение AD FS форм войти в, как показано взаимодействие с пользователем Azure AD."
author: billmath
ms.author: billmath
manager: femila
ms.date: 10/24/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: e7bac1db17eb4facc7643fe0db0ccf00c119a45d
ms.sourcegitcommit: 9278435cbfa8dbeb30d0557ed0d27832b154edd2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="using-an-azure-ad-ux-web-theme-in-active-directory-federation-services"></a>С помощью веб-темы Azure AD взаимодействию с Пользователем в службах федерации Active Directory
Вход форм Служб федерации Active Directory в настоящее время зеркало Azure и Office 365 входа в систему.  Чтобы обеспечить более универсальный и легкое взаимодействие для конечных пользователей, мы выпустили выполните каскадных темы таблицы стилей web можно применять к серверам службы федерации Active Directory.  В настоящее время форм выполнять вход в AD FS на Windows Server 2016 выглядит следующее:

![Текущий вход](media/Azure-UX-Web-Theme-in-AD-FS/one.png)


С помощью новой таблицы стилей взаимодействие с пользователем будет выглядеть больше похож на Azure и Office 365 возможности входа в систему.

## <a name="download-the-css-style-sheet"></a>Загрузите таблицу стилей CSS
Вы можете скачать веб-тему из следующих Github [расположение ](https://github.com/Microsoft/adfsWebCustomization/tree/master/centeredUi).


## <a name="enabling-the-new-web-theme"></a>Включение нового веб-темы
Чтобы включить новую веб-тему используйте следующую процедуру:

### <a name="to-enable-the-new-azure-ad-ux-web-theme-in-ad-fs"></a>Чтобы включить новую веб-тему Azure AD UX в AD FS
1.  Запустите PowerShell от имени администратора
2.  Создайте новую веб-тему с помощью PowerShell:  `New-AdfsWebTheme –Name custom –StyleSheet @{path="c:\NewTheme.css"}`
3.  Установить новую тему в качестве активной темы, с помощью PowerShell: <ph x="1">«Set-AdfsWebConfig - ActiveThemeName настраиваемые»
! [</ph>PowerShell](media/Azure-UX-Web-Theme-in-AD-FS/two.png)
4.  Тестирование входа, перейдя к https://<AD FS name.domain>/adfs/ls/idpinitiatedsignon.htm ![входа](media/Azure-UX-Web-Theme-in-AD-FS/three.png)

>! [ПРИМЕЧАНИЕ.] Необходимо убедиться, что была включена, idpinitiatedsignon.  Она не включена по умолчанию.  Чтобы включить idpinitiatedsignon используйте следующую команду PowerShell:  `Set-AdfsProperties –EnableIdpInitiatedSignonPage $True`

## <a name="image-recommendations"></a>Рекомендации образа
Ниже приведены рекомендации по размер изображения фона и изображение логотипа.

### <a name="logo"></a>Логотип
- 24 точки высота, ширина max 256px
- Не добавляйте любой заполнения вокруг логотипа в ОС.  Убедитесь, что прозрачный фон активов.

### <a name="background"></a>Фон
- размер 1024 x 1080 пикселей, размер файла не должен превышать 200 КБ.  Максимальное разрешение возможности следует использовать с пропорции 16:9 или 16:10, которая отслеживает размер изображения в разделе ограниченного использования программ.

## <a name="next-steps"></a>Дальнейшие действия
- [Настройка AD FS в Windows Server 2016](AD-FS-Customization-in-Windows-Server-2016.md)
- [Дополнительная настройка](Advanced-Customization-of-AD-FS-Sign-in-Pages.md)
- [Пользовательские веб-темы](Custom-Web-Themes-in-AD-FS.md)
