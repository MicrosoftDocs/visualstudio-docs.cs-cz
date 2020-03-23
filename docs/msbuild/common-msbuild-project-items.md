---
title: Běžné položky projektu MSBuild | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634445"
---
# <a name="common-msbuild-project-items"></a>Běžné položky projektu MSBuild

V MSBuild položka je pojmenovaný odkaz na jeden nebo více souborů. Položky obsahují metadata, jako jsou názvy souborů, cesty a čísla verzí. Všechny typy projektů v sadě Visual Studio mají několik položek společné. Tyto položky jsou definovány v souboru *Microsoft.Build.CommonTypes.xsd*.
## <a name="common-items"></a>Běžné položky

 Následuje seznam všech běžných položek projektu.
Následuje seznam všech běžných položek projektu.

### <a name="reference"></a>Referenční informace

 Představuje odkaz sestavení (spravované) v projektu.

|Název metadat položky|Popis|
|---------------|-----------------|
|Cesta nápovědy|Volitelný řetězec. Relativní nebo absolutní cesta sestavení.|
|Name (Název)|Volitelný řetězec. Zobrazovaný název sestavení, například System.Windows.Forms.|
|Název Fusion|Volitelný řetězec. Určuje jednoduchý nebo silný název fúze pro položku.<br /><br /> Pokud je tento atribut přítomen, může ušetřit čas, protože soubor sestavení není nutné otevřít k získání názvu fúze.|
|Specifická verze|Volitelná logická hodnota. Určuje, zda má být odkazována pouze verze v názvu fúze.|
|Aliasy|Volitelný řetězec. Všechny aliasy pro odkaz.|
|Private|Volitelná logická hodnota. Určuje, zda má být odkaz zkopírován do výstupní složky. Tento atribut odpovídá **Copy Local** vlastnost odkazu, který je v ide sady Visual Studio.|

### <a name="comreference"></a>Odkaz COMReference

 Představuje odkaz na komponentu MODELU COM (nespravované) v projektu. Tato položka se vztahuje pouze na projekty .NET.

|Název metadat položky|Popis|
|---------------|-----------------|
|Name (Název)|Volitelný řetězec. Zobrazovaný název komponenty.|
|Identifikátor GUID|Povinný řetězec. Identifikátor GUID pro součást ve {12345678-1234-1234-1234-1234567891234}formuláři .|
|VersionMajor|Povinný řetězec. Hlavní část čísla verze komponenty. Například "5", pokud je číslo plné verze "5.46."|
|VersionMinor|Povinný řetězec. Dílčí část čísla verze komponenty. Například "46", pokud je číslo plné verze "5.46."|
|LCID|Volitelný řetězec. Id národního prostředí pro komponentu.|
|ObálkaTool|Volitelný řetězec. Název obálky nástroj, který se používá na součásti, například "tlbimp."|
|Izolovaný|Volitelná logická hodnota. Určuje, zda se jedná o součást bez reg.|

### <a name="comfilereference"></a>ComFileReference

 Představuje seznam knihoven typů, které `TypeLibFiles` jsou předány parametru [resolvecomreference](resolvecomreference-task.md) cíle. Tato položka se vztahuje pouze na projekty .NET.

|Název metadat položky|Popis|
|---------------|-----------------|
|ObálkaTool|Volitelný řetězec. Název obálky nástroj, který se používá na součásti, například "tlbimp."|

### <a name="nativereference"></a>NativeReference

 Představuje nativní soubor manifestu nebo odkaz na takový soubor.

|Název metadat položky|Popis|
|---------------|-----------------|
|Name (Název)|Povinný řetězec. Základní název souboru manifestu.|
|Cesta nápovědy|Povinný řetězec. Relativní cesta souboru manifestu.|

### <a name="projectreference"></a>ProjectReference

 Představuje odkaz na jiný projekt.

