---
title: Editor barev VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea5695c41b19cbd77c56a63f22b52fca5ee6f1eb
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295443"
---
# <a name="vsix-color-editor"></a>Editor barev VSIX
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nástroj Editor barev rozšíření sady Visual Studio může vytvářet a upravovat vlastní barvy pro Visual Studio. Nástroj může také generovat klíče prostředků motivu, aby bylo možné použít barvy v kódu. Tento nástroj je užitečný pro vytváření barev pro rozšíření sady Visual Studio, které podporuje. Tento nástroj může otevřít soubory. pkgdef a. XML. Motivy sady Visual Studio (soubory. vstheme) lze použít s editorem barev rozšíření sady Visual Studio změnou přípony souboru na. XML. Soubory. vstheme lze navíc importovat do aktuálního souboru. XML.  
  
 ![Editor barev VSIX Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "Editor barev VSIX Hero")  
  
 **Definiční soubory balíčku**  
  
 Soubory definice balíčku (. pkgdef) jsou soubory, které definují motivy. Barvy samotné jsou uloženy v souborech Color. XML motivu, které jsou zkompilovány do souboru. pkgdef. Soubory. pkgdef jsou nasazeny do vyhledávacích umístění sady Visual Studio, zpracované za běhu a sloučeny dohromady pro definování motivů.  
  
 **Barevné tokeny**  
  
 Barevný token se skládá ze čtyř prvků:  
  
- **Název kategorie:** Logické seskupení pro sadu barev. Pokud již existují barvy, které jsou specifické pro požadovaný prvek uživatelského rozhraní nebo skupinu prvků uživatelského rozhraní, použijte existující název kategorie.  
  
- **Název tokenu:** Popisný název pro tokeny barev a sady tokenů. Sady obsahují názvy tokenů pozadí a popředí (text) a také všechny jejich stavy a ty by měly být pojmenovány tak, aby bylo možné snadno identifikovat páry a stavy, na které se vztahují.  
  
- **Hodnoty barev (nebo odstíny):** Nutné pro každý barevný motiv. Vždy vytvářet hodnoty barev pozadí a textu ve dvojicích. Barvy jsou spárovány pro pozadí/popředí, takže barva textu (popředí) je vždy čitelná vzhledem k barvě pozadí, na které je vykreslena. Tyto barvy jsou propojené a použijí se společně v uživatelském rozhraní. Pokud pozadí není určeno pro použití s textem, nedefinujte barvu popředí.  
  
- **Název systémové barvy:** Pro použití v horních displejích.  
  
## <a name="how-to-use-the-tool"></a>Jak používat nástroj  
 Jak je to možné, a tam, kde je to vhodné, by se měly znovu použít stávající barvy sady Visual Studio místo toho, aby se prováděly nové. Nicméně pro případy, kdy nejsou definovány žádné odpovídající barvy, by měly být vytvořeny vlastní barvy, aby bylo udržování kompatibility s rozšířeními kompatibilní.  
  
 **Vytváření nových barevných tokenů**  
  
 Chcete-li vytvořit vlastní barvy pomocí editoru barev rozšíření sady Visual Studio, postupujte podle následujících kroků:  
  
1. Určete kategorii a názvy tokenů pro nové tokeny barev.  
  
2. Vyberte odstíny, které prvek uživatelského rozhraní použije pro každý motiv a systémovou barvu pro Vysoký kontrast.  
  
3. Pomocí editoru barev vytvořte nové barevné tokeny.  
  
4. Použijte barvy v rozšíření sady Visual Studio.  
  
5. Otestujte změny v aplikaci Visual Studio.  
  
   **Krok 1: určení kategorie a názvů tokenů pro nové tokeny barev**  
  
   Preferované schéma pojmenování pro VSColor je **[Category] [typ uživatelského rozhraní] [State]** . Nepoužívejte slovo "Color" v názvech VSColor, protože je redundantní.  
  
   Názvy kategorií poskytují logické seskupení a měly by být definovány co nejpřesněji. Například název jednoho okna nástroje může být název kategorie, ale název celé obchodní jednotky nebo týmu projektu není. Seskupení položek do kategorií pomáhá zabránit záměnám mezi barvami se stejným názvem.  
  
   Název tokenu musí jasně označovat typ prvku a situace, nebo "State", pro který bude použita barva. Například aktivní Tip pro data **[typ uživatelského rozhraní]** může být pojmenován "**DataTip**" a " **[State]** " může mít název "**aktivní**", což má za následek název barvy "**DataTipActive**". Vzhledem k tomu, že tipy k datům obsahují text, musí být definován popředí i barva pozadí. Pomocí párování pozadí a popředí automaticky vytvoří Editor barev barvy "**DataTipActive**" pro pozadí a "**DataTipActiveText**" pro popředí.  
  
   Pokud má část uživatelského rozhraní pouze jeden stav, může být část názvu **[State]** vynechána. Například pokud má vyhledávací pole ohraničení a nedochází k žádné změně stavu, která by ovlivnila barvu ohraničení, název tokenu barvy ohraničení lze jednoduše vyvolat "**SearchBoxBorder**".  
  
   Mezi běžné názvy stavů patří:  
  
