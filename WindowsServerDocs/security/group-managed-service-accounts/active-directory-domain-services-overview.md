---
title: Общие сведения о службах домен Active Directory
description: Безопасность Windows Server
ms.prod: windows-server
ms.technology: security-auditing
ms.topic: article
ms.assetid: 6cfe9479-5d17-41d5-939a-891e5233fdca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 9c2182139ee7f891cd026545fecc69610c0b00a6
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520280"
---
# <a name="overview-of-active-directory-domain-services"></a>Общие сведения о службах домен Active Directory

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016

Каталог — это иерархическая структура, в которой хранятся сведения об объектах в сети. Служба каталогов, например домен Active Directory Services (AD DS), предоставляет методы для хранения данных каталога и предоставления доступа к этим данным сетевым пользователям и администраторам. Например, AD DS хранит сведения об учетных записях пользователей, таких как имена, пароли, Номера телефонов и т. д., а также позволяет другим полномочным пользователям в той же сети получить доступ к этим сведениям.

Active Directory хранит сведения об объектах в сети и предоставляет эту информацию администраторам и пользователям, которые могут легко найти и использовать ее. Active Directory использует структурированное хранилище данных в качестве основы для логической иерархической организации сведений в каталоге.

Это хранилище данных, также называемое каталогом, содержит сведения об Active Directoryных объектах. Обычно эти объекты включают в себя общие ресурсы, такие как серверы, тома, принтеры, учетные записи пользователей и компьютеров сети. Дополнительные сведения о Active Directory хранилище данных см. в разделе [хранилище данных каталога](https://technet.microsoft.com/library/cc736627(v=ws.10).aspx).

Безопасность интегрирована с Active Directory путем проверки подлинности входа и управления доступом к объектам в каталоге. С одним сетевым входом администраторы могут управлять данными каталога и Организацией по всей сети, а полномочные пользователи сети могут получать доступ к ресурсам в любой точке сети. Администрирование на основе политики облегчает управление даже очень сложной сетью. Дополнительные сведения о Active Directory безопасности см. в разделе Общие сведения о безопасности.

Active Directory также включает:
* Набор правил, **схема**, определяющая классы объектов и атрибутов, содержащихся в каталоге, ограничения и ограничения для экземпляров этих объектов и формат их имен. Дополнительные сведения о схеме см. в разделе Schema.


* **Глобальный каталог** , содержащий сведения о каждом объекте в каталоге. Это позволяет пользователям и администраторам находить данные каталога независимо от того, какой домен в каталоге действительно содержит данные. Дополнительные сведения о глобальном каталоге см. в статье роль глобального каталога.


* **Механизм запросов и индексов**, чтобы объекты и их свойства могли быть опубликованы и найдены сетевыми пользователями или приложениями. Дополнительные сведения о запросах к каталогу см. в разделе Поиск сведений о каталоге.


* **Служба репликации** , которая распределяет данные каталога по сети. Все контроллеры домена в домене участвуют в репликации и содержат полную копию всех данных каталога для своего домена. Любые изменения данных каталога реплицируются в домене на все контроллеры домена. Дополнительные сведения о репликации Active Directory см. в разделе Общие сведения о репликации.

## <a name="understanding-active-directory"></a>Основные сведения о Active Directory
 В этом разделе приводятся ссылки на основные понятия Active Directory:

* [Технологии структуры и хранения Active Directory](https://technet.microsoft.com/library/cc759186(v=ws.10).aspx)
* [Роли контроллера доменов](https://technet.microsoft.com/library/cc786438(v=ws.10).aspx)
* Схема Active Directory
* [Представление о довериях](https://technet.microsoft.com/library/cc771294(v=ws.10).aspx)
* [Технологии репликации Active Directory](https://technet.microsoft.com/library/cc786438(v=ws.10).aspx)
* [Технологии поиска и публикации Active Directory](https://technet.microsoft.com/library/cc775686(v=ws.10).aspx)
* Взаимодействие с DNS и групповая политика
* [Основные сведения о схеме](https://technet.microsoft.com/library/cc759402(v=ws.10).aspx)

Подробный список концепций Active Directory см. в разделе [Общие сведения о Active Directory](https://technet.microsoft.com/library/cc781408(v=ws.10).aspx).

