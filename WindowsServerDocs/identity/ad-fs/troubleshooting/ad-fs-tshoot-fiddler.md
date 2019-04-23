---
title: AD FS Устранение неполадок — Fiddler
description: В этом документе описывается функция Fiddler и как установить и настроить Fiddler для устранения неполадок утверждений AD FS
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 03/02/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 822300d0e4b6ae462a3c942e22530bbed5f93e86
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59865635"
---
# <a name="ad-fs-troubleshooting---fiddler"></a>AD FS Устранение неполадок — Fiddler
Fiddler — это средство, который может использоваться для записи веб-трафик HTTP/HTTPS.  Это средство можно использовать для устранения процесс выдачи утверждений.  Взглянув на трафик можно получить, лучше понять где разбить взаимодействие.  В этом документе вы узнаете, как установить и настроить Fiddler для захвата трафика AD FS.  Пример fiddler с помощью WS-Federation см. в разделе [AD FS, устранение неполадок - Fiddler - WS-Federation](ad-fs-tshoot-fiddler-ws-fed.md)

## <a name="download-and-install-fiddler"></a>Скачайте и установите Fiddler
Вы можете скачать Fiddler [здесь](https://www.telerik.com/download/fiddler).  После загрузки его пойти дальше и установить его.

## <a name="configure-fiddler-to-capture-ad-fs-traffic"></a>Настройте Fiddler для записи трафика AD FS
Чтобы записать трафика AD FS, необходимо настроить Fiddler для расшифровки трафика SSL. 

### <a name="configure-the-fiddler-ssl-certificate"></a>Настройка сертификата Fiddler SSL
 Используйте следующую процедуру для настройки Fiddler для расшифровки трафика SSL.

1.  Откройте Fiddler
2.  В верхней части в разделе **средства**выберите **параметры Fiddler**.
3.  Перейдите на вкладку HTTPS.
4.  Установите флажок **расшифровывать трафик HTTPS** и выберите **из браузеров только** из раскрывающегося списка.
5.  Установите флажок **игнорировать ошибки сертификата сервера**.
6.  Нажмите кнопку **ОК**.

![Fiddler](media/ad-fs-tshoot-fiddler/fiddler1.png)

## <a name="next-steps"></a>Следующие шаги

- [Устранение неполадок AD FS](ad-fs-tshoot-overview.md)