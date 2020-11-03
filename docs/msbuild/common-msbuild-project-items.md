---
title: Společné položky projektu nástroje MSBuild | Microsoft Docs
description: Přečtěte si o běžných položkách projektu MSBuild. Položky jsou pojmenovány jako odkazy na jeden nebo více souborů a mají metadata, jako jsou názvy souborů, cesty a čísla verzí.
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 638f67575a7214047cdb917c994179ac144e60b2
ms.sourcegitcommit: 49c959911128a733ed2858db7c0e3b565f934b1a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2020
ms.locfileid: "93238620"
---
# <a name="common-msbuild-project-items"></a>Společné položky projektu nástroje MSBuild

V nástroji MSBuild je položka pojmenovaný odkaz na jeden nebo více souborů. Položky obsahují metadata, jako jsou názvy souborů, cesty a čísla verzí. Všechny typy projektů v aplikaci Visual Studio mají několik položek společné. Tyto položky jsou definovány v souboru *Microsoft. Build. CommonTypes. xsd* .

## <a name="common-items"></a>Společné položky

Níže je seznam všech běžných položek projektu.

### <a name="reference"></a>Odkaz

Představuje odkaz sestavení (spravovaného) v projektu.

|Název metadat položky|Popis|
|---------------|-----------------|
|Cestu|Volitelný řetězec. Relativní nebo absolutní cesta k sestavení|
|Název|Volitelný řetězec. Zobrazovaný název sestavení, například "System. Windows. Forms."|
|Fusion|Volitelný řetězec. Určuje jednoduchý nebo silný název fúze pro položku.<br /><br /> Pokud je tento atribut přítomen, může ušetřit čas, protože soubor sestavení není nutné otevřít, aby získal název fúze.|
|SpecificVersion|Volitelná logická hodnota. Určuje, zda má být odkazována pouze verze v názvu fúze.|
|Aliasy|Volitelný řetězec. Všechny aliasy pro referenci|
|Privátní|Volitelná logická hodnota. Určuje, zda má být odkaz zkopírován do výstupní složky. Tento atribut odpovídá vlastnosti **Copy Local** odkazu, který je v integrovaném vývojovém prostředí sady Visual Studio.|

### <a name="comreference"></a>COMReference

Představuje odkaz na komponentu modelu COM (nespravovaný) v projektu. Tato položka se vztahuje pouze na projekty .NET.

|Název metadat položky|Popis|
|---------------|-----------------|
|Název|Volitelný řetězec. Zobrazovaný název součásti.|
|Identifikátor GUID|Povinný řetězec. Identifikátor GUID pro komponentu ve formuláři {12345678-1234-1234-1234-1234567891234} .|
|VersionMajor|Povinný řetězec. Hlavní část čísla verze součásti. Například "5", pokud je číslo úplné verze "5,46".|
|VersionMinor|Povinný řetězec. Vedlejší část čísla verze součásti. Například "46", pokud je číslo úplné verze "5,46".|
|LCID|Volitelný řetězec. LocaleID pro komponentu|
|WrapperTool|Volitelný řetězec. Název nástroje obálky, který se používá pro komponentu, například "Tlbimp".|
|Isolated|Volitelná logická hodnota. Určuje, zda je komponenta komponentou bez registrace.|

### <a name="comfilereference"></a>COMFileReference

Představuje seznam knihoven typů, které jsou předány `TypeLibFiles` parametru cíle [ResolveComReference –](resolvecomreference-task.md) . Tato položka se vztahuje pouze na projekty .NET.

|Název metadat položky|Popis|
|---------------|-----------------|
|WrapperTool|Volitelný řetězec. Název nástroje obálky, který se používá pro komponentu, například "Tlbimp".|

### <a name="nativereference"></a>NativeReference

Představuje nativní soubor manifestu nebo odkaz na takový soubor.

|Název metadat položky|Popis|
|---------------|-----------------|
|Název|Povinný řetězec. Základní název souboru manifestu.|
|Cestu|Povinný řetězec. Relativní cesta k souboru manifestu.|

### <a name="projectreference"></a>ProjectReference

