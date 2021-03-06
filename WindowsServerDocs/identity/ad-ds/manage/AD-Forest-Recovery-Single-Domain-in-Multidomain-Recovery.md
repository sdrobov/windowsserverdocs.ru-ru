---
title: Восстановление леса AD — восстановление отдельного домена в лесу с несколькими доменами
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: 267541be-2ea7-4af6-ab34-8b5a3fedee2d
ms.technology: identity-adds
ms.openlocfilehash: 84ce874ea85cce7ea562fcd5169902086732b4c4
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86960846"
---
# <a name="ad-forest-recovery---recovering-a-single-domain-in-a-multidomain-forest"></a>Восстановление леса AD — восстановление отдельного домена в лесу с несколькими доменами

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

Возможны случаи, когда необходимо восстановить только один домен в лесу, который имеет несколько доменов, а не полное восстановление леса. В этом разделе приводятся рекомендации по восстановлению отдельного домена и возможных стратегий восстановления.  
  
Восстановление в одном домене представляет собой уникальную задачу перестроения серверов глобального каталога (GC). Например, если первый контроллер домена (DC) для домена восстанавливается из резервной копии, созданной на неделю раньше, то все остальные глобальные каталоги в лесу будут иметь более актуальные данные для этого домена, чем восстановленный контроллер домена. Для повторного установления согласованности данных GC существует несколько вариантов:  
  
- Отменяет размещение и повторное размещение восстановленного раздела доменов из всех глобальных каталогов в лесу, за исключением тех, которые находятся в восстановленном домене одновременно.  
- Выполните процедуру восстановления леса, чтобы восстановить домен, а затем удалите устаревшие объекты из GC в других доменах.  
  
В следующих разделах приводятся общие рекомендации по каждому параметру. Полный набор действий, которые необходимо выполнить для восстановления, зависит от разных сред Active Directory.  
  
## <a name="rehost-all-gcs"></a>Повторное размещение всех глобальных каталогов  

> [!WARNING]
> Пароль учетной записи администратора домена для всех доменов должен быть готов к использованию, если проблема не позволяет получить доступ к GC для входа в систему.  

Повторное размещение всех глобальных каталогов можно выполнить с помощью команд repadmin/унхост и repadmin/рехост (входит в состав repadmin/експерселп). Команды repadmin выполняются на каждом GC в каждом домене, который не восстанавливается. Необходимо убедиться, что все глобальные каталоги больше не хранят копию восстановленного домена. Чтобы добиться этого, сначала отменяйте размещение раздела домена с всех контроллеров домена для всех доменов, восстановленных без каких-либо устройств. После того как все глобальные каталоги больше не содержат секцию, ее можно разместить на своем компьютере. При повторном размещении рассмотрим структуру узла и репликации леса, например, завершите переразмещение одного контроллера домена на сайт, прежде чем переразмещать другие контроллеры этого сайта.  
  
Этот вариант может оказаться выгодным для небольшой организации, имеющей только несколько контроллеров домена для каждого домена. Все глобальные каталоги можно перестраивать на пятницу ночью и при необходимости выполнить полную репликацию для всех разделов домена только для чтения до понедельника утра. Но если необходимо восстановить большой домен, охватывающий сайты по всему миру, то при повторном размещении раздела домена только для чтения на всех глобальных каталогах для других доменов может значительно повлиять на операции и, возможно, потребуется время простоя.  
  
## <a name="remove-lingering-objects"></a>Удалить устаревшие объекты

Подобно процессу восстановления леса, вы восстанавливаете один контроллер домена из резервной копии в домене, который необходимо восстановить, выполняете очистку метаданных оставшихся контроллеров домена, а затем переустанавливаете AD DS для создания домена. В глобальных каталогах всех доменов леса удаляются устаревшие объекты для раздела, доступного только для чтения восстановленного домена.  

Источником для очистки устаревших объектов должен быть контроллер домена в восстановленном домене. Чтобы убедиться, что у исходного контроллера домена нет устаревших объектов для всех разделов предметной области, можно удалить глобальный каталог, если он был GC.  

Удаление устаревших объектов выгодно для крупных организаций, которые не могут снизить время простоя, связанные с другими вариантами.  

Дополнительные сведения см. [в разделе Удаление устаревших объектов с помощью repadmin](/previous-versions/windows/it-pro/windows-server-2003/cc785298(v=ws.10)).

## <a name="next-steps"></a>Дальнейшие шаги

- [Восстановление леса AD — необходимые условия](AD-Forest-Recovery-Prerequisties.md)  
- [Восстановление леса AD — Девисинг план восстановления пользовательского леса](AD-Forest-Recovery-Devising-a-Plan.md)  
- [Восстановление леса AD. обнаружение проблемы](AD-Forest-Recovery-Identify-the-Problem.md)
- [Восстановление леса AD. Определение способа восстановления](AD-Forest-Recovery-Determine-how-to-Recover.md)
- [Восстановление леса AD — выполнение начального восстановления](AD-Forest-Recovery-Perform-initial-recovery.md)  
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)  
- [Восстановление леса AD — часто задаваемые вопросы](AD-Forest-Recovery-FAQ.md)  
- [Восстановление леса Active Directory. Восстановление одного домена в лесу с несколькими доменами](AD-Forest-Recovery-Single-Domain-in-Multidomain-Recovery.md)  
- [Восстановление леса Active Directory — восстановление леса с контроллерами домена Windows Server 2003](AD-Forest-Recovery-Windows-Server-2003.md)  
