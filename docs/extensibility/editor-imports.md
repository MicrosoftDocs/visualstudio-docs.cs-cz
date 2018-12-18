---
title: Importy do editoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ede17217dbac62bcc0086e6f4e5afca0cf9e0a0
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637210"
---
# <a name="editor-imports"></a>Importy do editoru
Můžete naimportovat celou řadou služeb editoru, objekty pro vytváření a zprostředkovatelů, které poskytují rozšíření s různými druhy přístup k základní editor. Například můžete importovat <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> abyste měli <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> pro daný typ obsahu. (Tento Navigátor umožňuje provádět různé druhy hledání na textovou vyrovnávací paměť).  
  
 Použití editoru importu, importujete ho jako pole nebo vlastnosti třídy, která se exportuje součást Managed Extensibility Framework.  
  
> [!NOTE]
>  Další informace o rozhraní Managed Extensibility Framework, naleznete v tématu [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
## <a name="import-syntax"></a>Importovat syntaxe  
 Následující příklad ukazuje, jak importovat editoru možnosti výrobní službu.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Pokud chcete importovat službu jako pole a nejedná se o vlastnost, byste měli nastavit na `null` v deklaraci, aby se zabránilo upozornění kompilátoru o není přiřazování k proměnné:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Další příklady použití importy najdete v následujících návodech:  
  
 [Návod: Vytvoření okrajového piktogramu](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Návod: Přizpůsobení zobrazení textu](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Návod: Zvýraznění textu](../extensibility/walkthrough-highlighting-text.md)  
  
 [Návod: Zobrazení QuickInfo popisky](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Návod: Zobrazení vyhrazené nápovědy](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Návod: Zobrazení dokončování příkazů](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Návod: Zobrazení návrhů](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)  
  
## <a name="import-the-service-provider"></a>Importovat poskytovatele služeb  
 Můžete také importovat <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (najít v sestavení Microsoft.VisualStudio.Shell.Immutable.10.0) stejným způsobem, chcete-li získat přístup ke službám Visual Studio:  
  
```csharp  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Zobrazit [návod: přístup k objektu DTE z rozšíření editoru](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) Další informace.  
  
## <a name="services"></a>Služby  
 Editor služby jsou obecně jednotlivé entity, které poskytují služby a jsou sdíleny napříč více komponent.  
  
|Importovat|Poskytuje|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Vztah mezi přípony souborů a <xref:Microsoft.VisualStudio.Utilities.IContentType> objekty.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Kolekce <xref:Microsoft.VisualStudio.Utilities.IContentType> objekty.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>objekty.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Mnoho objektů editoru adaptéru:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> Objekt pro zadaný text zobrazení.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> Rozdílů.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> Rozdílů.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> Nebo <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Sady <xref:Microsoft.VisualStudio.Text.ITextBuffer> objekty.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Pro <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Udržuje kolekci <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objekty.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> Pro textovou vyrovnávací paměť.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> Pro zobrazení textu.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> Pro zadaný obor.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> Pro zobrazení textu.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Automaticky odsazovat dostane <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> objekty.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Spravuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> pro <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generuje text ve formátu RTF ze sady rozsahy snímku.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> pro formátování řádků textu v zobrazení.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|A <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> objekt pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Vyhledá text snímku.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> Pro <xref:Microsoft.VisualStudio.Text.ITextBuffer> podle <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> Pro zobrazení textu.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standardní sada glyfů.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> Pro <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Zpracování pomocí klávesnice stopy.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standardní <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objekty.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Udržuje vztah mezi vyrovnávací paměti textu a <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> objekty.|  
  
## <a name="other-imports"></a>Další importy  
 Objekty Factory zprostředkovatelů a můžou být zprostředkovatelé jsou obecně entity, které může mít více instancí ve více komponent.  
  
|Importovat|Poskytuje|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> Typu <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) pro danou vyrovnávací paměti.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Označovatel značky text ( <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> Pro danou <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## <a name="see-also"></a>Viz také:  
 [Jazykové služby a editor Rozšiřovací body](../extensibility/language-service-and-editor-extension-points.md)
