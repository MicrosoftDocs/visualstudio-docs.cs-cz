---
title: Použití MSBuild.exe k sestavování specifických cílů v řešeních
description: Naučte se používat MSBuild.exe příkazového řádku k sestavování specifických cílů konkrétních projektů v řešeních.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94fcd9e1ed16b86caf65b9c7fab44ba4f93b7a7a
ms.sourcegitcommit: 55bc9df751a21656de8cc5b6dbd8a2a1915ec690
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2021
ms.locfileid: "99572899"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Postupy: sestavování specifických cílů v řešení pomocí MSBuild.exe

Můžete použít *MSBuild.exe* k sestavení specifických cílů konkrétních projektů v řešení.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Sestavení konkrétního cíle konkrétního projektu v řešení

1. Do příkazového řádku zadejte `MSBuild.exe <SolutionName>.sln` , kde `<SolutionName>` odpovídá názvu souboru řešení, které obsahuje cíl, který chcete spustit.

2. Zadejte cíl za `-target:` přepínačem ve formátu \<ProjectName> : \<TargetName> . Pokud název projektu obsahuje některý ze znaků `%` , `$` ,,, `@` , `;` `.` `(` , `)` , nebo `'` , nahraďte je `_` v zadaném cílovém názvu.

## <a name="example"></a>Příklad

 Následující příklad provede `Rebuild` cíl `NotInSlnFolder` projektu a poté provede `Clean` cíl `InSolutionFolder` projektu, který je umístěn ve složce řešení *NewFolder* .

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Řešení potíží

Pokud chcete prostudovat možnosti, které máte k dispozici, můžete k tomu použít možnost ladění poskytovanou nástrojem MSBuild. Nastavte proměnnou prostředí `MSBUILDEMITSOLUTION=1` a sestavte řešení. Tím se vytvoří soubor MSBuild s názvem *\<SolutionName> . sln. metaproj* , který ukazuje interní pohled nástroje MSBuild o řešení v čase sestavení. Můžete zkontrolovat toto zobrazení, abyste zjistili, jaké cíle jsou k dispozici pro sestavení.

Nevytvářejte s touto sadou proměnných prostředí, pokud nepotřebujete toto interní zobrazení. Toto nastavení může způsobit problémy při vytváření projektů ve vašem řešení. Místo toho hledejte v [binárním protokolu](obtaining-build-logs-with-msbuild.md#save-a-binary-log) .

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k příkazovému řádku](../msbuild/msbuild-command-line-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
