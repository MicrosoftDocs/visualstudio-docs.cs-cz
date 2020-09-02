---
title: IDiaSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7fb8c5336a14180b3742fa02a91e6532b6e5831
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465347"
---
# <a name="idiasession"></a>IDiaSession
Poskytuje kontext dotazu pro symboly ladění.

## <a name="syntax"></a>Syntax

```
IDiaSession : IUnknown
```

## <a name="methods"></a>Metody
V následující tabulce jsou uvedeny metody `IDiaSession` .

|Metoda|Popis|
|------------|-----------------|
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Načte adresu načtení pro spustitelný soubor, který odpovídá symbolům v tomto úložišti symbolů. Jedná se o stejnou hodnotu, která byla předána `put_loadAddress` metodě.|
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Nastaví adresu zatížení pro spustitelný soubor, který odpovídá symbolům v tomto úložišti symbolů. **Poznámka:**  Je důležité volat tuto metodu při získání `IDiaSession` objektu a před tím, než začnete používat objekt.|
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Načte odkaz na globální rozsah.|
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Načte enumerátor pro všechny tabulky obsažené v úložišti symbolů.|
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Načte enumerátor pro všechny pojmenované symboly ve statických umístěních.|
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Načte všechny podřízené položky zadaného nadřazeného identifikátoru, který se shoduje s názvem a typem symbolu.|
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Načte zadaný typ symbolu, který obsahuje nebo je nejblíže zadané adrese.|
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Načte zadaný typ symbolu, který obsahuje nebo je nejblíže k zadané relativní virtuální adrese (RVA).|
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Načte zadaný typ symbolu, který obsahuje nebo je nejbližší k zadané virtuální adrese (VA).|
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Načte symbol, který obsahuje zadaný token metadat.|
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Kontroluje, zda jsou dva symboly ekvivalentní.|
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Načte symbol podle jeho jedinečného identifikátoru.|
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Načte zadaný typ symbolu, který obsahuje nebo je nejbližší, zadanou relativní virtuální adresu a posun.|
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Načte zadaný typ symbolu, který obsahuje nebo je nejbližší, zadanou virtuální adresu a posun.|
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Načte zdrojový soubor podle kompilantu a Name.|
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Načte zdrojový soubor podle identifikátoru zdrojového souboru.|
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Načte čísla řádků v zadaném kompilantu a identifikátoru zdrojového souboru.|
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Načte řádky v zadaném kompilantu, které obsahují zadanou adresu.|
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Načte řádky v zadaném kompilantu, které obsahují zadanou relativní virtuální adresu.|
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Najde informace o číslech řádků na řádcích obsažených v zadaném rozsahu adres.|
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Načte řádky v zadaném kompilantu podle zdrojového souboru a čísla řádku.|
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Načte zdroj, který byl umístěn do úložiště symbolů podle zprostředkovatelů atributů nebo jiných komponent procesu kompilace.|
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Načte výčtové sekvence datových proudů ladění.|
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Načte výčet, který umožňuje klientovi iterovat všemi vloženými snímky na dané adrese.|
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Načte výčet, který umožňuje klientovi iterovat všemi vloženými snímky na zadané relativní virtuální adrese (RVA).|
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Načte výčet, který umožňuje klientovi iterovat všemi vloženými snímky na zadané virtuální adrese (VA).|
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech funkcí, které jsou vloženy přímo nebo nepřímo zadaným nadřazeným symbolem.|
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech funkcí, které jsou vloženy přímo nebo nepřímo, zadaným nadřazeným symbolem a jsou obsaženy v zadaném rozsahu adres.|
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech funkcí, které jsou vloženy přímo nebo nepřímo zadaným nadřazeným symbolem a jsou obsaženy v rámci zadané relativní virtuální adresy (RVA).|
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech funkcí, které jsou vloženy přímo nebo nepřímo, zadaným nadřazeným symbolem a jsou obsaženy v rámci zadané virtuální adresy (VA).|
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech funkcí, které jsou vloženy přímo nebo nepřímo v zadaném zdrojovém souboru a čísle řádku.|
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech zapsaných funkcí, které odpovídají zadanému názvu.|
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Vrátí výčet symbolů pro proměnnou, na kterou je zadaná hodnota značky odpovídat ve funkci zástupného kódu nadřazeného akcelerátoru.|
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|S ohledem na odpovídající hodnotu značky vrátí tato metoda výčet symbolů, které jsou obsaženy v zadané relativní virtuální adrese v zadané nadřazené funkci akcelerátoru.|
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Vrátí výčet symbolů pro vložené rámce, které odpovídají zadanému názvu vložené funkce.|
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Vrátí výčet symbolů pro vložené rámce, které odpovídají zadanému zdrojovému umístění.|

## <a name="remarks"></a>Poznámky
Je důležité volat metodu [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) po vytvoření `IDiaSession` objektu – a hodnota předaná `put_loadAddress` metodě musí být nenulová – pro všechny vlastnosti virtuální adresy (VA) symbolů, které mají být přístupné. Zátěžová adresa pochází z libovolného programu, který načte laděný spustitelný soubor. Například můžete volat funkci Win32 `GetModuleInformation` pro načtení adresy zatížení pro spustitelný soubor, s ohledem na popisovač spustitelného souboru.

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
Záhlaví: Dia2. h

Knihovna: diaguids. lib

KNIHOVNA DLL: msdia80.dll

## <a name="see-also"></a>Viz také
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [Přehled](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [Exe](../../debugger/debug-interface-access/exe.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
- [Dotazování na soubor .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
