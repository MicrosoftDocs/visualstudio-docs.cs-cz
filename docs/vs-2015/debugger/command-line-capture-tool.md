---
title: Nástroj příkazového řádku pro zachycení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 208ff7f9bbfc2d07669a8b485edffc8dfc4cd54f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64810011"
---
# <a name="command-line-capture-tool"></a>Nástroj příkazového řádku pro zachytávání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DXCap.exe je nástroj příkazového řádku pro zachytávání a přehrávání grafiky diagnostiky. Podporuje Direct3D 10 přes Direct3D 12 na všech úrovních funkcí.  
  
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
 `-file` `filename`  
 V části režim digitalizace ( `-c` ) `filename` Určuje název souboru protokolu grafiky, na který jsou informace o grafikech zaznamenávány. Pokud `filename` parametr není zadán, budou informace o grafice zaznamenávány do souboru s názvem `<appname>-<date>-<time>.vsglog` ve výchozím nastavení.  
  
 V části režim ověřování (-v) `filename` Určuje název souboru protokolu grafiky, který se má ověřit. Pokud `filename` parametr není zadán, bude znovu použit protokol grafiky, který byl naposledy ověřen.  
  
 `-frame` `frames`  
 V části režim sběru `frames` Určuje snímky, které chcete zachytit. První snímek je 1. Můžete zadat více snímků pomocí čárky a rozsahů. Například pokud `frames` je `2, 5, 7-9, 15` , pak `2` `5` `7` `8` `9` `15` jsou zachyceny snímky,,,,, a.  
  
 `-period` `periods`  
 V části režim zachycení `periods` určuje rozsahy času (v sekundách), během kterých chcete zachytit snímky. Můžete zadat více teček pomocí čárky a rozsahů. Například pokud `periods` je `2.1-5, 7.0-9.3` , pak jsou zachyceny rámce, které jsou vykresleny mezi `2.1` a `5` sekundami a mezi `7` a `9.3` sekundami.  
  
 `-manual`  
 V části režim sběru `-manual` určíte, že se snímky budou zachytávat ručně stisknutím klávesy PRINT SCREEN. Snímky lze zachytit při spuštění aplikace; Chcete-li zastavit zachytávání snímků, vraťte se do rozhraní příkazového řádku a stiskněte klávesu ENTER.  
  
 `-c` `app` [`args...`]  
 Režim zachycení. V části režim zachycení `app` Určuje název aplikace, ze které chcete zachytit informace grafiky; `args...` Určuje další parametry příkazového řádku pro tuto aplikaci.  
  
 `-p` [`filename`]  
 Režim přehrávání ( `-p` ). V části režim přehrávání `filename` Určuje název souboru protokolu grafiky, který se má přehrát. Pokud `filename` parametr není zadán, bude znovu použit protokol grafiky, který se naposledy nahrává zpět.  
  
 `-debug`  
 V části režim přehrávání `-debug` Určuje, zda má být přehrávání provedeno s povolenou vrstvou ladění Direct3D.  
  
 `-warp`  
 V části režim přehrávání `-warp` Určuje, zda má být přehrávání provedeno pomocí nástroje pro vykreslování softwaru na křivce.  
  
 `-hw`  
 V části režim přehrávání `-hw` Určuje, zda má být přehrávání provedeno pomocí hardwaru GPU.  
  
 `-config`  
 V části režim přehrávání `-config` zobrazí informace o počítači, který se použil k zachycení souboru protokolu grafiky, pokud se tyto informace nahrály do protokolu.  
  
 `-rawmode`  
 V části režim přehrávání `-rawmode` Určuje, zda má být přehrávání provedeno bez úprav zaznamenaných událostí. V rámci normálního provozu může režim přehrávání udělat drobné změny v přehrávání, aby se zjednodušilo ladění a urychlilo přehrávání. Například může simulovat výstup řetězce přepnutí místo provádění příkazů přepnutí řetězu. Obvykle se nejedná o problém, ale může být potřeba, abyste přehrávání provedli způsobem, který je pro zaznamenané události přesnější. tuto možnost můžete například použít k obnovení chování vykreslování na celé obrazovce do aplikace, která byla zachycena při spuštění v režimu celé obrazovky.  
  
 `-toXML` [`xml_filename`]  
 V části režim přehrávání `xml_filename` Určuje název souboru, do kterého je zapsána reprezentace XML přehrávání. Pokud `xml_filename` parametr není zadán, reprezentace XML je zapsána do souboru s názvem stejným jako soubor, který je přehráván zpět, ale předává `.xml` příponu.  
  
 `-v`  
 Režim ověřování. V režimu ověřování se zachycené snímky přehrávají na hardware i v KŘIVce a jejich výsledky se porovnávají pomocí funkce porovnání obrázků. Pomocí této funkce můžete rychle identifikovat problémy s ovladači, které mají vliv na vykreslování.  
  
 `-examine` `events`  
 V části režim ověřování `events` Určuje sadu grafických událostí, jejichž okamžité výsledky jsou porovnávány. Například `-examine present,draw,copy,clear` omezí porovnání jenom na události patřící do těchto kategorií.  
  
