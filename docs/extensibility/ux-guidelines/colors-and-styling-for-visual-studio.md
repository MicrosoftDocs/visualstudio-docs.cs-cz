---
title: Barvy a styly pro Visual Studio | Microsoft Docs
description: Přečtěte si, jak prostředí Visual Studio pro uživatele používá barvu jako komunikační nástroj místo z čistě estetických důvodů.
ms.custom: SEO-VS-2020
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc98e3c2717b14ac1933e5b41269af1efb8e932f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089911"
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

Pomocné metody ve `Microsoft.VisualStudio.Shell.VsColors` třídě v metodě MPF obsahují `GetThemedGDIColor()` a `GetThemedWPFColor()` . Tyto pomocné metody vracejí hodnotu barvy záznamu motivu jako `System.Drawing.Color` nebo `System.Windows.Media.Color` , aby bylo možné je použít v uživatelském rozhraní WINFORMS nebo WPF.

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

Třídu lze také použít k získání VSCOLOR identifikátorů pro daný klíč prostředku barvy WPF nebo naopak.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Metody `VsColors` třídy dotazování na službu VSColor, aby vracely hodnotu barvy pokaždé, když jsou vyvolány. Chcete-li získat hodnotu barvy jako `System.Drawing.Color` , alternativa s vyšším výkonem je místo toho použít metody `Microsoft.VisualStudio.PlatformUI.VSThemeColor` třídy, která ukládá do mezipaměti hodnoty barvy získané ze služby VSColor. Třída se přihlašuje interně k událostem zprávy všesměrového vysílání prostředí a zahodí hodnotu uloženou v mezipaměti, když dojde k události měnící se motiv. Třída také poskytuje. Síťová událost, která se přihlásí k odběru změn motivů. Použijte `ThemeChanged` událost pro přidání nové obslužné rutiny a použijte `GetThemedColor()` metodu k získání hodnot barvy pro `ThemeResourceKeys` důležité. Vzorový kód by mohl vypadat takto:

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a> Volba Vysoký kontrastch barev

### <a name="overview"></a>Přehled

Systém Windows používá několik vysoce kontrastních motivů na úrovni systému, které zvyšují barevný kontrast textu, pozadí a obrázků, což usnadňuje zobrazení prvků na obrazovce. Z důvodu přístupnosti je důležité, aby prvky rozhraní sady Visual Studio správně reagovaly, když uživatelé přepínají na motiv Vysoký kontrast.

Pro Vysoký kontrast motivy lze použít pouze několik systémových barev. Při volbě názvů systémových barev si pamatujte následující tipy:

- **Vyberte systémové barvy, které mají stejný sémantický význam** jako prvek, který barevně vybarvit. Například pokud zvolíte barvu s vysokým kontrastem pro text v rámci okna, použijte WindowText a ne ControlText.

- **Zvolte páry na popředí** nebo na pozadí společně nebo nebudete mít jistotu, že volba barvy bude fungovat ve všech motivech vysoký kontrast.

- **Určete, které části uživatelského rozhraní jsou nejdůležitější a ujistěte se, že oblasti obsahu budou vystupovat.** Dojde ke ztrátě velkého množství podrobností, které malé rozdíly v barevných odstínech obvykle odlišují, takže použití silné barvy ohraničení je běžné pro definování oblastí obsahu, protože pro různé oblasti obsahu nejsou k dispozici žádné barevné varianty.

### <a name="system-color-set"></a>Systémová sada barev

Tabulka na [blogu týmu WPF: SystemColors reference](/archive/blogs/wpf/systemcolors-reference) označuje úplnou sadu systémových názvů barev a odpovídající odstíny zobrazené v jednotlivých motivech.

Při použití této omezené sady barev na vaše uživatelské rozhraní *se očekává, že přijdete o jemný detail, který se nachází v "normálním" motivu*. Tady je příklad uživatelského rozhraní s drobnými šedými barvami, které se používají k odlišení oblastí v rámci okna nástroje. Když se spáruje se stejným oknem, které se zobrazuje v režimu Vysoký kontrast, vidíte, že všechna pozadí mají stejný odstín a ohraničení těchto oblastí jsou označená pouze ohraničením:

