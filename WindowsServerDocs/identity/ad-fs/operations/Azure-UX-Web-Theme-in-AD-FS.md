---
title: Веб-темы Azure AD UX в AD FS
description: Следующий документ описывается изменение входа AD FS форм, как указано в пользовательском интерфейсе Azure AD.
author: billmath
ms.author: billmath
manager: femila
ms.date: 10/24/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 8d6afd7829c92382815e95b8c43a054b000359e2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59887885"
---
# <a name="using-an-azure-ad-ux-web-theme-in-active-directory-federation-services"></a>С помощью Azure AD UX веб-темы в службах федерации Active Directory
AD FS формы входа в настоящее время не отражает Azure/Office 365 входа в систему.  Чтобы предоставить более универсальный код и простой для конечных пользователей, мы выпустили выполните каскадных темы таблицы стилей web которой могут применяться к серверам AD FS.  В настоящее время формы входа в систему для AD FS на Windows Server 2016 выглядит следующим образом:

![Текущий вход](media/Azure-UX-Web-Theme-in-AD-FS/one.png)


Взаимодействие с пользователем в новую таблицу стилей, будут выглядеть больше похожи на Azure и Office 365 действия входа в систему.

## <a name="download-the-css-style-sheet"></a>Загрузить таблицу стилей CSS
Веб-тему можно загрузить со следующих Github [расположение](https://github.com/Microsoft/adfsWebCustomization/tree/master/centeredUi).


## <a name="enabling-the-new-web-theme"></a>Включение нового веб-темы
Чтобы включить новую веб-тему используйте следующую процедуру:

### <a name="to-enable-the-new-azure-ad-ux-web-theme-in-ad-fs"></a>Чтобы включить новую веб-тему пользовательского интерфейса Azure AD в AD FS
1.  Запустите PowerShell с правами администратора
2.  Создайте новый веб-темы, с помощью PowerShell:  `New-AdfsWebTheme –Name custom –StyleSheet @{path="c:\NewTheme.css"}`
3.  Установите новую тему в качестве активной темы, с помощью PowerShell:  `Set-AdfsWebConfig -ActiveThemeName custom`
![PowerShell](media/Azure-UX-Web-Theme-in-AD-FS/two.png)
4.  Тестирование входа, перейдя к https://<AD FS name.domain>/adfs/ls/idpinitiatedsignon.htm ![единого входа](media/Azure-UX-Web-Theme-in-AD-FS/three.png)

> ! [ПРИМЕЧАНИЕ] Необходимо убедиться, что этот idpinitiatedsignon был включен.  Оно не включено по умолчанию.  Чтобы включить idpinitiatedsignon используйте следующую команду PowerShell:  `Set-AdfsProperties –EnableIdpInitiatedSignonPage $True`

## <a name="image-recommendations"></a>Изображение рекомендации
Включение выровненные по центру пользовательский Интерфейс позволяет использовать те же образы для фона и логотипа, который уже существуют для фирменной символики компании Azure Active Directory. Как правило применяются те же рекомендации, размер, соотношение и формат.

### <a name="logo"></a>Эмблема
Описание | Ограничения | Рекомендации
------- | ------- | ----------
Логотип отображается поверх панель входа. | Прозрачный JPG или PNG<br>Максимальная высота: 36 пикселей<br>Максимальная ширина: 245 пикселей | Используйте логотип вашей организации.<br>Используйте прозрачное изображение. Не следует предполагать, что фон будет белым.<br>Не добавляйте отступ вокруг логотипа на изображении или логотип будет выглядеть непропорционально маленьким.

### <a name="background"></a>Фон
Описание | Ограничения | Рекомендации
------- | ------- | ----------
Этот параметр отображается в качестве фона страницы входа в систему, привязанный к центру видимого пространства и всегда масштабируется или обрезается под размер окна браузера.    <br>Это изображение не отображается на узких экранах телефонов.<br>Черная маска с прозрачностью 0,55 применяется через этот образ при загрузке страницы. | JPG или PNG<br>Размеры изображения: 1920 x 1080 пикселей<br>Размер файла: &lt; 300 КБ | <br>Использовать образы где нет строго определенной темы. Непрозрачная форма входа отображается над центре этого изображения и может закрыть часть изображения, в зависимости от размера окна браузера.<br>Небольшой размер файла для быстрой загрузки.

## <a name="next-steps"></a>Следующие шаги
- [Настройка AD FS в Windows Server 2016](AD-FS-Customization-in-Windows-Server-2016.md)
- [Дополнительная настройка](Advanced-Customization-of-AD-FS-Sign-in-Pages.md)
- [Пользовательские веб-темы](Custom-Web-Themes-in-AD-FS.md)
