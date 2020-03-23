---
title: Barvy a styling pro Visual Studio | Dokumenty společnosti Microsoft
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ceea00a3fa77a9c1106f24f28ac1d5890437b41
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303153"
---
# <a name="colors-and-styling-for-visual-studio"></a>Barvy a styly pro Visual Studio

## <a name="use-color-in-visual-studio"></a>Použití barev v sadě Visual Studio

V sadě Visual Studio se barva používá především jako komunikační nástroj, nikoli pouze jako dekorace. Používejte barvu minimálně a rezervujte ji pro situace, kdy chcete:

- Komunikace významu nebo přidružení (například modifikátory platformy nebo jazyka)

- Upoutat pozornost (například označení změny stavu)

- Zlepšete čitelnost a poskytněte orientační body pro navigaci v ui

- Zvýšit vhodnost

Existuje několik možností pro přiřazení barev prvkům uživatelského rozhraní v sadě Visual Studio. Někdy může být obtížné zjistit, kterou možnost máte použít, nebo jak ji správně používat. Toto téma vám pomůže:

- Seznamte se s různými službami a systémy používanými k definování barev v sadě Visual Studio.

- Vyberte správnou možnost pro daný prvek.

- Správně použijte zvolenou možnost.

> [!NOTE]
> Nikdy hardcode hex, RGB, nebo systémové barvy na prvky uživatelského rozhraní. Použití služeb umožňuje flexibilitu v ladění odstínu. Navíc bez služby nebudete moci využít možnosti přepínání motivů [služby VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Metody pro přiřazení barev prvkům rozhraní sady Visual Studio

Zvolte metodu, která nejlépe vyhovuje vašim prvkům uživatelského rozhraní.

| Vaše ui | Metoda | Co jsou zač? |
| --- | --- | --- |
| Máte vložená nebo samostatná dialogová okna. | **Systémové barvy** | Systémové názvy, které umožňují operačnímu systému definovat barvu a vzhled prvků uživatelského rozhraní, například běžné ovládací prvky dialogového okna. |
| Máte vlastní uživatelské rozhraní, které chcete být konzistentní s celkovým prostředím VS a máte prvky uživatelského rozhraní, které odpovídají kategorii a sémantický význam sdílených tokenů. | **Běžné sdílené barvy** | Existující předdefinované názvy barevných tokenů pro určité prvky uživatelského rozhraní |
| Máte jednotlivé funkce nebo skupinu funkcí a pro podobné prvky neexistuje žádná sdílená barva. | **Vlastní barvy** | Názvy barevných tokenů, které jsou specifické pro oblast a nejsou určeny ke sdílení s jiným uživatelským prostředím |
| Chcete povolit koncovému uživateli přizpůsobit uživatelské rozhraní nebo obsah (například pro textové editory nebo specializované návrháře windows). | **Přizpůsobení koncových uživatelů**<br /><br />**(Dialogové &gt; okno Možnosti nástroje)** | Nastavení definovaná na stránce "Písma a barvy" v dialogovém okně **Možnosti nástrojů &gt; ** nebo na specializované stránce specifické pro jednu funkci ui. |

### <a name="visual-studio-themes"></a>Motivy visual studia

Visual Studio obsahuje tři různé barevné motivy: světlé, tmavé a modré. Detekuje také režim vysokého kontrastu, což je barevný motiv pro celý systém určený pro usnadnění přístupu.

Uživatelé jsou vyzváni k výběru motivu při prvním použití sady Visual Studio a jsou schopni přepnout motivy později přechodem na **nástroje &gt; možnosti &gt; prostředí &gt; obecné** a výběrnového motivu z rozbalovací nabídky "barevný motiv".

Uživatelé mohou také pomocí Ovládacích panelů přepnout celé své systémy do jednoho z několika motivů s vysokým kontrastem. Pokud uživatel vybere motiv s vysokým kontrastem, volič barevného motivu sady Visual Studio již neovlivní barvy v sadě Visual Studio, i když se všechny změny motivu uloží, když uživatel ukončí režim vysokého kontrastu. Další informace o režimu Vysoký kontrast naleznete v [tématu Volba barev s vysokým kontrastem](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Služba VSColor

Visual Studio poskytuje službu barev prostředí, známou jako služba VSColor, která umožňuje svázat barevné hodnoty prvků uživatelského rozhraní s pojmenovanou položkou obsahující barevné hodnoty pro každý motiv sady Visual Studio. Tím je zajištěno, že se barvy automaticky změní tak, aby odrážely aktuální motiv vybraný uživatelem nebo režim vysokého kontrastu systému. Použití služby znamená, že implementace všech změn barev souvisejících s motivem je zpracována na jednom místě a pokud používáte společné sdílené barvy ze služby, vaše ui bude automaticky odrážet nové motivy v budoucích verzích sady Visual Studio.

### <a name="implementation"></a>Implementace

Zdrojový kód sady Visual Studio obsahuje několik souborů definice balíčku, které obsahují seznamy názvů tokenů a příslušné hodnoty barev pro každý motiv. Služba barev čte VSColors definované v těchto souborech definice balíčku. Tyto barvy jsou odkazovány ve značkách XAML nebo `IVsUIShell5.GetThemedColor` v kódu a poté načteny prostřednictvím metody nebo mapování DynamicResource.

### <a name="system-colors"></a>Systémové barvy

Běžné ovládací prvky ve výchozím nastavení odkazují na systémové barvy. Pokud chcete, aby vaše uI používat systémové barvy, jako když vytváříte vložené nebo samostatné dialogové okno, nemusíte nic dělat.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Běžné sdílené barvy ve službě VSColor

Prvky rozhraní by měly odrážet celkové prostředí sady Visual Studio. Opětovným použitím běžných sdílených barev, které jsou vhodné pro komponentu uživatelského rozhraní, kterou navrhujete, zajistíte, že vaše rozhraní je konzistentní s ostatními rozhraními sady Visual Studio a že se barvy automaticky aktualizují při přidání nebo aktualizaci motivů.

Před použitím běžných sdílených barev se ujistěte, že rozumíte správnému použití. Nesprávné použití běžných sdílených barev může vést k nekonzistentnímu, frustrujícímu nebo matoucímu prostředí pro uživatele.

### <a name="user-customizable-colors"></a>Uživatelsky přizpůsobitelné barvy

Viz: [Vystavení barev koncovým uživatelům](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Někdy budete chtít povolit koncovému uživateli přizpůsobit uživatelské rozhraní, například při vytváření editoru kódu nebo návrhové plochy. Přizpůsobitelné komponenty uživatelského prostředí se nacházejí v části **Písma a barvy** v dialogovém okně **Možnosti nástrojů, &gt; ** kde mohou uživatelé změnit barvu popředí, barvu pozadí nebo obojí.

![Dialogové &gt; okno Možnosti nástroje](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Dialogové &gt; okno Možnosti nástroje

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>Služba VSColor

Visual Studio poskytuje službu barev prostředí, která se také nazývá služba VSColor nebo služba barvy prostředí. Tato služba umožňuje svázat barevné hodnoty prvků uživatelského rozhraní s sadou barev název-hodnota obsahující barvy pro každý motiv. Služba VSColor musí být použita pro všechny prvky uživatelského rozhraní, aby se barvy automaticky změnily tak, aby odrážely aktuální motiv vybraný uživatelem, a aby se uživatelské rozhraní vázané na službu barev prostředí integrovala s novými motivy v budoucích verzích sady Visual Studio.

### <a name="how-the-service-works"></a>Jak služba funguje

Služba barev prostředí čte VSColors definované v .pkgdef pro komponentu ui. Tyto VSColors jsou pak odkazuje v XAML značky nebo `IVsUIShell5.GetThemedColor` kód `DynamicResource` a jsou načteny prostřednictvím nebo mapování.

![Architektura barevné služby prostředí](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Architektura barevné služby prostředí

### <a name="accessing-the-service"></a>Přístup ke službě

Existuje několik různých způsobů, jak získat přístup ke službě VSColor, v závislosti na tom, jaký druh barevných tokenů používáte a jaký kód máte.

#### <a name="predefined-environment-colors"></a>Předdefinované barvy prostředí

##### <a name="from-native-code"></a>Z nativního kódu

Prostředí poskytuje službu, která `COLORREF` poskytuje přístup k barvy. Služba/rozhraní je:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

V souboru VSShell80.idl má `__VSSYSCOLOREX` výčet konstanty barev prostředí. Chcete-li jej použít, předejte jako hodnotu `enum __VSSYSCOLOREX` indexu buď jednu z hodnot z dokumentovaných v `GetSysColor`msdn nebo běžné číslo indexu, které přijímá rozhraní API systému Windows, , . Tím získá zpět hodnotu RGB barvy, která by měla být použita v druhém parametru.

Pokud ukládáte pero nebo štětec s `AdviseBroadcastMessages` novou barvou, musíte (mimo `WM_SYSCOLORCHANGE` prostředí `WM_THEMECHANGED` sady Visual Studio) a poslouchat a zprávy.

Chcete-li získat přístup ke službě barev v nativním kódu, provedete volání, které se podobá tomuto:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Hodnoty `COLORREF` vrácené `GetVSSysColorEx()` podle obsahují pouze R,G,B součásti barvy motivu. Pokud položka motivu používá průhlednost, hodnota alfa kanálu se před vrácením zahodí. Proto pokud barva prostředí zájmu je třeba použít v místě, kde je `IVsUIShell5.GetThemedColor` důležité `IVsUIShell2::GetVSSysColorEx`kanálu transparentnosti, měli byste použít místo , jak je popsáno dále v tomto tématu.

##### <a name="from-managed-code"></a>Ze spravovaného kódu

Přístup ke službě VSColor prostřednictvím nativního kódu je poměrně jednoduchý. Pokud však pracujete prostřednictvím spravovaného kódu, může být určení způsobu použití služby složité. S ohledem na to je zde fragment kódu Jazyka C#, který tento proces prokazuje:

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

##### <a name="from-wpf-ui"></a>Z wpf ui

Můžete svázat s barvami sady Visual Studio `ResourceDictionary`prostřednictvím hodnot exportovaných do aplikace . Níže je uveden příklad použití prostředků z tabulky barev a vazby na data písem prostředí v XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Pomocné třídy a metody spravovaného kódu

Pro spravovaný kód obsahuje knihovna`Microsoft.VisualStudio.Shell.12.0.dll`rozhraní Managed Package Framework prostředí ( ) několik pomocných tříd usnadňujících použití tematických barev.

Pomocné metody ve `Microsoft.VisualStudio.Shell.VsColors` třídě v `GetThemedGDIColor()` MPF zahrnují a `GetThemedWPFColor()`. Tyto pomocné metody vrátí hodnotu barvy `System.Drawing.Color` položky motivu jako nebo `System.Windows.Media.Color`, které mají být použity v WinForms nebo WPF UI.

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

Třídu lze také získat identifikátory VSCOLOR pro daný klíč prostředku wpf barvy nebo naopak.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Metody třídy `VsColors` dotaz u služby VSColor vrátit hodnotu barvy pokaždé, když jsou vyvolány. Chcete-li získat `System.Drawing.Color`hodnotu barvy jako , alternativou s `Microsoft.VisualStudio.PlatformUI.VSThemeColor` lepším výkonem je místo toho použít metody třídy, která ukládá hodnoty barev získané ze služby VSColor. Třída se interně přihlásí k událostem všesměrového vysílání prostředí a zahodí hodnotu uloženou v mezipaměti, když dojde k události změny motivu. Také třída poskytuje . NET-přátelské události přihlásit se ke změnám motivu. Pomocí `ThemeChanged` události přidejte novou obslužnou rutinu `GetThemedColor()` a `ThemeResourceKeys` pomocí metody můžete získat hodnoty barev pro zajímavé. Ukázkový kód může vypadat takto:

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>Volba barev S vysokým kontrastem

### <a name="overview"></a>Přehled

Systém Windows používá několik vysoce kontrastních motivů na úrovni systému, které zvyšují barevný kontrast textu, pozadí a obrázků, takže prvky vypadají na obrazovce odlišněji. Z důvodů usnadnění přístupu je důležité, aby prvky rozhraní sady Visual Studio správně reagovaly, když uživatelé přepnou na motiv s vysokým kontrastem.

Pro motivy s vysokým kontrastem lze použít pouze několik systémových barev. Při výběru názvů systémových barev si zapamatujte následující tipy:

- **Zvolte systémové barvy, které mají stejný sémantický význam** jako prvek, který zbarvíte. Pokud například vybíráte pro text v okně vysoce kontrastní barvu, použijte WindowText a not ControlText.

- **Vyberte si nové prostředí / pozadí dvojice** dohromady, nebo nebudete mít jistotu, že vaše volba barev bude fungovat ve všech high contrast témata.

- **Určete, které části vašeho hlavního nastavení jsou nejdůležitější, a ujistěte se, že oblasti obsahu budou vyčnívat.** Ztratíte mnoho detailů, které by jemné rozdíly v barevném odstínu normálně rozlišovaly, takže použití silných okrajových barev je společné pro definování oblastí obsahu, protože neexistují žádné barevné varianty pro různé oblasti obsahu.

### <a name="system-color-set"></a>Systémová barevná sada

Tabulka na [WPF Team Blog: SystemColors Reference](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) označuje úplnou sadu názvů systémových barev a odpovídající odstíny zobrazené v každém motivu.

Při použití této omezené sady barev v ui *se očekává, že ztratíte jemné detaily, které byly přítomny v "normální" motivy*. Zde je příklad ui s jemnými šedými barvami, které se používají k rozlišení oblastí v okně nástroje. Při spárování se stejným oknem zobrazeným v režimu vysoký kontrast můžete vidět, že všechna pozadí mají stejný odstín a ohraničení těchto oblastí je označeno pouze ohraničením:

![Příklad ztráty jemných detailů ve vysokém kontrastu](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Příklad ztráty jemných detailů ve vysokém kontrastu

#### <a name="choosing-text-colors-in-an-editor"></a>Výběr barev textu v editoru

Obarvený text se používá v editoru nebo na návrhové ploše k označení významu, například umožňuje snadnou identifikaci skupin podobných položek. V motivu vysoký kontrast však nemáte možnost rozlišovat mezi více než třemi barvami textu. WindowText, GrayText a HotTrackText jsou jediné barvy dostupné na površích WindowBackground. Vzhledem k tomu, že nelze použít více než tři barvy, pečlivě zvolte nejdůležitější rozdíly, které chcete zobrazit v režimu vysoký kontrast.

Odstíny pro každý z názvů tokenů povolených na povrchu editoru, jak se zobrazují v každém motivu s vysokým kontrastem:

![Porovnání editoru s vysokým kontrastem](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Porovnání editoru s vysokým kontrastem

Příklady povrchu editoru v modrém motivu:

![Motiv Editor v modré barvě](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Motiv Editor v modré barvě

![Motiv Editor s vysokým kontrastem #1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Motiv Editor s vysokým kontrastem #1

### <a name="usage-patterns"></a>Vzorce použití

Mnoho běžných prvků uživatelského rozhraní již má definované barvy s vysokým kontrastem. Tyto vzory použití můžete odkazovat při výběru vlastních názvů barev systému, takže prvky uživatelského rozhraní jsou konzistentní s podobnými součástmi.

| Barva systému | Využití |
| --- | --- |
| Aktivní titulek | - Aktivní IDE a rafted okno tlačítko glyfy na vznášedlo a stiskněte<br />- Titulní lišta pozadí pro IDE a rafted okna<br />- Výchozí pozadí stavového řádku |
| ActiveCaptionText | - Aktivní IDE a rafted okna pro titulní panel popředí (text a glyfy)<br />- Pozadí a hranice aktivních okenních tlačítek na vznášet a stiskněte |
| Řízení | - Combo box, drop-down seznam, a řízení vyhledávání výchozí a zakázané pozadí, včetně drop-down tlačítko<br />- Dock cílové tlačítko pozadí<br />- Pozadí panelu příkazů<br />- Pozadí okna nástroje |
| ControlDark | - IDE pozadí<br />- Oddělovače menu a panelu příkazů<br />- Ohraničení panelu příkazů<br />- Stíny menu<br />- Karta okna nástroje výchozí a jevem ohraničení a oddělovač<br />- Dokument dobře přetečení tlačítko pozadí<br />- Dok cíl glyf hranice |
| ControlDarkDark |- Nezaostřené, vybrané okno karty dokumentu |
| Řídicí světlo |- Automatické skrytí ohraničení karty<br />- Pole se seznamem a ohraničení rozevíracího seznamu<br />- Dock cílové pozadí a hranice |
| ControlLightLight | - Vybraná, zaměřená prozatímní hranice |
| ControlText | - Pole se seznamem a rozevírací seznam glyfů<br />- Okno nástroje nevybraný text karty |
| Šedý text |- Pole se seznamem a rozevírací seznam zakázané ohraničení, rozevírací glyf, text a text položky nabídky<br />- Zakázaný text nabídky<br />- Search control 'možnosti vyhledávání' hlavičkový text<br />- Oddělovač kontrolních řezů vyhledávání |
| Zvýraznit | - Všechny vznášet a stisknuté pozadí a ohraničení, s výjimkou pole se seznamem rozevírací tlačítko pozadí a dokument dobře přetečení tlačítko hranice<br />- Pozadí vybrané položky |
| ZvýraznitText | - Všechny vznášet a lisované popředí (text a glyfy)<br />- Zaostřené okno nástroje a ovládací prvek okna karty dokumentu popředí<br />- Zaostřené okno okna okna záhlaví ohraničení<br />- Focused, vybrané prozatímní kartu popředí<br />- Dokument dobře přetečení tlačítko hranice na vznášet a stiskněte tlačítko<br />- Vybrané ohraničení ikony|
| HotTrack | - Posuvník palec pozadí a ohraničení na stisknutí<br />- Posuvník šipka glyf na stisknutí |
| Neaktivnítitulek | - Neaktivní IDE a rafted okno tlačítko glyfy na hover<br />- Titulní lišta pozadí pro IDE a rafted okna<br />- Zakázané pozadí řízení vyhledávání |
| Neaktivní titulektextu | - Neaktivní IDE a rafted okna záhlaví popředí (text a glyfy)<br />- Neaktivní okna tlačítka pozadí a ohraničení na vznášet<br />- Nezaostřené okno nástroje pozadí a ohraničení<br />- Zakázané řízení vyhledávání popředí |
| Nabídka | - Pozadí rozbalovací nabídky<br />- Zkontrolovat a zdravotně zkontrolovat zaškrtnutí pozadí |
| Text nabídky | - Ohraničení rozevíracího lístku<br />- Kontrolní značky<br />- Menu glyfy<br />- Text rozevíracího menu<br />- Vybrané ohraničení ikony |
| Posuvník | - Posuvník a posuvník šipka pozadí, všechny stavy |
| Okno | - Auto-skrýt kartu pozadí<br />- Menu bar a příkaz police pozadí<br />- Nezaostřené nebo nevybrané pozadí karty okna dokumentu a ohraničení dokumentu, pro otevřené i prozatímní karty<br />- Nezaostřené pozadí záhlaví okna nástroje<br />- Pozadí karty okna nástroje, vybrané i nevybrané |
| Rámeček okna | - IDE hranice |
| Text okna | - Auto-skrýt kartu popředí<br />- Vybrané okno nástroje v popředí<br />- Nezaostřené okno dokumentu kartu a nezaostřené nebo nevybrané prozatímní kartu popředí<br />- Výchozí popředí stromového zobrazení a najeďte na nevybraný glyf<br />- Okno nástroje vybrané ohraničení karty<br />- Posuvník palec pozadí, ohraničení a glyf |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>Vystavení barev koncovým uživatelům

### <a name="overview"></a>Přehled

Někdy budete chtít povolit koncovému uživateli přizpůsobit uživatelské rozhraní, například při vytváření editoru kódu nebo návrhové plochy. Nejběžnější způsob, jak to provést, je pomocí dialogového **okna Možnosti &gt; nástrojů.** Pokud nemáte vysoce specializované uživatelské rozhraní, které vyžaduje speciální ovládací prvky, nejjednodušší způsob, jak prezentovat vlastní nastavení, je prostřednictvím stránky **Písma a barvy** v části **Prostředí** v dialogovém okně. Pro každý prvek, který zveřejňujete pro vlastní nastavení, může uživatel změnit barvu popředí, barvu pozadí nebo obojí.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Vytvoření balíčku VSPackage pro přizpůsobitelné barvy

A VSPackage můžete ovládat písma a barvy prostřednictvím vlastních kategorií a zobrazení položek na stránce vlastnosti Písma a barvy. Při použití tohoto mechanismu VSPackages musí implementovat [rozhraní IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) a jeho přidružené rozhraní.

V zásadě tento mechanismus lze upravit všechny existující položky zobrazení a kategorie, které je obsahují. Však by neměl být použit k úpravě kategorie editoru textu nebo jeho zobrazení položek. Další informace o kategorii Textový editor naleznete v tématu [Přehled písem a barev](/visualstudio/extensibility/font-and-color-overview?view=vs-2015).

Chcete-li implementovat vlastní kategorie nebo zobrazit položky, musí VSPackage:

- **Vytvořte nebo identifikujte kategorie v registru.** IDE implementace **písma a barvy** stránky vlastnosti používá tyto informace správně dotaz na službu podporující danou kategorii.

- **Vytvořte nebo identifikujte skupiny v registru (volitelné).** Může být užitečné definovat skupinu, která představuje sjednocení dvou nebo více kategorií. Pokud je definována skupina, ide automaticky sloučí podkategorie a distribuuje položky zobrazení v rámci skupiny.

- **Implementujte podporu ide.**

- **Zpracovat změny písma a barvy.**

#### <a name="to-create-or-identify-categories"></a>Vytvoření nebo identifikace kategorií

Vytvořte zvláštní typ položky `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` registru `<Category>` kategorie pod kde je nelokalizovaný název kategorie.

Naplňte registr dvěma hodnotami:

| Name (Název) | Typ | Data | Popis |
| --- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Identifikátor GUID vytvořený k identifikaci kategorie |
| Balíček | REG_SZ | GUID | Identifikátor GUID služby VSPackage, který podporuje kategorii |

 Služba zadaná v registru musí poskytovat implementaci [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) pro odpovídající kategorii.

#### <a name="to-create-or-identify-groups"></a>Vytvoření nebo identifikace skupin

Vytvořte zvláštní typ položky `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` registru `<group>` kategorie pod kde je nelokalizovaný název skupiny.

Naplňte registr dvěma hodnotami:

| Name (Název) | Typ | Data | Popis |
|--- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Identifikátor GUID vytvořený k identifikaci kategorie |
| Balíček | REG_SZ | GUID | Identifikátor GUID služby VSPackage, který podporuje kategorii |

Služba zadaná v registru musí <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> poskytovat implementaci pro odpovídající skupinu.

![Implementace IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Provádění`IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Implementace podpory ide

Implementovat [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), který vrátí buď [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) rozhraní nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> rozhraní ide pro každou kategorii nebo skupiny GUID zadaný.

Pro každou kategorii, kterou podporuje, VSPackage implementuje samostatnou instanci rozhraní [IVsFontAndColorDefaults.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)

Metody implementované prostřednictvím [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) musí poskytnout ide s:

- Seznamy zobrazovaných položek v kategorii

- Lokalizovatelné názvy pro zobrazované položky

- Zobrazit informace pro každého člena kategorie

> [!NOTE]
> Každá kategorie musí obsahovat alespoň jednu položku zobrazení.

Rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> používá rozhraní k definování sjednocení několika kategorií.

Jeho implementace poskytuje ide s:

- Seznam kategorií, které tvoří danou skupinu

- Přístup k instancím [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) podporujících každou kategorii ve skupině

- Lokalizovatelné názvy skupin

#### <a name="updating-the-ide"></a>Aktualizace rozhraní IDE

IDE ukládá informace o nastavení písma a barev. Proto po jakékoli změně konfigurace písma a barvy ide, zajištění, že mezipaměť je aktuální je osvědčeným postupem.

Aktualizace mezipaměti se provádí prostřednictvím rozhraní [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) a lze provést globálně nebo pouze na vybraných položkách.

### <a name="handling-font-and-color-changes"></a>Zpracování změn písma a barev

Chcete-li správně podporovat vybarvení textu, který zobrazí VSPackage, vybarvení služba podporující VSPackage musí reagovat na změny iniciované uživatelem provedené prostřednictvím fonty a barvy vlastnosti stránky.

Chcete-li to provést, VSPackage musí:

- **zpracování událostí generovaných ide** implementací rozhraní [IVsFontAndColorEvents.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) Rozhraní IDE volá příslušnou metodu následující změny uživatele písma a barvy stránky. Například volá [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) metoda, pokud je vybráno nové písmo.

  **Nebo**

- **dotazování ide pro změny**. To lze provést prostřednictvím systémem implementovaného rozhraní [IVsFontAndColorStorage.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) Ačkoli především pro podporu trvalosti, [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) metoda můžete získat informace o písmu a barvě pro zobrazení položek. Další informace o nastavení písem a barev naleznete v článku MSDN [Přístup k uloženým nastavením písma a barev](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015).

> [!NOTE]
> Chcete-li zajistit, že výsledky dotazování jsou správné, použijte [rozhraní IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) k určení, zda vyprázdnění mezipaměti a aktualizace jsou potřebné před voláním metody načítání [rozhraní IVsFontAndColorStorage.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrace vlastních písem a barev Kategorie bez implementace rozhraní

Následující příklad kódu ukazuje, jak zaregistrovat vlastní písmo a barvu Kategorie bez implementace rozhraní:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Pro tento příklad kódu:

- `"NameID"`= ID prostředku lokalizovaného názvu kategorie v balíčku
- `"ToolWindowPackage"`= IDENTIFIKÁTOR GUID balíčku
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`je pouze příklad a skutečná hodnota může být nový identifikátor GUID poskytnutý implementátorem.

### <a name="set-the-font-and-color-property-category-guid"></a>Nastavení identifikátoru GUID vlastnosti Písmo a barva

Příklad kódu níže ukazuje nastavení kategorie GUID.

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
