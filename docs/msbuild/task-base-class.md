---
title: Třída Task Base | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631949"
---
# <a name="task-base-class"></a>Task – základní třída

Mnohé úlohy mají v konečném důsledku dědění z <xref:Microsoft.Build.Utilities.Task> třídy. Tato třída přidá několik parametrů do úkolů, které jsou z nich odvozeny. Tyto parametry jsou uvedeny v tomto dokumentu.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry této základní třídy.

|Parametr|Popis|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Volitelný <xref:Microsoft.Build.Framework.IBuildEngine> parametr.<br /><br /> Určuje rozhraní Build Engine dostupné pro úlohy. Modul sestavení automaticky nastaví tento parametr tak, aby umožňoval úkolům volat zpět do něj.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Volitelný <xref:Microsoft.Build.Framework.IBuildEngine2> parametr.<br /><br /> Určuje rozhraní Build Engine dostupné pro úlohy. Modul sestavení automaticky nastaví tento parametr tak, aby umožňoval úkolům volat zpět do něj.<br /><br /> Toto je vlastnost pohodlí, aby autoři úloh, které dědí z této třídy, nemuseli přetypovat hodnotu z `IBuildEngine` na `IBuildEngine2` .|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Volitelný <xref:Microsoft.Build.Framework.IBuildEngine3> parametr.<br /><br /> Určuje rozhraní modulu sestavení poskytované hostitelem.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Volitelný <xref:Microsoft.Build.Framework.ITaskHost> parametr.<br /><br /> Určuje instanci objektu hostitele (může mít hodnotu null). Modul sestavení nastavuje tuto vlastnost, pokud má rozhraní IDE hostitele přidružený objekt hostitele s touto konkrétní úlohou.|
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Volitelný <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametr jen pro čtení.<br /><br /> Objekt pomocníka protokolování..|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
