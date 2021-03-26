---
title: Adresování DPI Issues2 | Microsoft Docs
description: Přečtěte si o problémech týkajících se programování pro obrazovky s vysokým rozlišením, jako je například škálování obsahu, problémy rozložení a používání rozhraní API pro škálování přes DPI.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9cf7b4fe19cdefe11b77de1418b16454089f45c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097510"
---
# <a name="address-dpi-issues"></a>Problémy s adresou DPI
Rostoucí počet zařízení se dodává s obrazovkami s vysokým rozlišením. Tyto obrazovky obvykle mají více než 200 pixelů na palec (ppi). Práce s aplikací na těchto počítačích bude vyžadovat, aby se obsah navzájem škálovat tak, aby splňoval požadavky na zobrazení obsahu v normální vzdálenosti pro zařízení. Od 2014 je primární cíl pro zobrazení s vysokou hustotou mobilní výpočetní zařízení (tablety, clamshell přenosné počítače a telefony).

Windows 8.1 a vyšší obsahuje několik funkcí, které těmto počítačům umožňují pracovat s monitory a prostředími, kde je počítač připojen k obou hodnotám s vysokou hustotou a standardní hustotou.

- Systém Windows vám umožní škálovat obsah na zařízení pomocí nastavení "nastavit text a další položky větší nebo menší" (k dispozici od Windows XP).

- Windows 8.1 a vyšší automaticky škálují obsah pro většinu aplikací tak, aby byly konzistentní při přesunu mezi zobrazeními různých hustot pixelů. Když je primární displej vysoký hustota (200% škálování) a sekundární displej má standardní hustotu (100%), Windows automaticky škáluje obsah okna aplikace v sekundárním zobrazení (1 pixel se zobrazuje pro každé 4 pixely vykreslené aplikací).

- Systém Windows bude mít ve výchozím nastavení správné měřítko pro hustotu pixelů a zobrazení vzdálenosti pro displej (Windows 7 a vyšší, OEM-konfigurovatelný).

- Systém Windows dokáže automaticky škálovat obsah až na 250% na nových zařízeních, která přesahují 280 PPI (od Windows 8.1 S14).

  Systém Windows nabízí možnost nabývat se škálováním uživatelského rozhraní pro využití většího počtu pixelů. Aplikace výslovný do tohoto systému tím, že deklaruje samou "systémovou podporu DPI". Aplikace, které to nedělají, se škálují podle systému. Výsledkem může být přibližné uživatelské prostředí, kde je celá aplikace rovnoměrně roztažena na pixel. Například:

  ![Přibližné problémy s DPI](../extensibility/media/dpi-issues-fuzzy.png "Přibližné problémy s DPI")

  Aplikace Visual Studio výslovný v pro škálování DPI, a proto není virtualizovaná.

  Windows (a Visual Studio) využívají několik technologií uživatelského rozhraní, které mají různý způsob, jak řešit faktory škálování nastavené systémem. Například:

- WPF měří ovládací prvky v cestě nezávislé na zařízení (jednotky, ne pixely). Uživatelské rozhraní WPF automaticky škáluje na aktuální DPI.

- Všechny velikosti textu bez ohledu na rámec uživatelského rozhraní jsou vyjádřeny v bodech a jsou proto zpracovány systémem jako nezávislé na rozlišení DPI. Text v Win32, WinForms a WPF se už při vykreslování na zobrazovací zařízení správně škáluje.

- Dialogová okna Win32/WinForms a Windows mají za úkol povolit rozložení, která mění velikost textu (například prostřednictvím mřížky, toku a panelů rozložení tabulky). Tato možnost umožňuje zabránit pevně zakódovaným umístěním v pixelech, které se při zvýšení velikosti písma nezmění.

- Ikony poskytované systémem nebo prostředky na základě systémových metrik (například SM_CXICON a SM_CXSMICON) jsou již škálované.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Starší rozhraní Win32 (GDI, GDI+) a uživatelské rozhraní založené na WinForms
I když je WPF již vysokým rozlišením DPI, mnoho z našich kódu založených na Win32/GDI nebylo původně napsáno s ohledem na rozlišení DPI. Systém Windows zadal rozhraní API pro škálování přes DPI. Opravy problémů Win32 by se měly konzistentně používat v rámci produktu. Visual Studio poskytuje pomocnou knihovnu tříd, aby se předešlo duplicitě funkcí a zajistila se konzistence napříč produktem.

