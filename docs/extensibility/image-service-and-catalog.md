---
title: Služba a katalog imagí | Microsoft Docs
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2647c09718f17235a3024f5787a0b85a7633ee1
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982240"
---
# <a name="image-service-and-catalog"></a>Služba a katalog imagí
Tento kuchařka obsahuje doprovodné materiály a osvědčené postupy pro přijetí služby image a katalogu imagí sady Visual Studio představené v aplikaci Visual Studio 2015.

 Image Service představená v aplikaci Visual Studio 2015 umožňuje vývojářům získat nejlepší obrázky pro zařízení a vybraný motiv uživatele k zobrazení obrázku, včetně oprav pro kontext, ve kterém se zobrazují. Přijetí služby imagí vám pomůže eliminovat hlavní užitečné body související s údržbou prostředků, škálováním na HDPI a s nimi.

|||
|-|-|
|**Problémy dnes**|**Řešení**|
|Prolnutí barvy pozadí|Vestavěná směs alfa|
|Obrázky (některé)|Metadata motivu|
|Vysoký kontrast režim|Alternativní prostředky Vysoký kontrast|
|Pro různé režimy DPI je potřeba víc prostředků.|Vybratelné prostředky s využitím Fallback pro použití vektoru|
|Duplicitní obrázky|Koncept jednoho identifikátoru na bitovou kopii|

 Proč přijmout službu Image Service?

- Vždycky z Visual studia získat nejnovější obraz "z" pixelů – dokonalý

- Můžete odesílat a používat vlastní image.

- Nemusíte testovat své image, když Windows přidá nové škálování DPI.

- Vyřeší staré prahové hodnoty ve vašich implementacích.

  Panel nástrojů prostředí sady Visual Studio před a po použití služby Image Service:

  ![Před a po – služba Image Service](../extensibility/media/image-service-before-and-after.png "Před a po – služba Image Service")

## <a name="how-it-works"></a>Jak to funguje
 Služba image může poskytovat obrázek rastrového obrázku, který je vhodný pro všechny podporované architektury uživatelského rozhraní:

- WPF: BitmapSource

- WinForms: System. Drawing. Bitmap

- Win32: HBITMAP

  Diagram toku služby image

  ![Diagram toku služby image](../extensibility/media/image-service-flow-diagram.png "Diagram toku služby image")

  **Monikery imagí**

  Moniker obrázku (neboli moniker pro krátký) je dvojice identifikátorů GUID a ID, která jednoznačně identifikuje prostředek obrázku nebo prostředek seznamu obrázků v knihovně imagí.

  **Známé monikery**

  Sada zástupných názvů imagí obsažených v katalogu imagí sady Visual Studio a veřejně obspotřebních komponent a rozšíření sady Visual Studio.

  **Image – soubory manifestu**

  Soubory manifestu obrázků ( *. imagemanifest*) jsou soubory XML, které definují sadu prostředků obrázků, monikery, které tyto prostředky představují, a skutečný obrázek nebo obrázky, které představují jednotlivé assety. Manifesty obrázků mohou definovat samostatné obrázky nebo seznamy obrázků pro podporu starší verze uživatelského rozhraní. Kromě toho existují atributy, které lze nastavit buď na Asset, nebo na jednotlivých obrázcích za každým Assetem, aby se změnily, kdy a jak se tyto prostředky zobrazují.

  **Schéma manifestu obrázku**

  Úplný manifest obrázku vypadá takto:

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

 V rámci podpory čitelnosti a údržby může manifest obrázku používat symboly pro hodnoty atributů. Symboly jsou definovány takto:

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
|**Dílčí element**|**Definition**|
|Importovat|Importuje symboly daného souboru manifestu pro použití v aktuálním manifestu.|
|Hlavních|Symbol představuje GUID a musí odpovídat formátování identifikátoru GUID.|
|ID|Symbol představuje ID a musí být nezáporné celé číslo.|
|String|Symbol představuje libovolnou řetězcovou hodnotu.|

 V symbolech rozlišuje velká a malá písmena a jsou odkazovány pomocí syntaxe $ (symbol-Name):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Některé symboly jsou předdefinované pro všechny manifesty. Ty lze použít v atributu identifikátoru URI \<zdrojového > nebo \<Import > elementu do odkazů na cesty na místním počítači.

