---
title: Služba jazyka a editoru Rozšiřovací body | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0bcbef5094bd12392b7ea79865e1d28e2934a11e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743588"
---
# <a name="language-service-and-editor-extension-points"></a>Rozšiřovací body služeb jazyka a editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor poskytuje Rozšiřovací body, které můžete rozšířit jako součásti Managed Extensibility Framework (MEF), včetně většina funkcí služby jazyka. Toto jsou hlavní rozšíření kategorií bodu:  
  
-   Typy obsahu  
  
-   Typy klasifikace a klasifikace formáty  
  
-   Okraje a posuvníky  
  
-   Značky  
  
-   Vylepšení  
  
-   Procesory myši  
  
-   Vyřadit obslužné rutiny  
  
-   Možnosti  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>Rozšíření typů obsahu  
 Typy obsahu jsou definice typů zpracovat editoru, například text, "text", "kód" nebo "CSharp". Nový typ obsahu definujete deklarováním proměnné typu <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> a poskytuje jedinečný název nového typu obsahu. K registraci typu obsahu v editoru, exportujte ho spolu s následujícími atributy:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> je název typu obsahu.  
  
- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> je název typu obsahu, ze kterého je odvozen tohoto typu obsahu. Typ obsahu může dědit z více jiné typy obsahu.  
  
  Vzhledem k tomu, <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> zapečetěné třídy, můžete ho exportovat s parametr typu.  
  
  Následující příklad ukazuje atributů exportu v definici typu obsahu.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Typy obsahu, může být založen na nula nebo více stávajícím obsahu typy. Toto jsou předdefinované typy:  
  
- Žádné: základní typ obsahu. Nadřazený všechny ostatní typy obsahu.  
  
- Text: základní typ pro jiné projekci obsahu. Dědí z "žádný".  
  
- Ve formátu prostého textu: pro text bez kódu. Dědí z "text".  
  
- Kód: pro kód všeho druhu. Dědí z "text".  
  
- Inertním: vyloučí z jakéhokoli druhu zpracování textu. Text tohoto typu obsahu nebude mít nikdy žádná všechna rozšíření použit.  
  
- Projekce: za obsah vyrovnávací paměti projekce. Dědí z "žádný".  
  
- IntelliSense: pro obsah technologie IntelliSense. Dědí z "text".  
  
- Sighelp: nápovědu k signatuře. Dědí z "intellisense".  
  
- Sighelp-doc: dokumentace nápovědy podpis. Dědí z "intellisense".  
  
  Toto jsou některé typy obsahu, které jsou definovány pomocí sady Visual Studio a některých jazyků, které jsou hostovány v sadě Visual Studio:  
  
- Základní  
  
- C/C++  
  
- ConsoleOutput  
  
- CSharp  
  
- CSS  
  
- KODÉRU  
  
- FindResults  
  
- F#  
  
- HTML  
  
- JScript  
  
- XAML  
  
- XML  
  
  Chcete-li vyhledat seznam dostupných typů obsahu, importovat <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, která udržuje kolekci typů obsahu editoru. Následující kód importuje tuto službu jako vlastnost.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Chcete-li přidružit typu obsahu s příponou názvu souboru, použijte <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  V sadě Visual Studio, jsou registrované přípony názvů souborů pomocí <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> v balíčku služby jazyka. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Přidruží MEF typu obsahu s příponou názvu souboru, který byl zaregistrován tímto způsobem.  
  
 Pokud chcete exportovat příponu názvu souboru do definice typu obsahu, musí obsahovat následující atributy:  
  
- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Určuje příponu názvu souboru.  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Určuje typ obsahu.  
  
  Vzhledem k tomu, <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> zapečetěné třídy, můžete ho exportovat s parametr typu.  
  
  Následující příklad ukazuje export atributy na příponu názvu souboru s definicí typu obsahu.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> Spravuje přidružení přípony názvů souborů a typy obsahu.  
  