> [!TIP]
> Doporučujeme začít s, `-examine present,draw,copy,clear` protože se tím odhalí většinu problémů, ale bude trvat mnohem méně času než širší sada událostí. V případě potřeby můžete zadat větší nebo jinou sadu událostí a ověřit tak tyto události a odhalit další typy problémů.  
  
 `-haltonfail`  
 V části režim ověřování `-haltonfail` zastaví ověřování, pokud jsou zjištěny rozdíly mezi hardwarem a zobrazovacím osnovou. Po stisknutí klávesy se ověřování obnoví.  
  
 `-exitonfail`  
 V režimu ověřování `-exitonfail` ukončí nástroj okamžitě ověřování, pokud jsou zjištěny rozdíly mezi hardwarem a zobrazovacím osnovou. Když se program ukončí tímto způsobem, vrátí se `0` do prostředí; v opačném případě vrátí `1` .  
  
 `-showprogress`  
 V části režim ověřování se `-showprogress` zobrazí informace o průběhu relace ověření. Na levé straně se zobrazí průběh pokřivení. na pravé straně se zobrazí průběh hardwaru.  
  
 `-e` `search_string`  
 Vytvoří výčet nainstalovaných aplikací pro Windows Store. Tyto informace můžete použít k provádění zachycení příkazového řádku s aplikacemi pro Windows Store.  
  
 `-info`  
 Zobrazí informace o počítači a knihovně DLL pro zachycení.  
  
