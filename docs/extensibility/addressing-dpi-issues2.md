---
title: Řešení problémů dpi2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740104"
---
# <a name="address-dpi-issues"></a>Řešení problémů s DPI
Stále větší počet zařízení se dodává s obrazovkami s "vysokým rozlišením". Tyto obrazovky mají obvykle více než 200 pixelů na palec (ppi). Práce s aplikací v těchto počítačích bude vyžadovat, aby byl obsah škálován tak, aby vyhovoval potřebám zobrazení obsahu v normální vzdálenosti zobrazení zařízení. Od roku 2014 jsou primárním cílem displejů s vysokou hustotou mobilní výpočetní zařízení (tablety, notebooky a telefony).

Windows 8.1 a vyšší obsahuje několik funkcí, které umožňují těmto strojům pracovat s displeji a prostředími, kde je počítač připojen k displejům s vysokou hustotou i standardní hustotou současně.

- Systém Windows umožňuje škálovat obsah do zařízení pomocí nastavení Nastavit text a další položky větší nebo menší (dostupné od systému Windows XP).

- Windows 8.1 a vyšší automaticky změní měřítko obsahu pro většinu aplikací tak, aby byl konzistentní při přesunu mezi displeji s různou hustotou pixelů. Pokud je primární mitaní displeje s vysokou hustotou (200% změna měřítka) a sekundární mita je standardní hustota (100 %), systém Windows automaticky změní měřítko obsahu okna aplikace na sekundárním displeji (1 pixel zobrazený na každé 4 pixely vykreslené aplikací).

- Systém Windows bude výchozí pro správnou změnu měřítka pro hustotu pixelů a vzdálenost zobrazení displeje (Windows 7 a vyšší, konfigurovatelné oem).

- Windows může automaticky škálovat obsah až na 250% na nových zařízeních, která překročí 280 ppi (od Windows 8.1 S14).

  Systém Windows má způsob, jak se vypořádat s škálováním v y ui využít zvýšené počty pixelů. Aplikace se přihlásí do tohoto systému tím, že deklaruje sebe "systém DPI vědomi." Aplikace, které to nedělají, jsou škálovány systémem. To může mít za následek "fuzzy" uživatelské prostředí, kde je celá aplikace rovnoměrně roztažena pixel. Například:

  ![Problémy S DPI při blízce](../extensibility/media/dpi-issues-fuzzy.png "Problémy S DPI při blízce")

  Visual Studio se přihlásí k nastavení podle velikosti DPI, a proto není "virtualizované".

  Windows (a Visual Studio) využívají několik technologií ui, které mají různé způsoby řešení faktory škálování nastavené systémem. Například:

- WPF měří ovládací prvky způsobem nezávislým na zařízení (jednotky, nikoli pixely). WPF UI automaticky navíjí pro aktuální DPI.

- Všechny velikosti textu bez ohledu na rozhraní rozhraní jsou vyjádřeny v bodech, a proto jsou systémem považovány za nezávislé na DPI. Text ve Win32, WinForms a WPF již škálovat správně při nakreslené na zobrazovací zařízení.

- Dialogy a okna Win32/WinForms mají prostředky pro povolení rozložení, které se změní velikost s textem (například prostřednictvím mřížky, toku a panelů rozložení tabulky). Ty umožňují vyhnout se pevně zakódované umístění pixelů, které nejsou zmenšeny při zvětšení velikosti písma.

- Ikony poskytované systémem nebo prostředky na základě systémových metrik (například SM_CXICON a SM_CXSMICON) jsou již navýšeny.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Starší win32 (GDI, GDI+) a winforms-založené ui
Zatímco WPF je již vysoká DPI-aware, hodně z našeho Win32/GDI-založené kód nebyl původně napsán s ohledem na povědomí DPI. Systém Windows poskytuje nastavení API pro škálování DPI. Opravy win32 problémy by měly používat tyto konzistentně v celém produktu. Visual Studio poskytuje knihovnu pomocných tříd, aby se zabránilo duplikování funkcí a zajištění konzistence v celém produktu.

