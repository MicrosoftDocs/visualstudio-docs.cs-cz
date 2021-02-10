---
title: Písma a formátování pro Visual Studio | Microsoft Docs
description: Přečtěte si o písmech a formátování pro nové funkce, které navrhujete pro Visual Studio, včetně toho, jak používat písmo prostředí.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f1b9b7e7f20c93cd2067d1210245da8ef6ce8813
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952028"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Písma a formátování pro Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> Písmo prostředí
 Všechna písma v sadě Visual Studio musí být vystavena uživateli pro přizpůsobení. To se primárně provádí pomocí stránky **písma a barvy** v dialogovém okně **nástroje > možnosti** . Existují tři hlavní kategorie nastavení písem:

- **Písmo prostředí** – primární písmo pro integrované vývojové prostředí (IDE), které se používá pro všechny prvky rozhraní, včetně dialogových oken, nabídek, oken nástrojů a oken dokumentů. Ve výchozím nastavení je písmo prostředí svázáno se systémovým písmem, které se v aktuálních verzích Windows zobrazuje jako 9 bodů Segoe UI. Použití jednoho písma pro všechny prvky rozhraní pomáhá zajistit konzistentní vzhled písma v rámci prostředí IDE.

- **Textový editor** – prvky, které jsou na kódu a další textové editory, lze přizpůsobit na stránce textový editor v **nabídce nástroje > možnosti**.

- **Konkrétní kolekce** – okna návrháře, která nabízejí přizpůsobení uživatelského rozhraní, mohou vystavovat písma specifická pro svou návrhovou plochu na jejich vlastní stránce nastavení v části **nástroje > možnosti**.

### <a name="editor-font-customization-and-resizing"></a>Přizpůsobení a změna velikosti písma editoru
 Uživatelé často zvětší nebo zmenší velikost nebo barvu textu v editoru podle jejich předvolby, a to nezávisle na obecném uživatelském rozhraní. Vzhledem k tomu, že se písmo prostředí používá pro prvky, které se mohou objevit v rámci nebo jako součást editoru nebo návrháře, je důležité poznamenat očekávané chování při změně jedné z těchto klasifikací písma.

 Při vytváření prvků uživatelského rozhraní, které se zobrazí v editoru, ale nejsou součástí *obsahu*, je důležité použít písmo prostředí a nikoli text písma, aby se prvky měnily předvídatelným způsobem.

1. V případě textu kódu v editoru změňte velikost pomocí písma textu kódu a nastavte reakci na úroveň přiblížení textu editoru.

2. Všechny ostatní prvky rozhraní by měly být svázané s nastavením písma prostředí a reagovat na všechny globální změny v prostředí. To zahrnuje (mimo jiné):

    - Text v místních nabídkách

    - Text v editoru, jako je například text nabídky žárovky, podokno rychlého hledání a přechod na podokno

    - Popisek textu v dialogových oknech, například **najít v souborech** nebo **Refaktorovat**

### <a name="accessing-the-environment-font"></a>Přístup k písma prostředí
 V nativním kódu nebo kódu WinForms je k prostředí možné přistupovat voláním metody `IUIHostLocale::GetDialogFont` po dotazování rozhraní ze `SID_SUIHostLocale` služby.

 Pro Windows Presentation Foundation (WPF) odvodíte třídu vašeho dialogového okna z `DialogWindow` třídy Shell namísto `Window` třídy WPF.

 Kód v jazyce XAML vypadá takto:

```xaml
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>
```