|||
|-|-|
|**Písmeno**|**Popis**|
|CommonProgramFiles|Hodnota proměnné prostředí% CommonProgramFiles%|
|LocalAppData|Hodnota proměnné prostředí% LocalAppData%|
|ManifestFolder|Složka obsahující soubor manifestu|
|Dokumenty|Úplná cesta ke složce dokumenty aktuálního uživatele|
|ProgramFiles|Hodnota proměnné prostředí% ProgramFiles%|
|Systém|Složka *Windows\System32*|
|Adresář|Hodnota proměnné prostředí% WinDir%|

 **Obrázek**

 Element \<image > definuje obrázek, na který může odkazovat moniker. Identifikátor GUID a ID, které se přijímají společně tvoří moniker bitové kopie. Moniker obrázku musí být v celé knihovně imagí jedinečný. Pokud má více než jeden obrázek daný moniker, při sestavování knihovny je ten, který se zachovává.

 Musí obsahovat alespoň jeden zdroj. Velikost neutrálních zdrojů poskytne nejlepší výsledky napříč širokou škálou velikostí, ale nevyžadují se. Je-li služba požádána o obrázek velikosti, která není definována v prvku \<image > element a neexistuje žádný neutrální zdroj, služba zvolí nejlepší zdroj specifický pro danou velikost a změní velikost na požadovanou velikost.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Atribut**|**Definition**|
