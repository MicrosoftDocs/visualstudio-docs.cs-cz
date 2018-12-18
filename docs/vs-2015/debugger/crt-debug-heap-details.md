---
title: Podrobnosti haldy ladění CRT | Dokumentace Microsoftu
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
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 691db8ce3b9b956ef7e0299acddac74c926fcf5a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803016"
---
# <a name="crt-debug-heap-details"></a>Podrobnosti haldy ladění CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma obsahuje podrobný pohled na haldu ladění CRT.  
  
##  <a name="BKMK_Contents"></a> Obsah  
 [Najít přetečení vyrovnávací paměti s haldou ladění](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Typy bloků na haldě ladění](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Zkontrolujte na těsnost integrity a paměť haldy](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Konfigurace ladění haldy](#BKMK_Configure_the_debug_heap)  
  
 [nové, odstranit a _CLIENT_BLOCKs v C++ ladění haldy](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Funkce vykazování stavu haldy](#BKMK_Heap_State_Reporting_Functions)  
  
 [Požadavky na přidělení haldy sledování](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Najít přetečení vyrovnávací paměti s haldou ladění  
 Dva z nejběžnějších a vystopovatelných problémů, které potkávají programátory jsou přepisování konce přidělené vyrovnávací paměti a nevrácená paměť (neúspěšný pokus volná přidělení, poté, co už nejsou potřeba). Halda ladění poskytuje výkonné nástroje pro řešení problémů s přidělením paměti tohoto druhu.  
  
 Ladicí verze funkcí haldy volání standardní nebo základní verze, používané v verze sestavení. Pokud budete požadovat blok paměti, přidělí správce hald ladění ze základní haldy mírně větší blok paměti, než je požadován a vrací ukazatel na vaši část tohoto bloku. Předpokládejme například, že vaše aplikace obsahuje volání: `malloc( 10 )`. V sestavení pro vydání [malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) by volat základní rutinu přidělení haldy požadující přidělení 10 bajtů. V sestavení pro ladění, ale `malloc` zavolal [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb), která by potom volala základní rutinu přidělení haldy požadující přidělení 10 bajtů plus přibližně 36 bajtů další paměti. Všechny výsledné bloky paměti v haldě ladění jsou spojeny do jednoho propojeného seznamu a seřazeny podle toho, kdy byly přiděleny.  
  
 Další paměť přidělená rutinami haldy ladění je používána pro ukládání informací, pro ukazatele, propojují paměť bloků ladicího dohromady a pro malé mezipaměti na každé straně vašich dat, které zachytí přepisy přiděleného regionu.  
  
 Struktura hlavičky bloku sloužící k ukládání informací o vedení haldy ladění je v současné době deklarována takto v DBGINT. H hlavičkový soubor:  
  
```  
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
  
 `NoMansLand` Vyrovnávací paměť po obou stranách oblasti dat uživatele bloku jsou aktuálně 4 bajty a jsou vyplněny hodnotou známého bajtu používaného rutinami ladění haldy k ověřování, že omezení uživatele bloku paměti nebyly přepsány. Halda ladění také doplní nové bloky paměti se známou hodnotou. Pokud se rozhodnete ponechat uvolněné bloky v propojeném seznamu haldy, jak je popsáno níže, tyto uvolněné bloky také zaplněny známou hodnotou. V současné době skutečně používané bajtové hodnoty jsou následující:  
  
 NoMansLand (0xFD)  
 "NoMansLand" vyrovnávací paměti na obou stranách paměti používané aplikace jsou nyní vyplněny 0xFD.  
  
 Uvolněné bloky (0xDD)  
 Uvolněné bloky jsou uchovávané nepoužívané v haldě ladění propojeného seznamu, když `_CRTDBG_DELAY_FREE_MEM_DF` je nastavený příznak jsou nyní vyplněny 0xDD.  
  
 Nové objekty (0xCD)  
 Nové objekty jsou vyplněny hodnotou 0xCD při přidělování.  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop")  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Typy bloků na haldě ladění  
 Každý blok paměti v haldě ladění je přiřazen k jednomu z pěti typů rozdělení. Tyto typy jsou sledovány a jinak hlášeny pro účely detekce nevrácení a vykazování stavu. Můžete zadat typ bloku přidělením pomocí přímého volání jedné z funkcí přidělení haldy ladění, jako [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Pět typů bloků paměti v haldě ladění (nastavit **nBlockUse** člena **_CrtMemBlockHeader** struktura) jsou následující:  
  
 **_NORMAL_BLOCK –**  
 Volání [malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) nebo [calloc](http://msdn.microsoft.com/library/17bb79a1-98cf-4096-90cb-1f9365cd6829) vytvoří blok Normal. Pokud máte v úmyslu používat pouze normální bloky a nepotřebujete bloky klienta, můžete definovat [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), což způsobí, že všechny přidělení haldy namapována na své ekvivalenty ladění v sestaveních ladění volá. To vám umožní soubor název a informace čísla řádku o každého volání přidělení v odpovídajícím záhlaví bloku.  
  
 `_CRT_BLOCK`  
 Bloky paměti přidělené interně mnoha funkcemi knihovny run-time jsou označeny jako CRT bloky tak mohly být zpracovány samostatně. V důsledku toho dochází k detekci přetečení a jiné operace nemusí být ovlivněny. Přidělení musí nikdy přidělit, přerozdělit nebo uvolnit jakýkoli blok typu CRT.  
  
 `_CLIENT_BLOCK`  
 Aplikace může zvlášť sledovat danou skupinu přidělení pro účely ladění jejich přidělením jako tento typ bloku paměti pomocí explicitního volání funkcí haldy ladění. Knihovny MFC například přidělují všechny **objektů CObject** jako bloky klienta; jiné aplikace mohou mít jiné paměťové objekty v blocích klienta. Podtypy bloků klienta lze také zadat pro větší rozlišovací schopnost sledování. Chcete-li určit podtypy bloků klienta, shift číslo doleva o 16 bitů a `OR` s `_CLIENT_BLOCK`. Příklad:  
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 Funkci háčku dodaná klientem pro výpis objektů uložených v blocích klienta lze nainstalovat pomocí [_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033)a pak bude volána pokaždé, když bude blok klienta vypsán pomocí funkce ladění. Navíc [_CrtDoForAllClientObjects](http://msdn.microsoft.com/library/d0fdb835-3cdc-45f1-9a21-54208e8df248) slouží k volání dané funkce poskytnuté aplikací pro každý blok klient v haldě ladění.  
  
 **_FREE_BLOCK**  
 Za normálních okolností jsou bloky, které jsou uvolněny odebrán ze seznamu. Zkontroluje, jestli uvolněné paměti není stále zapisováno, nebo simulovat podmínky nedostatku paměti, můžete zachovat uvolněné bloky v propojeném seznamu, označeny jako volné a se známou bajtovou hodnotou (nyní 0xDD).  
  
 **_IGNORE_BLOCK –**  
 Je možné vypnout operace haldy ladění pro určitou dobu. Během této doby se bloky paměti jsou uloženy v seznamu, ale jsou označeny jako bloky ignorovat.  
  
 Pokud chcete zjistit typ a podtyp daného bloku, použijte funkci [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) a makra **_BLOCK_TYPE** a **_BLOCK_SUBTYPE**. Makra jsou definovány (v crtdbg.h) následovně:  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Zkontrolujte na těsnost integrity a paměť haldy  
 Mnoho funkcí haldy ladění je třeba přistupovat zevnitř vašeho kódu. Následující část popisuje některé funkce a jejich použití.  
  
 `_CrtCheckMemory`  
 Můžete použít volání [_CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765), například pro kontrolu integrity haldy v libovolném bodě. Tato funkce zkontroluje každý blok paměti v haldě, ověří, že jsou platné informace záhlaví bloku paměti a potvrdí, že vyrovnávací paměti nebyly upraveny.  
  
 `_CrtSetDbgFlag`  
 Můžete řídit, jak haldy ladění uchovává informace o přidělení pomocí vnitřního příznaku [_crtDbgFlag](http://msdn.microsoft.com/library/9e7adb47-8ab9-4e19-81d5-e2f237979973), který lze přečíst a nastavit pomocí [_CrtSetDbgFlag](http://msdn.microsoft.com/library/b5657ffb-6178-4cbf-9886-1af904ede94c) funkce. Tak, že tento příznak změníte, můžete dát pokyn haldě ladění pro kontrolu nevracení paměti při ukončení programu a podávala zjištění. Podobně můžete určit, že uvolněné bloky paměti nesmí být odebrány ze seznamu propojených pro simulaci situace nedostatku paměti. Při kontrole haldy tyto uvolněné bloky jsou kontrolovány v k zajištění toho, aby nebyly narušeny.  
  
 **_CrtDbgFlag** příznak obsahuje následující pole bit:  
  
|Bitové pole.|Výchozí<br /><br /> value|Popis|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|On|Zapne předělení ladění. Když tento bit vypnutý, zůstane přidělení zřetězeno, ale jejich typ bloku je **_IGNORE_BLOCK**.|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|Off|Zabraňuje skutečnému uvolňování, například v případě simulace nedostatku paměti paměti. Když je tento bit zapnutý, uvolněné bloky jsou uchovávány v propojeném seznamu haldy ladění, ale jsou označené jako **_FREE_BLOCK** a vyplněny zvláštní bajtovou hodnotou.|  
|**_CRTDBG_CHECK_ALWAYS_DF**|Off|Způsobí, že **_CrtCheckMemory** volat na každé alokaci a dealokaci. Toto zpomalí provádění, ale rychle zachytí chyby.|  
|**_CRTDBG_CHECK_CRT_DF**|Off|Způsobí, že bloky označené jako typ **_CRT_BLOCK** mají být zahrnuty do detekce nevrácení paměti a rozdílu stavu operace. Když je tento bit vypnutý, paměť používaná interně knihovnou run-time je ignorována během těchto operací.|  
|**_CRTDBG_LEAK_CHECK_DF**|Off|Způsobuje spuštění kontroly nevracení při ukončení programu prostřednictvím volání provést **_CrtDumpMemoryLeaks**. Zpráva o chybě je generována, pokud se aplikaci nepodaří uvolnění veškeré přidělené paměti.|  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> Konfigurace ladění haldy  
 Všechna volání funkce haldy jako `malloc`, `free`, `calloc`, `realloc`, `new`, a `delete` přeložit na ladicí verze těchto funkcí, které pracují v haldě ladění. Při uvolnění bloku paměti ladění haldy automaticky kontroluje integritu na obou stranách přidělené oblasti vyrovnávací paměti a vydá zprávu o chybě, pokud došlo k přepsání.  
  
 **Použití haldy ladění**  
  
- Propojte sestavení ladění aplikace s ladicí verzí knihovny run-time C.  
  
  **Chcete-li změnit jeden nebo více bitových polí _crtDbgFlag a vytvoření nového stavu pro příznak**  
  
1. Volání `_CrtSetDbgFlag` s `newFlag` parametr nastaven na `_CRTDBG_REPORT_FLAG` (k získání aktuálního `_crtDbgFlag` stavu) a vrácené hodnoty uložte v dočasné proměnné.  
  
2. Zapněte všechny bity `OR`- ováním (bitový &#124; symbol) dočasné proměnné s odpovídajícími bitovými maskami (představovanými v kódu aplikace konstantami manifestu).  
  
3. Vypnout podle bity `AND`- ing (bitové & symbol) proměnné s `NOT` (bitový ~ symbol) z příslušné bitovými maskami.  
  
4. Volání `_CrtSetDbgFlag` s `newFlag` parametr nastaven na hodnotu uloženou v dočasné proměnné, chcete-li vytvořit nový stav pro `_crtDbgFlag`.  
  
   Například následující řádky kódu zapnout automatickou detekci nevrácení paměti a vypnou kontrolu bloků typu `_CRT_BLOCK`:  
  
```  
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> nové, odstranit a _CLIENT_BLOCKs v C++ ladění haldy  
 Ladicí verze knihovny run-time C obsahuje ladicí verze jazyka C++ `new` a `delete` operátory. Pokud používáte `_CLIENT_BLOCK` typ přidělení, je třeba zavolat ladicí verzi `new` operátor přímo nebo vytvořit makra, která nahradí `new` operátor v režimu ladění, jak je znázorněno v následujícím příkladu:  
  
```  
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
  
 Ladicí verze `delete` operátor funguje s blokem všech typů a nevyžaduje žádné změny ve svém programu při kompilaci verze vydání.  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> Funkce vykazování stavu haldy  
 **_CrtMemState**  
  
 Chcete-li zachytit souhrnný snímek stavu haldy v daném okamžiku, použijte strukturu _CrtMemState definovanou v CRTDBG. V:  
  
```  
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
  
 Tato struktura ukládá ukazatel na první blok (poslední přidělený) v propojeném seznamu haldy ladění. Potom ve dvou polích zaznamenává, kolik jednotlivých typů paměťových blokovat (_NORMAL_BLOCK, `_CLIENT_BLOCK`, _FREE_BLOCK a tak dále) jsou v seznamu a počet bajtů alokovaných v každém druhu bloku. Nakonec zaznamená nejvyšší počet bajtů alokovaných v haldě jako celek až k danému bodu a počet bajtů v tuto chvíli přidělená.  
  
 **Ostatní funkce vykazování CRT**  
  
 Následující funkce sestavy stavu a obsahu haldy a použijte informace pro zjištění nevracení paměti a dalších problémů.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[_CrtMemCheckpoint](http://msdn.microsoft.com/library/f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc)|Uloží snímek haldy ve **_CrtMemState** struktura poskytnuté aplikací.|  
|[_CrtMemDifference](http://msdn.microsoft.com/library/0f327278-b551-482f-958b-76941f796ba4)|Porovná dvě struktury stavu paměti, ukládá rozdíly mezi nimi ve třetí struktuře stavu a vrátí TRUE, pokud dva stavy se liší.|  
|[_CrtMemDumpStatistics](http://msdn.microsoft.com/library/27b9d731-3184-4a2d-b9a7-6566ab28a9fe)|Výpisy stavu systému daného **_CrtMemState** struktury. Struktura může obsahovat snímek stavu ladění haldy v daném okamžiku nebo rozdíl mezi dvěma snímky.|  
|[_CrtMemDumpAllObjectsSince](http://msdn.microsoft.com/library/c48a447a-e6bb-475c-9271-a3021182a0dc)|Vypíše informace o všech objektech, které jsou přiděleny od pořízení daného snímku haldy nebo od začátku spuštění. Pokaždé, když se vypíše **_CLIENT_BLOCK** bloku volá funkci připojení poskytnutou aplikací, pokud byla nainstalována pomocí **_CrtSetDumpClient**.|  
|[_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c)|Určuje, zda paměti došlo k nevrácení od spuštění programu a pokud ano, vypíše všechny přidělené objekty. Pokaždé, když **_CrtDumpMemoryLeaks** výpisy stavu systému **_CLIENT_BLOCK** bloku volá funkci připojení poskytnutou aplikací, pokud byla nainstalována pomocí **_CrtSetDumpClient**.|  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> Požadavky na přidělení haldy sledování  
 Ačkoli přesným rozpoznáním zdrojový soubor název a číslo řádku na která spustí k vyhodnocení nebo vytváření sestav – makro je často velmi užitečné při hledání příčiny problému, stejné není pravděpodobné jako na hodnotu true z funkcí přidělení haldy. Když lze makra vkládat na mnoho vhodných míst v logické stromové struktuře aplikace, je přidělení často ukryto ve speciální rutině, která je volána z mnoha různých míst v mnoha různých časech. Otázka obvykle není který řádek kódu způsobil špatné přidělené, ale spíše které jedna z tisíců přidělení provedených tohoto řádku kódu bylo chybné a proč.  
  
 **Počty požadavků na jedinečné přidělení a _crtBreakAlloc**  
  
 Výhod jedinečného čísla požadavku přidělení u každého bloku haldy ladění je nejjednodušší způsob, jak identifikovat konkrétní volání přidělení haldy, které se nezdařilo. Pokud informace o bloku jsou vykázány jednou z funkcí s výpisem paměti, je toto číslo žádosti o přidělení uzavřeno ve složených závorkách (například "{36}").  
  
 Jakmile budete znát číslo žádosti o přidělení nesprávně přiděleného bloku, které můžete předat toto číslo [_CrtSetBreakAlloc](http://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1) aby vytvořila zarážku. Spuštění se přeruší těsně před rozdělením bloku a vy tak můžete zpětně zjistit, jaké rutina je odpovědná za chybné volání. Aby se zabránilo opětovné kompilaci, můžete provést totéž v ladicím programu nastavením **_crtBreakAlloc** na číslo žádosti o přidělení vás zajímají.  
  
 **Vytváření verzí ladění pro vaše rutiny přidělení**  
  
 Poněkud složitějším přístupem je vytvoření verzí ladění vlastní rutiny přidělení srovnatelné **_dbg** verze [funkcí přidělení haldy](../debugger/debug-versions-of-heap-allocation-functions.md). Můžete poté předat zdrojový soubor a řádku argumentů prostřednictvím základní rutiny přidělení haldy a okamžitě budete moci zobrazit, odkud pochází chybné přidělení.  
  
 Předpokládejme například, že aplikace obsahuje běžně používanou rutinu, která je podobný následujícímu:  
  
```  
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 V souboru hlaviček můžete přidat například následující kód:  
  
```  
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 V dalším kroku můžete změnit přidělení v vaše rutině vytváření záznamu takto:  
  
```  
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
  
 Teď zdrojového souboru název a číslo řádku kde `addNewRecord` byla volána se uloží do každého výsledného bloku přiděleného v haldě ladění a budou hlášeny po prozkoumání tohoto bloku.  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
## <a name="see-also"></a>Viz také  
 [Ladění nativního kódu](../debugger/debugging-native-code.md)



