---
title: Prvek úkolu cíle (MSBuild) | Dokumenty společnosti Microsoft
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a4ec2203430045c083b46b2eea8d3e884a4b794
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263169"
---
# <a name="task-element-of-target-msbuild"></a>Prvek úkolu targetu (MSBuild)

Vytvoří a provede instanci úlohy MSBuild. Název prvku je určen názvem vytvářeného úkolu.

 \<> \<> projektu

## <a name="syntax"></a>Syntaxe

```xml
<Task Parameter1="Value1"... ParameterN="ValueN"
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"
    Condition="'String A' == 'String B'" >
    <Output... />
</Task>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Condition`|Nepovinný atribut. Podmínka, která má být vyhodnocena. Další informace naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).|
|`ContinueOnError`|Nepovinný atribut. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Pokud úloha selže, následné úkoly v [Target](../msbuild/target-element-msbuild.md) element a sestavení pokračovat v provádění a všechny chyby z úkolu jsou považovány za upozornění.<br />-   **ErrorAndContinue**. Pokud úloha selže, následné `Target` úkoly v prvku a sestavení pokračovat v provádění a všechny chyby z úkolu jsou považovány za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Pokud úloha selže, zbývající úkoly v elementu `Target` a sestavení nejsou `Target` provedeny a celý prvek a sestavení se považuje za neúspěšné.<br /><br /> Verze rozhraní .NET Framework před 4.5 `true` `false` podporovaly pouze hodnoty a.<br /><br /> Další informace naleznete v [tématu Postup: Ignorovat chyby v úkolech](../msbuild/how-to-ignore-errors-in-tasks.md).|
|`Parameter`|Povinné, pokud třída úkolu obsahuje jednu `[Required]` nebo více vlastností označených atributem.<br /><br /> Uživatelem definovaný parametr úlohy, který obsahuje hodnotu parametru jako jeho hodnotu. V `Task` elementu může být libovolný počet parametrů, přičemž každé mapování atributů na vlastnost .NET ve třídě úkolu.|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Výstup](../msbuild/output-element-msbuild.md)|Ukládá výstupy z úkolu v souboru projektu. V úloze může `Output` být nula nebo více prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Cíl](../msbuild/target-element-msbuild.md) | Element kontejneru pro úlohy MSBuild. |

## <a name="remarks"></a>Poznámky

 Prvek `Task` v souboru projektu MSBuild vytvoří instanci úkolu, nastaví na něm vlastnosti a provede ji. Element `Output` ukládá výstupní parametry ve vlastnostech nebo položkách, které mají být použity jinde v souboru projektu.

 Pokud jsou v nadřazeném `Target` prvku úkolu nějaké prvky [OnError,](../msbuild/onerror-element-msbuild.md) budou stále `false`vyhodnoceny, pokud se úkol nezdaří a `ContinueOnError` má hodnotu . Další informace o úkolech naleznete v [tématu Úkoly](../msbuild/msbuild-tasks.md).

## <a name="example"></a>Příklad

 Následující příklad kódu vytvoří instanci třídy [úlohy Csc,](../msbuild/csc-task.md) nastaví šest vlastností a provede úlohu. Po spuštění je hodnota `OutputAssembly` vlastnosti objektu umístěna do `FinalAssemblyName`seznamu položek s názvem .

```xml
<Target Name="Compile" DependsOnTarget="Resources" >
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

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