## <a name="extending-classification-types-and-classification-formats"></a>Rozšíření typů klasifikaci a klasifikaci formáty  
 Typy klasifikace můžete použít k definování typů text, pro které chcete poskytnout různé zpracování (například obarvení modrý text "– klíčové slovo" a "komentář" zelená). Definujte nový typ klasifikace deklarováním proměnné typu <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> a poskytuje tak jedinečný název.  
  
 Pokud chcete zaregistrovat typ klasifikace editor, ho exportujte společně s následujícími atributy:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název typu klasifikace.  
  
- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: název typu klasifikace, ze kterého dědí tento typ klasifikace. Všechny typy klasifikace dědí "text" a typ klasifikace může dědit z více jiných typů klasifikace.  
  
  Vzhledem k tomu, <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> zapečetěné třídy, můžete ho exportovat s parametr typu.  
  
  Následující příklad ukazuje atributů exportu v definici typu klasifikace.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> Poskytuje přístup ke standardní klasifikace. Typy integrovaných klasifikace patří tyto:  
  
- "text"  
  
- "přirozeného jazyka" (je odvozen od "text")  
  
- "formální jazyk" (je odvozen od "text")  
  
- "string" (je odvozen od "literál")  
  
- "znak" (je odvozen od "literál")  
  
- "Číselná" (je odvozen od "literál")  
  
  Sadu typů různých chyb dědí <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Patří mezi ně následující typy chyb:  
  
- "Chyba syntaxe"  
  
- "Chyba kompilátoru"  
  
- "Další chyba"  
  
- "upozornění"  
  
  Chcete-li vyhledat seznam dostupných typů klasifikace, importovat <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, která udržuje kolekci typů klasifikace pro editor. Následující kód importuje tuto službu jako vlastnost.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Definici formátu klasifikace můžete definovat pro nový typ klasifikace. Odvodit třídu z <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> a exportujte ho s typem <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>společně s následujícími atributy:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název formátu.  
  
- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: Zobrazovaný název formátu.  
  
- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Určuje, zda se zobrazí ve formátu na **písma a barvy** stránku **možnosti** dialogové okno.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: Priorita formátu. Platné hodnoty jsou od <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: Tento formát je namapovaný zadejte název klasifikace.  
  
  Následující příklad ukazuje atributů exportu v definici formátu klasifikace.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Chcete-li zjistit, ze seznamu dostupných formátů, importovat <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, která udržuje kolekci formáty pro editor. Následující kód importuje tuto službu jako vlastnost.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>Rozšiřování okraje a posuvníky  
 Okraje a posuvníky jsou prvky hlavního zobrazení editoru kromě samotného zobrazení textu. Můžete zadat libovolný počet okraje kromě standardních okraje, které se zobrazí po zobrazení textu.  
  
 Implementace <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> rozhraní k definování okraj. Musíte také implementovat <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> rozhraní pro vytváření na okraj.  
  
 Zaregistrujte poskytovatele okraj v editoru, musíte exportovat poskytovatele společně s následujícími atributy:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název na okraj.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: pořadí, ve kterém se zobrazí na okraji, vzhledem k jinými okraji.  
  
   Toto jsou integrované okraje:  
  
  - "Wpf vodorovný posuvník"  
  
  - "Wpf svislý posuvník"  
  
  - "Číslo řádku Wpf okraj"  
  
    Vodorovné okraje, které mají atribut pořadí `After="Wpf Horizontal Scrollbar"` se zobrazí pod integrované okraj a horizontální okraje, které mají atribut pořadí `Before ="Wpf Horizontal Scrollbar"` se zobrazují nad integrované okraj. Klikněte pravým tlačítkem myši svislé okraje, které mají atribut pořadí `After="Wpf Vertical Scrollbar"` se zobrazí napravo od posuvník. Left svislé okraje, které mají atribut pořadí `After="Wpf Line Number Margin"` (Pokud je zobrazen) se zobrazí na levém okraji čísla řádku.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: typ rozpětí (vlevo, vpravo, nahoře nebo dole).  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsah (například "text" nebo "code"), pro který je platný vaše okraj.  
  
  Následující příklad ukazuje export atributy na zprostředkovateli okraj okraje, která se zobrazí napravo od na okraji čísla řádku.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Rozšíření značek  
 Značky jsou způsob, jak data přidružení různé druhy textu. V mnoha případech související data se zobrazí jako vizuální efekt, ale ne všechny značky obsahovat vizuální prezentace. Můžete definovat vlastní typ značky implementací <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Musíte také implementovat <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> zajištění značky pro danou sadu rozpětí textu a <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> poskytnout označovatel. Je nutné exportovat poskytovateli označovatel společně s následujícími atributy:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: typ obsah (například "text" nebo "code"), pro který je platný vaší značky.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: typ značky.  
  
  Následující příklad ukazuje na zprostředkovateli označovatel atributů exportu.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TagType(typeof(TestTag))]  
