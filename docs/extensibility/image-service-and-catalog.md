---
title: Služba vyhledávání a katalog obrázků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c37da890842711b941e61aadc23ed85d60672f3c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823759"
---
# <a name="image-service-and-catalog"></a>Služba bitových kopií a katalog
Tato kuchařka obsahuje pokyny a osvědčené postupy pro přijetí, služby Visual Studio Image a Image katalog zavedena v sadě Visual Studio 2015.  
  
 Služba bitových kopií zavedena v sadě Visual Studio 2015 umožňuje vývojářům získat nejlepší Image pro zařízení a uživatele zvolené motivu a zobrazte obrázek, včetně správné motivy pro daný kontext, ve kterém jsou zobrazeny. Zavádění bitové kopie služeb vám pomohou eliminovat hlavní slabiny týkající se údržby asset, HDPI škálování a motivů.  
  
|||  
|-|-|  
|**Problémy ještě dnes**|**Řešení**|  
|Prolnutí barva pozadí|Integrované prolnutí alfa|  
|Obrázky motivů (některé)|Motiv metadat|  
|Vysoký kontrast|Alternativní prostředky vysoký kontrast|  
|Potřebujete víc prostředků pro různé režimy DPI|Vybrat prostředky s vektorové použití náhradní lokality|  
|Duplicitní imagí|Jeden identifikátor za koncept bitové kopie|  
  
 Proč přijmout službu image?  
  
- Vždy získáte nejnovější "perfektním vzhledem" image ze sady Visual Studio  
  
- Můžete odesílat projekty a používat vlastní Image  
  
- Není potřeba testovat vaše image, pokud Windows přidá nový Škálování DPI  
  
- Řešení původní architektury překážek, se kterými ve vaší implementace  
  
  Nástrojů sady Visual Studio shell, před a za používání služby bitové kopie:  
  
  ![Image Service před a po](../extensibility/media/image-service-before-and-after.png "Image Service před a po ní")  
  
## <a name="how-it-works"></a>Jak to funguje
 Služba bitových kopií, můžete zadat rastrovými obrázky image, která je vhodná pro všechny podporované architektury uživatelského rozhraní:  
  
- WPF: BitmapSource  
  
- WinForms: System.Drawing.Bitmap  
  
- Win32: HBITMAP  
  
  Vývojový diagram služby Image  
  
  ![Image Service vývojový Diagram](../extensibility/media/image-service-flow-diagram.png "obrázku vývojový Diagram služby")  
  
  **Obrázek monikery**  
  
  Moniker bitové kopie (nebo moniker short) je identifikátor GUID a ID pár, který jednoznačně identifikuje prostředek obrázku nebo seznam prostředků obrázků v knihovně obrázků.  
  
  **Známé monikery**  
  
  Sada obrázků monikery obsaženým v katalogu obrázků Visual Studio a veřejně použitelnost podle jakékoli součásti sady Visual Studio nebo rozšíření.  
  
  **Soubory manifestu obrázků**  
  
  Manifestu obrázků (*.imagemanifest*) soubory jsou soubory XML, které definují sadu prostředky obrázků, zástupných názvů, které představují tyto prostředky a skutečné bitové kopie nebo bitové kopie, které představují každého prostředku. Manifesty Image můžete definovat samostatné obrázky nebo bitové kopie jsou uvedené pro stále podporuje starší verze uživatelského rozhraní. Kromě toho jsou atributy, které je možné nastavit na prostředku nebo na jednotlivých obrázků za každý prostředek změnit, kdy a jak tyto prostředky jsou zobrazené.  
  
  **Schéma manifestu obrázků**  
  
  Manifest kompletní obrázek vypadá takto:  
  
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
  
 Jako podporu čitelnost a údržbu, image manifest můžete použít symboly pro hodnoty atributů. Značky jsou definovány takto:  
  
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
|**Dílčí element**|**Definice**|  
|Importovat|Importuje symboly daný soubor manifestu pro použití v aktuální manifestu|  
|identifikátor GUID|Symbol představuje identifikátor GUID a musí odpovídat identifikátoru GUID formátování|  
|ID|Symbol představuje ID a musí být nezáporné celé číslo|  
|String|Symbol představuje hodnotu libovolný řetězec|  
  
 Symboly jsou malá a velká písmena a odkazované pomocí syntaxe $(symbol-name):  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 U všech manifestů jsou předdefinovány některé symboly. Ty je možné použít v atributu identifikátor Uri \<zdroj > nebo \<Import > – element pro cesty odkazů v místním počítači.  
  
