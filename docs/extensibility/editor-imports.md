---
title: Importovat editory | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712016"
---
# <a name="editor-imports"></a>Importy editoru
Můžete importovat řadu služeb editoru, továrn a zprostředkovatelů, které poskytují vaše rozšíření s různými druhy přístupu k základnímu editoru. Například můžete importovat <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> a poskytnout vám <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> pro daný typ obsahu. (Tento navigátor umožňuje provádět různé druhy hledání v textové vyrovnávací paměti.)

 Chcete-li použít Import editoru, importujte jej jako pole nebo vlastnost třídy, která exportuje součást Managed Extensibility Framework součásti.

> [!NOTE]
> Další informace o Managed Extensibility Framework naleznete v tématu [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Syntaxe importu
 Následující příklad ukazuje, jak importovat službu pro vytváření možností editoru.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Pokud chcete službu importovat jako pole a ne jako vlastnost, měli byste ji nastavit na `null` v deklaraci, aby nedošlo k upozorněním kompilátoru o přiřazení k proměnné:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Další příklady použití importu najdete v následujících návodech:

- [Návod: vytvoření glyfu marže](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Návod: přizpůsobení zobrazení textu](../extensibility/walkthrough-customizing-the-text-view.md)

- [Návod: zvýraznění textu](../extensibility/walkthrough-highlighting-text.md)

- [Návod: zobrazení QuickInfoch popisků](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Návod: zobrazení podpisu – Help](../extensibility/walkthrough-displaying-signature-help.md)

- [Návod: dokončování příkazů zobrazení](../extensibility/walkthrough-displaying-statement-completion.md)

- [Návod: zobrazení návrhů žárovky](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Import poskytovatele služeb
 Můžete také importovat <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (nalezeno v sestavení Microsoft. VisualStudio. Shell. unmutable. 10.0) stejným způsobem, jak získat přístup ke službám sady Visual Studio:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Další informace najdete v tématu [Návod: přístup k objektu DTE z rozšíření editoru](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) .

## <a name="services"></a>Služby
 Služby editoru jsou všeobecně samostatné entity, které poskytují službu a jsou sdíleny napříč více komponentami.

|Import|Zde|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Vztah mezi příponami souborů a <xref:Microsoft.VisualStudio.Utilities.IContentType> objekty.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Kolekce <xref:Microsoft.VisualStudio.Utilities.IContentType> objektů.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> objekty.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Mnoho objektů adaptérů editoru:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>Objekt pro dané zobrazení textu.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|A <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|A <xref:Microsoft.VisualStudio.Text.ITextDocument> .|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>Rozdíly.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>Rozdíly.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>Nebo <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>Pro sadu <xref:Microsoft.VisualStudio.Text.ITextBuffer> objektů.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Pro <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Udržuje kolekci <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objektů.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>Pro textovou vyrovnávací paměť.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>Pro textové zobrazení.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>Pro zadaný obor.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>Pro textové zobrazení.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Získá automatické odsazení prostřednictvím <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> objektů.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Spravuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> pro <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|A <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generuje text ve formátu RTF ze sady rozsahů snímků.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>Pro formátování textových čar v zobrazení.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>Objekt pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Vyhledá textový snímek.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>Pro <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>Pro textové zobrazení.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standardní sada glyfů.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Sleduje zpracování klávesnice.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standardní <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objekty.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Udržuje vztah mezi textovými vyrovnávacími paměťmi a  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> objekty.|

## <a name="other-imports"></a>Další importy
 Továrny a zprostředkovatelé zprostředkovatelů jsou obecně entitami, které mohou mít více instancí ve více součástech.

|Import|Zde|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>Typ <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> ) pro danou vyrovnávací paměť.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Textová značka autor značky (a <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>Pro daný <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|A <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|A <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|A <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession> .|

## <a name="see-also"></a>Viz také
- [Rozšiřovací body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
