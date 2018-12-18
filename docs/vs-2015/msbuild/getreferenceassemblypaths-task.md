---
title: Getreferenceassemblypaths – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b885443fba9b92e1d4004987988e4d743f3921d1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244477"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Vrátí odkaz na sestavení cesty různých platforem.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `GetReferenceAssemblyPaths` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Volitelné `String[]` výstupní parametr.<br /><br /> Vrátí cestu, na základě `TargetFrameworkMoniker` parametru. Pokud `TargetFrameworkMoniker` má hodnotu null nebo být prázdný, tato cesta bude `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Volitelné `String[]` výstupní parametr.<br /><br /> Vrátí cestu, na základě `TargetFrameworkMoniker` parametr bez zohlednění část zástupný název profilu. Pokud `TargetFrameworkMoniker` má hodnotu null nebo být prázdný, tato cesta bude `String.Empty`.|  
|`TargetFrameworkMoniker`|Volitelné `String` parametru.<br /><br /> Určuje moniker cílového rozhraní, která souvisí s cesty referenčního sestavení.|  
|`RootPath`|Volitelné `String` parametru.<br /><br /> Určuje kořenová cesta pro generování cesta pro odkaz na sestavení.|  
|`BypassFrameworkInstallChecks`|Volitelná [logická hodnota] (<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) parametru.<br /><br /> Pokud `true`, obchází základní kontroly, který `GetReferenceAssemblyPaths` provádí ve výchozím nastavení k zajištění, že určitá rozhraní modulu runtime jsou nainstalovány, v závislosti na cílové rozhraní.|  
|`TargetFrameworkMonikerDisplayName`|Volitelné `String` výstupní parametr.<br /><br /> Určuje zobrazovaný název pro moniker cílového rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě s parametry, které jsou uvedené v tabulce, zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



