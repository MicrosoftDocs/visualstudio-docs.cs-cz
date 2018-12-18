---
title: Nástroj příkazového řádku pro zachytávání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4cafc8c066025f87d233d8b6db8a97be1aa16f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770692"
---
# <a name="command-line-capture-tool"></a>Nástroj příkazového řádku pro zachytávání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DXCap.exe je nástroj příkazového řádku pro zachycení diagnostiky grafiky a přehrávání. Podporuje Direct3D 10 až Direct3D 12 přes všechny funkce úrovně.  
  
## <a name="syntax"></a>Syntaxe  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe –p [filename] –screenshot [-frame frames]  
DXCap.exe –p [filename] –toXML [xml_filename]  
DXCap.exe –v [–file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe –info  
```  
  
#### <a name="parameters"></a>Parametry  
 `-file``filename`  
 V části režim zachycení (`-c`), `filename` Určuje název, který informace grafiky se zaznamenají do souboru protokolu grafiky. Pokud `filename` není zadán, informace grafiky se zaznamenají do souboru s názvem `<appname>-<date>-<time>.vsglog` ve výchozím nastavení.  
  
 V části ověření (-v) režimu `filename` Určuje název souboru protokolu grafiky má být ověřen. Pokud `filename` není zadán, je znovu použít protokol grafiky, která byla naposledy ověřena.  
  
 `-frame``frames`  
 V části režim zachycení `frames` určuje počet snímků, které chcete zaznamenat. První snímek je 1. Můžete zadat více snímků s použitím čárky a rozsahy adres. Například pokud `frames` je `2, 5, 7-9, 15`, pak snímků `2`, `5`, `7`, `8`, `9`, a `15` jsou zachyceny.  
  
 `-period``periods`  
 V části režim zachycení `periods` určuje rozsahy dobu v sekundách, během kterých chcete zachytávat snímky. Můžete zadat několik teček s použitím čárky a rozsahy adres. Například pokud `periods` je `2.1-5, 7.0-9.3`, pak snímků, které jsou generovány mezi `2.1` a `5` sekund a mezi`7` a `9.3` se zaznamenají sekundy.  
  
 `-manual`  
 V části režim zachycení `-manual` Určuje, že snímky budou zachyceny ručně pomocí klávesy Print Screen. Snímky se dají zachytit při spuštění aplikace; Zastavit zachytávání snímků, vraťte se do rozhraní příkazového řádku a stiskněte klávesu enter.  
  
 `-c` `app` [`args...`]  
 Režim zachycení. V části režim zachycení `app` Určuje název aplikace, kterou chcete zachytit informace grafiky z; `args...` Určuje další parametry příkazového řádku do této aplikace.  
  
 `-p` [`filename`]  
 Přehrávání režimu (`-p`). V režimu přehrávání `filename` Určuje název souboru protokolu grafiky dají přehrávat. Pokud `filename` není zadán, protokol grafiky, který byl naposledy přehrát je znovu použít.  
  
 `-debug`  
 V režimu přehrávání `-debug` určuje by se měla provést přehrávání s povolenu vrstvu ladění Direct3D.  
  
 `-warp`  
 V režimu přehrávání `-warp` určuje přehrávání se provádí pomocí zobrazovací jednotky softwaru WARP.  
  
 `-hw`  
 V režimu přehrávání `-hw` určuje přehrávání se provádí pomocí hardwarové GPU.  
  
 `-config`  
 V režimu přehrávání `-config` zobrazí informace o počítači, který byl použit k zachycení souboru protokolu grafiky, pokud tyto informace se zaznamenávají do protokolu.  
  
 `-rawmode`  
 V režimu přehrávání `-rawmode` určuje přehrávání by provádět bez nutnosti upravovat zaznamenané události. V rámci normálního provozu režimu přehrávání může být mírně přehrávání pro zjednodušení, ladění a zrychlit přehrávání. Například může simulovat výstupní řetězec přepnutí namísto provádění příkazů řetězce přepnutí. Obvykle to není problém, ale může být nutné přehrávání vyskytuje v tak, aby více věrnou k zaznamenané události; Například můžete použít tuto možnost k obnovení chování vykreslování celé obrazovky do aplikace, která se zaznamenala při spuštění v režimu celé obrazovky.  
  
 `-toXML` [`xml_filename`]  
 V režimu přehrávání `xml_filename` Určuje název souboru, ve kterém reprezentaci XML pro přehrávání je zapsán do. Pokud `xml_filename` není zadán, reprezentaci XML je zapsána do souboru s názvem stejný jako soubor se přehrát, ale vzhledem `.xml` rozšíření.  
  
 `-v`  
 Režim ověřování. V režimu ověřování zachycené snímky jsou přehrávat na hardware a Warp je hodnota a jejich výsledky jsou porovnány pomocí funkce porovnání obrázku. Tuto funkci můžete rychle identifikovat problémy s ovladači, které ovlivňují váš vykreslování.  
  
 `-examine``events`  
 V režimu ověřování `events` určuje sadu událostí grafiky jsou porovnány jejichž okamžitou výsledky. Například `-examine present,draw,copy,clear` omezuje porovnávání pouze události, které patří do těchto kategorií.  
  
> [!TIP]
>  Doporučujeme začít se `-examine present,draw,copy,clear` vzhledem k tomu, že to bude odhalit většinu problémů, ale trvá mnohem kratší dobu než rozsáhlejší sadu událostí. V případě potřeby můžete zadat větší nebo jinou sadu událostí můžete ověřovat tyto události a odhalit další druhy problémů.  
  
 `-haltonfail`  
 V režimu ověřování `-haltonfail` zastaví ověření, když se zjistí rozdíly mezi hardwarem a WARP renderer. Ověření se obnoví po stisknutí klávesy.  
  
 `-exitonfail`  
 V režimu ověřování `-exitonfail` ukončí ověření hned při zjištění rozdíly mezi hardwarem a WARP renderer. Při ukončení programu tímto způsobem, vrátí `0` prostředí; v opačném případě vrátí `1`.  
  
 `-showprogress`  
 V režimu ověřování `-showprogress` zobrazuje informace o průběhu relace ověřování. Zobrazí se průběh WARP na levé straně; Zobrazí se průběh hardwaru na pravé straně.  
  
 `-e``search_string`  
 Vytvoří výčet aplikace Windows Store, které jsou nainstalovány. Tyto informace můžete použít k provedení příkazového řádku zachycení s aplikacemi pro Windows Store.  
  
 `-info`  
 Zobrazí informace o knihovnách DLL počítače a zachycení.  
  
## <a name="remarks"></a>Poznámky  
 DXCap.exe funguje v tří režimů:  
  
 Režim zachycení (-c)  
 Zachytit informace grafiky z běžící aplikaci a uložte ho do souboru protokolu grafiky. Možnosti zachytávání a formát souboru jsou stejné jako sady Visual Studio.  
  
 Přehrávání režimu (-p)  
 Přehrávání událostí grafiky dříve zaznamenaný z existujícího souboru protokolu grafiky. Ve výchozím nastavení v okně, dojde k přehrávání i v případě protokolu grafiky souboru byla zaznamenána aplikace na celé obrazovce. Pouze při protokolu grafiky souboru byla zaznamenána celá obrazovka aplikace, dojde k přehrávání v celé obrazovky a `–rawmode` určena.  
  
 Režim ověřování (`-v`)  
 Ověří chování vykreslování tak, že přehrávání zachycených snímků na hardware a Warp je hodnota, pak jejich výsledky porovnání funkcí porovnání bitové kopie. Tuto funkci můžete rychle identifikovat problémy s ovladači, které ovlivňují váš vykreslování.  
  
 Kromě těchto režimech dxcap.exe provádí dvě další funkce, které neprovádějte zachytávání a přehrávání grafické informace.  
  
 Funkci výčtu (`-e`)  
 Zobrazí podrobnosti o aplikacích Windows Store, které jsou nainstalované na počítači. Mezi tyto podrobnosti patří název balíčku a ID aplikace, které identifikují spustitelný soubor v aplikaci Windows Store. Zachytit informace grafiky z aplikace pro windows store pomocí DXCap.exe, použijte název balíčku a ID aplikace namísto názvu spustitelného souboru, který se používá při zaznamenávání desktopové aplikace.  
  
 (Informace o funkci`-info)`  
 Zobrazí podrobnosti o počítači a zachycení knihovny DLL.  
  
## <a name="examples"></a>Příklady  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Zachytit informace grafiky z desktopové aplikace  
 Použití `–c` zadat aplikaci, ze kterého chcete zachytit informace grafiky.  
  
```ms-dos  
DXCap.exe –c BasicHLSL11.exe  
```  
  
 Ve výchozím nastavení, informace grafiky se zaznamenají do souboru s názvem `<appname>-<date>-<time>.vsglog`. Použití `–file` a vybrat jiný soubor chcete nahrát.  
  
```ms-dos  
DXCap.exe –file regression_test_12.vsglog –c BasicHLSL11.exe  
```  
  
 Zadejte další parametry příkazového řádku pro aplikaci, kterou právě zachycujete z včetně po název souboru aplikace.  
  
```ms-dos  
DXCap.exe –c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 Příkaz v předchozím příkladu jsou zaznamenány informace grafiky z desktopové verzi Internet Exploreru při zobrazení webové stránky v www.fishgl.com využívající rozhraní API WebGL k vykreslení 3D obsahu.  
  
