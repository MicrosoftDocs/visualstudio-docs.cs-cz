---
title: 'Postup: Sestavení postupně | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4911bb131f5c5c878b82865b3dee61fd7bedbe1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634159"
---
# <a name="how-to-build-incrementally"></a>Postup: Sestavení postupně

Při vytváření velkého projektu je důležité, aby dříve vytvořené součásti, které jsou stále aktuální, nebyly znovu sestaveny. Pokud jsou všechny cíle vytvořeny pokaždé, každé sestavení bude trvat dlouhou dobu k dokončení. Chcete-li povolit přírůstková sestavení (sestavení, ve kterých jsou znovu sestaveny pouze cíle, které nebyly vytvořeny před nebo cíle, které jsou zastaralé), microsoft build engine (MSBuild) může porovnat časová razítka vstupních souborů s časovými razítky výstupních souborů a určete, zda chcete cíl přeskočit, sestavit nebo částečně znovu sestavit. Však musí být mapování 1:1 mezi vstupy a výstupy. Transformace můžete použít k povolení cílů k identifikaci tohoto přímého mapování. Další informace o transformacích naleznete v tématu [Transformace](../msbuild/msbuild-transforms.md).

## <a name="specify-inputs-and-outputs"></a>Určení vstupů a výstupů

Cíl lze sestavit postupně, pokud jsou vstupy a výstupy zadány v souboru projektu.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Určení vstupů a výstupů pro cíl

- Použijte `Inputs` atributy a `Outputs` `Target` prvku. Například:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

MSBuild můžete porovnat časová razítka vstupních souborů s časová razítka výstupních souborů a určit, zda přeskočit, sestavit nebo částečně znovu sestavit cíl. V následujícím příkladu, pokud `@(CSFile)` je některý soubor v seznamu položek novější než soubor *hello.exe,* msbuild spustí cíl; v opačném případě bude přeskočen:

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Pokud jsou vstupy a výstupy zadány v cíli, může každý výstup mapovat pouze na jeden vstup nebo nemůže existovat žádné přímé mapování mezi výstupy a vstupy. V předchozí [úloze Csc](../msbuild/csc-task.md), například výstup *hello.exe*, nelze mapovat na žádný jednotlivý vstup - záleží na všech z nich.

> [!NOTE]
> Cíl, ve kterém neexistuje žádné přímé mapování mezi vstupy a výstupy bude vždy sestavení častěji než cíl, ve kterém každý výstup lze mapovat pouze jeden vstup, protože MSBuild nelze určit, které výstupy je třeba znovu sestavit, pokud některé vstupy byly změněny.

Úkoly, ve kterých můžete identifikovat přímé mapování mezi výstupy a vstupy, jako je [například úloha LC](../msbuild/lc-task.md), jsou nejvhodnější pro přírůstková sestavení, na rozdíl od úkolů, jako jsou [Csc](../msbuild/csc-task.md) a [Vbc](../msbuild/vbc-task.md), které vytvářejí jedno výstupní sestavení z několika vstupů.

## <a name="example"></a>Příklad

Následující příklad používá projekt, který vytváří soubory nápovědy pro hypotetický systém nápovědy. Projekt funguje tak, že převádí zdrojové soubory *TXT* na zprostředkující soubory *.help* *obsahu.* Projekt používá následující hypotetické úkoly:

- `GenerateContentFiles`: Převede soubory *TXT* na soubory *obsahu.*

- `BuildHelp`: Kombinuje soubory *obsahu* a soubory metadat XML a vytváří konečný soubor *.help.*

Projekt používá transformace k vytvoření mapování 1:1 mezi vstupy a `GenerateContentFiles` výstupy v úkolu. Další informace naleznete v [tématu Transformace](../msbuild/msbuild-transforms.md). `Output` Prvek je také nastaven tak, aby automaticky `GenerateContentFiles` používal výstupy z `BuildHelp` úkolu jako vstupy pro úlohu.

Tento soubor projektu `Convert` obsahuje `Build` cíle i cíle. A `GenerateContentFiles` `BuildHelp` úkoly jsou `Convert` umístěny v a `Build` cíle, respektive tak, aby každý cíl lze sestavit postupně. Pomocí `Output` prvku jsou výstupy `GenerateContentFiles` úkolu umístěny v `ContentFile` seznamu položek, kde je lze použít `BuildHelp` jako vstupy pro úkol. Použití `Output` prvku tímto způsobem automaticky poskytuje výstupy z jednoho úkolu jako vstupy pro jiný úkol, takže není nutné v jednotlivých úkolech ručně vypsat jednotlivé položky nebo seznamy položek.

> [!NOTE]
> Přestože `GenerateContentFiles` cíl může sestavit postupně, všechny výstupy z tohoto cíle `BuildHelp` jsou vždy požadovány jako vstupy pro cíl. MSBuild automaticky poskytuje všechny výstupy z jednoho cíle jako vstupy pro jiný cíl při použití `Output` prvku.

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <TXTFile Include="*.txt"/>
        <XMLFiles Include="\metadata\*.xml"/>
    </ItemGroup>

    <Target Name = "Convert"
        Inputs="@(TXTFile)"
        Outputs="@(TXTFile->'%(Filename).content')">

        <GenerateContentFiles
            Sources = "@(TXTFile)">
            <Output TaskParameter = "OutputContentFiles"
                ItemName = "ContentFiles"/>
        </GenerateContentFiles>
    </Target>

    <Target Name = "Build" DependsOnTargets = "Convert"
        Inputs="@(ContentFiles);@(XMLFiles)"
        Outputs="$(MSBuildProjectName).help">

        <BuildHelp
            ContentFiles = "@(ContentFiles)"
            MetadataFiles = "@(XMLFiles)"
            OutputFileName = "$(MSBuildProjectName).help"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Cíle](../msbuild/msbuild-targets.md)
- [Cílový prvek (MSBuild)](../msbuild/target-element-msbuild.md)
- [Transformace](../msbuild/msbuild-transforms.md)
- [Úkol CsC](../msbuild/csc-task.md)
- [Úloha Vbc](../msbuild/vbc-task.md)
