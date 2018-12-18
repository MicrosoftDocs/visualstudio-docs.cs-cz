---
title: Idiasession – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2baa4b026fd9856625ce25be283c2c969f79a99
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799623"
---
# <a name="idiasession"></a>IDiaSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poskytuje kontext dotazu pro symboly ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 V následující tabulce jsou uvedeny metody objektu `IDiaSession`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Načte adresu zatížení pro spustitelný soubor, který odpovídá symboly v tomto úložišti symbolů. Jedná se o stejnou hodnotu, která byla předána `put_loadAddress` metody.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Nastaví adresu zatížení pro spustitelný soubor, který odpovídá na symboly v tomto úložišti symbolů. **Poznámka:** je potřeba volat tuto metodu, když dojde `IDiaSession` objektu a před zahájením používání objektu.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Získá odkaz na globální obor.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Získá enumerátor pro všechny tabulky, které jsou obsaženy v úložišti symbolů.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Získá enumerátor pro všechny pojmenované symboly ve statické umístěních.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Načte všechny podřízené objekty zadaný nadřazený identifikátor odpovídající název a značka typu.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Načte typ zadaný symbol, který obsahuje, nebo co nejblíže k zadané adrese.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Načte typ zadaný symbol, který obsahuje, nebo co nejblíže k zadané relativní virtuální adrese (RVA).|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Načte typ zadaný symbol, který obsahuje, nebo je nejblíže zadanou virtuální adresu (VA).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Načte symbol, který obsahuje token Zadaná metadata.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Kontroluje, jestli dva symboly jsou ekvivalentní.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Načte symbol podle jejího jedinečného identifikátoru.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Načte typ zadaný symbol, který obsahuje, nebo je nejblíže zadanou relativní virtuální adresu a posun.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Načte typ zadaný symbol, který obsahuje, nebo co nejblíže, zadanou virtuální adresu a posun.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Načte kompilace a název zdrojového souboru.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Zkopíruje zdrojový soubor pomocí identifikátoru zdrojového souboru.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Načte čísla řádků v rámci zadaný identifikátor souboru kompilace a zdroje.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Načte řádky v zadané kompilace, které obsahují zadané adrese.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Načte řádky v zadané kompilace, které obsahují zadaný relativní virtuální adresu.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Vyhledá informace o čísle řádku pro řádky, které jsou součástí zadaného rozsahu adres.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Načte řádky v zadané kompilace pomocí zdrojového souboru a číslo řádku.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Získá zdroj, který je umístěný do úložiště symbolů podle poskytovatele atributu ani jiné součásti procesu kompilace.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Načte Výčtový posloupnost ladění datových proudů.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Načte výčet, který umožňuje klientovi iterovat přes všechny vložené rámce na dané adrese.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Načte výčet, který umožňuje klientovi iterovat přes všechny vložené rámce na zadaný relativní virtuální adrese (RVA).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Načte výčet, který umožňuje klientovi iterovat přes všechny vložené rámce na zadanou virtuální adresu (VA).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Načte výčet, který umožňuje klientovi k iteraci v rámci o počtu řádků všech funkcí, které jsou vloženy, přímo nebo nepřímo, symbolem zadaný nadřazený prvek.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Načte výčet, který umožňuje klientovi k iteraci v rámci o počtu řádků všech funkcí, které jsou vloženy, přímo nebo nepřímo, symbolem zadaný nadřazený prvek a jsou obsaženy v rámci zadaný rozsah adres.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Načte výčet, který umožňuje klientovi k iteraci v rámci o počtu řádků všech funkcí, které jsou vloženy, přímo nebo nepřímo, symbolem zadaný nadřazený prvek a jsou obsaženy v rámci zadaného relativní virtuální adresu (RVA).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Načte výčet, který umožňuje klientovi k iteraci v rámci o počtu řádků všech funkcí, které jsou vloženy, přímo nebo nepřímo, symbolem zadaný nadřazený prvek a jsou obsaženy v rámci zadané virtuální adresy (VA).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Načte výčet, který umožňuje klientovi k iteraci v rámci informace o číslech řádků všech funkcí, které jsou vloženy, přímo nebo nepřímo v zadaný zdrojový soubor a číslo řádku.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Načte výčet, který umožňuje klientovi k iteraci v rámci informace o číslech řádků všech vložených funkcí, které odpovídají zadaným názvem.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Vrátí výčet symboly proměnné, která odpovídá hodnotě zadané značky v nadřazeném prvku. funkce se zakázaným inzerováním akcelerátoru.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Odpovídající hodnota značky zadány, tato metoda vrátí výčet symboly, které jsou obsaženy ve funkci se zakázaným inzerováním akcelerátor zadaný nadřazený prvek na zadaný relativní virtuální adrese.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Vrátí výčet symbolů pro vložené rámce odpovídající názvu funkce zadány jako vložené.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Vrátí výčet symboly pro vložené rámce, které odpovídají zadaným zdrojovým umístěním.|  
  
## <a name="remarks"></a>Poznámky  
 Je potřeba volat [idiasession::put_loadaddress –](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metoda po vytvoření `IDiaSession` objektu – a hodnota předaná `put_loadAddress` metoda musí být nenulové – pro všechny virtuální adresy (VA) vlastnosti symboly, které budou přístupné. Adresa zatížení pochází z libovolné aplikace načíst laděnému spustitelnému souboru. Například můžete volat funkci Win32 `GetModuleInformation` načíst adresu zatížení pro spustitelný soubor, Zadaný popisovač ke spustitelnému souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak získat `IDiaSession` rozhraní jako součást obecné inicializace DIA SDK.  
  
```cpp#  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Dia2.h  
  
 Knihovna: diaguids.lib  
  
 Knihovny DLL: msdia80.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Přehled](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [soubor EXE](../../debugger/debug-interface-access/exe.md)   
 [Idiaaddressmap –](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiadatasource –](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::opensession –](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymbol::findchildren –](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Dotazování na soubor .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)



