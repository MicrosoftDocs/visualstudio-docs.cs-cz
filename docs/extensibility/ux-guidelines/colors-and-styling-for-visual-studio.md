---
title: Barvy a styly pro Visual Studio | Microsoft Docs
description: Přečtěte si, jak prostředí Visual Studio pro uživatele používá barvu jako komunikační nástroj místo z čistě estetických důvodů.
ms.custom: SEO-VS-2020
ms.date: 07/31/2017
ms.topic: reference
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 307a4013c06258524c60619c6eff40e4d64740b6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904484"
---
# <a name="colors-and-styling-for-visual-studio"></a>Barvy a styly pro Visual Studio

## <a name="use-color-in-visual-studio"></a>Použití barev v aplikaci Visual Studio

V aplikaci Visual Studio se barva používá hlavně jako komunikační nástroj, nikoli jenom jako dekorace. Používejte barvy minimální a rezervujte ji v situacích, kde chcete:

- Význam nebo afilace komunikace (například modifikátory platformy nebo jazyka)

- Přilákat pozornost (například indikuje změnu stavu)

- Zlepšení čitelnosti a poskytování orientačních bodů pro navigaci v uživatelském rozhraní

- Zvýšení účelnosti

Pro přiřazení barev k prvkům uživatelského rozhraní v aplikaci Visual Studio existuje několik možností. Někdy může být obtížné zjistit, kterou možnost byste měli použít, nebo jak ji používat správně. Toto téma vám pomůže:

- Porozumění různým službám a systémům, které se používají k definování barev v aplikaci Visual Studio.

- Vyberte pro daný prvek správnou možnost.

- Správně použijte možnost, kterou jste zvolili.

