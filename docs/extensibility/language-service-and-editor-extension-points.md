---
title: Jazykové služby a rozšiřující body editoru | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bb086eb99e4b8128c04f62f9b370eb2eab8fa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703047"
---
# <a name="language-service-and-editor-extension-points"></a>Jazykové služby a rozšiřující body editoru
Editor poskytuje rozšiřující body, které můžete rozšířit jako součásti architektury spravované rozšiřitelnosti (MEF), včetně většiny funkcí jazykové služby. Toto jsou hlavní kategorie bodů rozšíření:

- Typy obsahu

- Typy klasifikací a formáty klasifikace

- Okraje a posuvníky

- Značky

- Ozdoby

- Myš procesory

- Obslužné rutiny přetažení

- Možnosti

- IntelliSense

## <a name="extend-content-types"></a>Rozšíření typů obsahu
 Typy obsahu jsou definice druhů textu zpracovávaných editorem, například "text", "kód" nebo "CSharp". Nový typ obsahu definujete deklarováním <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> proměnné typu a zadáním jedinečného názvu nového typu obsahu. Chcete-li zaregistrovat typ obsahu v editoru, exportujte jej spolu s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>je název typu obsahu.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>je název typu obsahu, ze kterého je tento typ obsahu odvozen. Typ obsahu může dědit z více jiných typů obsahu.

  Vzhledem <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> k tomu, že třída je zapečetěna, můžete ji exportovat bez parametru typu.

  Následující příklad ukazuje atributy exportu v definici typu obsahu.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Typy obsahu mohou být založeny na nule nebo více již existujících typech obsahu. Jedná se o vestavěné typy:

- Jakýkoliv: základní typ obsahu. Nadřazený všechny ostatní typy obsahu.

- Text: základní typ pro obsah bez projekce. Dědí z "any".

- Prostý text: pro text bez kódu. Dědí z "text".

- Kód: pro kód všeho druhu. Dědí z "text".

- Inertní: vylučuje text z jakéhokoli druhu manipulace. U textu tohoto typu obsahu nebude nikdy použito žádné rozšíření.

- Projekce: pro obsah projekčních pufry. Dědí z "any".

- Intellisense: pro obsah IntelliSense. Dědí z "text".

- Sighelp: podpis pomoc. Dědí z "intellisense".

- Sighelp-doc: dokumentace nápovědy k podpisu. Dědí z "intellisense".

  Toto jsou některé typy obsahu, které jsou definovány visual studio a některé jazyky, které jsou hostované v sadě Visual Studio:

- Základní

- C/C++

- ConsoleOutput

- Csharp

- CSS

- Enc

- NajítVýsledky

- F#

- HTML

- JScript

- XAML

- XML

  Chcete-li zjistit seznam dostupných <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>typů obsahu, importujte soubor , který udržuje kolekci typů obsahu pro editor. Následující kód importuje tuto službu jako vlastnost.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Chcete-li přidružit typ obsahu <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>k příponě názvu souboru, použijte .

> [!NOTE]
> V sadě Visual Studio jsou přípony <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> názvů souborů registrovány pomocí balíčku služby jazyka. Přidruží <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> typ obsahu MEF s příponou názvu souboru, která byla zapsána tímto způsobem.

 Chcete-li exportovat příponu názvu souboru do definice typu obsahu, musíte uvést následující atributy:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: určuje příponu názvu souboru.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: určuje typ obsahu.

  Vzhledem <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> k tomu, že třída je zapečetěna, můžete ji exportovat bez parametru typu.

  Následující příklad ukazuje atributy exportu přípony názvu souboru do definice typu obsahu.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 Spravuje <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> přidružení mezi příponami názvů souborů a typy obsahu.

## <a name="extend-classification-types-and-classification-formats"></a>Rozšíření typů klasifikací a formátů klasifikace
 Typy klasifikace můžete použít k definování typů textu, pro které chcete poskytnout různé zpracování (například vybarvení "klíčové slovo" text modrý a "komentář" text zelený). Definujte nový typ klasifikace deklarováním proměnné typu <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> a jeho jedinečným názvem.

 Chcete-li zaregistrovat typ klasifikace u editoru, exportujte jej spolu s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název typu klasifikace.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: název typu klasifikace, ze kterého tento typ klasifikace dědí. Všechny typy klasifikace dědí z "text" a typ klasifikace může dědit z více jiných typů klasifikace.

  Vzhledem <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> k tomu, že třída je zapečetěna, můžete ji exportovat bez parametru typu.

  Následující příklad ukazuje atributy exportu v definici typu klasifikace.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 Poskytuje <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> přístup ke standardním klasifikacím. Integrované typy klasifikace zahrnují tyto:

