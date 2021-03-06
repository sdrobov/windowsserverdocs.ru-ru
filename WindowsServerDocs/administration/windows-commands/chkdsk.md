---
title: chkdsk
description: Справочная статья по команде Chkdsk, которая проверяет метаданные файловой системы и файловой системы тома на наличие логических и физических ошибок.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 62912a3c-d2cc-4ef6-9679-43709a286035
author: jasongerend
ms.author: jgerend
manager: lizapo
ms.date: 10/09/2019
ms.openlocfilehash: b98699b7e0925b43c15a602b9c193be9301a14ce
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85929992"
---
# <a name="chkdsk"></a>chkdsk

Проверяет файловую систему и метаданные файловой системы тома на наличие логических и физических ошибок. Если используется без параметров, **chkdsk** отображает только состояние тома и не исправляет ошибки. Если используется с параметрами **/f**, **/r**, **/x**или **/b** , он устраняет ошибки в томе.

> [!IMPORTANT]
> Членство в группе локальных **администраторов** (или аналогичной) является минимальным требованием для запуска **программы chkdsk**. Чтобы открыть окно командной строки от имени администратора, щелкните правой кнопкой мыши пункт **Командная строка** в меню **Пуск** и выберите команду **Запуск от имени администратора**.

> [!IMPORTANT]
> Прерывание работы **chkdsk** не рекомендуется. Однако отмена или прерывание работы **chkdsk** не должна покидать том, который больше поврежден, чем был запущен **программой CHKDSK** . Повторное выполнение **chkdsk** проверяет и должно восстанавливать все оставшееся повреждение тома.

> [!NOTE]
> CHKDSK может использоваться только для локальных дисков. Команда не может использоваться с буквой локального диска, которая была перенаправлена по сети.

## <a name="syntax"></a>Синтаксис

