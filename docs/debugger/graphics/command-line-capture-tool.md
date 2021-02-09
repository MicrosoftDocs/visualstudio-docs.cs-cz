---
title: Nástroj pro zachycení Command-Line | Microsoft Docs
description: Přečtěte si o DXCap.exe, nástroji příkazového řádku pro zachytávání a přehrávání grafiky, které podporuje Direct3D 10 přes Direct3D 12 na všech úrovních funkcí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ee7acfd6256affee7a8204c2e70e18210c5f3dcf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877730"
---
# <a name="command-line-capture-tool"></a>Nástroj příkazového řádku pro zachytávání
DXCap.exe je nástroj příkazového řádku pro zachytávání a přehrávání grafiky diagnostiky. Podporuje Direct3D 10 přes Direct3D 12 na všech úrovních funkcí.

## <a name="syntax"></a>Syntaxe

```cmd
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]
DXCap.exe -p [filename] -screenshot [-frame frames]
DXCap.exe -p [filename] -toXML [xml_filename]
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]
DXCap.exe -e [search_string]
DXCap.exe -info
```

#### <a name="parameters"></a>Parametry
 `-file``filename`V části režim digitalizace ( `-c` ) `filename` Určuje název souboru protokolu grafiky, na který jsou informace o grafikech zaznamenávány. Pokud `filename` není zadaný, do souboru s názvem ve výchozím nastavení se zaznamenávají informace o grafice `<appname>-<date>-<time>.vsglog` .

 V části režim ověřování (-v) `filename` Určuje název souboru protokolu grafiky, který se má ověřit. Pokud `filename` není zadaný, použije se znovu protokol grafiky, který byl naposledy ověřen.

 `-frame``frames`V části režim sběru `frames` Určuje snímky, které chcete zachytit. První snímek je 1. Můžete zadat několik snímků pomocí čárky a rozsahů. Například pokud `frames` je `2, 5, 7-9, 15` , pak `2` `5` `7` `8` `9` `15` jsou zachyceny snímky,,,,, a.

> [!TIP]
> Použijte `-frame` `manual` k určení, že se snímky budou zachytávat ručně stisknutím klávesy PRINT SCREEN. Snímky lze zachytit při spuštění aplikace; Chcete-li zastavit zachytávání snímků, vraťte se do rozhraní příkazového řádku a stiskněte klávesu ENTER.

 `-period``periods`V části režim zachycení `periods` určuje rozsahy času (v sekundách), během kterých chcete zachytit snímky. Můžete zadat několik teček pomocí čárky a rozsahů. Například pokud `periods` je `2.1-5, 7.0-9.3` , pak jsou zachyceny rámce, které jsou vykresleny mezi `2.1` a `5` sekundami a mezi `7` a `9.3` sekundami.

 `-c``app`[ `args...` ] Režim zachycení. V části režim zachycení `app` Určuje název aplikace, ze které chcete zachytit informace grafiky; `args...` Určuje další parametry příkazového řádku pro tuto aplikaci.

 `-p` [ `filename` ] Režim přehrávání ( `-p` ). V části režim přehrávání `filename` Určuje název souboru protokolu grafiky, který se má přehrát. Pokud `filename` není zadaný, použije se znovu protokol grafiky, který se naposledy nahrává zpátky.

 `-debug` V části režim přehrávání `-debug` Určuje, zda má být přehrávání přehráno s povolenou vrstvou ladění Direct3D.

 `-warp` V části režim přehrávání `-warp` Určuje, zda má být přehrávání přehráno pomocí nástroje pro vykreslování softwaru na křivce.

 `-hw` V části režim přehrávání `-hw` Určuje, že přehrávání má být přehráváno pomocí hardwaru GPU.

 `-config` V části režim přehrávání `-config` zobrazí všechny informace o počítači, který se použil k zachycení souboru protokolu grafiky.

 `-rawmode` V části režim přehrávání `-rawmode` Určuje, zda má být přehrávání provedeno bez úprav zaznamenaných událostí. V rámci normálního provozu může režim přehrávání udělat drobné změny v přehrávání, aby se zjednodušilo ladění a urychlilo přehrávání. Například může simulovat výstup řetězce přepnutí místo provádění příkazů přepnutí řetězu. Obvykle se nejedná o problém, ale může být potřeba, abyste přehrávání provedli způsobem, který je pro zaznamenanou událost přesnější. Tuto možnost můžete například použít k obnovení chování vykreslování na celé obrazovce do aplikace, která byla zachycena při spuštění v režimu celé obrazovky.

 `-toXML` [ `xml_filename` ] V režimu přehrávání `xml_filename` Určuje název souboru, do kterého se zapisuje reprezentace XML přehrávání. Pokud `xml_filename` parametr není zadán, reprezentace XML je zapsána do souboru s názvem stejným jako soubor, který je přehráván zpět, ale předává `.xml` příponu.

 `-v` Režim ověřování. V režimu ověřování se zachycené snímky přehrávají na hardware i v KŘIVce a jejich výsledky se porovnávají pomocí funkce porovnání obrázků. Pomocí této funkce můžete rychle identifikovat problémy s ovladači, které mají vliv na vykreslování.

 `-examine``events`V části režim ověřování `events` Určuje sadu grafických událostí, jejichž okamžité výsledky jsou porovnávány. Například `-examine present,draw,copy,clear` omezí porovnání jenom na události patřící do těchto kategorií.