> [!NOTE]
> Nikdy nekódujte pevně hexadecimální, RGB nebo systémové barvy k prvkům uživatelského rozhraní. Používání služeb umožňuje flexibilitu při optimalizaci odstínu. Kromě toho bez služby nebude možné využívat možnosti přepínání motivů [služby VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Metody pro přiřazení barev k prvkům rozhraní sady Visual Studio

Vyberte metodu, která nejlépe vyhovuje vašim prvkům uživatelského rozhraní.

| Vaše uživatelské rozhraní | Metoda | Jaké argumenty to jsou? |
| --- | --- | --- |
| Máte vložená nebo samostatná dialogová okna. | **Systémové barvy** | Názvy systémů, které umožňují operačnímu systému definovat barvu a vzhled prvků uživatelského rozhraní, jako jsou běžné ovládací prvky dialogu. |
| Máte vlastní uživatelské rozhraní, které chcete mít v souladu s celkovým prostředím VS a máte prvky uživatelského rozhraní, které odpovídají kategorii a sémantickému významu sdílených tokenů. | **Společné sdílené barvy** | Existující předdefinované názvy barevných tokenů pro konkrétní prvky uživatelského rozhraní |
| Máte individuální funkci nebo skupinu funkcí a neexistuje žádná sdílená barva pro podobné prvky. | **Vlastní barvy** | Názvy tokenů barev, které jsou specifické pro oblast a nejsou určeny pro sdílení s jiným uživatelským rozhraním |
| Chcete koncovému uživateli dovolit přizpůsobit uživatelské rozhraní nebo obsah (například pro textové editory nebo specializované okna návrháře). | **Přizpůsobení koncovým uživatelům**<br /><br />**(Nástroje &gt; Dialogové okno Možnosti)** | Nastavení definovaná na stránce písma a barvy dialogového okna **&gt; Možnosti nástrojů** nebo na speciální stránku specifickou pro jednu funkci uživatelského rozhraní. |

### <a name="visual-studio-themes"></a>Motivy sady Visual Studio

Sada Visual Studio nabízí tři různé barevné motivy: světlá, tmavá a modrá. Také detekuje režim Vysoký kontrast, což je barevný motiv v rámci systému navržený pro usnadnění přístupu.

Uživatelé jsou při prvním použití aplikace Visual Studio vyzváni k výběru motivu a je možné přepínat motivy později tak, že přejdete do části **&gt; možnosti &gt; prostředí &gt; Obecné** a zvolíte nový motiv z rozevírací nabídky "barevný motiv".

Uživatelé také mohou použít ovládací panely k přepínání celého systému do jednoho z několika Vysoký kontrast motivů. Pokud uživatel vybere motiv Vysoký kontrast, pak selektor barevných motivů sady Visual Studio již nemá vliv na barvy v aplikaci Visual Studio, i když uživatel ukončí Vysoký kontrast režim, budou uloženy všechny změny motivů. Další informace o režimu Vysoký kontrast najdete v tématu [výběr vysoký kontrast barev](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Služba VSColor

Visual Studio poskytuje službu barev prostředí, která se označuje jako služba VSColor, která umožňuje navazovat hodnoty barev vašich prvků uživatelského rozhraní na pojmenovanou položku, která obsahuje hodnoty barev pro každý motiv sady Visual Studio. Tím se zajistí, že se barvy automaticky změní tak, aby odrážely aktuální motiv vybraný uživatelem nebo režim systému Vysoký kontrast. Používání služby znamená, že implementace všech změn barev souvisejících s motivem se zpracovává na jednom místě a pokud používáte společné sdílené barvy ze služby, vaše uživatelské rozhraní automaticky odmítne nové motivy v budoucích verzích sady Visual Studio.

### <a name="implementation"></a>Implementace

Zdrojový kód sady Visual Studio zahrnuje několik definičních souborů balíčku, které obsahují seznam názvů tokenů a příslušné hodnoty barvy pro každý motiv. Služba Color přečte VSColors definované v těchto definičních souborech balíčku. Tyto barvy jsou odkazovány v kódu XAML nebo v kódu a poté načteny buď pomocí `IVsUIShell5.GetThemedColor` metody, nebo pomocí mapování DynamicResource.

### <a name="system-colors"></a>Systémové barvy

Běžné ovládací prvky odkazují na barvy systému ve výchozím nastavení. Pokud chcete, aby uživatelské rozhraní používalo systémové barvy, například při vytváření vloženého nebo samostatného dialogu, nemusíte nic dělat.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Společné sdílené barvy ve službě VSColor

Prvky rozhraní by měly odrážet celé prostředí sady Visual Studio. Tím, že znovu použijete společné sdílené barvy, které jsou vhodné pro komponentu uživatelského rozhraní, kterou navrhujete, zajistíte, že vaše rozhraní je konzistentní s jinými rozhraními sady Visual Studio a že se barvy automaticky aktualizují při přidání nebo aktualizaci motivů.

Než začnete používat běžné sdílené barvy, ujistěte se, že rozumíte jejich správnému používání. Nesprávné použití běžných sdílených barev může mít za následek nekonzistentní, frustrující nebo matoucí prostředí pro vaše uživatele.

### <a name="user-customizable-colors"></a>Uživatelsky přizpůsobitelné barvy

Viz: vystavení [barev koncovým uživatelům](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

V některých případech budete chtít, aby koncový uživatel mohl přizpůsobit uživatelské rozhraní, například když vytváříte Editor kódu nebo návrhovou plochu. Přizpůsobitelné komponenty uživatelského rozhraní jsou k dispozici v části **písma a barvy** dialogového okna **&gt; Možnosti nástrojů** , kde se mohou uživatelé rozhodnout změnit barvu popředí, barvu pozadí nebo obojí.

![&gt;Dialogové okno Možnosti nástrojů](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 – a_ToolsOptionsDialog")<br />&gt;Dialogové okno Možnosti nástrojů

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a> Služba VSColor

Visual Studio poskytuje službu barev prostředí, která se také označuje jako služba VSColor nebo služba barev prostředí. Tato služba umožňuje navazovat hodnoty barev vašich prvků uživatelského rozhraní na sadu barev název-hodnota obsahující barvy pro každý motiv. Služba VSColor se musí použít pro všechny prvky uživatelského rozhraní, aby se barvy automaticky změnily tak, aby odrážely aktuální motiv vybraný uživatelem, a takže uživatelské rozhraní vázané na službu Color Service prostředí bude v budoucích verzích sady Visual Studio integrováno s novými motivy.

### <a name="how-the-service-works"></a>Jak služba funguje

Služba barvy prostředí čte VSColors definované v pkgdef pro komponentu uživatelského rozhraní. Tyto VSColors jsou následně odkazovány v kódu XAML nebo kódu a jsou načteny buď pomocí `IVsUIShell5.GetThemedColor` mapování, nebo `DynamicResource` .

![Architektura služby Color Service prostředí](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 – a_EnvironmentColorServiceArchitecture")<br />Architektura služby Color Service prostředí

### <a name="accessing-the-service"></a>Přístup ke službě

Existuje několik různých způsobů, jak získat přístup ke službě VSColor, v závislosti na druhu barevných tokenů, které používáte, a na tom, jaký typ kódu máte.

#### <a name="predefined-environment-colors"></a>Předdefinované barvy prostředí

##### <a name="from-native-code"></a>Z nativního kódu

Prostředí poskytuje službu, která poskytuje přístup k `COLORREF` barvám. Služba/rozhraní:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

V souboru VSShell80. idl `__VSSYSCOLOREX` má výčet konstanty barvy prostředí. Pokud ho chcete použít, předejte jako hodnotu indexu jednu z hodnot `enum __VSSYSCOLOREX` popsaných na webu MSDN nebo běžné číslo indexu, které rozhraní API systému Windows `GetSysColor` podporuje. Tím se vrátí hodnota RGB barvy, která by se měla použít ve druhém parametru.

Pokud uložíte pero nebo štětec s novou barvou, je nutné `AdviseBroadcastMessages` (z prostředí sady Visual Studio) a naslouchat `WM_SYSCOLORCHANGE` `WM_THEMECHANGED` zprávám.

Chcete-li získat přístup ke službě Color Service v nativním kódu, proveďte volání, které se podobá této:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> `COLORREF`Hodnoty vrácené funkcí `GetVSSysColorEx()` obsahují pouze součásti R, G, B barvy motivu. Pokud položka motivu používá transparentnost, před vrácením se hodnota alfa kanálu zahodí. Proto pokud je potřeba použít barvu prostředí zájmu na místo, kde je kanál transparentnosti důležitý, měli byste použít `IVsUIShell5.GetThemedColor` místo `IVsUIShell2::GetVSSysColorEx` , jak je popsáno dále v tomto tématu.

##### <a name="from-managed-code"></a>Ze spravovaného kódu

Přístup ke službě VSColor prostřednictvím nativního kódu je poměrně jasné. Pokud ale pracujete prostřednictvím spravovaného kódu, ale určíte, jak používat službu, může být obtížné. V takovém případě je zde uveden fragment kódu jazyka C#, který demonstruje tento proces:

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell2.GetVSSysColorEx((int)__VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Pokud pracujete v Visual Basic, použijte:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Z uživatelského rozhraní WPF

Můžete navazovat barvy sady Visual Studio prostřednictvím hodnot exportovaných do aplikace `ResourceDictionary` . Níže je uveden příklad používání prostředků z tabulky barev a vazba na data písma prostředí v jazyce XAML.

```xml
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Pomocné třídy a metody pro spravovaný kód

Pro spravovaný kód obsahuje Knihovna architektury spravovaného balíčku () tohoto prostředí `Microsoft.VisualStudio.Shell.12.0.dll` několik pomocných tříd, které usnadňují použití barev motivů.

Pomocné metody ve `Microsoft.VisualStudio.Shell.VsColors` třídě v metodě MPF obsahují `GetThemedGDIColor()` a `GetThemedWPFColor()` . Tyto pomocné metody vrátí hodnotu barvy položky motivu jako nebo , která `System.Drawing.Color` `System.Windows.Media.Color` se použije v uživatelském rozhraní WinForms nebo WPF.

```csharp
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}
```

Třídu lze také použít k získání identifikátorů VSCOLOR pro daný klíč prostředku barvy WPF nebo naopak.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Metody třídy dotazování služby VSColor, aby při každém vyvolání vrátily `VsColors` hodnotu barvy. Pokud chcete získat hodnotu barvy jako , je alternativou s lepším výkonem místo toho použít metody třídy , která ukládá hodnoty barev získané ze služby `System.Drawing.Color` `Microsoft.VisualStudio.PlatformUI.VSThemeColor` VSColor do mezipaměti. Třída se interně přihlásí k odběru událostí zpráv všesměrového vysílání prostředí a při změně události motivu zahodí hodnotu v mezipaměti. Třída také poskytuje . Událost vhodná pro NET, která se přihlásí k odběru změn motivu. Pomocí `ThemeChanged` události přidejte novou obslužnou rutinu a pomocí metody získejte hodnoty barev, které `GetThemedColor()` `ThemeResourceKeys` vás zajímají. Vzorový kód by mohl vypadat takhle:

```csharp
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a> Výběr Vysoký kontrast barev

### <a name="overview"></a>Přehled

Windows používá několik motivů na úrovni systému s vysokým kontrastem, které zvyšují barevný kontrast textu, pozadí a obrázků, takže prvky se na obrazovce zobrazují odlišnějším způsobem. Z důvodů přístupnosti je důležité, aby Visual Studio rozhraní správně reagovaly, když uživatelé přepněte na Vysoký kontrast motiv.

Pro různé motivy lze použít pouze Vysoký kontrast barev. Při výběru názvů systémových barev mějte na paměti následující tipy:

- **Zvolte systémové barvy, které mají stejný sémantický význam** jako element, který barvením chcete. Pokud například vybíráte barvu vysokého kontrastu pro text v okně, použijte WindowText a ne ControlText.

- **Zvolte páry popředí a pozadí** dohromady nebo si nejste jistí, že vaše volba barvy bude fungovat ve všech Vysoký kontrast motivech.

- **Určete, které části uživatelského rozhraní jsou** nejdůležitější, a ujistěte se, že oblasti obsahu budou odnikud. Přijdete o spoustu podrobností, které by drobné rozdíly v barevném odstínu normálně rozlišují, takže použití silných barev ohraničení je běžné při definování oblastí obsahu, protože neexistují žádné barevné varianty pro různé oblasti obsahu.

### <a name="system-color-set"></a>Sada barev systému

Tabulka na [blogu WPF Team Blog: SystemColors Reference](/archive/blogs/wpf/systemcolors-reference) označuje úplnou sadu názvů systémových barev a odpovídající odstíny zobrazené v každém motivu.

Při použití této omezené sady barev v uživatelském rozhraní se očekává, že ztratíte drobné detaily, které byly přítomny *v "normálních" motivech*. Tady je příklad uživatelského rozhraní s drobnými šedými barvami, které slouží k rozlišení oblastí v okně nástroje. Při spárování se stejným oknem zobrazeným v režimu Vysoký kontrast můžete vidět, že všechna pozadí jsou stejná a ohraničení těchto oblastí jsou označena pouze ohraničením:

![Příklad ztráty drobných podrobností v Vysoký kontrast](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 – a_PropertiesWindow")<br />Příklad ztráty drobných podrobností v Vysoký kontrast

#### <a name="choosing-text-colors-in-an-editor"></a>Volba barev textu v editoru

Barevný text se používá v editoru nebo na návrhové ploše k označení významu, jako je například umožnění snadné identifikace skupin podobných položek. V Vysoký kontrast motivu ale nemáte možnost rozlišovat mezi více než třemi barvami textu. WindowText, GrayText a HotTrackText jsou jediné barvy, které jsou k dispozici na površích WindowBackground. Vzhledem k tomu, že nemůžete použít více než tři barvy, pečlivě zvolte nejdůležitější rozdíly, které chcete zobrazit v Vysoký kontrast režimu.

Hues pro každý z názvů tokenů povolených na ploše editoru, jak se zobrazují v každém Vysoký kontrast motivu:

![Vysoký kontrast editoru](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 – b_HCEditorComparison")<br />Vysoký kontrast editoru

Příklady plochy editoru v modrém motivu:

![Editor v modrém motivu](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 – c_EditorBlue")<br />Editor v modrém motivu

![Editor v Vysoký kontrast #1 motivu](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 – d_EditorHC1")<br />Editor v Vysoký kontrast #1 motivu

### <a name="usage-patterns"></a>Vzory využití

Mnoho běžných prvků uživatelského rozhraní již Vysoký kontrast definované barvy. Na tyto vzory použití můžete odkazovat při výběru vlastních názvů barev systému, aby prvky uživatelského rozhraní byly konzistentní s podobnými komponentami.

| Barva systému | Využití |
| --- | --- |
| ActiveCaption (Aktivnícaption) | – Aktivní integrované vývojové prostředí (IDE) a piktogramy tlačítek s aktivovaným oknem při najetí myší a stisknutí klávesy<br />– Pozadí záhlaví integrovaného vývojového prostředí a oken<br />– Pozadí výchozího stavového řádku |
| ActiveCaptionText | – Aktivní integrované vývojové prostředí (IDE) a předsudky pro záhlaví popředí (text a piktogramy)<br />– Pozadí a ohraničení tlačítek aktivních oken při najetí myší a stisknutí |
| Řízení | – Pole se seznamem, rozevírací seznam a výchozí a zakázané pozadí ovládacího prvku vyhledávání, včetně tlačítka rozevíracího seznamu<br />– Dock target button background (Ukotvit pozadí cílového tlačítka)<br />– Pozadí panelu příkazů<br />– Pozadí okna nástroje |
| Ovládací prvek ControlDark | – Pozadí integrovaného vývojového prostředí (IDE)<br />– Oddělovače nabídek a panelů příkazů<br />– Ohraničení panelu příkazů<br />– Stíny nabídek<br />– Výchozí karta panelu nástrojů a najetí myší na ohraničení a oddělovač<br />– Pozadí tlačítka pro dobře přetečené dokumenty<br />– Ukotvení ohraničení cílového piktogramu |
| ControlDarkDark |– Okno karty Vybraný dokument bez výběru |
| Ovládací prvek |– Automaticky skrýt ohraničení karty<br />– Pole se seznamem a ohraničení rozevíracího seznamu<br />– Ukotvení pozadí a ohraničení cíle |
| Ovládací prvekLightLight | - Vybraná, cílená ohraničení |
| Text ovládacího prvku | – Pole se seznamem a piktogram rozevíracího seznamu<br />– Text karty s nevybraným oknem nástroje |
| GrayText |– Pole se seznamem a rozevírací seznam zakázaly ohraničení, rozevírací seznam piktogramů, text a text položky nabídky<br />– Text nabídky Zakázáno<br />– Text záhlaví vyhledávacího ovládacího prvku možnosti hledání<br />– Oddělovač oddílu ovládacího prvku vyhledávání |
| Zvýraznit | – Všechna pozadí a ohraničení při najetí myší a stisknutí, kromě ohraničení tlačítka rozevíracího seznamu s rozevíracím seznamem a pozadí tlačítka s přetečemi dokumentů<br />– Pozadí vybraných položek |
| ZvýraznitText | – Všechna najetí myší a stisknutí popředí (text a piktogramy)<br />– Zacílné okno nástroje a ovládací prvek okna karty dokumentu na popředí<br />– Ohraničení záhlaví v zacílovém okně nástroje<br />– Zacíliní, vybraná tabulátorová karta popředí<br />– Ohraničení tlačítka pro přetečení dokumentu při najetí myší a stisknutí<br />– Ohraničení vybrané ikony|
| Sledování na okruhu (HotTrack) | – Posouvání pozadí jezdce a ohraničení při stisknutí<br />– Piktogram šipky posuvníku při stisknutí |
| InactiveCaption | – Neaktivní integrované vývojové prostředí (IDE) a piktogramy tlačítek s neaktivním oknem při najetí myší<br />– Pozadí záhlaví integrovaného vývojového prostředí a oken<br />– Zakázané pozadí ovládacího prvku vyhledávání |
| InactiveCaptionText | – Neaktivní integrované vývojové prostředí (IDE) a neaktivní záhlaví oken v popředí (text a piktogramy)<br />– Neaktivní tlačítka oken – pozadí a ohraničení při najetí myší<br />– Pozadí a ohraničení tlačítka s nezaostřením panelu nástrojů<br />– Zakázaný ovládací prvek hledání na popředí |
| Nabídka | – Pozadí rozevírací nabídky<br />- Zaškrtnuté a zakázané pozadí zaškrtnutí |
| Text nabídky | – Ohraničení rozevírací nabídky<br />– Značky zaškrtnutí<br />– Piktogramy nabídky<br />– Text rozevírací nabídky<br />– Ohraničení vybrané ikony |
| Posuvník | – Posuvník a pozadí se šipkou posuvníku, všechny stavy |
| Okno | – Automaticky skrýt pozadí karty<br />– Řádek nabídek a pozadí pro polici příkazů<br />– Pozadí a ohraničení karty okna dokumentu bez výběru nebo bez výběru, a to pro otevřené i základní karty<br />– Pozadí záhlaví okna nástroje bez zaostření<br />– Pozadí karty panelu nástrojů, vybrané i nevybrané |
| WindowFrame | – Ohraničení integrovaného vývojového prostředí (IDE) |
| Text okna | – Automatické skrytí popředí karty<br />- Vybraná karta panelu nástrojů v popředí<br />– Karta s oknem dokumentu bez výběru a nezaostřená nebo nevybraná tabulátor pro popředí<br />– Výchozí stromové zobrazení popředí a najetí myší na nevybrané piktogramy<br />– Ohraničení karty vybraného panelu nástrojů<br />– Pozadí, ohraničení a piktogram posuvníku |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> Vystavení barev koncovým uživatelům

### <a name="overview"></a>Přehled

Někdy budete chtít koncovému uživateli povolit přizpůsobení uživatelského rozhraní, například při vytváření editoru kódu nebo návrhové plochy. Nejběžnější způsob, jak to provést, je pomocí **dialogového &gt; okna Možnosti** nástrojů. Pokud nemáte vysoce specializované uživatelské rozhraní, které vyžaduje speciální ovládací prvky, nejjednodušší způsob,  jak přizpůsobení prezentovat, je prostřednictvím stránky Písma a **barvy** v části Prostředí dialogového okna. Pro každý prvek, který zpřístupníte pro přizpůsobení, může uživatel změnit barvu popředí, barvu pozadí nebo obojí.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Sestavení balíčku VSPackage pro přizpůsobitelné barvy

Balíček VSPackage může řídit písma a barvy prostřednictvím vlastních kategorií a zobrazovat položky na stránce vlastností Písma a barvy. Při použití tohoto mechanismu musí balíčky VSPackage implementovat rozhraní [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) a jeho přidružená rozhraní.

Tento mechanismus lze v zásadě použít k úpravě všech existujících položek zobrazení a kategorií, které je obsahují. Neměl by se ale používat k úpravě kategorie textového editoru ani jeho zobrazované položky. Další informace o kategorii Textový editor najdete v tématu [Přehled písem a barev.](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015)

Pokud chcete implementovat vlastní kategorie nebo zobrazit položky, musí balíček VSPackage:

- **Vytvořte nebo identifikujte kategorie v registru.** Implementace rozhraní IDE stránky vlastností Písma a **barvy** používá tyto informace ke správnému dotazu na službu podporující danou kategorii.

- **Vytvořte nebo identifikujte skupiny v registru (volitelné).** Může být užitečné definovat skupinu, která představuje sjednocené dvě nebo více kategorií. Pokud je definovaná skupina, integrované vývojové prostředí (IDE) automaticky sloučí podkategorie a distribuuje zobrazované položky v rámci skupiny.

- **Implementace podpory integrovaného vývojového prostředí (IDE).**

- **Zpracování změn písma a barev**

#### <a name="to-create-or-identify-categories"></a>Vytvoření nebo identifikace kategorií

Vytvořte speciální typ položky registru kategorie v části `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` kde `<Category>` je nelokalizovaný název kategorie.

Naplňte registr dvěma hodnotami:

| Název | Typ | Data | Description |
| --- | --- | --- | --- |
| Kategorie | REG_SZ | Identifikátor GUID | Identifikátor GUID vytvořený k identifikaci kategorie |
| Balíček | REG_SZ | Identifikátor GUID | Identifikátor GUID služby VSPackage, která podporuje kategorii |

 Služba zadaná v registru musí poskytovat implementaci [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) pro odpovídající kategorii.

#### <a name="to-create-or-identify-groups"></a>Vytvoření nebo identifikace skupin

Vytvořte speciální typ položky registru kategorie v části `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` kde `<group>` je nelokalizovaný název skupiny.

Naplňte registr dvěma hodnotami:

| Název | Typ | Data | Description |
|--- | --- | --- | --- |
| Kategorie | REG_SZ | Identifikátor GUID | Identifikátor GUID vytvořený k identifikaci kategorie |
| Balíček | REG_SZ | Identifikátor GUID | Identifikátor GUID služby VSPackage, která podporuje kategorii |

Služba zadaná v registru musí poskytovat implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> pro odpovídající skupinu.

![Implementace IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 – a_FontAndColorGroup")<br />Implementace `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Implementace podpory integrovaného vývojového prostředí

Implementujte [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), který vrátí rozhraní [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) nebo rozhraní integrovaného vývojového prostředí (IDE) pro každou zadanou kategorii <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> nebo identifikátor GUID skupiny.

Pro každou kategorii, která podporuje, implementuje balíček VSPackage samostatnou instanci rozhraní [IVsFontAndColorDefaults.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)

Metody implementované prostřednictvím [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) musí poskytnout integrované vývojové prostředí s:

- Seznamy zobrazované položky v kategorii

- Lokalizovatelné názvy pro zobrazované položky

- Zobrazení informací pro každého člena kategorie

> [!NOTE]
> Každá kategorie musí obsahovat alespoň jednu zobrazované položky.

Integrované vývojové prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> (IDE) používá rozhraní k definování sjednoceného několika kategorií.

Jeho implementace poskytuje integrované vývojové prostředí (IDE) s těmito funkcemi:

- Seznam kategorií, které tvoří danou skupinu

- Přístup k instancím [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) podporující každou kategorii v rámci skupiny

- Názvy lokalizovatelných skupin

#### <a name="updating-the-ide"></a>Aktualizace integrovaného vývojového prostředí (IDE)

Integrované vývojové prostředí (IDE) ukládá informace o nastavení písma a barvy do mezipaměti. Proto je po jakékoli úpravě konfigurace písma a barvy integrovaného vývojového prostředí osvědčeným postupem zajistit, aby mezipaměť byla aktuální.

Aktualizace mezipaměti se provádí prostřednictvím rozhraní [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) a je možné ji provést globálně nebo pouze u vybraných položek.

### <a name="handling-font-and-color-changes"></a>Zpracování změn písma a barev

Aby služba zabarvení podporující balíček VSPackage správně podporovala zabarvení textu, musí reagovat na uživatelem iniciované změny provedené na stránce vlastností Písma a Barvy.

K tomu je potřeba VSPackage:

- **zpracujte události generované** rozhraním IDE implementací rozhraní [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) . Rozhraní IDE volá příslušnou metodu podle uživatelských úprav stránky písma a barvy. Například volá metodu [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) , pokud je vybráno nové písmo.

  **OR**

- **cyklické dotazování na rozhraní IDE o změny**. To lze provést prostřednictvím rozhraní [Chyba metody IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) implementovaného systémem. I když primárně pro podporu trvalosti, metoda [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) může získat informace o písmech a barvách pro zobrazení položek. Další informace o nastavení písma a barev najdete v článku na webu MSDN, který [přistupuje k uloženým písmům a nastavením barev](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-stored-font-and-color-settings?preserve-view=true&view=vs-2015).

> [!NOTE]
> Aby bylo zajištěno, že jsou výsledky cyklického dotazování správné, pomocí rozhraní [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) určete, zda je před voláním metod načtení z rozhraní [Chyba metody IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) nutné vyprázdnit mezipaměť a aktualizovat.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrace vlastní kategorie písma a barev bez implementace rozhraní

Následující příklad kódu ukazuje, jak zaregistrovat vlastní písmo a kategorii barev bez implementace rozhraní:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Pro tento příklad kódu:

- `"NameID"` = ID prostředku lokalizovaného názvu kategorie v balíčku
- `"ToolWindowPackage"` = GUID balíčku
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` je pouze příklad a skutečná hodnota může být nový identifikátor GUID poskytnutý implementací.

### <a name="set-the-font-and-color-property-category-guid"></a>Nastavení písma a vlastností barev – GUID kategorie

Následující příklad kódu ukazuje nastavení identifikátorů GUID kategorií.

```csharp
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
IVsTextEditorPropertyContainer spPropContainer;
Guid GUID_EditPropCategory_View_MasterSettings =
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
hr = spPropCatContainer.GetPropertyCategory(
ref GUID_EditPropCategory_View_MasterSettings,
out spPropContainer);
if(hr == 0)
{
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,
catGUID);
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,
catGUID);
}
}
```
