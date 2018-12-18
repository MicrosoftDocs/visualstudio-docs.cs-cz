---
title: Pracovní prostor indexování v sadě Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 5004db0d895d1fdc697c18606c346c24cd484527
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939147"
---
# <a name="workspace-indexing"></a>Indexování pracovního prostoru

V řešení, projekt systémy odpovídají za poskytování funkcí pro sestavení, ladění, **GoTo** hledání symbolů a další. Systémy projektu může provést tuto práci, protože porozumí relace a možnosti souborů v rámci projektu. [Otevřít složku](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) pracovní prostor se musí stejné insight a zajistit tak také bohaté funkce integrovaného vývojového prostředí. Shromažďování a trvalé ukládání těchto dat je proces s názvem indexování pracovního prostoru. Tato indexovaná data může být dotázán pomocí sady asynchronního rozhraní API. Zařízení Extender mohl podílet na procesu indexování poskytnutím <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>, které už víte, jak zpracovat některé typy souborů.

## <a name="types-of-indexed-data"></a>Typy indexovaná data

Existují tři typy dat, která se indexují. Všimněte si, že byl očekáván ze souboru skenerů typ se liší od typu deserializovat z indexu.

|Data|Skener typ souboru|Typ výsledku dotazu indexu|Související typy|
|--|--|--|--|
|Odkazy|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Symboly|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> by měl být použít namísto `IIndexWorkspaceService` pro dotazy|
|Hodnoty dat|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Dotazování na indexovaná data

Existují dva asynchronní typy, které jsou k dispozici pro přístup k trvalá data. První je prostřednictvím <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Poskytuje základní přístup do jednoho souboru `FileReferenceResult` a `FileDataResult` dat a ukládá do mezipaměti výsledky. Druhým je <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> která nepoužívá ukládání do mezipaměti, ale umožňuje více možností dotazování.

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

## <a name="participating-in-indexing"></a>Účastní indexování

Pracovní prostor indexování zhruba následující následující posloupnost:

1. Zjišťování a trvalého souboru systémových entit v pracovním prostoru (pouze na počáteční počáteční kontroly).
1. Na soubor, odpovídající zprostředkovatel s nejvyšší prioritou se zobrazí výzva k vyhledání `FileReferenceInfo`s.
1. Na soubor, odpovídající zprostředkovatel s nejvyšší prioritou se zobrazí výzva k vyhledání `SymbolDefinition`s.
1. Na soubor, všichni poskytovatelé vyzváni k zadání `FileDataValue`s.

Rozšíření můžete exportovat skener implementací `IWorkspaceProviderFactory<IFileScanner>` a export typu s <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. `SupportedTypes` Argument atributu by měla být jedna nebo více hodnot z <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Skenerem příklad naleznete v tématu VS SDK [ukázka](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Neexportovat skener soubor, který se podporuje `FileScannerTypeConstants.FileScannerContentType` typu. Používá se Microsoft pouze k interním účelům.

V situacích, pokročilé může podporovat rozšíření dynamicky libovolnou sadu typů souborů. Místo export MEF `IWorkspaceProviderFactory<IFileScanner>`, můžete exportovat rozšíření `IWorkspaceProviderFactory<IFileScannerProvider>`. Po zahájení indexování tento typ objektu pro vytváření importované, vytvořena instance, který se mají jeho <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> metoda vyvolána. `IFileScanner` instance podporuje libovolnou hodnotu od `FileScannerTpeConstants` bude respektovat, ne jenom symboly.

## <a name="next-steps"></a>Další kroky

* [Pracovní prostory a jazykových služeb](workspace-language-services.md) – zjistěte, jak integrovat jazykových služeb do pracovního prostoru služby otevřít složku.
* [Pracovní prostor sestavení](workspace-build.md) -podporuje funkce Otevřít složku sestavení systémy, jako je MSBuild a soubory pravidel.