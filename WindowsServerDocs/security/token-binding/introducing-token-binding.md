---
title: Общие сведения о привязке токена
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 4623a48c-cefd-4a27-9173-2af58ac212f2
manager: alanth
author: justinha
ms.technology: security-authentication
ms.date: 11/09/2016
ms.openlocfilehash: 2a0bb8c75fe3ca7f7befe0bd67eb3d363a5ad7a9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59884235"
---
# <a name="introducing-token-binding"></a>Общие сведения о привязке токена

>Область применения. Windows Server 2016 и Windows 10

Token Binding protocol дает приложениям и службам для криптографически привязки маркеров безопасности на уровне TLS, для устранения кражи маркеров и атаки с повторением. Привязки TLS [RFC5246] долгоживущие, уникально идентифицируемыми может охватывать несколько сеансов TLS и соединений.

Поддерживаемые версии:

- Windows 10 версии 1507 — отключено по умолчанию
    - Token Binding Protocol добавлены [[draft-ietf-tokbind-protocol-01]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/01/)
    - WinInet и HTTP. Поддержка SYS привязки токенов по протоколу HTTP [[draft-ietf-tokbind-https-01]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/01/)
- Windows 10 версии 1511 и 1607 и Windows Server 2016 — на по умолчанию
    - Token Binding Protocol обновлены [[draft-ietf-tokbind-protocol-01]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/01/)
    - Расширения TLS для согласования привязки токенов, которые добавлены [[draft-popov-tokbind согласования-00]](https://tools.ietf.org/html/draft-popov-tokbind-negotiation-00)
    - WinInet и HTTP. Поддержка SYS привязки токенов по протоколу HTTP, которые обновлены [[draft-ietf-tokbind-https-02]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/02/)
- Windows 10 версии 1507 с сервисное обновление [KB4034668](https://support.microsoft.com/kb/KB4034668), Windows 10 версии 1511 с сервисное обновление [KB4034660](https://support.microsoft.com/kb/KB4034660), Windows 10, версия 1607 и Windows Server 2016 с сервисное обновление [KB4034658](https://support.microsoft.com/kb/KB4034658) по умолчанию поддерживают Token Binding Protocol версии 0.10 — на
    - Token Binding Protocol обновлены [[draft-ietf-tokbind-protocol-10]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/10/)
    - Расширения TLS для согласования привязки токенов, которые добавлены [[draft-ietf-tokbind согласования-05]](https://tools.ietf.org/html/draft-ietf-tokbind-negotiation-05)
    - WinInet и HTTP. Поддержка SYS привязки токенов по протоколу HTTP, которые обновлены [[draft-ietf-tokbind-https-06]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/06/)
- Windows 10 версии 1703 Token Binding Protocol версии 0.10 — по умолчанию поддерживает в
    - Token Binding Protocol обновлены [[draft-ietf-tokbind-protocol-10]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/10/)
    - Расширения TLS для согласования привязки токенов, которые добавлены [[draft-ietf-tokbind согласования-05]](https://tools.ietf.org/html/draft-ietf-tokbind-negotiation-05)
    - WinInet и HTTP. Поддержка SYS привязки токенов по протоколу HTTP, которые обновлены [[draft-ietf-tokbind-https-06]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/06/)
    - Устройства Windows с включенной безопасностью на основе виртуализации будет хранить эти ключи привязки токена в защищенной среде, которая изолирована от рабочей операционной системы

Сведения о поддержке ASP .NET можно найти в [.NET Framework Reference Source](https://referencesource.microsoft.com/#System.Web/ITlsTokenBindingInfo.cs,4a5e5668f5c31170). 

Сведения о платформе .NET Framework см. в разделах:

- [Усовершенствования работы в сети](https://blogs.msdn.microsoft.com/dotnet/2015/11/30/net-framework-4-6-1-is-now-available/#networking)

- [Класс .NET TokenBinding](https://msdn.microsoft.com/library/system.security.authentication.extendedprotection.tokenbinding.aspx)