|Název metadat položky|Popis|
|---------------|-----------------|
|Name (Název)|Volitelný řetězec. Zobrazovaný název odkazu.|
|Project|Volitelný řetězec. Identifikátor GUID pro referenci {12345678-1234-1234-1234-1234567891234}ve formuláři .|
|Balíček|Volitelný řetězec. Cesta k souboru projektu, na který se odkazuje.|
|Sestava ReferenceOutput|Volitelná logická hodnota. Pokud je `false`nastavena na , nezahrnuje výstup odkazovaného projektu jako [odkaz na](#reference) tento projekt, ale stále zajišťuje, že druhý projekt vytvoří před tímto projektem. Výchozí hodnota `true`je na .|

### <a name="compile"></a>Kompilaci

 Představuje zdrojové soubory pro kompilátor.

| Název metadat položky | Popis |
|-----------------------| - |
| ZávisléNa | Volitelný řetězec. Určuje soubor, na kterém tento soubor závisí, aby byl správně kompilován. |
| AutoGen | Volitelná logická hodnota. Označuje, zda byl soubor generován pro projekt integrovaným vývojového prostředí sady Visual Studio (IDE). |
| Odkaz | Volitelný řetězec. Cesta notace, která má být zobrazena, když je soubor fyzicky umístěn mimo vliv souboru projektu. |
| Viditelné | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumníkovi řešení** v sadě Visual Studio. |
| CopyToOutputDirectory | Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. Nikdy<br />2. Vždy<br />3. ZachovatNejnovější |

### <a name="embeddedresource"></a>Vložený prostředek

 Představuje prostředky, které mají být vloženy do generovaného sestavení.

| Název metadat položky | Popis |
|-----------------------| - |
| ZávisléNa | Volitelný řetězec. Určuje soubor, na kterém tento soubor závisí, aby byl správně kompilován. |
| Generátor | Povinný řetězec. Název generátoru souborů, který je spuštěn na této položce. |
| LastGenOutput | Povinný řetězec. Název souboru, který byl vytvořen libovolným generátorem souborů, který byl spuštěn na této položce. |
| CustomToolNamespace | Povinný řetězec. Obor názvů, ve kterém by měl vytvořit kód libovolný generátor souborů spuštěný v této položce. |
| Odkaz | Volitelný řetězec. Cesta notace se zobrazí, pokud je soubor fyzicky umístěn mimo vliv projektu. |
| Viditelné | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumníkovi řešení** v sadě Visual Studio. |
| CopyToOutputDirectory | Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. Nikdy<br />2. Vždy<br />3. ZachovatNejnovější |
| Logický název | Povinný řetězec. Logický název vloženého prostředku. |

### <a name="content"></a>Obsah

 Představuje soubory, které nejsou kompilovány do projektu, ale mohou být vloženy nebo publikovány společně s ním.

| Název metadat položky | Popis |
|-----------------------| - |
| ZávisléNa | Volitelný řetězec. Určuje soubor, na kterém tento soubor závisí, aby byl správně kompilován. |
| Generátor | Povinný řetězec. Název generátoru souborů, který běží na tuto položku. |
| LastGenOutput | Povinný řetězec. Název souboru, který byl vytvořen libovolným generátorem souborů, který byl spuštěn na této položce. |
| CustomToolNamespace | Povinný řetězec. Obor názvů, ve kterém by měl vytvořit kód libovolný generátor souborů spuštěný v této položce. |
| Odkaz | Volitelný řetězec. Cesta notace, která má být zobrazena, pokud je soubor fyzicky umístěn mimo vliv projektu. |
| PublishState | Povinný řetězec. Stav publikování obsahu buď:<br /><br /> - Výchozí<br />- Zahrnuto<br />- Vyloučeno<br />- Datový soubor<br />- Předpoklad |
| IsAssembly | Volitelná logická hodnota. Určuje, zda se jedná o sestavení. |
| Viditelné | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumníkovi řešení** v sadě Visual Studio. |
| CopyToOutputDirectory | Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. Nikdy<br />2. Vždy<br />3. ZachovatNejnovější |

### <a name="none"></a>Žádný

 Představuje soubory, které by měly mít žádnou roli v procesu sestavení.

| Název metadat položky | Popis |
|-----------------------| - |
| ZávisléNa | Volitelný řetězec. Určuje soubor, na kterém tento soubor závisí, aby byl správně kompilován. |
| Generátor | Povinný řetězec. Název generátoru souborů, který je spuštěn na této položce. |
| LastGenOutput | Povinný řetězec. Název souboru, který byl vytvořen libovolným generátorem souborů, který byl spuštěn na této položce. |
| CustomToolNamespace | Povinný řetězec. Obor názvů, ve kterém by měl vytvořit kód libovolný generátor souborů spuštěný v této položce. |
| Odkaz | Volitelný řetězec. Cesta notace, která má být zobrazena, pokud je soubor fyzicky umístěn mimo vliv projektu. |
| Viditelné | Volitelná logická hodnota. Označuje, zda se má soubor zobrazit v **Průzkumníkovi řešení** v sadě Visual Studio. |
| CopyToOutputDirectory | Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. Nikdy<br />2. Vždy<br />3. ZachovatNejnovější |

### <a name="assemblymetadata"></a>Metadata sestavení

 Představuje atributy sestavení, které `[AssemblyMetadata(key, value)]`mají být generovány jako .

| Název metadat položky | Popis |
|-----------------------| - |
| Zařadit členy | Stane se prvním parametrem (klíčem) v konstruktoru atributu. `AssemblyMetadataAttribute` |
| Hodnota | Povinný řetězec. Stane se druhým parametrem (hodnotou) v konstruktoru atributu. `AssemblyMetadataAttribute` |

> [!NOTE]
> To platí pouze pro projekty, které používají sadku .NET Core SDK.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest

 Představuje manifest základní aplikace pro sestavení a obsahuje informace o zabezpečení nasazení ClickOnce.

### <a name="codeanalysisimport"></a>CodeAnalysisImport

 Představuje projekt FxCop importovat.

### <a name="import"></a>Import

 Představuje sestavení, jejichž obory názvů by měly být importovány kompilátorem jazyka.

## <a name="see-also"></a>Viz také

- [Běžné vlastnosti projektu MSBuild](../msbuild/common-msbuild-project-properties.md)