```
chkdsk [<volume>[[<path>]<filename>]] [/f] [/v] [/r] [/x] [/i] [/c] [/l[:<size>]] [/b]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<volume>` | Указывает букву диска (с последующим двоеточием), точку подключения или имя тома. |
| [ `[<path>]<filename>` | Используйте только с таблицей размещения файлов (FAT) и FAT32. Указывает расположение и имя файла или набора файлов, которые должна проверять **программа chkdsk** на наличие фрагментации. Вы можете использовать параметр **?** и **&#42;** подстановочных знаков для указания нескольких файлов. |
| /f | Исправляет ошибки на диске. Диск должен быть заблокирован. Если **chkdsk** не может заблокировать диск, появится сообщение с запросом на проверку диска при следующей перезагрузке компьютера. |
| /v | Отображает имя каждого файла в каждом каталоге при проверке диска. |
| /r | Поиск поврежденных секторов и восстановление сведений, доступных для чтения. Диск должен быть заблокирован. **/r** включает функции **/f**, а также дополнительный анализ ошибок физического диска. |
| /x | Принудительное отключение тома при необходимости. Все открытые дескрипторы диска становятся недействительными. **/x** также включает функции **/f**.  |
| /i | Используйте только с NTFS. Выполняет менее тщательные проверку записей индекса, что сокращает количество времени, необходимого для запуска **программы chkdsk**. |
| /C | Используйте только с NTFS. Не проверяет циклы в структуре папок, что сокращает количество времени, необходимого для запуска **программы chkdsk**.  |
| /l [: `<size>` ] | Используйте только с NTFS. Изменяет размер файла журнала до размера, который вы вводите. Если параметр size не задан, **/l** отображает текущий размер. |
| /b | Используйте только с NTFS. Очистка списка поврежденных кластеров на томе и повторное сканирование всех выделенных и свободных кластеров на наличие ошибок. **/b** включает функции **/r**. Используйте этот параметр после создания образа тома для нового жесткого диска. |
| /Scan | Используйте только с NTFS. Выполняет оперативную проверку тома. |
| /форцеоффлинефикс | Используйте только с NTFS (необходимо использовать с **/Scan**). Обход всего оперативного восстановления; все обнаруженные дефекты помещаются в очередь для восстановления в автономном режиме (например, `chkdsk /spotfix` ). |
| /перф | Используйте только с NTFS (необходимо использовать с **/Scan**). Использует больше системных ресурсов для выполнения проверки как можно быстрее. Это может негативно сказаться на производительности других задач, выполняемых в системе. |
| /spotfix | Используйте только с NTFS. Выполняет исправление на томе. |
| /сдклеануп | Используйте только с NTFS. Сбор мусора ненужных данных дескриптора безопасности (требует **/f**). |
| /оффлинесканандфикс | Запускает автономную проверку и исправление на томе. |
| /фриорфанедчаинс | Используйте только с FAT/FAT32/exFAT. Освобождает все потерянные цепочки кластеров, а не восстанавливает их содержимое. |
| /маркклеан | Используйте только с FAT/FAT32/exFAT. Помечает том как чистый, если не было обнаружено повреждений, даже если параметр **/f** не указан. |
| /? | Отображение справки в командной строке. |

## <a name="remarks"></a>Комментарии

- Параметр **/i** или **/c** сокращает время, необходимое для запуска **программы chkdsk** , пропуская определенные проверки тома.

- Если вы хотите исправить ошибки диска с помощью **chkdsk** , на диске не должно быть открытых файлов. Если файлы открыты, появляется следующее сообщение об ошибке:

  ```
  Chkdsk cannot run because the volume is in use by another process. Would you like to schedule this volume to be checked the next time the system restarts? (Y/N)
  ```

- Если вы решили проверить диск при следующей перезагрузке компьютера, **chkdsk** проверяет диск и автоматически исправляет ошибки при перезагрузке компьютера. Если раздел диска является загрузочным разделом, **chkdsk** автоматически перезагружает компьютер после проверки диска.

- Можно также использовать команду, `chkntfs /c` чтобы запланировать проверку тома при следующем перезапуске компьютера. Используйте `fsutil dirty set` команду, чтобы задать «грязный» бит тома (это указывает на повреждение), чтобы Windows выполняла **chkdsk** при перезапуске компьютера.

- Для проверки ошибок диска следует периодически использовать **chkdsk** в файловых системах FAT и NTFS. **Chkdsk** проверяет использование места на диске и дисков и предоставляет отчет о состоянии для каждой файловой системы. В отчете о состоянии отображаются ошибки, обнаруженные в файловой системе. Если запустить **chkdsk** без параметра **/f** в активном разделе, он может сообщить о ложных ошибках, так как он не может заблокировать диск.

- **Программа chkdsk** исправляет ошибки логических дисков только в том случае, если указан параметр **/f** . **Chkdsk** должна иметь возможность заблокировать диск для исправления ошибок.

  Поскольку восстановление в файловых системах FAT, как правило, изменяет таблицу выделения файлов диска и иногда приводит к потере данных, **chkdsk** может вывести сообщение с подтверждением следующего вида:

  ```
  10 lost allocation units found in 3 chains.
  Convert lost chains to files?
  ```

    - При нажатии клавиши **Y**Windows сохраняет каждую потерянную цепочку в корневом каталоге как файл с именем в формате file `<nnnn>` . chk. После завершения работы **chkdsk** вы можете проверить эти файлы, чтобы узнать, содержат ли они нужные данные.

    - Если нажать клавишу **N**, Windows исправит диск, но не сохранит содержимое потерянных единиц распределения.

- Если параметр **/f** не используется, **chkdsk** выводит сообщение о том, что файл должен быть исправлен, но не исправляет ошибки.

- Если вы используете `chkdsk /f*` на очень большом диске или на диске с очень большим количеством файлов (например, миллионы файлов), `chkdsk /f` выполнение может занять много времени.

- Используйте параметр **/r** для поиска ошибок физического диска в файловой системе и попытайтесь восстановить данные из всех затронутых секторов диска.

- Если указан параметр **/f** , то при наличии открытых файлов на диске **chkdsk** выводит сообщение об ошибке. Если параметр **/f** не указан и существуют открытые файлы, **chkdsk** может сообщать о потерянных единицах распределения на диске. Это может произойти, если открытые файлы еще не записаны в таблицу размещения файлов. Если **программа chkdsk** сообщает о сбое большого числа единиц распределения, попробуйте восстановить диск.

- Так как теневые копии общих папок исходный том не может быть заблокирован, пока **теневые копии общих папок** включен, выполнение **chkdsk** для исходного тома может сообщить ложные ошибки или вызвать непредвиденное завершение работы **программы chkdsk** . Однако можно проверить наличие ошибок в теневых копиях, запустив **chkdsk** в режиме только для чтения (без параметров) для проверки тома хранилища теневые копии общих папок.

- Команда **chkdsk** с различными параметрами доступна в консоли восстановления.

- При нечастом перезапуске серверов может потребоваться использовать команду **chkntfs** или `fsutil dirty query` команды, чтобы определить, задан ли уже установленный бит тома перед запуском программы chkdsk.

### <a name="understanding-exit-codes"></a>Основные сведения о кодах завершения

В следующей таблице перечислены коды завершения, которые сообщает **chkdsk** после завершения.

  | Код выхода | Описание |
  | --------- | ----------- |
  | 0 | Ошибки не найдены. |
  | 1 | Обнаружены и исправлены ошибки. |
  | 2 | Выполнена очистка диска (например, сборка мусора) или не выполнена очистка, поскольку не указан параметр **/f** . |
  | 3 | Не удалось проверить диск, ошибки не удалось исправить, или ошибки не были исправлены, поскольку не указан параметр **/f** . |

## <a name="examples"></a>Примеры

Чтобы проверить диск в диске D и исправить ошибки Windows, введите:

```
chkdsk d: /f
```

При возникновении ошибок **chkdsk** приостанавливает и отображает сообщения. **Программа chkdsk** завершает работу, отображая отчет со списком состояния диска. Невозможно открыть файлы на указанном диске, пока не завершится выполнение **программы chkdsk** .

Чтобы проверить все файлы на диске с файловой системой FAT в текущем каталоге для несмежных блоков, введите:

```
chkdsk *.*
```

**Chkdsk** отображает отчет о состоянии, а затем выводит список файлов, соответствующих спецификациям файлов с несмежными блоками.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