## <a name="high-resolution-images"></a>Obrázky ve vysokém rozlišení
Tato část je určena především pro vývojáře, kteří rozšiřují Visual Studio 2013. Pro Visual Studio 2015 použijte image služby, která je integrovaná do Sady Visual Studio. Můžete také zjistit, že je třeba podporovat nebo cílit na mnoho verzí sady Visual Studio, a proto použití služby bitové kopie v 2015 není možnost, protože neexistuje v předchozích verzích. Tato část je také pro vás pak.

## <a name="scaling-up-images-that-are-too-small"></a>Škálování obrazů, které jsou příliš malé
Obrázky, které jsou příliš malé lze škálovat nahoru a vykreslenna na GDI a WPF pomocí některé běžné metody. Spravované třídy pomocníků DPI jsou k dispozici interním a externím integrátorům sady Visual Studio, které řeší ikony škálování, bitmapy, ibitové pásy a imagelisty. Nativní pomocné klávesy založené na win32 jsou k dispozici pro škálování HICON, HBITMAP, HIMAGELIST a VsUI::GdiplusImage. Změna velikosti rastrového obrázku obvykle vyžaduje pouze jednořádkovou změnu po zahrnutí odkazu na pomocnou knihovnu. Například:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Změna velikosti seznamu obrázků závisí na tom, zda je seznam obrázků dokončen v době načítání nebo je připojen za běhu. Pokud je dokončena `LogicalToDeviceUnits()` v době načítání, volejte s imagelist stejně jako bitmap. Když kód potřebuje načíst jednotlivé bitmapy před dokončením seznamu obrázků, ujistěte se, že měřítko velikosti obrázku seznamu obrázků:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

V nativním kódu lze rozměry při vytváření seznamu obrázků změnit následujícím způsobem:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Funkce v knihovně umožňují určení algoritmu změny velikosti. Při změně velikosti obrázků, které mají být umístěny v seznamech obrázků, ujistěte se, že určit barvu pozadí, která se používá pro průhlednost, nebo použijte NearestNeighbor měřítko (což způsobí zkreslení na 125 % a 150 %).

Prostudujte <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> si dokumentaci k msdn.

V následující tabulce jsou uvedeny příklady měřítka image podle odpovídajících faktorů měřítka DPI. Obrázky nastíněné oranžově označují náš osvědčený postup od Visual Studia 2013 (100%-200% škálování DPI):

![Škálování problémů s dpi](../extensibility/media/dpi-issues-scaling.png "Škálování problémů s dpi")

## <a name="layout-issues"></a>Problémy s rozložením
Běžným problémům s rozložením se lze vyhnout především udržováním bodů v uživatelském rozhraní a vzhledem k sobě navzájem, nikoli pomocí absolutních umístění (konkrétně v jednotkách pixelů). Například:

- Pozice rozvržení/textu se musí přizpůsobit tak, aby odpovídaly zmenšeným obrázkům.

- Sloupce v mřížce musí mít šířky upravené pro text s měřítkem.

- Pevně zakódované velikosti nebo mezery mezi prvky bude také nutné škálovat nahoru. Velikosti, které jsou založeny pouze na rozměrech textu, jsou obvykle v pořádku, protože písma se automaticky zvětšují.

  Pomocné funkce jsou <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> k dispozici ve třídě, která umožňuje změnu měřítka na ose X a Y:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funkce umožňují změnu měřítka na ose X/Y)

- int mezera = DpiHelper.LogicalToDeviceUnitsX (10);

- int height = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);

  Existují LogicalToDeviceUnits přetížení povolit škálování objektů, jako je například Rect, Point a Size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Použití knihovny/třídy DPIHelper ke škálování obrázků a rozvržení
Pomocná knihovna Visual Studio DPI je k dispozici v nativních a spravovaných formulářích a může být použita mimo prostředí sady Visual Studio jinými aplikacemi.

Chcete-li použít knihovnu, přejděte na [ukázky rozšiřitelnosti sady Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) a klonovat ukázku high-DPI_Images_Icons.

Ve zdrojových souborech zahrňte *VsUIDpiHelper.h* a volejte statické funkce třídy: `VsUI::DpiHelper`

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Nepoužívejte pomocné funkce ve statických proměnných na úrovni modulu nebo třídy. Knihovna také používá statice pro synchronizaci vláken a může dojít k problémům s inicializací objednávky. Buď převést tyto statické proměnné nestatické členské proměnné nebo zabalit do funkce (tak se zkonstruovat při prvním přístupu).