|Hlavních|Požadovanou Část GUID monikeru image|
|ID|Požadovanou Část ID monikeru bitové kopie|
|AllowColorInversion|[Volitelné, výchozí hodnota true] Určuje, zda může být barva obrázku při použití na tmavém pozadí převrácena prostřednictvím kódu programu.|

 **Zdrojová**

 Zdrojový element > \<definuje jeden prostředek zdroje obrázku (XAML a PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Atribut**|**Definition**|
|identifikátor URI|Požadovanou Identifikátor URI, který definuje, ze kterého může být obrázek načten. Může to být jedna z následujících:<br /><br /> – [Identifikátor URI balíčku](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) pomocí autority Application:///<br />– Odkaz na prostředek absolutní součásti<br />– Cesta k souboru, který obsahuje nativní prostředek|
|Pozadí|Volitelné Označuje, jaký typ pozadí má zdroj použít.<br /><br /> Může to být jedna z následujících:<br /><br /> *Světlá:* Zdroj lze použít na světlém pozadí.<br /><br /> *Tmavě tmavá:* Zdroj lze použít na tmavém pozadí.<br /><br /> *HighContrast:* Zdroj lze použít na jakémkoli pozadí v režimu Vysoký kontrast.<br /><br /> *HighContrastLight:* Zdroj lze použít na světlém pozadí v režimu Vysoký kontrast.<br /><br /> *HighContrastDark:* Zdroj lze použít na tmavém pozadí v režimu Vysoký kontrast.<br /><br /> Pokud je atribut Background vynechán, lze zdroj použít na jakémkoli pozadí.<br /><br /> Pokud je pozadí *světlé*, *tmavé*, *HighContrastLight*nebo *HighContrastDark*, barvy zdroje se nikdy nezmění. Pokud je pozadí vynecháno nebo je nastaveno na *HighContrast*, je inverze barev zdroje řízena atributem **AllowColorInversion** obrázku.|

\<zdrojový > prvek může mít přesně jeden z následujících volitelných dílčích elementů:

||||
|-|-|-|
|**Element**|**Atributy (všechny povinné)**|**Definition**|
|Velikost \<|Hodnota|Zdroj se použije pro obrázky dané velikosti (v jednotkách zařízení). Obrázek bude čtvercový.|
|\<SizeRange >|MinSize, MaxSize|Zdroj bude použit pro obrázky z MinSize do MaxSize (v jednotkách zařízení) včetně. Obrázek bude čtvercový.|
|\<dimenzí >|Šířka, Výška|Zdroj se použije pro obrázky zadané šířky a výšky (v jednotkách zařízení).|
|\<DimensionRange >|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Zdroj bude použit pro obrázky z minimální šířky a výšky až po maximální šířku a výšku (v jednotkách zařízení) včetně.|

 \<zdrojový > prvek může mít také volitelný dílčí element \<NativeResource >, který definuje \<zdrojového >, který je načten z nativního sestavení namísto spravovaného sestavení.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Atribut**|**Definition**|
|Typ|Požadovanou Typ nativního prostředku, buď XAML, nebo PNG|
|ID|Požadovanou Část celého čísla ID nativního prostředku|

 **Obrázků**

 Prvek > \<ImageList definuje kolekci obrázků, které mohou být vráceny v jednom pruhu. Pruh je podle potřeby založený na vyžádání.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Atribut**|**Definition**|
|Hlavních|Požadovanou Část GUID monikeru image|
|ID|Požadovanou Část ID monikeru bitové kopie|
|Externí|[Volitelné, výchozí hodnota false] Určuje, zda moniker image odkazuje na obrázek v aktuálním manifestu.|

 Moniker pro obsažený obrázek nemusí odkazovat na obrázek definovaný v aktuálním manifestu. Pokud v knihovně obrázků není nalezen obsažený obrázek, bude na svém místě použit prázdný zástupný obrázek.

## <a name="using-the-image-service"></a>Používání služby Image Service

### <a name="first-steps-managed"></a>První kroky (spravované)
 Chcete-li použít službu image, je nutné přidat do projektu odkazy na některá nebo všechna následující sestavení:

- *Microsoft. VisualStudio. ImageCatalog. dll*

  - Vyžaduje se, pokud použijete integrovaný katalog imagí **KnownMonikers**.

- *Microsoft. VisualStudio. Imaging. dll*

  - Vyžaduje se, pokud používáte **CrispImage** a **ImageThemingUtilities** v uživatelském rozhraní WPF.

- *Microsoft. VisualStudio. Imaging. Interop. 14.0. DesignTime. dll*

  - Vyžaduje se, pokud použijete typy **ImageMoniker** a **structsize** .

  - **EmbedInteropTypes** by měla být nastavená na true.

- *Microsoft. VisualStudio. Shell. Interop. 14.0. DesignTime*

  - Vyžaduje se, pokud použijete typ **IVsImageService2** .

  - **EmbedInteropTypes** by měla být nastavená na true.

- *Microsoft. VisualStudio. Utilities. dll*

  - Vyžaduje se, pokud použijete **BrushToColorConverter** pro **ImageThemingUtilities. ImageBackgroundColor** v uživatelském rozhraní WPF.

- *Microsoft. VisualStudio. Shell.\<VSVersion >. 0*

  - Vyžaduje se, pokud použijete typ **IVsUIObject** .

- *Microsoft. VisualStudio. Shell. Interop. 10.0. dll*

  - Vyžaduje se, pokud použijete pomocníky uživatelského rozhraní související s WinForms.

  - **EmbedInteropTypes** by měla být nastavená na true.

### <a name="first-steps-native"></a>První kroky (nativní)
 Chcete-li použít službu Image Service, je nutné zahrnout do projektu některá nebo všechna následující záhlaví:

- **KnownImageIds. h**

  - Vyžaduje se, pokud použijete vestavěný katalog imagí **KnownMonikers**, ale nemůžete použít typ **ImageMoniker** , například při vracení hodnot z **IVsHierarchy GetGuidProperty** nebo **GetProperty** volání.

- **KnownMonikers. h**

  - Vyžaduje se, pokud použijete integrovaný katalog imagí **KnownMonikers**.

- **ImageParameters140. h**

  - Vyžaduje se, pokud použijete typy **ImageMoniker** a **structsize** .

- **VSShell140. h**

  - Vyžaduje se, pokud použijete typ **IVsImageService2** .

- **ImageThemingUtilities. h**

  - Vyžaduje se, pokud nemůžete nechat službu Image Service pokládat za vás.

  - Tuto hlavičku nepoužívejte, pokud služba Image dokáže zpracovat vaše image.

::: moniker range="vs-2017"
- **VSUIDPIHelper. h**

  - Vyžaduje se, pokud k získání aktuálního rozlišení DPI použijete pomocná okna.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness. h**

  - Vyžaduje se, pokud k získání aktuálního rozlišení DPI použijete pomocníky pro sledování DPI.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Návody napsat nové uživatelské rozhraní WPF?

1. Začněte přidáním odkazů na sestavení požadovaných v oddílu výše uvedeného prvního kroku do vašeho projektu. Nemusíte přidávat všechny z nich, takže přidejte pouze odkazy, které potřebujete. (Poznámka: Pokud používáte nebo máte přístup k **barvám** namísto **štětců**, můžete přeskočit odkaz na **nástroje**, protože ho nebudete potřebovat.)

2. Vyberte požadovanou image a získejte její moniker. Použijte **KnownMoniker**, nebo použijte své vlastní, pokud máte vlastní image a monikery.

3. Přidejte **CrispImages** do kódu XAML. (Viz následující příklad.)

4. V hierarchii uživatelského rozhraní nastavte vlastnost **ImageThemingUtilities. ImageBackgroundColor** . (Tuto hodnotu byste měli nastavit v umístění, kde je barva pozadí známá, ne nutně na **CrispImage**.) (Viz následující příklad.)

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

 **Návody aktualizovat existující uživatelské rozhraní WPF?**

 Aktualizace stávajícího uživatelského rozhraní WPF je poměrně jednoduchý proces, který se skládá ze tří základních kroků:

1. Nahraďte všechny prvky \<image > v uživatelském rozhraní pomocí prvků \<CrispImage >.

2. Změňte všechny zdrojové atributy na atributy monikeru.

    - Pokud se image nikdy nemění a používáte **KnownMonikers**, pak staticky navažte tuto vlastnost na **KnownMoniker**. (Viz výše uvedený příklad.)

    - Pokud se image nikdy nemění a používáte vlastní image, pak staticky propojíte s vlastním monikerem.

    - Pokud se může obrázek změnit, navažte atribut monikeru na vlastnost kódu, která upozorní na změny vlastností.

3. Někde v hierarchii uživatelského rozhraní nastavte **ImageThemingUtilities. ImageBackgroundColor** , abyste se ujistili, že inverze barvy funguje správně.

    - To může vyžadovat použití třídy **BrushToColorConverter** . (Viz výše uvedený příklad.)

## <a name="how-do-i-update-win32-ui"></a>Návody aktualizovat uživatelské rozhraní Win32?
 Přidejte následující kód do kódu, kdykoli je to vhodné, abyste nahradili nezpracované načítání imagí. V případě potřeby přepínejte hodnoty pro vracení HBITMAPs versus HICONs versus HIMAGELIST.

 **Získat službu Image Service**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Vyžadování obrázku**

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

## <a name="how-do-i-update-winforms-ui"></a>Návody aktualizovat uživatelské rozhraní WinForms?
 Přidejte následující kód do kódu, kdykoli je to vhodné, abyste nahradili nezpracované načítání imagí. V případě potřeby přepínejte hodnoty pro vracení rastrových obrázků a ikon.

 **Užitečný příkaz using**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Získat službu Image Service**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Požádat o obrázek**

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

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Návody použít monikery obrázků v novém okně nástroje?
 Šablona projektu balíčku VSIX byla aktualizována pro sadu Visual Studio 2015. Chcete-li vytvořit nové okno nástroje, klikněte pravým tlačítkem na projekt VSIX a vyberte **přidat** > **novou položku** (**CTRL**+**SHIFT**+**a**). V uzlu rozšiřitelnost pro jazyk projektu vyberte **vlastní okno nástrojů**, přiřaďte oknu nástrojů název a stiskněte tlačítko **Přidat** .

 Jedná se o klíčová místa pro použití monikerů v okně nástroje. Postupujte podle pokynů pro každý z těchto kroků:

1. Karta panelu nástrojů v případě, že jsou karty dostatečně malé (používají se také v přepínání okna+**kartě** **CTRL** ).

    Přidejte tento řádek do konstruktoru pro třídu, která je odvozena z typu **třídy ToolWindowPane** :

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Příkaz pro otevření okna nástroje.

    V souboru *. vsct* pro balíček upravte příkazové tlačítko okna nástroje:

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

   **Návody použít monikery imagí v existujícím okně nástrojů?**

   Aktualizace stávajícího okna nástroje na použití monikerů obrázků je podobná postupu při vytváření nového okna nástroje.

   Jedná se o klíčová místa pro použití monikerů v okně nástroje. Postupujte podle pokynů pro každý z těchto kroků:

3. Karta panelu nástrojů v případě, že jsou karty dostatečně malé (používají se také v přepínání okna+**kartě** **CTRL** ).

   1. Odeberte tyto řádky (pokud existují) v konstruktoru pro třídu, která je odvozena z typu **třídy ToolWindowPane** :

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Viz krok #1 Návody použití monikerů obrázků v novém okně nástroje? " výše v části.

4. Příkaz pro otevření okna nástroje.

   - Viz krok #2 Návody použití monikerů obrázků v novém okně nástroje? " výše v části.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Návody použít monikery imagí v souboru. vsct?
 Aktualizujte soubor *. vsct* tak, jak je znázorněno na řádcích s komentářem níže:

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

 **Co když je třeba soubor. vsct přečíst také staršími verzemi sady Visual Studio?**

 Starší verze sady Visual Studio nerozpoznají příznak příkazu **IconIsMoniker** . Můžete použít image ze služby image ve verzích sady Visual Studio, které je podporují, ale nadále používat staré obrázky ve starších verzích sady Visual Studio. Chcete-li to provést, ponechte soubor *. vsct* beze změny (a proto kompatibilní se staršími verzemi sady Visual Studio) a vytvořte soubor CSV (hodnoty oddělené čárkami), který se mapuje z párů identifikátorů GUID/ID definovaných v \<rastrových obrázkůch v souboru *. vsct* > element na páry identifikátorů GUID/identifikátorů monikeru obrázku.

 Formát souboru CSV mapování:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 Soubor CSV se nasadí s balíčkem a jeho umístění je určené vlastností **IconMappingFilename** atributu balíčku **ProvideMenuResource** :

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename** je buď relativní cesta implicitně rootovaná na $PackageFolder $ (jako v příkladu výše), nebo absolutní cesta explicitně rootovaná v adresáři definovaném proměnnou prostředí, například *@ "%USERPROFILE%\dir1\dir2\ MyMappingFile. csv "* .

## <a name="how-do-i-port-a-project-system"></a>Návody rozportovat systém projektu?
 **Jak dodat ImageMonikers pro projekt**

1. Implementujte **VSHPROPID_SupportsIconMonikers** na **IVsHierarchy**projektu a vraťte true.

2. Implementujte buď **VSHPROPID_IconMonikerImageList** (Pokud původní projekt používal **VSHPROPID_IconImgList**), nebo **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (Pokud původní projekt používal **VSHPROPID_IconHandle** a **VSHPROPID_OpenFolderIconHandle**).

3. Změňte implementaci původní VSHPROPIDs pro ikony a vytvořte tak starší verze ikon, pokud je požadují Rozšiřovací body. **IVsImageService2** poskytuje funkce potřebné k získání těchto ikon.

   **Další požadavky pro charakter VBC# /Project**

   Implementujte **VSHPROPID_SupportsIconMonikers** jenom v případě, že zjistíte, že váš projekt je **nejvzdálenějším charakterem**. V opačném případě nemusí skutečný charakter obrazu v realitě podporovat monikery obrázků a váš základní charakter může efektivně skrývat přizpůsobené image.

   **Návody použít monikery imagí v CPS?**

   Nastavení vlastních imagí v CPS (společný systém projektů) je možné provést ručně nebo prostřednictvím šablony položky, která se dodává se sadou SDK pro rozšiřitelnost systému projektů.

   **Používání sady SDK pro rozšiřitelnost systému projektů**

   Postupujte podle pokynů v tématu zadání [vlastních ikon pro typ projektu/typ položky](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) k přizpůsobení vašich imagí CPS. Další informace o CPS najdete v [dokumentaci k rozšíření systému projektu Visual Studio](https://github.com/Microsoft/VSProjectSystem) .

   **Ruční použití ImageMonikers**

4. Implementujte a exportujte rozhraní **IProjectTreeModifier** v systému projektu.

5. Určete, který **KnownMoniker** nebo vlastní moniker obrázku chcete použít.

6. V metodě **ApplyModifications** proveďte následující v metodě před vrácením nového stromu, podobně jako v následujícím příkladu:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Pokud vytváříte nový strom, můžete vlastní image nastavit předáním požadovaných monikerů do metody NewTree, podobně jako v následujícím příkladu:

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Návody převést z reálného obrazového pruhu na obrázkový pruh založený na monikeru?
 **Potřebuji podporovat HIMAGELISTs**

 Pokud již existuje nějaký existující obrazový pruh pro váš kód, který chcete aktualizovat, aby používal službu Image Service, ale máte omezené rozhraní API, které vyžaduje předávání seznamů obrázků, můžete získat výhody služby image. Chcete-li vytvořit obrázkový pruh založený na monikerech, použijte následující postup k vytvoření manifestu z existujících monikerů.

1. Spusťte nástroj **ManifestFromResources** a předejte mu pruh obrázku. Tím se vygeneruje manifest pro pruh.

   - Doporučené: Zadejte jiný než výchozí název manifestu, aby odpovídal jeho využití.

2. Pokud používáte jenom **KnownMonikers**, udělejte toto:

   - Nahraďte část \<images > manifestu pomocí \<image/>.

   - Odeberte všechna ID podimage (cokoli s \<název imagestrip > _ # #).

   - Doporučené: Přejmenujte symbol AssetsGuid a symbol pruhu obrázku tak, aby odpovídaly jeho využití.

   - Nahraďte identifikátor GUID každého **ContainedImage**pomocí $ (ImageCatalogGuid), nahraďte jednotlivá ID **ContainedImage**pomocí $ (\<moniker >) a přidejte do každého **ContainedImage** atribut External = "true".

       - \<moniker > by měl být nahrazen **KnownMoniker** , který odpovídá imagi, ale s názvem "KnownMonikers". odebráno z názvu.

   - Přidejte < importovat manifest = "$ (ManifestFolder)\\< relativní instalační cestu k adresáři *\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest"/\*> na začátek oddílu \<symboly >.

       - Relativní cesta je určena umístěním nasazení definovaným při vytváření obsahu manifestu.

3. Spusťte nástroj **ManifestToCode** , který vygeneruje obálky, aby existující kód měl moniker, který může použít k dotazování služby image pro obrazový svazek.

   - Doporučené: Zadejte jiné než výchozí názvy pro obálky a obory názvů, aby odpovídaly jejich využití.

4. Proveďte všechny změny, vytváření a nasazování instalačního programu a další změny kódu pro práci s Image Service a novými soubory.

   Vzorový manifest, včetně interních i externích imagí, pro zjištění, jak by měl vypadat takto:

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

1. Určete sadu **KnownMonikers** , která odpovídá obrázkům v obrazovém panelu, nebo vytvořte vlastní monikery pro obrázky v obrazovém snímku.

2. Aktualizujte jakékoli mapování, které jste použili k získání obrázku v požadovaném indexu v obrazovém pruhu pro místo toho použít monikery.

3. Aktualizujte kód tak, aby používal službu image k žádosti o monikery prostřednictvím aktualizovaného mapování. (To může znamenat, že aktualizace na **CrispImages** pro spravovaný kód nebo požadavek HBITMAPs nebo HICONs z Image Service a jejich předání pro nativní kód.)

## <a name="testing-your-images"></a>Testování imagí
 Pomocí nástroje Prohlížeč knihovny obrázků můžete testovat manifesty imagí, abyste měli jistotu, že všechno je správně vytvořené. Tento nástroj najdete v [sadě Visual Studio 2015 SDK](visual-studio-sdk.md). Dokumentaci k tomuto nástroji a dalším uživatelům najdete [tady](https://aka.ms/VSImageThemeTools).

## <a name="additional-resources"></a>Další zdroje

### <a name="samples"></a>Ukázky
 Několik ukázek sady Visual Studio na GitHubu bylo aktualizováno, aby ukázaly, jak používat službu Image jako součást různých bodů rozšiřitelnosti sady Visual Studio.

 Nejnovější ukázky najdete [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) .

### <a name="tooling"></a>Nástroje
 Vytvořila se sada nástrojů podpory pro službu Image Service, která vám pomůže při vytváření nebo aktualizaci uživatelského rozhraní, které funguje s imagí služby. Další informace o jednotlivých nástrojích najdete v dokumentaci dodávané s nástroji. Nástroje jsou zahrnuty v rámci sady [Visual Studio 2015 SDK](visual-studio-sdk.md).

 **ManifestFromResources**

 Nástroj Manifest from Resources převezme seznam prostředků obrázků (PNG nebo XAML) a vygeneruje soubor manifestu image pro použití těchto imagí ve službě Image Service.

 **ManifestToCode**

 Nástroj manifest to Code přebírá soubor manifestu obrázku a generuje soubor obálky pro odkazování na hodnoty manifestu v souborech Code (C++, C#, nebo VB) nebo *. vsct* .

 **ImageLibraryViewer**

 Nástroj Prohlížeč knihovny obrázků může načíst manifesty obrázků a umožňuje uživatelům manipulovat stejným způsobem, jako by se v aplikaci Visual Studio zajistilo správné vytváření manifestu. Uživatel může změnit nastavení pozadí, velikosti, DPI, Vysoký kontrast a dalších nastavení. Zobrazuje také informace o načítání pro hledání chyb v manifestech a zobrazuje zdrojové informace pro každý obrázek v manifestu.

## <a name="faq"></a>Nejčastější dotazy

- Existují nějaké závislosti, které je potřeba zahrnout při načítání \<odkazů include = "Microsoft. VisualStudio. *. Spolupráce. 14.0. DesignTime "/>?

  - Nastavte EmbedInteropTypes = "true" na všech interoperabilních knihovnách DLL.

- Návody nasadit manifest image s rozšířením?

  - Přidejte soubor *. imagemanifest* do projektu.

  - Nastavte "zahrnout do VSIX" na hodnotu true.

- Aktualizujem systém projektu CPS. Co se stalo s **ImageName** a **StockIconService**?

  - Ty se odebraly, když se Služba CPS aktualizovala tak, aby používala monikery. Již nemusíte volat **StockIconService**, jednoduše předat požadovaný **KnownMoniker** metodě nebo vlastnosti pomocí metody rozšíření **ToProjectSystemType ()** v nástrojích CPS. Mapování můžete najít z **ImageName** na **KnownMonikers** níže:

    |||
    |-|-|
    |**ImageName**|**KnownMoniker**|
    |ImageName. OfflineWebApp|KnownImageIds. Web|
    |ImageName. WebReferencesFolder|KnownImageIds. Web|
    |ImageName. OpenReferenceFolder|KnownImageIds.FolderOpened|
    |ImageName. ReferenceFolder|KnownImageIds. reference|
    |ImageName. reference|KnownImageIds. reference|
    |ImageName. SdlWebReference|KnownImageIds.WebReferenceFolder|
    |ImageName. DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|
    |ImageName. Folder|KnownImageIds.FolderClosed|
    |ImageName. OpenFolder|KnownImageIds.FolderOpened|
    |ImageName. ExcludedFolder|KnownImageIds.HiddenFolderClosed|
    |ImageName. OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|
    |ImageName. ExcludedFile|KnownImageIds.HiddenFile|
    |ImageName. DependentFile|KnownImageIds.GenerateFile|
    |ImageName. MissingFile|KnownImageIds.DocumentWarning|
    |ImageName. WindowsForm|KnownImageIds.WindowsForm|
    |ImageName. WindowsUserControl|KnownImageIds. UserControl|
    |ImageName. WindowsComponent|KnownImageIds.ComponentFile|
    |ImageName. XmlSchema|KnownImageIds. XMLSchema|
    |ImageName. XmlFile|KnownImageIds. XMLFile|
    |ImageName. Web– formulář|KnownImageIds. Web|
    |ImageName. WebService|KnownImageIds. WebService|
    |ImageName. WebUserControl|KnownImageIds. WebUserControl|
    |ImageName. WebCustomUserControl|KnownImageIds.WebCustomControl|
    |ImageName. AspPage|KnownImageIds.ASPFile|
    |ImageName. GlobalApplicationClass|KnownImageIds.SettingsFile|
    |ImageName. WebConfig|KnownImageIds.ConfigurationFile|
    |ImageName. HtmlPage|KnownImageIds.HTMLFile|
    |ImageName. StyleSheet|KnownImageIds. StyleSheet|
    |ImageName. ScriptFile|KnownImageIds.JSScript|
    |ImageName. TextFile|KnownImageIds. Document|
    |ImageName. SettingsFile|KnownImageIds. Settings|
    |ImageName. Resources|KnownImageIds. Documents|
    |ImageName. Bitmap|KnownImageIds. Image|
    |ImageName. Icon|KnownImageIds.IconFile|
    |ImageName. Image|KnownImageIds. Image|
    |ImageName. ImageMap|KnownImageIds.ImageMapFile|
    |ImageName. XWorld|KnownImageIds.XWorldFile|
    |ImageName. audio|KnownImageIds. Sound|
    |ImageName. video|KnownImageIds. Media|
    |ImageName. cab|KnownImageIds.CABProject|
    |ImageName. jar|KnownImageIds. JARFile|
    |ImageName. DataEnvironment|KnownImageIds. DataTable|
    |ImageName. PreviewFile|KnownImageIds. Report|
    |ImageName. DanglingReference|KnownImageIds.ReferenceWarning|
    |ImageName. XsltFile|KnownImageIds. XSLTransform|
    |ImageName. Cursor|KnownImageIds.CursorFile|
    |ImageName. AppDesignerFolder|KnownImageIds. Property|
    |ImageName. data|KnownImageIds. Database|
    |ImageName. Application|KnownImageIds. Application|
    |ImageName. DataSet|KnownImageIds. Database – databáze|
    |ImageName. pfx|KnownImageIds. Certificate|
    |ImageName. snk|KnownImageIds. Rule|
    |ImageName. VisualBasicProject|KnownImageIds.VBProjectNode|
    |ImageName. CSharpProject|KnownImageIds.CSProjectNode|
    |ImageName. Empty|KnownImageIds. blank|
    |ImageName. MissingFolder|KnownImageIds.FolderOffline|
    |ImageName. SharedImportReference|KnownImageIds.SharedProject|
    |ImageName. SharedProjectCs|KnownImageIds.CSSharedProject|
    |ImageName. SharedProjectVc|KnownImageIds.CPPSharedProject|
    |ImageName. SharedProjectJs|KnownImageIds.JSSharedProject|
    |ImageName. CSharpCodeFile|KnownImageIds.CSFileNode|
    |ImageName. VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - Aktualizujem poskytovatele seznamu pro doplňování. Co **KnownMonikers** odpovídá starým hodnotám **StandardGlyphGroup** a **StandardGlyph** ?

    ||||
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupConstant|GlyphItemPublic|ConstantPublic|
    |GlyphGroupConstant|GlyphItemInternal|ConstantInternal|
    |GlyphGroupConstant|GlyphItemFriend|ConstantInternal|
    |GlyphGroupConstant|GlyphItemProtected|ConstantProtected|
    |GlyphGroupConstant|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant|GlyphItemShortcut|ConstantShortcut|
    |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|
    |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|
    |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|
    |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|
    |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|
    |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationItemPublic|
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationItemProtected|
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationItemPrivate|
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationItemShortcut|
    |GlyphGroupEvent|GlyphItemPublic|EventPublic|
    |GlyphGroupEvent|GlyphItemInternal|EventInternal|
    |GlyphGroupEvent|GlyphItemFriend|EventInternal|
    |GlyphGroupEvent|GlyphItemProtected|EventProtected|
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|
    |GlyphGroupException|GlyphItemPublic|ExceptionPublic|
    |GlyphGroupException|GlyphItemInternal|ExceptionInternal|
    |GlyphGroupException|GlyphItemFriend|ExceptionInternal|
    |GlyphGroupException|GlyphItemProtected|ExceptionProtected|
    |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|
    |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|
    |GlyphGroupField|GlyphItemPublic|FieldPublic|
    |GlyphGroupField|GlyphItemInternal|FieldInternal|
    |GlyphGroupField|GlyphItemFriend|FieldInternal|
    |GlyphGroupField|GlyphItemProtected|FieldProtected|
    |GlyphGroupField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|
    |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|
    |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupMacro|GlyphItemPublic|MacroPublic|
    |GlyphGroupMacro|GlyphItemInternal|MacroInternal|
    |GlyphGroupMacro|GlyphItemFriend|MacroInternal|
    |GlyphGroupMacro|GlyphItemProtected|MacroProtected|
    |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|
    |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|
    |GlyphGroupMap|GlyphItemPublic|MapPublic|
    |GlyphGroupMap|GlyphItemInternal|MapInternal|
    |GlyphGroupMap|GlyphItemFriend|MapInternal|
    |GlyphGroupMap|GlyphItemProtected|MapProtected|
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate|
    |GlyphGroupMap|GlyphItemShortcut|MapShortcut|
    |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|
    |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|
    |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|
    |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|
    |GlyphGroupMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupOverload|GlyphItemPublic|MethodPublic|
    |GlyphGroupOverload|GlyphItemInternal|MethodInternal|
    |GlyphGroupOverload|GlyphItemFriend|MethodInternal|
    |GlyphGroupOverload|GlyphItemProtected|MethodProtected|
    |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupModule|GlyphItemPublic|ModulePublic|
    |GlyphGroupModule|GlyphItemInternal|ModuleInternal|
    |GlyphGroupModule|GlyphItemFriend|ModuleInternal|
    |GlyphGroupModule|GlyphItemProtected|ModuleProtected|
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|
    |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|
    |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|
    |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|
    |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|
    |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|
    |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|
    |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|
    |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|
    |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|
    |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|
    |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|
    |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|
    |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|
    |GlyphGroupStruct|GlyphItemPublic|StructurePublic|
    |GlyphGroupStruct|GlyphItemInternal|StructureInternal|
    |GlyphGroupStruct|GlyphItemFriend|StructureInternal|
    |GlyphGroupStruct|GlyphItemProtected|StructureProtected|
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|
    |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|
    |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|
    |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|
    |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|
    |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|
    |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|
    |GlyphGroupType|GlyphItemPublic|TypePublic|
    |GlyphGroupType|GlyphItemInternal|TypeInternal|
    |GlyphGroupType|GlyphItemFriend|TypeInternal|
    |GlyphGroupType|GlyphItemProtected|TypeProtected|
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut|
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|
    |GlyphGroupUnion|GlyphItemInternal|UnionInternal|
    |GlyphGroupUnion|GlyphItemFriend|UnionInternal|
    |GlyphGroupUnion|GlyphItemProtected|UnionProtected|
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|
    |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|
    |GlyphGroupVariable|GlyphItemPublic|FieldPublic|
    |GlyphGroupVariable|GlyphItemInternal|FieldInternal|
    |GlyphGroupVariable|GlyphItemFriend|FieldInternal|
    |GlyphGroupVariable|GlyphItemProtected|FieldProtected|
    |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|
    |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|
    |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|
    |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|
    |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|
    |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|
    |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|
    |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|
    |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|
    |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupError||StatusError|
    |GlyphBscFile||ClassFile|
    |GlyphAssembly||Odkaz|
    |GlyphLibrary||Knihovna|
    |GlyphVBProject||VBProjectNode|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||CPPProjectNode|
    |GlyphDialogId||Dialogový|
    |GlyphOpenFolder||FolderOpened|
    |GlyphClosedFolder||FolderClosed|
    |GlyphArrow||GoToNext|
    |GlyphCSharpFile||CSFileNode|
    |GlyphCSharpExpansion||Zlomk|
    |GlyphKeyword||IntellisenseKeyword|
    |GlyphInformation||StatusInformation|
    |GlyphReference||ClassMethodReference|
    |GlyphRecursion||Rekurze|
    |GlyphXmlItem||Inteligentní|
    |GlyphJSharpProject||Dokumentů|
    |GlyphJSharpDocument||Dokument|
    |GlyphForwardType||GoToNext|
    |GlyphCallersGraph||CallTo|
    |GlyphCallGraph||CallFrom|
    |GlyphWarning||StatusWarning|
    |GlyphMaybeReference||QuestionMark|
    |GlyphMaybeCaller||CallTo|
    |GlyphMaybeCall||CallFrom|
    |GlyphExtensionMethod||ExtensionMethod|
    |GlyphExtensionMethodInternal||ExtensionMethod|
    |GlyphExtensionMethodFriend||ExtensionMethod|
    |GlyphExtensionMethodProtected||ExtensionMethod|
    |GlyphExtensionMethodPrivate||ExtensionMethod|
    |GlyphExtensionMethodShortcut||ExtensionMethod|
    |GlyphXmlAttribute||XmlAttribute|
    |GlyphXmlChild||Třída|
    |GlyphXmlDescendant||XmlDescendant|
    |GlyphXmlNamespace||XmlNamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphXmlChildQuestion||XmlElementLowConfidence|
    |GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |GlyphCompletionWarning||IntellisenseWarning|
