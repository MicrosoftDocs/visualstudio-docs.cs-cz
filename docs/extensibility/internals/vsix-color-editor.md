---
title: Editor barev VSIX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13f2633895e1bf0f228f9984ade99b01f6e0cc12
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915825"
---
# <a name="vsix-color-editor"></a>Editor barev VSIX
Nástroj editoru barev rozšíření sady Visual Studio můžete vytvářet a upravovat vlastní barvy pro sadu Visual Studio. Nástroj může také generovat klíče motivů prostředků tak, aby barvy můžete použít v kódu. Tento nástroj je užitečný pro provádění barvy pro rozšíření sady Visual Studio, který podporuje motivů. Tento nástroj můžete otevřít soubory .pkgdef a XML. Visual Studio motivů (.vstheme soubory) je možné rozšíření barva Editor sady Visual Studio tak, že změníte příponu .xml. Kromě toho lze importovat .vstheme soubory do aktuálního souboru .xml.  
  
 ![Hero Editor barev VSIX](../../extensibility/internals/media/vsix-color-editor-hero.png "Hero Editor barev VSIX")  
  
 **Definičních souborech balíčku**  
  
 Balíček definice (.pkgdef) soubory jsou soubory, které definují motivů. Barvy sami jsou uloženy v souborech XML barvu motivu, které jsou kompilovány do souboru .pkgdef. Soubor .pkgdef jsou nasazené do sady Visual Studio prohledávatelná umístění, zpracovaných za běhu a sloučení definovat motivů.  
  
 **Barva tokeny**  
  
 Barva token se skládá ze čtyř prvků:  
  
-   **Název kategorie:** logické seskupení pro sadu barev. Použijte stávající název kategorie, pokud jsou již barvy, které jsou specifické pro požadovaný prvek uživatelského rozhraní nebo skupiny prvků uživatelského rozhraní.  
  
-   **Název tokenu:** popisný název pro barvu tokenu a tokenu sady. Sady zahrnují na pozadí a popředí (text) token názvy, jakož i jejich stavů, a ty by měly být pojmenovány tak, aby se snadno rozpoznat páry a stavy, které se vztahují na.  
  
-   **Barevné hodnoty (nebo bubliny):** potřebné pro každý barevný motiv. Vždy vytvořte textu a pozadí hodnot barev v párech. Barvy jsou párovat pro pozadí a popředí, tak, aby vždy čitelné barevném pozadí, na kterém je vykreslen barva textu (popředí). Tyto barvy jsou propojeny a použije se současně v uživatelském rozhraní. Pokud na pozadí není určena pro použití s textem, nedefinují barvu popředí.  
  
-   **Název systémové barvy:** pro použití v zobrazení s vysokým kontrastem.  
  
## <a name="how-to-use-the-tool"></a>Jak používat nástroj  
 Co je to možné, a kde je to vhodné, by měl znovu použít existující sady Visual Studio barvy místo provedení nové značky. V případech, kde jsou definovány žádné odpovídající barvy, měl by být vlastních barev však vytvořen zachovat kompatibilitu s rozšíření motivů.  
  
 **Vytváření nových tokenů barva**  
  
 Pokud chcete vytvořit vlastní barvy pomocí editoru barev rozšíření sady Visual Studio, postupujte takto:  
  
1. Určete název kategorie a token pro nové tokeny barvu.  
  
2. Vyberte bubliny, která prvek uživatelského rozhraní pro vysoký kontrast – použije pro každý motiv a systémovou barvou.  
  
3. Vytvořit nové barevné tokeny pomocí editoru barev.  
  
4. Použití barev v rozšíření sady Visual Studio.  
  