Přístup k funkcím pomocné spoje DPI ze spravovaného kódu, který bude spuštěn v prostředí sady Visual Studio:

- Náročný projekt musí odkazovat na nejnovější verzi prostředí MPF. Například:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Ujistěte se, že projekt má odkazy na **System.Windows.Forms**, **PresentationCore**a **PresentationUI**.

- V kódu použijte obor názvů **Microsoft.VisualStudio.PlatformUI** a volejte statické funkce třídy DpiHelper. Pro podporované typy (body, velikosti, obdélníky a tak dále) jsou k dispozici rozšiřující funkce, které vracejí nové objekty s měřítkem. Například:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Řešení wpf obrazu fuzziness v zoomable UI
V WPF bitmapy jsou automaticky velikost wpf pro aktuální úroveň zvětšení DPI pomocí vysoce kvalitní bikubický algoritmus (výchozí), který funguje dobře pro obrázky nebo velké screenshoty, ale je nevhodné pro ikony položek nabídky, protože zavádí vnímané fuzziness.

Doporučení:

- Pro obrázek loga a <xref:System.Windows.Media.BitmapScalingMode> kresbu bannerů lze použít výchozí režim změna velikosti.

- U položek nabídky a ikonografických <xref:System.Windows.Media.BitmapScalingMode> obrazů by měl být použit, pokud nezpůsobí jiné artefakty zkreslení, které eliminují rozmazání (při 200 % a 300 %).

- U velkých úrovní zvětšení není násobky 100 % (například 250 % nebo 350 %), změna velikosti ikonografických obrazů s bikubickými výsledky v fuzzy, vybledlém uzlení. Lepší výsledek je dosaženo nejprve škálování obrazu s NearestNeighbor na největší násobek 100 % (například 200 % nebo 300 %) a škálování s bikubické odtud. Další informace naleznete v tématu Zvláštní případ: předběžné škálování bitových kopií WPF pro velké úrovně DPI.

  Třída DpiHelper v oboru názvů Microsoft.VisualStudio.PlatformUI <xref:System.Windows.Media.BitmapScalingMode> poskytuje člena, který lze použít pro vazbu. To umožní prostředí Visual Studio řídit režim změny velikosti bitmapy v celém produktu rovnoměrně, v závislosti na faktor uchajení DPI.

  Chcete-li jej použít v XAML, přidejte:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Prostředí Visual Studio již nastaví tuto vlastnost v oknech nejvyšší úrovně a dialogových oknech. WPF založené na ukrajině spuštěné v sadě Visual Studio již zdědí. Pokud se nastavení nerozšíří do konkrétního uživatelského rozhraní, lze jej nastavit na kořenovém prvku uživatelského rozhraní XAML/WPF. Místa, kde k tomu dojde, zahrnují automaticky otevíraná okna, na prvky s nadřazenými prvky win32 a okna návrháře, která vyjdou proces, například Blend.

Některé ui můžete škálovat nezávisle na úrovni přiblížení dpi sady systému, jako je například textový editor Visual Studio a WPF-založené návrháři (WPF Desktop a Windows Store). V těchto případech DpiHelper.BitmapScaleingMode by neměl být používán. Chcete-li tento problém vyřešit v editoru, tým IDE vytvořil vlastní vlastnost s názvem RenderOptions.BitmapScalingMode. Nastavte tuto hodnotu vlastnosti na HighQuality nebo NearestNeighbor v závislosti na kombinované úrovni přiblížení systému a vašeho uj.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Zvláštní případ: předškálování obrazů WPF pro velké úrovně DPI
U velmi velkých úrovní zvětšení, které nejsou násobky 100 % (například 250 %, 350 % a tak dále), můžete škálovat ikonografické obrazy s bikubickými výsledky v neostrém, vybledlém uzlení. Dojem z těchto obrazů vedle ostrého textu je téměř jako optický iluzi. Obrázky se zdají být blíže k oku a rozostřené ve vztahu k textu. Změna měřítka výsledek v této zvětšené velikosti lze zlepšit nejprve škálování obrazu s NearestNeighbor na největší násobek 100 % (například 200 % nebo 300 %) a škálování s bikubickým do konce (dalších 50%).

