---
title: Společné položky projektu nástroje MSBuild | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: c7725108fd71f4292a8d3fa4dfe68ca29d3dcd90
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634445"
---
# <a name="common-msbuild-project-items"></a>Společné položky projektu nástroje MSBuild

V nástroji MSBuild je položka pojmenovaný odkaz na jeden nebo více souborů. Položky obsahují metadata, jako jsou názvy souborů, cesty a čísla verzí. Všechny typy projektů v aplikaci Visual Studio mají několik položek společné. Tyto položky jsou definovány v souboru *Microsoft. Build. CommonTypes. xsd*.
## <a name="common-items"></a>Společné položky

 Níže je seznam všech běžných položek projektu.
Níže je seznam všech běžných položek projektu.

### <a name="reference"></a>Referenční informace

 Představuje odkaz sestavení (spravovaného) v projektu.

|Název metadat položky|Popis|
|---------------|-----------------|
|HintPath|Volitelný řetězec. Relativní nebo absolutní cesta k sestavení|
|Název|Volitelný řetězec. Zobrazovaný název sestavení, například "System. Windows. Forms."|
|Fusion|Volitelný řetězec. Určuje jednoduchý nebo silný název fúze pro položku.<br /><br /> Pokud je tento atribut přítomen, může ušetřit čas, protože soubor sestavení není nutné otevřít, aby získal název fúze.|
|SpecificVersion|Volitelná logická hodnota. Určuje, zda má být odkazována pouze verze v názvu fúze.|
|Aliasy|Volitelný řetězec. Všechny aliasy pro referenci|
|Private|Volitelná logická hodnota. Určuje, zda má být odkaz zkopírován do výstupní složky. Tento atribut odpovídá vlastnosti **Copy Local** odkazu, který je v integrovaném vývojovém prostředí sady Visual Studio.|

### <a name="comreference"></a>COMReference

 Představuje odkaz na komponentu modelu COM (nespravovaný) v projektu. Tato položka se vztahuje pouze na projekty .NET.

|Název metadat položky|Popis|
|---------------|-----------------|
|Název|Volitelný řetězec. Zobrazovaný název součásti.|
|identifikátor GUID|Povinný řetězec. Identifikátor GUID pro komponentu ve formuláři {12345678-1234-1234-1234-1234567891234}.|
|VersionMajor|Povinný řetězec. Hlavní část čísla verze součásti. Například "5", pokud je číslo úplné verze "5,46".|
|VersionMinor|Povinný řetězec. Vedlejší část čísla verze součásti. Například "46", pokud je číslo úplné verze "5,46".|
|IDENTIFIKÁTORY|Volitelný řetězec. LocaleID pro komponentu|
|WrapperTool|Volitelný řetězec. Název nástroje obálky, který se používá pro komponentu, například "Tlbimp".|
|Izolován|Volitelná logická hodnota. Určuje, zda je komponenta komponentou bez registrace.|

### <a name="comfilereference"></a>COMFileReference

 Představuje seznam knihoven typů, které jsou předány do parametru `TypeLibFiles` cíle [ResolveComReference –](resolvecomreference-task.md) . Tato položka se vztahuje pouze na projekty .NET.

|Název metadat položky|Popis|
|---------------|-----------------|
|WrapperTool|Volitelný řetězec. Název nástroje obálky, který se používá pro komponentu, například "Tlbimp".|

### <a name="nativereference"></a>NativeReference

 Představuje nativní soubor manifestu nebo odkaz na takový soubor.

|Název metadat položky|Popis|
|---------------|-----------------|
|Název|Povinný řetězec. Základní název souboru manifestu.|
|HintPath|Povinný řetězec. Relativní cesta k souboru manifestu.|

### <a name="projectreference"></a>ProjectReference

 Představuje odkaz na jiný projekt.

|Název metadat položky|Popis|
|---------------|-----------------|
|Název|Volitelný řetězec. Zobrazovaný název odkazu|
|Project|Volitelný řetězec. Identifikátor GUID odkazu ve formuláři {12345678-1234-1234-1234-1234567891234}.|
|Balíček|Volitelný řetězec. Cesta k souboru projektu, na který se odkazuje|
|ReferenceOutputAssembly|Volitelná logická hodnota. Pokud je nastaveno na `false`, nezahrnuje výstup odkazovaného projektu jako [odkaz](#reference) na tento projekt, ale stále zajišťuje, že druhý projekt bude sestaven před tímto. Výchozí hodnota je `true`.|

### <a name="compile"></a>Kompilace

 Představuje zdrojové soubory pro kompilátor.

| Název metadat položky | Popis |
|-----------------------| - |
| DependentUpon | Volitelný řetězec. Určuje soubor, na kterém je tento soubor závislý, aby se správně zkompiluje. |
| AutoGen | Volitelná logická hodnota. Určuje, zda byl soubor generován pro projekt pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio. |
| Odkaz | Volitelný řetězec. Cesta k zápisu, která se má zobrazit, pokud je soubor fyzicky umístěný mimo vliv souboru projektu. |
| Viditelný | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumník řešení** v aplikaci Visual Studio. |
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
| Viditelný | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumník řešení** v aplikaci Visual Studio. |
| CopyToOutputDirectory | Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. nikdy<br />2. vždycky<br />3. PreserveNewest |
| LogicalName | Povinný řetězec. Logický název vloženého prostředku. |

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
| Viditelný | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumník řešení** v aplikaci Visual Studio. |
| CopyToOutputDirectory | Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. nikdy<br />2. vždycky<br />3. PreserveNewest |

### <a name="none"></a>Žádná

 Představuje soubory, které by neměly mít žádné role v procesu sestavení.

| Název metadat položky | Popis |
|-----------------------| - |
| DependentUpon | Volitelný řetězec. Určuje soubor, na kterém je tento soubor závislý, aby se správně zkompiluje. |
| Generátor | Povinný řetězec. Název jakéhokoli generátoru souborů, který je spuštěn na této položce. |
| LastGenOutput | Povinný řetězec. Název souboru, který byl vytvořen generátorem souborů, který u této položky běžel. |
| CustomToolNamespace | Povinný řetězec. Obor názvů, ve kterém má každý generátor souborů, který běží na této položce, vytvořit kód. |
| Odkaz | Volitelný řetězec. Cesta k zápisu, která se má zobrazit, pokud je soubor fyzicky umístěný mimo vliv projektu. |
| Viditelný | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumník řešení** v aplikaci Visual Studio. |
| CopyToOutputDirectory | Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. nikdy<br />2. vždycky<br />3. PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata –

 Představuje atributy sestavení, které mají být generovány jako `[AssemblyMetadata(key, value)]`.

| Název metadat položky | Popis |
|-----------------------| - |
| Zařadit členy | Se bude první parametr (klíč) v konstruktoru atributu `AssemblyMetadataAttribute`. |
| Hodnota | Povinný řetězec. Se bude druhým parametrem (hodnota) v konstruktoru atributu `AssemblyMetadataAttribute`. |

> [!NOTE]
> To platí jenom pro projekty, které používají jenom .NET Core SDK.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest

 Představuje manifest základní aplikace pro sestavení a obsahuje informace o zabezpečení nasazení ClickOnce.

### <a name="codeanalysisimport"></a>CodeAnalysisImport

 Představuje projekt FxCop, který se má importovat.

### <a name="import"></a>Import

 Představuje sestavení, jejichž obory názvů by měly být importovány Visual Basic kompilátorem.

## <a name="see-also"></a>Viz také

- [Obecné vlastnosti projektu nástroje MSBuild](../msbuild/common-msbuild-project-properties.md)
