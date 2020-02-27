---
title: Import – element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 044c531432de987fc7f3d34ce5344ad0374bcd00
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633743"
---
# <a name="import-element-msbuild"></a>Import – element (MSBuild)

Importuje obsah jednoho souboru projektu do jiného souboru projektu.

\<> projektu \<Import >

## <a name="syntax"></a>Syntaxe

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Project`|Požadovaný atribut.<br /><br /> Cesta k souboru projektu, který se má importovat Cesta může obsahovat zástupné znaky. Vyhovující soubory jsou importovány v seřazeném pořadí. Pomocí této funkce můžete přidat kód do projektu pouhým přidáním souboru kódu do adresáře.|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|
|`Sdk`| Nepovinný atribut.<br /><br /> Odkazuje na sadu SDK projektu.|

### <a name="child-elements"></a>Podřízené prvky

 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [Projektem](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu MSBuild. |
| [ImportGroup –](../msbuild/importgroup-element.md) | Obsahuje kolekci `Import` prvků seskupených pod volitelnou podmínkou. |

## <a name="remarks"></a>Poznámky

 Pomocí elementu `Import` lze znovu použít kód, který je společný pro mnoho souborů projektu. To usnadňuje udržování kódu, protože jakékoli aktualizace, které provedete v rámci sdíleného kódu, se rozšíří do všech projektů, které ho importují.

 Podle konvence jsou sdílené importované soubory projektu uloženy jako soubory *. targets* , ale jsou standardní soubory projektu nástroje MSBuild. Nástroj MSBuild nebrání v importu projektu s jinou příponou názvu souboru, doporučujeme však použít rozšíření *. targets* pro zajištění konzistence.

 Relativní cesty v importovaných projektech jsou interpretovány relativně k adresáři importovaného projektu. Proto pokud je soubor projektu importován do několika souborů projektu v různých umístěních, relativní cesty v importovaném souboru projektu budou interpretovány jinak pro každý importovaný projekt.

 Všechny vlastnosti nástroje MSBuild, které se vztahují k souboru projektu, například `MSBuildProjectDirectory` a `MSBuildProjectFile`, které jsou odkazovány v importovaném projektu, jsou přiřazeny hodnoty na základě importu souboru projektu.

 Pokud importovaný projekt nemá atribut `DefaultTargets`, importované projekty jsou zkontrolovány v pořadí, v jakém jsou importovány, a je použita hodnota prvního zjištěného `DefaultTargets` atributu. Například pokud Projecta import ProjectB a ProjectC (v tomto pořadí) a importy ProjectB, MSBuild nejprve vyhledá `DefaultTargets` zadané v Projecta, pak na ProjectB, pak na projekt a nakonec ProjectC.

 Schéma importovaného projektu je stejné jako standardní projekt. I když nástroj MSBuild může být schopný sestavit importovaný projekt, není pravděpodobné, protože importovaný projekt obvykle neobsahuje informace o tom, které vlastnosti se mají nastavit nebo pořadí, ve kterém se mají spustit cíle. Importovaný projekt závisí na projektu, do kterého je importován, aby poskytoval tyto informace.

## <a name="wildcards"></a>Zástupné znaky

 V .NET Framework 4 umožňuje MSBuild v atributu projektu zástupné znaky. Pokud existují zástupné znaky, všechny nalezené shody jsou seřazené (za účelem reprodukovatelnosti) a poté jsou importovány v tomto pořadí, jako kdyby byla objednávka explicitně nastavena.

 To je užitečné, pokud chcete nabízet bod rozšiřitelnosti, aby mohl někdo jiný importovat soubor bez nutnosti explicitně přidat název souboru do importovaného souboru. Pro tento účel obsahuje *Microsoft. Common. targets* v horní části souboru následující řádek.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Příklad

 Následující příklad ukazuje projekt, který obsahuje několik položek a vlastností a importuje obecný soubor projektu.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <resourcefile>Strings.resx</resourcefile>

        <compiledresources>
            $(O)\$(MSBuildProjectName).Strings.resources
        </compiledresources>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" />

        <Reference Include="System" />
        <Reference Include="System.Data" />
    </ItemGroup>

    <Import Project="$(CommonLocation)\General.targets" />
</Project>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Postupy: použití stejného cíle ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
