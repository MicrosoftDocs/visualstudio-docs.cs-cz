---
title: Cílový prvek (MSBuild) | Dokumenty společnosti Microsoft
ms.date: 06/13/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 472d4c9c4c44176048a1bfd8c0791a1a406b95bd
ms.sourcegitcommit: 8ff6c6975148ce43bdac21c8995fbab910c312fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2020
ms.locfileid: "80375553"
---
# <a name="target-element-msbuild"></a>Cílový prvek (MSBuild)

Obsahuje sadu úloh pro MSBuild provádět postupně.

 \<> \<> projektu

## <a name="syntax"></a>Syntaxe

```xml
<Target Name="Target Name"
        Inputs="Inputs"
        Outputs="Outputs"
        Returns="Returns"
        KeepDuplicateOutputs="true/false"
        BeforeTargets="Targets"
        AfterTargets="Targets"
        DependsOnTargets="DependentTarget"
        Condition="'String A' == 'String B'"
        Label="Label">
    <Task>... </Task>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <OnError... />
</Target>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Požadovaný atribut.<br /><br /> Název cíle Cílový název může obsahovat `$@()%*?.`libovolný znak s výjimkou .|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Pokud je podmínka `false`vyhodnocena na , cíl neprovede tělo cíle nebo `DependsOnTargets` žádné cíle, které jsou nastaveny v atributu. Další informace o podmínkách naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).|
|`Inputs`|Nepovinný atribut.<br /><br /> Soubory, které tvoří vstupy do tohoto cíle. Více souborů je odděleno středníky. Časová razítka souborů budou porovnána s časovými razítky souborů `Outputs` `Target` v souborech, aby bylo možné určit, zda je aktuální. Další informace naleznete [v tématu Přírůstková sestavení](../msbuild/incremental-builds.md), [Postup: Sestavení postupně](../msbuild/how-to-build-incrementally.md)a [Transformace](../msbuild/msbuild-transforms.md).|
|`Outputs`|Nepovinný atribut.<br /><br /> Soubory, které tvoří výstupy do tohoto cíle. Více souborů je odděleno středníky. Časová razítka souborů budou porovnána s časovými razítky souborů `Inputs` `Target` v souborech, aby bylo možné určit, zda je aktuální. Další informace naleznete [v tématu Přírůstková sestavení](../msbuild/incremental-builds.md), [Postup: Sestavení postupně](../msbuild/how-to-build-incrementally.md)a [Transformace](../msbuild/msbuild-transforms.md).|
|`Returns`|Nepovinný atribut.<br /><br /> Sada položek, které budou k dispozici pro úkoly, které vyvolávají tento cíl, například úkoly MSBuild. Více cílů je odděleno středníky. Pokud cíle v souboru `Returns` nemají žádné atributy, výstupní atributy se místo toho používají pro tento účel.|
|`KeepDuplicateOutputs`|Volitelný logický atribut.<br /><br /> Pokud `true`jsou zaznamenány více odkazů na stejnou položku v cílové vrátí.  Ve výchozím nastavení `false`je tento atribut .|
|`BeforeTargets`|Nepovinný atribut.<br /><br /> Seznam cílových názvů oddělených středníkem.  Pokud je zadán, označuje, že tento cíl by měl být spuštěn před zadaným cílem nebo cíli. To umožňuje autorovi projektu rozšířit existující sadu cílů bez jejich přímé úpravy. Další informace naleznete v [tématu Target build order](../msbuild/target-build-order.md).|
|`AfterTargets`|Nepovinný atribut.<br /><br /> Seznam cílových názvů oddělených středníkem. Pokud je zadán, označuje, že tento cíl by měl běžet za zadaný cíl nebo cíle. To umožňuje autorovi projektu rozšířit existující sadu cílů bez jejich přímé úpravy. Další informace naleznete v [tématu Target build order](../msbuild/target-build-order.md).|
|`DependsOnTargets`|Nepovinný atribut.<br /><br /> Cíle, které musí být provedeny před provedením tohoto cíle nebo může dojít k analýze závislosti nejvyšší úrovně. Více cílů je odděleno středníky.|
|`Label`|Nepovinný atribut.<br /><br /> Identifikátor, který může identifikovat nebo objednat systémové a uživatelské prvky.|

### <a name="child-elements"></a>Podřízené prvky

| Element | Popis |
| - | - |
| [Úkol](../msbuild/task-element-msbuild.md) | Vytvoří a provede instanci úlohy MSBuild. V cíli může být nula nebo více úkolů. |
| [Propertygroup](../msbuild/propertygroup-element-msbuild.md) | Obsahuje sadu uživatelem `Property` definovaných prvků. Počínaje rozhraním .NET Framework 3.5 může `Target` prvek obsahovat `PropertyGroup` prvky. |
| [Skupina položek](../msbuild/itemgroup-element-msbuild.md) | Obsahuje sadu uživatelem `Item` definovaných prvků. Počínaje rozhraním .NET Framework 3.5 může `Target` prvek obsahovat `ItemGroup` prvky. Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md). |
| [Přichybě](../msbuild/onerror-element-msbuild.md) | Způsobí, že jeden nebo `ContinueOnError` více cílů provést, `false`pokud je atribut ErrorAndStop (nebo ) pro neúspěšný úkol. V cíli může `OnError` být nula nebo více prvků. Pokud `OnError` jsou přítomny prvky, musí `Target` být poslední prvky v prvku.<br /><br /> Informace o `ContinueOnError` atributu naleznete v tématu [Task element (MSBuild)](../msbuild/task-element-msbuild.md). |

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Požadovaný kořenový prvek souboru projektu MSBuild. |

## <a name="remarks"></a>Poznámky

 První cíl ke spuštění je určen v době běhu. Cíle mohou mít závislosti na jiných cílech. Například cíl pro nasazení závisí na cíl pro kompilaci. Modul MSBuild provádí závislosti v pořadí, ve kterém `DependsOnTargets` se zobrazí v atributu zleva doprava. Další informace naleznete v tématu [Cíle](../msbuild/msbuild-targets.md).

 MSBuild závisí na pořadí importu a poslední definice `Name` cíle s určitým atributem je použitá definice.

 Cíl je spuštěn pouze jednou během sestavení, i v případě, že více než jeden cíl má závislost na něm.

 Pokud cíl je přeskočen, `Condition` protože `false`jeho atribut vyhodnocuje na , může `Condition` být stále `true` spuštěna, pokud je vyvolána později v sestavení a jeho atribut vyhodnotí v té době.

 Před MSBuild `Target` 4, vrátil všechny položky, které byly zadány v atributu. `Outputs`  Chcete-li to provést, MSBuild musel zaznamenat tyto položky v případě, že úkoly později v sestavení požadované. Protože neexistoval žádný způsob, jak označit, které cíle měly výstupy, které `Outputs` by volající `Target`vyžadovali, MSBuild akumuloval všechny položky ze všech na všech vyvolaných s. To vedlo k problémům s škálováním pro sestavení, která měla velký počet výstupních položek.

 Pokud uživatel zadá `Returns` na `Target` libovolný prvek v projektu, pak pouze ty `Target`s, které mají `Returns` atribut zaznamenat tyto položky.

 A `Target` může obsahovat `Outputs` atribut `Returns` i atribut.  `Outputs`se používá `Inputs` s k určení, zda cíl je aktuální. `Returns`, pokud je k dispozici, přepíše hodnotu `Outputs` a určí, které položky jsou vráceny volajícím.  Pokud `Returns` není k `Outputs` dispozici, pak budou k dispozici volajícím s výjimkou případu popsaného výše.

 Před MSBuild 4, kdykoli `Target` zahrnuty více odkazů na `Outputs`stejnou položku v jeho , tyto duplicitní položky by být zaznamenány. Ve velmi velkých sestaveních, které měly velký počet výstupů a mnoho vzájemně propojených projektů, by to způsobilo, že by došlo k plýtvání velkým množstvím paměti, protože duplicitní položky nebyly k ničemu. Pokud `KeepDuplicateOutputs` je atribut `true`nastaven na , tyto duplikáty jsou zaznamenány.

## <a name="example"></a>Příklad

 Následující příklad kódu `Target` ukazuje prvek, `Csc` který provede úlohu.

```xml
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">
    <Csc Sources="@(CSFile)"
          TargetType="library"
          Resources="@(CompiledResources)"
          EmitDebugInformation="$(includeDebugInformation)"
          References="@(Reference)"
          DebugType="$(debuggingType)" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Viz také

- [Cíle](../msbuild/msbuild-targets.md)
- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
