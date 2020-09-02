---
title: Třída Task Base | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b1d82356d2f19388fd642214d03c1a1097b81ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149459"
---
# <a name="task-base-class"></a>Třída Base úlohy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)