- Aktivní  
  
- Termín  
  
- MouseOver  
  
- MouseDown  
  
- Vybráno  
  
- Zaměřil  
  
  Příklady několika názvů tokenů pro části ovládacího prvku položky seznamu:  
  
- Collection  
  
- ListItemBorder  
  
- ListItemMouseOver  
  
- ListItemMouseOverBorder  
  
- ListItemSelected  
  
- ListItemSelectedBorder  
  
- ListItemDisabled  
  
- ListItemDisabledBorder  
  
  **Krok 2: vyberte odstíny, které prvek uživatelského rozhraní použije pro každý motiv a systémovou barvu pro Vysoký kontrast.**  
  
  Při volbě vlastních barev uživatelského rozhraní vyberte podobný existující prvek uživatelského rozhraní a použijte jeho barvy jako základ. Barvy pro prvky uživatelského rozhraní v dialogovém okně prošly kontrolou a testováním, takže budou vypadat vhodně a chovají se správně ve všech motivech.  
  
  **Krok 3: pomocí editoru barev vytvořte nové barevné tokeny.**  
  
  Spusťte Editor barev a otevřete nebo vytvořte nový soubor. XML barvy vlastního motivu. V nabídce vyberte **upravit > novou barvu** . Tím se otevře dialogové okno pro zadání kategorie a jednoho nebo více názvů pro položky barev v rámci této kategorie:  
  
  ![Nová barva editoru barev VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "Nová barva editoru barev VSIX")  
  
  Vyberte existující kategorii nebo vyberte **Nová kategorie** a vytvořte novou kategorii. Otevře se další dialog a vytvoří se nový název kategorie:  
  
  ![Editor barev VSIX – nová kategorie](../../extensibility/internals/media/vsix-color-editor-new-category.png "Editor barev VSIX – nová kategorie")  
  
  Nová kategorie pak bude k dispozici v rozevírací nabídce **Nová kategorie barev** . Po výběru kategorie zadejte jeden název na řádek pro každý nový token barvy a po dokončení vyberte vytvořit.  
  
  ![Editor barev VSIX – nová barva vyplněná](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Editor barev VSIX – nová barva vyplněná")  
  
  Hodnoty barvy jsou zobrazeny ve dvojicích pozadí a popředí s hodnotou "none", což značí, že barva nebyla definována. Poznámka: Pokud barva neobsahuje dvojici barev textu/pozadí, je nutné definovat pouze pozadí.  
  
  ![Hodnoty barvy v editoru barev VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Hodnoty barvy v editoru barev VSIX")  
  
  Chcete-li upravit barevný token, vyberte položku barvy pro motiv (sloupec) daného tokenu. Hodnotu barvy přidejte buď zadáním hodnoty hexadecimální barvy ve formátu ARGB s 8 číslicemi, zadáním názvu systémové barvy do buňky nebo použitím rozevírací nabídky k výběru požadované barvy pomocí sady posuvníků barev nebo seznamu systémových barev.  
  
  ![Editor barev VSIX – úprava barvy](../../extensibility/internals/media/vsix-color-editor-edit-color.png "Editor barev VSIX – úprava barvy")  
  
  ![Pozadí editoru barev VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Pozadí editoru barev VSIX")  
  
  Pro součásti, které nepotřebují zobrazovat text, zadejte pouze jednu hodnotu barvy: barvu pozadí. V opačném případě zadejte hodnoty pro barvu pozadí a textu oddělené lomítkem.  
  
  Při zadávání hodnot pro Vysoký kontrast zadejte platné názvy barev systému Windows. Nezadávejte hodnoty pevně zakódované ARGB. Seznam platných systémových barev můžete zobrazit tak, že v rozevíracích nabídkách hodnota barvy vyberete "Background: System" nebo "popředí: systém". Při vytváření prvků, které mají textové komponenty, použijte správný dvojici barev pozadí/textu nebo je možné, že text nebude čitelný.  
  
  Až dokončíte vytváření, nastavování a upravování barevných tokenů, uložte je do požadovaného formátu. XML nebo. pkgdef. Tokeny barev bez nastaveného pozadí ani sady popředí budou uloženy jako prázdné barvy ve formátu. XML, ale byly zahozeny ve formátu. pkgdef. Pokud se pokusíte uložit prázdné barvy do souboru. pkgdef, zobrazí se dialogové okno s upozorněním na potenciální ztrátu barev.  
  
  **Krok 4: použijte barvy v rozšíření sady Visual Studio.**  
  
  Po definování nových tokenů barev zahrňte do souboru projektu. pkgdef s akcí sestavit "nastavit na" obsah "a" zahrnout do VSIX "nastavenou na hodnotu" true ".  
  
  ![Editor barev VSIX pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "Editor barev VSIX pkgdef")  
  
  V editoru barev rozšíření sady Visual Studio vyberte soubor > zobrazení kód prostředku pro zobrazení kódu, který se používá pro přístup k vlastním barvám v uživatelském rozhraní založeném na WPF.  
  
  ![Prohlížeč kódu prostředku pro Editor barev VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Prohlížeč kódu prostředku pro Editor barev VSIX")  
  
  Zahrňte tento kód do statické třídy v projektu. Odkaz na **Microsoft. VisualStudio. Shell.\<VSVersion > 0. dll** je nutné přidat do projektu pro použití typu **ThemeResourceKey** .  
  
```csharp  
namespace MyCustomColors  
{  
    public static class MyCategory  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");  
  
        private static ThemeResourceKey _MyColor1ColorKey;  
        private static ThemeResourceKey _MyColor1BrushKey;  
        private static ThemeResourceKey _MyColor1TextColorKey;  
        private static ThemeResourceKey _MyColor1TextBrushKey;  
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }  
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }  
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }  
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }  
        #endregion  
    }  
}  
```  
  
 To umožňuje přístup k barvám v kódu XAML a umožňuje uživatelskému rozhraní reagovat na změny motivu.  
  
```xaml  
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"  
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
             xmlns:ns="clr-namespace:MyCustomColors">  
  <Grid>  
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"  
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"  
      >Sample Text</TextBlock>  
  
  </Grid>  
</UserControl>  
```  
  
 **Krok 5: testování změn v aplikaci Visual Studio.**  
  
 Editor barev může dočasně použít barevné tokeny na spuštěné instance sady Visual Studio pro zobrazení živých změn barev bez nového sestavení balíčku rozšíření. Provedete to tak, že kliknete na tlačítko použít tento motiv ke spuštění sady Visual Studio Windows v záhlaví každého sloupce motivu. Tento dočasný motiv zmizí, až bude editor barev VSIX uzavřen.  
  
 ![Použije se Editor barev VSIX.](../../extensibility/internals/media/vsix-color-editor-apply.png "Použije se Editor barev VSIX.")  
  
 Chcete-li provést změny trvale, znovu sestavte a znovu nasaďte rozšíření sady Visual Studio po přidání nových barev do souboru. pkgdef a psaní kódu, který bude tyto barvy používat. Opětovným sestavením rozšíření sady Visual Studio dojde k sloučení hodnot registru pro nové barvy do zbývajících motivů. Pak znovu spusťte aplikaci Visual Studio, zobrazte uživatelské rozhraní a ověřte, zda se nové barvy zobrazí podle očekávání.  
  
## <a name="notes"></a>Poznámky  
 Tento nástroj je určen pro vytváření vlastních barev pro existující motivy sady Visual Studio nebo pro úpravu barev vlastního motivu sady Visual Studio. Chcete-li vytvořit kompletní vlastní motiv sady Visual Studio, Stáhněte si z galerie rozšíření sady Visual Studio [rozšíření editoru barevných motivů](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) sady Visual Studio.  
  
## <a name="sample-output"></a>Vzorový výstup  
 **Výstup barvy XML**  
  
 Soubor. XML generovaný nástrojem bude vypadat přibližně takto:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">  
      <Color Name="ColorName1">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
      <Color Name="ColorName2">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
        <Foreground Type="CT_RAW" Source="FF000000" />  
      </Color>  
      <Color Name="ColorName3">  
        <Background Type="CT_RAW" Source="FFFF0000" />  
      </Color>  
      <Color Name="ColorName4">  
        <Background Type="CT_RAW" Source="FF000088" />  
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
    </Category>  
  </Theme>  
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>  
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>  
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>  
</Themes>  
  
```  
  
 **Výstup barvy PKGDEF**  
  
 Soubor. pkgdef generovaný nástrojem bude vypadat přibližně takto:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]  
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff  
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]  
"Data"=hex:...  
  
```  
  
 **C#Obálka klíčů prostředků**  
  
 Barvy klíče prostředků vygenerované nástrojem budou vypadat podobně jako v tomto příkladu:  
  
```csharp  
namespace MyNamespace  
{  
    public static class MyColors  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
  
        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }  
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }  
  
        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }  
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }  
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }  
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }  
  
        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }  
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }  
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }  
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }  
        #endregion  
    }  
}  
```  
  
 **Obálka slovníku prostředků WPF**  
  
 Klíče **ResourceDictionary** barvy generované nástrojem budou podobné tomuto:  
  
```xaml  
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:colors="clr-namespace:MyNamespace">  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />  
</ResourceDictionary>  
```
