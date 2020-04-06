---
title: Editor barev VSIX | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3ed1f1a2a761a6602ac891eb78b5a5436abf92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704045"
---
# <a name="vsix-color-editor"></a>Editor barev VSIX
Nástroj Visual Studio Extension Color Editor může vytvářet a upravovat vlastní barvy pro Visual Studio. Nástroj může také generovat klíče prostředků motivu tak, aby barvy lze použít v kódu. Tento nástroj je užitečný pro vytváření barev pro rozšíření sady Visual Studio, které podporuje motivy. Tento nástroj může otevřít soubory .pkgdef a XML. Motivy sady Visual Studio (soubory.vstheme) lze použít s Editorem barev rozšíření sady Visual Studio změnou přípony souboru na XML. Soubory .vstheme lze navíc importovat do aktuálního souboru XML.

 ![VSIX Barva Editor Hrdina](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX Barva Editor Hrdina")

 **Definiční soubory balíčků**

 Definice balíčku (.pkgdef) soubory jsou soubory, které definují motivy. Samotné barvy jsou uloženy v souborech XML s barvou motivu, které jsou zkompilovány do souboru .pkgdef. Soubory .pkgdef jsou nasazeny do prohledávatELNÝCH umístění sady Visual Studio, zpracovány za běhu a sloučeny za účelem definování motivů.

 **Barevné žetony**

 Barevný token se skládá ze čtyř prvků:

- **Název kategorie:** Logické seskupení pro sadu barev. Existující název kategorie použijte, pokud již existují barvy, které jsou specifické pro požadovaný prvek uživatelského rozhraní nebo skupinu prvků uživatelského rozhraní.

- **Název tokenu:** Popisný název pro sady tokenů barev a tokenů. Sady zahrnují názvy tokenů pozadí a popředí (text) stejně jako všechny jejich stavy a ty by měly být pojmenovány tak, aby bylo snadné identifikovat dvojice a stavy, které se vztahují k.

- **Barevné hodnoty (nebo odstíny):** Potřebné pro každý barevný motiv. Vždy vytvářejte hodnoty barev pozadí a textu ve dvojicích. Barvy jsou spárovány pro pozadí nebo popředí tak, aby barva textu (popředí) byla vždy čitelná proti barvě pozadí, na kterou je nakreslena. Tyto barvy jsou propojeny a budou použity společně v ui. Pokud pozadí není určeno pro použití s textem, nedefinujte barvu popředí.

- **Název systémové barvy:** Pro použití ve vysoce kontrastních displejích.

## <a name="how-to-use-the-tool"></a>Jak nástroj používat
 Co nejvíce a je-li to vhodné, existující barvy sady Visual Studio by měly být znovu použity namísto vytváření nových. V případech, kdy nejsou definovány žádné vhodné barvy, by však měly být vytvořeny vlastní barvy, aby byly motivy rozšíření kompatibilní.

 **Vytváření nových barevných tokenů**

 Chcete-li vytvořit vlastní barvy pomocí Editoru barev rozšíření sady Visual Studio, postupujte takto:

1. Určete názvy kategorií a tokenů pro nové tokeny barev.

2. Zvolte odstíny, které bude prvek ui používat pro každý motiv a barvu systému pro vysoký kontrast.

3. Pomocí editoru barev vytvořte nové barevné tokeny.

4. Použijte barvy v rozšíření Sady Visual Studio.

5. Otestujte změny v sadě Visual Studio.

   **Krok 1: Určete názvy kategorií a tokenů pro nové barevné tokeny.**

   Upřednostňované schéma pojmenování pro VSColor je **[Kategorie] [typ uI] [State]**. Nepoužívejte slovo "barva" v názvech VSColor, protože je nadbytečné.

   Názvy kategorií poskytují logické seskupení a měly by být definovány co nejúžeji. Například název jednoho okna nástroje může být název kategorie, ale název celé organizační jednotky nebo projektového týmu není. Seskupení položek do kategorií pomáhá zabránit záměně mezi barvami se stejným názvem.

   Název tokenu musí jasně označovat typ prvku a situace nebo "stav", pro který bude použita barva. Například **[typ uživatelského nastavení]** aktivního datového tipu může být pojmenován "**DataTip**" a **[State]** může být pojmenován "**Aktivní**", což vede k názvu barvy**DataTipActive**" . Vzhledem k tomu, že datové tipy mají text, je třeba definovat barvu popředí i pozadí. Pomocí párování pozadí a popředí editor barev automaticky vytvoří barvy "**DataTipActive**" pro pozadí a "**DataTipActiveText**" pro popředí.

   Pokud část uživatelského pole má pouze jeden stav, **část [State]** názvu může být vynechána. Pokud má například vyhledávací pole ohraničení a neexistuje žádná změna stavu, která by ovlivnila barvu ohraničení, může být název tokenu barvy ohraničení jednoduše nazván **"SearchBoxBorder**".

   Některé běžné názvy stavů zahrnují:

- Aktivní

- Inactive

- Mouseover

- Mousedown

- Vybráno

- Focused

  Příklady několika názvů tokenů pro části ovládacího prvku položky seznamu:

- Listitem

- ListItemBorder

- ListItemMouseOver

- ListItemMouseOverBorder

- Vybraná položka seznamu

- ListItemSelectedBorder

- Položka listovázakázána

- ListItemDisabledBorder

  **Krok 2: Zvolte odstíny, které bude prvek ui používat pro každý motiv a barvu systému pro vysoký kontrast.**

  Při výběru vlastních barev pro ui vyberte podobný existující prvek ui a použijte jeho barvy jako základ. Barvy pro in-the-box prvky uživatelského rozhraní prošly kontrolou a testováním, takže budou vypadat vhodně a budou se chovat správně ve všech tématech.

  **Krok 3: Pomocí editoru barev vytvořte nové barevné tokeny.**

  Spusťte editor barev a otevřete nebo vytvořte nový vlastní soubor XML barev motivu. V nabídce vyberte **Upravit > novou barvu.** Otevře se dialogové okno pro určení kategorie a jednoho nebo více názvů pro položky barev v této kategorii:

  ![VSIX Color Editor Nová barva](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX Color Editor Nová barva")

  Vyberte existující kategorii nebo vyberte **Nová kategorie** a vytvořte novou kategorii. Otevře se jiný dialog, který vytvoří nový název kategorie:

  ![VSIX Editor barev Nová kategorie](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX Editor barev Nová kategorie")

  Nová kategorie pak bude dostupná v rozevírací nabídce Kategorie **Nová barva.** Po výběru kategorie zadejte pro každý nový barevný token jeden název na řádek a po dokončení vyberte "Vytvořit":

  ![VSIX Color Editor Nová barva vyplněna](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSIX Color Editor Nová barva vyplněna")

  Hodnoty barev jsou zobrazeny v párech pozadí/popředí s "None" označující, že barva nebyla definována. Poznámka: Pokud barva nemá dvojici barev a pozadí textu, musí být definováno pouze pozadí.

  ![Barevné hodnoty Editoru barev VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Barevné hodnoty Editoru barev VSIX")

  Chcete-li upravit barevný token, vyberte položku barvy motivu (sloupce) tohoto tokenu. Přidejte hodnotu barvy buď zadáním šestnáctkové hodnoty barvy v osmimístném formátu ARGB, zadáním názvu systémové barvy do buňky, nebo použitím rozevírací nabídky pro výběr požadované barvy pomocí sady posuvníků barev nebo seznamu systémových barev.

  ![VSIX Editor barev Upravit barvu](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX Editor barev Upravit barvu")

  ![Pozadí editoru barev VSIX](../../extensibility/internals/media/vsix-color-editor-background.png "Pozadí editoru barev VSIX")

  U součástí, které nepotřebují zobrazovat text, zadejte pouze jednu hodnotu barvy: barvu pozadí. V opačném případě zadejte hodnoty pro barvu pozadí i textu oddělenou lomítkem.

  Při zadávání hodnot pro hodnotu Vysoký kontrast zadejte platné názvy barev systému Windows. Nezadávejte pevně zakódované hodnoty ARGB. Seznam platných názvů systémových barev můžete zobrazit výběrem možnosti "Pozadí: Systém" nebo "Popředí: Systém" v rozevíracích nabídkách hodnoty barev. Při vytváření prvků, které mají textové součásti, použijte správný pár barev pozadí/textového systému nebo text může být nečitelný.

  Po dokončení vytváření, nastavení a úprav barevných tokenů je uložte do požadovaného formátu XML nebo .pkgdef. Barevné tokeny bez pozadí ani sady popředí budou uloženy jako prázdné barvy ve formátu XML, ale zahozeny ve formátu .pkgdef. Dialogové okno vás upozorní na potenciální ztrátu barev, pokud se pokusíte uložit prázdné barvy do souboru .pkgdef.

  **Krok 4: Použijte barvy v rozšíření Sady Visual Studio.**

  Po definování nové barevné tokeny, zahrnout .pkgdef v souboru projektu s "Build Akce" nastavena na "Obsah" a "Zahrnout do VSIX" nastavena na "True".

  ![VSIX Editor barev pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSIX Editor barev pkgdef")

  V Editoru barev rozšíření Visual Studio zvolte Soubor > Zobrazit kód prostředku, chcete-li zobrazit kód, který se používá pro přístup k vlastním barvám v uzlech založených na WPF.

  ![Prohlížeč kódů zdrojů Editoru barev VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "Prohlížeč kódů zdrojů Editoru barev VSIX")

  Zahrnout tento kód do statické třídy v projektu. Odkaz na **Microsoft.VisualStudio.Shell.\< VSVersion>.0.dll** je třeba přidat do projektu použít **Typ ThemeResourceKey.**

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

 To umožňuje přístup k barvám v kódu XAML a umožňuje uživatelskému uživatelskému nastavení reagovat na změny motivu.

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

 **Krok 5: Otestujte změny v sadě Visual Studio.**

 Editor barev můžete dočasně použít tokeny barev na spuštěné instance sady Visual Studio zobrazit živé změny barev bez opětovného sestavení balíčku rozšíření. Chcete-li tak učinit, klepněte na tlačítko Použít tento motiv pro spuštění windows sady Visual Studio umístěné v záhlaví každého sloupce motivu. Toto dočasné téma zmizí, když je VSIX Color Editor uzavřen.

 ![VSIX Color Editor použít](../../extensibility/internals/media/vsix-color-editor-apply.png "VSIX Color Editor použít")

 Chcete-li změny trvalé, znovu sestavit a znovu nasadit rozšíření Sady Visual Studio po přidání nové barvy do souboru .pkgdef a psaní kódu, který bude používat tyto barvy. Opětovné sestavení rozšíření sady Visual Studio sloučí hodnoty registru pro nové barvy do zbývajících motivů. Potom znovu spusťte Visual Studio, zobrazte uI a ověřte, zda se nové barvy zobrazí podle očekávání.

## <a name="notes"></a>Poznámky
 Tento nástroj je určen k vytváření vlastních barev pro již existující motivy sady Visual Studio nebo pro úpravy barev vlastního motivu sady Visual Studio. Chcete-li vytvořit kompletní vlastní motivy sady Visual Studio, stáhněte si [rozšíření Editor barevných motivů sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) z galerie rozšíření sady Visual Studio.

## <a name="sample-output"></a>Vzorový výstup
 **Barevný výstup XML**

 Soubor XML generovaný nástrojem bude podobný tomuto:

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

 **Barevný výstup PKGDEF**

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

 **Obálka klíčů prostředků jazyka C#**

 Klíče prostředků barev generované nástrojem budou podobné tomuto:

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

 Color **ResourceDictionary** klíče generované nástrojem bude podobný tento:

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