Kód na pozadí:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Nahraďte `Microsoft.VisualStudio.Shell.11.0` aktuální verzí knihovny MPF dll.)

 Chcete-li zobrazit dialogové okno, zavolejte `ShowModal()` na třídu znovu " `ShowDialog()` ". `ShowModal()` nastaví v prostředí správný modální stav, zajistí, aby se dialogové okno nacentroval na střed nadřazeného okna a tak dále.

 Kód je následující:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` Vrátí bool? (hodnota Nullable) s hodnotou `DialogResult` , kterou lze použít v případě potřeby. Návratová hodnota má hodnotu true, pokud bylo dialogové okno zavřeno s **OK**.

 Pokud potřebujete zobrazit některé uživatelské rozhraní WPF, které není dialog a je hostováno vlastním, jako je `HwndSource` místní okno nebo podřízené okno WPF v nadřazeném okně Win32/WinForms, budete muset nastavit `FontFamily` a `FontSize` v kořenovém prvku prvku WPF. (Prostředí nastaví vlastnosti v hlavním okně, ale nebudou zděděné za a `HWND` ). Prostředí poskytuje prostředky, na které lze vlastnosti svázat, například takto:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> Formátování (škálování/tučné) – referenční informace
 Některá dialogová okna vyžadují, aby určitý text byl tučný, nebo jinou než velikost písma prostředí. Dříve byla písma větší než písmo prostředí kódována jako " `environment font +2` " nebo podobná. Použití poskytnutých fragmentů kódu bude podporovat monitory s vysokým rozlišením DPI a zajistí, aby se text zobrazoval vždy ve správné velikosti a váhy (například Light nebo Semilight).

> [!NOTE]
> Než použijete formátování, ujistěte se, že budete postupovat podle pokynů, které najdete ve [stylu textu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle). * *

 Chcete-li změnit velikost písma prostředí, nastavte styl TextBlock nebo popisku tak, jak je uvedeno. Každý z těchto fragmentů kódu, který se správně používá, vygeneruje správné písmo, včetně odpovídající velikosti a variací váhy.

 Kde " `vsui` " je odkaz na obor názvů `Microsoft.VisualStudio.Shell` :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% písmo prostředí + světlo

**Zobrazuje se jako:** 34 PT Segoe UI Light.

::: moniker range="vs-2017"

**Použijte pro:** (vzácné) jedinečné BRANDINGOVÉ uživatelské rozhraní, například na úvodní stránce.

::: moniker-end

::: moniker range=">=vs-2019"

**Použijte pro:** (vzácné) jedinečné uživatelské rozhraní značky

::: moniker-end

**Procedurální kód:** Kde `textBlock` je dříve definovaný TextBlock a `label` je dříve definovaný popisek:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** Nastavte styl TextBlock nebo popisku, jak je znázorněno na obrázku.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% písmo prostředí + světlo
 **Vypadá takto:** 28 PT Segoe UI světlé **použití pro:** názvy dialogových oken velkých podpisů, hlavní nadpis v sestavách

 **Procedurální kód:** Kde `textBlock` je dříve definovaný TextBlock a `label` je dříve definovaný popisek:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** Nastavte styl TextBlock nebo popisku, jak je znázorněno na obrázku.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% Font prostředí + Semilight
 **Vypadá takto:** 18 bodů Segoe UI Semilight **použití pro:** dílčí hlavičky, názvy v malých a středně velkých dialogových oknech.

 **Procedurální kód:** Kde `textBlock` je dříve definovaný TextBlock a `label` je dříve definovaný popisek:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** Nastavte styl TextBlock nebo popisku, jak je znázorněno níže:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% písma prostředí
 **Vypadá takto:** 14 b Segoe UI **použít pro:** NADPISY oddílů v uživatelském rozhraní a sestavách dokumentu

 **Procedurální kód:** Kde `textBlock` je dříve definovaný TextBlock a `label` je dříve definovaný popisek:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** Nastavte styl TextBlock nebo popisku, jak je znázorněno níže:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133% písma prostředí
 **Vypadá takto:** 12 bodů Segoe UI **použít pro:** menší podpoložky v dialogových oknech PODPISŮ a v uživatelském rozhraní dokumentu.

 **Procedurální kód:** Kde `textBlock` je dříve definovaný TextBlock a `label` je dříve definovaný popisek:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** Nastavte styl TextBlock nebo popisku, jak je znázorněno níže:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% písma prostředí
 **Zobrazuje se jako:** 11 bodů Segoe UI **použít pro:** nadpisy oddílů v dialogových oknech podpisů, horních uzlech ve stromovém zobrazení a svislém procházení karet.

 **Procedurální kód:** Kde `textBlock` je dříve definovaný TextBlock a `label` je dříve definovaný popisek:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** Nastavte styl TextBlock nebo popisku, jak je znázorněno níže:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Písmo prostředí + tučné
 **Zobrazuje se jako:** tučné 9 pt Segoe UI **použít pro:** popisky a podhlaví v dialogových oknech podpisů, sestavách a v uživatelském rozhraní dokumentu.

 **Procedurální kód:** Kde `textBlock` je dříve definovaný TextBlock a `label` je dříve definovaný popisek:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** Nastavte styl TextBlock nebo popisku, jak je znázorněno níže:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Lokalizovatelné styly
 V některých případech musí lokalizovat upravovat styly písem pro různá národní prostředí, jako je například odebrání tučného písma z textu pro východoasijské jazyky. Aby bylo možné zajistit lokalizaci stylů písem, musí být tyto styly v souboru. resx. Nejlepším způsobem, jak dosáhnout tohoto a stále upravovat styly písem v návrháři formuláře sady Visual Studio, je explicitně nastavit styly písma v době návrhu. I když se tím vytvoří plný objekt Font a může se zdát, že dojde k přerušení dědičnosti nadřazených písem, použije se k nastavení písma jenom vlastnost FontStyle.

 Řešením je zapojit událost formuláře dialogového okna `FontChanged` . V `FontChanged` události Projděte všechny ovládací prvky a ověřte, zda je jejich písmo nastaveno. Pokud je nastaveno, změňte ho na nové písmo založené na písmu formuláře a na předchozí styl písma ovládacího prvku. Příkladem v kódu je:

```csharp
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 Pomocí tohoto kódu garantujeme, že při aktualizaci písma formuláře se budou aktualizovat i písma ovládacích prvků. Tato metoda by měla být volána také z konstruktoru formuláře, protože dialogové okno může selhat při získání instance `IUIService` a `FontChanged` událost nebude nikdy zavolána. Připojení `FontChanged` umožní dialogům dynamicky vybrat nové písmo, a to i v případě, že už je dialogové okno otevřené.

