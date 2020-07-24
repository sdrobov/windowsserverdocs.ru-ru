---
title: Веб-тема Azure AD UX в AD FS
description: В следующем документе описано, как изменить вход AD FS Forms, чтобы он наглядел похож на пользовательский интерфейс Azure AD.
author: billmath
ms.author: billmath
manager: femila
ms.date: 10/24/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: ce9bddbc9b03a9019860e9b831bb928326098b76
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965956"
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
3. Установка новой темы в качестве активной темы с помощью PowerShell: `Set-AdfsWebConfig -ActiveThemeName custom` 
    ![ PowerShell](media/Azure-UX-Web-Theme-in-AD-FS/two.png)
4. Протестируйте вход, перейдя в https:// <AD FS name.domain> /адфс/лс/idpinitiatedsignon.htm ![ Вход.](media/Azure-UX-Web-Theme-in-AD-FS/three.png)

> ! МЕТИМ Необходимо убедиться, что страницу idpinitiatedsignon включен.  По умолчанию оно отключено.  Чтобы включить страницу idpinitiatedsignon, используйте следующую команду PowerShell:`Set-AdfsProperties –EnableIdpInitiatedSignonPage $True`

## <a name="image-recommendations"></a>Рекомендации по созданию образа
Включение центрированного пользовательского интерфейса позволяет использовать те же изображения для фона и эмблемы, которые уже могут присутствовать для Azure Active Directory фирменной символики компании. Как правило, применяются те же рекомендации, что и для размера, соотношения и формата.

### <a name="logo"></a>Эмблема

Описание | Ограничения | Рекомендации
------- | ------- | ----------
Эмблема отображается в верхней части панели входа. | Прозрачное изображение в формате JPG или PNG<br>Максимальная высота: 36 пикселей<br>Максимальная ширина: 245 пикселей | Используйте логотип своей организации здесь.<br>Используйте прозрачное изображение. Не думайте, что фон будет белым.<br>Не добавляйте отступ вокруг логотипа на изображении, так как в этом случае логотип будет выглядеть непропорционально маленьким.

### <a name="background"></a>Фон

Описание | Ограничения | Рекомендации
------- | ------- | ----------
Это значение используется для отображения фона страницы входа. Изображение привязано к центру видимого пространства и всегда масштабируется или обрезается под размер окна браузера.    <br>Это изображение не отображается на узких экранах телефонов.<br>При загрузке страницы к изображению применяется черная маска с прозрачностью 0,55. | JPG или PNG<br>Размеры изображения: 1920 x 1080 пикселей<br>Размер файла: &lt; 300 КБ | <br>Используйте изображения, если нет строго определенной темы. В центре этого изображения отображается непрозрачная форма входа, которая может закрыть часть изображения в зависимости от размера окна браузера.<br>Чтобы ускорить загрузку, не выбирайте файлы большого размера.

## <a name="next-steps"></a>Дальнейшие шаги
- [Настройка AD FS в Windows Server 2016](./ad-fs-customization-in-windows-server.md)
- [Дополнительная настройка](Advanced-Customization-of-AD-FS-Sign-in-Pages.md)
- [Пользовательские веб-темы](Custom-Web-Themes-in-AD-FS.md)