> [!TIP]
> Doporučujeme začít s, `-examine present,draw,copy,clear` protože se tím odhalí většinu problémů, ale bude trvat mnohem méně času než širší sada událostí. V případě potřeby můžete zadat větší nebo jinou sadu událostí a ověřit tak tyto události a odhalit další typy problémů.

 `-haltonfail` V části režim ověřování `-haltonfail` zastaví ověřování, pokud jsou zjištěny rozdíly mezi hardwarem a zobrazovacím osnovou. Po stisknutí klávesy se ověřování obnoví.

 `-exitonfail` V režimu ověřování `-exitonfail` ukončí nástroj okamžitě ověřování, pokud jsou zjištěny rozdíly mezi hardwarem a zobrazovacím osnovou. Když se program ukončí tímto způsobem, vrátí se `0` do prostředí; v opačném případě vrátí `1` .

 `-showprogress` V části režim ověřování se `-showprogress` zobrazí informace o průběhu relace ověření. Na levé straně se zobrazí průběh pokřivení. na pravé straně se zobrazí průběh hardwaru.

 `-e``search_string`Vytvoří výčet nainstalovaných aplikací UWP. Tyto informace můžete použít k provádění zachycení příkazového řádku s aplikacemi UWP.

 `-info` Zobrazí informace o počítači a knihovně DLL pro zachycení.

