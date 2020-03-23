---
title: Písma a formátování sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8634ab15a10b59fc21de390e0633d6d91793616d
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303132"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Písma a formátování pro Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>Písmo prostředí
 Všechna písma v sadě Visual Studio musí být uživateli vystavena pro vlastní nastavení. To se provádí především prostřednictvím stránky **Písma a barvy** v dialogovém okně **Nástroje > možnosti.** Tři hlavní kategorie nastavení písma jsou:

- **Písmo prostředí** - primární písmo pro rozhraní IDE (integrované vývojové prostředí), které se používá pro všechny prvky rozhraní, včetně dialogových oken, nabídek, oken nástrojů a oken dokumentů. Ve výchozím nastavení je písmo prostředí svázáno se systémovým písmem, které se v aktuálních verzích systému Windows zobrazuje jako ui se sesegoe o velikosti 9 bodů. Použití jednoho písma pro všechny prvky rozhraní pomáhá zajistit konzistentní vzhled písma v celém rozhraní IDE.

- **Textový editor** - prvky, které se vynořují v kódu a další textové editory, lze přizpůsobit na stránce Textový editor v **části Nástroje > možnosti**.

- **Konkrétní kolekce** – okna návrháře, která nabízejí uživatelské přizpůsobení prvků rozhraní, mohou vystavit písma specifická pro jejich návrhovou plochu na vlastní stránce nastavení v **části Nástroje > možnosti**.

### <a name="editor-font-customization-and-resizing"></a>Přizpůsobení a změna velikosti písma editoru
 Uživatelé často zvětší nebo zvětší velikost a / nebo barvu textu v editoru podle svých preferencí, nezávisle na obecném uživatelském rozhraní. Vzhledem k tomu, že písmo prostředí se používá na prvky, které se mohou objevit v rámci nebo jako součást editoru nebo návrháře, je důležité si uvědomit očekávané chování při změně jedné z těchto klasifikací písem.

 Při vytváření prvků uživatelského rozhraní, které se zobrazují v editoru, ale nejsou součástí *obsahu*, je důležité použít písmo prostředí a nikoli písmo textu tak, aby se velikost prvků přehodla předvídatelným způsobem.

1. Pro text kódu v editoru změňte velikost s nastavením písma textu kódu a reagujte na úroveň zvětšení textu editoru.

2. Všechny ostatní prvky rozhraní by měly být vázány na nastavení písma prostředí a reagovat na všechny globální změny v prostředí. To zahrnuje (ale není omezena na):

    - Text v kontextových nabídkách

    - Text v editoru adornment, jako je text nabídky žárovky, podokno rychlého hledání editoru a přechod do podokna

    - Popistextu v dialogových oknech, například **Najít v souborech** nebo **Refaktorovat**

### <a name="accessing-the-environment-font"></a>Přístup k písmu prostředí
 V nativním kódu nebo winforms písmo prostředí `IUIHostLocale::GetDialogFont` lze přistupovat voláním `SID_SUIHostLocale` metody po dotazování rozhraní ze služby.

 Pro Windows Presentation Foundation (WPF) odvodit `DialogWindow` třídu dialogového okna `Window` z třídy prostředí namísto třídy WPF.

 V XAML kód vypadá takto:

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

