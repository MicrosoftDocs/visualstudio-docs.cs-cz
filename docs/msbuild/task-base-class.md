---
title: Základní třída úkolu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7d6e0870f809a30bc3feb7ecb7a7302b7729124
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631949"
---
# <a name="task-base-class"></a>Základní třída úkolu

Mnoho úkolů nakonec dědí z třídy. <xref:Microsoft.Build.Utilities.Task> Tato třída přidá několik parametrů k úkolům, které z nich vyplývají. Tyto parametry jsou uvedeny v tomto dokumentu.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry této základní třídy.

|Parametr|Popis|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Volitelný <xref:Microsoft.Build.Framework.IBuildEngine> parametr.<br /><br /> Určuje rozhraní modulu sestavení, které je k dispozici pro úkoly. Modul sestavení automaticky nastaví tento parametr tak, aby úkoly volat zpět do něj.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Volitelný <xref:Microsoft.Build.Framework.IBuildEngine2> parametr.<br /><br /> Určuje rozhraní modulu sestavení, které je k dispozici pro úkoly. Modul sestavení automaticky nastaví tento parametr tak, aby úkoly volat zpět do něj.<br /><br /> Toto je vlastnost pohodlí tak, aby autoři úloh dědí z `IBuildEngine` `IBuildEngine2`této třídy nemusí přetypovat hodnotu z do .|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Volitelný <xref:Microsoft.Build.Framework.IBuildEngine3> parametr.<br /><br /> Určuje rozhraní modulu sestavení poskytované hostitelem.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Volitelný <xref:Microsoft.Build.Framework.ITaskHost> parametr.<br /><br /> Určuje instanci objektu hostitele (může mít hodnotu null). Modul sestavení nastaví tuto vlastnost, pokud ide hostitele přidruží objekt hostitele k této konkrétní úloze.|
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Volitelný <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametr jen pro čtení.<br /><br /> Pomocné s posuzovacím objektem protokolování..|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