## <a name="remarks"></a>Poznámky  
 DXCap.exe funguje ve třech režimech:  
  
 Režim zachycení (-c)  
 Zachyťte informace grafiky ze spuštěné aplikace a zaznamenejte je do souboru protokolu grafiky. Možnosti zachycení a formát souboru jsou stejné jako u sady Visual Studio.  
  
 Režim přehrávání (-p)  
 Přehrajte dříve zaznamenané události grafiky z existujícího souboru protokolu grafiky. Ve výchozím nastavení se přehrávání objevuje v okně, i když byl soubor protokolu grafiky zachycen z celoobrazovkového aplikace. Přehrávání probíhá na celé obrazovce pouze v případě, že soubor protokolu grafiky byl zachycen z celoobrazovkového aplikace a `–rawmode` je určen.  
  
 Režim ověřování ( `-v` )  
 Ověří chování vykreslování přehráním zachycených snímků na hardwaru i v KŘIVce a pak porovná jejich výsledky pomocí funkce porovnání obrázků. Pomocí této funkce můžete rychle identifikovat problémy s ovladači, které mají vliv na vykreslování.  
  
 Kromě těchto režimů dxcap.exe provádí dvě další funkce, které neprovádějí zachytávání nebo přehrávání informací grafiky.  
  
 Funkce výčtu ( `-e` )  
 Zobrazí podrobnosti o aplikacích pro Windows Store, které jsou nainstalovány v počítači. Mezi tyto podrobnosti patří název balíčku a AppID, které identifikují spustitelný soubor v aplikaci pro Windows Store. K zachycení informací grafiky z aplikace pro Windows Store pomocí DXCap.exe použijte název balíčku a AppID místo spustitelného souboru, který se používá při zachycení desktopové aplikace.  
  
 Info – funkce (`-info)`  
 Zobrazí podrobnosti o počítači a knihovně DLL pro zachycení.  
  
## <a name="examples"></a>Příklady  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Zachytit informace grafiky z desktopové aplikace  
 Použijte `–c` k určení aplikace, ze které chcete zachytit informace grafiky.  
  
```ms-dos  
DXCap.exe –c BasicHLSL11.exe  
```  
  
 Ve výchozím nastavení jsou informace o grafice zaznamenávány do souboru s názvem `<appname>-<date>-<time>.vsglog` . Použijte `–file` k určení jiného souboru pro nahrání.  
  
```ms-dos  
DXCap.exe –file regression_test_12.vsglog –c BasicHLSL11.exe  
```  
  
 Zadejte další parametry příkazového řádku pro aplikaci, ze které zachytíte, zahrnutím těchto souborů za název souboru aplikace.  
  
```ms-dos  
DXCap.exe –c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 Příkaz v předchozím příkladu zachycuje informace grafiky z desktopové verze Internet Exploreru při prohlížení webové stránky umístěné na www.fishgl.com, která používá rozhraní WebGL API k vykreslování 3D obsahu.  
  
> [!NOTE]
> Vzhledem k tomu, že argumenty příkazového řádku, které se zobrazí po předání aplikace do ní, je nutné před použitím možnosti zadat argumenty určené pro DXCap.exe `–c` .  
  
### <a name="capture-graphics-information-from-a-windows-store-app"></a>Zachyťte informace grafiky z aplikace pro Windows Store.  
 Můžete zachytit informace grafiky z aplikace pro Windows Store.  
  
```ms-dos  
DXCap.exe –c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 Použití DXCap.exe k zachycení z aplikace pro Windows Store je podobné jako při zachycení z desktopové aplikace pro Windows, ale místo toho identifikuje desktopovou aplikaci podle názvu souboru, identifikujete aplikaci pro Windows Store podle názvu balíčku a názvu nebo ID spustitelného souboru uvnitř tohoto balíčku, ze kterého chcete zachytit. Pro snazší zjištění, jak identifikovat aplikace pro Windows Store, které jsou nainstalované na vašem počítači, použijte `–e` možnost s DXCap.exe pro jejich výčet:  
  
```ms-dos  
DXCap.exe -e  
```  
  
 Můžete zadat volitelný hledaný řetězec, který vám umožní najít aplikaci, kterou hledáte. Když je zadán hledaný řetězec, DXCap.exe vytvoří výčet aplikací pro Windows Store, jejichž název balíčku, název aplikace nebo ID aplikace odpovídají hledanému řetězci. Při hledání se nerozlišují malá a velká písmena.  
  
```ms-dos  
DXCap.exe –e map  
```  
  
 Výše uvedený příkaz vytvoří výčet aplikací pro Windows Store, které odpovídají mapě. Zde je výstup:  
  
 **Balíček Microsoft. BingMaps:**  
 **InstallDirectory: C:\Program Files\WindowsApps\Microsoft. BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **FullName: Microsoft. BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID          : S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Název: Microsoft. BingMaps**  
 **Vydavatel: CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S = Washington, C = US**  
 **Verze: 2.1.2914.1734**  
 **Spouštěné aplikace:**  
 **ID: AppexMaps**  
 **Exe  : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA: ne**  
 **AppSpec (pro spuštění): DXCap.exe-c Microsoft. BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe, AppexMaps** Poslední řádek výstupu pro každou aplikaci s výčtem zobrazí příkaz, který můžete použít k zachycení informací grafiky z ní.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Zachyťte určité snímky nebo snímky mezi určitými časy.  
 Použijte `–frame` k určení snímků, které chcete zachytit pomocí čárky a rozsahů:  
  
```ms-dos  
DXCap.exe –frame 2,5,7-9,15 –c SimpleBezier11.exe  
```  
  
 Nebo můžete použít `–period` k určení sady časových rozsahů, během kterých chcete zachytit snímky. Časové rozsahy jsou zadány v sekundách a lze zadat více rozsahů:  
  
```ms-dos  
DXCap.exe –period 2.1-5, 7.0-9.3 –c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Zachytit snímky interaktivně  
 Použijte `–manual` k interaktivnímu zachycení snímků. Stiskněte klávesu ENTER a zahajte zachytávání a stisknutím klávesy ENTER zastavte.  
  
```ms-dos  
DXCap.exe –manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphics-log-file"></a>Přehrání souboru protokolu grafiky  
 Slouží `-p` k přehrání dříve zaznamenaného souboru protokolu grafiky.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog  
```  
  
 Ponechte název souboru a přehrajte si protokol grafiky, který jste si poznamenali naposledy.  
  
```ms-dos  
DXCap.exe –p  
```  
  
### <a name="play-back-in-raw-mode"></a>Přehrát v nezpracovaném režimu  
 Použijte `-rawmode` k přehrání zachycených příkazů přesně tak, jak k nim došlo. Při normálním přehrávání jsou některé příkazy emulované, například soubor protokolu grafiky zachycený z aplikace na celé obrazovce se přehrává v okně. v případě povoleného nezpracovaného režimu se stejný soubor pokusí přejít zpět na celou obrazovku.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>Přehrání pomocí pokřivení nebo hardwarového zařízení  
 Možná budete chtít vynutit přehrání souboru protokolu grafiky zaznamenaného na hardwarovém zařízení, které bude používat deformaci, nebo vynutit přehrávání protokolu zachyceného v pokřivení, aby používalo hardwarové zařízení. Použijte `-warp` k přehrání pozadí pomocí PŘEkřivení.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -warp  
```  
  
 Používá `-hw` se k přehrání hardwaru.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Ověření souboru protokolu grafiky proti KŘIVce  
 V části režim ověřování se soubor protokolu grafiky přehrává na hardware i v KŘIVce a jejich výsledky jsou porovnávány. To vám může přispět k identifikaci chyb vykreslování, které jsou způsobeny ovladačem. Použijte – v k ověření správného chování grafického hardwaru proti pokřivení.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Chcete-li snížit množství porovnávání, můžete zadat podmnožinu příkazů pro porovnání a jiné příkazy budou ignorovány. Use – prověřte a určete příkazy, jejichž výsledky chcete porovnat.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog –examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Převod souboru protokolu grafiky na PNGs  
 Chcete-li zobrazit nebo analyzovat snímky ze souboru protokolu grafiky, DXCap.exe mohou ukládat zachycené snímky jako soubory obrázků. png (Portable Network Graphics). Pro `-screenshot` výstup zachycených snímků do souborů. png použijte v části režim přehrávání.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 Použijte `–frame` s `–screenshot` k určení snímků, které chcete výstupem.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot –frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Převod souboru protokolu grafiky na XML  
 Pro zpracování a analýzu grafických protokolů pomocí známých nástrojů, jako je například FindStr nebo XSLT, může DXCap.exe převést soubor protokolu grafiky do formátu XML. `-toXML`V části režim přehrávání převeďte protokol do formátu XML místo jeho opětovného přehrání.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML  
```  
  
 Ve výchozím nastavení je výstup XML zapsán do souboru se stejným názvem, jako má protokol grafiky, ale má příponu. XML. V předchozím příkladu bude soubor XML pojmenován **regression_test_12.xml**. Chcete-li zadat jiný název souboru XML, zadejte jej po `-toXML` .  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML temp.xml  
```  
  
 Výsledný soubor bude obsahovat kód XML, který bude vypadat nějak takto:  
  
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
