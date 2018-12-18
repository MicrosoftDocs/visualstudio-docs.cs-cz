---
title: Barvy a styly pro sadu Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/31/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d8285ad08a9ad83ecd137223459a6b29cb7ae69
ms.sourcegitcommit: a34b7d4fdb3872865fcf98ba24a0fced58532adc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561709"
---
# <a name="colors-and-styling-for-visual-studio"></a>Barvy a styly pro sadu Visual Studio

## <a name="use-color-in-visual-studio"></a>Použití barev v sadě Visual Studio

V sadě Visual Studio barva se používá především jako komunikační nástroj, nejen jako dekorace. Použít barvu minimálně a vyhradit pro situace, ve které chcete:

- Komunikaci význam nebo umístění (například modifikátory platformu a jazyk)

- Upoutat pozornost (například označující změnu stavu)

- Lepší čitelnost a poskytovat zajímavá pro procházení uživatelského rozhraní

- Zvýšení žádoucí

Existuje několik možností pro přiřazení barev k elementům uživatelského rozhraní v sadě Visual Studio. V některých případech může být obtížné obrázek si možnosti, kterou se má použít, nebo jak používat správně. Toto téma vám pomůže:

- Seznamte s různými službami a systémy, které slouží k definování barev v sadě Visual Studio.

- Výběr správné možnosti pro daný element.

- Správně použijte možnost, kterou jste zvolili.