> [!NOTE]
>  Protože k němu jsou předány argumenty příkazového řádku, které se zobrazí po aplikaci, je nutné zadat argumenty, které jsou určené pro DXCap.exe před použitím `–c` možnost.  
  
### <a name="capture-graphics-information-from-a-windows-store-app"></a>Zachytit informace grafiky z aplikace pro Windows Store.  
 Můžete zachytit informace grafiky z aplikace pro Windows Store.  
  
```ms-dos  
DXCap.exe –c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 Použití DXCap.exe zaznamenat z aplikace pro Windows Store je podobný používání má zaznamenat z aplikace klasické pracovní plochy Windows, ale aplikace klasické pracovní plochy místo identifikace podle názvu souboru, identifikovat aplikace Windows Store v jazyce podle svého balíčku název a název nebo ID spustitelný soubor uvnitř daného balíčku stáří, který chcete zaznamenat z. Aby bylo snazší zjistit, jak identifikovat aplikace Windows Store, které jsou nainstalované na počítači, použijte `–e` parametrem DXCap.exe výčet je:  
  
```ms-dos  
DXCap.exe -e  
```  
  
 Můžete zadat volitelné hledaný řetězec pro vám pomůže najít aplikaci, kterou hledáte. Pokud je k dispozici hledaný řetězec, zobrazí DXCap.exe aplikace Windows Store, jejíž název balíčku, název aplikace nebo ID aplikace odpovídaly hledaný řetězec. Hledání nerozlišuje velká a malá písmena.  
  
```ms-dos  
DXCap.exe –e map  
```  
  
 Výše uvedeného příkazu zobrazí aplikace Windows Store, které odpovídají "mapy"; Zde je výstup:  
  
 **Balíček "Microsoft.BingMaps":**  
 **InstallDirectory: Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe C:\Program**  
 **Jméno a příjmení: Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID          : S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Název: Microsoft.BingMaps**  
 **Vydavatel: CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S = Washington, C = US**  
 **Verze: 2.1.2914.1734**  
 **Spustitelná aplikace:**  
 **ID: AppexMaps**  
 **Exe  : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA: Ne**  
 **AppSpec (ke spuštění): DXCap.exe - c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps** poslední řádek výstupu u každé Výčtový aplikace zobrazí příkaz vám umožní zachytit informace grafiky z něj.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Zaznamenávejte určité snímky nebo snímků mezi určitou dobu.  
 Použití `–frame` zadat počet snímků, které chcete zaznamenat pomocí čárky a rozsahy adres:  
  
```ms-dos  
DXCap.exe –frame 2,5,7-9,15 –c SimpleBezier11.exe  
```  
  
 Nebo použijte `–period` určit sadu časových rozsahů, během které k zachycení snímků. Časových rozsahů se zadávají v sekundách a více rozsahů je možné zadat:  
  
```ms-dos  
DXCap.exe –period 2.1-5, 7.0-9.3 –c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Interaktivní zachytávání snímků.  
 Použití `–manual` k zachycení snímků interaktivně. Stisknutím klávesy Enter se spustit zachytávání a stisknutím klávesy Enter akci k zastavení.  
  
