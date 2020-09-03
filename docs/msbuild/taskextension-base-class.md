---
title: Základní třída TaskExtension – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3dc771f16c7077549ba06d5cdda422319554d40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631702"
---
# <a name="taskextension-base-class"></a>TaskExtension – základní třída

Mnoho úloh dědí z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Tento řetěz dědičnosti přidá několik parametrů k úlohám, které jsou z nich odvozeny. Tyto parametry jsou uvedeny v tomto dokumentu.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry základních tříd.

|Parametr|Popis|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Volitelný <xref:Microsoft.Build.Framework.IBuildEngine> parametr.<br /><br /> Určuje rozhraní Build Engine dostupné pro úlohy. Modul sestavení automaticky nastaví tento parametr tak, aby umožňoval úkolům volat zpět do něj.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Volitelný <xref:Microsoft.Build.Framework.IBuildEngine2> parametr.<br /><br /> Určuje rozhraní Build Engine dostupné pro úlohy. Modul sestavení automaticky nastaví tento parametr tak, aby umožňoval úkolům volat zpět do něj.<br /><br /> Toto je vlastnost pohodlí, aby autoři úloh, které dědí z této třídy, nemuseli přetypovat hodnotu z `IBuildEngine` na `IBuildEngine2` .|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Volitelný <xref:Microsoft.Build.Framework.IBuildEngine3> parametr.<br /><br /> Určuje rozhraní modulu sestavení poskytované hostitelem.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Volitelný <xref:Microsoft.Build.Framework.ITaskHost> parametr.<br /><br /> Určuje instanci objektu hostitele (může mít hodnotu null). Modul sestavení nastavuje tuto vlastnost, pokud má rozhraní IDE hostitele přidružený objekt hostitele s touto konkrétní úlohou.|
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Volitelný <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametr jen pro čtení.<br /><br /> Získá `TaskLoggingHelperExtension` objekt, který obsahuje metody protokolování úkolů.|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