## <a name="high-resolution-images"></a>Obrázky s vysokým rozlišením
Tato část je primárně určená pro vývojáře, kteří rozšiřují Visual Studio 2013. Pro Visual Studio 2015 použijte službu Image Service, která je integrovaná do sady Visual Studio. Můžete také zjistit, že potřebujete podporovat nebo cílit na mnoho verzí sady Visual Studio, a proto použití služby image v 2015 není možností, protože neexistuje v předchozích verzích. Tato část je také k disdobu.

## <a name="scaling-up-images-that-are-too-small"></a>Horizontální navýšení nebo zmenšení velikosti imagí
Obrázky, které jsou příliš malé, lze škálovat a vykreslovat pomocí GDI a WPF pomocí některých běžných metod. Spravované pomocné třídy DPI jsou k dispozici pro interní a externí integrátory sady Visual Studio k adresování ikon škálování, rastrových obrázků, imagestrips a ImageList. K dispozici jsou nativní pomocníky C/C + + založené na Win32 pro škálování HICON, HBITMAP, HIMAGELIST a Vsui nebyla rozpoznána:: GdiplusImage. Škálování rastrového obrázku obvykle vyžaduje pouze změnu jednoho řádku po zahrnutí odkazu do pomocné knihovny. Například:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Změna velikosti seznamu ImageList závisí na tom, zda je ovládací prvek ImageList dokončen v době načítání nebo je připojen v době běhu. Pokud je dokončeno v době načítání, zavolejte `LogicalToDeviceUnits()` pomocí ovládacího prvku ImageList jako rastrový obrázek. Když kód potřebuje načíst jednotlivou bitmapu před vytvořením seznamu ImageList, nezapomeňte škálovat velikost obrázku ovládacího prvku ImageList:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

V nativním kódu lze dimenze škálovat při vytváření seznamu ImageList následujícím způsobem:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Funkce v knihovně umožňují zadat algoritmus změny velikosti. Při škálování obrázků, které se mají umístit do ImageList, nezapomeňte zadat barvu pozadí, která se má použít k průhlednosti, nebo použít škálování NearestNeighbor (což způsobí deformaci na 125% a 150%).

Projděte si <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> dokumentaci na webu MSDN.

V následující tabulce jsou uvedeny příklady, jak mají být obrázky škálované v odpovídajících faktorech škálování DPI. Obrázky popsaných v oranžovém textu jsou osvědčené postupy Visual Studio 2013 (100% až 200% DPI):

![Škála DPI pro problémy](../extensibility/media/dpi-issues-scaling.png "Škála DPI pro problémy")

## <a name="layout-issues"></a>Problémy s rozložením
Běžným problémům s rozložením se můžete vyhnout především tím, že se body v uživatelském rozhraní navzájem škálují a jsou relativní od sebe, a ne pomocí absolutních umístění (konkrétně v jednotkách pixelů). Například:

- Pro obrázky škálované na více místech je nutné upravit rozložení/umístění textu na účet.

- Sloupce v Gridech musí mít upravenou šířku pro text s možností horizontálního navýšení kapacity.

- Také je potřeba škálovat pevně zakódované velikosti nebo prostor mezi prvky. Velikosti, které jsou založené jenom na rozměrech textu, jsou obvykle přesné, protože se automaticky škálují velikost písem.

  Pomocné funkce jsou ve třídě k dispozici <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> pro povolení škálování na ose X a Y:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funkce povolující škálování na ose X/Y)

- int Space = DpiHelper. LogicalToDeviceUnitsX (10);

- int Height = Vsui nebyla rozpoznána::D piHelper:: LogicalToDeviceUnitsY (5);

  K dispozici jsou LogicalToDeviceUnits přetížení, aby bylo možné objekty škálování, jako je například Rect, Point a Size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Použití knihovny/třídy DPIHelper ke škálování obrázků a rozložení
Pomocná knihovna DPI sady Visual Studio je k dispozici v nativních a spravovaných formulářích a lze ji použít mimo prostředí sady Visual Studio jinými aplikacemi.

Pokud chcete použít knihovnu, navštivte [Ukázky rozšiřitelnosti sady Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) a naklonujte ukázku High-DPI_Images_Icons.

