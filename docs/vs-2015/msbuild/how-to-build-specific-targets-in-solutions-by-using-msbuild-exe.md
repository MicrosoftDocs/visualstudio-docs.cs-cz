---
title: 'Postupy: sestavování specifických cílů v řešení pomocí MSBuild.exe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bfef86b8ea82077ba7fe3f753f9835c06c3380a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156658"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Postupy: Sestavování specifických cílů v řešení pomocí nástroje MSBuild.exe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít MSBuild.exe k sestavení specifických cílů konkrétních projektů v řešení.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Sestavení konkrétního cíle konkrétního projektu v řešení  
  
1. Do příkazového řádku zadejte `MSBuild.exe <SolutionName>.sln` , kde `<SolutionName>` odpovídá názvu souboru řešení, které obsahuje cíl, který chcete spustit.  
  
2. Zadejte cíl za přepínačem **/t** ve formátu *ProjectName*:*cílový_název*.  
  
## <a name="example"></a>Příklad  
 Následující příklad provede `Rebuild` cíl `NotInSlnFolder` projektu a poté provede `Clean` cíl `InSolutionFolder` projektu, který je umístěn ve `NewFolder` složce řešení.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Viz také  
 [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Nástroji](msbuild.md)  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
