---
title: Шаг 8. Настройка INET1
description: 'Этот раздел является частью руководства по лаборатории тестирования: демонстрация многосайтового развертывания DirectAccess для Windows Server 2016'
manager: brianlic
ms.prod: windows-server
ms.technology: networking-da
ms.topic: article
ms.assetid: 693acb5c-dffc-4484-8286-163bb67724c9
ms.author: coreyp
author: coreyp-at-msft
ms.openlocfilehash: ca8a49e612bef9c4a72c47e8d0e147a900686f84
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861547"
---
# <a name="step-8-configure-inet1"></a>ШАГ 8. Настройка INET1

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Чтобы разрешить клиентским компьютерам подключаться к серверам удаленного доступа через Интернет, необходимо настроить запись DNS для 2-EDGE1 в INET1.  
  
### <a name="to-create-the-2-edge1-dns-entry"></a>Создание записи DNS 2-EDGE1  
  
1.  На **начальном** экране введите**днсмгмт. msc**и нажмите клавишу ВВОД.  
  
2.  В дереве консоли откройте **зоны прямого просмотра**, щелкните **contoso.com**, щелкните правой кнопкой мыши **contoso.com**, а затем выберите **новый узел (A или AAAA)** .  
  
3.  В списке **имя**введите **2-EDGE1**. В списке **IP-адрес**введите **131.107.0.20**. Щелкните **Добавить узел**, после чего нажмите **OK**, а затем — **Готово**.  
  