|||  
|-|-|  
|**Symbol**|**Popis**|  
|CommonProgramFiles|Hodnota proměnné prostředí % CommonProgramFiles %|  
|LocalAppData|Hodnota proměnné prostředí % LocalAppData %|  
|ManifestFolder|Složku, která obsahuje soubor manifestu|  
|Dokumenty|Úplná cesta ke složce Dokumenty aktuálního uživatele|  
|ProgramFiles|Hodnota proměnné prostředí % ProgramFiles %|  
|Systém|*Windows\System32* složky|  
|WinDir|Hodnota proměnné prostředí % WinDir %|  
  
 **Obrázek**  
  
 \<Image > element definuje bitovou kopii, která lze odkazovat pomocí monikeru. Identifikátor GUID a ID, které dohromady tvoří moniker bitové kopie. Moniker bitové kopie musí být jedinečný ve knihovny celého obrázku. Pokud více než jednu image má daný monikeru, došlo při vytváření knihovny k první z nich je ten, který je zachováno.  
  
 Musí obsahovat alespoň jeden zdroj. Velikost jazykově neutrální zdrojů vám poskytne nejlepší výsledky napříč širokou škálu velikostí, ale nejsou vyžadovány. Pokud služba se zobrazí výzva o určité imagi velikost není definovaný v \<Image > element a neexistuje žádný zdroj velikost doménově neutrální, služba bude zvolit nejlepší zdroj konkrétní velikosti a škálovat ji na požadovanou velikost.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|identifikátor GUID|[Povinné] Část GUID moniker obrázku.|  
