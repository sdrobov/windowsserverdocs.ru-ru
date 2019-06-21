---
Title: 'SMB: Файлам и принтерам, совместного использования портов должны быть открыты'
TOCTitle: 'SMB: File and printer sharing ports should be open'
ms.date: 07/02/2012
ms.prod: windows-server-threshold
ms.technology: storage
author: JasonGerend
manager: elizapo
ms.author: jgerend
ms.openlocfilehash: fae579347a43dfa361206e65032b1f3da512ec4a
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67284374"
---
# <a name="smb-file-and-printer-sharing-ports-should-be-open"></a>SMB: Файлам и принтерам, совместного использования портов должны быть открыты


Обновлено: 2 февраля 2011 г.

Область применения. Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 и Windows Server 2012, Windows Server 2008 R2

*В этом разделе рассматривается решение конкретной проблемы, обнаруженной при проверке, анализатор соответствия рекомендациям. Информация в этой статье применяются только к компьютерам, которые файл службы анализатор соответствия рекомендациям выполните с ними и возникают проблемы, описанной в этом разделе. Дополнительные сведения о рекомендациях и проверках см. в разделе* [анализатор соответствия рекомендациям](http://go.microsoft.com/fwlink/?linkid=122786%0d%0a).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Операционная система</strong></p></td>
<td><p>Windows Server</p></td>
</tr>
<tr class="even">
<td><p><strong>Продукта или компонента</strong></p></td>
<td><p>Файловые службы</p></td>
</tr>
<tr class="odd">
<td><p><strong>Уровень серьезности</strong></p></td>
<td><p>Ошибка</p></td>
</tr>
<tr class="even">
<td><p><strong>Категория</strong></p></td>
<td><p>Конфигурация</p></td>
</tr>
</tbody>
</table>

## <a name="issue"></a>Проблемы

> *Порты брандмауэра, необходимые для к файлам и принтерам, не открыть (порты 445 и 139).*

## <a name="impact"></a>Влияние

> *Компьютеры, не смогут получить доступ к общим папкам и другие службы сети на основе Server Message Block SMB на этом сервере.*

## <a name="resolution"></a>Разрешение

> *Включите к файлам и принтерам для обмена данными через брандмауэр компьютера.*

Для выполнения этой процедуры как минимум необходимо быть участником группы **Администраторы** (либо аналогичной).

## <a name="to-open-the-firewall-ports-to-enable-file-and-printer-sharing"></a>Чтобы открыть порты брандмауэра, чтобы включить к файлам и принтерам

1.  Откройте панель управления, нажмите кнопку **система и безопасность**, а затем нажмите кнопку **брандмауэра Windows**.

2.  В левой области щелкните **Дополнительные параметры**и в дереве консоли щелкните **правила для входящих подключений**.

3.  В разделе **правила для входящих подключений**, найдите правила **к файлам и принтерам (NB-сеанса-In)** и **к файлам и принтерам (SMB — входящий)** .

4.  Для каждого правила, щелкните правой кнопкой мыши правило и нажмите кнопку **включить правило**.

## <a name="additional-references"></a>Дополнительная справка

[Общее представление об общих папках и брандмауэре Windows](https://technet.microsoft.com/library/cc731402.aspx)()https://technet.microsoft.com/library/cc731402.aspx)

