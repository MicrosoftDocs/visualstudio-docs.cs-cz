---
title: Rozšíření služby jazyka a editoru | Microsoft Docs
description: Seznamte se s rozšiřovacími body v Visual Studio kódu, které můžete rozšířit, včetně většiny funkcí služby jazyka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 293851f1f3e72508a9bc119fb7551b0118ab2a9b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903144"
---
# <a name="language-service-and-editor-extension-points"></a>Nápěvné body služby jazyka a editoru
Editor poskytuje rozšiřovací body, které můžete rozšířit jako Managed Extensibility Framework komponent (MEF), včetně většiny funkcí služby jazyka. Toto jsou hlavní kategorie ná příponových bodů:

- Typy obsahu

- Typy klasifikace a formáty klasifikace

- Okraje a posuvníky

- Značky

- Ozdoby

- Procesory myši

- Obslužné rutiny pro zahodí

- Možnosti

- IntelliSense

## <a name="extend-content-types"></a>Rozšíření typů obsahu
 Typy obsahu jsou definice druhů textu, které editor zpracovává, například "text", "code" nebo "CSharp". Nový typ obsahu definujete deklarováním proměnné typu a poskytnutím jedinečného názvu nového <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> typu obsahu. Pokud chcete zaregistrovat typ obsahu v editoru, exportujte ho společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> je název typu obsahu.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> je název typu obsahu, ze kterého je tento typ obsahu odvozen. Typ obsahu může dědit z několika dalších typů obsahu.

  Vzhledem k <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> tomu, že třída je zapečetěná, můžete ji exportovat bez parametru typu.

  Následující příklad ukazuje atributy exportu pro definici typu obsahu.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Typy obsahu mohou být založené na žádných nebo více existujících typech obsahu. Toto jsou předdefinové typy:

- Libovolný: základní typ obsahu. Nadřazený prvek všech ostatních typů obsahu.

- Text: Základní typ pro obsah mimo projekci. Dědí z "any".

- Prostý text: pro text bez kódu. Dědí z "text".

- Kód: pro kód všech druhů. Dědí z "text".

- Inert: Vyloučí text z jakéhokoli druhu zpracování. U textu tohoto typu obsahu se nikdy nebude aplikovat žádné rozšíření.

- Projekce: pro obsah vyrovnávacích pamětí projekce. Dědí z "any".

- Intellisense: pro obsah IntelliSense. Dědí z "text".

- Sighelp: podpisová nápověda. Dědí z intellisense.

- Sighelp-doc: dokumentace k nápovědě k signaturě. Dědí z intellisense.

  Toto jsou některé typy obsahu, které jsou definovány Visual Studio a některé jazyky, které jsou hostovány v Visual Studio:

- Basic

- C/C++

- ConsoleOutput

- Csharp

- Šablony stylů CSS

- Enc

- FindResults (Výsledky hledání)

- F#

- HTML

- JScript

- XAML

- XML

  Pokud chcete zjistit seznam dostupných typů obsahu, naimportujte soubor , který udržuje kolekci typů <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> obsahu pro editor. Následující kód naimportuje tuto službu jako vlastnost.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Pokud chcete přidružit typ obsahu k příponě názvu souboru, použijte <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> .

> [!NOTE]
> V Visual Studio jsou přípony názvů souborů registrované pomocí v <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> balíčku služby jazyka. Přidruží <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> typ obsahu MEF k příponě názvu souboru, která byla zaregistrována tímto způsobem.

 Pokud chcete exportovat příponu názvu souboru do definice typu obsahu, musíte zahrnout následující atributy:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Určuje příponu názvu souboru.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Určuje typ obsahu.

  Vzhledem k <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> tomu, že třída je zapečetěná, můžete ji exportovat bez parametru typu.

  Následující příklad ukazuje export atributů pro příponu názvu souboru do definice typu obsahu.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 Spravuje přidružení mezi příponami názvů souborů a <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> typy obsahu.

## <a name="extend-classification-types-and-classification-formats"></a>Rozšíření typů klasifikace a formátů klasifikace
 Typy klasifikace můžete použít k definování druhů textu, pro který chcete zajistit různé zpracování (například obarvení "klíčového slova" textu modře a "komentář" textu zeleně). Definujte nový typ klasifikace deklarováním proměnné typu <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> a poskytnutím jedinečného názvu.

 Pokud chcete zaregistrovat typ klasifikace v editoru, exportujte ho společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název typu klasifikace.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: Název typu klasifikace, ze kterého tento typ klasifikace dědí. Všechny typy klasifikace dědí z textu a typ klasifikace může dědit z několika dalších typů klasifikace.

  Vzhledem k <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> tomu, že třída je zapečetěná, můžete ji exportovat bez parametru typu.

  Následující příklad ukazuje atributy exportu u definice typu klasifikace.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 Poskytuje <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> přístup ke standardním klasifikacím. Mezi předdefinové typy klasifikace patří:

