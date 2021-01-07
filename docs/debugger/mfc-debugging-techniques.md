---
title: Techniky ladění MFC | Microsoft Docs
description: 'Naučte se naučit ladit programy MFC, včetně: kódované zarážky, trasování, detekce nevracení paměti, výpisů paměti objektů a zmenšení velikosti programu.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5cf00191aff408b1133c281e10eea17e3a923215
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975118"
---
# <a name="mfc-debugging-techniques"></a>Techniky ladění MFC
Při ladění programu knihovny MFC mohou být tyto techniky ladění užitečné.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> V tomto tématu
[AfxDebugBreak](#BKMK_AfxDebugBreak)

[Makro TRACE](#BKMK_The_TRACE_macro)

[Zjišťování nevracení paměti v knihovně MFC](#BKMK_Memory_leak_detection_in_MFC)

- [Sledování přidělení paměti](#BKMK_Tracking_memory_allocations)

- [Povolení diagnostiky paměti](#BKMK_Enabling_memory_diagnostics)

- [Pořizování snímků paměti](#BKMK_Taking_memory_snapshots)

- [Zobrazení statistiky paměti](#BKMK_Viewing_memory_statistics)

- [Pořizování výpisů objektů](#BKMK_Taking_object_dumps)

  - [Interpretace výpisů paměti](#BKMK_Interpreting_memory_dumps)

  - [Přizpůsobení výpisů objektů](#BKMK_Customizing_object_dumps)

  - [Zmenšení velikosti sestavení ladění knihovny MFC](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)

  - [Sestavování aplikace MFC s ladicími informacemi pro vybrané moduly](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)

## <a name="afxdebugbreak"></a><a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak
Knihovna MFC poskytuje speciální funkci [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) pro zarážky s pevným kódováním ve zdrojovém kódu:

```cpp
AfxDebugBreak( );
```

Na platformách Intel `AfxDebugBreak` vytvoří následující kód, který přeruší ve zdrojovém kódu místo kódu jádra:

```cpp
_asm int 3
```

Na jiných platformách `AfxDebugBreak` pouze volá `DebugBreak` .

Nezapomeňte odebrat `AfxDebugBreak` příkazy při vytváření sestavení pro vydání nebo k jeho obnově použijte `#ifdef _DEBUG` .

[V tomto tématu](#BKMK_In_this_topic)

## <a name="the-trace-macro"></a><a name="BKMK_The_TRACE_macro"></a> Makro TRACE
Chcete-li zobrazit zprávy z programu v [okně výstupu](../ide/reference/output-window.md)ladicího programu, můžete použít makro [ATLTRACE](/previous-versions/6xkxyz08(v=vs.140)) nebo makro [Trace](/previous-versions/6w95a4ha(v=vs.140)) MFC. Podobně jako [kontrolní výrazy](../debugger/c-cpp-assertions.md)jsou makra trasování aktivní pouze v ladicí verzi programu a zmizí při kompilování ve vydané verzi.

Následující příklady znázorňují některé způsoby, jak můžete použít makro **Trace** . Například `printf` makro **Trace** může zpracovat určitý počet argumentů.

```cpp
int x = 1;
int y = 16;
float z = 32.0;
TRACE( "This is a TRACE statement\n" );

TRACE( "The value of x is %d\n", x );

TRACE( "x = %d and y = %d\n", x, y );

TRACE( "x = %d and y = %x and z = %f\n", x, y, z );
```

Makro TRACE vhodným způsobem zpracovává \* parametry char a wchar_t \* . Následující příklady ukazují použití SLEDOVACÍho makra spolu s různými typy řetězcových parametrů.

```cpp
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);

TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);

TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);
```

Další informace o makru **trasování** naleznete v tématu [diagnostické služby](/cpp/mfc/reference/diagnostic-services).

[V tomto tématu](#BKMK_In_this_topic)

## <a name="detecting-memory-leaks-in-mfc"></a><a name="BKMK_Memory_leak_detection_in_MFC"></a> Zjišťování nevracení paměti v knihovně MFC
Knihovna MFC poskytuje třídy a funkce pro zjišťování paměti, která je přidělena, ale nikdy neuvolněna.

### <a name="tracking-memory-allocations"></a><a name="BKMK_Tracking_memory_allocations"></a> Sledování přidělení paměti
V knihovně MFC můžete použít makro [DEBUG_NEW](/previous-versions/tz7sxz99(v=vs.140)) místo operátoru **New** , které vám pomůžou najít nevracení paměti. V ladicí verzi programu `DEBUG_NEW` uchovává záznam o názvu souboru a čísle řádku pro každý objekt, který přiděluje. Při kompilaci verze pro vydání programu se `DEBUG_NEW` přeloží na jednoduchou **novou** operaci bez názvu souboru a čísla řádku. Proto platíte bez snížení rychlosti v prodejní verzi programu.

Pokud nechcete přepsat celý program pro použití `DEBUG_NEW` místo **nového**, můžete toto makro definovat ve zdrojových souborech:

```cpp
#define new DEBUG_NEW
```

Když provedete [Výpis objektu](#BKMK_Taking_object_dumps), každý objekt přidělený pomocí zobrazí `DEBUG_NEW` soubor a číslo řádku, kde byl přidělen, což vám umožní určit zdroje nevracení paměti.

Ladicí verze rozhraní knihovny MFC používá program `DEBUG_NEW` automaticky, ale váš kód nikoli. Pokud chcete využít výhod, je `DEBUG_NEW` nutné použít `DEBUG_NEW` explicitně nebo **#define nové** , jak je uvedeno výše.

[V tomto tématu](#BKMK_In_this_topic)

### <a name="enabling-memory-diagnostics"></a><a name="BKMK_Enabling_memory_diagnostics"></a> Povolení diagnostiky paměti
Předtím, než budete moci použít funkce diagnostiky paměti, je nutné povolit trasování diagnostiky.

**Povolení nebo zakázání diagnostiky paměti**

- Pokud chcete povolit nebo zakázat přidělování diagnostických paměti, zavolejte globální funkci [AfxEnableMemoryTracking](/previous-versions/hzsxb6e8(v=vs.140)) . Vzhledem k tomu, že Diagnostika paměti je ve výchozím nastavení zapnuta v knihovně ladění, tato funkce se obvykle používá k jejich dočasnému vypnutí, což zvyšuje rychlost spuštění programu a snižuje výstup diagnostiky.

  **Výběr specifických funkcí diagnostiky paměti pomocí afxMemDF**

- Pokud potřebujete přesnější kontrolu nad funkcemi diagnostiky paměti, můžete selektivně zapnout a vypnout jednotlivé funkce diagnostiky paměti nastavením hodnoty globální proměnné [afxMemDF](/previous-versions/ahe4a83t(v=vs.140))knihovny MFC. Tato proměnná může mít následující hodnoty určené výčtovým typem **afxMemDF**.

  |Hodnota|Popis|
  |-----------|-----------------|
  |**allocMemDF**|Zapněte funkci přidělování diagnostických paměti (výchozí).|
  |**delayFreeMemDF**|Zpoždění uvolnění paměti při volání `delete` nebo `free` ukončení programu. Tím dojde k tomu, že program přidělí maximální možnou velikost paměti.|
  |**checkAlwaysMemDF**|Zavolejte [AfxCheckMemory](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) při každém přidělení nebo uvolnění paměti.|

  Tyto hodnoty lze použít v kombinaci pomocí logického typu nebo operace, jak je znázorněno zde:

  ```C++
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;
  ```

  [V tomto tématu](#BKMK_In_this_topic)

### <a name="taking-memory-snapshots"></a><a name="BKMK_Taking_memory_snapshots"></a> Pořizování snímků paměti

1. Vytvořte objekt [CMemoryState](/previous-versions/visualstudio/visual-studio-2010/2ads32e2(v=vs.100)) a zavolejte členskou funkci [CMemoryState:: Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint) . Tím se vytvoří první snímek paměti.

2. Poté, co program provede operaci přidělení paměti a zrušení přidělení, vytvořte další `CMemoryState` objekt a zavolejte `Checkpoint` pro daný objekt. Tím se získá druhý snímek využití paměti.

3. Vytvořte třetí `CMemoryState` objekt a zavolejte jeho členskou funkci [CMemoryState::D ifference](/cpp/mfc/reference/cmemorystate-structure#difference) a poskytněte jako argumenty dva předchozí `CMemoryState` objekty. Pokud existuje rozdíl mezi dvěma stavy paměti, `Difference` funkce vrátí nenulovou hodnotu. To znamená, že některé bloky paměti nebyly navráceny.

    Tento příklad ukazuje, jak kód vypadá takto:

    ```cpp
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

    Všimněte si, že příkazy pro kontrolu paměti jsou v závorkách **#ifdef _DEBUG/#endif** bloky, aby byly kompilovány pouze ve verzi programu pro ladění.

    Když teď víte, že existuje nevrácená paměť, můžete použít jinou členskou funkci [CMemoryState::D umpstatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) , která vám pomůže ji najít.

    [V tomto tématu](#BKMK_In_this_topic)

### <a name="viewing-memory-statistics"></a><a name="BKMK_Viewing_memory_statistics"></a> Zobrazení statistiky paměti
Funkce [CMemoryState::D ifference](/cpp/mfc/reference/cmemorystate-structure#difference) prohledává dva objekty stavu paměti a detekuje všechny objekty, které nejsou navráceny z haldy mezi počátečním a koncovým stavem. Po pořízení snímků paměti a jejich porovnání pomocí `CMemoryState::Difference` můžete zavolat [CMemoryState::D umpstatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) a získat informace o objektech, které nebyly uvolněny.

Uvažujte následující příklad:

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpStatistics();
}
```

Ukázkový výpis z příkladu vypadá takto:

```cpp
0 bytes in 0 Free Blocks
22 bytes in 1 Object Blocks
45 bytes in 4 Non-Object Blocks
Largest number used: 67 bytes
Total allocations: 67 bytes
```

Bezplatné bloky jsou bloky, jejichž zrušení přidělení je zpožděno, pokud `afxMemDF` bylo nastaveno na `delayFreeMemDF` .

Běžné bloky objektů, zobrazené na druhém řádku, zůstávají přiděleny na haldě.

Bloky bez objektu obsahují pole a struktury přidělené s `new` . V tomto případě byly na haldě přiděleny čtyři bloky bez objektu Object, ale nejsou navráceny.

`Largest number used` poskytuje v každém okamžiku maximální velikost paměti, kterou program používá.

`Total allocations` poskytne celkové množství paměti používané programem.

[V tomto tématu](#BKMK_In_this_topic)

### <a name="taking-object-dumps"></a><a name="BKMK_Taking_object_dumps"></a> Pořizování výpisů objektů
V programu knihovny MFC lze pomocí [CMemoryState::D umpallobjectssince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) vypsat popis všech objektů v haldě, která nebyla uvolněna. `DumpAllObjectsSince` Vypíše všechny objekty přidělené od posledního [CMemoryState:: Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint). Pokud není `Checkpoint` provedeno žádné volání, `DumpAllObjectsSince` vypíše všechny objekty a neobjekty, které jsou aktuálně v paměti.

> [!NOTE]
> Než budete moci použít výpis objektu knihovny MFC, je nutné [Povolit trasování diagnostiky](#BKMK_Enabling_memory_diagnostics).

> [!NOTE]
> MFC při ukončení programu automaticky vypíše všechny nevrácené objekty, takže nemusíte vytvářet kód pro výpis objektů v tomto okamžiku.

Následující testy kódu pro nevracení paměti porovnáním dvou stavů paměti a vypíše všechny objekty, pokud je zjištěna nevracení.

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpAllObjectsSince();
}
```

Obsah výpisu paměti vypadá takto:

```cmd
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

Čísla v závorkách na začátku většiny řádků určují pořadí, ve kterém byly objekty přiděleny. Poslední přidělený objekt má nejvyšší číslo, které se zobrazí v horní části výpisu paměti.

Chcete-li získat maximální množství informací z výpisu objektu, můžete přepsat `Dump` členskou funkci libovolného `CObject` objektu odvozeného pro přizpůsobení výpisu objektu.

Můžete nastavit zarážku pro konkrétní přidělení paměti nastavením globální proměnné `_afxBreakAlloc` na číslo zobrazené v závorkách. Pokud program znovu spustíte, ladicí program přeruší provádění, když toto přidělení bude provedeno. Pak se můžete podívat na zásobník volání a zjistit, jak váš program získal daný bod.

Běhová knihovna jazyka C má podobnou funkci, [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc), kterou lze použít pro přidělení za běhu c.

[V tomto tématu](#BKMK_In_this_topic)

#### <a name="interpreting-memory-dumps"></a><a name="BKMK_Interpreting_memory_dumps"></a> Interpretace výpisů paměti
Podívejte se na tento výpis objektu podrobněji:

```cmd
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

Program, který vygeneroval tento výpis, měl pouze dvě explicitní přidělení – jeden v zásobníku a jeden na haldě:

```cpp
// Do your memory allocations and deallocations.
CString s("This is a frame variable");
// The next object is a heap object.
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
```

`CPerson`Konstruktor přebírá tři argumenty, které jsou ukazatele na `char` , které jsou použity k inicializaci `CString` proměnných členů. V výpisu paměti můžete zobrazit `CPerson` objekt spolu se třemi bloky, které nejsou objekty (3, 4 a 5). Ty uchovávají znaky pro `CString` členské proměnné a nebudou odstraněny, pokud `CPerson` je vyvolán destruktor objektu.

Blok číslo 2 je `CPerson` samotný objekt. `$51A4` představuje adresu bloku a je následován obsahem objektu, který byl výstupem `CPerson` :: `Dump` při volání metody [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince).

Můžete odhadnout, že blok číslo 1 je přidružen k `CString` proměnné rámce z důvodu jeho pořadového čísla a velikosti, která odpovídá počtu znaků v `CString` proměnné snímku. Proměnné, které jsou přiděleny v rámci rámce, jsou automaticky uvolněny, když se rámec přechází z rozsahu.

**Proměnné snímků**

Obecně platí, že byste neměli starosti s objekty haldy přidruženými k proměnným snímků, protože jsou automaticky uvolněny, když proměnné rámce přestanou mimo rozsah. Aby nedocházelo k zbytečným výpisům paměti, měli byste umístit volání do, aby byla `Checkpoint` mimo rozsah proměnných rámce. Můžete například umístit závorky oboru kolem předchozího alokačního kódu, jak je znázorněno zde:

```cpp
oldMemState.Checkpoint();
{
    // Do your memory allocations and deallocations ...
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
}
newMemState.Checkpoint();
```

V případě, že jsou zavedeny závorky oboru, je výpis paměti pro tento příklad následující:

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215
```

**Nepřidělené objekty**

Všimněte si, že některá přidělení jsou objekty (například `CPerson` ) a některé jsou nepřidělené objekty. "Nepřidělené objekty" jsou alokace pro objekty, které nejsou odvozeny od `CObject` nebo z přidělení primitivních typů jazyka C, jako například `char` , `int` nebo `long` . Pokud třída odvozená <strong>CObject</strong>přiděluje dodatečné místo, například pro vnitřní vyrovnávací paměti, tyto objekty budou zobrazovat objekt i neobjektová přidělení.

**Prevence nevracení paměti**

V kódu výše si všimněte, že blok paměti přidružený k `CString` proměnné rámce byl uvolněn automaticky a nezobrazuje se jako nevracení paměti. Automatické zrušení přidělení přidružené k pravidlům oboru se stará o většinu nevracení paměti přidružených k proměnným rámců.

Pro objekty, které jsou přiděleny haldě, je však nutné explicitně odstranit objekt, aby nedošlo k nevrácení paměti. Chcete-li vyčistit poslední nevrácenou paměť v předchozím příkladu, odstraňte `CPerson` objekt přidělený na haldě následujícím způsobem:

```cpp
{
    // Do your memory allocations and deallocations.
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
    delete p;
}
```

[V tomto tématu](#BKMK_In_this_topic)

#### <a name="customizing-object-dumps"></a><a name="BKMK_Customizing_object_dumps"></a> Přizpůsobení výpisů objektů
Při odvozování třídy z [CObject](/cpp/mfc/reference/cobject-class)můžete přepsat `Dump` členskou funkci tak, aby poskytovala Další informace, když použijete [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) k vypsání objektů do [okna výstup](../ide/reference/output-window.md).

`Dump`Funkce zapíše textovou reprezentaci členských proměnných objektu do kontextu výpisu paměti ([CDumpContext](/cpp/mfc/reference/cdumpcontext-class)). Kontext výpisu se podobá vstupně-výstupnímu streamu. K odeslání dat do nástroje lze použít operátor Append ( **<<** ) `CDumpContext` .

Při přepsání `Dump` funkce byste nejprve měli zavolat verzi základní třídy, aby vypsala `Dump` obsah objektu základní třídy. Pak výstup textového popisu a hodnoty pro každou členskou proměnnou odvozené třídy.

Deklarace `Dump` funkce vypadá takto:

```cpp
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

Vzhledem k tomu, že výpis objektu dává smysl pouze při ladění programu, `Dump` je deklarace funkce v závorkách s **#ifdef _DEBUG/#endif** .

V následujícím příkladu `Dump` funkce nejprve volá `Dump` funkci pro svou základní třídu. Pak zapíše krátký popis každé členské proměnné spolu s hodnotou člena do diagnostického datového proudu.

```cpp
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

`CDumpContext`Chcete-li určit, kde bude výstup výpisu pokračovat, musíte zadat argument. Ladicí verze knihovny MFC poskytuje předdefinovaný `CDumpContext` objekt s názvem `afxDump` , který odesílá výstup do ladicího programu.

```cpp
CPerson* pMyPerson = new CPerson;
// Set some fields of the CPerson object.
//...
// Now dump the contents.
#ifdef _DEBUG
pMyPerson->Dump( afxDump );
#endif
```

[V tomto tématu](#BKMK_In_this_topic)

## <a name="reducing-the-size-of-an-mfc-debug-build"></a><a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Zmenšení velikosti sestavení ladění knihovny MFC
Ladicí informace pro rozsáhlou aplikaci knihovny MFC může zabírat spoustu místa na disku. K zmenšení velikosti můžete použít jeden z těchto postupů:

1. Znovu sestavte knihovny MFC pomocí možnosti [/Z7,/Zi,/Zi (formát ladicích informací)](/cpp/build/reference/z7-zi-zi-debug-information-format) místo **/Z7**. Tyto možnosti vytvoří soubor s jedním programem databáze (PDB), který obsahuje ladicí informace pro celou knihovnu, snižuje redundanci a šetří místo.

2. Znovu sestavte knihovny MFC bez ladicích informací (možnost No [/Z7,/Zi,/Zi (formát ladicích informací)](/cpp/build/reference/z7-zi-zi-debug-information-format) ). V tomto případě nedostatek ladicích informací zabrání v použití většiny funkcí ladicího programu v rámci kódu knihovny MFC, ale protože knihovny MFC jsou již důkladně laděny, nemusí se jednat o problém.

3. Sestavte vlastní aplikaci s ladicími informacemi pro vybrané moduly pouze, jak je popsáno níže.

    [V tomto tématu](#BKMK_In_this_topic)

### <a name="building-an-mfc-app-with-debug-information-for-selected-modules"></a><a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Sestavování aplikace MFC s ladicími informacemi pro vybrané moduly
Sestavování vybraných modulů pomocí ladicích knihoven knihovny MFC vám umožní v těchto modulech použít krokování a další ladicí zařízení. Tento postup využívá konfiguraci ladění a vydání projektu, takže vyžaduje změny popsané v následujících krocích (a také provedení příkazu "znovu sestavit vše" v případě potřeby kompletního sestavení pro vydání).

1. V Průzkumník řešení vyberte projekt.

2. V nabídce **zobrazení** vyberte položku **stránky vlastností**.

3. Nejprve vytvoříte novou konfiguraci projektu.

   1. V dialogovém okně **\<Project> stránky vlastností** klikněte na tlačítko **Configuration Manager** .

   2. V [dialogovém okně Configuration Manager](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100))vyhledejte v mřížce svůj projekt. Ve sloupci **Konfigurace** vyberte **\<New...>** .

   3. V [dialogovém okně Nová konfigurace projektu](/previous-versions/visualstudio/visual-studio-2010/0eh8w4cf(v=vs.100))zadejte název nové konfigurace, například "částečný ladění", do pole **název konfigurace projektu** .

   4. V seznamu **Kopírovat nastavení ze** vyberte možnost **verze**.

   5. Kliknutím na tlačítko **OK** zavřete dialogové okno **Konfigurace nového projektu** .

   6. Zavřete dialogové okno **Configuration Manager** .

4. Nyní budete nastavovat možnosti pro celý projekt.

   1. V dialogovém okně **stránky vlastností** ve složce **Vlastnosti konfigurace** vyberte kategorii **Obecné** .

   2. V mřížce nastavení projektu rozbalte položku **výchozí hodnoty projektu** (v případě potřeby).

   3. V části **výchozí nastavení projektu** Najděte **použití knihovny MFC**. Aktuální nastavení se zobrazí v pravém sloupci mřížky. Klikněte na aktuální nastavení a změňte jej tak, aby **používalo knihovnu MFC ve statické knihovně**.

   4. V levém podokně dialogového okna **stránky vlastností** otevřete složku **C/C++** a vyberte **preprocesor**. V mřížce Properties (vlastnosti) Najděte **Definice preprocesoru** a nahraďte "NDEBUG" pomocí "_DEBUG".

   5. V levém podokně dialogového okna **stránky vlastností** otevřete složku **linker** a vyberte **vstupní** kategorii. V mřížce Properties (vlastnosti) Najděte **Další závislosti**. V nastavení **Další závislosti** zadejte "NAFXCWD". LIB "a" LIBCMT ".

   6. Kliknutím na tlačítko **OK** uložte nové možnosti sestavení a zavřete dialogové okno **stránky vlastností** .

5. V nabídce **sestavení** vyberte znovu **sestavit**. Tím dojde k odebrání všech informací o ladění z modulů, ale nemá vliv na knihovnu knihovny MFC.

6. Nyní je nutné přidat ladicí informace zpět do vybraných modulů v aplikaci. Mějte na paměti, že můžete nastavit zarážky a provádět další funkce ladicího programu pouze v modulech, které jste shromáždili pomocí ladicích informací. Pro každý soubor projektu, do kterého chcete zahrnout informace o ladění, proveďte následující kroky:

   1. V Průzkumník řešení otevřete složku **zdrojové soubory** nacházející se v projektu.

   2. Vyberte soubor, pro který chcete nastavit informace o ladění.

   3. V nabídce **zobrazení** vyberte položku **stránky vlastností**.

   4. V dialogovém okně **stránky vlastností** otevřete ve složce **nastavení konfigurace** složku **C/C++** a pak vyberte kategorii **Obecné** .

   5. V mřížce vlastnosti vyhledejte **Formát ladicí informace.**

   6. Klikněte na nastavení **formátu ladicí informace** a vyberte požadovanou možnost (obvykle **/Zi**) pro informace o ladění.

   7. Pokud používáte aplikaci generovanou průvodcem aplikací nebo pokud mají předkompilované hlavičky, je nutné před kompilací dalších modulů vypnout předkompilovaných hlaviček nebo je znovu zkompilovat. V opačném případě se zobrazí upozornění C4650 a chybová zpráva C2855. Předkompilované hlavičky můžete vypnout tak, že změníte nastavení **předkompilovanách hlaviček vytvořit/použít** v dialogovém okně **\<Project> vlastnosti** (složka **Vlastnosti konfigurace** , podsložka **C/C++** , kategorie **předkompilovaných hlaviček** ).

7. V nabídce **sestavení** vyberte **sestavení** a znovu sestavte soubory projektu, které nejsou aktuální.

   Jako alternativu k techniky popsané v tomto tématu můžete použít externí soubor pravidel pro definování jednotlivých možností pro jednotlivé soubory. V takovém případě pro propojení s knihovnami ladění knihovny MFC je nutné definovat příznak [_DEBUG](/cpp/c-runtime-library/debug) pro každý modul. Pokud chcete použít knihovny verzí knihovny MFC, je nutné definovat NDEBUG. Další informace o zápisu externích souborů pravidel naleznete v [referenci NMAKE](/cpp/build/running-nmake).

   [V tomto tématu](#BKMK_In_this_topic)

## <a name="see-also"></a>Viz také
[Ladění nativního kódu](../debugger/debugging-native-code.md)