---
title: Распространенные команды git bash для использования с GitHub
description: Список некоторых наиболее часто используемых команд в Git Bash при работе с GitHub.
author: eross-msft
ms.author: lizross
ms.date: 05/06/2019
ms.openlocfilehash: 4ce5d4d8ce382e9ba421c20595715ec473cca241
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70864994"
---
# <a name="common-git-bash-commands"></a>Распространенные команды git bash

Это некоторые наиболее часто используемые команды в Git bash, основанные на том, когда они будут использоваться в процессе создания и редактирования содержимого.

## <a name="master-branch-related"></a>Связанные с главной ветвью

В качестве основы для любой новой ветви всегда следует использовать Master.

| Command | Описание |
|---------|-------------|
| `git checkout master` | Переключение на главную базу из любой другой ветви |
| `git pull upstream master` | Обновление локальной копии главного репозитория в рабочей базе данных |

## <a name="branch-related"></a>Связанные с ветвью

| Command | Описание |
|---------|-------------|
| `git branch` | Просмотр существующих ветвей |
| `git checkout -B <name-of-branch>` | Создание новой ветви |
| `git checkout <name-of-branch>` | Изменить на другую ветвь |
| `git status` | Проверка того, что происходит в вашей ветви |
| `git branch -D <name-of-branch>` | Удаление существующей ветви (убедитесь, что вы не находитесь в ней) |

## <a name="check-in-related-done-as-a-group-in-order"></a>Запись после изменения (выполняется как группа, по порядку)

| Command | Описание |
|---------|-------------|
| `git add --all` | После сохранения работы добавьте ее в ветвь. |
| `git commit -m “public comment, including quotes”` | Зафиксируйте изменения в ветви |
| `git pull upstream master` | Обновление локальной копии главного репозитория в рабочей базе данных |
| `git push origin <name-of-branch>` | Отправка в удаленную версию локальной ветви |