5. Otestujte změny v sadě Visual Studio.  
  
   **Krok 1: Určení kategorie a token názvy pro nové tokeny barvu.**  
  
   Upřednostňované pojmenování schéma je VSColor **[kategorie] [uživatelské rozhraní typu] [stav]**. Nepoužívejte slova "color" v názvech VSColor, protože je redundantní.  
  
   Názvy kategorií zajišťují logické seskupení a musí být definován jako nejpřesnějším co nejvíc. Například název okna jediného nástroje může být název kategorie, ale není název celý obchodní jednotky nebo projektu týmu. Seskupení položek do kategorií pomáhá zabránit nejasnostem mezi barvy se stejným názvem.  
  
   Název tokenu musí jasně označují typ elementu a situace nebo "stavu" pro které se použijí barvy. Například aktivní data tip. **[uživatelské rozhraní typu]** by mohla mít název "**datového tipu**" a **[stavu]** by mohla mít název "**aktivní**," výsledkem Barva názvu "**DataTipActive**." Protože datových tipech obsahují text, popředí a barvu pozadí je potřeba určit. Pomocí na pozadí a popředí párování editor barev automaticky vytvoří barvy "**DataTipActive**" pozadí a "**DataTipActiveText**" pro popředí.  
  
   Pokud se část uživatelského rozhraní obsahuje pouze jeden stav **[stavu]** lze vynechat část názvu. Například pokud není žádná změna stavu, které má vliv na barvu ohraničení vaší vyhledávací pole má ohraničení, pak názvu pro token Barva okraje lze jednoduše volat "**SearchBoxBorder**."  
  
   Některé běžné názvy patří:  
  
- Aktivní  
  
- Neaktivní  
  
- Myš nad  
  
- MouseDown  
  
- Vybrané  
  
- Fokus  
  
  Příklady několik tokenů názvů pro část ovládacího prvku položky seznamu:  
  
- ListItem  
  
- ListItemBorder  
  
- ListItemMouseOver  
  
- ListItemMouseOverBorder  
  
- ListItemSelected  
  
- ListItemSelectedBorder  
  
- ListItemDisabled  
  