- "text"

- "přirozený jazyk" (odvozený z "textu")

- "formální jazyk" (odvozený z "textu")

- "string" (odvodí z "literálu")

- "znak" (pochází z "literálu")

- "číselné" (odvozeno z "literálu")

  Sada různých typů chyb <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>dědí z . Zahrnují následující typy chyb:

- "syntaktická chyba"

- "chyba kompilátoru"

- "jiná chyba"

- "varování"

  Chcete-li zjistit seznam dostupných <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>typů klasifikace, importujte , který udržuje kolekci typů klasifikace pro editor. Následující kód importuje tuto službu jako vlastnost.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Můžete definovat definici formátu klasifikace pro nový typ klasifikace. Odvodit <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> třídu z <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>a exportovat s typem , spolu s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název formátu.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: zobrazovaný název formátu.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Určuje, zda se formát zobrazí na stránce **Písma a barvy** dialogového okna **Volby.**

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: priorita formátu. Platné hodnoty <xref:Microsoft.VisualStudio.Text.Classification.Priority>jsou z .

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

 Chcete-li zjistit seznam dostupných <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>formátů, importujte soubor , který udržuje kolekci formátů pro editor. Následující kód importuje tuto službu jako vlastnost.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Rozšíření okrajů a posuvníků
 Okraje a posuvníky jsou hlavní prvky zobrazení editoru kromě samotného zobrazení textu. Kromě standardních okrajů, které se zobrazují kolem textového zobrazení, můžete zadat libovolný počet okrajů.

 Implementujte <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> rozhraní k definování okraje. Je také nutné <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> implementovat rozhraní k vytvoření okraje.

 Chcete-li zaregistrovat zprostředkovatele marže u editoru, musíte exportovat zprostředkovatele spolu s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název okraje.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: pořadí, ve kterém se okraj zobrazuje vzhledem k ostatním okrajům.

   Jedná se o předdefinované marže:

  - "Wpf vodorovný posuvník"

  - "Wpf svislý posuvník"

  - "Wpf řádek číslo rozpětí"

    Vodorovné okraje, které mají `After="Wpf Horizontal Scrollbar"` atribut pořadí jsou zobrazeny pod předdefinovaným okrajem a `Before ="Wpf Horizontal Scrollbar"` vodorovné okraje, které mají atribut pořadí, jsou zobrazeny nad předdefinovaným okrajem. Pravé svislé okraje, `After="Wpf Vertical Scrollbar"` které mají atribut pořadí jsou zobrazeny vpravo od posuvníku. Vlevo svislé okraje, `After="Wpf Line Number Margin"` které mají atribut pořadí, se zobrazí vlevo od okraje čísla řádku (pokud je viditelný).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: druh okraje (vlevo, vpravo, nahoře nebo dole).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "kód"), pro který je vaše marže platná.

  Následující příklad ukazuje atributy exportu na zprostředkovatele marže pro okraj, který se zobrazí vpravo od okraje čísla řádku.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Rozšířit značky
 Značky jsou způsobem, jak připojovat data k různým druhům textu. V mnoha případech jsou přidružená data zobrazena jako vizuální efekt, ale ne všechny značky mají vizuální prezentaci. Vlastní druh značky můžete definovat <xref:Microsoft.VisualStudio.Text.Tagging.ITag>implementací . Je také <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> nutné implementovat poskytnout značky pro danou sadu <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> rozsahů textu a poskytnout tagger. Zprostředkovatele taggeru je nutné exportovat společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "kód"), pro který je značka platná.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: druh značky.

  Následující příklad ukazuje atributy exportu u poskytovatele tagger.

