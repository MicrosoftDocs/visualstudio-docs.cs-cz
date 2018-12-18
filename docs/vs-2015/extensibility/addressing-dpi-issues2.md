---
title: Adresování DPI Problémy2 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 542676de0efabcfa58945fc1572fc5539f52c209
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752524"
---
# <a name="addressing-dpi-issues"></a>Řešení problémů s nastavením DPI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rostoucí počet zařízení, který se dodává s "ve vysokém rozlišení" obrazovky. Tyto obrazovky mají obvykle více než 200 pixely na palec (ICP). K práci s aplikací na těchto počítačích potřebovat obsah vertikálně navyšovat kapacitu pro potřeby zobrazení obsahu na dálku normálního zobrazení zařízení. Primární cíl s vysokou hustotou zobrazí je v době 2014, mobilní, výpočetních zařízeních (tablety, přenosné počítače design a telefony).  
  
 Windows 8.1 a novější obsahuje několik funkcí, které umožňují tyto počítače pracovat se zobrazí a prostředí, kde počítač je připojený k oběma s vysokou hustotou běžný hustota zobrazí ve stejnou dobu.  
  
- Windows vám umožní do změní měřítko obsahu pro zařízení s využitím "Zkontrolujte text a další položky větší nebo menší" nastavení (dostupné od verze Windows XP).  
  
- Windows 8.1 a vyšší budou automaticky změnit měřítko obsahu pro většinu aplikací, aby byla konzistentní při přesunu mezi zobrazí různé hustota pixelů. Když (200 % škálování) s vysokou hustotou je primárního a sekundárního display je standardní hustota (100 %), Windows bude automaticky snižovat obsah okna aplikace na sekundárního display (1 pixelu zobrazí pro každé 4 pixelů vykreslený aplikace).  
  
- Windows se ve výchozím nastavení právo škálování hustota pixelů a zobrazení vzdálenosti použitá pro zobrazení (Windows 7 a vyšší, OEM konfigurovatelné).  
  
- Windows může automaticky škálovat obsahu až 250 % na nová zařízení, které překračují 280 pixelů na palec (od verze Windows 8.1 s.14).  
  
  Windows má způsob řešení problémů s vertikálním navýšení kapacity uživatelského rozhraní, jak využít výhod vyšší pixel počty. Aplikace vyjádřit výslovný souhlas pro tento systém sám deklarací "systém rozpoznání nastavení DPI." Aplikace, které to nedělali se škálovat v systému. Výsledkem může být "přibližné" uživatelské prostředí, kde bude celá aplikace je jednotně pixel roztažená. Příklad:  
  
  ![DPI problémy s fuzzy logikou](../extensibility/media/dpi-issues-fuzzy.png "DPI problémy s fuzzy logikou")  
  
  Vyjádřit výslovný souhlas pro právě DPI škálování s ohledem na Visual Studio a proto není "virtualizovaný."  
  
  Windows (a sady Visual Studio) využívejte několik technologií uživatelského rozhraní, které mají různé způsoby řešení problémů s škálování faktorů nastaví ho systém. Příklad:  
  
- Ovládací prvky WPF měří způsobem nezávislým na zařízení (jednotky, ne pixelů). Rozhraní WPF se automaticky škáluje pro aktuální DPI.  
  
- Všechny velikosti textu bez ohledu na architekturu uživatelského rozhraní jsou vyjádřeny v bodech a tak nakládá systému jako nezávislé na DPI. Text v systému Win32, WinForms a WPF již vertikálně navýšit kapacitu správně při vykreslení zobrazení zařízení.  
  
- Win32/WinForms dialogová okna a windows mají způsoby povolení rozložení, které mění svou velikost textu – například prostřednictvím mřížky, flow a panely rozložení tabulky. Tyto povolit, jak se vyhnout pevně zakódované pixel umístění, které udávají, pokud se zvýší velikost písma.  
  
- Poskytuje systém ikony nebo prostředky na základě metrik systému (například SM_CXICON a SM_CXSMICON) jsou již škálovat.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Starší Win32 (GDI, rozhraní GDI +) a uživatelského rozhraní založeného na WinForms  
 WPF je již vysoké-rozlišení DPI, velkou část našeho kódu založené na Win32/GDI nebyl zapsán původně povědomí o DPI v úvahu. Windows poskytuje rozhraní API pro Škálování DPI. Opravy Win32 by měl použít konzistentně napříč produktu. Visual Studio poskytuje pomocné rutiny knihovny tříd, aby se zabránilo duplikování funkcí a zajištění konzistence napříč produktu.  
  
