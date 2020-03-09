---
title: Barvy a styly pro Visual Studio | Microsoft Docs
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ceea00a3fa77a9c1106f24f28ac1d5890437b41
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408998"
---
# <a name="colors-and-styling-for-visual-studio"></a>Barvy a styly pro sadu Visual Studio

## <a name="use-color-in-visual-studio"></a>Použití barev v aplikaci Visual Studio

V sadě Visual Studio barva se používá především jako komunikační nástroj, nejen jako dekorace. Použít barvu minimálně a vyhradit pro situace, ve které chcete:

- Komunikaci význam nebo umístění (například modifikátory platformu a jazyk)

- Upoutat pozornost (například označující změnu stavu)

- Lepší čitelnost a poskytovat zajímavá pro procházení uživatelského rozhraní

- Zvýšení žádoucí

Existuje několik možností pro přiřazení barev k elementům uživatelského rozhraní v sadě Visual Studio. Někdy může být obtížné zjistit, kterou možnost byste měli použít, nebo jak ji používat správně. Toto téma vám pomůže:

- Seznamte s různými službami a systémy, které slouží k definování barev v sadě Visual Studio.

- Výběr správné možnosti pro daný element.

- Správně použijte možnost, kterou jste zvolili.

> [!NOTE]
> Nikdy nekódujte pevně hexadecimální, RGB nebo systémové barvy k prvkům uživatelského rozhraní. Pomocí služby umožňuje flexibilitu při ladění odstín. Kromě toho bez služby nebude možné využívat možnosti přepínání motivů [služby VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Prvky rozhraní metody pro přiřazení barev k sadě Visual Studio

Zvolte metodu, která nejlépe odpovídá vaší prvky uživatelského rozhraní.

| Vaše uživatelské rozhraní | Metoda | Jaké jsou jejich? |
| --- | --- | --- |
| S vloženými nebo samostatné dialogových oknech. | **Systémové barvy** | Názvy systémů, které umožňují operačnímu systému definovat barvu a vzhled prvků uživatelského rozhraní, jako jsou běžné ovládací prvky dialogu. |
| Máte vlastní uživatelské rozhraní, které mají být konzistentní s celkové prostředí VS a máte prvky uživatelského rozhraní, které odpovídají kategorii a sémantický význam sdílené tokenů. | **Společné sdílené barvy** | Existující názvy token předdefinované barvy pro konkrétní prvky uživatelského rozhraní |
| Máte jednotlivé funkce nebo skupiny funkcí a neexistuje žádné sdílené barvy pro podobné prvky. | **Vlastní barvy** | Token názvy barev, které jsou specifické pro oblast, které není určené ke sdílení s další uživatelského rozhraní |
| Chcete povolit koncovému uživateli přizpůsobit uživatelské rozhraní nebo obsah (například pro textových editorů nebo specializovaná návrháře windows). | **Přizpůsobení koncovým uživatelům**<br /><br />**(Nástroje &gt; možnosti dialogového okna)** | Nastavení definovaná na stránce písma a barvy dialogového okna **nástroje &gt; možnosti** nebo specializované stránky specifické pro jednu funkci uživatelského rozhraní. |

### <a name="visual-studio-themes"></a>Visual Studio motivy

Sada Visual Studio nabízí tři různé barevné motivy: světlá, tmavá a modrá. Zjistí také režim s vysokým kontrastem, který je systémová barevný motiv určený pro usnadnění přístupu.

Uživatelé jsou při prvním použití aplikace Visual Studio vyzváni k výběru motivu a mohou později přepnout motivy tak, že přejdete na **nástroje &gt; možností &gt; prostředí &gt; obecné** a zvolíte nový motiv z rozevírací nabídky "barevný motiv".

Uživatelé také přepnout celý systémů do jednoho z několika vysokého kontrastu, motivů pomocí ovládacích panelů. Pokud uživatel vybere motiv s vysokým kontrastem, pak modulu pro výběr barvy motivu sady Visual Studio už má vliv na barev v sadě Visual Studio, i když žádné změny motivu se uloží pro, když uživatel ukončí režim s vysokým kontrastem. Další informace o režimu Vysoký kontrast najdete v tématu [výběr vysoký kontrast barev](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Služba VSColor

Visual Studio poskytuje službu prostředí barvy, známé jako VSColor služby, který umožňuje svázat barevných prvků uživatelského rozhraní s názvem záznam obsahující hodnoty barev pro každý motiv sady Visual Studio. Tím se zajistí, že vaše barvy se automaticky změní tak, aby odrážely aktuální uživatel vybral motiv nebo systém režim s vysokým kontrastem. Používání služby znamená, že implementace všechny změny motivů související barev je zpracována na jednom místě, a pokud používáte společné sdílené barvy ze služby, vaše uživatelské rozhraní bude automaticky odrážet nové motivy v budoucích verzích sady Visual Studio.

### <a name="implementation"></a>Implementace

Zdrojový kód sady Visual Studio obsahuje několik definičních souborech balíčku, které obsahují seznamy tokenů názvy a hodnoty příslušných barvu pro každý motiv. Barva služby přečte VSColors definované v těchto definičních souborů balíčku. Tyto barvy jsou odkazovány v kódu XAML nebo v kódu a poté načteny prostřednictvím metody `IVsUIShell5.GetThemedColor` nebo mapování DynamicResource.

### <a name="system-colors"></a>Systémové barvy

Běžné ovládací prvky odkazovat ve výchozím nastavení systémových barev. Pokud chcete, aby uživatelské rozhraní používalo systémové barvy, například při vytváření vloženého nebo samostatného dialogu, nemusíte nic dělat.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Ve službě VSColor běžné sdílené barvy

Vaše prvky rozhraní by měly odrážet celkové prostředí sady Visual Studio. Tím, že znovu použijete společné sdílené barvy, které jsou vhodné pro komponentu uživatelského rozhraní, kterou navrhujete, zajistíte, že vaše rozhraní je konzistentní s jinými rozhraními sady Visual Studio a že se barvy automaticky aktualizují při přidání nebo aktualizaci motivů.

Než začnete používat společné sdílené barvy, ujistěte se, že vám pochopit, jak správně používat. Nesprávné použití společné sdílené barvy může způsobit nekonzistentní, frustrující nebo matoucí prostředí pro vaše uživatele.

### <a name="user-customizable-colors"></a>Uživatelsky přizpůsobitelnými barvy

Viz: vystavení [barev koncovým uživatelům](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

V některých případech budete chtít, aby koncový uživatel mohl přizpůsobit uživatelské rozhraní, například když vytváříte Editor kódu nebo návrhovou plochu. Přizpůsobitelné komponenty uživatelského rozhraní jsou k dispozici v části **písma a barvy** dialogového okna **nástroje &gt; možnosti** , kde mohou uživatelé změnit barvu popředí, barvu pozadí nebo obojí.

![Dialogové okno Možnosti &gt; nástrojů](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 – a_ToolsOptionsDialog")<br />Dialogové okno Možnosti &gt; nástrojů

## <a name="BKMK_TheVSColorService"></a>Služba VSColor

Visual Studio poskytuje službu barva prostředí, označovaný taky jako služba VSColor nebo služba barva prostředí. Tato služba umožňuje svázat nastavení barev pro každý motiv obsahující název hodnota barvy barevných prvků uživatelského rozhraní. Službu VSColor musí použít pro všechny prvky uživatelského rozhraní tak, aby barvy automaticky změnit tak, aby odrážela aktuální uživatel vybral motiv a tak, aby uživatelské rozhraní svázaná se službou barva prostředí se bude integrovat s nové motivy v budoucích verzích sady Visual Studio.

### <a name="how-the-service-works"></a>Jak služba funguje

Barva služby prostředí přečte že vscolors definované v .pkgdef součásti uživatelského rozhraní. Tyto VSColors jsou následně odkazovány v kódu XAML nebo kódu a jsou načteny prostřednictvím `IVsUIShell5.GetThemedColor` nebo mapování `DynamicResource`.

![Architektura služby Color Service prostředí](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 – a_EnvironmentColorServiceArchitecture")<br />Architektura služby Color Service prostředí

### <a name="accessing-the-service"></a>Přístupu ke službě

Existuje několik různých způsobů přístupu VSColor služby, v závislosti na tom, jaký druh barva tokeny můžete používají a jaký druh kódu, je nutné.

#### <a name="predefined-environment-colors"></a>Prostředí předdefinované barvy

##### <a name="from-native-code"></a>Z nativního kódu

Prostředí poskytuje službu, která poskytuje přístup k `COLORREF` barev. Služba/rozhraní je:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

V souboru VSShell80. idl má výčet `__VSSYSCOLOREX` konstanty barev prostředí. Pokud ho chcete použít, předejte jako hodnotu indexu jednu z hodnot `enum __VSSYSCOLOREX` popsaných na webu MSDN nebo běžné číslo indexu, které rozhraní API systému Windows, `GetSysColor`akceptuje. Tím získá zpět hodnoty RGB barvy, který se má použít ve druhém parametru.

Pokud uložíte pero nebo štětec s novou barvou, je nutné `AdviseBroadcastMessages` (z prostředí sady Visual Studio) a naslouchat `WM_SYSCOLORCHANGE` a `WM_THEMECHANGED` zpráv.

Chcete-li získat přístup ke službě Color Service v nativním kódu, proveďte volání, které se podobá této:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Hodnoty `COLORREF` vrácené `GetVSSysColorEx()`m obsahují pouze součásti R, G, B barvy motivu. Pokud položka motiv používá transparentnosti, hodnotu alfa kanálu se zahodí před vrácením. Proto pokud je potřeba použít barvu prostředí zájmu na místo, kde je kanál transparentnosti důležitý, měli byste místo `IVsUIShell2::GetVSSysColorEx`použít `IVsUIShell5.GetThemedColor`, jak je popsáno dále v tomto tématu.

##### <a name="from-managed-code"></a>Ze spravovaného kódu

Přístup k službě VSColor prostřednictvím nativního kódu je poměrně jednoduché. Pokud pracujete prostřednictvím spravovaného kódu, ale zjišťování toho, jak používat službu může být složité. To na paměti tady je C# fragment kódu představením toho tento postup:

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

Pokud pracujete v jazyce Visual Basic, použijte:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Z uživatelského rozhraní WPF

Pomocí hodnot exportovaných do `ResourceDictionary`aplikace můžete navazovat barvy sady Visual Studio. Níže je příklad použití prostředků z tabulky barev, stejně jako vytvoření vazby na data písma prostředí v XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Pomocné rutiny třídy a metody pro spravovaný kód

Pro spravovaný kód obsahuje Knihovna architektury spravovaného balíčku (`Microsoft.VisualStudio.Shell.12.0.dll`) prostředí několik pomocných tříd usnadňujících použití barev motivů.

Pomocné metody ve třídě `Microsoft.VisualStudio.Shell.VsColors` v poli MPF zahrnují `GetThemedGDIColor()` a `GetThemedWPFColor()`. Tyto pomocné metody vracejí hodnotu barvy položky motivu jako `System.Drawing.Color` nebo `System.Windows.Media.Color`, aby se použily v uživatelském rozhraní WinForms nebo WPF.

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

Třídy lze také získat VSCOLOR identifikátory pro danou WPF barva klíč prostředku, nebo naopak.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Metody `VsColors` třídy dotazování na službu VSColor, aby vrátila hodnotu barvy pokaždé, když jsou vyvolány. Chcete-li získat hodnotu barvy jako `System.Drawing.Color`, je alternativa s vyšším výkonem místo toho použití metod `Microsoft.VisualStudio.PlatformUI.VSThemeColor` třídy, která ukládá do mezipaměti hodnoty barvy získané ze služby VSColor. Třída interně se přihlásí k odběru událostí zprávy všesměrového vysílání prostředí a zahodí hodnotu uloženou v mezipaměti při výskytu události měnící motiv. Navíc poskytuje třídy. Událost NET přívětivá přihlásit k odběru změn motiv. Pomocí události `ThemeChanged` přidejte novou obslužnou rutinu a pomocí metody `GetThemedColor()` Získejte hodnoty barev pro `ThemeResourceKeys` zájmu. Vzorový kód by mohl vypadat takto:

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

## <a name="BKMK_ChoosingHighContrastColors"></a>Volba Vysoký kontrastch barev

### <a name="overview"></a>Přehled

Windows používá několik motivů vysokého kontrastu úrovni systému, které zvyšují barevný kontrast textu, pozadí a obrázků, provádění prvky se zobrazí na obrazovce zřetelný. Z důvodu usnadnění je důležité, že prvky rozhraní sady Visual Studio nereaguje správně uživatelé přepněte motiv s vysokým kontrastem.

Vysoký kontrast – motivy lze použít pouze na několik systémových barev. Pokud zvolíte, že váš systém názvy barev, mějte na paměti následující tipy:

- **Vyberte systémové barvy, které mají stejný sémantický význam** jako prvek, který barevně vybarvit. Například pokud zvolíte vysoký kontrast pro text v rámci časového období, použijte WindowText a není ControlText.

- **Zvolte páry na popředí** nebo na pozadí společně nebo nebudete mít jistotu, že volba barvy bude fungovat ve všech motivech vysoký kontrast.

- **Určete, které části uživatelského rozhraní jsou nejdůležitější a ujistěte se, že oblasti obsahu budou vystupovat.** Dojde ke ztrátě velkého množství podrobností, které malé rozdíly v barevných odstínech obvykle odlišují, takže použití silné barvy ohraničení je běžné pro definování oblastí obsahu, protože pro různé oblasti obsahu nejsou k dispozici žádné barevné varianty.

### <a name="system-color-set"></a>Sada barev systému

Tabulka na [blogu týmu WPF: SystemColors reference](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) označuje úplnou sadu systémových názvů barev a odpovídající odstíny zobrazené v jednotlivých motivech.

Při použití této omezené sady barev na vaše uživatelské rozhraní *se očekává, že přijdete o jemný detail, který se nachází v "normálním" motivu*. Tady je příklad uživatelského rozhraní s drobným šedé, které slouží k odlišení oblastí v rámci panelu nástrojů. V kombinaci s stejné okno zobrazuje v režimu vysokého kontrastu, uvidíte, že pozadí jsou stejné hue a ohraničení tyto oblasti jsou označeny ohraničení samostatně:

![Příklad toho, jak se v Vysoký kontrast ztratí informace o jemných podrobnostech](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 – a_PropertiesWindow")<br />Příklad toho, jak se v Vysoký kontrast ztratí informace o jemných podrobnostech

#### <a name="choosing-text-colors-in-an-editor"></a>Výběr barvy textu v editoru

Barevný text se používá v editoru nebo na návrhové ploše k označení významu, jako je například umožnění snadné identifikace skupin podobných položek. V motiv s vysokým kontrastem ale nemáte schopnost rozlišovat mezi více než tři barvy textu. WindowText, GrayText a HotTrackText jsou k dispozici na površích WindowBackground pouze barvy. Protože nelze použít více než třemi barvami, pečlivě určit nejdůležitější rozdíly, které chcete zobrazit v režimu vysokého kontrastu.

Odstíny pro každý token názvů povolené na povrchu editoru, jako jsou uvedeny v jednotlivých motiv s vysokým kontrastem:

![Porovnání editoru Vysoký kontrast](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 – b_HCEditorComparison")<br />Porovnání editoru Vysoký kontrast

Příklady editoru plochy v motivu modrý:

![Editor v modrém motivu](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 – c_EditorBlue")<br />Editor v modrém motivu

![Editor v Vysoký kontrast #1 motiv](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 – d_EditorHC1")<br />Editor v Vysoký kontrast #1 motiv

### <a name="usage-patterns"></a>Vzory využití

Mnoho běžných prvků uživatelského rozhraní už má definované Vysoký kontrasté barvy. Tyto vzory využití může odkazovat při výběru vlastní systém názvy barev, tak, že vaše prvky uživatelského rozhraní jsou konzistentní s podobné součásti.

| Systémové barvy | Využití |
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
| Zvýraznění | – Všechny najetí myší a nahrané pozadí a ohraničení, s výjimkou pozadí rozevíracího seznamu pole se seznamem a ohraničení tlačítka pro přetečení dokumentu<br />– Pozadí vybraných položek |
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

## <a name="BKMK_ExposingColorsForEndUsers"></a>Vystavení barev koncovým uživatelům

### <a name="overview"></a>Přehled

Někdy budete chtít, aby koncový uživatel mohl přizpůsobit uživatelské rozhraní, například když vytváříte Editor kódu nebo návrhovou plochu. Nejběžnější způsob, jak to provést, je pomocí dialogového okna **nástroje &gt; možnosti** . Pokud nemáte vysoce specializované uživatelské rozhraní, které vyžaduje speciální ovládací prvky, nejjednodušší způsob, jak prezentovat vlastní nastavení, je prostřednictvím stránky **písma a barvy** v části **prostředí** dialogového okna. Pro každý prvek, který zveřejníte pro přizpůsobení uživatel může zvolit změnit barvu popředí, pozadí nebo obojí.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Vytváření balíčku VSPackage pro přizpůsobitelné barvy

VSPackage můžete řídit písma a barvy prostřednictvím vlastní kategorie a zobrazení položek na stránce vlastností písma a barvy. Při použití tohoto mechanismu musí sady VSPackage implementovat rozhraní [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) a jeho přidružená rozhraní.

V zásadě tento mechanismus je možné změnit všechny existující zobrazit položky a kategorie, které je obsahují. Ale by neměly být použít změnit kategorii textový Editor, nebo jeho položky zobrazení. Další informace o kategorii textový editor najdete v tématu [Přehled písma a barev](/visualstudio/extensibility/font-and-color-overview?view=vs-2015).

Pokud chcete implementovat vlastní kategorie nebo zobrazit položky, musí VSPackage:

- **Vytvořte nebo Identifikujte kategorie v registru.** Implementace rozhraní IDE stránky vlastností **písma a barvy** používá tyto informace k řádnému dotazování na službu, která podporuje danou kategorii.

- **Vytvořte nebo Identifikujte skupiny v registru (volitelné).** Může být užitečné k definování skupiny, která představuje sjednocení dvou nebo více kategorií. Pokud skupina je definována, rozhraní IDE automaticky sloučí podkategorie a distribuuje zobrazení položek v rámci skupiny.

- **Implementujte podporu IDE.**

- **Zpracuje změny písma a barev.**

#### <a name="to-create-or-identify-categories"></a>K vytvoření nebo určení kategorie

Vytvořte speciální typ položky registru Category v rámci `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]`, kde `<Category>` je nelokalizovaný název kategorie.

Naplnění registru pomocí dvou hodnot:

| Název | Typ | Data | Popis |
| --- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Vytvoří identifikátor GUID k identifikaci kategorii |
| Balíček | REG_SZ | GUID | Identifikátor GUID služby VSPackage, která podporuje kategorii |

 Služba zadaná v registru musí poskytovat implementaci [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) pro odpovídající kategorii.

#### <a name="to-create-or-identify-groups"></a>Vytvořte nebo Identifikujte skupiny

Vytvořte speciální typ položky registru kategorie v `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]`, kde `<group>` je nelokalizovaný název skupiny.

Naplnění registru pomocí dvou hodnot:

| Název | Typ | Data | Popis |
|--- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Vytvoří identifikátor GUID k identifikaci kategorii |
| Balíček | REG_SZ | GUID | Identifikátor GUID služby VSPackage, která podporuje kategorii |

Služba zadaná v registru musí poskytovat implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> pro odpovídající skupinu.

![Implementace IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 – a_FontAndColorGroup")<br />Implementace `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>K implementaci podpora integrované vývojové prostředí

Implementujte metodu [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), která vrací rozhraní [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) nebo rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> k integrovanému vývojovém prostředí (IDE) pro každou kategorii nebo identifikátor GUID skupiny.

Pro každou kategorii, kterou podporuje, VSPackage implementuje samostatnou instanci rozhraní [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) .

Metody implementované prostřednictvím [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) musí poskytovat integrované vývojové prostředí (IDE) s:

- Seznamy zobrazení položek v kategorii

- Lokalizovatelné názvy pro zobrazení položek

- Zobrazení informací pro každého člena kategorie

> [!NOTE]
> Každá kategorie musí obsahovat alespoň jednu zobrazovanou položku.

Rozhraní IDE používá rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> k definování sjednocení několika kategorií.

Jeho implementace poskytuje integrované vývojové prostředí s:

- Seznam kategorií, které tvoří danou skupinu

- Přístup k instancím [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) , které podporují jednotlivé kategorie v rámci skupiny

- Názvy zdrojů lokalizovatelných skupin

#### <a name="updating-the-ide"></a>Aktualizuje se rozhraní IDE

Rozhraní IDE ukládá do mezipaměti informace o nastavení písem a barev. Proto po jakékoliv úpravě konfigurace rozhraní IDE písma a barvy zajišťující, že je aktuální mezipaměti je osvědčeným postupem.

Aktualizace mezipaměti se provádí prostřednictvím rozhraní [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) a je možné ji provést globálně nebo pouze na vybraných položkách.

### <a name="handling-font-and-color-changes"></a>Zpracování změn písma a barvy

Pro podporu správně zabarvení textu, který zobrazí VSPackage, musí služba zabarvení podporující sady VSPackage reagovat na uživatelem iniciované změny prostřednictvím stránky vlastností písma a barvy.

K tomuto účelu VSPackage musí:

- **zpracujte události generované** rozhraním IDE implementací rozhraní [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) . Integrované vývojové prostředí volá metodu odpovídající následující stránky písma a barev uživatelské úpravy. Například volá metodu [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) , pokud je vybráno nové písmo.

  **ANI**

- **cyklické dotazování na rozhraní IDE o změny**. To lze provést prostřednictvím rozhraní [Chyba metody IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) implementovaného systémem. I když primárně pro podporu trvalosti, metoda [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) může získat informace o písmech a barvách pro zobrazení položek. Další informace o nastavení písma a barev najdete v článku na webu MSDN, který [přistupuje k uloženým písmům a nastavením barev](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015).

> [!NOTE]
> Aby bylo zajištěno, že jsou výsledky cyklického dotazování správné, pomocí rozhraní [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) určete, zda je před voláním metod načtení z rozhraní [Chyba metody IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) nutné vyprázdnit mezipaměť a aktualizovat.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrace vlastní písma a barvy kategorie bez implementace rozhraní

Následující příklad kódu ukazuje, jak zaregistrovat vlastní písma a barev kategorie bez implementace rozhraní:

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

### <a name="set-the-font-and-color-property-category-guid"></a>Nastavit vlastnost kategorii písma a barvy GUID

Následující příklad kódu ukazuje nastavení kategorie identifikátory GUID.

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