|ID|[Povinné] ID část moniker obrázku.|  
|AllowColorInversion|[Volitelné, výchozí hodnota true] Určuje, jestli obrázek může mít jeho barvy programově obrácený v tmavém pozadí.|  
  
 **Zdroj**  
  
 \<Zdroj > element definuje jediný zdroj zdroj obrázku (XAML a PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Identifikátor URI|[Povinné] Identifikátor URI, který definuje, kde je možné načíst image z. Může být jeden z následujících akcí:<br /><br /> -A [identifikátory Pack URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) používání aplikace pro: / / / / / autority<br />Odkaz na prostředek – absolutní komponenty<br />– Cesta k souboru, který obsahuje nativní prostředky|  
|Pozadí|[Volitelné] Určuje, co na pozadí, který zdroj je určena pro použití typu.<br /><br /> Může být jeden z následujících akcí:<br /><br /> *Světle:* zdroj jde použít na světla na pozadí.<br /><br /> *Tmavý:* zdroj je možné v tmavém pozadí.<br /><br /> *Funkce Vysoký kontrast:* zdroj jde použít na jakékoli na pozadí v režimu vysokého kontrastu.<br /><br /> *HighContrastLight:* zdroj je možné na pozadí světla v režimu vysokého kontrastu.<br /><br /> *HighContrastDark:* zdroj je možné v tmavém pozadí v režimu vysokého kontrastu.<br /><br /> Pokud je atribut pozadí vynechán, zdroj je možné na jakékoli na pozadí.<br /><br /> Pokud je na pozadí *světla*, *tmavě*, *HighContrastLight*, nebo *HighContrastDark*, se nikdy převrátí zdroje na barvy. Pokud je vynechán nebo nastaven na pozadí *funkce Vysoký kontrast*, inverzi barev zdroji se řídí na obrázku **AllowColorInversion** atribut.|  

|||  
  
 A \<zdroj > prvek může mít nastavený právě jeden z následující volitelné dílčí prvky:  
  
||||  
|-|-|-|  
|**Element**|**Atributy (všechny povinné)**|**Definice**|  
|\<Velikost >|Hodnota|Zdroj se použije pro Image dané velikosti (v jednotkách zařízení). Image bude čtvereček.|  
|\<SizeRange >|MinSize MaxSize|Zdroj se použije pro obrázky z MinSize pro parametr MaxSize (v jednotkách zařízení) (včetně). Image bude čtvereček.|  
|\<Dimenze >|Šířka, výška|Zdroj se použije pro Image dané šířky a výšky (v jednotkách zařízení).|  
|\<DimensionRange >|Hodnota MinWidth MinHeight,<br /><br /> MaxWidth MaxHeight|Zdroj se použije pro obrázků ze minimální šířky a výšky na maximální šířku nebo výšku (v jednotkách zařízení) (včetně).|  
  
 A \<zdroj > prvek může mít také volitelný \<NativeResource > dílčího elementu, který definuje \<zdroj >, který je načten z nativní sestavení spíše než spravovaná sestavení.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Typ|[Povinné] Typ nativního prostředku, XAML nebo PNG|  
|ID|[Povinné] Část celého čísla ID nativní prostředky|  
  
 **Ovládací prvek ImageList**  
  
 \<ImageList > element definuje kolekci imagí, které mohou být vráceny v jedné pruhu. Pruh je postavená na požádání, podle potřeby.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|identifikátor GUID|[Povinné] Část GUID moniker obrázku.|  
|ID|[Povinné] ID část moniker obrázku.|  
|Externí|[Volitelné, výchozí hodnota je false] Určuje, zda moniker bitové kopie odkazuje na obrázek v aktuální manifestu.|  
  
 Moniker pro bitovou kopii obsaženého nemusí odkazovat na image definovaný v manifestu aktuální. Pokud bitovou kopii obsaženého nebyl nalezen v knihovně image, image prázdný zástupný symbol se použije na příslušné místo.  
  
## <a name="using-the-image-service"></a>Pomocí služby image  
  
### <a name="first-steps-managed"></a>První kroky (spravované)  
 Pokud chcete používat službu bitových kopií, budete muset do projektu přidejte odkazy na některé nebo všechny následující sestavení:  
  
-   *Microsoft.VisualStudio.ImageCatalog.dll*  
  
    -   Povinné, pokud používáte integrované image katalogu **KnownMonikers**.  
  
-   *Microsoft.VisualStudio.Imaging.dll*  
  
    -   Povinné, pokud používáte **CrispImage** a **ImageThemingUtilities** v uživatelském rozhraní WPF.
  
-   *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*  
  
    -   Povinné, pokud používáte **ImageMoniker** a **Structsize** typy.  
  
    -   **EmbedInteropTypes** by měla být nastavena na hodnotu true.  
  
-   *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime*  
  
    -   Povinné, pokud používáte **IVsImageService2** typu.  
  
    -   **EmbedInteropTypes** by měla být nastavena na hodnotu true.  
  
-   *Microsoft.VisualStudio.Utilities.dll*  
  
    -   Povinné, pokud používáte **BrushToColorConverter** pro **ImageThemingUtilities.ImageBackgroundColor** v uživatelském rozhraní WPF.  
  
-   *Microsoft.VisualStudio.Shell. \<VSVersion >.0*  
  
    -   Povinné, pokud používáte **IVsUIObject** typu.  
  
-   *Microsoft.VisualStudio.Shell.Interop.10.0.dll*  
  
    -   Povinné, pokud používáte pomocné rutiny související s WinForms uživatelského rozhraní.  
  
    -   **EmbedInteropTypes** by měla být nastavena na hodnotu true  
  
### <a name="first-steps-native"></a>První kroky (nativní)  
 Pokud chcete používat službu bitových kopií, budete muset zahrnuje některé nebo všechny následující hlavičky do projektu:  
  
-   **KnownImageIds.h**  
  
    -   Povinné, pokud používáte integrované image katalogu **KnownMonikers**, ale nemůžete použít **ImageMoniker** typu, například při vrácení hodnot z **IVsHierarchy GetGuidProperty**nebo **GetProperty** volání.  
  
-   **KnownMonikers.h**  
  
    -   Povinné, pokud používáte integrované image katalogu **KnownMonikers**.  
  
-   **ImageParameters140.h**  
  
    -   Povinné, pokud používáte **ImageMoniker** a **Structsize** typy.  
  
-   **VSShell140.h**  
  
    -   Povinné, pokud používáte **IVsImageService2** typu.  
  
-   **ImageThemingUtilities.h**  
  
    -   Povinné, pokud se nemůžete umožňují zpracovat motivy pro vás služba bitových kopií.  
  
    -   Tato hlavička nepoužívejte, pokud služba bitových kopií může zpracovávat vaše image motivů.  
  
-   **VSUIDPIHelper.h**  
  
    -   Povinné, pokud používáte DPI pomocné rutiny zobrazíte aktuální DPI.  
  
## <a name="how-do-i-write-new-wpf-ui"></a>Jak se píše nové uživatelské rozhraní WPF?  
  
1.  Začněte tím, že přidáte odkazy na sestavení podle výše uvedeného první kroky části do projektu. Není nutné přidat všechny z nich, proto přidejte jenom odkazy, které potřebujete. (Poznámka: Pokud používáte nebo máte přístup k **barvy** místo **štětce**, pak je možné přeskočit odkaz na **nástroje**, protože není třeba převaděč.)  
  
2.  Vyberte požadovanou image a získat jeho moniker. Použít **KnownMoniker**, nebo použijte vlastní, pokud máte vlastní vlastních imagí a zástupných názvů.  
  
3.  Přidat **CrispImages** do vaší XAML. (Viz následující příklad).  
  
4.  Nastavte **ImageThemingUtilities.ImageBackgroundColor** vlastnost ve vaší hierarchii uživatelského rozhraní. (Toto nastavení do umístění, kde barvu pozadí je známé, ne nutně v **CrispImage**.) (Viz následující příklad).  
  
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
  
 **Jak aktualizovat stávající rozhraní WPF**  
  
 Aktualizace existujícího rozhraní WPF je poměrně jednoduchý proces, který se skládá ze tří základních kroků:  
  
1.  Nahradit vše \<Image > prvky v uživatelském rozhraní s \<CrispImage > elementy.  
  
2.  Změňte všechny atributy zdroje na Moniker atributy.  
  
    -   Pokud se nikdy nemění na obrázku a jeho použití **KnownMonikers**, staticky vázat vlastnosti k **KnownMoniker**. (Viz výše uvedeném příkladu).  
  
    -   Pokud se nikdy nemění bitovou kopii a použití vlastní image, staticky svážou pro vlastní zástupný název.  
  
    -   Pokud můžete změnit na obrázku, atribut Monikeru svázat vlastnost kódu, která upozorní na změny vlastností.  
  
3.  Někde v hierarchii uživatelského rozhraní nastavit **ImageThemingUtilities.ImageBackgroundColor** k Ujistěte se, že inverze barev funguje správně.  
  
    -   To může vyžadovat použití **BrushToColorConverter** třídy. (Viz výše uvedeném příkladu).  
  
## <a name="how-do-i-update-win32-ui"></a>Jak můžu aktualizovat uživatelské rozhraní systému Win32?  
 Přidejte následující kód bez ohledu na to vhodné nahradit nezpracovaná načítání obrázků. Přepnout hodnoty vrácením HBITMAPs oproti HICONs oproti HIMAGELIST podle potřeby.  
  
 **Získání bitové kopie služby**  
  
```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  
  
 **Vyžádání image**  
  
```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  
  
CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  
  
```  
  
## <a name="how-do-i-update-winforms-ui"></a>Jak můžu aktualizovat WinForms uživatelského rozhraní?  
 Přidejte následující kód bez ohledu na to vhodné nahradit nezpracovaná načítání obrázků. Přepnout hodnoty vrácením rastrové obrázky a ikony, podle potřeby.  
  
 **Příspěvek je užitečný using – příkaz**  
  
```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  
  
 **Získání bitové kopie služby**  
  
```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  
  
```  
  
 **Požadují bitovou kopii**  
  
```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  
  
// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  
  
Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  
  
```  
  
## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Jak použít obraz monikery v novém okně nástroje?  
 Šablona projektu VSIX balíček byl aktualizovaný pro Visual Studio 2015. K vytvoření nového okna nástroje, klikněte pravým tlačítkem na projekt VSIX a vyberte **přidat** > **nová položka** (**Ctrl**+**Shift** + **A**). V uzlu rozšíření pro jazyk projektu, vyberte **vlastního panelu nástrojů**, poskytují panel nástrojů, název a stiskněte klávesu **přidat** tlačítko.  
  
 Jedná se o klíčových místa k použití zástupných názvů v panelu nástrojů. Postupujte podle pokynů pro každou:  
  
1. Na kartě okna nástroje když karty získat dostatečně malá, (používá se také v **Ctrl**+**kartu** přepínač okna).  
  
    Přidejte následující řádek do konstruktoru pro třídu, která je odvozena z **ToolWindowPane** typu:  
  
   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   this.BitmapImageMoniker = KnownMonikers.Blank;  
   ```  
  
2. Příkaz pro otevření okna nástrojů.  
  
    V *.vsct* soubor balíčku, panel nástrojů příkazového tlačítka Upravit:  
  
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
  
   **Použití zástupných názvů bitové kopie v existující panelu nástrojů**  
  
   Aktualizace existujícího okna nástroje použít obraz monikery je podobný postup pro vytvoření nového okna nástroje.  
  
   Jedná se o klíčových místa k použití zástupných názvů v panelu nástrojů. Postupujte podle pokynů pro každou:  
  
3. Na kartě okna nástroje když karty získat dostatečně malá, (používá se také v **Ctrl**+**kartu** přepínač okna).  
  
   1.  Odebrat tyto řádky (pokud existují) v konstruktoru pro třídu, která je odvozena z **ToolWindowPane** typu:  
  
       ```csharp  
       this.BitmapResourceID = <Value>;  
       this.BitmapIndex = <Value>;  
       ```  
  
   2.  Viz krok #1 "Použití zástupných názvů bitové kopie v novém okně nástroje?" výše uvedené části.  
  
4. Příkaz pro otevření okna nástrojů.  
  
   -   Viz krok #2 "Použití zástupných názvů bitové kopie v novém okně nástroje?" výše uvedené části.  
  
## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Použití zástupných názvů image v souboru .vsct  
 Aktualizace vašeho *.vsct* souboru, jak je uvedeno ve níže uvedené komentářem řádky:  
  
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
  
 **Co když Moje souboru .vsct musí také čtení ve starších verzích sady Visual Studio?**  
  
 Starší verze sady Visual Studio nedokáže rozpoznat **IconIsMoniker** příkazu příznak. Ve verzích sady Visual Studio, které ho podporují, ale pokračovat v používání starého typu Image ke starším verzím sady Visual Studio můžete použít Image z image služby. K tomuto účelu ponechte *.vsct* soubor beze změny (a tedy kompatibilní se staršími verzemi sady Visual Studio) a vytvořit z dvojice GUID a ID definované v souboru CSV (hodnoty oddělené čárkami), která se mapuje *.vsct* souboru \<rastrové obrázky > prvek dvojice GUID a ID moniker bitové kopie.  
  
 Formát souboru CSV mapování je:  
  
```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  
  
 Soubor CSV se nasazuje se balíček a jeho umístění je určená **IconMappingFilename** vlastnost **ProvideMenuResource** atribut balíčku:  
  
```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  
  
 **IconMappingFilename** je relativní cesta implicitně kořenovým adresářem v $PackageFolder$ (jako v příkladu výše) nebo absolutní cesta explicitně kořenovým adresářem v adresáře určené proměnnou prostředí, jako například *@"% UserProfile%\dir1\dir2\MyMappingFile.csv"*.  
  
## <a name="how-do-i-port-a-project-system"></a>Jak se port bude systém projektu?  
 **Jak dodávat ImageMonikers pro projekt**  
  
1. Implementace **VSHPROPID_SupportsIconMonikers** na projektu **IVsHierarchy**a vrátí hodnotu true.  
  
2. Implementovat buď **VSHPROPID_IconMonikerImageList** (pokud použili původní projekt **VSHPROPID_IconImgList**) nebo **VSHPROPID_IconMonikerGuid**,  **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (pokud použili původní projekt  **VSHPROPID_IconHandle** a **VSHPROPID_OpenFolderIconHandle**).  
  
3. Změňte implementaci původní VSHPROPIDs u ikon, vytvořit "starší" verze ikony, pokud Rozšiřovací body o ně požádat. **IVsImageService2** poskytuje funkce potřebné k získání těchto ikon  
  
   **Další požadavky pro VB / C# projekt digitálních**  
  
   Implementovat pouze **VSHPROPID_SupportsIconMonikers** Pokud zjistíte, že je váš projekt **nejkrajnější flavor**. V opačném případě skutečné nejkrajnější charakter nemusí podporovat monikery image ve skutečnosti a základní flavor může efektivně "skrytí" přizpůsobené Image.  
  
   **Použití zástupných názvů bitové kopie v systému CPS**  
  
   Nastavení vlastních imagí v systému CPS (Common Project System) to provést ručně nebo pomocí šablony položky, který je součástí sady SDK rozšíření systému projektu.  
  
   **Pomocí rozšíření systému projektu sady SDK**  
  
   Postupujte podle pokynů na adrese [zadejte vlastní ikony pro typ typem projektu/položky](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) přizpůsobení Image CPS. Další informace o prohlášení CPS najdete [dokumentace k rozšiřitelnosti systém projektů Visual Studia](https://github.com/Microsoft/VSProjectSystem)  
  
   **Ručně pomocí ImageMonikers**  
  
4. Implementujte a exportujte **IProjectTreeModifier** rozhraní v systému projektu.  
  
5. Určení, které **KnownMoniker** nebo moniker vlastní image, kterou chcete použít.  
  
6. V **ApplyModifications** metoda, proveďte následující někde v metodě před vrácením nového stromu, podobně jako následujícím příkladu:  
  
   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
   ```  
  
7. Pokud vytváříte nové větve, můžete nastavit vlastní Image předáním požadované monikery do metody NewTree, podobně jako následujícím příkladu:  
  
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
  
## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Jak převést skutečné obrázku na základě moniker obrázku?  
 **Je potřeba podporovat HIMAGELISTs**  
  
 Pokud je již existujícího obrázku pro kód, který chcete aktualizovat používat služba bitových kopií, ale jsou omezené aktivitami rozhraní API, které vyžadují předávání kolem seznamy obrázků, stále získáte výhody služby bitové kopie. Pokud chcete vytvořit na základě moniker obrázku, podle následujících pokynů k vytvoření manifestu z existující monikery.  
  
1. Spustit **ManifestFromResources** nástroj, předají se jí obrázku. Tím se vygeneruje manifest pro pruh.  
  
   -   Doporučeno: Zadejte název jiné výchozí manifest tak, aby odpovídala jeho využití.  
  
2. Pokud používáte pouze **KnownMonikers**, proveďte následující kroky:  
  
   -   Nahradit \<Imagí > manifestu se \<image / >.  
  
   -   Odebrat všechny subimage ID (cokoli s \<imagestrip name > _ ##).  
  
   -   Doporučeno: přejmenujte AssetsGuid symbol a symbol pruhu image tak, aby odpovídala jeho využití.  
  
   -   Nahraďte každé **ContainedImage**identifikátor GUID s $(ImageCatalogGuid), nahraďte každé **ContainedImage**ID s $(\<moniker >) a přidejte externí = "true" atribut pro každý **ContainedImage**  
  
       -   \<moniker > by měla být nahrazena **KnownMoniker** odpovídající image, ale s "KnownMonikers." odebrat z názvu.  
  
   -   Přidat < Import Manifest="$(ManifestFolder)\\< nainstalovat relativní cestu k domovskému adresáři na *\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" /\*> do horní části \<symboly > oddílu.  
  
       -   Relativní cesta se určuje podle umístění nasazení, které jsou definované v nastavení pro vytváření pro manifest.  
  
3. Spustit **ManifestToCode** nástroj pro generování obálky tak, aby měl monikeru může použít k dotazování na obrázek službu obrázku existující kód.  
  
   -   Doporučeno: Zadejte jiný než výchozí názvy obálky a obory názvů tak, aby odpovídaly jejich použití.  
  
4. Toto všechno dělat přidá, instalační program pro vytváření a nasazování a dalších změn kódu pro práci s služba bitových kopií a nové soubory.  
  
   Ukázka manifestu včetně interních i externích imagí, které chcete zobrazit, co by měl vypadat jako:  
  
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
  
 **Není potřeba podporovat HIMAGELISTs**  
  
1.  Určení sady **KnownMonikers** , která odpovídají Image vašeho obrázku nebo vytvořte vlastní monikery pro Image ve vaší obrázku.  
  
2.  Aktualizujte jakýkoli mapování, které jste použili k načtení image na požadovaný index obrázku místo toho použít zástupných názvů.  
  
3.  Aktualizujte kód Refaktorovat pro použití image služby k vyžádání monikery prostřednictvím aktualizované mapování. (To může znamenat aktualizace **CrispImages** pro spravovaného kódu, nebo si vyžádat HBITMAPs nebo HICONs od služba bitových kopií a prošly kolem pro nativní kód.)  
  
## <a name="testing-your-images"></a>Testování obrázků  
 Nástroj Prohlížeč knihovny obrázků můžete použít k testování vaše image manifesty, abyste měli jistotu, že všechno je správně nastavená oprávnění. Nástroj v [Visual Studio 2015 SDK](visual-studio-sdk.md). Pro tento nástroj a další dokumentaci najdete [tady](http://aka.ms/VSImageThemeTools).  
  
## <a name="additional-resources"></a>Další zdroje  
  
### <a name="samples"></a>Ukázky kódu  
 Některé ukázky sady Visual Studio na Githubu byla aktualizována, aby ukazují, jak použít službu bitových kopií v rámci různých bodů rozšiřitelnosti sady Visual Studio.  
  
 Zkontrolujte [ http://github.com/Microsoft/VSSDK-Extensibility-Samples ](http://github.com/Microsoft/VSSDK-Extensibility-Samples) nejnovější ukázek.  
  
### <a name="tooling"></a>Nástroje  
 Sada nástrojů podpory pro službu bitových kopií byl vytvořen pro vytváření nebo aktualizaci uživatelského rozhraní, která spolupracuje se službou bitové kopie. Další informace o jednotlivých nástrojích naleznete v dokumentaci nástroje. Nástroje jsou součástí [Visual Studio 2015 SDK](visual-studio-sdk.md).
  
 **ManifestFromResources**  
  
 Manifest z prostředků nástroje přebírá seznam prostředků obrázků (PNG nebo XAML) a vygeneruje soubor obrázku manifestu pro použití se službou bitové kopie těchto imagí.  
  
 **ManifestToCode**  
  
 Manifest do kódu – nástroj přebírá soubor manifestu image a vytvoří soubor obálky pro odkazování na manifestu hodnoty v kódu (C++, C# nebo VB) nebo *.vsct* soubory.  
  
 **ImageLibraryViewer**  
  
 Nástroj Prohlížeč knihovny obrázků můžete načíst obrázek manifestů a umožňuje uživatelům s nimi manipulovat stejným způsobem, který sada Visual Studio by zajistit, aby že správně vytvořena manifest. Uživatel může změnit na pozadí, velikosti, nastavení DPI, vysoký kontrast a další nastavení. Také zobrazuje načítání informace pomáhají najít chyby v manifestech a zobrazí informace o zdroji pro každý obrázek v manifestu.  
  
## <a name="faq"></a>Nejčastější dotazy  
  
-   Neexistují žádné závislosti, které uvedete při načítání \<Include="Microsoft.VisualStudio.* odkaz. Interop.14.0.DesignTime"/ >?  
  
    -   Nastavit EmbedInteropTypes = "true" na všechny spolupráce knihovny DLL.  
  
-   Nasazení manifestu obrázků se rozšíření rozhraní my  
  
    -   Přidat *.imagemanifest* soubor do projektu.  
  
    -   "Zahrnout do VSIX" nastavena na hodnotu True.  
  
-   Aktualizuji CPS systému projektu. Co se stalo s **ImageName** a **StockIconService**?  
  
    -   Tyto byly odebrány při aktualizaci CPS použití zástupných názvů. Už nemusíte volat **StockIconService**, stačí pouze předat požadovaný **KnownMoniker** metoda nebo vlastnost pomocí **ToProjectSystemType()** metody rozšíření v prohlášení CPS nástroje. Můžete tu také mapování z **ImageName** k **KnownMonikers** níže:  
  
        |||  
        |-|-|  
        |**ImageName**|**KnownMoniker**|  
        |ImageName.OfflineWebApp|KnownImageIds.Web|  
        |ImageName.WebReferencesFolder|KnownImageIds.Web|  
        |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
        |ImageName.ReferenceFolder|KnownImageIds.Reference|  
        |ImageName.Reference|KnownImageIds.Reference|  
        |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|  
        |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|  
        |ImageName.Folder|KnownImageIds.FolderClosed|  
        |ImageName.OpenFolder|KnownImageIds.FolderOpened|  
        |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|  
        |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|  
        |ImageName.ExcludedFile|KnownImageIds.HiddenFile|  
        |ImageName.DependentFile|KnownImageIds.GenerateFile|  
        |ImageName.MissingFile|KnownImageIds.DocumentWarning|  
        |ImageName.WindowsForm|KnownImageIds.WindowsForm|  
        |ImageName.WindowsUserControl|KnownImageIds.UserControl|  
        |ImageName.WindowsComponent|KnownImageIds.ComponentFile|  
        |ImageName.XmlSchema|KnownImageIds.XMLSchema|  
        |ImageName.XmlFile|KnownImageIds.XMLFile|  
        |ImageName.WebForm|KnownImageIds.Web|  
        |ImageName.WebService|KnownImageIds.WebService|  
        |ImageName.WebUserControl|KnownImageIds.WebUserControl|  
        |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
        |ImageName.AspPage|KnownImageIds.ASPFile|  
        |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
        |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
        |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
        |ImageName.StyleSheet|KnownImageIds.StyleSheet|  
        |ImageName.ScriptFile|KnownImageIds.JSScript|  
        |ImageName.TextFile|KnownImageIds.Document|  
        |ImageName.SettingsFile|KnownImageIds.Settings|  
        |ImageName.Resources|KnownImageIds.DocumentGroup|  
        |ImageName.Bitmap|KnownImageIds.Image|  
        |ImageName.Icon|KnownImageIds.IconFile|  
        |ImageName.Image|KnownImageIds.Image|  
        |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
        |ImageName.XWorld|KnownImageIds.XWorldFile|  
        |ImageName.Audio|KnownImageIds.Sound|  
        |ImageName.Video|KnownImageIds.Media|  
        |ImageName.Cab|KnownImageIds.CABProject|  
        |ImageName.Jar|KnownImageIds.JARFile|  
        |ImageName.DataEnvironment|KnownImageIds.DataTable|  
        |ImageName.PreviewFile|KnownImageIds.Report|  
        |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
        |ImageName.XsltFile|KnownImageIds.XSLTransform|  
        |ImageName.Cursor|KnownImageIds.CursorFile|  
        |ImageName.AppDesignerFolder|KnownImageIds.Property|  
        |ImageName.Data|KnownImageIds.Database|  
        |ImageName.Application|KnownImageIds.Application|  
        |ImageName.DataSet|KnownImageIds.DatabaseGroup|  
        |ImageName.Pfx|KnownImageIds.Certificate|  
        |ImageName.Snk|KnownImageIds.Rule|  
        |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|  
        |ImageName.CSharpProject|KnownImageIds.CSProjectNode|  
        |ImageName.Empty|KnownImageIds.Blank|  
        |ImageName.MissingFolder|KnownImageIds.FolderOffline|  
        |ImageName.SharedImportReference|KnownImageIds.SharedProject|  
        |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|  
        |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|  
        |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|  
        |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|  
        |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|  
  
    -   Aktualizuji poskytovatel seznamu dokončení. Co **KnownMonikers** odpovídat původní **StandardGlyphGroup** a **StandardGlyph** hodnoty?  
  
        ||||  
        |-|-|-|  
        |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
        |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
        |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
        |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
        |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
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
        |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
        |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
        |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
        |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
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
        |GlyphDialogId||Dialogové okno|  
        |GlyphOpenFolder||FolderOpened|  
        |GlyphClosedFolder||FolderClosed|  
        |GlyphArrow||Přejít na další|  
        |GlyphCSharpFile||CSFileNode|  
        |GlyphCSharpExpansion||Fragment kódu|  
        |GlyphKeyword||IntellisenseKeyword|  
        |GlyphInformation||StatusInformation|  
        |GlyphReference||ClassMethodReference|  
        |GlyphRecursion||Rekurze|  
        |GlyphXmlItem||Značka|  
        |GlyphJSharpProject||DocumentCollection|  
        |GlyphJSharpDocument||Dokument|  
        |GlyphForwardType||Přejít na další|  
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
        |GlyphXmlAttribute||Atributy XmlAttribute|  
        |GlyphXmlChild||Třída XmlElement|  
        |GlyphXmlDescendant||XmlDescendant|  
        |GlyphXmlNamespace||XmlNamespace|  
        |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
        |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
        |GlyphXmlChildQuestion||XmlElementLowConfidence|  
        |GlyphXmlChildCheck||XmlElementHighConfidence|  
        |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
        |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
        |GlyphCompletionWarning||IntellisenseWarning|