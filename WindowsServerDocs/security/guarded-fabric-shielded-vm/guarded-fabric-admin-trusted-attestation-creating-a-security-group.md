---
title: Создайте группу безопасности для защищенных узлов и регистрации группы в службе HGS
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: a12c8494-388c-4523-8d70-df9400bbc2c0
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: fb84720b94746a3c5757037ceb5c9bc8c965ff7f
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66447163"
---
# <a name="create-a-security-group-for-guarded-hosts-and-register-the-group-with-hgs"></a>Создайте группу безопасности для защищенных узлов и регистрации группы в службе HGS

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

>[!IMPORTANT]
>Режим AD является устаревшим, начиная с Windows Server 2019. Для сред, где аттестацию доверенного платформенного МОДУЛЯ не поддерживается, Настройка [размещения Аттестация ключей](guarded-fabric-initialize-hgs-key-mode.md). Аттестация ключей узла обеспечивает аналогичный уверенность в режим AD и проще в настройке. 


В этом разделе описывается промежуточные этапы для подготовки узлов Hyper-V в качестве защищенных узлов, с помощью аттестацию с доверием администратора (режим AD). Перед выполнением следующих действий, выполните действия, описанные в [Настройка структуры DNS для узлов, которые станут защищенных узлов](guarded-fabric-configuring-fabric-dns-ad.md).


## <a name="create-a-security-group-and-add-hosts"></a>Создайте группу безопасности и добавьте узлы

1. Создайте новый **GLOBAL** безопасности в домене fabric и добавить узлы Hyper-V, которые будут выполняться экранированных виртуальных машин. Перезапустите узлы, чтобы обновить их членства в группе.

2. Используйте Get-ADGroup, чтобы получить идентификатор безопасности (SID) группы безопасности и предоставляют их администратор службы защиты узла. 

    ```powershell
    Get-ADGroup "Guarded Hosts"
    ```

    ![Команда Get-AdGroup с выходными данными](../media/Guarded-Fabric-Shielded-VM/guarded-host-get-adgroup.png)

## <a name="register-the-sid-of-the-security-group-with-hgs"></a>Зарегистрируйте идентификатор безопасности группы безопасности в службе HGS  

1. На сервер HGS выполните следующую команду для регистрации в группу безопасности в службе HGS. 
   Повторно выполните команду, при необходимости для дополнительной группы. 
   Введите понятное имя для группы. 
   Он не должен совпадать с именем группы безопасности Active Directory. 

   ```powershell
   Add-HgsAttestationHostGroup -Name "<GuardedHostGroup>" -Identifier "<SID>"
   ```

2. Чтобы проверить, была добавлена группа, запустите [Get-HgsAttestationHostGroup](https://technet.microsoft.com/library/mt652172.aspx). 

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Подтверждение аттестации](guarded-fabric-confirm-hosts-can-attest-successfully.md)


## <a name="see-also"></a>См. также

- [Развертывание службы защиты узла для защищенных узлов и экранированных виртуальных машин](guarded-fabric-deploying-hgs-overview.md)