Představuje odkaz na jiný projekt. `ProjectReference` položky jsou transformované na [referenční](#reference) položky podle `ResolveProjectReferences` cíle, takže jakákoli platná metadata na odkazu můžou být platná `ProjectReference` , pokud ho proces transformace nepřepíše.

|Název metadat položky|Popis|
|---------------|-----------------|
|Název|Volitelný řetězec. Zobrazovaný název odkazu|
|GlobalPropertiesToRemove|Volitelné `string[]` . Názvy vlastností, které mají být odebrány při sestavování odkazovaného projektu, například `RuntimeIdentifier;PackOnBuild` . Výchozí hodnota je prázdná.|
|Project|Volitelný řetězec. Identifikátor GUID odkazu ve formuláři {12345678-1234-1234-1234-1234567891234} .|
|OutputItemType|Volitelný řetězec. Typ položky, do které se mají generovat výstupy cíle Výchozí hodnota je prázdná. Pokud jsou referenční metadata nastavená na "true" (výchozí), budou se cílové výstupy nastavovat jako odkazy na kompilátor.|
|ReferenceOutputAssembly|Volitelná logická hodnota. Pokud je nastaveno na `false` , nezahrnuje výstup odkazovaného projektu jako [odkaz](#reference) na tento projekt, ale stále zajišťuje, aby druhý projekt sestavil před tímto prvkem. Výchozí hodnota je `true` .|
|SetConfiguration|Volitelný řetězec. Nastaví globální vlastnost `Configuration` odkazovaného projektu, například `Configuration=Release` .|
|SetPlatform|Volitelný řetězec. Nastaví globální vlastnost `Platform` odkazovaného projektu, například `Platform=AnyCPU` .|
|SetTargetFramework|Volitelný řetězec. Nastaví globální vlastnost `TargetFramework` odkazovaného projektu, například `TargetFramework=netstandard2.0` .|
|SkipGetTargetFrameworkProperties|Volitelná logická hodnota. Pokud `true` , sestavení odkazovaného projektu se sestaví bez vyjednávání hodnoty nejvíce kompatibilního `TargetFramework` . Výchozí hodnota je `false` .|
|Targets|Volitelné `string[]` . Středníkem oddělený seznam cílů v odkazovaných projektech, které by měly být sestaveny. Výchozí hodnota je hodnota, jejíž výchozí hodnota je `$(ProjectReferenceBuildTargets)` prázdná, což značí výchozí cíle.|

### <a name="compile"></a>Sestavení

Představuje zdrojové soubory pro kompilátor.

| Název metadat položky | Popis |
|-----------------------| - |
| DependentUpon | Volitelný řetězec. Určuje soubor, na kterém je tento soubor závislý, aby se správně zkompiluje. |
| AutoGen | Volitelná logická hodnota. Určuje, zda byl soubor generován pro projekt pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio. |
| Odkaz | Volitelný řetězec. Cesta k zápisu, která se má zobrazit, pokud je soubor fyzicky umístěný mimo vliv souboru projektu. |
| Viditelné | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumník řešení** v aplikaci Visual Studio. |
| CopyToOutputDirectory | Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. nikdy<br />2. vždycky<br />3. PreserveNewest |

### <a name="embeddedresource"></a>EmbeddedResource

Představuje prostředky, které mají být vloženy do generovaného sestavení.

| Název metadat položky | Popis |
|-----------------------| - |
| DependentUpon | Volitelný řetězec. Určuje soubor, na kterém je tento soubor závislý, aby se správně zkompiluje. |
| Generátor | Povinný řetězec. Název jakéhokoli generátoru souborů, který je spuštěn na této položce. |
| LastGenOutput | Povinný řetězec. Název souboru, který byl vytvořen generátorem souborů, který u této položky běžel. |
| CustomToolNamespace | Povinný řetězec. Obor názvů, ve kterém má každý generátor souborů, který běží na této položce, vytvořit kód. |
| Odkaz | Volitelný řetězec. Cesta k zápisu se zobrazí, pokud je soubor fyzicky umístěný mimo vliv projektu. |
| Viditelné | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumník řešení** v aplikaci Visual Studio. |
| CopyToOutputDirectory | Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. nikdy<br />2. vždycky<br />3. PreserveNewest |
| Logický operátor | Povinný řetězec. Logický název vloženého prostředku. |

### <a name="content"></a>Obsah

Představuje soubory, které nejsou zkompilovány do projektu, ale mohou být vloženy nebo publikovány společně s ní.

| Název metadat položky | Popis |
|-----------------------| - |
| DependentUpon | Volitelný řetězec. Určuje soubor, na kterém je tento soubor závislý, aby se správně zkompiluje. |
| Generátor | Povinný řetězec. Název jakéhokoli generátoru souborů, který se na této položce spouští. |
| LastGenOutput | Povinný řetězec. Název souboru, který byl vytvořen generátorem souborů spuštěným u této položky. |
| CustomToolNamespace | Povinný řetězec. Obor názvů, ve kterém má každý generátor souborů, který běží na této položce, vytvořit kód. |
| Odkaz | Volitelný řetězec. Cesta k zápisu, která se má zobrazit, pokud je soubor fyzicky umístěný mimo vliv projektu. |
| PublishState | Povinný řetězec. Stav publikování obsahu, a to buď:<br /><br /> – Výchozí<br />– Zahrnuto<br />– Vyloučené<br />– Datový datový<br />– Předpoklad |
| Sestavení | Volitelná logická hodnota. Určuje, zda je soubor sestavením. |
| Viditelné | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumník řešení** v aplikaci Visual Studio. |
| CopyToOutputDirectory | Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. nikdy<br />2. vždycky<br />3. PreserveNewest |

### <a name="none"></a>Žádné

Představuje soubory, které by neměly mít žádné role v procesu sestavení.

| Název metadat položky | Popis |
|-----------------------| - |
| DependentUpon | Volitelný řetězec. Určuje soubor, na kterém je tento soubor závislý, aby se správně zkompiluje. |
| Generátor | Povinný řetězec. Název jakéhokoli generátoru souborů, který je spuštěn na této položce. |
| LastGenOutput | Povinný řetězec. Název souboru, který byl vytvořen generátorem souborů, který u této položky běžel. |
| CustomToolNamespace | Povinný řetězec. Obor názvů, ve kterém má každý generátor souborů, který běží na této položce, vytvořit kód. |
| Odkaz | Volitelný řetězec. Cesta k zápisu, která se má zobrazit, pokud je soubor fyzicky umístěný mimo vliv projektu. |
| Viditelné | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumník řešení** v aplikaci Visual Studio. |
| CopyToOutputDirectory | Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. nikdy<br />2. vždycky<br />3. PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata –

Představuje atributy sestavení, které mají být generovány jako `[AssemblyMetadata(key, value)]` .

| Název metadat položky | Popis |
|-----------------------| - |
| Zařadit členy | Se bude první parametr (klíč) v `AssemblyMetadataAttribute` konstruktoru atributu. |
| Hodnota | Povinný řetězec. Se bude druhým parametrem (hodnota) v `AssemblyMetadataAttribute` konstruktoru atributu. |

> [!NOTE]
> Tato položka se vztahuje na projekty používající sadu SDK pro .NET 5 (a .NET Core) a novější verze.

### <a name="internalsvisibleto"></a>InternalsVisibleTo

Určuje sestavení, která mají být generována jako `[InternalsVisibleTo(..)]` atributy sestavení.

| Název metadat položky | Popis |
|-----------------------| - |
| Zařadit členy | Název sestavení |
| Klíč | Volitelný řetězec. Veřejný klíč sestavení. |

> [!NOTE]
> Tato položka se vztahuje na projekty používající sadu SDK pro .NET 5 (a .NET Core) a novější verze.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest

Představuje manifest základní aplikace pro sestavení a obsahuje informace o zabezpečení nasazení ClickOnce.

### <a name="codeanalysisimport"></a>CodeAnalysisImport

Představuje projekt FxCop, který se má importovat.

### <a name="import"></a>Import

Představuje sestavení, jejichž obory názvů by měly být importovány Visual Basic kompilátorem.

## <a name="see-also"></a>Viz také:

- [Obecné vlastnosti projektu nástroje MSBuild](../msbuild/common-msbuild-project-properties.md)
- [Vlastnosti nástroje MSBuild pro projekty .NET Core SDK](/dotnet/core/project-sdk/msbuild-props)
- [Společná metadata položky MSBuild](common-msbuild-item-metadata.md)