---
title: Idiasession – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b2791f318a921a25535d5e9a8f17e2c595f1f56
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468330"
---
# <a name="idiasession"></a>IDiaSession
Poskytuje kontext dotazu pro symboly ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Následující tabulka uvádí metody `IDiaSession`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Načte adresu zatížení pro spustitelný soubor, který odpovídá symboly v tomto úložišti symbol. Toto je stejnou hodnotu, která byla předána `put_loadAddress` metoda.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Nastaví adresu zatížení pro spustitelný soubor, který odpovídá na symboly v tomto úložišti symbol. **Poznámka:** je třeba volat tuto metodu, když dojde `IDiaSession` objektu a před zahájením práce objektu.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Získá odkaz na globální obor.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Získá enumerátor pro všechny tabulky obsažené v úložišti symbol.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Získá enumerátor pro všechny pojmenované symboly v statické umístěních.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Načte všechny podřízené objekty zadaný nadřazený identifikátor odpovídající název a symbol typu.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Načte typ zadaný symbol, který obsahuje, nebo je nejblíže k zadaná adresa.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Načte typ zadaný symbol, který obsahuje, nebo je nejblíže k zadaný relativní virtuální adresy (RVA).|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Načte typ zadaný symbol, který obsahuje, nebo je nejblíže k zadané virtuální adresy (VA).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Načte symbol, který obsahuje token Zadaná metadata.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Kontroluje, zda jsou dva symboly ekvivalentní.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Získá symbol svůj jedinečný identifikátor.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Načte typ zadaný symbol, který obsahuje, nebo je nejblíže k posunu a relativní zadanou virtuální adresu.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Načte typ zadaný symbol, který obsahuje, nebo je nejblíže k zadanou virtuální adresu a posun.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Načte kompilace a název zdrojového souboru.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Načte zdrojového souboru pomocí identifikátoru zdrojového souboru.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Načte čísla řádků v rámci zadaný identifikátor souboru kompilace a zdroje.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Načte řádků v zadané kompilace, které obsahují zadaná adresa.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Načte řádků v zadané kompilace, které obsahují zadaný relativní virtuální adresu.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Vyhledá informace o řádku čísle řádků v zadaného rozsahu adres.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Načte řádků v zadané kompilace číslem zdrojový soubor a řádku.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Načte zdroji, který se nachází do úložiště symbolů atribut zprostředkovatelé ani jiné součásti procesu kompilace.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Načte výčtové posloupností ladění datových proudů.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Načte výčet, který umožňuje klientům k iteraci v rámci celé vložené rámce na danou adresu.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Načte výčet, který umožňuje klientům k iteraci v rámci celé vložené rámce zadaný relativní virtuální adresy (RVA).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Načte výčet, který umožňuje klientům k iteraci v rámci celé vložené rámce zadané virtuální adresy (VA).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Načte výčet, který umožňuje klientům k iteraci v rámci informace číslo řádku všech funkcí, které jsou vložená, přímo nebo nepřímo, podle zadaný nadřazený symbolu.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Načte výčet, který umožňuje klientům k iteraci v rámci informace číslo řádku všech funkcí, které jsou vložená, přímo nebo nepřímo, podle symbol zadaný nadřazený a jsou obsaženy v rámci zadaný rozsah adres.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Načte výčet, který umožňuje klientům k iteraci v rámci informace číslo řádku všech funkcí, které jsou vložená, přímo nebo nepřímo, podle symbol zadaný nadřazený a jsou obsaženy v rámci zadaného relativní virtuální adresy (RVA).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Načte výčet, který umožňuje klientům k iteraci v rámci informace číslo řádku všech funkcí, které jsou vložená, přímo nebo nepřímo, podle symbol zadaný nadřazený a jsou obsaženy v rámci zadané virtuální adresy (VA).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Načte výčet, který umožňuje klientům k iteraci v rámci informace o všech funkcí, které jsou vložená, přímo ani nepřímo, počet zadaný zdrojový soubor a řádku číslo řádku.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Načte výčet, který umožňuje klientům k iteraci v rámci řádku informace o čísle všechny vloženou obslužnou funkcí, které odpovídají zadaným názvem.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Vrátí výčet symbolů pro proměnnou, která odpovídá hodnotě zadané značky v nadřazené akcelerátoru se zakázaným inzerováním funkce.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Zadané odpovídající hodnota značky, tato metoda vrátí výčet symboly, které jsou obsaženy ve funkci se zakázaným inzerováním akcelerátoru zadaný nadřazený na zadaný relativní virtuální adresu.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Vrátí výčet symboly pro vložené rámce odpovídající název funkce zadaný vložené.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Vrátí výčet symboly pro vložené rámce, které odpovídají zadaným zdrojovým umístěním.|  
  
## <a name="remarks"></a>Poznámky  
 Je důležité k volání [idiasession::put_loadaddress –](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metoda po vytvoření `IDiaSession` objektu – a hodnota předaná `put_loadAddress` metoda musí být nenulové – pro všechny virtuální adresy (VA) vlastnosti symboly, které budou přístupné. Adresa zátěže pochází z ať programu načíst laděné spustitelný soubor. Například můžete volat funkci Win32 `GetModuleInformation` načíst adresu zatížení pro spustitelný soubor, Zadaný popisovač ke spustitelnému souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak získat `IDiaSession` rozhraní jako součást obecné inicializace DIA SDK.  
  
```C++  
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
 [Rozhraní (přístup k rozhraní SDK ladění)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Přehled](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Soubor EXE](../../debugger/debug-interface-access/exe.md)   
 [Idiaaddressmap –](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiadatasource –](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::opensession –](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymbol::findchildren –](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Dotazování na soubor .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)