## <a name="remarks"></a>Poznámky
 DXCap.exe funguje ve třech režimech:

 Režim digitalizace (-c) zachytí informace grafiky ze spuštěné aplikace a zaznamená je do souboru protokolu grafiky. Možnosti zachycení a formát souboru jsou stejné jako u sady Visual Studio.

 Režim přehrávání (-p) přehrávání dříve zachycených grafických událostí z existujícího souboru protokolu grafiky. Ve výchozím nastavení se přehrávání objevuje v okně, i když byl soubor protokolu grafiky zachycen z celoobrazovkového aplikace. Přehrávání probíhá na celé obrazovce pouze v případě, že soubor protokolu grafiky byl zachycen z celoobrazovkového aplikace a `-rawmode` je určen.

 Režim ověřování ( `-v` ) ověřuje chování vykreslování tím, že přehrává zachycené snímky na hardwaru i v křivce a pak porovnává jejich výsledky pomocí funkce porovnání obrázků. Pomocí této funkce můžete rychle identifikovat problémy s ovladači, které mají vliv na vykreslování.

 Kromě těchto režimů dxcap.exe provádí dvě další funkce, které neprovádějí zachytávání nebo přehrávání informací grafiky.

 Funkce Enumeration ( `-e` ) zobrazí podrobnosti o aplikacích UWP, které jsou nainstalovány v počítači. Mezi tyto podrobnosti patří název balíčku a AppID, které identifikují spustitelný soubor v aplikaci pro UWP. K zachycení informací grafiky z aplikace pro Windows Store pomocí DXCap.exe použijte název balíčku a AppID místo spustitelného souboru, který se používá při zachycení desktopové aplikace.

 Info ( `-info)` zobrazí podrobnosti o počítači a knihovnách DLL pro zachycení.

## <a name="examples"></a>Příklady

### <a name="capture-graphics-information-from-a-desktop-app"></a>Zachytit informace grafiky z desktopové aplikace
 Použijte `-c` k určení aplikace, ze které chcete zachytit informace grafiky.

```cmd
DXCap.exe -c BasicHLSL11.exe
```

 Ve výchozím nastavení jsou informace o grafice zaznamenávány do souboru s názvem `<appname>-<date>-<time>.vsglog` . Použijte `-file` k určení jiného souboru pro nahrání.

```cmd
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe
```

 Zadejte další parametry příkazového řádku pro aplikaci, ze které zachytíte, zahrnutím těchto souborů za název souboru aplikace.

```cmd
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"
```

 Příkaz v předchozím příkladu zachycuje informace grafiky z desktopové verze Internet Exploreru při prohlížení webové stránky umístěné na www.fishgl.com, která používá rozhraní WebGL API k vykreslování 3D obsahu.

> [!NOTE]
> Vzhledem k tomu, že argumenty příkazového řádku, které se zobrazí po předání aplikace do ní, je nutné před použitím možnosti zadat argumenty určené pro DXCap.exe `-c` .

### <a name="capture-graphics-information-from-a-uwp-app"></a>Zachyťte informace grafiky z aplikace pro UWP.
 Můžete zachytit informace grafiky z aplikace pro UWP.

```cmd
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps
```

 Použití DXCap.exe k zachycení z aplikace pro UWP je podobné jako při zachycení z desktopové aplikace pro Windows, ale místo toho identifikuje desktopovou aplikaci podle jejího názvu souboru, určíte aplikaci UWP podle jejího názvu a názvu nebo ID spustitelného souboru uvnitř tohoto balíčku, ze kterého chcete zachytit. K tomu, aby bylo snazší zjistit, jak identifikovat aplikace pro UWP nainstalované na vašem počítači, použijte `-e` možnost s DXCap.exe pro jejich výčet:

```cmd
DXCap.exe -e
```

 Můžete zadat volitelný hledaný řetězec, který vám umožní najít aplikaci, kterou hledáte. Když je zadaný hledaný řetězec, DXCap.exe vytvoří výčet aplikací UWP, jejichž název balíčku, název aplikace nebo ID aplikace odpovídají hledanému řetězci. Při hledání se nerozlišují malá a velká písmena.

```cmd
DXCap.exe -e map
```

 Příkaz výše zobrazuje výčet aplikací pro UWP, které odpovídají mapě. Zde je výstup:

 **Balíček Microsoft. BingMaps ":** **InstallDirectory: C: \ Program Files \ WindowsApps \ Microsoft. BingMaps_2.1.2914.1734_X64__8wekyb3d8bbwe** **FullName: Microsoft. BingMaps_2.1.2914.1734 _x64__8wekyb3d8bbwe** **identifikátor UserSID: S-1-5-21-2127521184-1604012920-1887927527-5603533** **Název: Microsoft. BingMaps** **Publish: CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S = Washington, C = US** **verze: 2.1.2914.1734** **spouštěné aplikace:** **ID: AppexMaps** **exe: C: \ program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe** **IsWWA: No** **AppSpec (ke spuštění): DXCap.exe-C Microsoft. BingMaps_2.1.2914.1734 _x64__8wekyb3d8bbwe, AppexMaps** poslední řádek výstupu pro každou aplikaci zobrazí příkaz, který můžete použít k zaznamenání grafické informace z ní.

### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Zachyťte určité snímky nebo snímky mezi určitými časy.
 Použijte `-frame` k určení snímků, které chcete zachytit pomocí čárky a rozsahů:

```cmd
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe
```

 Nebo můžete použít `-period` k určení sady časových rozsahů, během kterých chcete zachytit snímky. Časové rozsahy jsou zadány v sekundách a lze zadat více rozsahů:

```cmd
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe
```

### <a name="capture-frames-interactively"></a>Zachytit snímky interaktivně
 Použijte `-manual` k interaktivnímu zachycení snímků. Stiskněte klávesu ENTER a zahajte zachytávání a stisknutím klávesy ENTER zastavte.

```cmd
DXCap.exe -manual -c SimpleBezier11.exe
```

### <a name="play-back-a-graphic-log-file"></a>Přehrát soubor protokolu grafiky
 Slouží `-p` k přehrání dříve zaznamenaného souboru protokolu grafiky.

```cmd
DXCap.exe -p regression_test_12.vsglog
```

 Ponechte název souboru a přehrajte si protokol grafiky, který jste si poznamenali naposledy.

```cmd
DXCap.exe -p
```

### <a name="play-back-in-raw-mode"></a>Přehrát v nezpracovaném režimu
 Použijte `-rawmode` k přehrání zachycených příkazů přesně tak, jak k nim došlo. Při normálním přehrávání jsou některé příkazy emulované, například soubor protokolu grafiky zachycený z aplikace na celé obrazovce se přehrává v okně. v případě povoleného nezpracovaného režimu se stejný soubor pokusí přejít zpět na celou obrazovku.

```cmd
DXCap.exe -p regression_test_12.vsglog -rawmode
```

### <a name="play-back-using-warp-or-a-hardware-device"></a>Přehrání pomocí pokřivení nebo hardwarového zařízení
 Možná budete chtít vynutit přehrání souboru protokolu grafiky zaznamenaného na hardwarovém zařízení, které bude používat deformaci, nebo vynutit přehrávání protokolu zachyceného v pokřivení, aby používalo hardwarové zařízení. Použijte `-warp` k přehrání pozadí pomocí PŘEkřivení.

```cmd
DXCap.exe -p regression_test_12.vsglog -warp
```

 Používá `-hw` se k přehrání hardwaru.

```cmd
DXCap.exe -p regression_test_12.vsglog -hw
```

### <a name="validate-a-graphics-log-file-against-warp"></a>Ověření souboru protokolu grafiky proti KŘIVce
 V části režim ověřování se soubor protokolu grafiky přehrává na hardware i v KŘIVce a jejich výsledky jsou porovnávány. To vám může přispět k identifikaci chyb vykreslování, které jsou způsobeny ovladačem. Pomocí-v můžete ověřit správné chování grafického hardwaru proti pokřivení.

```cmd
DXCap.exe -v regression_test_12.vsglog
```

 Chcete-li snížit množství porovnávání, můžete zadat podmnožinu příkazů pro porovnání a jiné příkazy budou ignorovány. Pomocí příkazu-prověřte zadejte příkazy, jejichž výsledky chcete porovnat.

```cmd
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear
```

### <a name="convert-a-graphics-log-file-to-pngs"></a>Převod souboru protokolu grafiky na PNGs
 Chcete-li zobrazit nebo analyzovat snímky ze souboru protokolu grafiky, DXCap.exe mohou ukládat zachycené snímky jako soubory obrázků. png (Portable Network Graphics). Pro `-screenshot` výstup zachycených snímků do souborů. png použijte v části režim přehrávání.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot
```

 Použijte `-frame` s `-screenshot` k určení snímků, které chcete výstupem.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9
```

### <a name="convert-a-graphics-log-file-to-xml"></a>Převod souboru protokolu grafiky na XML
 Pro zpracování a analýzu grafických protokolů pomocí známých nástrojů, jako je například FindStr nebo XSLT, může DXCap.exe převést soubor protokolu grafiky do formátu XML. `-toXML`V části režim přehrávání převeďte protokol do formátu XML místo jeho opětovného přehrání.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML
```

 Ve výchozím nastavení je výstup XML zapsán do souboru se stejným názvem, jako má protokol grafiky, ale má příponu. XML. V předchozím příkladu bude soubor XML pojmenován **regression_test_12.xml**. Chcete-li zadat jiný název souboru XML, zadejte jej po `-toXML` .

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml
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