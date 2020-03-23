---
title: Úkol OutOutOutOutDateItems | Dokumenty společnosti Microsoft
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: bfa60ff0f7e4060f5725fe54bd5950d858b86a22
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272402"
---
# <a name="getoutofdateitems-task"></a>Úloha GetOutOfDateItems

Pomocná úloha, která čte staré tlogy, zapisuje nové tlogy a vrací sadu položek, které nejsou aktuální.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **GetOutOfDateItems.**

|Parametr|Popis|
|---------------|-----------------|
|**Kontrola vzájemných závislostí**|Volitelný **parametr bool.**|
|**PříkazNázev metadat**|Volitelný parametr **řetězce.**|
|**Název metadat závislostí**|Volitelný parametr **řetězce.**|
|**Vzájemné závislosti Has**|Volitelný výstupní parametr **bool.**|
|**Zastaralé zdroje**|Volitelný výstupní parametr **ITaskItem[].**|
|**VýstupyNázev metadat**|Povinný parametr **řetězce.**|
|**Zdrojů**|Volitelný parametr **ITaskItem[].**|
|**TlogDirectory**|Povinný parametr **řetězce.**|
|**TLogNamePrefix**|Povinný parametr **řetězce.**|

## <a name="see-also"></a>Viz také

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)