Následuje příklad rozdílů ve výsledcích, kde je měřítko prvního obrázku s vylepšeným algoritmem dvojitého škálování 100%->200%->250% a druhý pouze s bikubickým 100%->250%.

![Příklad dvojího škálování problémů DPI](../extensibility/media/dpi-issues-double-scaling-example.png "Příklad dvojího škálování problémů DPI")

Chcete-li povolit uživatelskérozhraní používat toto dvojité škálování, xaml značky pro zobrazení každého prvku image bude muset být změněn. Následující příklady ukazují, jak používat dvojité škálování v WPF v sadě Visual Studio pomocí knihovny DpiHelper a prostředí.12/14.

Krok 1: Předškálovat obrázek na 200 %, 300 % a tak dále pomocí NearestNeighbor.

Přednastavení obrazu pomocí převaděče použitého na vazbu nebo pomocí rozšíření značek XAML. Například:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Pokud obraz také musí být tématem (většina, ne-li všechny, by), značky můžete použít jiný převaděč, který nejprve se motivy obrazu a pak pre-škálování. Značka může použít <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> buď <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>nebo , v závislosti na požadovaném výstupu převodu.

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

Krok 2: Ujistěte se, že konečná velikost je správná pro aktuální DPI.

Vzhledem k tomu, že WPF změní měřítko uI pro aktuální DPI pomocí BitmapScalingMode vlastnost nastavena na UIElement, image ovládací prvek pomocí předškálované ho obraz jako jeho zdroj bude vypadat dvakrát nebo třikrát větší, než by měl. Níže jsou uvedeny několik způsobů, jak čelit tomuto efektu:

- Pokud znáte rozměr původního obrazu na 100 %, můžete určit přesnou velikost ovládacího prvku Obraz. Tyto velikosti budou odrážet velikost ui před škálování je použita.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Pokud není známa velikost původního obrazu, LayoutTransform lze změnit měřítko konečný image objektu. Například:

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
Ve výchozím nastavení ovládací prvky WebOC (například ovládací prvek WebBrowser v WPF nebo rozhraní IWebBrowser2) neumožňují detekci hdpi a podporu. Výsledkem bude vložený ovládací prvek s obsahem zobrazení, který je na displeji s vysokým rozlišením příliš malý. Následující text popisuje, jak povolit podporu vysokého DPI v konkrétní instanci webového weboc.

Implementujte rozhraní IDocHostUIHandler (viz článek MSDN na [iDocHostUIHandler :](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85))

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

Volitelně implementujte rozhraní ICustomDoc (viz článek MSDN na [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Přidružte třídu, která implementuje IDocHostUIHandler s dokumentem WebOC. Pokud jste implementovali rozhraní ICustomDoc výše, pak jakmile weboc je vlastnost dokumentu je platný, přetypovat do ICustomDoc a volání SetUIHandler metoda, předávání třídy, která implementuje IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Pokud jste neimplementovali rozhraní ICustomDoc, pak jakmile weboc je vlastnost dokumentu je platný, budete muset přetypovat `SetClientSite` do IOleObject a volat metodu, předávání ve třídě, která implementuje IDocHostUIHandler. Nastavte příznak DOCHOSTUIFLAG_DPI_AWARE na dochostuiinfo `GetHostInfo` předané volání metody:

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

To by mělo být vše, co potřebujete k získání ovládacího prvku WebOC pro podporu HPDI.

## <a name="tips"></a>Tipy

1. Pokud se změní vlastnost document na ovládacím prvku WebOC, možná budete muset znovu přidružit dokument ke třídě IDocHostUIHandler.

2. Pokud výše uvedené nefunguje, je známý problém s WebOC není vyzvednutí změny příznaku DPI. Nejspolehlivějším způsobem, jak to opravit, je přepnout optický zoom WebOC, což znamená dvě volání se dvěma různými hodnotami pro procento zvětšení. Navíc pokud je toto řešení vyžadováno, může být nutné provést při každém volání navigace.

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