Kód za:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Nahraďte `Microsoft.VisualStudio.Shell.11.0` aktuální verzí dll MPF.)

 Chcete-li zobrazit dialogové`ShowModal()`okno, volejte `ShowDialog()`" " na třídu přes . `ShowModal()`nastaví správný modální stav ve skořepině, zajistí, že dialog bude vycentrován v nadřazeném okně a tak dále.

 Kód je následující:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal`vrátí bool? (nullable Boolean) `DialogResult`s , který lze použít v případě potřeby. Vrácená hodnota je true, pokud dialog byl uzavřen s **OK**.

 Pokud potřebujete zobrazit některé wpf uzly, které není dialog `HwndSource`a je hostován v jeho vlastní , například vyskakovací okno nebo `FontFamily` `FontSize` WPF podřízené okno Win32/WinForms nadřazené okno, budete muset nastavit a na kořenový prvek WPF element. (Skořepina nastaví vlastnosti v hlavním okně, ale `HWND`nebudou zděděny za ). Prostředí poskytuje prostředky, ke kterým mohou být vlastnosti vázány, například takto:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>Odkaz na formátování (změna velikosti/tučného písma)
 Některá dialogová okna vyžadují, aby byl určitý text tučný nebo velikost jiná než písmo prostředí. Dříve byla písma větší než písmo`environment font +2`prostředí kódována jako " " nebo podobně. Použití zadaných fragmentů kódu bude podporovat monitory s vysokým DPI a zajistí, aby se zobrazovaný text vždy zobrazoval ve správné velikosti a hmotnosti (například Light nebo Semilight).

> [!NOTE]
> Před použitím formátování se ujistěte, že dodržujete pokyny ve [stylu Text](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**

 Chcete-li změnit velikost písma prostředí, nastavte styl textblocku nebo labelu, jak je uvedeno. Každý z těchto fragmentů kódu, správně použitý, vygeneruje správné písmo, včetně příslušných velikostí a hmotnostních variant.

 Kde`vsui`" " je odkaz `Microsoft.VisualStudio.Shell`na obor názvů :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% písmo prostředí + světlo

**Objeví se jako:** 34 pt Segoe UI Light

::: moniker range="vs-2017"

**Použití pro:** (vzácné) jedinečné značkové ui, například na úvodní stránce

::: moniker-end

::: moniker range=">=vs-2019"

**Použití pro:** (vzácné) jedinečné značkové ui

::: moniker-end

**Procesní kód:** Kde `textBlock` je dříve definovaný `label` TextBlock a je dříve definovaný label:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** Nastavte styl textbloku nebo popisku, jak je znázorněno na obrázku.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% písmo prostředí + světlo
 **Zobrazuje se jako:** 28 bodů Segoe UI Light **Use for:** velké názvy dialogů s podpisem, hlavní nadpis v sestavách

 **Procesní kód:** Kde `textBlock` je dříve definovaný `label` TextBlock a je dříve definovaný label:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** Nastavte styl textbloku nebo popisku, jak je znázorněno na obrázku.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% písmo prostředí + Semilight
 **Vypadá jako:** 18 pt Segoe UI Semilight **Použití pro:** podpoložky, názvy v malých a středních dialogových oknech

 **Procesní kód:** Kde `textBlock` je dříve definovaný `label` TextBlock a je dříve definovaný label:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** Nastavte styl textového bloku nebo popisku, jak je znázorněno na obrázku:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% písmo prostředí
 **Zobrazuje se jako:** 14 pt Segoe UI **Použití pro:** nadpisy oddílů v ui dokumentu nebo sestavách

 **Procesní kód:** Kde `textBlock` je dříve definovaný `label` TextBlock a je dříve definovaný label:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** Nastavte styl textového bloku nebo popisku, jak je znázorněno na obrázku:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133% písmo prostředí
 **Zobrazuje se jako:** 12 pt Segoe UI **Použití pro:** menší podnadpisy v dialogových oknech signatur a dobře dokumentovaného ui

 **Procesní kód:** Kde `textBlock` je dříve definovaný `label` TextBlock a je dříve definovaný label:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** Nastavte styl textového bloku nebo popisku, jak je znázorněno na obrázku:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% písmo prostředí
 **Zobrazuje se jako:** 11 bodů Uživatelské ho uživatelského okna Segoe **Použití pro:** nadpisy oddílů v dialogových oknech podpisu, horní uzly ve stromovém zobrazení, navigace na svislé tabulátory

 **Procesní kód:** Kde `textBlock` je dříve definovaný `label` TextBlock a je dříve definovaný label:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** Nastavte styl textového bloku nebo popisku, jak je znázorněno na obrázku:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Písmo prostředí + tučné písmo
 **Zobrazuje se jako:** tučné 9 pt Segoe UI **Použití pro:** popisky a podhlavy v dialogových oknech podpisu, sestavách a dobře dokumentovém uzemnovacím okně

 **Procesní kód:** Kde `textBlock` je dříve definovaný `label` TextBlock a je dříve definovaný label:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** Nastavte styl textového bloku nebo popisku, jak je znázorněno na obrázku:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Lokalizovatelné styly
 V některých případech budou muset lokalizátory upravit styly písma pro různá národní prostředí, například odebrat tučné písmo z textu pro východoasijské jazyky. Aby bylo možné lokalizaci stylů písma, musí být tyto styly v souboru Resx. Nejlepší způsob, jak toho dosáhnout a stále upravovat styly písma v návrháři formulářů sady Visual Studio, je explicitně nastavit styly písma v době návrhu. I když to vytvoří úplný objekt písma a může se zdát, že přerušit dědičnost nadřazených písem, pouze FontStyle vlastnost se používá k nastavení písma.

 Řešením je připojit `FontChanged` událost formuláře dialogu. V `FontChanged` případě, procházka všechny ovládací prvky a zkontrolujte, zda je nastavena jejich písma. Pokud je nastavena, změňte ji na nové písmo na základě písma formuláře a předchozího stylu písma ovládacího prvku. Příkladem tohoto v kódu je:

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

 Použití tohoto kódu zaručuje, že při aktualizaci písma formuláře se aktualizují také písma ovládacích prvků. Tato metoda by měla být také volána z konstruktoru formuláře, `IUIService` protože `FontChanged` dialogové okno může selhat získat instanci a událost se nikdy požáru. Hákování `FontChanged` umožní dialogům dynamicky vyzvednout nové písmo i v případě, že dialogové okno je již otevřené.

### <a name="testing-the-environment-font"></a>Testování písma prostředí
 Chcete-li zajistit, aby vaše ui používalo písmo prostředí a respektovalo nastavení velikosti, otevřete **možnosti nástroje > > prostředí > písma a barvy** a v rozevírací nabídce Zobrazit nastavení pro:.

 ![Nastavení Písma a barvy &gt; v dialogovém okně Volby nástrojů](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Nastavení Písma a barvy &gt; v dialogovém okně Volby nástrojů

 Nastavte písmo na něco velmi odlišného od výchozího. Chcete-li, aby bylo zřejmé, které ui neaktualizuje, zvolte písmo s patkámi (například "Times New Roman") a nastavte velmi velkou velikost. Pak otestujte své prostředí, abyste se ujistili, že respektuje prostředí. Zde je příklad pomocí dialogového okna licence:

 ![Příklad textu nového nemotivního prostředí](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Příklad textu nového nemotivního prostředí

 V tomto případě "Informace o uživateli" a "Informace o produktu" nerespektují písmo. V některých případech to může být explicitní volba návrhu, ale může se jedná o chybu, pokud explicitní písmo není zadáno jako součást specifikací redline.

 Chcete-li písmo obnovit, klepněte na tlačítko Použít výchozí hodnoty v části **Nástroje > Možnosti > prostředí > Písma a barvy**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>Styl textu
 Styl textu odkazuje na velikost písma, tloušťku a velikost písmen. Pokyny k implementaci naleznete [v tématu Písmo prostředí](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Textový kryt

#### <a name="all-caps"></a>Všechna čepice
 Nepoužívejte všechna velká písmena pro názvy nebo popisky v sadě Visual Studio.

#### <a name="all-lowercase"></a>Všechna malá písmena
 Nepoužívejte všechna malá písmena pro názvy nebo popisky v sadě Visual Studio.

#### <a name="sentence-and-title-case"></a>Velká a velká písmena
 Text v sadě Visual Studio by měl v závislosti na situaci používat písmena nadpisu nebo velká písmena věty.

|Použít případ názvu pro:|Použít případ věty pro:|
|-------------------------|----------------------------|
|Názvy dialogů|Popisky|
|Skupinová pole|Políčka|
|Položky nabídky|Přepínače|
|Položky kontextové nabídky|Položky seznamu|
|Tlačítka|Stavové řádky|
|Popisky tabulek||
|Záhlaví sloupců||
|Popisy||

##### <a name="title-case"></a>Případ nadpisu
 Případ nadpisu je styl, ve kterém jsou velká písmena většiny nebo všech slov ve frázi velkými písmeny. V sadě Visual Studio se titulní písmeno používá pro mnoho položek, včetně:

- **Popisy.** Příklad: Náhled vybraných položek

- **Záhlaví sloupců.** Příklad: "Odezva systému"

- **Položky nabídky.** Příklad: "Uložit vše"

  Při použití title case, toto jsou pokyny pro to, kdy slova velká a kdy je ponechat malá písmena:

|Velká písmena|Komentáře a příklady|
|---------------|---------------------------|
|Všechna nosná ustanovení||
|Všechny akce|Včetně "Is" a dalších forem "být"|
|Všechna příslovce|Včetně "než" a "Kdy"|
|Všechna přídavná jména|Včetně "To" a "To"|
|Všechna potomstva|Včetně přivlastňovací "Jeho", stejně jako "Je to", kontrakce předešlého "to" a sloveso "je"|
|První a poslední slova, bez ohledu na části řeči||
|Předložky, které jsou součástí slovesné fráze|"Uzavření všech oken" nebo "Vypnutí systému"|
|Všechna písmena s akronymem|HTML, XML, URL, IDE, RGB|
|Druhé slovo ve složeném slově, pokud se jedná o vlastní jméno nebo správné přídavné jméno, nebo pokud mají slova stejnou hmotnost|Křížový odkaz, software před společností Microsoft, přístup pro čtení/zápis, běh|

|Malá písmena|Příklady|
|---------------|--------------|
|Druhé slovo ve složeném slově, pokud se jedná o jinou část řeči nebo příčestí, které mění první slovo|Jak na to, Vzlet|
|články, pokud jeden není první slovo v názvu|a, an, the|
|Koordinovat spojky|a, ale, pro, ani, nebo|
|Předložky se slovy ze čtyř nebo méně písmen mimo slovesnou frázi|do, na, jako pro, z, na vrcholu|
|"Do", pokud se používá v infinitivu fráze|"Jak formátovat pevný disk"|

##### <a name="sentence-case"></a>Případ věty
 Případ věty je standardní metoda psaní velkých písmen, ve které je velké pouze první slovo věty, spolu s vlastními vlastními jménemi a slovem "I". Obecně platí, že věta případ je jednodušší pro celosvětové publikum číst, zvláště když obsah bude přeložen strojem. Použít případ věty pro:

1. **Zprávy stavového řádku.** Jedná se o jednoduché, krátké a poskytují pouze informace o stavu. Příklad: "Načítání souboru projektu"

2. **Všechny ostatní prvky uživatelského rozhraní**, včetně popisků, zaškrtávacích políček, přepínacích tlačítek a položek seznamu. Příklad: "Vybrat všechny položky v seznamu"

### <a name="text-formatting"></a>Formátování textu
 Výchozí formátování textu v sadě Visual Studio 2013 je řízeno [písmem prostředí](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Tato služba pomáhá zajistit konzistentní vzhled písma v celém integrovaném vývojovém prostředí (Integrované vývojové prostředí) a musíte ji použít k zajištění konzistentního prostředí pro uživatele.

 Výchozí velikost používaná službou písem Sady Visual Studio pochází ze systému Windows a zobrazuje se jako 9 bodů.

 Formátování můžete použít na písmo prostředí. Toto téma popisuje, jak a kde používat styly. Informace o implementaci naleznete v části [Písmo prostředí](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Tučný text
 Tučný text se v sadě Visual Studio používá střídmě a měl by být vyhrazen pro:

- popisky otázek v průvodcích

- určení aktivního projektu v Průzkumníku řešení

- přepsané hodnoty v okně nástroje Vlastnosti

- některé události v rozevíracím seznamu editoru jazyka Visual Basic

- obsah vytvořený serverem v osnově dokumentu pro webové stránky

- záhlaví oddílů ve složitém dialogu nebo návrhářském uzlině

#### <a name="italics"></a>Kurzíva
 Visual Studio nepoužívá kurzívu nebo tučným písmem kurzívou text.

#### <a name="color"></a>Barvy

- Modrá barva je vyhrazena pro hypertextové odkazy (navigace a příkazy) a nikdy by neměla být použita pro orientaci.

- Větší nadpisy (písmo prostředí x 155 % nebo větší) lze barvit pro tyto účely:

  - Poskytnutí vizuální přitažlivosti k podpisu visual studio ui

  - Upozornit na určitou oblast

  - Nabídka odlehčení od standardní barvy textu tmavě šedé/černé prostředí

- Barva v nadpisech by měla využívat existující barvy značky Visual Studio, především hlavní fialová, #FF68217A.

- Při použití barev v nadpisech je nutné dodržovat pokyny pro [barvy systému Windows](/windows/desktop/uxguide/vis-color), včetně kontrastního poměru a dalších aspektů usnadnění přístupu.

### <a name="font-size"></a>Velikost písma
 Návrh ui visual studia nabízí světlejší vzhled s větším bílým prostorem. Pokud je to možné, byly chromové a titulní pruhy zmenšeny nebo odstraněny. Zatímco hustota informací je požadavek v sadě Visual Studio, typografii i nadále důležité, s důrazem na více otevřené řádkování a variace velikosti písma a závaží.

 Níže uvedené tabulky obsahují podrobnosti návrhu a vizuální příklady pro písma zobrazení používaná v sadě Visual Studio. Některé varianty písma zobrazení mají velikost i hmotnost, například Polosvětle nebo Světlo, zakódované do jejich vzhledu.

 Fragmenty kódu implementace pro všechna písma zobrazení naleznete v [odkazu Formátování (změna velikosti/tučného písma).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)

#### <a name="375-environment-font--light"></a>375% písmo prostředí + světlo

|||
|-|-|
|**Použití:** Vzácné. Pouze jedinečné značkové ui.<br /><br /> **Do:**<br /><br /> - Použití věty případ<br />- Vždy používejte nízká hmotnost<br /><br /> **Ne:**<br /><br /> - Použití pro jiné než podpisové ui, jako je úvodní stránka<br />- Tučná, kurzíva nebo tučná kurzíva<br />- Použití pro základní text<br />- Použití v oknech nástrojů|**Objeví se jako:** 34 pt Segoe UI Light<br /><br /> **Vizuální příklad:**<br /><br /> *Aktuálně není používán. Může být použit na úvodní stránce sady Visual Studio 2017.*|

#### <a name="310-environment-font--light"></a>310% písmo prostředí + světlo

::: moniker range="vs-2017"

|||
|-|-|
|**Použití:**<br /><br /> - Větší nadpis v dialogových oknech podpisu<br />- Hlavní číslo zprávy<br /><br /> **Do:**<br /><br /> - Použití věty případ<br />- Vždy používejte nízká hmotnost<br /><br /> **Ne:**<br /><br /> - Použití pro jiné než podpisové ui, jako je úvodní stránka<br />- Tučná, kurzíva nebo tučná kurzíva<br />- Použití pro základní text<br />- Použití v oknech nástrojů|**Objeví se jako:** 28 pt Segoe UI Light<br /><br /> **Vizuální příklad:**<br /><br /> ![Příklad 310 % písma prostředí &#43; nadpis Ulehčit](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|||
|-|-|
|**Použití:**<br /><br /> - Větší nadpis v dialogových oknech podpisu<br />- Hlavní číslo zprávy<br /><br /> **Do:**<br /><br /> - Použití věty případ<br />- Vždy používejte nízká hmotnost<br /><br /> **Ne:**<br /><br /> - Použití pro jiné než podpisové uI<br />- Tučná, kurzíva nebo tučná kurzíva<br />- Použití pro základní text<br />- Použití v oknech nástrojů|**Objeví se jako:** 28 pt Segoe UI Light<br /><br /> **Vizuální příklad:**<br /><br /> ![Příklad 310 % písma prostředí &#43; nadpis Ulehčit](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% písmo prostředí + Semilight

|||
|-|-|
|**Použití:**<br /><br /> - Podpoložky<br />- Tituly v malých a středních dialogových oknech<br /><br /> **Do:**<br /><br /> - Použití věty případ<br />- Vždy používejte semilight hmotnost<br /><br /> **Ne:**<br /><br /> - Tučná, kurzíva nebo tučná kurzíva<br />- Použití pro základní text<br />- Použití v oknech nástrojů|**Objeví se jako:** 18 pt Segoe UI Semillight<br /><br /> **Vizuální příklad:**<br /><br /> ![Příklad 200% písma prostředí &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% písmo prostředí

|||
|-|-|
|**Použití:**<br /><br /> - Nadpisy oddílů v ui dokumentu<br />- Zprávy<br /><br /> **Do:** Použít velká a velká písmena věty<br /><br /> **Ne:**<br /><br /> - Tučná, kurzíva nebo tučná kurzíva<br />- Použití pro základní text<br />- Použití ve standardních ovládacích prvcích sady Visual Studio<br />- Použití v oknech nástrojů|**Zobrazuje se jako:** 14 pt Segoe UI<br /><br /> **Vizuální příklad:**<br /><br /> ![Příklad nadpisu písma 155 % prostředí](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% písmo prostředí

|||
|-|-|
|**Použití:**<br /><br /> - Menší podnadpisy v dialogových oknech podpisu<br />- Menší podpoložky v dokumentovat dobře UI<br /><br /> **Do:** Použít velká a velká písmena věty<br /><br /> **Ne:**<br /><br /> - Tučná, kurzíva nebo tučná kurzíva<br />- Použití pro základní text<br />- Použití ve standardních ovládacích prvcích sady Visual Studio<br />- Použití v oknech nástrojů|**Zobrazuje se jako:** 12 pt Segoe UI<br /><br /> **Vizuální příklad:**<br /><br /> ![Příklad nadpisu písma 133 % prostředí](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% písmo prostředí

|||
|-|-|
|**Použití:**<br /><br /> - Nadpisy oddílů v dialogových oknech podpisu<br />- Horní uzly ve stromovém zobrazení<br />- Vertikální navigace na kartě<br /><br /> **Do:** Použít velká a velká písmena věty<br /><br /> **Ne:**<br /><br /> - Tučná, kurzíva nebo tučná kurzíva<br />- Použití pro základní text<br />- Použití ve standardních ovládacích prvcích sady Visual Studio<br />- Použití v oknech nástrojů|**Zobrazuje se jako:** 11 pt Segoe UI<br /><br /> **Vizuální příklad:**<br /><br /> ![Příklad nadpisu písma 122 % prostředí](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Písmo prostředí + tučné písmo

|||
|-|-|
|**Použití:**<br /><br /> - Popisky a podhlavy v dialogových oknech podpisu<br />- Štítky a podhlavy v sestavách<br />- Popisky a podhlavy v dokumentu dobře UI<br /><br /> **Do:**<br /><br /> - Použití věty případ<br />- Používejte tučnou hmotnost<br /><br /> **Ne:**<br /><br /> - Kurzíva nebo tučná kurzíva<br />- Použití pro základní text<br />- Použití ve standardních ovládacích prvcích sady Visual Studio<br />- Použití v oknech nástrojů|**Objeví se jako:** tučně 9 pt Segoe UI<br /><br /> **Vizuální příklad:**<br /><br /> ![Příklad písma prostředí &#43; nadpis Tučné](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Písmo prostředí

|||
|-|-|
|**Použití:** Všechny ostatní texty<br /><br /> **Do:** Použít velká a velká písmena věty<br /><br /> **Ne:** Kurzíva nebo tučná kurzíva|**Zobrazuje se jako:** 9 pt Segoe UI<br /><br /> **Vizuální příklad:**<br /><br /> ![Příklad písma Prostředí](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Odsazení a mezery
 Nadpisy vyžadují prostor kolem nich, aby jim odpovídající důraz. Tato mezera se liší v závislosti na velikosti bodu a co dalšího je v blízkosti nadpisu, například vodorovné pravidlo nebo řádek textu v písmu prostředí.

- Ideální odsazení pro nadpis samo o sobě by mělo být 90 % výškového prostoru znaku kapitálu. Například nadpis 28 pt Segoe UI Light má výšku zakončení 26 bodů a odsazení by mělo být přibližně 23 bodů nebo přibližně 31 pixelů.

- Minimální mezera kolem nadpisu by měla být 50 % výšky znaku hlavního města. Pokud je nadpis doplněn pravidlem nebo jiným přiléhajícím prvkem, může být použito méně místa.

- Text písma s tučným písmem by měl sledovat výchozí mezery výšky řádku a odsazení.

## <a name="see-also"></a>Viz také

- [MSDN: Písma (Windows)](/windows/desktop/uxguide/vis-fonts)
- [MSDN: Text uživatelského rozhraní (Windows)](/windows/desktop/uxguide/text-ui)