Ve zdrojových souborech vložte *VsUIDpiHelper. h* a zavolejte statické funkce `VsUI::DpiHelper` třídy:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Nepoužívejte pomocné funkce ve statických proměnných na úrovni modulu nebo třídy. Knihovna také používá statické objekty pro synchronizaci vláken a můžete spustit v případě problémů s inicializací. Buď převod těchto statických na nestatické proměnné členů, nebo jejich zabalení do funkce (takže se vytvoří při prvním přístupu).

Pro přístup k podpůrným funkcím DPI ze spravovaného kódu, který se spustí v prostředí sady Visual Studio:

- Nenáročný projekt musí odkazovat na nejnovější verzi prostředí MPF. Například:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Ujistěte se, že projekt obsahuje odkazy na **System. Windows. Forms**, **PresentationCore** a **PresentationUI**.

- V kódu použijte obor názvů **Microsoft. VisualStudio. PlatformUI** a volejte statické funkce třídy DpiHelper. Pro podporované typy (body, velikosti, obdélníky atd.) jsou k dispozici funkce rozšíření, které vracejí nové objekty s měřítkem. Například:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Práce s imagemi WPF tomu v uživatelském rozhraní s přiblížením
V technologii WPF se automaticky mění velikost rastrových obrázků WPF pro aktuální úroveň přiblížení v DPI pomocí vysoce kvalitního bikubické algoritmu (výchozí), který funguje dobře pro obrázky nebo velké snímky obrazovky, ale je nevhodný pro ikony položek nabídek, protože zavádí vnímaný tomu.

Doporučení:

- V případě obrázku loga a kresby bannerů se <xref:System.Windows.Media.BitmapScalingMode> dá použít výchozí režim změny velikosti.

- V případě položek nabídky a Iconography obrázků <xref:System.Windows.Media.BitmapScalingMode> by se měla použít, když nezpůsobí jiné artefakty deformace k vyloučení tomu (na 200% a 300%).

- Pro velké úrovně přiblížení nepatří mezi násobky 100% (například 250% nebo 350%), škálování Iconography imagí pomocí bikubické má za následek přibližné a vybledlé uživatelské rozhraní. Lepší výsledek se získá tak, že se napřed velikost bitové kopie NearestNeighbor na největší násobek 100% (například 200% nebo 300%). a škálujte pomocí bikubické. Další informace najdete v tématu zvláštní případ: předškálování obrázků WPF pro velké úrovně DPI.

  Třída DpiHelper v oboru názvů Microsoft. VisualStudio. PlatformUI poskytuje člen <xref:System.Windows.Media.BitmapScalingMode> , který lze použít pro vazbu. Umožní prostředí sady Visual Studio řídit režim škálování rastrového obrázku napříč produktem jednotně v závislosti na faktoru škálování DPI.

  Pokud ho chcete použít v jazyce XAML, přidejte:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Prostředí sady Visual Studio už tuto vlastnost nastavuje v oknech a oknech nejvyšší úrovně. Uživatelské rozhraní založené na WPF, které běží v aplikaci Visual Studio, ho už zdědí. Pokud se nastavení nerozšíří na vaše konkrétní části uživatelského rozhraní, může být nastaveno na kořenovém prvku uživatelského rozhraní XAML/WPF. Místo, kde k tomu dojde, patří automaticky otevíraná okna, u elementů s nadřazenými prvky Win32 a v oknech návrháře, jejichž zpracování je mimo proces, jako je například Blend.

Některé uživatelské rozhraní se může škálovat nezávisle na úrovni přiblížení DPI nastavené systémem, jako je textový editor sady Visual Studio a Návrháři založené na WPF (Desktop WPF a Windows Store). V těchto případech by se neměl používat DpiHelper. BitmapScalingMode. Chcete-li tento problém vyřešit v editoru, vytvořil tým IDE vlastní vlastnost s názvem RenderOptions. BitmapScalingMode. Nastavte tuto hodnotu vlastnosti na HighQuality nebo NearestNeighbor v závislosti na kombinované úrovni přiblížení systému a uživatelského rozhraní.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Zvláštní případ: zmenšení měřítka obrázků WPF pro velké úrovně DPI
U velmi velkých úrovní přiblížení, které nepatří mezi násobky 100% (například 250%, 350% atd.), škálování Iconography imagí s bikubické výsledky v přibližném a neočekávaném uživatelském rozhraní. Dojem těchto obrázků spolu s ostrým textem je skoro podobný optické iluzi. Obrázky se zdají být blíž k očí a ve vztahu k textu jsou mimo fokus. Výsledek škálování v této zvětšené velikosti se dá zlepšit tak, že se napřed velikost obrázku NearestNeighbor na největší násobek 100% (například 200% nebo 300%). a škálování s bikubickéem na zbytek (další 50%).

