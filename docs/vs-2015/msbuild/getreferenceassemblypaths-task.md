---
title: Úloha GetReferenceAssemblyPaths – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f771f3c769ea41979210058a58dc1d0d125a4ffe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149474"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vrátí cesty referenčního sestavení různých rozhraní.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `GetReferenceAssemblyPaths` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Volitelný `String[]` výstupní parametr.<br /><br /> Vrátí cestu na základě `TargetFrameworkMoniker` parametru. Pokud má `TargetFrameworkMoniker` hodnotu null nebo je prázdná, bude tato cesta `String.Empty` .|  
|`FullFrameworkReferenceAssemblyPaths`|Volitelný `String[]` výstupní parametr.<br /><br /> Vrátí cestu na základě `TargetFrameworkMoniker` parametru bez zvážení části profilu monikeru. Pokud má `TargetFrameworkMoniker` hodnotu null nebo je prázdná, bude tato cesta `String.Empty` .|  
|`TargetFrameworkMoniker`|Volitelný `String` parametr.<br /><br /> Určuje moniker cílového rozhraní .NET Framework, který je přidružen k referenčním cestám sestavení.|  
|`RootPath`|Volitelný `String` parametr.<br /><br /> Určuje kořenovou cestu, která se má použít k vygenerování cesty referenčního sestavení.|  
|`BypassFrameworkInstallChecks`|Volitelné [Boolean] (<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->ukazatele.<br /><br /> Pokud `true` , obchází základní kontroly, které `GetReferenceAssemblyPaths` jsou ve výchozím nastavení prováděny, aby bylo zajištěno, že jsou v závislosti na cílové architektuře nainstalovány konkrétní prostředí modulu runtime.|  
|`TargetFrameworkMonikerDisplayName`|Volitelný `String` výstupní parametr.<br /><br /> Určuje zobrazovaný název pro moniker cílového rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
