---
title: Добавьте сведения об узле для аттестацию с доверием администратора
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 87089ebc-b953-4aa3-96b5-966cf91acb02
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 7949711dbb0f89f5404b491d60938985bfa98c22
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59849465"
---
>Относится к: Windows Server (полугодовой канал), Windows Server 2016

# <a name="authorize-hyper-v-hosts-using-admin-trusted-attestation"></a>Авторизация с помощью аттестацию с доверием администратора узлов Hyper-V

>[!IMPORTANT]
>Аттестацию с доверием администратора (режим AD) является устаревшим, начиная с Windows Server 2019. Для сред, где аттестацию доверенного платформенного МОДУЛЯ не поддерживается, Настройка [размещения Аттестация ключей](guarded-fabric-initialize-hgs-key-mode.md). Аттестация ключей узла обеспечивает аналогичный уверенность в режим AD и проще в настройке. 


Чтобы авторизовать защищенного узла в режиме AD: 

1. В домене fabric добавьте узлы Hyper-V в группу безопасности.
2. В домене HGS зарегистрируйте идентификатор безопасности группы безопасности в службе HGS. 

## <a name="add-the-hyper-v-host-to-a-security-group-and-reboot-the-host"></a>Добавьте узел Hyper-V в группу безопасности, а затем перезагрузите узел

1. Создание **GLOBAL** безопасности в домене fabric и добавить узлы Hyper-V, которые будут выполняться экранированных виртуальных машин. 
   Перезапустите узлы, чтобы обновить их членства в группе.

2. Используйте Get-ADGroup, чтобы получить идентификатор безопасности (SID) группы безопасности и предоставляют их администратор службы защиты узла. 

   ```powershell
   Get-ADGroup "Guarded Hosts"
   ```

   ![Команда Get-AdGroup с выходными данными](../media/Guarded-Fabric-Shielded-VM/guarded-host-get-adgroup.png)

## <a name="register-the-sid-of-the-security-group-with-hgs"></a>Зарегистрируйте идентификатор безопасности группы безопасности в службе HGS  

1. Получить идентификатор безопасности группы безопасности для защищенных узлов из администратору структуры и выполните следующую команду для регистрации в группу безопасности в службе HGS. 
   Повторно выполните команду, при необходимости для дополнительной группы. 
   Введите понятное имя для группы. 
   Он не должен совпадать с именем группы безопасности Active Directory. 

   ```powershell
   Add-HgsAttestationHostGroup -Name "<GuardedHostGroup>" -Identifier "<SID>"
   ```

2. Чтобы проверить, была добавлена группа, запустите [Get-HgsAttestationHostGroup](https://technet.microsoft.com/library/mt652172.aspx). 