> [!NOTE]
> Nikdy pevně hex, RGB nebo systémové barvy prvkům uživatelského rozhraní. Pomocí služby umožňuje flexibilitu při ladění odstín. Navíc bez této služby, nebude moct využívat možnosti přepínání motivů [službu VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Prvky rozhraní metody pro přiřazení barev k sadě Visual Studio

Zvolte metodu, která nejlépe odpovídá vaší prvky uživatelského rozhraní.

| Vaše uživatelské rozhraní | Metoda | Jaké jsou jejich? |
| --- | --- | --- |
| S vloženými nebo samostatné dialogových oknech. | **Systémové barvy** | Běžné ovládací prvky dialogového okna, jako jsou systémové názvy, které umožňují definovat barvu a vzhled prvky uživatelského rozhraní operačního systému. |
| Máte vlastní uživatelské rozhraní, které mají být konzistentní s celkové prostředí VS a máte prvky uživatelského rozhraní, které odpovídají kategorii a sémantický význam sdílené tokenů. | **Společné sdílené barvy** | Existující názvy token předdefinované barvy pro konkrétní prvky uživatelského rozhraní |
| Máte jednotlivé funkce nebo skupiny funkcí a neexistuje žádné sdílené barvy pro podobné prvky. | **Vlastní barvy** | Token názvy barev, které jsou specifické pro oblast, které není určené ke sdílení s další uživatelského rozhraní |
| Chcete povolit koncovému uživateli přizpůsobit uživatelské rozhraní nebo obsah (například pro textových editorů nebo specializovaná návrháře windows). | **Přizpůsobení koncových uživatelů**<br /><br />**(Nástroje &gt; dialogové okno Možnosti)** | Nastavení definované na stránce "Písma a barvy" **nástroje &gt; možnosti** dialogové okno nebo speciální stránky specifické pro jeden funkce uživatelského rozhraní. |

### <a name="visual-studio-themes"></a>Visual Studio motivy

Visual Studio obsahuje tří různých barev motivů: světla, tmavý a modrou. Zjistí také režim s vysokým kontrastem, který je systémová barevný motiv určený pro usnadnění přístupu.

Uživatelé vyzváni k výběru motivu při jejich prvním použití sady Visual Studio a je možné později změnit motivy tak, že přejdete do **nástroje &gt; možnosti &gt; prostředí &gt; Obecné** a nový motiv z výběru "barevný motiv" rozevírací nabídky.

Uživatelé také přepnout celý systémů do jednoho z několika vysokého kontrastu, motivů pomocí ovládacích panelů. Pokud uživatel vybere motiv s vysokým kontrastem, pak modulu pro výběr barvy motivu sady Visual Studio už má vliv na barev v sadě Visual Studio, i když žádné změny motivu se uloží pro, když uživatel ukončí režim s vysokým kontrastem. Další informace o režim s vysokým kontrastem, naleznete v tématu [výběr vysoký kontrast – barvy](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Služba VSColor

Visual Studio poskytuje službu prostředí barvy, známé jako VSColor služby, který umožňuje svázat barevných prvků uživatelského rozhraní s názvem záznam obsahující hodnoty barev pro každý motiv sady Visual Studio. Tím se zajistí, že vaše barvy se automaticky změní tak, aby odrážely aktuální uživatel vybral motiv nebo systém režim s vysokým kontrastem. Používání služby znamená, že implementace všechny změny motivů související barev je zpracována na jednom místě, a pokud používáte společné sdílené barvy ze služby, vaše uživatelské rozhraní bude automaticky odrážet nové motivy v budoucích verzích sady Visual Studio.

### <a name="implementation"></a>Implementace

Zdrojový kód sady Visual Studio obsahuje několik definičních souborech balíčku, které obsahují seznamy tokenů názvy a hodnoty příslušných barvu pro každý motiv. Barva služby přečte VSColors definované v těchto definičních souborů balíčku. Tyto barvy se odkazuje v kódu XAML nebo v kódu a pak načten prostřednictvím buď `IVsUIShell5.GetThemedColor` metody nebo DynamicResource mapování.

### <a name="system-colors"></a>Systémové barvy

Běžné ovládací prvky odkazovat ve výchozím nastavení systémových barev. Pokud chcete, aby vaše uživatelské rozhraní používat barvy systému, stejně jako při vytváření vložené nebo samostatné dialogovém okně nemusíte nic dělat.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Ve službě VSColor běžné sdílené barvy

Vaše prvky rozhraní by měly odrážet celkové prostředí sady Visual Studio. Opětovným použitím běžné sdílené barvy, které jsou vhodné pro součást uživatelského rozhraní, kterou vytváříte, zajistíte tím, že vaše rozhraní je konzistentní s jinými rozhraními sady Visual Studio a že barev bude automaticky aktualizovat při přidávání nebo aktualizaci motivy.

Než začnete používat společné sdílené barvy, ujistěte se, že vám pochopit, jak správně používat. Nesprávné použití společné sdílené barvy může způsobit nekonzistentní, frustrující nebo matoucí prostředí pro vaše uživatele.

### <a name="user-customizable-colors"></a>Uživatelsky přizpůsobitelnými barvy

Přejděte na téma: [vystavení barvy pro koncové uživatele](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

V některých případech budete chtít povolit koncovému uživateli přizpůsobit uživatelské rozhraní, stejně jako při vytváření editoru kódu nebo návrhovou plochu. Přizpůsobitelné součásti uživatelského rozhraní jsou součástí **písma a barvy** část **nástroje &gt; možnosti** dialogové okno, ve kterém uživatelé mohou změnit barvu popředí, pozadí nebo obojí.

![Nástroje &gt; dialogové okno Možnosti](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")<br />Nástroje &gt; dialogové okno Možnosti

##  <a name="BKMK_TheVSColorService"></a> Služba VSColor

Visual Studio poskytuje službu barva prostředí, označovaný taky jako služba VSColor nebo služba barva prostředí. Tato služba umožňuje svázat nastavení barev pro každý motiv obsahující název hodnota barvy barevných prvků uživatelského rozhraní. Službu VSColor musí použít pro všechny prvky uživatelského rozhraní tak, aby barvy automaticky změnit tak, aby odrážela aktuální uživatel vybral motiv a tak, aby uživatelské rozhraní svázaná se službou barva prostředí se bude integrovat s nové motivy v budoucích verzích sady Visual Studio.

### <a name="how-the-service-works"></a>Jak služba funguje

Barva služby prostředí přečte že vscolors definované v .pkgdef součásti uživatelského rozhraní. Tyto VSColors se pak odkazuje v kódu XAML nebo kódu a jsou načteny prostřednictvím buď `IVsUIShell5.GetThemedColor` nebo `DynamicResource` mapování.

![Architektura služby barva prostředí](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")<br />Architektura služby barva prostředí

### <a name="accessing-the-service"></a>Přístupu ke službě

Existuje několik různých způsobů přístupu VSColor služby, v závislosti na tom, jaký druh barva tokeny můžete používají a jaký druh kódu, je nutné.

#### <a name="predefined-environment-colors"></a>Prostředí předdefinované barvy

##### <a name="from-native-code"></a>Z nativního kódu

Poskytuje službu, která poskytuje přístup k prostředí `COLORREF` barev. Služba/rozhraní je:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

V souboru VSShell80.idl výčtu `__VSSYSCOLOREX` má barva konstanty prostředí. Pro použití je třeba předat jako hodnotu indexu některá z hodnot z `enum __VSSYSCOLOREX` zdokumentované v MSDN nebo pravidelné index číslo, které v systému Windows, rozhraní API, `GetSysColor`, přijímá. Tím získá zpět hodnoty RGB barvy, který se má použít ve druhém parametru.

Pokud ukládáte pera nebo novou barvou štětce, je nutné `AdviseBroadcastMessages` (z prostředí sady Visual Studio) a naslouchat `WM_SYSCOLORCHANGE` a `WM_THEMECHANGED` zprávy.


Přístup k této službě barvy v nativním kódu, provedete volání, které vypadá takto:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> `COLORREF` Hodnot vrácených `GetVSSysColorEx()` obsahovat pouze R, G, B součástí barvu motivu. Pokud položka motiv používá transparentnosti, hodnotu alfa kanálu se zahodí před vrácením. Proto pokud barvu prostředí zájmu musí být použita na místě, kde kanál transparentnosti je důležité, abyste používali `IVsUIShell5.GetThemedColor` místo `IVsUIShell2::GetVSSysColorEx`, jak je popsáno dále v tomto tématu.

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

Mohl vytvořit vazbu k Visual Studio barvy prostřednictvím hodnoty exportovat do aplikace sady `ResourceDictionary`. Níže je příklad použití prostředků z tabulky barev, stejně jako vytvoření vazby na data písma prostředí v XAML.

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

Pro spravovaný kód k prostředí Managed Package Framework knihovny (`Microsoft.VisualStudio.Shell.12.0.dll`) obsahuje několik pomocných tříd usnadnění použití motivy barev.

Pomocné metody v `Microsoft.VisualStudio.Shell.VsColors` zahrnují třídy v MPF `GetThemedGDIColor()` a `GetThemedWPFColor()`. Těchto metod helper vrátí hodnotu barvy motivu vstupu jako `System.Drawing.Color` nebo `System.Windows.Media.Color`, který se má použít v WinForms nebo WPF uživatelského rozhraní.

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

Metody `VsColors` třídy dotazování na službu VSColor vrátit hodnotu barvy pokaždé, když jsou vyvolány. Získat hodnotu barvy jako `System.Drawing.Color`, alternativou s lepším výkonem je místo toho použití metod pro posunutí `Microsoft.VisualStudio.PlatformUI.VSThemeColor` třídu, která ukládá do mezipaměti, barevné hodnoty získané ze služby VSColor. Třída interně se přihlásí k odběru událostí zprávy všesměrového vysílání prostředí a zahodí hodnotu uloženou v mezipaměti při výskytu události měnící motiv. Navíc poskytuje třídy. Událost NET přívětivá přihlásit k odběru změn motiv. Použít `ThemeChanged` událost přidat novou obslužnou rutinu a používat `GetThemedColor()` metodu k získání barva hodnoty `ThemeResourceKeys` zájmu. Vzorový kód by mohl vypadat takto:

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

##  <a name="BKMK_ChoosingHighContrastColors"></a> Výběr vysoký kontrast – barvy

### <a name="overview"></a>Přehled

Windows používá několik motivů vysokého kontrastu úrovni systému, které zvyšují barevný kontrast textu, pozadí a obrázků, provádění prvky se zobrazí na obrazovce zřetelný. Z důvodu usnadnění je důležité, že prvky rozhraní sady Visual Studio nereaguje správně uživatelé přepněte motiv s vysokým kontrastem.

Vysoký kontrast – motivy lze použít pouze na několik systémových barev. Pokud zvolíte, že váš systém názvy barev, mějte na paměti následující tipy:

- **Zvolte systémové barvy, které mají stejný význam sémantické** jako element, který se barevné zvýrazňování. Například pokud zvolíte vysoký kontrast pro text v rámci časového období, použijte WindowText a není ControlText.

- **Vybrat dvojice popředí nebo pozadí** společně nebo nesmí být jistí, že v všechny Vysokokontrastních motivech bude fungovat výběr barvy.

- **Určit, jaké části uživatelského rozhraní jsou nejdůležitější a ujistěte se, že se zvýraznění oblasti obsahu.** Velké množství podrobností, která by obvykle rozlišit lišila odstín barvy, dojde ke ztrátě, takže použití barvy ohraničení silné je společné pro definování oblasti obsahu, protože nejsou žádné varianty barev pro různé oblasti obsahu.

### <a name="system-color-set"></a>Sada barev systému

V tabulce v [WPF Team Blog: odkaz SystemColors](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) označuje kompletní sadu názvy barev systému a odpovídající odstíny zobrazí v každé motiv.

Při použití omezenou sadu barev uživatelské rozhraní, *očekává se, že dojde ke ztrátě drobným podrobnosti, které byly k dispozici v "normální" motivy*. Tady je příklad uživatelského rozhraní s drobným šedé, které slouží k odlišení oblastí v rámci panelu nástrojů. V kombinaci s stejné okno zobrazuje v režimu vysokého kontrastu, uvidíte, že pozadí jsou stejné hue a ohraničení tyto oblasti jsou označeny ohraničení samostatně:

![Příklad, jak drobným podrobnosti jsou ztraceny ve vysokém kontrastu](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")<br />Příklad, jak drobným podrobnosti jsou ztraceny ve vysokém kontrastu

#### <a name="choosing-text-colors-in-an-editor"></a>Výběr barvy textu v editoru

Obarvený řetězec ve text slouží k označení význam, jako je umožňující snadnou identifikaci skupin podobné položky v editoru nebo na návrhové ploše. V motiv s vysokým kontrastem ale nemáte schopnost rozlišovat mezi více než tři barvy textu. WindowText, GrayText a HotTrackText jsou k dispozici na površích WindowBackground pouze barvy. Protože nelze použít více než třemi barvami, pečlivě určit nejdůležitější rozdíly, které chcete zobrazit v režimu vysokého kontrastu.

Odstíny pro každý token názvů povolené na povrchu editoru, jako jsou uvedeny v jednotlivých motiv s vysokým kontrastem:

![Vysoký kontrast editor porovnání](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")<br />Vysoký kontrast editor porovnání

Příklady editoru plochy v motivu modrý:

![Editor motivu modrý](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")<br />Editor v modrý motiv

![Editor motivu Vysoký kontrast 1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />Editor motivu Vysoký kontrast 1

### <a name="usage-patterns"></a>Vzory využití

Mnoho běžných prvků uživatelského rozhraní již mít vysoký kontrast – barvy, které jsou definovány. Tyto vzory využití může odkazovat při výběru vlastní systém názvy barev, tak, že vaše prvky uživatelského rozhraní jsou konzistentní s podobné součásti.

| Systémové barvy | Použití |
| --- | --- |
| ActiveCaption | – Integrované vývojové prostředí aktivní a glyfy rafted okno tlačítko na při najetí myší a stiskněte klávesu<br />-Title pozadí panelu pro integrované vývojové prostředí a rafted windows<br />– Pozadí panelu výchozí stav |
| ActiveCaptionText | -Active integrovaného vývojového prostředí a rafted okna popředí panelu title (text a glyfy)<br />-Na pozadí a ohraničení tlačítka aktivní okno na při najetí myší a stiskněte klávesu |
| Ovládací prvek | – Pole se seznamem, rozevíracího seznamu a hledání řídit výchozí a zakázán na pozadí, včetně tlačítko rozevíracího seznamu<br />-Pozadí tlačítka target ukotvení<br />-– Pozadí panelu příkaz<br />– Pozadí okna nástroj |
| ControlDark | – Integrované vývojové prostředí pozadí<br />-Oddělovače řádku nabídek a příkazů<br />-– Ohraničení panelu příkaz<br />– Shadows nabídka<br />– Nástroj okraj výchozí a při najetí myší kartě okna a oddělovač<br />-Dokumentu i na pozadí tlačítko přetečení<br />– Dock cíl piktogram ohraničení |
| ControlDarkDark |– Okno s kartou bez fokusu, vybraný dokument |
| ControlLight |-Karta border automatického schovávání<br />– Ohraničení pole se seznamem pole a rozevírací seznam<br />-Ukotvit cílové pozadí a ohraničení |
| ControlLightLight | – Vybraný, úzce zaměřený prozatímní ohraničení |
| ControlText | – Piktogram pole se seznamem pole a rozevírací seznam<br />– Text kartě okna nevybranou nástroj |
| GrayText |– Pole se seznamem a rozevírací seznam zakázané ohraničení, piktogram rozevíracího seznamu, text a text položky nabídky<br />– Text zakázáno nabídky<br />– Text záhlaví ovládacího prvku "možnosti hledání" hledání<br />– Oddělovač oddílu vyhledávání ovládacích prvků |
| Zvýraznění | – Veškerá při najetí myší a při stisknutí pozadí a ohraničení, s výjimkou pole se seznamem ohraničení pole pro rozevírací tlačítko na pozadí a dokument dobře přetečení tlačítko<br />– Pozadí vybrané položky |
| HighlightText | – Veškerá při najetí myší a při stisknutí foregrounds (text a glyfy)<br />-Zaměřený nástroj oken a dokumentů kartě okna ovládacího prvku popředí<br />-Zaměřený nástroj okno nadpis panel ohraničení<br />-Cílené, vybrané prozatímní kartě popředí<br />-Document dobře přetečení tlačítko ohraničení při najetí myší a stisknutím klávesy<br />-Vybrané ikony ohraničení|
| HotTrack | -Posuvník jezdce na pozadí a ohraničení při stisknutí<br />-Posuvníku piktogram šipky při stisknutí |
| InactiveCaption | – Integrované vývojové prostředí neaktivní a rafted okno glyfy tlačítka při najetí myší<br />-Title pozadí panelu pro integrované vývojové prostředí a rafted windows<br />-Zakázaný vyhledávání pozadí ovládacího prvku |
| InactiveCaptionText | – Integrované vývojové prostředí neaktivní a rafted windows nadpis panelu popředí (text a glyfy)<br />-Neaktivního okna tlačítka na pozadí a ohraničení při najetí myší<br />-Bez fokusu nástroj okno tlačítko na pozadí a ohraničení<br />-Zakázaný hledání popředí ovládacího prvku |
| Nabídka | – Pozadí nabídky rozevírací seznam<br />-Checked a zakázané zaškrtávací políčko na pozadí |
| MenuText | -Rozevírací nabídka ohraničení<br />-Značky zaškrtnutí<br />– Glyph nabídka<br />– Textu rozevírací nabídky<br />-Vybrané ikony ohraničení |
| Posuvník | -Posun řádku a posuvník šipku na pozadí, všechny stavy |
| Okno | Automatického schovávání kartu na pozadí<br />-Nabídky panelu a příkaz police pozadí<br />– Dokument bez fokusu nebo nevybraný okno kartu pozadí a ohraničení dokumentu, otevřené a dočasné karty<br />– Pozadí panelu název okna nástroj bez fokusu<br />– Nástroj kartu pozadí okna, vybrali i nevybrané |
| WindowFrame | – Integrované vývojové prostředí ohraničení |
| WindowText | -Automatického schovávání kartu popředí<br />– Vybraný nástroj okno Karta popředí<br />– Bez fokusu nebo nevybraný prozatímní kartě popředí a na kartě okna dokumentu bez fokusu<br />-Popředí výchozí zobrazení a strom při najetí myší nad nevybrané glyfů<br />– Okraj vybraná karta okna nástroj<br />-Posuvníku thumb pozadí ohraničení a piktogram |

##  <a name="BKMK_ExposingColorsForEndUsers"></a> Vystavení barvy pro koncové uživatele

### <a name="overview"></a>Přehled

Někdy budete chtít povolit koncovému uživateli přizpůsobit uživatelské rozhraní, stejně jako při vytváření editoru kódu nebo návrhovou plochu. Nejběžnější způsob je pomocí **nástroje &gt; možnosti** dialogového okna. Pokud měli vysoce specializované uživatelské rozhraní, které vyžaduje speciální ovládací prvky, je nejjednodušší způsob, jak k dispozici přizpůsobení prostřednictvím **písma a barvy** stránky v rámci **prostředí** části dialogového okna. Pro každý prvek, který zveřejníte pro přizpůsobení uživatel může zvolit změnit barvu popředí, pozadí nebo obojí.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Vytváření balíčku VSPackage pro přizpůsobitelné barvy

VSPackage můžete řídit písma a barvy prostřednictvím vlastní kategorie a zobrazení položek na stránce vlastností písma a barvy. Při používání tohoto mechanismu, musí implementovat rozšíření VSPackages [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) rozhraní a jeho přidružené rozhraní.

V zásadě tento mechanismus je možné změnit všechny existující zobrazit položky a kategorie, které je obsahují. Ale by neměly být použít změnit kategorii textový Editor, nebo jeho položky zobrazení. Další informace o kategorii textový Editor, naleznete v tématu [písma a barvy přehled](../font-and-color-overview.md).

Pokud chcete implementovat vlastní kategorie nebo zobrazit položky, musí VSPackage:

- **Vytvořte nebo Identifikujte kategorií v registru.** Implementace rozhraní IDE **písma a barvy** stránku vlastností používá tyto informace se správně dotázat služba podporující dané kategorie.

- **Vytvořte nebo Identifikujte skupiny v registru (volitelné).** Může být užitečné k definování skupiny, která představuje sjednocení dvou nebo více kategorií. Pokud skupina je definována, rozhraní IDE automaticky sloučí podkategorie a distribuuje zobrazení položek v rámci skupiny.

- **Implementace podpora integrované vývojové prostředí.**

- **Zpracování změn písma a barvy.**

#### <a name="to-create-or-identify-categories"></a>K vytvoření nebo určení kategorie

Vytvořit zvláštní druh položky registru kategorie `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` kde `<Category>` je nelokalizovaný název kategorie.

Naplnění registru pomocí dvou hodnot:

| Název | Typ | Data | Popis |
| --- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Vytvoří identifikátor GUID k identifikaci kategorii |
| Balíček | REG_SZ | GUID | Identifikátor GUID služby VSPackage, která podporuje kategorii |

 Služba uvedený v registru musí poskytovat implementaci [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) pro odpovídající kategorii.

#### <a name="to-create-or-identify-groups"></a>Vytvořte nebo Identifikujte skupiny

Vytvořit zvláštní druh položky registru kategorie `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` kde `<group>` je nelokalizovaný název skupiny.

Naplnění registru pomocí dvou hodnot:

| Název | Typ | Data | Popis |
|--- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Vytvoří identifikátor GUID k identifikaci kategorii |
| Balíček | REG_SZ | GUID | Identifikátor GUID služby VSPackage, která podporuje kategorii |

Služba uvedený v registru musí poskytovat implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> pro příslušné skupiny.

![Provádění IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 a_FontAndColorGroup")<br />Provádění `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>K implementaci podpora integrované vývojové prostředí

Implementace [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), který vrátí buď [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) rozhraní nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> rozhraní IDE pro každou kategorii nebo skupině zadaným identifikátorem GUID.

Pro každou kategorii podporuje, VSPackage implementuje samostatnou instanci [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) rozhraní.

Metody implementovány pomocí [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) nezajistil integrované vývojové prostředí s:

- Seznamy zobrazení položek v kategorii

- Lokalizovatelné názvy pro zobrazení položek

- Zobrazení informací pro každého člena kategorie

> [!NOTE]
> Každé kategorie musí obsahovat alespoň jednu položku zobrazení.

Využívá integrovaného vývojového prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> rozhraní definovat sjednocení několik kategorií.

Jeho implementace poskytuje integrované vývojové prostředí s:

- Seznam kategorií, které tvoří danou skupinu

- Přístup k instancím typu [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) podpora jednotlivých kategorií v rámci skupiny

- Názvy zdrojů lokalizovatelných skupin

#### <a name="updating-the-ide"></a>Aktualizuje se rozhraní IDE

Rozhraní IDE ukládá do mezipaměti informace o nastavení písem a barev. Proto po jakékoliv úpravě konfigurace rozhraní IDE písma a barvy zajišťující, že je aktuální mezipaměti je osvědčeným postupem.

Aktualizace mezipaměti se provádí prostřednictvím [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) rozhraní a může být provedena globálně, nebo jenom na vybraných položek.

### <a name="handling-font-and-color-changes"></a>Zpracování změn písma a barvy

Pro podporu správně zabarvení textu, který zobrazí VSPackage, musí služba zabarvení podporující sady VSPackage reagovat na uživatelem iniciované změny prostřednictvím stránky vlastností písma a barvy.

K tomuto účelu VSPackage musí:

- **zpracování událostí generovaných IDE** implementací [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) rozhraní. Integrované vývojové prostředí volá metodu odpovídající následující stránky písma a barev uživatelské úpravy. Například volání [onfontchanged –](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) metodu, pokud je vybrána nového písma.

  **OR**

- **dotazování rozhraní IDE pro změny**. To lze provést prostřednictvím systému implementované [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) rozhraní. I když především pro podporu trvalost, [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) metoda můžete získat informace o písma a barvy pro zobrazení položek. Další informace o nastavení písma a barvy, najdete v článku na webu MSDN [přístup k uložené písmo a barvy nastavení](../accessing-stored-font-and-color-settings.md).

> [!NOTE]
> Ujistěte se, že jsou správné výsledky dotazování, můžete [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) rozhraní k určení, pokud se před voláním metody načítání potřebuje vyprázdnění mezipaměti a aktualizace [IVsFontAndColorStorage ](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) rozhraní.

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

- `"NameID"` = Název lokalizované kategorie v balíčku ID prostředku
- `"ToolWindowPackage"` = Identifikátor GUID balíčku
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` Skutečná hodnota může být nový identifikátor GUID poskytované implementátora je uvedené jenom jako příklad.

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