\<CodeContentPlaceHolder></CodeContentPlaceHolder> 8 Vestavěné jsou následující druhy značek:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: spojené <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>s .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: spojené s typy chyb.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: spojené s ozdobou.

  > [!NOTE]
  > Příklad a naleznete <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>v definici HighlightWordTag v [návodu: Zvýraznění textu](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: spojené s oblastmi, které lze rozbalit nebo sbalit v osnově.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definuje prostor, který ozdoba zabírá v textovém zobrazení. Další informace o prostorvyjednávání vylepšení naleznete v následující části.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: Poskytuje automatické rozestupy a velikosti pro vylepšení.

  Chcete-li najít a použít značky <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> pro <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>vyrovnávací paměti a <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> zobrazení, importujte nebo , které poskytují požadovaný typ. Následující kód importuje tuto službu jako vlastnost.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Značky a definice markerů
 Třídu můžete <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> rozšířit a definovat vzhled značky. Třídu (jako <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>)musíte exportovat s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název použitý k odkazu na tento formát

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: To způsobí, že formát se zobrazí v ui

  V konstruktoru definujete zobrazovaný název a vzhled značky. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>definuje barvu výplně <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> a barvu ohraničení. Jedná <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> se o lokalizovatelný název definice formátu.

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

 Chcete-li použít tuto definici formátu na značku, naodkazujte název, který jste nastavili v atributu name třídy (nikoli zobrazovaný název).

> [!NOTE]
> Příklad a naleznete <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>v části Třída HighlightWordFormatDefinition v [návodu: Zvýraznění textu](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Rozšířit vylepšení
 Vylepšení definují vizuální efekty, které lze přidat buď do textu, který je zobrazen v textovém zobrazení, nebo do samotného zobrazení textu. Můžete definovat vlastní vylepšení jako libovolný <xref:System.Windows.UIElement>typ .

 Ve třídě ozdoby musíte deklarovat <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Chcete-li vrstvu vylepšení zaregistrovat, exportujte ji spolu s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název ozdoby.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: pořadí ozdoby s ohledem na jiné vrstvy ozdoby. Třída <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definuje čtyři výchozí vrstvy: Výběr, Osnova, Stříška a Text.

  Následující příklad ukazuje atributy exportu v definici vrstvy vylepšení.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Je nutné vytvořit druhou třídu, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> a zpracovává jeho <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> událost vytvořením instance vylepšení. Tuto třídu je nutné exportovat spolu s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "kód"), pro který je vylepšení platné.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: druh zobrazení textu, pro které je tato vylepšení platná. Třída <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> má sadu předdefinovaných rolí zobrazení textu. Používá se <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> například především pro zobrazení textu souborů. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>Používá se pro zobrazení textu, která může uživatel upravovat nebo procházet pomocí myši a klávesnice. Příklady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> zobrazení jsou textové zobrazení editoru a okno **Výstup.**

  Následující příklad ukazuje atributy exportu na zprostředkovatele vylepšení.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Mezera vyjednávání vylepšení je ten, který zabírá prostor na stejné úrovni jako text. Chcete-li vytvořit tento druh vylepšení, musíte definovat třídu značek, která dědí z <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, která definuje množství místa, které ozdoba zabírá.

 Stejně jako u všech vylepšení, musíte exportovat definici vrstvy vylepšení.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Chcete-li vytvořit instanci mezery vyjednávání vylepšení, musíte vytvořit <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>třídu, která implementuje , kromě třídy, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (stejně jako u jiných druhů vylepšení).

 Chcete-li zaregistrovat zprostředkovatele tagger, musíte jej exportovat společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "kód"), pro který je vaše vylepšení platné.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: druh zobrazení textu, pro které je tato značka nebo vylepšení platná. Třída <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> má sadu předdefinovaných rolí zobrazení textu. Používá se <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> například především pro zobrazení textu souborů. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>Používá se pro zobrazení textu, která může uživatel upravovat nebo procházet pomocí myši a klávesnice. Příklady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> zobrazení jsou textové zobrazení editoru a okno **Výstup.**

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: druh značky nebo ozdoby, které jste definovali. Je nutné přidat <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>sekundu pro .

  Následující příklad ukazuje atributy exportu na zprostředkovatele tagger pro značku vylepšení vyjednávání místa.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Rozšíření myších procesorů
 Můžete přidat speciální zpracování pro vstup myši. Vytvořte třídu, <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> která dědí z a přepsat události myši pro vstup, který chcete zpracovat. Musíte také <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> implementovat do druhé třídy <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> a exportovat spolu s, který určuje druh obsahu (například "text" nebo "kód"), pro které je platná obslužná rutina myši.

 Následující příklad ukazuje atributy exportu u zprostředkovatele procesoru myši.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Rozšířit obslužné rutiny přetažení
 Můžete přizpůsobit chování rutiny přetažení pro určité druhy textu vytvořením třídy, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> a druhé třídy, která implementuje k vytvoření obslužné rutiny <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> přetažení. Obslužnou rutinu přetažení je nutné exportovat společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: textový formát, pro který je tato obslužná rutina přetažení platná. Následující formáty jsou zpracovány v pořadí podle priority od nejvyšší po nejnižší:

  1. Libovolný vlastní formát

  2. Filedrop

  3. Rozšířený metasoubor

  4. Waveaudio

  5. Riff

  6. Dif

  7. Národní prostředí

  8. Palety

  9. PenData

  10. Serializovatelný

  11. Symbolický odkaz

  12. Xaml

  13. Balíček XamlPackage

  14. Tiff

  15. Bitmapové

  16. Dib

  17. MetafileObrázek

  18. CSV

  19. System.string

  20. Formát HTML

  21. Unicodetext

  22. OEMText

  23. Text

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název obslužné rutiny přetažení.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: řazení obslužné rutiny přetažení před nebo za výchozí obslužnou rutinou přetažení. Výchozí obslužná rutina přetažení pro visual studio má název "DefaultFileDropHandler".

  Následující příklad ukazuje atributy exportu u poskytovatele obslužné rutiny přetažení.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Rozšíření možností editoru
 Možnosti můžete definovat tak, aby byly platné pouze v určitém oboru, například v textovém zobrazení. Editor poskytuje tuto sadu předdefinovaných možností: možnosti editoru, možnosti zobrazení a možnosti zobrazení Windows Presentation Foundation (WPF). Tyto možnosti naleznete <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>v <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>, a .

 Chcete-li přidat novou možnost, odvodit třídu z jedné z těchto tříd definice možnosti:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Následující příklad ukazuje, jak exportovat definici možnosti, která má logickou hodnotu.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Rozšíření technologie IntelliSense
 Technologie IntelliSense je obecný termín pro skupinu funkcí, které poskytují informace o strukturovaném textu a dokončování výkazu. Mezi tyto funkce patří dokončování výpisu, nápověda k podpisu, rychlé informace a žárovky. Dokončování příkazů pomáhá uživatelům správně zadat klíčové slovo nebo název člena jazyka. Nápověda k podpisu zobrazuje podpis nebo podpisy metody, kterou uživatel právě zadal. Rychlé informace zobrazí úplný podpis pro typ nebo název člena, když na něm spočívá myš. Žárovka poskytuje další akce pro určité identifikátory v určitých kontextech, například přejmenování všech výskytů proměnné po přejmenování jednoho výskytu.

 Návrh funkce Technologie IntelliSense je ve všech případech téměř stejný:

