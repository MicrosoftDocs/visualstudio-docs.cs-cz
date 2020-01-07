---
title: Target – element (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: c69ee5758d5c6e513af853a8d7589057c6537956
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566420"
---
# <a name="target-element-msbuild"></a>Target – element (MSBuild)
Obsahuje sadu úloh, které [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] spustit sekvenčně.

 \<projektu > \<Target >

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

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Požadovaný atribut.<br /><br /> Název cíle|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Pokud je podmínka vyhodnocena jako `false`, cíl nespustí tělo cíle nebo žádné cíle, které jsou nastaveny v atributu `DependsOnTargets`. Další informace o podmínkách najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|
|`Inputs`|Nepovinný atribut.<br /><br /> Soubory, které tvoří vstupy do tohoto cíle. Několik souborů je oddělených středníky. Časová razítka souborů budou porovnána s časovými razítky souborů v `Outputs`, aby bylo možné určit, zda je `Target` aktuální. Další informace naleznete v tématu [přírůstkové sestavení](../msbuild/incremental-builds.md), [Postupy: sestavení přírůstkově](../msbuild/how-to-build-incrementally.md)a [transformace](../msbuild/msbuild-transforms.md).|
|`Outputs`|Nepovinný atribut.<br /><br /> Soubory, které tvoří výstup do tohoto cíle. Několik souborů je oddělených středníky. Časová razítka souborů budou porovnána s časovými razítky souborů v `Inputs`, aby bylo možné určit, zda je `Target` aktuální. Další informace naleznete v tématu [přírůstkové sestavení](../msbuild/incremental-builds.md), [Postupy: sestavení přírůstkově](../msbuild/how-to-build-incrementally.md)a [transformace](../msbuild/msbuild-transforms.md).|
|`Returns`|Nepovinný atribut.<br /><br /> Sada položek, které budou zpřístupněny pro úlohy, které vyvolávají tento cíl, například úlohy MSBuild. Více cílů je odděleno středníky. Pokud cíle v souboru nemají žádné `Returns` atributy, místo toho se pro tento účel použijí atributy výstupy.|
|`KeepDuplicateOutputs`|Volitelný logický atribut.<br /><br /> Pokud `true`, jsou zaznamenávány více odkazů na stejnou položku v rámci vrácených cílů.  Ve výchozím nastavení je tento atribut `false`.|
|`BeforeTargets`|Nepovinný atribut.<br /><br /> Seznam cílových názvů oddělený středníkem  Je-li tento parametr zadán, označuje, že tento cíl bude spuštěn před zadaným cílem nebo cílem. Tím umožníte, aby autor projektu rozšířil existující sadu cílů beze změny přímo. Další informace najdete v tématu [cílové pořadí sestavení](../msbuild/target-build-order.md).|
|`AfterTargets`|Nepovinný atribut.<br /><br /> Seznam cílových názvů oddělený středníkem Když se tato parametr zadá, označuje, že se má tento cíl spustit po zadaném cíli nebo cíli. Tím umožníte, aby autor projektu rozšířil existující sadu cílů beze změny přímo. Další informace najdete v tématu [cílové pořadí sestavení](../msbuild/target-build-order.md).|
|`DependsOnTargets`|Nepovinný atribut.<br /><br /> Cíle, které je třeba provést před provedením tohoto cíle, nebo může dojít k analýze závislostí na nejvyšší úrovni. Více cílů je odděleno středníky.|
|`Label`|Nepovinný atribut.<br /><br /> Identifikátor, který může identifikovat nebo seřadit systémové a uživatelské prvky.|

### <a name="child-elements"></a>Podřízené prvky

| Prvek | Popis |
| - | - |
| [Úloha](../msbuild/task-element-msbuild.md) | Vytvoří a spustí instanci úlohy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. V cíli může být nula nebo více úkolů. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Obsahuje sadu uživatelsky definovaných prvků `Property`. Počínaje .NET Framework 3,5 `Target` prvek může obsahovat `PropertyGroup` elementy. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Obsahuje sadu uživatelsky definovaných prvků `Item`. Počínaje .NET Framework 3,5 `Target` prvek může obsahovat `ItemGroup` elementy. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md). |
| [OnError](../msbuild/onerror-element-msbuild.md) | Způsobí provedení jednoho nebo více cílů, pokud je atribut `ContinueOnError` ErrorAndStop (nebo `false`) pro neúspěšnou úlohu. V cíli může být nula nebo více `OnError` prvků. Pokud `OnError` prvky jsou přítomny, musí být poslední prvky v elementu `Target`.<br /><br /> Informace o atributu `ContinueOnError` naleznete v tématu [Task element (MSBuild)](../msbuild/task-element-msbuild.md). |

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="remarks"></a>Poznámky
 První cíl, který má být spuštěn, je určen v době běhu. Cíle můžou mít závislosti na jiných cílech. Například cíl pro nasazení závisí na cíli pro kompilaci. Modul [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] spouští závislosti v pořadí, ve kterém jsou uvedeny v atributu `DependsOnTargets`, zleva doprava. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md).

 MSBuild je závislý na pořadí importu a poslední definice cíle s konkrétním `Name` atributem je použitá definice.

 Cíl se spustí pouze jednou během sestavení, i když na něm závisí více než jeden cíl.

 Pokud je cíl vynechán, protože se jeho `Condition` atribut vyhodnocuje jako `false`, může být stále proveden, pokud je vyvolán později v sestavení a jeho atribut `Condition` se vyhodnotí jako `true` v daném čase.

 Před MSBuild 4 `Target` vrátila všechny položky, které byly zadány v atributu `Outputs`.  Nástroj MSBuild musel tyto položky zaznamenat v případě, že je požaduje, později v sestavení. Vzhledem k tomu, že neexistuje žádný způsob, jak určit, které cíle obsahovaly výstupy, které by volající vyžadovaly, nástroj MSBuild shromáždil všechny položky ze všech `Outputs` všech vyvolaných `Target`s. To vede k škálování problémů pro sestavení, která měla velký počet výstupních položek.

 Pokud uživatel určí `Returns` na jakémkoli `Target` elementu v projektu, pak pouze ty `Target`s, které mají atribut `Returns` pro záznam těchto položek.

 `Target` může obsahovat atribut `Outputs` a atribut `Returns`.  `Outputs` se používá s `Inputs` k určení, jestli je cíl aktuální. `Returns`je-li k dispozici, přepíše hodnotu `Outputs` a určí, které položky se vrátí volajícím.  Pokud `Returns` není k dispozici, `Outputs` bude zpřístupněn volajícím, s výjimkou výše popsaného případu.

 Před tím, než nástroj MSBuild 4 pokaždé, když `Target` do své `Outputs`zahrnout více odkazů na stejnou položku, budou tyto duplicitní položky zaznamenány. Ve velmi rozsáhlých sestaveních, která měla velký počet výstupů a mnoho vzájemně závislých projektů, by to znamenalo neplýtvání velkého množství paměti, protože duplicitní položky nebyly žádného použití. Je-li atribut `KeepDuplicateOutputs` nastaven na hodnotu `true`, jsou tyto duplicity zaznamenávány.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `Target` element, který spouští úlohu `Csc`.

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

## <a name="see-also"></a>Viz také:
- [Cíle](../msbuild/msbuild-targets.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