## <a name="high-resolution-images"></a>Obrázky s vysokým rozlišením  
 Tato část se především pro vývojáře v rozšíření sady Visual Studio 2013. Pro Visual Studio 2015 použijte službu bitových kopií, který je integrovaný do sady Visual Studio. Můžete také zjistit, že budete potřebovat pro podporu nebo cíle mnoho verzí sady Visual Studio a proto službu bitové kopie v 2015 není možné protože neexistuje v předchozích verzích. Tato část bude také za vás.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Vertikální navýšení bitové kopie, které jsou příliš malé  
 Bitové kopie, které jsou příliš malé můžete "vertikálně navýšit" a vykresleného v rozhraní GDI a WPF pomocí některé běžné metody. Spravované DPI pomocné třídy jsou k dispozici pro Visual Studio integrátorům interní a externí adresu škálování ikony, bitmapy, imagestrips a imagelists. Založené na Win32 nativní C / C++ nabízí pomocníky dostupné pro škálování HICON, HBITMAP, HIMAGELIST a VsUI::GdiplusImage. Škálování rastrového obrázku obvykle vyžaduje pouze jeden řádek změnu po zahrnutí odkazu na pomocné knihovny. Příklad:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Škálování třídu imagelist, závisí na, jestli ovládací prvek imagelist dokončení v okamžiku načtení, nebo je připojeno v době běhu. Pokud dokončení v okamžiku načtení volání LogicalToDeviceUnits() s ovládací prvek imagelist, stejně jako rastrový obrázek. Pokud kód potřebuje k načtení jednotlivých rastrový obrázek před sestavování seznamu imagelist, ujistěte se, že škálování velikost seznamu ImageList obrázku:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 Dimenze v nativním kódu, je možné škálovat při vytváření seznamu imagelist následujícím způsobem:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Funkce v knihovně umožňují určit algoritmu změny velikosti. Při škálování Image budou umístěny v imagelists, ujistěte se, že chcete zadat barvu pozadí, který se používá pro průhlednost nebo použití NearestNeighbor škálování (což způsobí narušení 125 % a 150 %).  
  
 Poraďte <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> dokumentaci na webu MSDN.  
  
 Následující tabulka uvádí příklady, jak by měl imagí škálovat na odpovídající DPI škálování faktorů. Obrázky v zelené označují naše osvědčený postup od Visual Studio 2013 (100 – 200 % DPI škálování):  
  
 ![Škálování problémů s nastavením DPI](../extensibility/media/dpi-issues-scaling.png "DPI problémů škálování")  
  
## <a name="layout-issues"></a>Problémy s rozložením  
 Běžné problémy s rozložením se lze vyvarovat primárně udržováním body v uživatelském rozhraní, škálování a vzhledem k mezi sebou, nikoli pomocí absolutní umístění (konkrétně v jednotkách pixelů). Příklad:  
  
- Pozice rozložení/textu třeba upravit počítat s vertikálním navýšením kapacity imagí.  
  
- Sloupce v tabulkách musí mít šířky přizpůsobené pro text vertikálním navýšením kapacity.  
  
- Pevně zakódované velikosti nebo mezeru mezi prvky také potřebovat vertikálně navyšovat kapacitu. Velikosti, které jsou založeny pouze na text dimenze jsou obvykle může být, protože písma automaticky škálovat.  
  
  Pomocné funkce jsou k dispozici v <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> třídu, která umožňuje škálování na ose X a Y:  
  
- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funkce povolit škálování na X a osy Y)  
  
- místo int = DpiHelper.LogicalToDeviceUnitsX (10);  
  
- Výška int = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
  Existují přetížení LogicalToDeviceUnits chcete povolit škálování na objekty, jako jsou OBD, bod a velikosti.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Používání knihovny/třídy DPIHelper měřítka obrázků a rozložení  
 Visual Studio DPI pomocné knihovny je k dispozici ve formulářích nativní a spravované a mimo prostředí sady Visual Studio můžete použít v jiných aplikacích.  
  
 Použití knihovny, přejděte [ukázky VSSDK rozšiřitelnost sady Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples) a naklonujte ukázkové vysoce DPI_Images_Icons  
  
 Ve zdrojových souborech zahrnují VsUIDpiHelper.h a volat statické funkce VsUI::DpiHelper třídy:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Nepoužívejte pomocné funkce v úrovni modulu nebo třídy statické proměnné. Statické knihovny používá také pro synchronizaci vláken a můžete narazit na problémy s inicializací pořadí. Tyto statické převést na nestatické členské proměnné nebo zabalit je do funkce (tak že získat postavená na první přístup).  
  
 Pro přístup k DPI pomocných funkcí ze spravovaného kódu, který se spustí do prostředí sady Visual Studio:  
  
