---
title: Prvek importu (MSBuild) | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 7d9e66934015c7c4a57c7d7c6911b9ebe02ac536
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094489"
---
# <a name="import-element-msbuild"></a>Prvek importu (MSBuild)

Importuje obsah jednoho souboru projektu do jiného souboru projektu.

\<> \<importu> projektu

## <a name="syntax"></a>Syntaxe

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Project`|Požadovaný atribut.<br /><br /> Cesta k importu souboru projektu. Cesta může obsahovat zástupné znaky. Odpovídající soubory jsou importovány v seřazené pořadí. Pomocí této funkce můžete přidat kód do projektu pouhým přidáním souboru kódu do adresáře.|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).|
|`Sdk`| Nepovinný atribut.<br /><br /> Odkazuje na projekt SDK.|

### <a name="child-elements"></a>Podřízené prvky

 Žádný

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Požadovaný kořenový prvek souboru projektu MSBuild. |
| [Skupina importu](../msbuild/importgroup-element.md) | Obsahuje kolekci `Import` prvků seskupených pod volitelnou podmínkou. |

## <a name="remarks"></a>Poznámky

 Pomocí `Import` prvku můžete znovu použít kód, který je společný pro mnoho souborů projektu. To usnadňuje údržbu kódu, protože všechny aktualizace, které provedete do sdíleného kódu, se rozšíří do všech projektů, které jej importují.

 Podle konvence jsou sdílené importované soubory projektu uloženy jako soubory *.targets,* ale jsou to standardní soubory projektu MSBuild. MSBuild nezabrání importu projektu, který má jinou příponu názvu souboru, ale doporučujeme použít příponu *.targets* pro konzistenci.

 Relativní cesty v importovaných projektech jsou interpretovány vzhledem k adresáři importujícího projektu (s několika výjimkami popsanými dále v tomto odstavci). Proto pokud soubor projektu je importován do několika souborů projektu v různých umístěních, relativní cesty v importovaném souboru projektu budou interpretovány odlišně pro každý importovaný projekt. Existují dvě výjimky. Jedinou výjimkou `Import` je, že v elementech je cesta vždy `Import` interpretována vzhledem k projektu, který obsahuje prvek. Další výjimkou je, že `UsingTask` vždy interpretuje relativní cestu pro `UsingTask` `AssemblyFile` atribut vzhledem k souboru, který obsahuje prvek.

 Všechny vyhrazené vlastnosti MSBuild, které se `MSBuildProjectDirectory` vztahují `MSBuildProjectFile`k souboru projektu, například a , které jsou odkazovány v importovaném projektu, jsou přiřazeny hodnoty založené na importujícím souboru projektu.

 Pokud importovaný projekt nemá `DefaultTargets` atribut, importované projekty jsou kontrolovány v pořadí, ve které jsou `DefaultTargets` importovány, a použije se hodnota prvního zjištěného atributu. Pokud například ProjectA importuje projekt YProjectB a ProjectC (v tomto pořadí) a `DefaultTargets` projectb importuje projekt ProjectD, msbuild nejprve vyhledá zadané na ProjectA, potom ProjectB, potom ProjectD a nakonec ProjectC.

 Schéma importovaného projektu je shodné se standardním projektem. Přestože MSBuild může být schopen vytvořit importovaný projekt, je nepravděpodobné, protože importovaný projekt obvykle neobsahuje informace o tom, které vlastnosti nastavit nebo pořadí, ve kterém chcete spustit cíle. Importovaný projekt závisí na projektu, do kterého je importován, aby tyto informace poskytl.

## <a name="wildcards"></a>Zástupné znaky

 V rozhraní .NET Framework 4 msbuild umožňuje zástupné znaky v atributu Project. Pokud existují zástupné znaky, všechny nalezené shody jsou seřazeny (pro reprodukovatelnost) a pak jsou importovány v tomto pořadí, jako by bylo pořadí explicitně nastaveno.

 To je užitečné, pokud chcete nabídnout bod rozšiřitelnosti, aby někdo jiný mohl importovat soubor, aniž by bylo nutné explicitně přidat název souboru do importujícího souboru. Pro tento účel *Microsoft.Common.Targets* obsahuje následující řádek v horní části souboru.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Příklad

 Následující příklad ukazuje projekt, který má několik položek a vlastností a importuje obecný soubor projektu.

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

- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Postup: Použití stejného cíle ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
