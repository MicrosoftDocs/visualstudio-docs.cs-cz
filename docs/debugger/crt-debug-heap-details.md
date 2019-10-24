---
title: Podrobnosti haldy ladění CRT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d09319e412d693fc9df95d9ae9b9773f0869afc3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745629"
---
# <a name="crt-debug-heap-details"></a>Podrobnosti haldy ladění CRT
Toto téma poskytuje podrobný přehled o haldě ladění CRT.

## <a name="BKMK_Contents"></a>Obsah
[Najít přetečení vyrovnávací paměti s haldou ladění](#BKMK_Find_buffer_overruns_with_debug_heap)

[Typy bloků na haldě ladění](#BKMK_Types_of_blocks_on_the_debug_heap)

[Kontrola integrity haldy a nevracení paměti](#BKMK_Check_for_heap_integrity_and_memory_leaks)

[Konfigurace haldy ladění](#BKMK_Configure_the_debug_heap)

[New, DELETE a _CLIENT_BLOCKs v haldě C++ ladění](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)

[Funkce vytváření sestav o stavu haldy](#BKMK_Heap_State_Reporting_Functions)

[Sledovat žádosti o přidělení haldy](#BKMK_Track_Heap_Allocation_Requests)

## <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a>Najít přetečení vyrovnávací paměti s haldou ladění
Dva nejběžnější a neodstranitelné problémy, ke kterým programátoři narazí, přepíší konec přidělené vyrovnávací paměti a nevrácené paměti (nedaří se jim uvolnit přidělení po jejich nepotřebě). Halda ladění poskytuje výkonné nástroje pro řešení problémů s přidělením paměti tohoto druhu.

Ladicí verze funkcí haldy volají standardní nebo základní verze používané v sestaveních vydaných verzí. Když vyžádáte blok paměti, Správce haldy ladění přidělí z základní haldy mírně větší blok paměti, než je požadováno, a vrátí ukazatel na vaši část tohoto bloku. Předpokládejme například, že vaše aplikace obsahuje volání: `malloc( 10 )`. V buildu pro vydání [](/cpp/c-runtime-library/reference/malloc) vyvolala objekt sestavil základní rutinu přidělení haldy požadující přidělení 10 bajtů. V sestavení ladění však `malloc` volat [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg), což by pak volalo základní rutinu přidělení haldy požadující přidělení 10 bajtů a přibližně 36 bajtů další paměti. Všechny výsledné bloky paměti v haldě ladění jsou propojeny v jednom propojeném seznamu, seřazené podle toho, kdy byly přiděleny.

Další paměť přidělená rutinami haldy ladění se používá pro informace o účetnictví, pro ukazatele, které propojuje bloky paměti ladění společně, a pro malé vyrovnávací paměti na obou stranách vašich dat, aby zachytával přepsání přidělené oblasti.

V současné době je struktura hlaviček bloku používaná k uložení informací o účetnictví haldy ladění deklarována takto v DBGINT. Soubor hlaviček H:

```cpp
typedef struct _CrtMemBlockHeader
{
// Pointer to the block allocated just before this one:
    struct _CrtMemBlockHeader *pBlockHeaderNext;
// Pointer to the block allocated just after this one:
    struct _CrtMemBlockHeader *pBlockHeaderPrev;
    char *szFileName;    // File name
    int nLine;           // Line number
    size_t nDataSize;    // Size of user block
    int nBlockUse;       // Type of block
    long lRequest;       // Allocation number
// Buffer just before (lower than) the user's memory:
    unsigned char gap[nNoMansLandSize];
} _CrtMemBlockHeader;

/* In an actual memory block in the debug heap,
 * this structure is followed by:
 *   unsigned char data[nDataSize];
 *   unsigned char anotherGap[nNoMansLandSize];
 */
```

Vyrovnávací paměti `NoMansLand` na obou stranách v oblasti dat uživatele bloku jsou aktuálně 4 bajty a jsou vyplněny známou bajtovou hodnotou, kterou používají rutiny pro ladění haldy k ověření, že limity paměti uživatele nebyly přepsány. Halda ladění také vyplní nové bloky paměti se známou hodnotou. Pokud se rozhodnete zachovat uvolněné bloky v propojeném seznamu haldy, jak je vysvětleno níže, tyto uvolněné bloky jsou také vyplněny známou hodnotou. V současné době jsou použity skutečné bajtové hodnoty následujícím způsobem:

NoMansLand (0xFD) vyrovnávací paměti "NoMansLand" na obou stranách paměti používané aplikací jsou nyní vyplněny 0xFD.

Uvolněné bloky (0xDD) uvolněné bloky používané v propojeném seznamu haldy ladění, pokud je nastaven příznak `_CRTDBG_DELAY_FREE_MEM_DF`, jsou aktuálně vyplněné 0xDD.

Nové objekty (0xCD) nové objekty jsou vyplněny 0xCD při jejich přidělení.

![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [](#BKMK_Contents)

## <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a>Typy bloků na haldě ladění
Každý blok paměti v haldě ladění je přiřazen k jednomu z pěti typů alokace. Tyto typy jsou sledovány a hlášeny jinak pro účely zjišťování nevracení a vytváření sestav stavu. Typ bloku můžete určit přidělením pomocí přímého volání jedné z funkcí alokace haldy ladění, jako je [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Pět typů paměťových bloků v haldě ladění (nastavené v **nBlockUse** členu struktury **_CrtMemBlockHeader** ) jsou následující:

**_NORMAL_BLOCK** Volání metody calloc [a](/cpp/c-runtime-library/reference/malloc) vytvoří [](/cpp/c-runtime-library/reference/calloc) normální blok. Pokud máte v úmyslu používat pouze normální bloky a nepotřebují klientské bloky, je vhodné definovat [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), což způsobí, že všechna volání přidělení haldy budou mapována na jejich ekvivalenty ladění v sestaveních ladění. To umožní uložit informace o názvu souboru a číslu řádku pro každé volání přidělení do odpovídající hlavičky bloku.

`_CRT_BLOCK` bloky paměti, které jsou přiděleny interně mnoha funkcím běhové knihovny jsou označeny jako bloky CRT, aby mohly být zpracovány samostatně. V důsledku toho nemusí být detekce nevracení a jiné operace ovlivněny. Přidělení nesmí nikdy přidělit, znovu přidělit nebo uvolnit libovolný blok typu CRT.

`_CLIENT_BLOCK` aplikace může uchovávat zvláštní sledování dané skupiny přidělení pro účely ladění tím, že je přidělí jako tento typ bloku paměti pomocí explicitních volání funkcí haldy ladění. Knihovna MFC například přiděluje všechny **objektů CObject** jako klientské bloky; jiné aplikace mohou v klientských blocích uchovávat různé paměťové objekty. Podtypy klientských bloků lze také zadat pro lepší členitost sledování. Chcete-li určit podtypy klientských bloků, posunete číslo nalevo o 16 bitech a `OR` `_CLIENT_BLOCK`. Příklad:

```cpp
#define MYSUBTYPE 4
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));
```

Funkce zavěšení poskytovanou klientem pro výpis objektů uložených v klientských blocích může být nainstalována pomocí [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)a pak bude volána vždy, když je klientský blok vypsán funkcí ladění. [_CrtDoForAllClientObjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects) lze také použít k volání dané funkce poskytnuté aplikací pro každý blok klienta v haldě ladění.

**_FREE_BLOCK** Obvykle jsou bloky, které jsou uvolněny, odebrány ze seznamu. Pokud chcete ověřit, jestli se uvolněná paměť pořád nepíše do nebo simulovat podmínky nedostatku paměti, můžete zvolit, aby se uvolněné bloky v propojeném seznamu zachovaly, označené jako volné a se známou hodnotou v bajtu (aktuálně 0xDD).

**_IGNORE_BLOCK** Je možné vypnout operace ladění haldy po určitou dobu. Během této doby jsou bloky paměti uchovávány v seznamu, ale jsou označeny jako ignorovat bloky.

Chcete-li určit typ a podtyp daného bloku, použijte funkci [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) a makra **_BLOCK_TYPE** a **_BLOCK_SUBTYPE**. Makra jsou definována (v souboru Crtdbg. h) následujícím způsobem:

```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)
```

![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [](#BKMK_Contents)

## <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a>Kontrola integrity haldy a nevracení paměti
Mnohé z funkcí haldy ladění musí být dostupné v rámci vašeho kódu. V následující části jsou popsány některé funkce a jejich použití.

`_CrtCheckMemory` můžete použít volání [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory), například pro kontrolu integrity haldy v jakémkoli bodě. Tato funkce zkontroluje každý blok paměti v haldě, ověří, zda jsou informace v hlavičce bloku paměti platné, a potvrdí, že vyrovnávací paměti nebyly upraveny.

`_CrtSetDbgFlag` můžete řídit, jak halda ladění udržuje přehled o přiděleních pomocí interního příznaku, [_crtDbgFlag](/cpp/c-runtime-library/crtdbgflag), který lze číst a nastavit pomocí funkce [_CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag) . Změnou tohoto příznaku můžete instruovat haldu ladění, aby kontrolovala nevracení paměti při ukončení programu a nahlášení všech zjištěných nevrácených operací. Podobně můžete určit, že uvolněné paměťové bloky nebudou odebrány z propojeného seznamu, aby se simulovaly situace v nedostatku paměti. Při kontrole haldy jsou tyto uvolněné bloky kontrolovány v celém rozsahu, čímž se zajistí, že nebudou narušeny.

Příznak **_crtDbgFlag** obsahuje následující bitová pole:

|Bitové pole|Výchozí<br /><br /> value|Popis|
|---------------|-----------------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|On|Zapne alokaci ladění. Když je tento bit vypnutý, přidělení zůstane zřetězené společně, ale jeho typ bloku je **_IGNORE_BLOCK**.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|Off|Zabraňuje ve skutečném uvolnění paměti, jako při simulaci podmínek s nízkou pamětí. Pokud je tento bit zapnutý, uvolněné bloky jsou uchovávány v propojeném seznamu haldy ladění, ale jsou označeny jako **_FREE_BLOCK** a jsou vyplněny speciální bajtovou hodnotou.|
|**_CRTDBG_CHECK_ALWAYS_DF**|Off|Způsobuje volání **_CrtCheckMemory** při každém přidělení a zrušení přidělení. To zpomaluje provádění, ale rychle zachycuje chyby.|
|**_CRTDBG_CHECK_CRT_DF**|Off|Způsobí, že bloky označené jako Type **_CRT_BLOCK** budou zahrnuty do operací detekce nevracení a rozdíl stavu. Pokud je tento bit vypnutý, paměť používaná interně knihovnou runtime se během takových operací ignoruje.|
|**_CRTDBG_LEAK_CHECK_DF**|Off|Způsobí, že se kontrola nevracení provádí při ukončení programu prostřednictvím volání **_CrtDumpMemoryLeaks**. Pokud aplikace nedokázala uvolnit veškerou přidělenou paměť, bude vygenerována zpráva o chybách.|

![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [](#BKMK_Contents)

## <a name="BKMK_Configure_the_debug_heap"></a>Konfigurace haldy ladění
Všechna volání funkcí haldy, jako jsou `malloc`, `free`, `calloc`, `realloc`, `new` a `delete` přeložit na ladicí verze těchto funkcí, které fungují v haldě ladění. Když uvolníte blok paměti, halda ladění automaticky kontroluje integritu vyrovnávací paměti na obou stranách vaší přidělené oblasti a při přepisování vydá zprávu o chybě.

**Použití haldy ladění**

- Propojte sestavení ladění aplikace pomocí ladicí verze knihovny run-time jazyka C.

  **Změna jednoho nebo více _crtDbgFlag bitových polí a vytvoření nového stavu pro příznak**

1. Zavolejte `_CrtSetDbgFlag` s parametrem `newFlag` nastaveným na `_CRTDBG_REPORT_FLAG` (pro získání aktuálního stavu `_crtDbgFlag`) a uložte vrácenou hodnotu do dočasné proměnné.

2. Zapněte všechny bity pomocí `OR` (bitový &#124; symbol) dočasné proměnné s odpovídajícím vyčíslení (reprezentovaným v kódu aplikace pomocí konstant manifestu).

3. Vypněte ostatní bity pomocí `AND` (bitový & symbol) proměnné s `NOT` (bitový symbol ~ symbol) odpovídající vyčíslení.

4. Chcete-li vytvořit nový stav pro `_crtDbgFlag`, zavolejte `_CrtSetDbgFlag` s parametrem `newFlag` nastaveným na hodnotu uloženou v dočasné proměnné.

   Například následující řádky kódu zapínají automatickou detekci úniku a vypnou kontrolu bloků typu `_CRT_BLOCK`:

```cpp
// Get current flag
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn on leak-checking bit.
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;

// Turn off CRT block checking bit.
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;

// Set flag to the new value.
_CrtSetDbgFlag( tmpFlag );
```

![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [](#BKMK_Contents)

## <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a>New, DELETE a _CLIENT_BLOCKs v haldě C++ ladění
Ladicí verze knihovny run-time jazyka C obsahují ladicí verze operátorů C++ `new` a `delete`. Použijete-li typ přidělení `_CLIENT_BLOCK`, je nutné zavolat přímo ladicí verzi operátoru `new` nebo vytvořit makra, která nahrazují operátor `new` v režimu ladění, jak je znázorněno v následujícím příkladu:

```cpp
/* MyDbgNew.h
 Defines global operator new to allocate from
 client blocks
*/

#ifdef _DEBUG
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)
#else
   #define DEBUG_CLIENTBLOCK
#endif // _DEBUG

/* MyApp.cpp
        Use a default workspace for a Console Application to
 *      build a Debug version of this code
*/

#include "crtdbg.h"
#include "mydbgnew.h"

#ifdef _DEBUG
#define new DEBUG_CLIENTBLOCK
#endif

int main( )   {
    char *p1;
    p1 =  new char[40];
    _CrtMemDumpAllObjectsSince( NULL );
}
```

Ladicí verze operátoru `delete` pracuje se všemi typy bloku a při kompilování vydané verze nevyžaduje žádné změny v programu.

![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [](#BKMK_Contents)

## <a name="BKMK_Heap_State_Reporting_Functions"></a>Funkce vytváření sestav o stavu haldy
 **_CrtMemState**

 Chcete-li zachytit Souhrnný snímek stavu haldy v daném čase, použijte strukturu _CrtMemState definovanou v souboru Crtdbg. Y

```cpp
typedef struct _CrtMemState
{
    // Pointer to the most recently allocated block:
    struct _CrtMemBlockHeader * pBlockHeader;
    // A counter for each of the 5 types of block:
    size_t lCounts[_MAX_BLOCKS];
    // Total bytes allocated in each block type:
    size_t lSizes[_MAX_BLOCKS];
    // The most bytes allocated at a time up to now:
    size_t lHighWaterCount;
    // The total bytes allocated at present:
    size_t lTotalCount;
} _CrtMemState;
```

Tato struktura uloží ukazatel na první blok (poslední přidělený) v propojeném seznamu haldy ladění. Pak ve dvou polích zaznamenává, kolik každého typu bloku paměti (_NORMAL_BLOCK, `_CLIENT_BLOCK`, _FREE_BLOCK a tak dále) jsou v seznamu a kolik bajtů bylo přiděleno v každém typu bloku. Nakonec zaznamenává nejvyšší počet bajtů přidělených v haldě jako celek až k tomuto bodu a počet aktuálně přidělených bajtů.

**Další funkce vytváření sestav CRT**

Následující funkce vykazují stav a obsah haldy a využívají tyto informace k detekci nevracení paměti a dalších problémů.

|Funkce|Popis|
|--------------|-----------------|
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|Uloží snímek haldy ve struktuře **_CrtMemState** dodávané aplikací.|
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|Porovná dvě struktury stavu paměti, uloží rozdíl mezi nimi ve třetí struktuře stavu a vrátí hodnotu TRUE, pokud jsou dva stavy odlišné.|
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|Vypíše danou strukturu **_CrtMemState** . Struktura může obsahovat snímek stavu haldy ladění v daném okamžiku nebo rozdíl mezi dvěma snímky.|
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Vypíše informace o všech objektech přidělených vzhledem k tomu, že daný snímek byl získán z haldy nebo od začátku provádění. Pokaždé, když vypíše blok **_CLIENT_BLOCK** , volá funkci připojení poskytnutou aplikací, pokud byla jedna nainstalována pomocí **_CrtSetDumpClient**.|
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Určuje, zda došlo k nevrácení paměti od spuštění programu, a pokud ano, vypíše všechny přidělené objekty. Pokaždé, když **_CrtDumpMemoryLeaks** vypíše blok **_CLIENT_BLOCK** , volá funkci připojení poskytnutou aplikací, pokud byla jedna nainstalována pomocí **_CrtSetDumpClient**.|

![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [](#BKMK_Contents)

## <a name="BKMK_Track_Heap_Allocation_Requests"></a>Sledovat žádosti o přidělení haldy
I když se podíváme na název zdrojového souboru a číslo řádku, ve kterém se spouští kontrolní výraz nebo makro vytváření sestav, je často velmi užitečné při hledání příčiny problému, totéž není, protože by to mohlo být pravda pro funkce přidělení haldy. I když mohou být makra vložena v mnoha vhodných bodech ve stromové struktuře aplikace, přidělení je často ukryto ve speciální rutině, která je volána z mnoha různých míst v mnoha různých časech. Otázka většinou není tím, který řádek kódu vedl k chybnému přidělení, ale místo toho, aby jedna z tisíců přidělení provedených tímto řádkem kódu byla chybná a proč.

**Jedinečné číslo žádosti o přidělení a _crtBreakAlloc**

Nejjednodušší způsob, jak identifikovat konkrétní volání přidělení haldy, které je chybné, je využít jedinečné číslo žádosti o přidělení přidružené ke každému bloku v haldě ladění. Pokud jsou informace o bloku hlášeny jednou z funkcí výpisu paměti, toto číslo žádosti o přidělení je uzavřeno ve složených závorkách (například "{36}").

Jakmile znáte číslo žádosti o přidělení nesprávného přiděleného bloku, můžete toto číslo předat [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc) a vytvořit zarážku. Spuštění bude přerušeno těsně před přidělením bloku a můžete zjistit, jakou rutinu zodpovídá za chybné volání. Aby nedošlo k opětovnému kompilování, můžete v ladicím programu provádět stejné věci nastavením **_crtBreakAlloc** na číslo žádosti o přidělení, které vás zajímá.

**Vytváření verzí ladění rutin přidělení**

Trochu komplikovanější je vytvořit ladicí verze vlastních rutin přidělení, porovnatelné s verzemi **_dbg** [funkcí přidělení haldy](../debugger/debug-versions-of-heap-allocation-functions.md). Pak můžete předat argumenty zdrojového souboru a čísla řádku do základních rutin přidělení haldy a okamžitě budete moci zjistit, kde vzniklo špatné přidělení.

Předpokládejme například, že vaše aplikace obsahuje často používanou rutinu podobnou následující:

```cpp
int addNewRecord(struct RecStruct * prevRecord,
                 int recType, int recAccess)
{
    // ...code omitted through actual allocation...
    if ((newRec = malloc(recSize)) == NULL)
    // ... rest of routine omitted too ...
}
```

V hlavičkovém souboru můžete přidat například následující kód:

```cpp
#ifdef _DEBUG
#define  addNewRecord(p, t, a) \
            addNewRecord(p, t, a, __FILE__, __LINE__)
#endif
```

Dále můžete změnit přidělení v rutině vytváření záznamů následujícím způsobem:

```cpp
int addNewRecord(struct RecStruct *prevRecord,
                int recType, int recAccess
#ifdef _DEBUG
               , const char *srcFile, int srcLine
#endif
    )
{
    /* ... code omitted through actual allocation ... */
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,
            srcFile, scrLine)) == NULL)
    /* ... rest of routine omitted too ... */
}
```

Nyní se název zdrojového souboru a číslo řádku, kde `addNewRecord` byl volán, uloží do každého výsledného bloku, který je přidělen v haldě ladění a bude hlášen při zkoumání tohoto bloku.

![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [](#BKMK_Contents)

## <a name="see-also"></a>Viz také:
[Ladění nativního kódu](../debugger/debugging-native-code.md)
