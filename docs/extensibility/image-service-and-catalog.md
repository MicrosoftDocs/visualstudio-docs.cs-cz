---
title: Image Service a katalog | Dokumenty společnosti Microsoft
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e1ccfad2a678656bcf09e37852532a8b28eb0e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710392"
---
# <a name="image-service-and-catalog"></a>Služba a katalog obrázků
Tato kuchařka obsahuje pokyny a osvědčené postupy pro přijetí služby Visual Studio Image Service a katalogu obrázků zavedené v sadě Visual Studio 2015.

 Služba image představená v sadě Visual Studio 2015 umožňuje vývojářům získat nejlepší obrázky pro zařízení a vybraný motiv uživatele k zobrazení obrázku, včetně oprav motivů pro kontext, ve kterém jsou zobrazeny. Přijetí služby image pomůže eliminovat hlavní body bolesti související s údržbou aktiv, škálováním HDPI a tématy.

|||
|-|-|
|**Problémy dnes**|**Řešení**|
|Prolnutí barev pozadí|Vestavěné alfa prolnutí|
|Tématika (některé) obrázky|Metadata motivu|
|Režim vysokého kontrastu|Alternativní zdroje s vysokým kontrastem|
|Potřebujete více zdrojů pro různé režimy DPI|Volitelné prostředky s vektorovou záložní|
|Duplikování obrazů|Jeden identifikátor na koncept obrázku|

 Proč přijmout image služby?

- Vždy získejte nejnovější obraz "pixel-perfect" z Visual Studia

- Můžete odeslat a používat své vlastní obrázky

- Není třeba testovat své obrázky, když systém Windows přidává nové měřítko DPI

- Řešení starých architektonických překážek ve vašich implementacích

  Panel nástrojů prostředí Visual Studio před a po použití služby image:

  ![Image Service před a po](../extensibility/media/image-service-before-and-after.png "Image Service před a po")

## <a name="how-it-works"></a>Jak to funguje
 Služba image může poskytnout bitmapovaný obrázek vhodný pro všechny podporované rozhraní rozhraní:

- WPF: Zdroj bitmapy

- WinForms: System.Drawing.Bitmap

- Win32: HBITMAP

  Diagram toku služby bitové kopie

  ![Vývojový diagram služby image](../extensibility/media/image-service-flow-diagram.png "Vývojový diagram služby image")

  **Přezdívky obrázků**

  Zástupný název obrázku (zkráceně zástupný název) je dvojice GUID/ID, která jednoznačně identifikuje datový zdroj obrázku nebo datový zdroj seznamu obrázků v knihovně obrázků.

  **Známé přezdívky**

  Sada zástupných názvů obrázků obsažená v katalogu obrázků sady Visual Studio a veřejně spotřební jakoukoli komponentou nebo rozšířením sady Visual Studio.

  **Soubory manifestu obrázku**

  Manifest obrazu (*.imagemanifest*) soubory jsou SOUBORY XML, které definují sadu obrazových datových zdrojů, zástupné názvy, které představují tyto prostředky, a skutečný obraz nebo obrázky, které představují každý datový zdroj. Manifesty obrázků můžete definovat samostatné obrázky nebo seznamy obrázků pro podporu staršího uznatých. Kromě toho existují atributy, které lze nastavit buď na datovém zdroji, nebo na jednotlivých obrázcích za každým datovým zdrojem, které mají změnit, kdy a jak jsou tyto prostředky zobrazeny.

  **Schéma manifestu obrázku**

  Kompletní manifest obrázku vypadá takto:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Import, Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Symboly**

 Jako pomůcku pro čitelnost a údržbu může manifest obrázku použít symboly pro hodnoty atributů. Symboly jsou definovány takto:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Dílčím**|**Definice**|
|Import|Importuje symboly daného souboru manifestu pro použití v aktuálním manifestu.|
|Identifikátor GUID|Symbol představuje identifikátor GUID a musí odpovídat formátování IDENTIFIKÁTORU GUID.|
|ID|Symbol představuje ID a musí být nezáporné celé číslo|
|Řetězec|Symbol představuje libovolnou řetězcovou hodnotu|

 Symboly rozlišují malá a velká písmena a odkazují se na něj pomocí syntaxe $(název symbolu):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Některé symboly jsou předdefinovány pro všechny manifesty. Ty lze použít v uri \<atribut zdroj \<> nebo import> prvek referenční cesty v místním počítači.

|||
|-|-|
|**Symbol**|**Popis**|
|CommonProgramFiles|Hodnota proměnné prostředí %CommonProgramFiles%|
|Místní AppData|Hodnota proměnné prostředí %LocalAppData%|
|Složka manifestu|Složka obsahující soubor manifestu|
|Mydocuments|Úplná cesta ke složce Dokumenty aktuálního uživatele|
|ProgramFiles|Hodnota proměnné prostředí %ProgramFiles%|
|Systém|Složka *Windows\System32*|
|Windir|Hodnota proměnné prostředí %WinDir%|

 **Image**

 Prvek \<Image> definuje obraz, na který lze odkazovat pomocí zástupného prvku. Identifikátor GUID a ID dohromady tvoří zástupný název obrázku. Zástupné symboly pro obraz musí být jedinečné v celé knihovně obrázků. Pokud více než jeden obrázek má daný zástupný název, první, který se setkal při vytváření knihovny je ten, který je zachován.

 Musí obsahovat alespoň jeden zdroj. Velikost-neutrální zdroje poskytne nejlepší výsledky v široké škále velikostí, ale nejsou vyžadovány. Pokud je služba požádána o obrázek o \<velikosti, která není definována v elementu Image> a neexistuje žádný zdroj neutrální velikost, služba zvolí zdroj pro nejlepší velikost a škáluje jej na požadovanou velikost.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Atribut**|**Definice**|