![Příklad toho, jak se v Vysoký kontrast ztratí informace o jemných podrobnostech](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 – a_PropertiesWindow")<br />Příklad toho, jak se v Vysoký kontrast ztratí informace o jemných podrobnostech

#### <a name="choosing-text-colors-in-an-editor"></a>Volba barev textu v editoru

Barevný text se používá v editoru nebo na návrhové ploše k označení významu, jako je například umožnění snadné identifikace skupin podobných položek. V Vysoký kontrastovém motivu však nemůžete odlišit více než tři barvy textu. WindowText, GrayText a HotTrackText jsou jediné barvy, které jsou k dispozici na WindowBackground površích. Vzhledem k tomu, že nemůžete použít více než tři barvy, pečlivě vyberte nejdůležitější rozdíly, které chcete zobrazit v režimu Vysoký kontrast.

Odstíny pro každý název tokenu povolený na povrchu editoru, jak se zobrazuje v jednotlivých motivech Vysoký kontrast:

![Porovnání editoru Vysoký kontrast](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 – b_HCEditorComparison")<br />Porovnání editoru Vysoký kontrast

Příklady plochy editoru v modrém motivu:

![Editor v modrém motivu](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 – c_EditorBlue")<br />Editor v modrém motivu

![Editor v Vysoký kontrast #1 motiv](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 – d_EditorHC1")<br />Editor v Vysoký kontrast #1 motiv

### <a name="usage-patterns"></a>Vzory využití

Mnoho běžných prvků uživatelského rozhraní už má definované Vysoký kontrasté barvy. Na tyto vzory použití můžete odkazovat při volbě názvů systémových barev, aby byly prvky uživatelského rozhraní konzistentní s podobnými součástmi.

| Systémová barva | Využití |
| --- | --- |
| ActiveCaption | – Aktivní prostředí IDE a na tlačítku pro tlačítko, které se zobrazí při najetí myší a stisknutí klávesy<br />– Pozadí záhlaví pro prostředí IDE a pro vory v systému Windows<br />– Výchozí pozadí stavového řádku |
| ActiveCaptionText | – Aktivní integrované vývojové prostředí (text a glyfy), které se zobrazuje v oknech záhlaví<br />– Pozadí a ohraničení aktivních tlačítek oken při přechodu myší a stisknutí klávesy |
| Řízení | – Pole se seznamem, rozevírací seznam a ovládací prvek hledání výchozí a zakázané pozadí, včetně tlačítka rozevíracího seznamu<br />– Pozadí ukotvení cílového tlačítka<br />– Pozadí panelu příkazů<br />– Panel nástrojů – pozadí |
| ControlDark | – IDE na pozadí<br />– Oddělovače panelu příkazů a nabídek<br />– Ohraničení panelu příkazů<br />– Stíny nabídky<br />-Panel nástrojů – výchozí nastavení a ohraničení a oddělovač najetí myší<br />– Pozadí tlačítka pro přetečení dokumentu<br />– Ohraničení glyfu cíle ukotvení |
| ControlDarkDark |– Bez fokusu, vybrané okno karty dokumentu |
| ControlLight |-Automaticky skrývat ohraničení tabulátoru<br />– Pole se seznamem a ohraničení rozevíracího seznamu<br />– Ukotvit cílové pozadí a ohraničení |
| ControlLightLight | -Selected, cílené dočasné ohraničení |
| ControlText | – Pole se seznamem a piktogram rozevíracího seznamu<br />-Panel nástrojů – nevybraný text karty |
| GrayText |– Pole se seznamem a rozevírací seznam – zakázané ohraničení, rozevírací glyf, text a text položky nabídky<br />-Text nabídky disabled<br />-Search – text v záhlaví možností vyhledávání<br />-Oddělovač oddílu ovládacího prvku hledání |
| Zvýraznit | – Všechny najetí myší a nahrané pozadí a ohraničení, s výjimkou pozadí rozevíracího seznamu pole se seznamem a ohraničení tlačítka pro přetečení dokumentu<br />– Pozadí vybraných položek |
| HighlightText | – Všechny najetí myší a stisknutí popředí (text a glyfy)<br />– Okno nástrojů s fokusem a okno s kartami dokumentu – popředí<br />– Ohraničení pruhového okna nástroje s fokusem<br />– Zaměření, vybrané dočasné popředí karty<br />– Ohraničení tlačítka pro přetečení dokumentu při najetí myší a stisknutí klávesy<br />– Ohraničení vybrané ikony|
| HotTrack | – Procházení posuvníku pozadí a ohraničení při stisknutí<br />– Glyf šipky posuvníku při stisknutí |
| InactiveCaption | – Neaktivní piktogramy a glyfy tlačítek oken při najetí myší<br />– Pozadí záhlaví pro prostředí IDE a pro vory v systému Windows<br />– Zakázané pozadí ovládacího prvku hledání |
| InactiveCaptionText | -Neaktivní integrované vývojové prostředí (IDE) a na popředí záhlaví oken (text a glyfy)<br />– Neaktivní tlačítka okna na pozadí a ohraničení při najetí myší<br />– Pozadí a ohraničení tlačítka panelu nástrojů bez fokusu<br />– Zakázané popředí ovládacího prvku hledání |
| Nabídka | – Rozevírací nabídka – pozadí<br />-Pozadí zaškrtnuté a zakázané zaškrtnutí |
| MenuText | – Ohraničení rozevírací nabídky<br />– Zaškrtnutí značek<br />– Glyfy nabídek<br />– Text rozevírací nabídky<br />– Ohraničení vybrané ikony |
| Posuvník | – Posuvník a šipky posuvníku, všechny stavy |
| Okno | -Automaticky skrývat pozadí karty<br />– Panel nabídek a pozadí příkazu<br />– Nevybrané nebo nevybrané pozadí karty okna dokumentu a ohraničení dokumentu pro otevřené i dočasné karty<br />– Pozadí panelu nástrojů na nevybraném panelu<br />-Panel nástrojů – pozadí, vybrané i nevybrané |
| WindowFrame | – Ohraničení IDE |
| WindowText | -Automaticky skrývat popředí tabulátoru<br />-Popředí vybraného nástroje – karta okna<br />– Karta okna dokumentu bez fokusu a nevybrané nebo nevybrané tlačítko s dočasnou kartou<br />– Stromové zobrazení výchozí popředí a najetí myší nad nevybraný glyf<br />-Panel nástrojů vybral ohraničení karty<br />– Posunutí pozadí, ohraničení a glyfy posuvníku |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> Vystavení barev koncovým uživatelům

### <a name="overview"></a>Přehled

Někdy budete chtít, aby koncový uživatel mohl přizpůsobit uživatelské rozhraní, například když vytváříte Editor kódu nebo návrhovou plochu. Nejběžnější způsob, jak to provést, je použít dialogové okno **&gt; Možnosti nástrojů** . Pokud nemáte vysoce specializované uživatelské rozhraní, které vyžaduje speciální ovládací prvky, nejjednodušší způsob, jak prezentovat vlastní nastavení, je prostřednictvím stránky **písma a barvy** v části **prostředí** dialogového okna. Pro každý prvek, který vystavíte pro přizpůsobení, může uživatel zvolit změnu barvy popředí, barvy pozadí nebo obojího.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Vytváření VSPackage pro přizpůsobitelné barvy

VSPackage může řídit písma a barvy pomocí vlastních kategorií a zobrazovat položky na stránce vlastností písma a barvy. Při použití tohoto mechanismu musí sady VSPackage implementovat rozhraní [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) a jeho přidružená rozhraní.

V zásadě lze tento mechanismus použít pro úpravu všech existujících položek zobrazení a kategorií, které je obsahují. Neměli byste je ale používat k úpravám kategorie textový editor ani zobrazení položek. Další informace o kategorii textový editor najdete v tématu [Přehled písma a barev](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015).

Chcete-li implementovat vlastní kategorie nebo zobrazit položky, VSPackage musí:

- **Vytvořte nebo Identifikujte kategorie v registru.** Implementace rozhraní IDE stránky vlastností **písma a barvy** používá tyto informace k řádnému dotazování na službu, která podporuje danou kategorii.

- **Vytvořte nebo Identifikujte skupiny v registru (volitelné).** Může být užitečné definovat skupinu, která představuje sjednocení dvou nebo více kategorií. Pokud je definovaná skupina, IDE automaticky sloučí podkategorie a rozloží zobrazované položky v rámci skupiny.

- **Implementujte podporu IDE.**

- **Zpracuje změny písma a barev.**

#### <a name="to-create-or-identify-categories"></a>Chcete-li vytvořit nebo identifikovat kategorie

Vytvořte speciální typ položky registru Category v rámci `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` Where `<Category>` je nelokalizovaný název kategorie.

Naplňte registr dvěma hodnotami:

| Název | Typ | Data | Description |
| --- | --- | --- | --- |
| Kategorie | REG_SZ | Identifikátor GUID | Identifikátor GUID vytvořený k identifikaci kategorie |
| Balíček | REG_SZ | Identifikátor GUID | Identifikátor GUID služby VSPackage, která podporuje kategorii |

 Služba zadaná v registru musí poskytovat implementaci [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) pro odpovídající kategorii.

#### <a name="to-create-or-identify-groups"></a>Vytvoření nebo identifikace skupin

Vytvořte speciální typ položky registru Category v rámci `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` Where `<group>` je nelokalizovaný název skupiny.

Naplňte registr dvěma hodnotami:

| Název | Typ | Data | Description |
|--- | --- | --- | --- |
| Kategorie | REG_SZ | Identifikátor GUID | Identifikátor GUID vytvořený k identifikaci kategorie |
| Balíček | REG_SZ | Identifikátor GUID | Identifikátor GUID služby VSPackage, která podporuje kategorii |

Služba zadaná v registru musí poskytovat implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> pro odpovídající skupinu.

![Implementace IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 – a_FontAndColorGroup")<br />Implementace `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Implementace podpory IDE

Implementujte metodu [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), která vrátí rozhraní [IVSFONTANDCOLORDEFAULTS](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> rozhraní IDE pro každou kategorii nebo identifikátor GUID skupiny.

Pro každou kategorii, kterou podporuje, VSPackage implementuje samostatnou instanci rozhraní [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) .

Metody implementované prostřednictvím [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) musí poskytovat integrované vývojové prostředí (IDE) s:

- Seznam položek zobrazení v kategorii

- Lokalizovatelné názvy pro zobrazované položky

- Zobrazit informace pro každého člena kategorie

> [!NOTE]
> Každá kategorie musí obsahovat alespoň jednu zobrazovanou položku.

Rozhraní IDE používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> rozhraní k definování sjednocení několika kategorií.

Jeho implementace poskytuje integrované vývojové prostředí (IDE) s:

- Seznam kategorií, které tvoří danou skupinu

- Přístup k instancím [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) , které podporují jednotlivé kategorie v rámci skupiny

- Lokalizovatelné názvy skupin

#### <a name="updating-the-ide"></a>Aktualizace IDE

Rozhraní IDE ukládá informace o nastavení písma a barev do mezipaměti. Proto po jakékoli změně konfigurace písma a barev IDE zajistěte, aby byla mezipaměť aktuální, což je nejlepší postup.

Aktualizace mezipaměti se provádí prostřednictvím rozhraní [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) a je možné ji provést globálně nebo pouze na vybraných položkách.

### <a name="handling-font-and-color-changes"></a>Zpracování změn písma a barev

Aby bylo možné správně podporovat barevné nabarvení textu, který VSPackage zobrazuje, musí služba coloring, která podporuje VSPackage, reagovat na změny iniciované uživatelem, které provedly prostřednictvím stránky vlastností písma a barvy.

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