```ms-dos  
DXCap.exe –manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphics-log-file"></a>Přehrávání souboru protokolu grafiky  
 Použití `-p` k přehrání dříve zaznamenaný grafického souboru protokolu.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog  
```  
  
 Nechte si název souboru k přehrání protokolu grafiky, která se zaznamenala jako poslední.  
  
```ms-dos  
DXCap.exe –p  
```  
  
### <a name="play-back-in-raw-mode"></a>Přehrání v nezpracovaných režimu  
 Použití `-rawmode` Chcete-li přehrát zaznamenané příkazy přesně tak, jak k nim došlo. V části Normální přehrávání určité příkazy jsou emulované, například soubor protokolu grafiky zachycených při zobrazení na celé obrazovce aplikace bude přehrávat v okně; s povoleným režimem nezpracovaná se pokusí stejný soubor přehrávat v zobrazení na celé obrazovce.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>Přehrát zpět pomocí WARP nebo hardwarového zařízení  
 Můžete chtít vynutit přehrát zadní soubor protokolu grafiky zaznamenaná v zařízení používat WARP, nebo vynutit přehrávání protokolů zachycené v použití hardwarového zařízení WARP. Použití `-warp` přehrávání zpět pomocí WARP.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -warp  
```  
  
 Použití `-hw` přehrávání zpět pomocí hardwaru.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Ověřit soubor protokolu grafiky proti WARP  
 V režimu ověřování soubor protokolu grafiky je přehrávat na hardware a Warp je hodnota a jejich výsledky porovnání. To může pomoct identifikovat chyb při vykreslování způsobených ovladače. – V slouží k ověření správné chování hardwarovou akceleraci proti WARP.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Ke snížení množství porovnávání, můžete zadat podmnožinu příkazů pro ověření pro porovnání a dalších příkazů, které se bude ignorovat. Použít – prozkoumejte zadat příkazy, jejichž výsledky chcete porovnat.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog –examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Převést soubor protokolu grafiky na formát PNG  
 K zobrazení nebo analýza snímků ze souboru protokolu grafiky, DXCap.exe můžete uložit zachycené snímky jako ve formátu PNG (Portable Network Graphics) soubory obrázků. Použití `-screenshot` k v režimu přehrávání na výstup zachycených snímků jako soubory ve formátu PNG.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 Použití `–frame` s `–screenshot` zadat počet snímků, které chcete do výstupu.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot –frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Převést na XML soubor protokolu grafiky  
 Chcete-li zpracovávat a analyzovat protokoly grafiky pomocí známých nástrojů, jako je FindStr nebo XSLT, DXCap.exe převést soubor protokolu grafiky do formátu XML. Použití `-toXML` v režimu přehrávání převést protokolu XML namísto přehrání ji zpět.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML  
```  
  
 Ve výchozím nastavení výstup XML je zapsán do souboru se stejným názvem jako protokol grafiky, ale které bylo přiděleno příponu .xml. V předchozím příkladu bude mít název souboru XML **regression_test_12.xml**. Zadejte jiný název souboru XML, zadejte ho po `-toXML`.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML temp.xml  
```  
  
 Výsledný soubor bude obsahovat soubor XML, který bude vypadat nějak takto:  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## <a name="requirements"></a>Požadavky