### <a name="testing-the-environment-font"></a>Testování písma prostředí
 Chcete-li zajistit, že vaše uživatelské rozhraní používá písmo prostředí a respektuje nastavení velikosti, otevřete **nástroje > možnosti > prostředí > písma a barvy** a v rozevírací nabídce "Zobrazit nastavení pro:" vyberte možnost "písmo prostředí".

 ![Nastavení písem a barev v &gt; dialogovém okně Možnosti nástrojů](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201 – a_OptionsFonts")<br />Nastavení písem a barev v &gt; dialogovém okně Možnosti nástrojů

 Nastavte písmo na něco jiného než výchozí. Aby bylo zřejmé, které uživatelské rozhraní se neaktualizuje, vyberte písmo s serifs (například "Times New Roman") a nastavte velmi velkou velikost. Pak otestujte uživatelské rozhraní, abyste se ujistili, že bude respektovat prostředí. Tady je příklad v dialogu s licencí:

 ![Příklad textu uživatelského rozhraní, které nerespektuje písmo prostředí](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201 – b_WrongFontDialog")<br />Příklad textu uživatelského rozhraní, které nerespektuje písmo prostředí

 V tomto případě se nerespektuje písmo "informace o uživateli" a informace o produktu. V některých případech to může být explicitní volba návrhu, ale může se jednat o chybu, pokud není explicitní písmo zadáno jako součást specifikace Redline.

 Pokud chcete písmo obnovit, klikněte na "použít výchozí" v části **nástroje > možnosti > prostředí > písma a barvy**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> Styl textu
 Styl textu odkazuje na velikost písma, váhu a velikost písmen. Pokyny k implementaci najdete v tématu [Písmo prostředí](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Velikost písmen textu

#### <a name="all-caps"></a>Všechna velká
 Nepoužívejte pro názvy ani popisky v aplikaci Visual Studio všechna písmena.

#### <a name="all-lowercase"></a>Všechna malá
 Pro názvy nebo popisky v aplikaci Visual Studio Nepoužívejte všechna malá písmena.

#### <a name="sentence-and-title-case"></a>Případ věty a nadpisu
 Text v aplikaci Visual Studio by měl v závislosti na situaci použít buď velká písmena v nadpisech, nebo velká a malá písmena.

|Použít velká a malá písmena pro:|Použít velká a malá písmena pro:|
|-------------------------|----------------------------|
|Názvy dialogových oken|Popisky|
|Skupinové rámečky|Zaškrtávací políčka|
|Položky nabídky|Přepínače|
|Položky místní nabídky|Položky seznamu|
|Tlačítka|Stavové řádky|
|Popisky tabulky||
|Záhlaví sloupců||
|Popisy||

##### <a name="title-case"></a>Případ názvu
 Název Case je stylem, ve kterém jsou první písmena většiny nebo všech slov v rámci fráze velká. V aplikaci Visual Studio se pro mnoho položek používá název Case, včetně:

- **Popisy.** Příklad: náhled vybraných položek

- **Záhlaví sloupců** Příklad: "systémová odezva"

- **Položky nabídky** Příklad: "Uložit vše"

  Při použití titulního případu se jedná o pokyny, kdy velká písmena velkých písmen a kdy je ponechají:

|Velká písmena|Komentáře a příklady|
|---------------|---------------------------|
|Všechna podstatná jména||
|Všechny akce|Včetně "is" a dalších forem "to je".|
|Všechny příslovce|Včetně "než" a "when"|
|Všechna přídavná jména|Včetně "This" a "to"|
|Všechna podstatná jména|Včetně possessive "jeho", a také "IT", "smluvní strany" pronoun "IT" a operace "je".|
|První a poslední slova bez ohledu na část řeči||
|Předpozice, které jsou součástí fráze příkazu|"Ukončení všech oken" nebo "vypnutí systému"|
|Všechna písmena akronymu|HTML, XML, URL, IDE, RGB|
|Druhé slovo ve složeném slově, pokud se jedná o podstatné jméno nebo náležité jméno, nebo pokud má tato slova stejnou váhu|Křížové odkazy, software před prodejem, přístup pro čtení a zápis, Run-Time|

|Malá písmena|Příklady|
|---------------|--------------|
|Druhé slovo ve složeném slově, pokud je to jiná část řeči nebo participle úpravou prvního slova|Postupy, odhlášení|
|Články, pokud jedna z nich není první slovo v nadpisu|a, an, the|
|Souřadnice souřadnic|a, ale, pro, nebo|
|Předpozice slov se čtyřmi nebo méně písmeny mimo slovesnou frázi|do, jako pro, mimo, na|
|"Do" při použití v nekonečnou frázi|Jak naformátovat pevný disk|

##### <a name="sentence-case"></a>Případ věty
 Případ věty je standardní metodou psaní velkých písmen pro psaní, při které je jenom první slovo věty velkými písmeny, a to I s případnými podstatnými jmenami a pronoun "I". Obecně platí, že velká písmena jsou pro každý celosvětovou cílovou skupinu jednodušší, zejména když bude obsah přeložen počítačem. Použít velká a malá písmena pro:

1. **Zprávy stavového řádku.** Jedná se o jednoduché, krátké a poskytování informací o stavu. Příklad: "načítání souboru projektu"

2. **Všechny ostatní prvky uživatelského rozhraní**, včetně popisků, zaškrtávacích políček, přepínačů a položek seznamu Příklad: "vybrat všechny položky v seznamu"

### <a name="text-formatting"></a>Formátování textu
 Výchozí formátování textu v Visual Studio 2013 je řízeno pomocí [písma prostředí](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Tato služba pomáhá zajistit konzistentní vzhled písem v rámci integrovaného vývojového prostředí (IDE) a je nutné ho použít k zajištění konzistentního prostředí pro vaše uživatele.

 Výchozí velikost používaná službou písem sady Visual Studio pochází ze systému Windows a zobrazuje se jako 9 bodů.

 Můžete použít formátování pro písmo prostředí. Toto téma popisuje, jak a kde použít styly. Informace o implementaci najdete v tématu [Písmo prostředí](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Tučný text
 Tučný text se v aplikaci Visual Studio používá zřídka a měl by být vyhrazený pro:

- popisky dotazů v průvodcích

- určení aktivního projektu v Průzkumník řešení

- přepsané hodnoty v okně nástrojů vlastnosti

- určité události v rozevíracích seznamech editoru Visual Basic

- obsah generovaný serverem v osnově v dokumentu pro webové stránky

- Záhlaví oddílů v komplexním dialogovém okně nebo v uživatelském rozhraní návrháře

#### <a name="italics"></a>Kurzíva
 Visual Studio nepoužívá kurzívu nebo tučný text kurzívu.

#### <a name="color"></a>Barva

- Modrá je vyhrazena pro hypertextové odkazy (navigace a příkazy) a nikdy by neměla být používána pro orientaci.

- Větší nadpisy (písmo prostředí × 155% nebo vyšší) mohou být pro tyto účely barevné:

  - Poskytnutí vizuálního odvolání pro podpis uživatelského rozhraní sady Visual Studio

  - Volání pozornosti do konkrétní oblasti

  - Nabídka normální barvy textu v tmavém šedém/černém prostředí

- Barva v nadpisech by měla využít existující barvy značky sady Visual Studio, hlavně hlavní fialovou, #FF68217A.

- Při použití barev v nadpisech musíte dodržovat [pokyny k barvě Windows](/windows/desktop/uxguide/vis-color), včetně poměru kontrastu a dalších otázek dostupnosti.

### <a name="font-size"></a>Velikost písma
 Návrh uživatelského rozhraní sady Visual Studio nabízí světlejší vzhled s více prázdnými znaky. Pokud je to možné, aplikace Chrome a záhlaví se snížily nebo odeberou. I když je hustota informací v aplikaci Visual Studio požadavkem, stále je důležitá typografie s důrazem na otevřené mezery mezi řádky a variací velikostí a vah písma.

 Následující tabulky obsahují podrobné informace o návrhu a vizuální příklady pro zobrazení písem použitá v aplikaci Visual Studio. Některé variace písma displeje mají velikost i váhu, například Semilight nebo Light, kódované na jejich vzhled.

 Fragmenty kódu implementace pro všechna zobrazovaná písma se dají najít v [odkazu formátování (škálování/tučné)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).

#### <a name="375-environment-font--light"></a>375% písmo prostředí + světlo

|Využití|Příznaky|
|-|-|
|**Použití:** Časté. Jenom jedinečné uživatelské rozhraní v brandingu<br /><br /> **Postup**<br /><br /> – Použít případ začátku věty<br />-Vždycky používat světlou váhu<br /><br /> **Ne:**<br /><br /> – Použijte pro jiné uživatelské rozhraní než podpisové uživatelské rozhraní, jako je úvodní stránka.<br />– Tučné, kurzíva nebo Tučná kurzíva<br />-Použít pro text zprávy<br />-Použít v oknech nástrojů|**Zobrazuje se jako:** 34 PT Segoe UI Light.<br /><br /> **Příklad vizuálu:**<br /><br /> *Aktuálně se nepoužívá. Lze použít na úvodní stránce sady Visual Studio 2017.*|

#### <a name="310-environment-font--light"></a>310% písmo prostředí + světlo

::: moniker range="vs-2017"

|Využití|Příznaky|
|-|-|
|**Využívání**<br /><br /> – Větší nadpis v dialogových oknech podpisu<br />– Záhlaví hlavní sestavy<br /><br /> **Postup**<br /><br /> – Použít případ začátku věty<br />-Vždycky používat světlou váhu<br /><br /> **Ne:**<br /><br /> – Použijte pro jiné uživatelské rozhraní než podpisové uživatelské rozhraní, jako je úvodní stránka.<br />– Tučné, kurzíva nebo Tučná kurzíva<br />-Použít pro text zprávy<br />-Použít v oknech nástrojů|**Zobrazuje se jako:** 28 bodů Segoe UI Light.<br /><br /> **Příklad vizuálu:**<br /><br /> ![Příklad 310% písma prostředí &#43; světlý nadpis](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 – a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|Využití|Příznaky|
|-|-|
|**Využívání**<br /><br /> – Větší nadpis v dialogových oknech podpisu<br />– Záhlaví hlavní sestavy<br /><br /> **Postup**<br /><br /> – Použít případ začátku věty<br />-Vždycky používat světlou váhu<br /><br /> **Ne:**<br /><br /> – Použijte pro jiné uživatelské rozhraní než Signature.<br />– Tučné, kurzíva nebo Tučná kurzíva<br />-Použít pro text zprávy<br />-Použít v oknech nástrojů|**Zobrazuje se jako:** 28 bodů Segoe UI Light.<br /><br /> **Příklad vizuálu:**<br /><br /> ![Příklad 310% písma prostředí &#43; světlý nadpis](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 – a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% Font prostředí + Semilight

|Využití|Příznaky|
|-|-|
|**Využívání**<br /><br /> – Podpoložky<br />– Názvy v malých a středních dialogových oknech<br /><br /> **Postup**<br /><br /> – Použít případ začátku věty<br />– Vždycky používat Semilight váhy<br /><br /> **Ne:**<br /><br /> – Tučné, kurzíva nebo Tučná kurzíva<br />-Použít pro text zprávy<br />-Použít v oknech nástrojů|**Vypadá takto:** 18 bodů Segoe UI Semillight<br /><br /> **Příklad vizuálu:**<br /><br /> ![Příklad písma prostředí 200% &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202 – b_EF200")|

#### <a name="155-environment-font"></a>155% písma prostředí

|Využití|Příznaky|
|-|-|
|**Využívání**<br /><br /> – Nadpisy oddílů v uživatelském rozhraní dokumentu<br />– Sestavy<br /><br /> **Do:** Použít případ věty<br /><br /> **Ne:**<br /><br /> – Tučné, kurzíva nebo Tučná kurzíva<br />-Použít pro text zprávy<br />– Použít ve standardních ovládacích prvcích sady Visual Studio<br />-Použít v oknech nástrojů|**Zobrazuje se jako:** 14 bodů Segoe UI<br /><br /> **Příklad vizuálu:**<br /><br /> ![Příklad 155% nadpisu písma prostředí](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202 – c_EF155")|

#### <a name="133-environment-font"></a>133% písma prostředí

|Využití|Příznaky|
|-|-|
|**Využívání**<br /><br /> -Menší podpozice v dialogových oknech podpisu<br />-Menší podpoložky v uživatelském rozhraní dokumentu<br /><br /> **Do:** Použít případ věty<br /><br /> **Ne:**<br /><br /> – Tučné, kurzíva nebo Tučná kurzíva<br />-Použít pro text zprávy<br />– Použít ve standardních ovládacích prvcích sady Visual Studio<br />-Použít v oknech nástrojů|**Vypadá takto:** Segoe UI 12 bodů<br /><br /> **Příklad vizuálu:**<br /><br /> ![Příklad 133% nadpisu písma prostředí](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202 – d_EF133")|

#### <a name="122-environment-font"></a>122% písma prostředí

|Využití|Příznaky|
|-|-|
|**Využívání**<br /><br /> – Nadpisy oddílů v dialogových oknech podpisu<br />– Hlavní uzly ve stromovém zobrazení<br />– Svislá navigace na kartách<br /><br /> **Do:** Použít případ věty<br /><br /> **Ne:**<br /><br /> – Tučné, kurzíva nebo Tučná kurzíva<br />-Použít pro text zprávy<br />– Použít ve standardních ovládacích prvcích sady Visual Studio<br />-Použít v oknech nástrojů|**Zobrazuje se jako:** 11 bodů Segoe UI<br /><br /> **Příklad vizuálu:**<br /><br /> ![Příklad 122% nadpisu písma prostředí](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202 – e_EF122")|

#### <a name="environment-font--bold"></a>Písmo prostředí + tučné

|Využití|Příznaky|
|-|-|
|**Využívání**<br /><br /> – Popisky a podhlaví v dialogových oknech podpisů<br />-Popisky a podhlaví v sestavách<br />-Popisky a podhlaví v uživatelském rozhraní dokumentu<br /><br /> **Postup**<br /><br /> – Použít případ začátku věty<br />– Použít Tučná tloušťku<br /><br /> **Ne:**<br /><br /> – Kurzíva nebo Tučná kurzíva<br />-Použít pro text zprávy<br />– Použít ve standardních ovládacích prvcích sady Visual Studio<br />-Použít v oknech nástrojů|**Zobrazuje se jako:** tučné 9 pt Segoe UI<br /><br /> **Příklad vizuálu:**<br /><br /> ![Příklad písma prostředí &#43; záhlaví tučně](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202 – f_EFB")|

#### <a name="environment-font"></a>Písmo prostředí

|Využití|Příznaky|
|-|-|
|**Použití:** Všechen jiný text<br /><br /> **Do:** Použít případ věty<br /><br /> **Ne:** Kurzíva nebo Tučná kurzíva|**Zobrazuje se jako:** 9 bodů Segoe UI<br /><br /> **Příklad vizuálu:**<br /><br /> ![Příklad písma prostředí](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202 – g_EF")|

### <a name="padding-and-spacing"></a>Odsazení a mezery
 Nadpisy vyžadují místo, které jim přidávají vhodné zdůraznění. Toto místo se liší v závislosti na velikosti bodu a na tom, co jiné má poblíž nadpisu, jako je například horizontální pravidlo nebo řádek textu v písmu prostředí.

- Ideální odsazení samotného nadpisu by mělo být 90% místa výšky velkých písmen. Například nadpis Segoe UI o velikosti 28 bodů má výšku zakončení 26 bodů a odsazení by mělo být přibližně 23 bodů nebo asi 31 pixelů.

- Minimální místo kolem nadpisu by mělo být 50% výšky znakového písmena. Menší místo lze použít, je-li k záhlaví připojeno pravidlo nebo jiný element se těsnou montáží.

- Text písma tučného prostředí by měl následovat za výchozím nastavením mezer a odsazení řádku.

## <a name="see-also"></a>Viz také

- [Písma (Windows)](/windows/desktop/uxguide/vis-fonts)
- [Text uživatelského rozhraní (Windows)](/windows/desktop/uxguide/text-ui)