internal class TestTaggerProvider : ITaggerProvider  
```  
  
 Následující typy značky jsou předdefinované:  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: přidružené <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: přidružené typy chyb.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: přidružené dalších úprav.  
  
  > [!NOTE]
  >  Příklad <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, viz HighlightWordTag definice v [návod: zvýraznění textu](../extensibility/walkthrough-highlighting-text.md).  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: přidružené k oblasti, které můžete rozbalit nebo sbalit v osnovy.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definuje prostor zabírá dalších úprav v náhledu textu. Další informace o vylepšení vyjednávání místa najdete v následující části.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: poskytuje automatické mezery a velikosti dalších úprav.  
  
  Vyhledání a používání značek pro vyrovnávací paměť a zobrazení, naimportujte <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> nebo <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, která získáte <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> požadovaného typu. Následující kód importuje tuto službu jako vlastnost.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Značky a MarkerFormatDefinitions  
 Můžete rozšířit <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> tříd k definování vzhledu značky. Je nutné exportovat vaší třídy (jako <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) s následujícími atributy:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název, který odkazuje tento formát  
  
- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: To způsobí, že formát, který se zobrazí v uživatelském rozhraní  
  
  V konstruktoru definujete zobrazovaný název a vzhled značky. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> Určuje barvu výplně a <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> definuje barvu ohraničení. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> Je lokalizovatelný název definice formátu.  
  
  Následuje příklad formátu definice:  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 Použít tento formát definice pro značku, odkazovat na název, který jste nastavili v atribut názvu třídy (ne zobrazovaným názvem).  
  
> [!NOTE]
>  Příklad <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, naleznete v tématu třídy HighlightWordFormatDefinition v [návod: zvýraznění textu](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extending-adornments"></a>Rozšíření grafických doplňků  
 Vylepšení definování vizuální efekty, které je možné přidat buď na text, který se zobrazí v náhledu textu nebo textu zobrazení samotný. Můžete definovat vlastní dalších úprav jako libovolný typ <xref:System.Windows.UIElement>.  
  
 Ve třídě dalších úprav, je třeba deklarovat <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. K registraci dalších úprav vrstvě, exportujte ho spolu s následujícími atributy:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název dalších úprav.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: řazení dalších úprav s ohledem na ostatních vrstvách dalších úprav. Třída <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definuje čtyři vrstvy výchozí: výběr, osnova, blikajícího kurzoru a Text.  
  
  Následující příklad ukazuje export atributy na definici vrstvy dalších úprav.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Je nutné vytvořit druhá třída, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> a zpracovává jeho <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> událostí po vytvoření instance dalších úprav. Je nutné exportovat této třídy společně s následujícími atributy:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: typ obsahu (například "text" nebo "code"), pro který je platný dalších úprav.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: typ textové zobrazení, pro kterou platí tato dalších úprav. Třída <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> obsahuje sadu rolí předdefinovaný text zobrazení. Například <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> primárně slouží k zobrazení textu souborů. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> slouží k zobrazení textu, že uživatel může upravovat nebo Navigovat pomocí myši a klávesnice. Příklady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> zobrazení jsou zobrazení textového editoru a **výstup** okna.  
  
  Následující příklad ukazuje atributů exportu v poskytovateli dalších úprav.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Dalších úprav vyjednávání místa je ten, který zabírá místo na stejné úrovni jako text. Chcete-li vytvořit tento druh dalších úprav, je nutné definovat, která dědí z třídy značka <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, která definuje velikost místa zabírá dalších úprav.  
  
 Stejně jako u všech grafických doplňků, musíte exportovat definice vrstvy dalších úprav.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 K vytvoření instance dalších úprav vyjednávání místa, je nutné vytvořit třídu, která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, kromě třídu, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (stejně jako u jiných typů vylepšení).  
  
 Zaregistrujte poskytovatele označovatel, je nutné jej exportovat společně s následujícími atributy:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: typ obsahu (například "text" nebo "code"), pro který je platný vašich dalších úprav.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: typ textové zobrazení, pro které bude tato značka nebo dalších úprav je platný. Třída <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> obsahuje sadu rolí předdefinovaný text zobrazení. Například <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> primárně slouží k zobrazení textu souborů. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> slouží k zobrazení textu, že uživatel může upravovat nebo Navigovat pomocí myši a klávesnice. Příklady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> zobrazení jsou zobrazení textového editoru a **výstup** okna.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: typ značky nebo dalších úprav, které jste definovali. Je nutné přidat sekundy <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> pro <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
  Následující příklad ukazuje atributů exportu v poskytovateli označovatel pro značku vyjednávání místo dalších úprav.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Rozšíření myši procesorů  
 Můžete přidat zvláštní zacházení vstup z myši. Vytvořte třídu, která dědí z <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> a přepsat události myši pro zpracování vstupu. Musíte také implementovat <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> v druhé třídu a exportujte ho spolu s <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> určující druh obsah (například "text" nebo "code"), pro který je platný obslužnou rutinu myši.  
  
 Následující příklad ukazuje atributů exportu ve zprostředkovateli procesoru myši.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Rozšíření obslužné rutiny přetažení  
 Můžete přizpůsobit chování rozevírací obslužných rutin pro konkrétní druhy text tak, že vytvoříte třídu, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> a druhá třída, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> vytvořit obslužnou rutinu přetažení. Je nutné exportovat obslužnou rutinu přetažení společně s následujícími atributy:  
  
- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: v textovém formátu, pro kterou platí tato obslužná rutina přetažení. Následující formáty jsou zpracovány v pořadí podle priority od nejvyšší po nejnižší:  
  
  1.  Všechny vlastní formát  
  
  2.  FileDrop  
  
  3.  EnhancedMetafile  
  
  4.  WaveAudio  
  
  5.  RIFF  
  
  6.  DIF  
  
  7.  Národní prostředí  
  
  8.  Paleta  
  
  9. PenData  
  
  10. Serializovatelné  
  
  11. SymbolicLink  
  
  12. XAML  
  
  13. XamlPackage  
  
  14. TIFF  
  
  15. Rastrový obrázek  
  
  16. DIB  
  
  17. MetafilePicture  
  
  18. SDÍLENÝ SVAZEK CLUSTERU  
  
  19. System.String  
  
  20. Formát HTML  
  
  21. UnicodeText  
  
  22. OEMText  
  
  23. Text  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název obslužnou rutinu přetažení.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: řazení obslužnou rutinu přetažení před nebo po ní výchozí obslužnou rutinu přetažení. Výchozí obslužnou rutinu přetažení pro sadu Visual Studio je s názvem "DefaultFileDropHandler".  
  
  Následující příklad ukazuje atributů exportu ve zprostředkovateli obslužná rutina přetažení.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Rozšíření možností editoru  
 Můžete definovat možnosti platný pouze v určitém rozsahu, například v náhledu textu. Tato sada předdefinovaných možností nabízí editor: Možnosti editoru, možnosti zobrazení a zobrazení možností Windows Presentation Foundation (WPF). Tyto možnosti lze nalézt v <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, a <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Pokud chcete přidat novou možnost, odvodíte třídu z jedné z těchto možností definice tříd:  
  
- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
  Následující příklad ukazuje, jak exportovat definice možnosti, která má hodnotu typu Boolean.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>Rozšíření technologie IntelliSense  
 Technologie IntelliSense je obecný termín pro skupinu funkcí, které poskytují informace o strukturovaných textových a dokončování pro něj. Tyto funkce patří dokončování příkazů, podpisu a rychlé informace a návrhy. Dokončování příkazů pomáhá uživatelům správně zadat název jazyka – klíčové slovo nebo člen. Nápovědu k signatuře zobrazí podpis nebo podpisy pro metodu, která má uživatel právě zadali. Rychlé informace zobrazí úplný podpis pro název typu nebo člena, když myší postavená na něm. Žárovka poskytovat další akce pro určité identifikátory v některých kontextech, například přejmenování všech výskytů dané proměnné po jeden výskyt je přejmenovaná.  
  
 Návrh funkci IntelliSense je skoro stejné ve všech případech:  
  
- IntelliSense *zprostředkovatele* je zodpovědný za celý proces.  
  
- IntelliSense *relace* představuje posloupnost událostí mezi aktivace komponentě přednášejícího a committal nebo zrušení výběru. Relace se obvykle aktivuje nějaké gesto uživatele.  
  
- IntelliSense *řadič* zodpovídá za rozhodování o tom, kdy by měla relace zahájení a ukončení. Také určuje, kdy informace by se měly potvrdit a kdy by se měly zrušit relace.  
  
- IntelliSense *zdroj* poskytuje obsah a rozhodne, která je nejlepší shodou.  
  
- IntelliSense *skládání* zodpovídá za zobrazení obsahu.  
  
  Ve většině případů doporučujeme poskytnout alespoň zdroji a kontroler. Můžete také zadat skládání, pokud chcete přizpůsobit zobrazení.  
  
### <a name="implementing-an-intellisense-source"></a>Implementace zdroj technologie IntelliSense  
 Přizpůsobení zdroji, musí implementovat jednu (nebo více) rozhraní následující zdroje:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> se už nepoužívá nahrazený <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Kromě toho je nutné implementovat zprostředkovatele stejného druhu:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> se už nepoužívá nahrazený <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Je nutné exportovat poskytovatele společně s následujícími atributy:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název zdroje.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: typ obsah (například "text" nebo "code"), ke kterému se vztahuje na zdroj.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: pořadí, ve kterém by se měla objevit zdroj (s ohledem na další zdroje).  
  
-   Následující příklad ukazuje export atributy u poskytovatele zdroj dokončení.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Další informace o implementaci zdroje technologie IntelliSense najdete v následujících návodech:  
  
 [Návod: Zobrazení popisů tlačítek s rychlými informacemi](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Návod: Zobrazení vyhrazené nápovědy](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Návod: Zobrazení dokončování příkazů](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Implementace řadič služby technologie IntelliSense  
 Přizpůsobení kontroleru, je nutné implementovat <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> rozhraní. Kromě toho je nutné implementovat zprostředkovatele kontroleru společně s následujícími atributy:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název kontroleru.  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: typ obsahu (například "text" nebo "code"), ke kterému se vztahuje na řadič.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: pořadí, ve kterém by se měla objevit kontroler (s ohledem na ostatní řadiče).  
  
  Následující příklad ukazuje na zprostředkovatele kontroleru dokončení atributů exportu.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Další informace o používání řadiče technologie IntelliSense najdete v následujících návodech:  
  
 [Návod: Zobrazení popisů tlačítek s rychlými informacemi](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

