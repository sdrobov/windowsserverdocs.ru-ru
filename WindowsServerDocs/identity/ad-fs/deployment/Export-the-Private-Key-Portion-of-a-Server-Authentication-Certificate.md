---
ms.assetid: cd4d4902-dcdf-49dd-8059-82a56bf4b585
title: Экспорт части сертификата аутентификации сервера с закрытым ключом
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 7837f1aeb5def401e199bf49d6fd5a204859fc4b
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965896"
---
# <a name="export-the-private-key-portion-of-a-server-authentication-certificate"></a>Экспорт части сертификата аутентификации сервера с закрытым ключом

Каждый сервер федерации в ферме службы федерации Active Directory (AD FS) \( AD FS \) должен иметь доступ к закрытому ключу сертификата проверки подлинности сервера. При реализации фермы серверов или веб-серверов федерации необходимо иметь один сертификат проверки подлинности. Этот сертификат должен быть выдан ЦС центра сертификации предприятия \( \) и должен иметь экспортируемый закрытый ключ. Закрытый ключ сертификата аутентификации сервера должен быть экспортируемым, чтобы его можно было предоставить всем серверам на ферме.  
  
Эта же концепция относится к фермам прокси-серверов федерации в том смысле, что все прокси сервера федерации в ферме должны совместно использовать частную часть одного сертификата проверки подлинности сервера.  
  
> [!NOTE]  
> Оснастка управления AD FS \- в относится к сертификатам проверки подлинности сервера для серверов федерации в качестве сертификатов связи служб.  
  
В зависимости от роли, которую будет воспроизводить этот компьютер, используйте эту процедуру на компьютере сервера федерации или прокси-сервера федерации, где установлен сертификат проверки подлинности сервера с закрытым ключом. По окончании процедуры можно импортировать этот сертификат на веб-сайт по умолчанию каждого сервера на ферме. Дополнительные сведения см. в разделе [Импорт сертификата проверки подлинности сервера на веб-сайт по умолчанию](Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md).  
  
Для выполнения этой процедуры требуется членство в группе **Администраторы** или в эквивалентной группе на локальном компьютере.  Просмотрите сведения об использовании соответствующих учетных записей и членстве в группах в [локальной среде и группах домена по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).   
  
### <a name="to-export-the-private-key-portion-of-a-server-authentication-certificate"></a>Экспорт части сертификата аутентификации сервера с закрытым ключом  
  
1. На **начальном** экране введите**службы IIS \( \) Диспетчер IIS**и нажмите клавишу ВВОД.  
  
2. В дереве консоли щелкните **ComputerName**.  
  
3. В центральной области дважды \- щелкните **Сертификаты сервера**.  
  
4. В центральной области щелкните правой кнопкой мыши \- сертификат, который необходимо экспортировать, и выберите пункт **Экспорт**.  
  
5. В диалоговом окне **Экспорт сертификатов** нажмите кнопку **…** .  
  
6. В окне **имя файла**введите **C: \\ **<em>намеофцертификате</em>, а затем нажмите кнопку **Открыть**.  
  
7. Введите пароль для сертификата, подтвердите его и нажмите кнопку **ОК**.  
  
8. Проверьте, успешно ли выполнен экспорт, убедившись, что заданный файл создан в заданном расположении.  
  
   > [!IMPORTANT]  
   > Для того чтобы этот сертификат можно было импортировать в локальное хранилище сертификатов на новом сервере, необходимо переместить файл на физический носитель и обеспечить его безопасность во время переноса на новый сервер. Очень важно обеспечить безопасность закрытого ключа. Если этот ключ скомпрометирован, безопасность всего развертывания AD FS, \( включая ресурсы в Организации и организации партнера по ресурсам, \) скомпрометирована.  
  
9. Импортируйте экспортированный сертификат аутентификации сервера в хранилище сертификатов на новом сервере до установки службы федерации. Дополнительные сведения об импорте сертификата см. в статье Импорт сертификата сервера \( [http: \/ \/ go.Microsoft.com \/ fwlink \/ ? LinkId \= 108283](https://go.microsoft.com/fwlink/?LinkId=108283) \) .  
  
## <a name="additional-references"></a>Дополнительные ссылки  
[Контрольный список. Настройка сервера федерации](Checklist--Setting-Up-a-Federation-Server.md)  
  
[Контрольный список. Настройка прокси-сервера федерации](Checklist--Setting-Up-a-Federation-Server-Proxy.md)  
  
[Требования к сертификатам для серверов федерации](../design/certificate-requirements-for-federation-servers.md)  
  
[Требования к сертификатам для прокси-серверов федерации](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807054(v=ws.11))  
  
