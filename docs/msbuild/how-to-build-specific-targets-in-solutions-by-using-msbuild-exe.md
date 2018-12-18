---
title: 'Postupy: sestavování specifických cílů v řešení pomocí MSBuild.exe | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb1dc2885d64999ac9f4d12568fd7da29a783d8e
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880653"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Postupy: sestavování specifických cílů v řešení pomocí MSBuild.exe
Můžete použít *MSBuild.exe* k sestavování specifických cílů konkrétní projekty v řešení.  
  
#### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>K sestavení specifické cílem určitého projektu v řešení  
  
1.  Na příkazovém řádku zadejte `MSBuild.exe <SolutionName>.sln`, kde `<SolutionName>` odpovídá názvu souboru řešení, která obsahuje cíl, který chcete spustit.  
  
2. Zadejte cíl po `-target:` přepnout ve formátu \<ProjectName >:\<TargetName >. Pokud název projektu obsahuje některý ze znaků `%`, `$`, `@`, `;`, `.`, `(`, `)`, nebo `'`, nahraďte pomocí `_` v zadaném Název cíle.
  
## <a name="example"></a>Příklad  
 Následující příklad provede `Rebuild` cíl `NotInSlnFolder` projektu a potom provede `Clean` cíl `InSolutionFolder` projekt, který se nachází v *NewFolder* složku řešení.  
  
```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Poradce při potížích

Pokud chcete zkontrolovat dostupné možnosti, můžete k tomu možnost ladění nástrojem MSBuild k dispozici. Nastavte proměnnou prostředí `MSBUILDEMITSOLUTION=1` a sestavte řešení. To vytvoří soubor MSBuild s názvem  *\<SolutionName >. sln.metaproj* , který se teď zobrazují v MSBuild interní řešení v okamžiku sestavení. Můžete si prohlédnout toto zobrazení můžete zjistit, jaké cíle jsou k dispozici pro sestavení.

Nejdou sestavit pomocí této proměnné prostředí, pokud je třeba interní zobrazení. Toto nastavení může způsobit problémy sestavení projektů v řešení.

## <a name="see-also"></a>Viz také:  
 [Odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](../msbuild/msbuild.md)  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
