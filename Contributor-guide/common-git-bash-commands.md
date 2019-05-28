---
title: Общие команды Git Bash для использования с GitHub
description: Список некоторых из наиболее часто используемых команд в Git Bash при работе с GitHub.
author: eross-msft
ms.author: lizross
ms.date: 05/06/2019
ms.openlocfilehash: 210acaf2b7911892bcfd81b6bbe1975f141308a1
ms.sourcegitcommit: 7e54a1bcd31cd2c6b18fd1f21b03f5cfb6165bf3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461692"
---
# <a name="common-git-bash-commands"></a>Общие команды Git Bash

Ниже перечислены некоторые наиболее часто используемые команды в Git Bash, когда их использование в вашей создания содержимого на основе и редактирования процесса.

## <a name="master-branch-related"></a>Связанные ветви master

Master должна всегда использовать в качестве основы любой новой ветви.

| Command | Описание |
|---------|-------------|
| `git checkout master` | Перейти в главную ветвь с любой другой ветви |
| `git pull upstream master` | Обновить локальную копию базы данных master из репозитория рабочей среде |

## <a name="branch-related"></a>Связанные ветви

| Command | Описание |
|---------|-------------|
| `git branch` | Просмотра существующих ветвей |
| `git checkout -B <name-of-branch>` | Создайте новую ветвь |
| `git checkout <name-of-branch>` | Изменить на другую ветвь |
| `git status` | Проверьте, что происходит в ветви |
| `git branch -D <name-of-branch>` | Удаление существующей ветвью (убедиться, что вы не в его) |

## <a name="check-in-related-done-as-a-group-in-order"></a>Проверка в связанные (выполнено как группа, в порядке)

| Command | Описание |
|---------|-------------|
| `git add --all` | Сохраните работу и добавьте его в ветвь |
| `git commit -m “public comment, including quotes”` | Зафиксируйте изменения в ветвь |
| `git pull upstream master` | Обновить локальную копию базы данных master из репозитория рабочей среде |
| `git push origin <name-of-branch>` | Отправка на удаленный версию локальной ветви |