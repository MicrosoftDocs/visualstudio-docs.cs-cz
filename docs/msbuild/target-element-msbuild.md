---
title: Target – element (MSBuild) | Microsoft Docs
description: Seznamte se s cílovým elementem MSBuild, který obsahuje sadu úloh, které nástroj MSBuild provede postupně.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 16b8533bed128199a4eb0b6e7171ed9c674d62f4
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048049"
---
# <a name="target-element-msbuild"></a>Target – element (MSBuild)

Obsahuje sadu úloh, které má nástroj MSBuild spustit sekvenčně.

 \<Project> \<Target>

## <a name="syntax"></a>Syntax

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
|`Name`|Požadovaný atribut.<br /><br /> Název cíle Název cíle může obsahovat libovolný znak s výjimkou `$@()%*?.` .|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Pokud je podmínka vyhodnocena jako `false` , cíl nespustí tělo cíle nebo žádné cíle, které jsou nastaveny v `DependsOnTargets` atributu. Další informace o podmínkách najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|
|`Inputs`|Nepovinný atribut.<br /><br /> Soubory, které tvoří vstupy do tohoto cíle. Několik souborů je oddělených středníky. Časová razítka souborů budou porovnána s časovými razítky souborů v `Outputs` , aby bylo možné zjistit, zda `Target` je v aktuálním stavu. Další informace naleznete v tématu [přírůstkové sestavení](../msbuild/incremental-builds.md), [Postupy: sestavení přírůstkově](../msbuild/how-to-build-incrementally.md)a [transformace](../msbuild/msbuild-transforms.md).|
|`Outputs`|Nepovinný atribut.<br /><br /> Soubory, které tvoří výstup do tohoto cíle. Několik souborů je oddělených středníky. Časová razítka souborů budou porovnána s časovými razítky souborů v `Inputs` , aby bylo možné zjistit, zda `Target` je v aktuálním stavu. Další informace naleznete v tématu [přírůstkové sestavení](../msbuild/incremental-builds.md), [Postupy: sestavení přírůstkově](../msbuild/how-to-build-incrementally.md)a [transformace](../msbuild/msbuild-transforms.md).|
|`Returns`|Nepovinný atribut.<br /><br /> Sada položek, které budou zpřístupněny pro úlohy, které vyvolávají tento cíl, například úlohy MSBuild. Více cílů je odděleno středníky. Pokud cíle v souboru nemají žádné `Returns` atributy, místo toho se pro tento účel použijí atributy výstupy.|
|`KeepDuplicateOutputs`|Volitelný atribut typu Boolean.<br /><br /> Pokud je `true` zaznamenáno více odkazů na stejnou položku v cílovém objektu vrátí se.  Ve výchozím nastavení je tento atribut `false` .|
|`BeforeTargets`|Nepovinný atribut.<br /><br /> Seznam cílových názvů oddělený středníkem  Je-li tento parametr zadán, označuje, že tento cíl bude spuštěn před zadaným cílem nebo cílem. Tím umožníte, aby autor projektu rozšířil existující sadu cílů beze změny přímo. Další informace najdete v tématu [cílové pořadí sestavení](../msbuild/target-build-order.md).|
|`AfterTargets`|Nepovinný atribut.<br /><br /> Seznam cílových názvů oddělený středníkem Když se tato parametr zadá, označuje, že se má tento cíl spustit po zadaném cíli nebo cíli. Tím umožníte, aby autor projektu rozšířil existující sadu cílů beze změny přímo. Další informace najdete v tématu [cílové pořadí sestavení](../msbuild/target-build-order.md).|
|`DependsOnTargets`|Nepovinný atribut.<br /><br /> Cíle, které je třeba provést před provedením tohoto cíle, nebo může dojít k analýze závislostí na nejvyšší úrovni. Více cílů je odděleno středníky.|
|`Label`|Nepovinný atribut.<br /><br /> Identifikátor, který může identifikovat nebo seřadit systémové a uživatelské prvky.|

