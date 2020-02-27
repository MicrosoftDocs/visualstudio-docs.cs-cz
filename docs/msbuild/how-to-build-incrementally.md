---
title: 'Postupy: přírůstkové sestavení | Microsoft Docs'
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634159"
---
# <a name="how-to-build-incrementally"></a>Postupy: přírůstkové sestavení

Při sestavování velkého projektu je důležité, aby dříve vytvořené komponenty, které jsou stále aktuální, nebyly znovu sestaveny. Pokud jsou všechny cíle sestaveny pokaždé, dokončení každého sestavení bude trvat dlouhou dobu. Chcete-li povolit přírůstková sestavení (sestavení, ve kterých jsou znovu sestaveny pouze ty cíle, které nebyly vytvořeny dříve nebo jsou-li cíle zastaraly), Microsoft Build Engine (MSBuild) může porovnat časová razítka vstupních souborů s časovými razítky výstupních souborů a Určete, zda se má přeskočit, sestavit nebo částečně znovu sestavit cíl. Musí však existovat mapování 1:1 mezi vstupy a výstupy. Pomocí transformací můžete umožnit cílem identifikovat toto přímé mapování. Další informace o transformacích naleznete v tématu [transformace](../msbuild/msbuild-transforms.md).

## <a name="specify-inputs-and-outputs"></a>Zadat vstupy a výstupy

Cíl lze vytvořit postupně, pokud jsou vstupy a výstupy zadány v souboru projektu.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Určení vstupů a výstupů pro cíl

- Použijte atributy `Inputs` a `Outputs` elementu `Target`. Příklad:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

Nástroj MSBuild může porovnat časová razítka vstupních souborů s časovými razítky výstupních souborů a určit, zda má být cíl vynechán, sestavení nebo částečně znovu sestaven. V následujícím příkladu, pokud je libovolný soubor v seznamu `@(CSFile)` položky novější než soubor *Hello. exe* , MSBuild spustí cíl; v opačném případě se přeskočí:

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Pokud jsou vstupy a výstupy zadány v cíli, každý výstup může být namapován pouze na jeden vstup nebo nemůže být žádné přímé mapování mezi výstupem a vstupy. V předchozí [úloze CSC](../msbuild/csc-task.md), například výstup, *Hello. exe*, nelze namapovat na žádný jednotlivý vstup – závisí na všech nich.

> [!NOTE]
> Cíl, ve kterém neexistuje žádné přímé mapování mezi vstupy a výstupy, bude vždy sestavovat častěji než cíl, ve kterém každý výstup může být namapován pouze na jeden vstup, protože nástroj MSBuild nemůže určit, které výstupy je nutné znovu sestavit, pokud se změnily některé vstupy.

Úlohy, ve kterých můžete identifikovat přímé mapování mezi výstupy a vstupy, jako je například [úloha LC](../msbuild/lc-task.md), jsou nejvhodnější pro přírůstková sestavení, na rozdíl od úloh jako [CSC](../msbuild/csc-task.md) a [Vbc](../msbuild/vbc-task.md), což vytváří jedno výstupní sestavení z řady vstupů.

## <a name="example"></a>Příklad

V následujícím příkladu je použit projekt, který sestaví soubory s nápovědu pro hypotetický systém pro nápovědu. Projekt funguje tak, že převede zdrojové soubory *. txt* do souborů mezilehlého *. Content* , které jsou pak kombinovány se soubory metadat XML pro vytvoření finálního souboru *. help* používaného systémem help. Projekt používá následující hypotetické úkoly:

- `GenerateContentFiles`: převede soubory *. txt* na soubory *. Content* .

- `BuildHelp`: kombinuje soubory *obsahu* a soubory XML s metadaty k sestavení finálního souboru *. help* .

Projekt používá transformaci k vytvoření mapování 1:1 mezi vstupy a výstupy v úloze `GenerateContentFiles`. Další informace najdete v tématu [transformace](../msbuild/msbuild-transforms.md). Také prvek `Output` je nastaven tak, aby automaticky používal výstupy z úlohy `GenerateContentFiles` jako vstupy pro `BuildHelp` úlohu.

Tento soubor projektu obsahuje cíle `Convert` i `Build`. Úkoly `GenerateContentFiles` a `BuildHelp` se umístí do `Convert` a `Build` cílů tak, aby se každý cíl mohl sestavit postupně. Pomocí elementu `Output` jsou výstupy úlohy `GenerateContentFiles` umístěny v seznamu `ContentFile` položky, kde je lze použít jako vstupy pro úlohu `BuildHelp`. Použití prvku `Output` tímto způsobem automaticky poskytuje výstupy z jednoho úkolu jako vstupy pro jinou úlohu, takže nemusíte v jednotlivých úkolech vypisovat jednotlivé seznamy položek nebo položek ručně.

> [!NOTE]
> I když cílový `GenerateContentFiles` může sestavovat přírůstkově, všechny výstupy z tohoto cíle jsou vždy požadovány jako vstupy pro `BuildHelp` cíle. Nástroj MSBuild automaticky poskytuje všechny výstupy z jednoho cíle jako vstupy pro jiný cíl při použití prvku `Output`.

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
- [Target – element (MSBuild)](../msbuild/target-element-msbuild.md)
- [Transformace](../msbuild/msbuild-transforms.md)
- [CSc – úloha](../msbuild/csc-task.md)
- [Vbc – úloha](../msbuild/vbc-task.md)
