---
title: Dovoz editora | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6af95b452166aa71950ac1e869d333d12d857b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712016"
---
# <a name="editor-imports"></a>Editor importy
Můžete importovat řadu editorslužby, továrny a zprostředkovatelé, které poskytují rozšíření s různými druhy přístupu k editoru jádra. Můžete například importovat, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> abyste získali a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> pro daný typ obsahu. (Tento navigátor umožňuje provádět různé druhy vyhledávání v textové vyrovnávací paměti.)

 Chcete-li použít import editoru, importujte jej jako pole nebo vlastnost třídy, která exportuje součást Framework spravované rozšiřitelnosti.

> [!NOTE]
> Další informace o rozhraní spravované rozšiřitelnosti naleznete v tématu [Spravované rozhraní rozšiřitelnosti (MEF).](/dotnet/framework/mef/index)

## <a name="import-syntax"></a>Importovat syntaxi
 Následující příklad ukazuje, jak importovat tovární službu možností editoru.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Pokud chcete importovat službu jako pole a ne vlastnost, `null` měli byste ji nastavit v deklaraci, abyste se vyhnuli upozorněníkompilátoru o nepřiřazování proměnné:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Další příklady použití importů najdete v následujících návodech:

- [Návod: Vytvoření symbolu okraje](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Návod: Přizpůsobení zobrazení textu](../extensibility/walkthrough-customizing-the-text-view.md)

- [Návod: Zvýraznění textu](../extensibility/walkthrough-highlighting-text.md)

- [Návod: Zobrazení popisů rychlých informací](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Návod: Zobrazit nápovědu k podpisu](../extensibility/walkthrough-displaying-signature-help.md)

- [Návod: Zobrazení dokončení příkazu](../extensibility/walkthrough-displaying-statement-completion.md)

- [Návod: Zobrazení návrhů žárovek](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Import poskytovatele služeb
 Můžete také importovat <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (nalezený v sestavení Microsoft.VisualStudio.Shell.Immutable.10.0) stejným způsobem získat přístup ke službám sady Visual Studio:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Další [informace najdete v tématu Návod: Přístup k objektu DTE z rozšíření editoru.](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md)

## <a name="services"></a>Služby
 Editor služby jsou obecně jediné entity, které poskytují službu a jsou sdíleny mezi více součástmi.

|Import|Poskytuje|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Vztah mezi příponami souborů a <xref:Microsoft.VisualStudio.Utilities.IContentType> objekty.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Kolekce <xref:Microsoft.VisualStudio.Utilities.IContentType> objektů.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>Objekty.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Mnoho objektů adaptéru editoru:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Objekt <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> pro dané zobrazení textu.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|A <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|A <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Rozdíly. <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Rozdíly. <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Nebo <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Pro <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> sadu <xref:Microsoft.VisualStudio.Text.ITextBuffer> objektů.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|A <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> pro <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|A <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|A <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|A <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Udržuje kolekci <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objektů.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Pro <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> text vyrovnávací paměti.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Pro <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> zobrazení textu.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Pro <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> zadaný obor.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Pro <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> zobrazení textu.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|A <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Získá automatické odsazení prostřednictvím <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> objektů.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Spravuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> for . <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|A <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generuje text ve formátu RTF ze sady rozsahů snímků.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Pro <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Formátování <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> řádků textu v zobrazení.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Objekt <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Prohledá snímek textu.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Pro <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> by <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Pro <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> zobrazení textu.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standardní sada glyfů.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|A <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Sleduje manipulaci s klávesnicí.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standardní <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objekty.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Udržuje vztah mezi textovými <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> vyrovnávacími paměťmi a objekty.|

## <a name="other-imports"></a>Ostatní dovozy
 Zprostředkovatel továrny a zprostředkovatelé jsou obecně entity, které mohou mít více instancí ve více komponent.

|Import|Poskytuje|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|A <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) pro danou vyrovnávací paměť.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Tagger textové značky <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> (a typu). <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|A <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>daný .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|A <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|A <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|A <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Viz také
- [Jazykové služby a rozšiřující body editoru](../extensibility/language-service-and-editor-extension-points.md)
