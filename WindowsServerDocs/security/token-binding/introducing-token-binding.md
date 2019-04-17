---
title: "Представляем привязка токенов"
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 4623a48c-cefd-4a27-9173-2af58ac212f2
manager: alanth
author: justinha
ms.technology: security-authentication
ms.date: 11/09/2016
ms.openlocfilehash: 2a0bb8c75fe3ca7f7befe0bd67eb3d363a5ad7a9
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="introducing-token-binding"></a>Представляем привязка токенов

>Область применения: Windows Server 2016 и Windows 10

Токен привязки протокол позволяет приложениям и службам для криптографически привязки их маркеры безопасности на уровне TLS для устранения маркера кражи и атак с повторением пакетов. Привязки TLS [RFC5246] долгоживущие, уникально распознаваемый может охватывать несколько сеансов TLS и подключений.

Поддержка версий:

- Windows 10 версии 1507 — по умолчанию выключена
    - Маркер привязки протокола добавлены [[черновик ietf-tokbind протокола-01]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/01/)
    - WinInet & HTTP.SYS привязка токенов по протоколу HTTP [[черновик ietf-tokbind-https-01]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/01/)
- Windows 10 версий 1511 и 1607 и Windows Server 2016 — на по умолчанию
    - Маркер привязки протокола обновлены [[черновик ietf-tokbind протокола-01]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/01/)
    - Расширение TLS для согласования привязка токенов добавлены [[черновик popov-tokbind согласования-00]](https://tools.ietf.org/html/draft-popov-tokbind-negotiation-00)
    - WinInet & HTTP.SYS поддержки токен привязки по протоколу HTTP обновлены [[черновик ietf-tokbind-https-02]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/02/)
- Windows 10 версии 1507 с обслуживанием обновления [KB4034668](https://support.microsoft.com/kb/KB4034668), Windows 10 версии 1511 с обслуживанием обновления [KB4034660](https://support.microsoft.com/kb/KB4034660), Windows 10 версии 1607 и Windows Server 2016 с обслуживанием обновления [KB4034658](https://support.microsoft.com/kb/KB4034658) поддержки токен привязки протокола версии 0.10 — на по умолчанию
    - Маркер привязки протокола обновлены [[черновик ietf-tokbind протокола-10]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/10/)
    - Расширение TLS для согласования привязка токенов добавлены [[черновик ietf-tokbind согласования-05]](https://tools.ietf.org/html/draft-ietf-tokbind-negotiation-05)
    - WinInet & HTTP.SYS поддержки токен привязки по протоколу HTTP обновлены [[черновик ietf-tokbind-https-06]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/06/)
- Windows 10 версии 1703 поддерживает токен привязки протокола версии 0.10 — на по умолчанию
    - Маркер привязки протокола обновлены [[черновик ietf-tokbind протокола-10]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/10/)
    - Расширение TLS для согласования привязка токенов добавлены [[черновик ietf-tokbind согласования-05]](https://tools.ietf.org/html/draft-ietf-tokbind-negotiation-05)
    - WinInet & HTTP.SYS поддержки токен привязки по протоколу HTTP обновлены [[черновик ietf-tokbind-https-06]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/06/)
    - Устройства Windows с безопасностью на основе виртуализации будет хранить ключи привязка токенов в защищенной среде, изолированной от операционной системы

Сведения о поддержке ASP .NET можно найти в [источник Справочник по .NET Framework](https://referencesource.microsoft.com/#System.Web/ITlsTokenBindingInfo.cs,4a5e5668f5c31170). 

Сведения о платформе .NET Framework см. в следующих разделах:

- [Дополнительные возможности сетей](https://blogs.msdn.microsoft.com/dotnet/2015/11/30/net-framework-4-6-1-is-now-available/#networking)

- [Класс .NET TokenBinding](https://msdn.microsoft.com/library/system.security.authentication.extendedprotection.tokenbinding.aspx)