-   Využívání projekt musí odkazovat na nejnovější verzi prostředí MPF. Příklad:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Ujistěte se projekt odkazuje **System.Windows.Forms**, **PresentationCore**, a **PresentationUI**.  
  
-   V kódu, použijte **Microsoft.VisualStudio.PlatformUI** obor názvů a volání statické funkce DpiHelper třídy. U podporovaných typů (body, velikosti, obdélníky a tak dále) jsou za předpokladu škálování funkcí rozšíření, které vrací nové objekty. Příklad:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Práce s WPF tomu bitové kopie v roztahováním uživatelského rozhraní  
 V WPF rastrové obrázky se mění velikost automaticky podle WPF pro aktuální úroveň přiblížení DPI pomocí algoritmu vysoce kvalitní bikubické (výchozí), která funguje dobře pro obrázky nebo velké snímky obrazovky, ale není vhodný pro ikony položky nabídky, protože zavádí vnímaná tomu .  
  
 Doporučení:  
  
- Pro image a Bannery logo obrázky, výchozí <xref:System.Windows.Media.BitmapScalingMode> by bylo možné použít režim změny velikosti.  
  
- Pro Image používá a položky nabídky <xref:System.Windows.Media.BitmapScalingMode> má být použit při nezpůsobí jiné artefakty narušení, chcete-li odstranit tomu (na 200 a 300 %).  
  
- • Pro velké přiblížení úrovně není násobcích 100 % (například 250 % nebo 350 %), změna měřítka obrázků používá s výsledky bikubické v přibližných shod, zesvětlení uživatelského rozhraní. Výsledkem lepší se získá první škálování image NearestNeighbor největší násobek 100 % (například 200 % nebo 300 %) a škálování s bikubické z něj. Najdete v článku zvláštní případ: prescaling WPF imagí pro velké DPI limity pro další informace.  
  
  Člen poskytuje DpiHelper třídy v oboru názvů Microsoft.VisualStudio.PlatformUI <xref:System.Windows.Media.BitmapScalingMode> , který je možné pro vazbu. To vám umožní prostředí sady Visual Studio k řízení rastrového obrázku nastaven režim měřítka napříč produktu rovnoměrně, v závislosti na Měřítko DPI.  
  
  Jeho použití v XAML, přidejte:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Prostředí sady Visual Studio nastaví tuto vlastnost již na nejvyšší úrovni okna a dialogová okna. WPF uživatelského rozhraní založeného na spouštění v sadě Visual Studio zdědí už ho. Pokud toto nastavení není rozšířit na vaše konkrétní části uživatelského rozhraní, lze nastavit v kořenovém elementu uživatelského rozhraní XAML nebo WPF. Automaticky otevíraná okna u elementů s jejich rodiči Win32, zahrnují místa, kde se to stane a návrháře windows, na kterých běží mimo zpracování, jako je například prolnutí.  
  
 Některé uživatelského rozhraní můžete škálovat nezávisle na úroveň přiblížení DPI sada systému, jako je například textový editor sady Visual Studio a Návrháře WPF (WPF Desktop a Windows Store). V takových případech není vhodné používat DpiHelper.BitmapScalingMode. Chcete-li vyřešit tento problém v editoru, integrovaném vývojovém prostředí týmu vytvořili vlastní vlastnost s názvem RenderOptions.BitmapScalingMode. Nastavte tuto hodnotu vlastnosti na HighQuality nebo NearestNeighbor v závislosti na úroveň zvětšení kombinované systému a uživatelské rozhraní.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Zvláštní případ: prescaling WPF imagí pro velké úrovně DPI  
 Pro velmi velké přiblížení úrovně, které nejsou násobkem 100 % (například 250 %, 350 % a tak dále) škálování používá Image s výsledkem bikubické přibližných shod, zesvětlení uživatelského rozhraní. Dojem těchto imagí společně s zřetelný text je téměř stejně jako u iluzí optické. Image se zdají být blíže okem a mimo fokus ve vztahu k textu. Škálování výsledek v tomto zvětšení velikosti lze vylepšit první škálování image NearestNeighbor největší násobek 100 % (například 200 % nebo 300 %) a škálování s bikubické zbývající (s další 50 %).  
  
 Následující je příkladem rozdíly ve výsledcích, kde je první obrázek škálovat s vylepšené škálování double algoritmus-100 % > 200 % -> 250 % a druhý právě díky bikubické 100 % -> 250 %.  
  
 ![DPI vydá Double škálování příklad](../extensibility/media/dpi-issues-double-scaling-example.png "DPI vydá Double škálování příklad")  
  
 Chcete-li povolit možnost použít tento škálování double, značky XAML pro zobrazování jednotlivých prvků Image uživatelského rozhraní bude potřeba upravit. Následující příklady ukazují, jak používat double škálování v subsystému WPF v sadě Visual Studio pomocí knihovny DpiHelper a Shell.12/14.  
  
 Krok 1: Prescale bitové kopie % 200, 300 % a pomocí NearestNeighbor.  
  
 Prescale image pomocí obou převaděč, použitý u vazby nebo pomocí rozšíření značek XAML. Příklad:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Pokud image musí být také s motivem (nejvíce, pokud tomu tak není, by měl), značky můžete použít různé převaděč, který nejprve provede motivů image a pak předem škálování. Značky můžete použít buď <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> nebo <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, v závislosti na požadované převodu výstupu.  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 Krok 2: Ujistěte se, že je správný pro aktuální DPI konečné velikosti.  
  
 Protože WPF škálovaly uživatelského rozhraní pro aktuální DPI BitmapScalingMode vlastnost nastavit UIElement, by měl ovládací prvek obrázku pomocí bitové kopie prescaled jako svůj zdroj bude vypadat dvakrát nebo třikrát větší než. Následuje několik způsobů, jak tento efekt čítače:  
  