- Za celkový proces je zodpovědný *zprostředkovatel* IntelliSense.

- *Relace* Technologie IntelliSense představuje posloupnost událostí mezi aktivací prezentujícího a vazbou nebo zrušením výběru. Relace je obvykle spuštěna některým uživatelským gestem.

- *Řadič* IntelliSense je zodpovědný za rozhodování o tom, kdy má relace začít a skončit. Rovněž rozhoduje o tom, kdy mají být informace potvrzeny a kdy má být relace zrušena.

- *Zdroj* Technologie IntelliSense poskytuje obsah a rozhoduje o nejlepší shodě.

- Za zobrazení obsahu je zodpovědný *prezentující* technologie IntelliSense.

  Ve většině případů doporučujeme zadat alespoň zdroj a řadič. Pokud chcete zobrazení přizpůsobit, můžete také zadat prezentujícího.

### <a name="implement-an-intellisense-source"></a>Implementace zdroje Technologie IntelliSense
 Chcete-li přizpůsobit zdroj, je nutné implementovat jedno (nebo více) z následujících zdrojových rozhraní:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>byl zastaralá ve prospěch <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.

 Kromě toho je nutné implementovat zprostředkovatele stejného druhu:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>byl zastaralá ve prospěch <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.

 Zprostředkovatele je nutné exportovat společně s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název zdroje.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "kód"), na který se zdroj vztahuje.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: pořadí, ve kterém by se měl zdroj objevit (s ohledem na jiné zdroje).

- Následující příklad ukazuje atributy exportu u zprostředkovatele zdroje dokončení.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Další informace o implementaci zdrojů Technologie IntelliSense naleznete v následujících návodech:

- [Návod: Zobrazení popisů rychlých informací](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Návod: Zobrazit nápovědu k podpisu](../extensibility/walkthrough-displaying-signature-help.md)

- [Návod: Zobrazení dokončení příkazu](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementace ovladače IntelliSense
 Chcete-li přizpůsobit řadič, <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> je nutné implementovat rozhraní. Kromě toho je nutné implementovat zprostředkovatele řadiče spolu s následujícími atributy:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: název regulátoru.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: druh obsahu (například "text" nebo "kód"), na který se správce vztahuje.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: pořadí, ve kterém by měl být regulátor uveden (s ohledem na ostatní regulátory).

  Následující příklad ukazuje atributy exportu na zprostředkovatele řadiče dokončení.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Další informace o používání ovladačů IntelliSense naleznete v následujících návodech:

- [Návod: Zobrazení popisů rychlých informací](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