- ListItemDisabledBorder  
  
  **Krok 2: Výběr bubliny, která prvek uživatelského rozhraní pro vysoký kontrast – použije pro každý motiv a systémovou barvou.**  
  
  Pokud výběr vlastních barev pro uživatelské rozhraní, vyberte podobné existující prvek uživatelského rozhraní a používat jeho barvy jako základ. Barev pro prvky uživatelského rozhraní in-the-box byly podrobeny kontrolu a testování, takže se chovají se odpovídající a fungují správně v všechny motivy.  
  
  **Krok 3: Použití editoru barev k vytváření tokenů novou barvu.**  
  
  Spusťte editor barev a otevřete nebo vytvořte nový soubor .xml barvy vlastní motiv. Vyberte **Upravit > novou barvu** z nabídky. Otevře se dialogové okno pro zadání kategorie a jeden nebo více názvů pro barvu položky v rámci dané kategorie:  
  
  ![Nová barva Editor barev VSIX](../../extensibility/internals/media/vsix-color-editor-new-color.png "novou barvu Editor barev VSIX")  
  
  Zvolte existující kategorii nebo vyberte **novou kategorii** vytvořit novou kategorii. Otevře se další dialog, vytváří se nový název kategorie:  
  
  ![Nová kategorie Editor barev VSIX](../../extensibility/internals/media/vsix-color-editor-new-category.png "novou kategorii Editor barev VSIX")  
  
  Novou kategorii poté bude k dispozici v **novou barvu** kategorie rozevírací nabídky. Když vyberete kategorii, zadejte jeden název na řádek pro každý nový token barvu a vyberte možnost "Vytvořit" po dokončení:  
  
  ![Editor barev novou barvu VSIX vyplněné](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSIX Editor barev novou barvu vyplněné")  
  
  Barevných jsou zobrazeny v párech na pozadí a popředí, s "None" označující, že barva nebyla definována. Poznámka: Pokud barvu nemá textového barvu pár barev na pozadí, pak pouze na pozadí musí být definován.  
  
  ![Hodnoty barev Editor barev VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "hodnot barev Editor barev VSIX")  
  
  Upravit token barvy, vyberte položku barvu motivu (sloupec) tohoto tokenu. Hodnota barvy přidáte buď zadáním barvu hexadecimálně hodnotu ve formátu číslice 8 ARGB, do buňky zadávat název barvy systému nebo pomocí rozevírací nabídky vyberte požadovanou barvu přes sadu posuvníky nebo seznam systémových barev.  
  
  ![Barva úpravy Editor barev VSIX](../../extensibility/internals/media/vsix-color-editor-edit-color.png "barva úpravy Editor barev VSIX")  
  
  ![Pozadí Editor barev VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "pozadí Editor barev VSIX")  
  
  Součástí, které není potřeba zobrazovat text, zadejte hodnotu pouze jednu barvu: barvu pozadí. V opačném případě zadejte hodnoty pro barvu textu a pozadí, oddělené lomítkem.  
  
  Při zadávání hodnot pro vysoký kontrast, zadejte platné názvy barev systému Windows. Nezadávejte hodnoty ARGB pevně zakódované. Zobrazení seznamu názvy barev platný systém tak, že vyberete "Na pozadí: systém" nebo "popředí:" z rozevíracích nabídek hodnotu barvy. Při vytváření prvky, které mají textové komponenty, použít pár barva systému správné/text na pozadí nebo textu může být nejde přečíst.  
  
  Po dokončení vytváření, nastavení a úprava tokenů barvu, je uložte do požadovaného XML nebo formátu .pkgdef. Barva tokeny s ani pozadí ani popředí sady budou uloženy jako prázdný barvy ve formátu XML, ale zahozeny ve formátu .pkgdef. Dialogové okno upozorní vás na potenciální ztrátě Barva při pokusu uložit barvy prázdný soubor .pkgdef.  
  
  **Krok 4: Použití barev v rozšíření sady Visual Studio.**  
  
  Po definování novou barvou tokeny, zahrnout .pkgdef v souboru projektu "Akce sestavení" nastavena na "Obsah" a "Zahrnout do VSIX" nastavena na hodnotu "True".  
  
  ![Editor barev VSIX pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "Editor barev VSIX pkgdef")  
  
  V editoru sady Visual Studio rozšíření Color, zvolte Soubor > zobrazení prostředků kódu zobrazíte kód, který se používá pro přístup k vlastní barvy v uživatelském rozhraní založeného na WPF.  
  
  ![Prohlížeč kód prostředku Editor barev VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "prohlížeč kód prostředku Editor barev VSIX")  
  
  Zahrňte tento kód ve statické třídě v projektu. Odkaz na **Microsoft.VisualStudio.Shell.\< VSVersion >.0.dll** musí být přidán do projektu pro použití **ThemeResourceKey** typu.  
  
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
  
 To umožňuje přístup k barvy v kódu XAML a umožní reagovat na změny motiv uživatelského rozhraní.  
  
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
  
 **Krok 5: Testování změn v sadě Visual Studio.**  
  
 Editor barev dočasně použít barvu tokeny pro spuštěné instance sady Visual Studio, chcete-li zobrazit změny barvy v za provozu bez nutnosti opětovného sestavení balíček rozšíření. Uděláte to tak, klepněte na tlačítko "Použít ke spuštění sady Visual Studio windows tento motiv" umístěné na záhlaví každého sloupce motiv. Tento dočasný motiv zmizí při zavření editoru barev VSIX.  
  
 ![Použít Editor barev VSIX](../../extensibility/internals/media/vsix-color-editor-apply.png "použít Editor barev VSIX")  
  
 Aby byly změny trvalé, sestavili a rozšíření sady Visual Studio po přidání nové barvy do souboru .pkgdef a psaní kódu, který bude používat tyto barvy. Znovu sestavit rozšíření sady Visual Studio sloučí hodnoty registru pro nové barvy do ostatních motivy. Potom znovu spustit Visual Studio, zobrazení uživatelského rozhraní a ověřte, že nové barvy zobrazují podle očekávání.  
  
## <a name="notes"></a>Poznámky  
 Tento nástroj je určena pro použití k vytvoření vlastních barev pro stávající motivů aplikace Visual Studio, nebo pro úpravu barvy vlastní motiv sady Visual Studio. Vytvoření kompletní vlastní motivů aplikace Visual Studio, stáhněte si [Editor motivů sady Visual Studio rozšíření](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) z Galerie rozšíření sady Visual Studio.  
  
## <a name="sample-output"></a>Vzorový výstup  
 **Výstupní barva XML**  
  
 Soubor .xml generovaný nástrojem bude podobný tomuto:  
  
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
  
 **Výstupní barva PKGDEF**  
  
 Soubor .pkgdef generovaný nástrojem bude podobný tomuto:  
  
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
  
 **Obálka klíče prostředku jazyka C#**  
  
 Klíče prostředku barva generovaný nástrojem bude podobný tomuto:  
  
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
  
 Barva **ResourceDictionary** klíče generovaný nástrojem bude podobný tomuto:  
  
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