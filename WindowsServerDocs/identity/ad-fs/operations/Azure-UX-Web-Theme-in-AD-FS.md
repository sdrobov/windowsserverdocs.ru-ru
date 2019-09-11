---
title: Веб-тема Azure AD UX в AD FS
description: В следующем документе описано, как изменить вход AD FS Forms, чтобы он наглядел похож на пользовательский интерфейс Azure AD.
author: billmath
ms.author: billmath
manager: femila
ms.date: 10/24/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 25ba9505f3f93fb236d6e60e49efc4206482f977
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70866005"
---
# <a name="using-an-azure-ad-ux-web-theme-in-active-directory-federation-services"></a>Использование веб-темы Azure AD UX в службы федерации Active Directory (AD FS)
Вход в AD FS Forms в настоящее время не отражает интерфейс входа Azure/O365.  Чтобы обеспечить более единообразную и эффективную работу конечных пользователей, мы выпустили веб-тему таблицы каскадных стилей, которую можно применить к серверам AD FS.  В настоящее время вход в формы для AD FS в Windows Server 2016 выглядит следующим образом:

![Текущий вход](media/Azure-UX-Web-Theme-in-AD-FS/one.png)


С новой таблицей стилей взаимодействие с пользователем будет выглядеть примерно так же, как в Azure и Office 365.

## <a name="download-the-css-style-sheet"></a>Загрузка таблицы стилей CSS
Вы можете скачать веб-тему из следующего [расположения](https://github.com/Microsoft/adfsWebCustomization/tree/master/centeredUi)GitHub.


## <a name="enabling-the-new-web-theme"></a>Включение новой веб-темы
Чтобы включить новую веб-тему, используйте следующую процедуру.

### <a name="to-enable-the-new-azure-ad-ux-web-theme-in-ad-fs"></a>Включение новой веб-темы Azure AD UX в AD FS
1. Запуск PowerShell от имени администратора
2. Создайте новую веб-тему с помощью PowerShell:`New-AdfsWebTheme –Name custom –StyleSheet @{path="c:\NewTheme.css"}`
3. Задайте новую тему в качестве активной темы с помощью PowerShell:  `Set-AdfsWebConfig -ActiveThemeName custom`
   ![Оболочк](media/Azure-UX-Web-Theme-in-AD-FS/two.png)
4. Протестируйте вход, перейдя в HTTPS://<AD FS name.domain>/ADFS/Ls/idpinitiatedsignon.htm ![вход.](media/Azure-UX-Web-Theme-in-AD-FS/three.png)

> ! МЕТИМ Необходимо убедиться, что страницу idpinitiatedsignon включен.  По умолчанию оно отключено.  Чтобы включить страницу idpinitiatedsignon, используйте следующую команду PowerShell:`Set-AdfsProperties –EnableIdpInitiatedSignonPage $True`

## <a name="image-recommendations"></a>Рекомендации по созданию образа
Включение центрированного пользовательского интерфейса позволяет использовать те же изображения для фона и эмблемы, которые уже могут присутствовать для Azure Active Directory фирменной символики компании. Как правило, применяются те же рекомендации, что и для размера, соотношения и формата.

### <a name="logo"></a>Эмблема

Описание | Ограничения | Рекомендации
------- | ------- | ----------
Эмблема отображается в верхней части панели входа. | Прозрачный JPG или PNG<br>Максимальная высота: 36 ПКС<br>Максимальная ширина: 245 ПКС | Используйте логотип своей организации здесь.<br>Использовать прозрачное изображение. Не думайте, что фон будет белым.<br>Не добавляйте отступы вокруг логотипа на изображении, или логотип будет выглядеть непропорционально мелким.

### <a name="background"></a>Фоновый

Описание | Ограничения | Рекомендации
------- | ------- | ----------
Этот параметр отображается в фоновом режиме страницы входа, привязан к центру видимого пространства и масштабируется и обрезается для заполнения окна браузера.    <br>На узких экранах, таких как мобильные телефоны, этот образ не отображается.<br>При загрузке страницы к этому изображению применяется Черная маска с 0,55 прозрачностью. | JPG или PNG<br>Размеры изображения: 1920 x 1080 px<br>Размер файла: &lt;300 КБ | <br>Используйте изображения, в которых нет строгого фокуса. Форма непрозрачного входа отображается над центром этого изображения и может охватывать любую часть изображения в зависимости от размера окна браузера.<br>Чтобы обеспечить быструю загрузку, размер файла должен быть небольшим.

## <a name="next-steps"></a>Следующие шаги
- [Настройка AD FS в Windows Server 2016](AD-FS-Customization-in-Windows-Server-2016.md)
- [Расширенная настройка](Advanced-Customization-of-AD-FS-Sign-in-Pages.md)
- [Пользовательские веб-темы](Custom-Web-Themes-in-AD-FS.md)