Následuje příklad rozdílů ve výsledcích, kdy se na první obrázek škáluje pomocí vylepšeného algoritmu dvojitého škálování 100%->200%->250% a druhý postup s bikubické 100%->250%.

![Příklad dvojitého škálování problémů v DPI](../extensibility/media/dpi-issues-double-scaling-example.png "Příklad dvojitého škálování problémů v DPI")

Aby bylo možné povolit uživatelské rozhraní pro použití tohoto dvojitého škálování, kód XAML pro zobrazení každého elementu obrázku bude nutné upravit. Následující příklady ukazují, jak používat dvojité škálování v WPF v aplikaci Visual Studio pomocí knihovny DpiHelper a prostředí. 12/14.

Krok 1: zmenšení bitové kopie na 200%, 300% a tak dále pomocí NearestNeighbor.

Zmenšete měřítko obrázku pomocí převaděče aplikovaného na vazbu nebo pomocí rozšíření značek XAML. Například:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Pokud je nutné, aby bitová kopie měla také motiv (nejvíce, pokud to není vše), značky mohou používat jiný převaděč, který nejprve provede tento obrázek a pak předem škálovat. Značky mohou použít buď <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> nebo <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> , v závislosti na požadovaném výstupu převodu.

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

Krok 2: Zajistěte, aby byla konečná velikost pro aktuální DPI správná.

Vzhledem k tomu, že WPF bude škálovat uživatelské rozhraní pro aktuální rozlišení DPI pomocí vlastnosti BitmapScalingMode nastavené u prvku UIElement, ovládací prvek obrázek s použitím obrázku s přednastaveným měřítkem bude vypadat dvakrát nebo třikrát větší, než by měl. Toto je několik způsobů, jak tento efekt načítačit:

- Pokud znáte rozměr původní image v 100%, můžete zadat přesnou velikost ovládacího prvku obrázek. Tyto velikosti budou odrážet velikost uživatelského rozhraní před použitím škálování.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Pokud není známa velikost původního obrázku, lze LayoutTransform použít ke snížení kapacity konečného objektu obrázku. Například:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Povolení podpory HDPI pro WebOC
Ve výchozím nastavení ovládací prvky WebOC (například ovládací prvek WebBrowser v WPF nebo rozhraní IWebBrowser2) nepovolují detekci HDPI a podporu. Výsledkem bude vložený ovládací prvek se zobrazeným obsahem, který je příliš malý pro zobrazení s vysokým rozlišením. V následující části se dozvíte, jak povolit podporu vysokého počtu DPI v konkrétní instanci webu WebOC.

Implementace rozhraní IDocHostUIHandler (viz článek na webu MSDN na [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

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

Volitelně implementujte rozhraní ICustomDoc (viz článek na webu MSDN na [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Přidružte třídu, která implementuje IDocHostUIHandler, k dokumentu WebOC. Pokud jste implementovali rozhraní ICustomDoc výše, potom jakmile je vlastnost dokumentu WebOC platná, přetypujte ji na ICustomDoc a zavolejte metodu SetUIHandler, která předává třídu, která implementuje IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Pokud jste rozhraní ICustomDoc neimplementovali, pak Jakmile je vlastnost dokumentu WebOC platná, je nutné ji přetypovat na IOleObject a volat `SetClientSite` metodu, která implementuje IDocHostUIHandler. Nastavte příznak DOCHOSTUIFLAG_DPI_AWARE DOCHOSTUIINFO předanému `GetHostInfo` volání metody:

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

To by mělo být všechno, co potřebujete k tomu, abyste mohli WebOC ovládací prvek pro podporu HPDI.

## <a name="tips"></a>Tipy

1. Pokud se změní vlastnost dokumentu na ovládacím prvku WebOC, může být nutné znovu přidružit dokument ke třídě IDocHostUIHandler.

2. Pokud výše uvedený postup nefunguje, existuje známý problém s WebOCem, který nevybírá změnu příznaku DPI. Nejspolehlivějším způsobem, jak to opravit, je přepnout Optické přiblížení WebOC, což znamená, že dvě volání se dvěma různými hodnotami pro procento zvětšení. Kromě toho, pokud je toto řešení vyžadováno, může být nutné jej provést při každém volání navigace.

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
