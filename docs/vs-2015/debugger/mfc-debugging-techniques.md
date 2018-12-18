---
title: Techniky ladění MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1e7a1ea69da1cafa38ae2a7bfa4551d3d40a8d4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745112"
---
# <a name="mfc-debugging-techniques"></a>Techniky ladění MFC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud ladíte aplikace knihovny MFC, může být užitečné tyto techniky ladění.  
  
##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 [Afxdebugbreak –](#BKMK_AfxDebugBreak)  
  
 [TRACE – makro](#BKMK_The_TRACE_macro)  
  
 [Zjišťování nevracení paměti v prostředí MFC](#BKMK_Memory_leak_detection_in_MFC)  
  
- [Sledování přidělení paměti](#BKMK_Tracking_memory_allocations)  
  
- [Povolení diagnostiky paměti](#BKMK_Enabling_memory_diagnostics)  
  
- [Pořizování snímků paměti](#BKMK_Taking_memory_snapshots)  
  
- [Statistika paměti zobrazení](#BKMK_Viewing_memory_statistics)  
  
- [Vypíše aktuální objekt](#BKMK_Taking_object_dumps)  
  
  - [Interpretace paměti výpisy stavu systému](#BKMK_Interpreting_memory_dumps)  
  
  - [Vypíše přizpůsobení objektu](#BKMK_Customizing_object_dumps)  
  
    [Zmenšení velikosti knihovny MFC ladění sestavení](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)  
  
  - [Vytvoření aplikace knihovny MFC s ladicími informacemi pro vybrané moduly](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)  
  
##  <a name="BKMK_AfxDebugBreak"></a> Afxdebugbreak –  
 Knihovna MFC poskytuje speciální [afxdebugbreak –](http://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) funkce pro pevné zakódování zarážky ve zdrojovém kódu:  
  
```  
AfxDebugBreak( );  
  
```  
  
 Na platformách Intel `AfxDebugBreak` vytvoří následující kód, který konce ve zdroji kódu namísto kódu jádra:  
  
```  
_asm int 3  
```  
  
 Na ostatních platformách `AfxDebugBreak` pouze volá `DebugBreak`.  
  
 Nezapomeňte odebrat `AfxDebugBreak` příkazy při vytvoření verze sestavení nebo použít `#ifdef _DEBUG` ohraničit je.  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_TRACE_macro"></a> TRACE – makro  
 Pro zobrazení zpráv ve svém programu v ladicím programu [okno výstup](../ide/reference/output-window.md), můžete použít [ATLTRACE](http://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e) – makro nebo MFC [trasování](http://msdn.microsoft.com/library/7b6f42d8-b55a-4bba-ab04-c46251778e6f) – makro. Stejně jako [kontrolní výrazy](../debugger/c-cpp-assertions.md), trasování makra jsou aktivní pouze v ladicí verzi programu a zmizí při kompilaci ve vydané verzi.  
  
 Následující příklady ukazují některé ze způsobů, jak můžete použít **trasování** – makro. Stejně jako `printf`, **trasování** – makro může zpracovat počet argumentů.  
  
```  
int x = 1;  
int y = 16;  
float z = 32.0;  
TRACE( "This is a TRACE statement\n" );  
  
TRACE( "The value of x is %d\n", x );  
  
TRACE( "x = %d and y = %d\n", x, y );  
  
TRACE( "x = %d and y = %x and z = %f\n", x, y, z );  
```  
  
 TRACE – makro správně zpracovává char * i wchar_t\* parametry. Následující příklady ukazují použití TRACE – makro společně se různé typy parametrů řetězce.  
  
```  
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);  
  
TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);  
  
TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);  
  
```  
  
 Další informace o **trasování** – makro, naleznete v tématu [diagnostické služby](http://msdn.microsoft.com/library/8d78454f-9fae-49c2-88c9-d3fabd5393e8).  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Memory_leak_detection_in_MFC"></a> Zjišťování nevracení paměti v prostředí MFC  
 Knihovna MFC poskytuje třídy a funkce pro detekci paměti, která je přidělena, ale nikdy navrácena.  
  
###  <a name="BKMK_Tracking_memory_allocations"></a> Sledování přidělení paměti  
 V knihovně MFC, můžete použít makra [DEBUG_NEW](http://msdn.microsoft.com/library/9b379344-4093-4bec-a3eb-e0d8a63ada9d) místo **nové** nevracení operátor pro usnadnění vyhledání paměti. Verze ladění programu `DEBUG_NEW` uchovává informace o číslo, pro každý objekt, který přiděluje název a řádek souboru. Při kompilaci verze vydání aplikace, `DEBUG_NEW` přeloží na jednoduchý **nové** operaci bez souboru název a informace čísla řádku. Tedy platit žádné snížení rychlosti ve vydané verzi programu.  
  
 Pokud nechcete přepsat celý váš program používat `DEBUG_NEW` místo **nové**, můžete definovat toto makro ve zdrojových souborech:  
  
```  
#define new DEBUG_NEW  
```  
  
 Když to uděláte [s výpisem paměti objektu](#BKMK_Taking_object_dumps), každého objektu přidělena pomocí `DEBUG_NEW` se zobrazí souboru a číslo řádku, kde byl přidělen, umožňující identifikaci zdrojů nevracení paměti.  
  
 Ladicí verze rozhraní MFC používá `DEBUG_NEW` automaticky, ale nikoli kódu. Pokud chcete, aby výhody `DEBUG_NEW`, je nutné použít `DEBUG_NEW` explicitně nebo **#define nový** jak je znázorněno výše.  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Enabling_memory_diagnostics"></a> Povolení diagnostiky paměti  
 Před použitím zařízení diagnostiky paměti, je nutné povolit diagnostické trasování.  
  
 **K povolení nebo zakázání Diagnostika paměti**  
  
- Volání funkce globální [afxenablememorytracking –](http://msdn.microsoft.com/library/0a40e0c4-855d-46e2-9577-a8f2346f47db) k zapnutí nebo vypnutí diagnostiky paměti alokátoru. Protože Diagnostika paměti jsou standardně povoleny v knihovně ladění, budete obvykle používat této funkce dočasně vypnout, což zvyšuje rychlost provádění programu a snižuje diagnostický výstup.  
  
  **Chcete-li vybrat konkrétní paměti diagnostické funkce s afxmemdf –**  
  
- Pokud chcete přesnější kontrolu nad paměti diagnostické funkce, můžete selektivně zapnout diagnostické funkce jednotlivých paměti zapnout a vypnout tak, že nastavíte hodnotu globální proměnné knihovny MFC [afxmemdf –](http://msdn.microsoft.com/library/cf117501-5446-4fce-81b3-f7194bc95086). Tato proměnná může mít následující hodnoty podle specifikace výčtového typu **afxmemdf –**.  
  
  |Hodnota|Popis|  
  |-----------|-----------------|  
  |**allocmemdf –**|Zapněte diagnostiku paměti alokátoru (výchozí).|  
  |**delayFreeMemDF**|Zpoždění uvolnění paměti při volání metody `delete` nebo `free` až do ukončení programu. To způsobí, že program k přidělení maximální množství paměti.|  
  |**checkAlwaysMemDF**|Volání [afxcheckmemory –](http://msdn.microsoft.com/library/4644da71-7d14-41dc-adc0-ee9558fd7a28) pokaždé, když je paměť přidělena nebo uvolněna.|  
  
   Tyto hodnoty můžete použít v kombinaci pomocí provádí operace logického operátoru OR, jak je znázorněno zde:  
  
  ```cpp  
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;  
  ```  
  
  [V tomto tématu](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Taking_memory_snapshots"></a> Pořizování snímků paměti  
  
1. Vytvoření [cmemorystate –](http://msdn.microsoft.com/en-us/8fade6e9-c6fb-4b2a-8565-184a912d26d2) objektu a volání [CMemoryState::Checkpoint](http://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a) členskou funkci. Tím se vytvoří první snímek paměti.  
  
2. Poté, co váš program provede jeho operace přidělování a navracení zpět paměti, vytvořte další `CMemoryState` objektu a volání `Checkpoint` pro daný objekt. Načte druhý snímek využití paměti.  
  
3. Vytvořte třetí `CMemoryState` objektu a volání jeho [CMemoryState::Difference](http://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) členská funkce, jako argumenty zadání předchozích dvou `CMemoryState` objekty. Pokud je rozdíl mezi dvěma stavy paměti, `Difference` funkce vrátí nenulovou hodnotu. To znamená, že, které dosud bylo zrušeno některé bloky paměti.  
  
    Tento příklad ukazuje, jak kód funguje:  
  
   ```  
   // Declare the variables needed  
   #ifdef _DEBUG  
       CMemoryState oldMemState, newMemState, diffMemState;  
       oldMemState.Checkpoint();  
   #endif  
  
       // Do your memory allocations and deallocations.  
       CString s("This is a frame variable");  
       // The next object is a heap object.  
      CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
  
   #ifdef _DEBUG  
       newMemState.Checkpoint();  
       if( diffMemState.Difference( oldMemState, newMemState ) )  
       {  
           TRACE( "Memory leaked!\n" );  
       }  
   #endif  
   ```  
  
    Všimněte si, že se výpisy paměti kontrola uváděn v závorkách `#ifdef` [_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a)/ **#endif** blokuje tak, aby se kompilují pouze v ladicí verze aplikace.  
  
    Teď, když víte, existuje nevracení paměti, můžete použít jiné členské funkce [CMemoryState::DumpStatistics](http://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) , který vám pomůže ho najít.  
  
   [V tomto tématu](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Viewing_memory_statistics"></a> Statistika paměti zobrazení  
 [CMemoryState::Difference](http://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) funkce zkoumá dva objekty stavu paměti a zjišťuje všechny objekty není zrušeno přidělení haldy mezi stavy začátek a konec. Poté, co jste pořídili snímky paměti a jejich porovnání pomocí `CMemoryState::Difference`, můžete volat [CMemoryState::DumpStatistics](http://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) zobrazíte informace o objektech, které dosud bylo zrušeno.  
  
 Vezměte v úvahu v následujícím příkladu:  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpStatistics();  
}  
```  
  
 Ukázka výpis paměti jako v příkladu vypadá takto:  
  
```  
0 bytes in 0 Free Blocks  
22 bytes in 1 Object Blocks  
45 bytes in 4 Non-Object Blocks  
Largest number used: 67 bytes  
Total allocations: 67 bytes  
```  
  
 Bezplatné bloky jsou bloky, jehož zrušení přidělení je zpožděno. Pokud `afxMemDF` byl nastaven na `delayFreeMemDF`.  
  
 Běžné objekt bloky, zobrazí na druhém řádku zůstanou přidělené na haldě.  
  
 Bloky non-object zahrnout pole a struktury alokována `new`. V tomto případě byla čtyři bloky neobjektové přidělený k haldě, ale není uvolněný.  
  
 `Largest number used` poskytuje maximální velikost paměti používá tento program v každém okamžiku.  
  
 `Total allocations` poskytuje celkový objem paměti používá tento program.  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Taking_object_dumps"></a> Vypíše aktuální objekt  
 V aplikaci knihovny MFC můžete použít [CMemoryState::DumpAllObjectsSince](http://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) pro výpis popis všech objektů na haldě, které dosud bylo zrušeno. `DumpAllObjectsSince` Vypíše všechny objekty přidělené od minulého [CMemoryState::Checkpoint](http://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a). Pokud ne `Checkpoint` volání proběhla, `DumpAllObjectsSince` vypíše všechny objekty a nonobjects aktuálně v paměti.  
  
> [!NOTE]
>  Před použitím výpis objektu knihovny MFC, je nutné [povolit diagnostické trasování](../debugger/mfc-debugging-techniques.md#BKMK_Enabling_Memory_Diagnostics).  
  
> [!NOTE]
>  MFC automaticky vypíše všechny uniklé objekty při ukončení programu, takže není potřeba vytvořit kód pro výpis objekty v daném okamžiku.  
  
 Následující kód testy pro nevracení paměti porovnáním dvou stavů – stav paměti a vypíše všechny objekty, pokud se zjistí nevracení.  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpAllObjectsSince();  
}  
```  
  
 Obsah výpis vypadat nějak takto:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Čísla ve složených závorkách na začátku většina řádků určit pořadí, ve kterém byly přiděleny objekty. Poslední přidělený objekt s nejvyšším číslem a zobrazí se v horní části výpisu paměti.  
  
 Chcete-li získat maximální množství informací z výpisu paměti objektu, můžete přepsat `Dump` členskou funkci žádné `CObject`-odvozenému objektu k přizpůsobení objektu s výpisem paměti.  
  
 Nastavením globální proměnné můžete nastavit zarážku na přidělení paměti konkrétní `_afxBreakAlloc` na číslo zobrazené ve složených závorkách. Pokud znovu spustíte program ladicí program přeruší provádění, místo pořízením toto rozdělení. Pak můžete zobrazit zásobník volání a podívat, jak se váš program máte do tohoto bodu.  
  
 Knihovny run-time jazyka C má podobnou funkci [_CrtSetBreakAlloc](http://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1), můžete použít pro přidělení C za běhu.  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
####  <a name="BKMK_Interpreting_memory_dumps"></a> Interpretace paměti výpisy stavu systému  
 Podívejte se na tento objekt výpis podrobněji:  
  
```  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Program, který vygeneroval tento výpis paměti má jenom dvě explicitní přidělení – jeden na zásobníku a jeden na haldě:  
  
```  
// Do your memory allocations and deallocations.  
CString s("This is a frame variable");  
// The next object is a heap object.  
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
```  
  
 `CPerson` Konstruktor má tři argumenty, které jsou ukazatele na `char`, které se používají k inicializaci `CString` členské proměnné. Ve výpisu stavu paměti, zobrazí se `CPerson` objekt spolu s tří bloků nonobject (3, 4 a 5). Tyto znaky pro uložení `CString` členské proměnné a nebudou odstraněny, když `CPerson` destruktor objektu je vyvolán.  
  
 Blok číslo 2 je `CPerson` samotného objektu. `$51A4` představuje adresu bloku a je následována obsah objektu, který byl výstupem `CPerson`::`Dump` když se zavolá pomocí [DumpAllObjectsSince](http://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2).  
  
 Můžete provést odhad, že je přidružený blok číslo 1 `CString` proměnné rámce z důvodu jeho pořadové číslo a velikost, která odpovídá počtu znaků v rámci `CString` proměnné. Proměnné, které jsou přiděleny v rámci počítače automaticky uvolní když rámec dostane mimo rozsah.  
  
 **Proměnné rámce**  
  
 Obecně platí by neměla starat o haldy objekty přidružené k proměnné rámce, protože jsou automaticky uvolní při proměnné rámce dostanou mimo rozsah. Aby se zabránilo nepořádku v vaše diagnostická výpisy paměti, by měl umístit vaše volání `Checkpoint` tak, aby byly mimo rozsah proměnné rámce. Například umístíte oboru závorky okolo kódu, předchozí přidělení, jak je znázorněno zde:  
  
```  
oldMemState.Checkpoint();  
{  
    // Do your memory allocations and deallocations ...  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
}  
newMemState.Checkpoint();  
```  
  
 Do závorek obor na místě je výpis paměti v tomto příkladu:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
```  
  
 **Nonobject přidělení**  
  
 Všimněte si, že některé přidělení objektů (například `CPerson`) a některé jsou nonobject přidělení. "Nonobject přidělení" jsou přidělení pro objekty není odvozeno od `CObject` nebo přidělení primitivních typů jazyka C, jako například `char`, `int`, nebo **dlouhé**. Pokud **CObject -** odvozené třídy přiděluje další místo, například pro vnitřní vyrovnávací paměti, se zobrazí tyto objekty objektu a nonobject přidělení.  
  
 **Prevence úniků paměti**  
  
 Všimněte si, že ve výše uvedeném kódu, že přidružený blok paměti `CString` proměnné rámce bylo zrušeno automaticky a není uveden jako nenavrácení paměti. Automatické zrušení přidělení související s pravidel oboru se postará o většině nevracení paměti, které jsou přidružené k proměnné rámce.  
  
 U objektů přidělených do ale je nutné explicitně odstranit objekt, aby se zabránilo nevrácení paměti. Chcete-li vyčistit poslední nevracení paměti v předchozím příkladu, odstraňte `CPerson` objekt přidělený do haldy, následujícím způsobem:  
  
```  
{  
    // Do your memory allocations and deallocations.  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
    delete p;  
}  
```  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
####  <a name="BKMK_Customizing_object_dumps"></a> Vypíše přizpůsobení objektu  
 Pokud odvodíte třídu od [CObject](http://msdn.microsoft.com/library/95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a), můžete přepsat `Dump` členskou funkci na další informace při použití [DumpAllObjectsSince](http://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) na objekty s výpisem paměti pro [Okno výstup](../ide/reference/output-window.md).  
  
 `Dump` Funkce zapíše textovou reprezentaci řetězce objektu členské proměnné do kontextu s výpisem paměti ([CDumpContext](http://msdn.microsoft.com/library/98c52b2d-14b5-48ed-b423-479a4d1c60fa)). Kontext s výpisem paměti je podobný datovému proudu vstupně-výstupních operací. Můžete použít operátor, který připojení (**<<**) k odesílání dat do `CDumpContext`.  
  
 Při přepsání `Dump` funkce, měli byste nejprve zavolat základní třídu verzi `Dump` Vypsat obsah objektu základní třídy. Potom výstupní textový popis a hodnotu pro každou proměnnou člena odvozené třídy.  
  
 Deklarace `Dump` funkce vypadá takto:  
  
```  
class CPerson : public CObject  
{  
public:  
#ifdef _DEBUG  
    virtual void Dump( CDumpContext& dc ) const;  
#endif  
  
    CString m_firstName;  
    CString m_lastName;  
    // And so on...  
};  
```  
  
 Vzhledem k tomu, že výpis objektu má smysl jenom při ladění programu, deklarace `Dump` funkce je uváděn s **#ifdef _DEBUG / #endif** bloku.  
  
 V následujícím příkladu `Dump` první volání funkce `Dump` funkce pro její základní třídě. Stručný popis jednotlivých členskou proměnnou spolu s hodnotu člena s hodnotou pak zapíše do streamu diagnostiky.  
  
```  
#ifdef _DEBUG  
void CPerson::Dump( CDumpContext& dc ) const  
{  
    // Call the base class function first.  
    CObject::Dump( dc );  
  
    // Now do the stuff for our specific class.  
    dc << "last name: " << m_lastName << "\n"  
        << "first name: " << m_firstName << "\n";  
}  
#endif  
```  
  
 Je nutné zadat `CDumpContext` argument pro určení, kam se obrátit výstup výpisu stavu systému. Ladicí verze knihovny MFC poskytuje i předdefinovanou `CDumpContext` objekt s názvem `afxDump` , který odesílá výstup do ladicího programu.  
  
```  
CPerson* pMyPerson = new CPerson;  
// Set some fields of the CPerson object.  
//...  
// Now dump the contents.  
#ifdef _DEBUG  
pMyPerson->Dump( afxDump );  
#endif  
```  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Zmenšení velikosti knihovny MFC ladění sestavení  
 Informace o ladění pro rozsáhlé aplikace knihovny MFC může trvat až velké množství místa na disku. Jeden z následujících postupů můžete použít ke zmenšení velikosti:  
  
1. Znovu sestavit pomocí knihovny MFC [/Z7, / zi, /ZI (formát informací o ladění)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) možnost, namísto **/Z7**. Tyto možnosti vytvoření souboru databáze (PDB) jednoduchý program, který obsahuje informace o ladění pro celou knihovnu, snižují redundanci a úspora místa.  
  
2. Opětovné sestavení knihovny MFC bez ladicích informací (žádné [/Z7, / zi, /ZI (formát informací o ladění)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) možnost). V takovém případě chybějící informace o ladění zabrání pomocí většina funkcí ladicího programu v rámci kódu knihovny MFC, ale protože knihovny MFC jsou již důkladně ladit, nemusí to být problém.  
  
3. Vytvoření vlastní aplikace s ladicími informacemi pro vybrané moduly pouze, jak je popsáno níže.  
  
   [V tomto tématu](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Vytvoření aplikace knihovny MFC s ladicími informacemi pro vybrané moduly  
 Vytváření vybrané moduly s knihovnami MFC ladění umožňuje používat krokování a jiných ladění zařízení v těchto modulech. Tento postup využívá i ladění a vydání režimy Visual C++ makefile, tedy vyžadovala změny podle následujících kroků (a také provedete "sestavit vše znovu" nezbytné, pokud je nutné použít úplné sestavení pro vydání).  
  
1. V Průzkumníku řešení vyberte projekt.  
  
2. Z **zobrazení** nabídce vyberte možnost **stránky vlastností**.  
  
3. Nejprve vytvoříte novou konfiguraci projektu.  
  
   1.  V  **\<Projekt > stránky vlastností** dialogové okno, klikněte na tlačítko **nástroje Configuration Manager** tlačítko.  
  
   2.  V [dialogové okno nástroje Configuration Manager](http://msdn.microsoft.com/en-us/fa182dca-282e-4ae5-bf37-e155344ca18b), vyhledejte svůj projekt v mřížce. V **konfigurace** sloupci vyberte  **\<nový … >**.  
  
   3.  V [dialogové okno Nový projekt konfigurace](http://msdn.microsoft.com/en-us/cca616dc-05a6-4fe3-bdc1-40c72a66f2be), zadejte název pro novou konfiguraci, jako je například "Částečné Debug", **název konfigurace projektu** pole.  
  
   4.  V **Kopírovat nastavení z** klikněte na položku **vydání**.  
  
   5.  Klikněte na tlačítko **OK** zavřete **nové konfigurace projektu**dialogové okno.  
  
   6.  Zavřít **nástroje Configuration Manager** dialogové okno.  
  
4. Nyní nastavíte možnosti pro celý projekt.  
  
   1.  V **stránky vlastností** dialogovém okně **vlastnosti konfigurace** složky, vyberte **Obecné** kategorie.  
  
   2.  V mřížce nastavení projektu rozbalte **výchozí nastavení projektu** (v případě potřeby).  
  
   3.  V části **výchozí nastavení projektu**, Najít **použít knihovnu MFC**. V pravém sloupci mřížky se zobrazí aktuální nastavení. Klikněte na aktuální nastavení a změňte ji na **použít knihovnu MFC ve statické knihovně**.  
  
   4.  V levém podokně **stránky vlastností** dialogovém okně Otevřít **C/C++** a pak zvolte položku **preprocesor**. V mřížce vlastností najít **Definice preprocesoru** a nahradit "NDEBUG" s "_DEBUG".  
  
   5.  V levém podokně **stránky vlastností** dialogovém okně Otevřít **Linkeru** a pak zvolte položku **vstup** kategorie. V mřížce vlastností najít **Další závislosti**. V **Další závislosti** nastavení, zadejte "NAFXCWD. LIB"a"Knihovny runtime LIBCMT."  
  
   6.  Klikněte na tlačítko **OK** nové možnosti sestavení uložte a zavřete **stránky vlastností** dialogové okno.  
  
5. Z **sestavení** nabídce vyberte možnost **znovu sestavit**. Odebere všechny informace o ladění z modulů, ale nemá vliv na knihovně MFC.  
  
6. Teď musíte přidat informace o ladění zpět do vybrané moduly ve vaší aplikaci. Mějte na paměti, že můžete nastavit zarážky a provádět jiné funkce ladicího programu pouze v modulech, které jste zkompilovali s ladicími informacemi. Pro každý soubor projektu, ve které chcete zahrnout informace o ladění, proveďte následující kroky:  
  
   1.  V Průzkumníku řešení otevřete **zdrojové soubory** složky umístěna ve složce projektu.  
  
   2.  Vyberte soubor, který chcete nastavit informace o ladění.  
  
   3.  Z **zobrazení** nabídce vyberte možnost **stránky vlastností**.  
  
   4.  V **stránky vlastností** dialogovém okně **nastavení konfigurace** složku, otevřete **C/C++** vyberte složku **Obecné** kategorie.  
  
   5.  V mřížce vlastností najít **formát informací o ladění.**  
  
   6.  Klikněte na tlačítko **formát informací o ladění** nastavení a vyberte požadovanou možnost (obvykle **/zi**) pro ladicí informace.  
  
   7.  Pokud používáte aplikace vygenerované průvodcem aplikací nebo mít předkompilované hlavičky, budete muset nebo vypnout předkompilovaných hlaviček zkompilujte je znovu před kompilací ostatní moduly. Jinak zobrazí se upozornění C4650 a chybovou zprávou C2855. Předkompilované hlavičky můžete vypnout tak, že změníte **vytvořit/použít předkompilovanou hlavičku** nastavení  **\<projektu > vlastnosti** dialogové okno (**vlastnosti konfigurace**  složce **C/C++** podsložku, **předkompilované hlavičky** kategorie).  
  
7. Z **sestavení** nabídce vyberte možnost **sestavení** k opětovnému sestavení soubory projektu, které jsou zastaralé.  
  
   Jako alternativu ke techniky popsané v tomto tématu, můžete zadat jednotlivé možnosti pro každý soubor externí soubor pravidel. Pokud chcete propojit s knihovnami MFC ladění, v takovém případě musíte definovat [_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) příznak pro každý modul. Pokud chcete používat verzi knihovny MFC, je nutné definovat NDEBUG. Další informace o psaní externí soubory pravidel najdete v článku [NMake – odkaz](http://msdn.microsoft.com/library/0421104d-8b7b-4bf3-86c1-928d9b7c1a8c).  
  
   [V tomto tématu](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Viz také  
 [Ladění jazyka Visual C++](../debugger/debugging-native-code.md)