|Identifikátor GUID|[Povinné] Část guid zástupného symbolu obrázku|
|ID|[Povinné] ID část zástupného symbolu obrázku|
|AllowColorInversion|[Volitelné, výchozí hodnota true] Označuje, zda obraz může mít své barvy programově obrácené při použití na tmavém pozadí.|

 **Zdroj**

 Element \<Zdroj> definuje jeden zdrojový datový zdroj obrazu (XAML a PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Atribut**|**Definice**|
|Uri|[Povinné] Identifikátor URI, který definuje, odkud lze obrázek načíst. Může to být jedna z následujících možností:<br /><br /> - Identifikátor [URI balíčku](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) používající application:/// autoritu<br />- Absolutní odkaz na zdroj komponenty<br />- Cesta k souboru obsahujícímu nativní prostředek|
|Pozadí|[Nepovinné] Označuje, co na druhu pozadí zdroj je určen k použití.<br /><br /> Může to být jedna z následujících možností:<br /><br /> *Světlo:* Zdroj lze použít na světlém pozadí.<br /><br /> *Tmavá:* Zdroj lze použít na tmavém pozadí.<br /><br /> *HighContrast:* Zdroj lze použít na libovolném pozadí v režimu vysokého kontrastu.<br /><br /> *HighContrastLight:* Zdroj lze použít na světlém pozadí v režimu vysoký kontrast.<br /><br /> *HighContrastDark:* Zdroj lze použít na tmavém pozadí v režimu vysoký kontrast.<br /><br /> Pokud pozadí atribut je vynechán, zdroj lze použít na libovolném pozadí.<br /><br /> Pokud pozadí je *světlo*, *tmavý*, *HighContrastLight*nebo *HighContrastDark*, barvy zdroje nejsou nikdy obrácené. Pokud pozadí je vynechánnebo nastavena na *HighContrast*, inverze zdroje barvy je řízen a **image AllowColorInversion** atribut.|

Element \<Source> může mít přesně jeden z následujících volitelných podelementů:

||||
|-|-|-|
|**Element**|**Atributy (vše povinné)**|**Definice**|
|\<Velikost>|Hodnota|Zdroj bude použit pro obrázky dané velikosti (v jednotkách zařízení). Obrázek bude čtvercový.|
|\<> rozsahu velikosti|MinSize, MaxVelikost|Zdroj bude použit pro obrázky z MinSize na MaxSize (v jednotkách zařízení) včetně. Obrázek bude čtvercový.|
|\<Kóty>|Šířka, Výška|Zdroj bude použit pro obrázky dané šířky a výšky (v jednotkách zařízení).|
|\<> rozměrů|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Zdroj bude použit pro obrázky od minimální šířky/výšky do maximální šířky/výšky (v jednotkách zařízení) včetně.|

 Element \<Source> může mít \<také volitelný podelement NativeResource \<>, který definuje zdrojový>, který je načten z nativního sestavení, nikoli ze spravovaného sestavení.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Atribut**|**Definice**|
|Typ|[Povinné] Typ nativního prostředku, buď XAML nebo PNG|
|ID|[Povinné] Část ID celého čísla nativního prostředku|

 **Imagelist**

 ImageList \<> prvek definuje kolekci obrázků, které mohou být vráceny v jednom proužku. Pás je postaven na vyžádání, podle potřeby.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Atribut**|**Definice**|
|Identifikátor GUID|[Povinné] Část guid zástupného symbolu obrázku|
|ID|[Povinné] ID část zástupného symbolu obrázku|
|Externí|[Volitelné, výchozí false] Označuje, zda zástupný název obrázku odkazuje na obrázek v aktuálním manifestu.|

 Zástupný název pro obsažený obraz nemusí odkazovat na obrázek definovaný v aktuálním manifestu. Pokud obsažený obrázek nelze v knihovně obrázků najít, bude na jeho místě použit prázdný zástupný obrázek.

## <a name="using-the-image-service"></a>Použití služby image

### <a name="first-steps-managed"></a>První kroky (spravované)
 Chcete-li použít službu image, je třeba přidat odkazy na některé nebo všechny následující sestavení do projektu:

- *Soubor Microsoft.VisualStudio.ImageCatalog.dll*

  - Povinné, pokud používáte vestavěný katalog bitových obrázků **KnownMonikers**.

- *Soubor Microsoft.VisualStudio.Imaging.dll*

  - Povinné, pokud používáte **CrispImage** a **ImageThemingUtilities** v wpf uz).

- *Soubor Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Povinné, pokud používáte **ImageMoniker** a **ImageAttributes** typy.

  - **EmbedInteropTypes** by měla být nastavena na hodnotu true.

- *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime*

  - Povinné, pokud používáte typ **IVsImageService2.**

  - **EmbedInteropTypes** by měla být nastavena na hodnotu true.

- *Soubor DLL Microsoft.VisualStudio.Utilities.dll*

  - Povinné, pokud použijete **BrushToColorConverter** pro **ImageThemingUtilities.ImageBackgroundColor** v wpf uzly.

- *Microsoft.VisualStudio.Shell. \<VSVersion>.0*

  - Povinné, pokud používáte typ **IVsUIObject.**

- *Soubor Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Povinné, pokud používáte pomocné s ui související s winforms.

  - **EmbedInteropTypes** by měla být nastavena na hodnotu true

### <a name="first-steps-native"></a>První kroky (nativní)
 Chcete-li službu image používat, je třeba do projektu zahrnout některá nebo všechna následující záhlaví:

- **Soubor KnownImageIds.h**

  - Povinné, pokud používáte předdefinovaný katalog bitových obrázků **KnownMonikers**, ale nelze použít **typ ImageMoniker,** například při vracení hodnot z **IVsHierarchy GetGuidProperty** nebo **GetProperty** volání.

- **ZnámýMonikers.h**

  - Povinné, pokud používáte vestavěný katalog bitových obrázků **KnownMonikers**.

- **ImageParameters140.h**

  - Povinné, pokud používáte **ImageMoniker** a **ImageAttributes** typy.

- **VSShell140.h**

  - Povinné, pokud používáte typ **IVsImageService2.**

- **ImageThemingUtilities.h**

  - Povinné, pokud nejste schopni nechat image služby zpracovat motivy za vás.

  - Nepoužívejte toto záhlaví, pokud image služba zvládne vaše obrázkové motivy.

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - Povinné, pokud používáte pomocné ukazatele DPI získat aktuální DPI.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - Povinné, pokud používáte pomocné ukazatele povědomí DPI získat aktuální DPI.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Jak napíšu nové wpf ui?

