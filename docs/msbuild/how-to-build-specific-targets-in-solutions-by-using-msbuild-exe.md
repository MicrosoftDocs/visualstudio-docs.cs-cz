---
title: Použití programu MSBuild.exe k vytváření konkrétních cílů v řešeních
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
ms.openlocfilehash: 178dfcaf0bdf8296fd271cb7c4e5dd0bbd251d7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633925"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Postup: Vytvoření konkrétních cílů v řešeních pomocí programu MSBuild.exe

*MSBuild.exe* můžete použít k vytvoření konkrétní cíle konkrétních projektů v řešení.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Vytvoření konkrétního cíle konkrétního projektu v řešení

1. Na příkazovém `MSBuild.exe <SolutionName>.sln`řádku `<SolutionName>` zadejte , kde odpovídá název souboru řešení, které obsahuje cíl, který chcete spustit.

2. Zadejte cíl `-target:` za přepínačem \<ve formátu\<Název_>: TargetName>. Pokud název projektu obsahuje některý `%` `$`ze `@` `;`znaků `.` `(`, `)`, `'`, , `_` , , , nebo , nahraďte je v zadaném cílovém názvu.

## <a name="example"></a>Příklad

 Následující příklad provede `Rebuild` cíl `NotInSlnFolder` projektu a potom provede `Clean` cíl `InSolutionFolder` projektu, který je umístěn ve složce řešení *NewFolder.*

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Řešení potíží

Pokud chcete prozkoumat možnosti, které máte k dispozici, můžete k tomu použít možnost ladění poskytovanou službou MSBuild. Nastavte proměnnou `MSBUILDEMITSOLUTION=1` prostředí a vytvořte řešení. Tím se vytvoří soubor MSBuild s názvem * \<SolutionName>.sln.metaproj,* který zobrazuje interní zobrazení řešení MSBuild v době sestavení. Toto zobrazení můžete zkontrolovat a určit, jaké cíle jsou k dispozici pro sestavení.

Nevytvářejte s touto sadou proměnných prostředí, pokud nepotřebujete toto interní zobrazení. Toto nastavení může způsobit problémy se vytvářením projektů v řešení.

## <a name="see-also"></a>Viz také

- [Odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Msbuild](../msbuild/msbuild.md)
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
