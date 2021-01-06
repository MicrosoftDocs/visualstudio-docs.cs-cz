---
title: Indexování pracovních prostorů v aplikaci Visual Studio | Microsoft Docs
description: Seznamte se s indexováním pracovních prostorů, což je kolekce a trvalé úložiště dat pro podporu bohatých funkcí IDE pro pracovní prostor otevřené složky.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 6b5c069ce3ae993f2d2371bffae3ac58b286fa70
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877049"
---
# <a name="workspace-indexing"></a>Indexování pracovního prostoru

V řešení jsou projektové systémy zodpovědné za poskytování funkčnosti pro sestavování, ladění, **goto** hledání symbolů a další. Projektové systémy mohou tuto práci provést, protože rozumí relaci a možnosti souborů v rámci projektu. Pracovní prostor [Otevřít složku](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) potřebuje stejný přehled, aby poskytoval i rozšířené funkce IDE. Kolekce a trvalé úložiště těchto dat je proces nazývaný indexování pracovního prostoru. Tato indexovaná data se dají dotazovat prostřednictvím sady asynchronních rozhraní API. Zařízení se mohou zúčastnit procesu indexování tím <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> , že poskytují informace o tom, jak zpracovat určité typy souborů.

## <a name="types-of-indexed-data"></a>Typy indexovaných dat

Existují tři druhy dat, která jsou indexována. Všimněte si, že typ očekávaný ze skenerů souborů se liší od typu deserializace z indexu.

|Data|Typ skeneru souborů|Typ výsledku dotazu na index|Související typy|
|--|--|--|--|
|Reference|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Symboly|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> by měl být použit místo `IIndexWorkspaceService` pro dotazy|
|Hodnoty dat|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Dotazování na indexovaná data

Pro přístup k trvalým datům jsou k dispozici dva asynchronní typy. První je až <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> . Poskytuje základní přístup k jednomu souboru `FileReferenceResult` a `FileDataResult` datům a ukládá výsledky do mezipaměti. Druhá je <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> ta, která nepoužívá ukládání do mezipaměti, ale umožňuje další možnosti dotazování.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Účast při indexování

Indexování pracovních prostorů zhruba následuje po následujícím pořadí:

1. Zjišťování a trvalost entit systému souborů v pracovním prostoru (pouze při prvotním spuštění kontroly).
1. Pro každý soubor je pro vyhledávání v pro k požádáno odpovídajícího poskytovatele s nejvyšší prioritou `FileReferenceInfo` .
1. Pro každý soubor je pro vyhledávání v pro k požádáno odpovídajícího poskytovatele s nejvyšší prioritou `SymbolDefinition` .
1. Pro každý soubor se zobrazí výzva pro všechny poskytovatele `FileDataValue` .

Rozšíření mohou exportovat skener implementací `IWorkspaceProviderFactory<IFileScanner>` a exportem typu pomocí <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> . `SupportedTypes`Argument atributu musí být jedna nebo více hodnot z <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> . Ukázkový skener najdete v [ukázce](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)sady vs SDK.

> [!WARNING]
> Neexportujte skener souborů, který podporuje daný `FileScannerTypeConstants.FileScannerContentType` typ. Používá se jenom pro interní účely Microsoftu.

V pokročilých situacích může rozšíření dynamicky podporovat libovolnou sadu typů souborů. Namísto exportu MEF `IWorkspaceProviderFactory<IFileScanner>` může rozšíření exportovat `IWorkspaceProviderFactory<IFileScannerProvider>` . Když indexování začne, tento typ objektu pro vytváření se naimportuje, vytvoří se jeho instance a <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> vyvolá se jeho metoda. `IFileScanner` instance podporující jakoukoli hodnotu od `FileScannerTpeConstants` se budou respektovat, nikoli jenom symboly.

## <a name="next-steps"></a>Další kroky

* [Pracovní prostory a jazykové služby](workspace-language-services.md) – Naučte se integrovat jazykové služby do pracovního prostoru otevřené složky.
* [Sestavení pracovního prostoru](workspace-build.md) – otevřená složka podporuje systémy sestavení, jako jsou MSBuild a soubory pravidel.