1. Začněte přidáním odkazů na sestavení požadovaných ve výše uvedené části prvních kroků do projektu. Nemusíte přidávat všechny z nich, takže přidejte jen odkazy, které potřebujete. (Poznámka: Pokud používáte nebo máte přístup k **barvy** místo **brushes**, pak můžete přeskočit odkaz na **nástroje**, protože nebudete potřebovat převaděč.)

2. Vyberte požadovaný obrázek a získejte jeho zástupný název. Použijte **KnownMoniker**, nebo použijte vlastní, pokud máte vlastní obrázky a zástupné názvy.

3. Přidejte do xaml **crispimage.** (Viz níže příklad.)

4. Nastavte vlastnost **ImageThemingUtilities.ImageBackgroundColor** v hierarchii ui. (To by mělo být nastaveno v místě, kde je známa barva pozadí, ne nutně na **CrispImage**.) (Viz níže příklad.)

```xaml
<Window
  x:Class="WpfApplication.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">
  <Window.Resources>
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>
  </Window.Resources>
  <StackPanel Background="White" VerticalAlignment="Center"
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />
  </StackPanel>
</Window>
```

 **Jak lze aktualizovat stávající wpf uznané uzlina?**

 Aktualizace existujícího rozhraní WPF je poměrně jednoduchý proces, který se skládá ze tří základních kroků:

1. Nahraďte všechny \<prvky image \<> v uživatelském rozhraní prvky CrispImage>.

2. Změňte všechny atributy Source na Atributy zástupný název.

    - Pokud se obraz nikdy nezmění a používáte **Funkce Známé Monikers**, spojte staticky tuto vlastnost s **vlastností KnownMoniker**. (Viz výše uvedený příklad.)

    - Pokud se obrázek nikdy nezmění a používáte vlastní bitovou kopii, staticky se spojte s vlastním zástupný název.

    - Pokud image může změnit, svázat atribut Zástupný název na vlastnost kódu, která upozorní na změny vlastnosti.

3. Někde v hierarchii ui nastavte **ImageThemingUtilities.ImageBackgroundColor,** abyste se ujistili, že inverze barev funguje správně.

    - To může vyžadovat použití **BrushToColorConverter** třídy. (Viz výše uvedený příklad.)

## <a name="how-do-i-update-win32-ui"></a>Jak mohu aktualizovat win32 ui?
 Pokud je to vhodné, přidejte do kódu následující, abyste nahradili nezpracované načítání obrázků. Přepněte hodnoty pro vrácení HBITMAPs versus HICONs versus HIMAGELIST podle potřeby.

 **Získání služby image**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Vyžádání obrázku**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>Jak lze aktualizovat ui winforms?
 Pokud je to vhodné, přidejte do kódu následující, abyste nahradili nezpracované načítání obrázků. Podle potřeby přepněte hodnoty pro vrácení bitmap versus ikon.

 **Užitečné pomocí příkazu**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Získání služby image**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Vyžádejte si obrázek**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Jak se používají zástupné názvy obrázků v novém okně nástroje?
 Šablona projektu balíčku VSIX byla aktualizována pro Visual Studio 2015. Chcete-li vytvořit nové okno nástroje, klepněte pravým tlačítkem myši na projekt VSIX a **vyberte** > přidat**novou položku** (**Ctrl**+**Shift**+**A**). V části Uzel rozšiřitelnost pro jazyk projektu vyberte **Vlastní okno nástroje**, pojmenujte okno nástroje a stiskněte tlačítko **Přidat.**

 Toto jsou klíčová místa pro použití zástupných názvů v okně nástroje. Postupujte podle pokynů pro každou z nich:

1. Karta okna nástroje, když jsou karty dostatečně malé (také se používá v přepínači okna **Ctrl**+**Tab).**

    Přidejte tento řádek do konstruktoru pro třídu, která je odvozena od typu **ToolWindowPane:**

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Příkaz pro otevření okna nástroje.

    V souboru *.vsct* pro balíček upravte příkazové tlačítko okna nástroje:

   ```xml
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->
     <Icon guid="ImageCatalogGuid" id="Blank" />
     <!-- Add this -->
     <CommandFlag>IconIsMoniker</CommandFlag>
     <Strings>
       <ButtonText>MyToolWindow</ButtonText>
     </Strings>
   </Button>
   ```

   **Jak se používají zástupné názvy obrázků v existujícím okně nástroje?**

   Aktualizace existujícího okna nástroje pro použití zástupných názvů obrázků je podobná krokům pro vytvoření nového okna nástroje.

   Toto jsou klíčová místa pro použití zástupných názvů v okně nástroje. Postupujte podle pokynů pro každou z nich:

3. Karta okna nástroje, když jsou karty dostatečně malé (také se používá v přepínači okna **Ctrl**+**Tab).**

   1. Odeberte tyto řádky (pokud existují) v konstruktoru pro třídu, která je odvozena od typu **ToolWindowPane:**

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Podívejte se na krok #1 "Jak lze použít zástupné názvy obrázků v novém okně nástroje?" výše.

