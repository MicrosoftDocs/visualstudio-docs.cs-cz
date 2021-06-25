---
title: Importy editoru | Microsoft Docs
description: Naučte se importovat editorské služby, továrny a zprostředkovatele, které poskytují vašemu rozšíření různé druhy přístupu k základnímu editoru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f2fa91b41017512b3f38ad61b800b293e0abaa1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898341"
---
# <a name="editor-imports"></a>Importy editoru
Můžete importovat řadu služeb editoru, továren a zprostředkovatelů, které poskytují vašemu rozšíření různé druhy přístupu k základnímu editoru. Můžete například importovat a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> poskytnout vám hodnotu pro daný typ <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> obsahu. (Tento navigátor umožňuje provádět různé druhy hledání ve vyrovnávací paměti textu.)

 Pokud chcete použít import editoru, naimportujte ho jako pole nebo vlastnost třídy, která exportuje Managed Extensibility Framework součást.

> [!NOTE]
> Další informace o tomto Managed Extensibility Framework v tématu [Managed Extensibility Framework (MEF).](/dotnet/framework/mef/index)

## <a name="import-syntax"></a>Syntaxe importu
 Následující příklad ukazuje, jak importovat službu pro vytváření možností editoru.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Pokud chcete službu importovat jako pole, a ne jako vlastnost, měli byste ji v deklaraci nastavit na , abyste se vyhnuli upozorněním kompilátoru na nepřiřazování `null` proměnné:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Další příklady použití importů najdete v následujících názorném postupu:

- [Návod: Vytvoření piktogramu okrajů](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Návod: Přizpůsobení textového zobrazení](../extensibility/walkthrough-customizing-the-text-view.md)

- [Návod: Zvýraznění textu](../extensibility/walkthrough-highlighting-text.md)

- [Návod: Zobrazení popisů rychlých informací](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Návod: Zobrazení nápovědy k signaturě](../extensibility/walkthrough-displaying-signature-help.md)

- [Návod: Zobrazení dokončování příkazů](../extensibility/walkthrough-displaying-statement-completion.md)

- [Návod: Zobrazení návrhů žárovky](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Import poskytovatele služeb
 Můžete také importovat (nachází se v sestavení <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> Microsoft.VisualStudio.Shell.Immutable.10.0) stejným způsobem, abyste měli přístup k Visual Studio službám:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Další [informace najdete v tématu Návod:](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) Přístup k objektu DTE z rozšíření editoru.

## <a name="services"></a>Služby
 Služby editoru jsou obecně jednotlivé entity, které poskytují službu a jsou sdíleny napříč několika komponentami.

|Import|Poskytuje|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Vztah mezi příponami souborů a <xref:Microsoft.VisualStudio.Utilities.IContentType> objekty.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Kolekce <xref:Microsoft.VisualStudio.Utilities.IContentType> objektů.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> Objekty.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Mnoho objektů adaptéru editoru:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Objekt <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> pro dané textové zobrazení.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|. <xref:Microsoft.VisualStudio.Text.ITextBuffer>|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|. <xref:Microsoft.VisualStudio.Text.ITextDocument>|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Jeden <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> z rozdílů.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Jeden <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> z rozdílů.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Nebo <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Pro <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> sadu <xref:Microsoft.VisualStudio.Text.ITextBuffer> objektů.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Pro <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Pro <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Pro <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Pro <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Udržuje kolekci <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objektů.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Pro <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> vyrovnávací paměť textu.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Pro <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> textové zobrazení.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|pro <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> zadaný obor.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Pro <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> textové zobrazení.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Pro <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Získá automatické odsazení prostřednictvím <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> objektů.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Spravuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> pro <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|. <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generuje text ve formátu RTF ze sady rozsahů snímků.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Pro <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Formátování <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> řádků textu v zobrazení|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Objekt <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Prohledá textový snímek.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Pro <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> pro <xref:Microsoft.VisualStudio.Text.ITextBuffer> podle <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Pro <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> textové zobrazení.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standardní sada piktogramů.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Pro <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Sleduje zpracování klávesnice.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standardní <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objekty.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Udržuje vztah mezi textovou vyrovnávací pamětí a  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> objekty.|

## <a name="other-imports"></a>Další importy
 Továren a zprostředkovatelé poskytovatelů jsou obecně entity, které mohou mít více instancí ve více komponentách.

|Import|Poskytuje|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Typ <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> ) pro danou vyrovnávací <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> paměť.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|A text marker tagger (a <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> of type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|pro <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> danou hodnotu <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>|

## <a name="see-also"></a>Viz také
- [Nápěvné body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