- "text"

- "natural language" (odvozeno od "text")

- "formal language" (odvozený od "text")

- "string" (odvozeno od "literálu")

- "character" (odvozeno od "literálu")

- "numerické" (odvozeno od "literálu")

  Sada různých typů chyb dědí z <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> . Zahrnují následující typy chyb:

- "chyba syntaxe"

- Chyba kompilátoru

- "other error" (jiná chyba)

- "warning" (upozornění)

  Pokud chcete zjistit seznam dostupných typů klasifikace, naimportujte soubor , který udržuje kolekci typů klasifikace <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> pro editor. Následující kód naimportuje tuto službu jako vlastnost.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Pro nový typ klasifikace můžete definovat definici formátu klasifikace. Odvodit třídu z a <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> exportovat ji s <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> typem , společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název formátu.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: zobrazovaný název formátu.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Určuje, jestli se formát zobrazí na **stránce Písma** a barvy **dialogového okna** Možnosti.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: priorita formátu. Platné hodnoty jsou z <xref:Microsoft.VisualStudio.Text.Classification.Priority> .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: název typu klasifikace, na který je tento formát mapován.

  Následující příklad ukazuje atributy exportu v definici formátu klasifikace.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Chcete-li zjistit seznam dostupných formátů, importujte <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> , a udržujte kolekci formátů pro Editor. Následující kód importuje tuto službu jako vlastnost.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Rozšířené okraje a posuvníky
 Okraje a posuvníky jsou prvky hlavního zobrazení editoru vedle samotného zobrazení textu. Kromě standardních okrajů, které se zobrazují kolem textového zobrazení, můžete také zadat libovolný počet okrajů.

 Implementujte <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> rozhraní pro definování okraje. Je také nutné implementovat <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> rozhraní pro vytvoření okraje.

 Chcete-li zaregistrovat poskytovatele marže v editoru, je nutné exportovat poskytovatele společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název okraje.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: pořadí, ve kterém se okraj zobrazuje vzhledem k ostatním okrajům.

   Jsou to předdefinované okraje:

  - "Horizontal ScrollBar WPF"

  - "Svislý posuvník WPF"

  - "Okraj pro číslo řádku WPF"

    Vodorovné okraje, které mají atribut Order, `After="Wpf Horizontal Scrollbar"` jsou zobrazeny pod předdefinovaným okrajem a vodorovné okraje, které mají atribut Order, `Before ="Wpf Horizontal Scrollbar"` se zobrazí nad rámec předdefinovaného okraje. Pravé svislé okraje, které mají atribut Order, `After="Wpf Vertical Scrollbar"` jsou zobrazeny napravo od posuvníku. Levé svislé okraje, které mají atribut Order, `After="Wpf Line Number Margin"` se zobrazí nalevo od okraje s číslem řádku (Pokud je zobrazený).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: druh okraje (vlevo, vpravo, nahoře nebo dole).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "Code"), pro který je vaše marže platná.

  Následující příklad ukazuje atributy exportu u poskytovatele okrajů pro okraj, který se zobrazí napravo od okraje s číslem řádku.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Rozšiřování značek
 Značky představují způsob, jak přidružit data k různým druhům textu. V mnoha případech se přidružená data zobrazují jako vizuální efekt, ale ne všechny značky mají vizuální prezentaci. Můžete definovat vlastní typ značky implementací <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Je také nutné implementovat <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> pro poskytnutí značek pro danou sadu textu, a <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> pro poskytnutí autor značky. Je nutné exportovat poskytovatele autor značky spolu s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "Code"), pro který je značka platná.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: druh značky.

  Následující příklad ukazuje atributy exportu u poskytovatele autor značky.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> následující typy značek jsou předdefinované:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: přidruženo k <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: přidruženo k typům chyb.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: přidruženo k vylepšení.

  > [!NOTE]
  > Příklad naleznete <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> v tématu definice HighlightWordTag v [návodu: zvýraznění textu](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: souvisí s oblastmi, které lze rozbalit nebo sbalit v sbalení.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definuje prostor, v němž je ovládací prvek v textovém zobrazení obsazený. Další informace o dalších možnostech vyjednávání najdete v následující části.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: poskytuje automatické mezery a velikost pro doplňky.

  Chcete-li vyhledat a použít značky pro vyrovnávací paměti a zobrazení, importujte <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> nebo <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> , který poskytuje <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> požadovaný typ. Následující kód importuje tuto službu jako vlastnost.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Značky a MarkerFormatDefinitions
 Můžete zvětšit <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> třídu pro definování vzhledu značky. Musíte exportovat třídu (jako <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> ) s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název použitý k odkazování na tento formát

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: způsobí zobrazení formátu v uživatelském rozhraní.

  V konstruktoru definujte zobrazované jméno a vzhled značky. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> Definuje barvu výplně a <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> Definuje barvu ohraničení. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>Je název lokalizovatelné definice formátu.

  Následuje příklad definice formátu:

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

 Chcete-li tuto definici formátu použít pro značku, odkazujte na název, který jste nastavili v atributu name třídy (nikoli zobrazované jméno).

> [!NOTE]
> Příklad naleznete v <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> tématu Třída HighlightWordFormatDefinition v [návodu: zvýraznění textu](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Rozšiřování vylepšení
 Doplňky definují vizuální efekty, které se dají přidat k textu, který se zobrazí v textovém zobrazení nebo v samotném zobrazení textu. Můžete definovat vlastní doplňky jako libovolný typ <xref:System.Windows.UIElement> .

 Ve třídě pro úpravy musíte deklarovat <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> . Chcete-li zaregistrovat vrstvu pro navýšení, exportujte ji společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název přívylepšení.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: pořadí doplňků s ohledem na jiné vrstvy příúprav. Třída <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definuje čtyři výchozí vrstvy: výběr, sbalení, blikající kurzor a text.

  Následující příklad ukazuje atributy exportu v definici vrstvy pro doplňky.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Je nutné vytvořit druhou třídu, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> a zpracuje její událost vytvořením doplňku <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> . Tuto třídu musíte exportovat spolu s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "Code"), pro který je doplňky platné.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: typ textového zobrazení, pro které je toto doplňky platné. Třída <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> má sadu předdefinovaných rolí zobrazení textu. Například <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> se primárně používá pro textová zobrazení souborů. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> se používá pro textová zobrazení, která může uživatel upravovat nebo navigovat pomocí myši a klávesnice. Příklady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> zobrazení jsou zobrazení textu editoru a okno **výstup** .

  Následující příklad ukazuje atributy exportu u poskytovatele doplňků.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Příznakem pro vyjednávání je jedno, které zabírá místo na stejné úrovni jako text. Chcete-li vytvořit tento druh doplňku, je nutné definovat třídu značek, která dědí z <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> , což definuje množství místa, které je přidaným vylepšením.

 Stejně jako u všech vylepšení je nutné exportovat definici vrstvy doplňků.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Chcete-li vytvořit instanci rozšíření pro vyjednávání prostoru, je nutné vytvořit třídu, která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> kromě třídy, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (jako u jiných druhů vylepšení).

 Chcete-li zaregistrovat poskytovatele autor značky, je nutné jej exportovat společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "Code"), pro který je vaše doplňky platné.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: typ textového zobrazení, pro který je tato značka nebo doplňky platná. Třída <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> má sadu předdefinovaných rolí zobrazení textu. Například <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> se primárně používá pro textová zobrazení souborů. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> se používá pro textová zobrazení, která může uživatel upravovat nebo navigovat pomocí myši a klávesnice. Příklady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> zobrazení jsou zobrazení textu editoru a okno **výstup** .

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: druh značky nebo doplňky, kterou jste definovali. Je nutné přidat druhý <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> pro <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  Následující příklad ukazuje atributy exportu v poskytovateli autor značky pro značku přidání prostoru pro vyjednávání.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Rozšíření procesorů myši
 Pro vstup myši můžete přidat speciální zpracování. Vytvořte třídu, která dědí z <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> a přepíše události myši pro vstup, který chcete zpracovat. Také je nutné implementovat <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> do druhé třídy a exportovat je společně s tím <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , který určuje druh obsahu (například "text" nebo "kód"), pro který je obslužná rutina myši platná.

 Následující příklad ukazuje atributy exportu u poskytovatele procesoru myši.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Rozšiřování obslužných rutin přetažení
 Můžete přizpůsobit chování obslužných rutin drop pro konkrétní druhy textu vytvořením třídy, která implementuje, <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> a druhé třídy, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> k vytvoření obslužné rutiny drop. Je nutné exportovat rutinu drop spolu s následujícími atributy:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: textový formát, pro který je tato obslužná rutina drop platná. Následující formáty jsou zpracovávány v pořadí podle priority od nejvyšší po nejnižší:

  1. Libovolný vlastní formát

  2. Přetažení

  3. EnhancedMetafile

  4. WaveAudio

  5. Riff

  6. Formát

  7. Národní prostředí

  8. Zadání

  9. PenData

  10. Serializovatelný

  11. SymbolicLink

  12. Formátu

  13. XamlPackage

  14. TIFF

  15. Monochromatick

  16. Formátu

  17. MetafilePicture

  18. CSV

  19. System. String

  20. Formát HTML

  21. UnicodeText

  22. OEMText

  23. Text

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název obslužné rutiny drop.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: řazení obslužné rutiny drop před nebo po výchozí obslužné rutině drop. Výchozí obslužná rutina drop pro Visual Studio má název "DefaultFileDropHandler".

  Následující příklad ukazuje atributy exportu u zprostředkovatele obslužné rutiny drop.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Rozšíření možností editoru
 Můžete definovat možnosti, které budou platné pouze v určitém oboru, například v textovém zobrazení. Editor poskytuje tuto sadu předdefinovaných možností: možnosti editoru, možnosti zobrazení a Windows Presentation Foundation (WPF) možnosti zobrazení. Tyto možnosti lze nalézt v <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> , <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> a <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 Chcete-li přidat novou možnost, odvodit třídu z jedné z těchto tříd definice možnosti:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Následující příklad ukazuje, jak exportovat definici možnosti, která má logickou hodnotu.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Rozšiřování IntelliSense
 IntelliSense je obecný termín pro skupinu funkcí, které poskytují informace o strukturovaném textu a doplňování příkazů. Mezi tyto funkce patří dokončování příkazů, podpisová Help, rychlé informace a žárovky. Dokončování příkazů pomáhá uživatelům zadat klíčové slovo jazyka nebo název člena správně. Help signatura zobrazí podpis nebo signatury pro metodu, kterou uživatel právě zadal. Rychlé informace zobrazí úplný podpis pro typ nebo název členu, když se na něj nachází ukazatel myši. Žárovka poskytuje další akce pro určité identifikátory v určitých kontextech, například přejmenování všech výskytů proměnné po přejmenování jednoho výskytu.

 Návrh funkce technologie IntelliSense je v všech případech stejný:

- *Zprostředkovatel* IntelliSense je zodpovědný za celý proces.

- *Relace* IntelliSense představuje posloupnost událostí mezi triggerem a potvrzením nebo zrušením výběru. Relace je obvykle aktivována pomocí některého gesta uživatele.

- *Kontroler* technologie IntelliSense zodpovídá za rozhodování, kdy by relace měla začít a končit. Také se rozhodne, kdy by měly být informace potvrzeny a kdy se má relace zrušit.

- *Zdroj* technologie IntelliSense poskytuje obsah a rozhoduje, co nejlépe odpovídá.

- *Předvádějící* IntelliSense zodpovídá za zobrazení obsahu.

  Ve většině případů doporučujeme zadat alespoň zdroj a kontroler. Chcete-li zobrazení přizpůsobit, můžete také zadat přednášejícího.

### <a name="implement-an-intellisense-source"></a>Implementace zdroje IntelliSense
 Chcete-li přizpůsobit zdroj, je nutné implementovat jednu (nebo více) následujících zdrojových rozhraní:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> se již nepoužívá namísto <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 Kromě toho je nutné implementovat poskytovatele stejného druhu:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> se již nepoužívá namísto <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 Je nutné exportovat zprostředkovatele společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název zdroje.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "Code"), na který se vztahuje zdroj.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: pořadí, ve kterém se má zdroj zobrazovat (s ohledem na jiné zdroje).

- Následující příklad ukazuje atributy exportu u poskytovatele zdroje dokončení.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Další informace o implementaci zdrojů IntelliSense naleznete v následujících návodech:

- [Návod: zobrazení QuickInfoch popisků](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Návod: zobrazení podpisu – Help](../extensibility/walkthrough-displaying-signature-help.md)

- [Návod: dokončování příkazů zobrazení](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementace kontroleru IntelliSense
 Chcete-li přizpůsobit kontroler, je nutné implementovat <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> rozhraní. Kromě toho musíte implementovat poskytovatele kontroleru společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název kontroleru.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "Code"), na který se kontroler vztahuje.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: pořadí, ve kterém se má kontroler zobrazit (s ohledem na jiné řadiče).

  Následující příklad ukazuje atributy exportu u poskytovatele kontroleru dokončení.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Další informace o použití řadičů IntelliSense najdete v následujících návodech:

- [Návod: zobrazení QuickInfoch popisků](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