4. Příkaz pro otevření okna nástroje.

   - Podívejte se na krok #2 "Jak lze použít zástupné názvy obrázků v novém okně nástroje?" výše.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Jak se používají zástupné názvy obrázků v souboru .vsct?
 Aktualizujte soubor *.vsct,* jak je uvedeno v komentářích řádky níže:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
             Change the id attribute to be the ID of the desired image moniker. -->
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />
        <CommandFlag>DynamicVisibility</CommandFlag>
        <CommandFlag>DefaultInvisible</CommandFlag>
        <CommandFlag>DefaultDisabled</CommandFlag>
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>IconAndText</CommandFlag>
        <!-- Add the IconIsMoniker CommandFlag -->
        <CommandFlag>IconIsMoniker</CommandFlag>
        <Strings>
          <ButtonText>Quick Fixes...</ButtonText>
          <CommandName>Show Quick Fixes</CommandName>
          <CanonicalName>ShowQuickFixes</CanonicalName>
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>
        </Strings>
      </Button>
    </Buttons>
  </Commands>
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->
  <Symbols>
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">
      <IDSymbol name="cmdidMyCommand" value="0x9437" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```

 **Co když můj soubor VSCT musí číst také starší verze sady Visual Studio?**

 Starší verze sady Visual Studio nerozpoznávají příkazový příznak **IconIsMoniker.** Můžete použít obrázky ze služby image ve verzích sady Visual Studio, které ji podporují, ale nadále používat staré image ve starších verzích sady Visual Studio. Chcete-li to provést, ponecháte soubor *.vsct* beze změny (a proto je kompatibilní se staršími verzemi sady Visual Studio) a vytvoříte soubor CSV (hodnoty oddělené \<čárkami), který se mapuje z dvojic GUID/ID definovaných v bitmapách *souboru .vsct*> element na dvojice zástupných guid/ID symbolů obrázku.

 Formát mapovacího souboru CSV je:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 Soubor CSV je nasazen s balíčkem a jeho umístění je určeno vlastností **IconMappingFilename** atributu **ProvideMenuResource** package:

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **Název IconMappingFile** je buď relativní cesta implicitně zakořeněná v $PackageFolder$ (jako v příkladu výše), nebo absolutní cesta explicitně zakořeněná v adresáři definovaném proměnnou prostředí, například *@"%UserProfile%\dir1\dir2\MyMappingFile.csv"*.

## <a name="how-do-i-port-a-project-system"></a>Jak lze přenést systém projektu?
 **Jak dodat ImageMonikers pro projekt**

1. Implementujte **VSHPROPID_SupportsIconMonikers** na **IVsHierarchy**projektu a vraťte hodnotu true.

2. Implementujte **buď VSHPROPID_IconMonikerImageList** (pokud původní projekt použil **VSHPROPID_IconImgList**) nebo **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid** **VSHPROPID_OpenFolderIconMonikerId** (pokud původní projekt použil **VSHPROPID_IconHandle** a **VSHPROPID_OpenFolderIconHandle**).

3. Změňte implementaci původních vshpropidů pro ikony k vytvoření "starší" verze ikon, pokud rozšíření body požadovat. **IVsImageService2** poskytuje funkce nezbytné k získání těchto ikon

   **Zvláštní požadavky na příchutě projektu VB/C#**

   Implementujte **VSHPROPID_SupportsIconMonikers** pouze v případě, že zjistíte, že váš projekt je **nejvzdálenější flavor**. V opačném případě skutečné vnější chuť nemusí podporovat popisy obrázků ve skutečnosti a vaše základní chuť může účinně "skrýt" přizpůsobené obrázky.

   **Jak se používají zástupné názvy obrázků v cps?**

   Nastavení vlastních bitových kopií v cps (Common Project System) lze provést ručně nebo pomocí šablony položky, která je dodávána s sadou SDK rozšiřitelnostsystému systému projektu.

   **Použití sady SDK rozšiřitelnosti systému projektu**

   Chcete-li přizpůsobit obrázky CPS, postupujte podle pokynů na [adrese Poskytnout vlastní ikony pro typ projektu nebo položku.](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) Další informace o cps lze nalézt v [dokumentaci rozšiřitelnosti systému Visual Studio Project System](https://github.com/Microsoft/VSProjectSystem)

   **Ruční použití ImageMonikers**

4. Implementujte a exportujte rozhraní **IProjectTreeModifier** v systému projektu.

5. Určete, který **zástupek ZnáméMoniker** nebo vlastní obrázek chcete použít.

6. V **ApplyModifications** metoda provést následující někde v metodě před vrácením nového stromu, podobně jako v následujícím příkladu:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Pokud vytváříte nový strom, můžete nastavit vlastní obrázky předáním požadovaných zástupných názvů do metody NewTree, podobně jako v níže uvedeném příkladu:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,
                                                /*filePath*/<value>,
                                                /*browseObjectProperties*/<value>,
                                                icon,
                                                expandedIcon);
   ```

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Jak lze převést z reálného proužku obrázku na zástupný proužek?
 **Potřebuji podpořit HIMAGELISTs**

 Pokud je již existující obrazový proužek pro váš kód, který chcete aktualizovat používat službu image, ale jsou omezeny api, které vyžadují předávání kolem seznamy obrázků, stále můžete získat výhody image služby. Chcete-li vytvořit zástupný název obrázku, postupujte podle následujících kroků a vytvořte manifest z existujících zástupných názvů.

1. Spusťte nástroj **ManifestFromResources** a předavěte jej k proužek obrázku. Tím se vytvoří manifest pro pás.

   - Doporučeno: zadejte nevýchozí název manifestu tak, aby vyhovoval jeho použití.