-   Pokud znáte dimenze původní bitové kopie na 100 %, můžete zadat přesný velikost ovládacího prvku obrázek. Tyto velikosti, bude odrážet že použít velikost uživatelského rozhraní před Škálováním.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Pokud velikost původní bitové kopie není znám, LayoutTransform umožňuje škálovat směrem dolů, do konečného objektu Image. Příklad:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>Povolení podpory HDPI k WebOC  
 Ve výchozím nastavení WebOC ovládací prvky (například ovládací prvek WebBrowser v WPF nebo rozhraní rozhraní IWebBrowser2) nepovolí HDPI zjišťování a podporu. Výsledkem bude vloženému ovládacímu prvku s zobrazit obsah, který je příliš malá v zobrazení s vysokým rozlišením. Následující popisuje, jak povolit podporu vysokých hodnot DPI v instanci WebOC konkrétní web.  
  
 Implementovat rozhraní IDocHostUIHandler (na najdete v článku na webu MSDN [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) rozhraní):  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 Implementujte rozhraní ICustomDoc (na najdete v článku na webu MSDN [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) rozhraní):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Třídy, která implementuje IDocHostUIHandler s dokumentem WebOC přidružte. Pokud jste implementovali rozhraní ICustomDoc výše, pak jako vlastnost dokumentu WebOC je platný, jej přetypovat ICustomDoc a volat metodu SetUIHandler předává třídu, která implementuje IDocHostUIHandler.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Pokud rozhraní ICustomDoc neimplementoval, poté co nejdříve vlastnost dokumentu WebOC je platná, musíte jej přetypovat IOleObject a volat metodu SetClientSite předávání ve třídě, která implementuje IDocHostUIHandler. Nastavte příznak DOCHOSTUIFLAG_DPI_AWARE DOCHOSTUIINFO předává do volání metody GetHostInfo:  
  
```csharp  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 To by měl být vše, co je potřeba získat WebOC ovládacího prvku pro podporu HPDI.  
  
## <a name="tips"></a>Tipy  
  
1.  Pokud se změní vlastnost dokumentu v ovládacím prvku WebOC, můžete potřebovat přidružení IDocHostUIHandler třídy dokumentu.  
  
2.  Pokud výše uvedené nebude fungovat, je známý problém s WebOC není ujímají změnu příznaku DPI. Nejspolehlivější způsob, jak to opravy je přepnete optické přiblížení WebOC význam dvě volání s dvě různé hodnoty pro procento zvětšení. Kromě toho pokud toto řešení je potřeba, může být potřeba provádět při každém volání navigace.  
  
    ```csharp  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```