### <a name="child-elements"></a>Podřízené prvky

| Element | Popis |
| - | - |
| [Úloha](../msbuild/task-element-msbuild.md) | Vytvoří a spustí instanci úlohy MSBuild. V cíli může být nula nebo více úkolů. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Obsahuje sadu uživatelsky definovaných `Property` prvků. Počínaje .NET Framework 3,5 `Target` prvek může obsahovat `PropertyGroup` elementy. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Obsahuje sadu uživatelsky definovaných `Item` prvků. Počínaje .NET Framework 3,5 `Target` prvek může obsahovat `ItemGroup` elementy. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md). |
| [OnError](../msbuild/onerror-element-msbuild.md) | Způsobí, že jeden nebo více cílů bude spuštěno, pokud `ContinueOnError` je atribut ErrorAndStop (nebo `false` ) pro neúspěšnou úlohu. V cíli může být nula nebo více `OnError` prvků. Pokud `OnError` jsou prvky přítomny, musí se jednat o poslední prvky v `Target` elementu.<br /><br /> Informace o atributu naleznete `ContinueOnError` v tématu [element Task (MSBuild)](../msbuild/task-element-msbuild.md). |

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu MSBuild. |

## <a name="remarks"></a>Poznámky

 První cíl, který má být spuštěn, je určen v době běhu. Cíle můžou mít závislosti na jiných cílech. Například cíl pro nasazení závisí na cíli pro kompilaci. Modul MSBuild spouští závislosti v pořadí, ve kterém jsou uvedeny v `DependsOnTargets` atributu zleva doprava. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md).

 MSBuild je závislý na pořadí importu a poslední definice cíle s konkrétním `Name` atributem je použitá definice.

 Cíl se spustí pouze jednou během sestavení, i když na něm závisí více než jeden cíl.

 Pokud je cíl vynechán, protože se jeho `Condition` atribut vyhodnocuje `false` , může být stále proveden, pokud je vyvolán později v sestavení a jeho atribut je `Condition` `true` v daném čase vyhodnocen jako.

 Před MSBuild 4 `Target` vrátily všechny položky, které byly zadány v `Outputs` atributu.  Nástroj MSBuild musel tyto položky zaznamenat v případě, že je požaduje, později v sestavení. Vzhledem k tomu, že neexistuje žádný způsob, jak určit, které cíle obsahovaly výstupy, které by volající vyžadovaly, nástroj MSBuild shromáždil všechny položky ze všech `Outputs` vyvolaných `Target` s. To vede k škálování problémů pro sestavení, která měla velký počet výstupních položek.

 Pokud uživatel určí `Returns` u libovolného `Target` elementu v projektu, pak pouze ty `Target` , které mají `Returns` atribut, tyto položky se zaznamenají.

 `Target`Může obsahovat `Outputs` atribut i `Returns` atribut.  `Outputs` se používá s `Inputs` k určení, zda je cíl v aktuálním stavu. `Returns`, pokud je k dispozici, Přepisuje hodnotu `Outputs` k určení, které položky jsou vraceny volajícím.  Pokud není k `Returns` `Outputs` dispozici, bude zpřístupněna volajícím s výjimkou výše popsaného případu.

 Před tím, než nástroj MSBuild 4 pokaždé, když jsou `Target` zahrnuté více odkazů na stejnou položku `Outputs` , budou tyto duplicitní položky zaznamenávány. Ve velmi rozsáhlých sestaveních, která měla velký počet výstupů a mnoho vzájemně závislých projektů, by to znamenalo neplýtvání velkého množství paměti, protože duplicitní položky nebyly žádného použití. Pokud `KeepDuplicateOutputs` je atribut nastaven na `true` , jsou tyto duplicity zaznamenávány.

## <a name="example"></a>Příklad

 Následující příklad kódu ukazuje `Target` prvek, který `Csc` úlohu spouští.

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

- [Targets](../msbuild/msbuild-targets.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