2. Pokud používáte pouze **KnownMonikers**, proveďte následující kroky:

   - Nahraďte \<oddíl obrázky \<> manifestu obrázky/>.

   - Odeberte všechna ID podbitých obrázků (cokoli s \<názvem imagestrip>_##).

   - Doporučeno: přejmenujte symbol AssetsGuid a symbol obrazového pásu tak, aby vyhovoval jeho použití.

   - Nahradit každý **ContainedImage**'s GUID s $(ImageCatalogGuid), nahradit každý **ContainedImage**'s ID s $(\<zástupný název>) a přidejte External="true" atribut pro každý **ContainedImage**

       - \<zástupný název> by měl být nahrazen **knownmoniker,** který odpovídá obrázku, ale "KnownMonikers." z názvu odebrána.

   - Přidejte <\\ Import Manifest="$(ManifestFolder)<\>Relativní instalační dir cestu k * \Microsoft.VisualStudio.ImageCatalog.imagemanifest" /\*> na \<začátek sekce Symboly>.

       - Relativní cesta je určena umístění majestátností definované ve vytváření nastavení manifestu.

3. Spusťte nástroj **ManifestToCode** pro generování obálky tak, aby existující kód má zástupný název, který lze použít k dotazování služby image pro obrazový proužek.

   - Doporučeno: zadejte nevýchozí názvy pro obálky a obory názvů tak, aby vyhovovaly jejich použití.

4. Proveďte všechny přidá, nastavení authoring / nasazení a další změny kódu pro práci s image služby a nové soubory.

   Ukázkový manifest včetně interních i externích obrázků, abyste zjistili, jak by měl vypadat:

```xml
<?xml version="1.0"?>
<ImageManifest
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">

  <Symbols>
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest
         where $(ManifestFolder) is the deployed location of this manifest. -->
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />
    <ID Name="MyImage_0" Value="100" />
    <ID Name="MyImage_1" Value="101" />
    <ID Name="InternalList" Value="1001" />
    <ID Name="ExternalList" Value="1002" />
  </Symbols>

  <Images>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">
      <Source Uri="$(Resources)/MyImage_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">
      <Source Uri="$(Resources)/MyImage_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>

  <ImageLists>
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />
    </ImageList>
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />
    </ImageList>
  </ImageLists>

</ImageManifest>
```

 **Nepotřebuji podporovat HIMAGELISTs**

1. Určete sadu **známých monikers,** které odpovídají obrázkům v pásu obrázku, nebo vytvořte vlastní zástupné názvy pro obrázky v obrazovém pásu.

2. Aktualizujte bez ohledu na mapování, které jste použili k získání obrázku na požadovaný index v proužku obrázku použít zástupné názvy místo.

3. Aktualizujte kód, abyste pomocí služby image požadovali zástupné názvy prostřednictvím aktualizovaného mapování. (To může znamenat aktualizaci **crispimages** pro spravovaný kód nebo vyžádání HBITMAPs nebo HICONs z image služby a předávání je kolem pro nativní kód.)

## <a name="testing-your-images"></a>Testování obrázků
 Pomocí nástroje Prohlížeč knihovny obrázků můžete otestovat manifesty obrázků, abyste se ujistili, že je vše správně nakonto. Nástroj najdete v sadě [Visual Studio 2015 SDK](visual-studio-sdk.md). Dokumentaci k tomuto nástroji a dalším naleznete [zde](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015).

## <a name="additional-resources"></a>Další zdroje

### <a name="samples"></a>ukázky
 Několik ukázky Visual Studio na GitHubu byly aktualizovány ukázat, jak používat službu bitové kopie jako součást různých bodů rozšiřitelnosti sady Visual Studio.

 Zkontrolujte [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) nejnovější vzorky.

### <a name="tooling"></a>Nástroje
 Sada nástrojů podpory pro službu Image Service byla vytvořena pro pomoc při vytváření nebo aktualizaci ui, který pracuje se službou Image Service. Další informace o jednotlivých nástrojích naleznete v dokumentaci dodané s nástroji. Nástroje jsou součástí sady [Visual Studio 2015 SDK](visual-studio-sdk.md).

 **ManifestFromResources**

 Nástroj Manifest from Resources pořídí seznam obrazových prostředků (PNG nebo XAML) a vygeneruje soubor manifestu obrázku pro použití těchto obrazů se službou image.

 **ManifestToCode**

 Nástroj Manifest to Code pořídí soubor manifestu obrazu a vygeneruje soubor obálky pro odkazování na hodnoty manifestu v kódu (C++, C#, nebo VB) nebo *.vsct.*

 **ImageLibraryViewer**

 Nástroj prohlížeč knihovny obrázků může načíst manifesty obrázků a umožňuje uživateli s nimi manipulovat stejným způsobem, jakým by visual studio zajistilo, že manifest je vytvořen správně. Uživatel může měnit pozadí, velikosti, nastavení DPI, vysoký kontrast a další nastavení. Zobrazí také informace o načítání, aby vyhledaly chyby v manifestech, a zobrazí zdrojové informace pro každý obrázek v manifestu.

## <a name="faq"></a>Nejčastější dotazy

- Existují všechny závislosti, které je \<nutné zahrnout při načítání reference Include="Microsoft.VisualStudio.*. Interop.14.0.DesignTime" />?

  - Nastavte embedInteropTypes="true" na všech interop dll.

- Jak nasadit manifest bitové kopie s rozšířením?

  - Přidejte soubor *.imagemanifest* do projektu.

  - Nastavte "Zahrnout do VSIX" na True.

- Aktualizuji svůj systém projektu CPS. Co se stalo s **ImageName** a **StockIconService**?

  - Tyto byly odebrány při aktualizaci serveru CPS na názvy zástupcích. Již není nutné volat **StockIconService**, stačí předat požadovaný **KnownMoniker** na metodu nebo vlastnost pomocí **ToProjectSystemType()** extension metoda v utilitÁCH CPS. Mapování z **ImageName** na **KnownMonikers** níže:

    |||
    |-|-|
    |**Imagename**|**ZnámýMoniker**|
    |ImageName.OfflineWebApp|Známé imageIds.Web|
    |ImageName.WebReferencesFolder|Známé imageIds.Web|
    |ImageName.OpenReferenceFolder|Známé ImageIds.FolderOtevřeno|
    |ImageName.ReferenceFolder|KnownImageIds.Reference|
    |ImageName.Reference|KnownImageIds.Reference|
    |ImageName.SdlWebReference|Složka KnownImageIds.WebReferenceFolder|
    |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|
    |ImageName.Folder|Známé ImageIds.FolderClosed|
    |ImageName.OpenFolder|Známé ImageIds.FolderOtevřeno|
    |ImageName.ExcludedFolder|Známé imageIds.HiddenFolderClosed|
    |ImageName.OpenExcludedFolder|Známé ImageIds.HiddenFolderOtevřeno|
    |ImageName.ExcludedFile|Soubor KnownImageIds.HiddenFile|
    |ImageName.DependentFile|Soubor KnownImageIds.GenerateFile|
    |ImageName.MissingFile|Funkce KnownImageIds.DocumentWarning|
    |ImageName.WindowsForm|KnownImageIds.WindowsForm|
    |ImageName.WindowsUserControl|Ovládací prvek KnownImageIds.UserControl|
    |ImageName.WindowsComponent|Soubor KnownImageIds.ComponentFile|
    |ImageName.XmlSchema|Známé ImageIds.XMLSchema|
    |ImageName.XmlFile|Soubor KnownImageIds.XMLFile|
    |ImageName.WebForm|Známé imageIds.Web|
    |ImageName.WebService|Služba KnownImageIds.WebService|
    |ImageName.WebUserControl|Ovládací prvek KnownImageIds.WebUserControl|
    |ImageName.WebCustomUserControl|Ovládací prvek KnownImageIds.WebCustomControl|
    |ImageName.AspPage|Soubor KnownImageIds.ASPFile|
    |ImageName.GlobalApplicationClass|Soubor KnownImageIds.SettingsFile|
    |ImageName.WebConfig|Soubor KnownImageIds.ConfigurationFile|
    |ImageName.HtmlPage|Soubor KnownImageIds.HTMLFile|
    |ImageName.StyleSheet|Soubor Svitek.Ids.KnownImageIDs.StyleSheet|
    |ImageName.ScriptFile|Soubor KnownImageIds.JSScript|
    |ImageName.TextFile|Známé ImageIds.Dokument|
    |ImageName.SettingsFile|Známé ImageIds.Settings|
    |ImageName.Resources|KnownImageIds.DocumentGroup|
    |ImageName.Bitmap|Známé ImageIds.Image|
    |ImageName.Icon|Soubor KnownImageIds.IconFile|
    |ImageName.Image|Známé ImageIds.Image|
    |ImageName.ImageMap|Soubor KnownImageIds.ImageMapFile|
    |ImageName.XWorld|Soubor KnownImageIds.XWorldFile|
    |ImageName.Audio|Známé ImageIds.Zvuk|
    |ImageName.Video|MediaImageIds.Media|
    |ImageName.Cab|KnownImageIds.CABProject|
    |ImageName.Jar|Soubor KnownImageIds.JARFile|
    |ImageName.DataEnvironment|Soubor KnownImageIds.DataTable|
    |ImageName.PreviewFile|Známé ImageIds.Report|
    |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|
    |Soubor ImageName.XsltFile|Známé ImageIds.XSLTransform|
    |ImageName.Cursor|Soubor KnownImageIds.CursorFile|
    |ImageName.AppDesignerFolder|Vlastnost KnownImageIds.Property|
    |ImageName.Data|Známé ImageIds.Database|
    |ImageName.Application|KnownImageIds.Application|
    |ImageName.DataSet|KnownImageIds.DatabaseGroup|
    |ImageName.Pfx|Známé ImageIds.Certificate|
    |ImageName.Snk|Známé ImageIds.Rule|
    |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|
    |ImageName.CSharpProject|Název KnownImageIds.CSProjectNode|
    |ImageName.Empty|Známé imageIds.Blank|
    |ImageName.MissingFolder|KnownImageIds.FolderOffline|
    |ImageName.SharedImportReference|KnownImageIds.SharedProject|
    |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|
    |ImageName.SharedProjectVc|Projekt KnownImageIds.CPPSharedProject|
    |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|
    |ImageName.CsharpCodeFile|Název KnownImageIds.CSFileNode|
    |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - Aktualizuji svého poskytovatele seznamu dokončení. Co **KnownMonikers** zápas na staré **StandardGlyphGroup** a **StandardGlyph** hodnoty?

    ||||
    |-|-|-|
    |Třída GlyphGroupClass|GlyphItemPublic|ClassPublic|
    |Třída GlyphGroupClass|GlyphItemInterní|ClassInternal|
    |Třída GlyphGroupClass|GlyphItemFriend|ClassInternal|
    |Třída GlyphGroupClass|GlyphItemProtected|ClassProtected|
    |Třída GlyphGroupClass|GlyphItemPrivate|ClassPrivate|
    |Třída GlyphGroupClass|GlyphItemZkratka|Zkratka class|
    |Konstanta GlyphGroup|GlyphItemPublic|ConstantPublic|
    |Konstanta GlyphGroup|GlyphItemInterní|ConstantInternal|
    |Konstanta GlyphGroup|GlyphItemFriend|ConstantInternal|
    |Konstanta GlyphGroup|GlyphItemProtected|ConstantProtected|
    |Konstanta GlyphGroup|GlyphItemPrivate|ConstantPrivate|
    |Konstanta GlyphGroup|GlyphItemZkratka|Zkratka Konstanta|
    |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|
    |GlyphGroupDelegate|GlyphItemInterní|Interní delegát|
    |GlyphGroupDelegate|GlyphItemFriend|Interní delegát|
    |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|
    |GlyphGroupDelegate|GlyphItemZkratka|Zástupce delegáta|
    |GlyfGroupEnum|GlyphItemPublic|VýčetVeřejný|
    |GlyfGroupEnum|GlyphItemInterní|VýčetInterní|
    |GlyfGroupEnum|GlyphItemFriend|VýčetInterní|
    |GlyfGroupEnum|GlyphItemProtected|EnumerationProtected|
    |GlyfGroupEnum|GlyphItemPrivate|Výčetsoukromé|
    |GlyfGroupEnum|GlyphItemZkratka|VýčetZkratka|
    |GlyphGroupEnumMember|GlyphItemPublic|VýčetItemPublic|
    |GlyphGroupEnumMember|GlyphItemInterní|VýčetItemInternal|
    |GlyphGroupEnumMember|GlyphItemFriend|VýčetItemInternal|
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationItemProtected|
    |GlyphGroupEnumMember|GlyphItemPrivate|VýčetItemPrivate|
    |GlyphGroupEnumMember|GlyphItemZkratka|VýčetPoložkyZkratka|
    |Událost GlyphGroupEvent|GlyphItemPublic|EventPublic|
    |Událost GlyphGroupEvent|GlyphItemInterní|EventInternal|
    |Událost GlyphGroupEvent|GlyphItemFriend|EventInternal|
    |Událost GlyphGroupEvent|GlyphItemProtected|EventProtected|
    |Událost GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |Událost GlyphGroupEvent|GlyphItemZkratka|EventShortcut|
    |Výjimka skupiny glyphgroup|GlyphItemPublic|ExceptionPublic|
    |Výjimka skupiny glyphgroup|GlyphItemInterní|ExceptionInternal|
    |Výjimka skupiny glyphgroup|GlyphItemFriend|ExceptionInternal|
    |Výjimka skupiny glyphgroup|GlyphItemProtected|ExceptionProtected|
    |Výjimka skupiny glyphgroup|GlyphItemPrivate|ExceptionPrivate|
    |Výjimka skupiny glyphgroup|GlyphItemZkratka|ExceptionShortcut|
    |GlyphGroupField|GlyphItemPublic|FieldPublic|
    |GlyphGroupField|GlyphItemInterní|PoleInterní|
    |GlyphGroupField|GlyphItemFriend|PoleInterní|
    |GlyphGroupField|GlyphItemProtected|FieldProtected|
    |GlyphGroupField|GlyphItemPrivate|PoleSoukromé|
    |GlyphGroupField|GlyphItemZkratka|Zkratka pole|
    |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupInterface|GlyphItemInterní|Rozhraní Interní|
    |GlyphGroupInterface|GlyphItemFriend|Rozhraní Interní|
    |GlyphGroupInterface|GlyphItemProtected|Rozhraní Protected|
    |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupInterface|GlyphItemZkratka|Zástupce rozhraní|
    |GlyphGroupMakro|GlyphItemPublic|MakroPublic|
    |GlyphGroupMakro|GlyphItemInterní|MakroInterní|
    |GlyphGroupMakro|GlyphItemFriend|MakroInterní|
    |GlyphGroupMakro|GlyphItemProtected|MacroProtected|
    |GlyphGroupMakro|GlyphItemPrivate|MacroPrivate|
    |GlyphGroupMakro|GlyphItemZkratka|Zástupce maker|
    |Mapa skupiny glyfů|GlyphItemPublic|Mapová veřejná|
    |Mapa skupiny glyfů|GlyphItemInterní|MapVnitřní|
    |Mapa skupiny glyfů|GlyphItemFriend|MapVnitřní|
    |Mapa skupiny glyfů|GlyphItemProtected|MapProtected|
    |Mapa skupiny glyfů|GlyphItemPrivate|Mapprivate|
    |Mapa skupiny glyfů|GlyphItemZkratka|Mapovat zkratku|
    |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|
    |GlyphGroupMapItem|GlyphItemInterní|MapItemInterní|
    |GlyphGroupMapItem|GlyphItemFriend|MapItemInterní|
    |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|
    |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|
    |GlyphGroupMapItem|GlyphItemZkratka|Zkratka MapItem|
    |Metoda GlyphGroupMethod|GlyphItemPublic|MethodPublic|
    |Metoda GlyphGroupMethod|GlyphItemInterní|MetodaInterní|
    |Metoda GlyphGroupMethod|GlyphItemFriend|MetodaInterní|
    |Metoda GlyphGroupMethod|GlyphItemProtected|MethodProtected|
    |Metoda GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|
    |Metoda GlyphGroupMethod|GlyphItemZkratka|Zkratka metody|
    |Přetížení skupiny glyphgroup|GlyphItemPublic|MethodPublic|
    |Přetížení skupiny glyphgroup|GlyphItemInterní|MetodaInterní|
    |Přetížení skupiny glyphgroup|GlyphItemFriend|MetodaInterní|
    |Přetížení skupiny glyphgroup|GlyphItemProtected|MethodProtected|
    |Přetížení skupiny glyphgroup|GlyphItemPrivate|MethodPrivate|
    |Přetížení skupiny glyphgroup|GlyphItemZkratka|Zkratka metody|
    |Modul GlyphGroupModule|GlyphItemPublic|ModulVeřejný|
    |Modul GlyphGroupModule|GlyphItemInterní|ModulInterní|
    |Modul GlyphGroupModule|GlyphItemFriend|ModulInterní|
    |Modul GlyphGroupModule|GlyphItemProtected|ModulProtected|
    |Modul GlyphGroupModule|GlyphItemPrivate|Modul Soukromý|
    |Modul GlyphGroupModule|GlyphItemZkratka|ModulZkratka|
    |GlyphGroupNamespace|GlyphItemPublic|Obor názvů Veřejný|
    |GlyphGroupNamespace|GlyphItemInterní|Obor názvůInterní|
    |GlyphGroupNamespace|GlyphItemFriend|Obor názvůInterní|
    |GlyphGroupNamespace|GlyphItemProtected|Obor názvůchráněný|
    |GlyphGroupNamespace|GlyphItemPrivate|Obor názvůPrivate|
    |GlyphGroupNamespace|GlyphItemZkratka|Zástupce oboru názvů|
    |GlyphGroupOperator|GlyphItemPublic|OperátorPublic|
    |GlyphGroupOperator|GlyphItemInterní|OperátorInterní|
    |GlyphGroupOperator|GlyphItemFriend|OperátorInterní|
    |GlyphGroupOperator|GlyphItemProtected|OperátorProtected|
    |GlyphGroupOperator|GlyphItemPrivate|OperátorPrivate|
    |GlyphGroupOperator|GlyphItemZkratka|OperátorZástupce|
    |Vlastnost GlyphGroupProperty|GlyphItemPublic|PropertyPublic|
    |Vlastnost GlyphGroupProperty|GlyphItemInterní|PropertyInternal|
    |Vlastnost GlyphGroupProperty|GlyphItemFriend|PropertyInternal|
    |Vlastnost GlyphGroupProperty|GlyphItemProtected|PropertyProtected|
    |Vlastnost GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|
    |Vlastnost GlyphGroupProperty|GlyphItemZkratka|PropertyZkratka vlastnosti|
    |GlyphGroupStruct|GlyphItemPublic|StrukturaVeřejná|
    |GlyphGroupStruct|GlyphItemInterní|StrukturaVnitřní|
    |GlyphGroupStruct|GlyphItemFriend|StrukturaVnitřní|
    |GlyphGroupStruct|GlyphItemProtected|StructureProtected|
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|
    |GlyphGroupStruct|GlyphItemZkratka|Zkratka Structure|
    |Šablona skupiny GlyphGroup|GlyphItemPublic|ŠablonaVeřejná|
    |Šablona skupiny GlyphGroup|GlyphItemInterní|ŠablonaInterní|
    |Šablona skupiny GlyphGroup|GlyphItemFriend|ŠablonaInterní|
    |Šablona skupiny GlyphGroup|GlyphItemProtected|ŠablonaChráněná|
    |Šablona skupiny GlyphGroup|GlyphItemPrivate|ŠablonaSoukromá|
    |Šablona skupiny GlyphGroup|GlyphItemZkratka|Zástupce šablony|
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInterní|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtectedProtected|
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GlyphItemZkratka|TypeDefinitionZkratk|
    |GlyphGroupType|GlyphItemPublic|TypePublic|
    |GlyphGroupType|GlyphItemInterní|TypeInternal|
    |GlyphGroupType|GlyphItemFriend|TypeInternal|
    |GlyphGroupType|GlyphItemProtected|TypeProtected|
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|
    |GlyphGroupType|GlyphItemZkratka|TypeShortcut|
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|
    |GlyphGroupUnion|GlyphItemInterní|UnionInternal|
    |GlyphGroupUnion|GlyphItemFriend|UnionInternal|
    |GlyphGroupUnion|GlyphItemProtected|UnionProtected|
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|
    |GlyphGroupUnion|GlyphItemZkratka|UnionShortcut|
    |Proměnná glyphgroup|GlyphItemPublic|FieldPublic|
    |Proměnná glyphgroup|GlyphItemInterní|PoleInterní|
    |Proměnná glyphgroup|GlyphItemFriend|PoleInterní|
    |Proměnná glyphgroup|GlyphItemProtected|FieldProtected|
    |Proměnná glyphgroup|GlyphItemPrivate|PoleSoukromé|
    |Proměnná glyphgroup|GlyphItemZkratka|Zkratka pole|
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|
    |GlyphGroupValueType|GlyphItemInterní|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemZkratka|Zkratka ValueType|
    |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|
    |GlyphGroupIntrinsic|GlyphItemInterní|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|
    |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|
    |GlyphGroupIntrinsic|GlyphItemZkratka|Objektový zkrat|
    |Metoda GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|
    |Metoda GlyphGroupJSharpMethod|GlyphItemInterní|MetodaInterní|
    |Metoda GlyphGroupJSharpMethod|GlyphItemFriend|MetodaInterní|
    |Metoda GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|
    |Metoda GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|
    |Metoda GlyphGroupJSharpMethod|GlyphItemZkratka|Zkratka metody|
    |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|
    |GlyphGroupJSharpField|GlyphItemInterní|PoleInterní|
    |GlyphGroupJSharpField|GlyphItemFriend|PoleInterní|
    |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|
    |GlyphGroupJSharpField|GlyphItemPrivate|PoleSoukromé|
    |GlyphGroupJSharpField|GlyphItemZkratka|Zkratka pole|
    |Třída GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|
    |Třída GlyphGroupJSharpClass|GlyphItemInterní|ClassInternal|
    |Třída GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|
    |Třída GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|
    |Třída GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|
    |Třída GlyphGroupJSharpClass|GlyphItemZkratka|Zkratka class|
    |GlyphGroupJSharpNamespace|GlyphItemPublic|Obor názvů Veřejný|
    |GlyphGroupJSharpNamespace|GlyphItemInterní|Obor názvůInterní|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|Obor názvůInterní|
    |GlyphGroupJSharpNamespace|GlyphItemProtected|Obor názvůchráněný|
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|Obor názvůPrivate|
    |GlyphGroupJSharpNamespace|GlyphItemZkratka|Zástupce oboru názvů|
    |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupJSharpInterface|GlyphItemInterní|Rozhraní Interní|
    |GlyphGroupJSharpInterface|GlyphItemFriend|Rozhraní Interní|
    |GlyphGroupJSharpInterface|GlyphItemProtected|Rozhraní Protected|
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupJSharpInterface|GlyphItemZkratka|Zástupce rozhraní|
    |Chyba skupiny GlyphGroupError||Chyba stavu|
    |Soubor Glyfů||Soubor classfile|
    |Sestava glyfů||Referenční informace|
    |Knihovna glyfů||Knihovna|
    |Projekt GlyphVB||VBProjektNode|
    |Projekt GlyphCool||CsProjectNode|
    |Projekt GlyphCpp||CPPProjectNode|
    |GlyphDialogId||Dialog|
    |Složka GlyphOpenFolder||Otevřená složka|
    |Složka GlyphClosedFolder||Složka uzavřena|
    |Glyfová šipka||PřejítDalší|
    |Soubor GlyphCSharpFile||CsFileNode|
    |Rozšíření GlyphCSharpExpansion||Fragment kódu|
    |Klíčové slovo glyf||Klíčové slovo Intellisense|
    |Informace o glyfech||StatusInformace|
    |Odkaz na glyfy||ClassMethodReference|
    |Glyfrecursion||Rekurze|
    |GlyphXmlItem||Značka|
    |GlyphJSharpProject||DocumentCollection|
    |GlyphJSharpDocument||Dokument|
    |GlyphForwardType||PřejítDalší|
    |Graf Glyfy||Volání|
    |Glyfový graf||Volání|
    |Upozornění na glyfy||Upozornění na stav|
    |GlyphMaybeReference||Otazník|
    |GlyphMaybeCaller||Volání|
    |GlyfyMaybeCall||Volání|
    |Metoda GlyphExtensionMethod||Metoda rozšíření|
    |GlyphExtensionMethodInternal||Metoda rozšíření|
    |GlyphExtensionMethodFriend||Metoda rozšíření|
    |GlyphExtensionMethodProtected||Metoda rozšíření|
    |GlyphExtensionMethodPrivate||Metoda rozšíření|
    |GlyphExtensionMethod||Metoda rozšíření|
    |Atribut GlyphXmlAttribute||Xmlattribute|
    |GlyphXmlChild||Xmlelement|
    |GlyphXmlDescendant||XmlDescendant|
    |GlyphXmlNamespace||Xmlnamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |Kontrola atributů GlyphXml||XmlAttributeHighConfidence|
    |GlyphXmlChildQuestion||XmlElementLowConfidence|
    |Kontrola GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlDescendantQuestion||XmlDescendantLowDůvěra|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |Upozornění na dokončení glyfů||Upozornění intellisense|
