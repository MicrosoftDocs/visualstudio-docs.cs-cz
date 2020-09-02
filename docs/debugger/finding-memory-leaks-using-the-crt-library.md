---
title: Vyhledání nevrácené paměti pomocí knihovny CRT | Microsoft Docs
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5deb42b2ab708bae572aebbcac15af2d077b14fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350482"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Hledání nevrácené paměti pomocí knihovny CRT

Nevracení paměti je v aplikacích C/C++ z nejvýraznějšího a obtížného zjišťování chyb. Nevracení paměti vedlo k selhání při správném uvolnění paměti, která byla dříve přidělena. Je možné, že se neprojeví nevracení paměti, ale v průběhu času může docházet ke zhroucení příznaků od špatného výkonu po selhání aplikace v případě, že dojde k nedostatku paměti. Nevrácení aplikace, která používá veškerou dostupnou paměť, může způsobit zhroucení jiných aplikací a nejasnosti, jakou zodpovídá aplikace. Dokonce neškodné neškodné nevracení paměti může poukazovat na další problémy, které by se měly opravit.

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Ladicí program a Knihovna CRT (C Run-Time Library) vám může pomáhat detekovat a identifikovat nevracení paměti.

## <a name="enable-memory-leak-detection"></a>Povolit detekci nevracení paměti

Primární nástroje pro zjišťování nevracení paměti jsou ladicí program jazyka C/C++ a funkce haldy ladění CRT (C Runtime Library).

Chcete-li povolit všechny funkce ladění haldy, zahrňte do programu C++ následující příkazy v následujícím pořadí:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

`#define`Příkaz mapuje základní verzi funkcí haldy CRT na odpovídající ladicí verzi. Pokud ponecháte `#define` příkaz, výpis nevracení paměti bude [méně podrobný](#interpret-the-memory-leak-report).

Včetně *souboru Crtdbg. h* mapuje `malloc` funkce a `free` na jejich ladicí verze [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) a [_free_dbg](/cpp/c-runtime-library/reference/free-dbg), které sledují přidělování a navracení paměti. Toto mapování probíhá pouze v sestavení ladění, které mají `_DEBUG` . Sestavení vydaných verzí využívají běžné `malloc` `free` funkce a.

Po povolení funkcí ladění haldy pomocí předchozích příkazů umístěte volání [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) před bodem ukončení aplikace, aby při ukončení aplikace zobrazila zprávu o nevracení paměti.

```cpp
_CrtDumpMemoryLeaks();
```

Pokud vaše aplikace obsahuje několik ukončení, nemusíte ručně umísťovat do `_CrtDumpMemoryLeaks` každého bodu ukončení. Chcete-li způsobit automatické volání do `_CrtDumpMemoryLeaks` každého bodu ukončení, umístěte volání na `_CrtSetDbgFlag` začátek vaší aplikace s bitovými poli zobrazenými zde:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

Ve výchozím nastavení `_CrtDumpMemoryLeaks` výstup zprávy o nevracení paměti do podokna **ladění** okna **výstup** . Použijete-li knihovnu, knihovna může obnovit výstup do jiného umístění.

Můžete použít `_CrtSetReportMode` k přesměrování sestavy do jiného umístění nebo zpět do okna **výstup** , jak je znázorněno zde:

```cpp
_CrtSetReportMode( _CRT_WARN, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Interpretace sestavy nevracení paměti

Pokud vaše aplikace nedefinuje `_CRTDBG_MAP_ALLOC` , [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) zobrazí sestavu nevracení paměti, která vypadá takto:

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Pokud vaše aplikace definuje `_CRTDBG_MAP_ALLOC` , vypadá sestava nevracení paměti takto:

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Druhá sestava zobrazuje název souboru a číslo řádku, ve kterém je nevrácená paměť nejprve přidělena.

Bez ohledu na to, zda definujete `_CRTDBG_MAP_ALLOC` , se zobrazí zpráva o nevracení paměti:

- Číslo přidělení paměti, které je `18` v příkladu
- Typ bloku, `normal` v příkladu.
- Umístění šestnáctkové paměti `0x00780E80` v příkladu.
- Velikost bloku `64 bytes` v příkladu.
- Prvních 16 bajtů dat v bloku, v šestnáctkovém tvaru.

Typy bloků paměti jsou *normální*, *klient*nebo *CRT*. *Normální blok* je běžná paměť přidělená vaším programem. *Klientský blok* je speciální typ bloku paměti, který používají programy MFC pro objekty, které vyžadují destruktor. Operátor MFC `new` vytvoří buď normální blok, nebo klientský blok, který je vhodný pro vytvoření objektu.

*Blok CRT* je přidělen knihovnou CRT pro vlastní použití. Knihovna CRT zpracovává dealokaci pro tyto bloky, takže se bloky CRT nebudou zobrazovat v sestavě nevracení paměti, pokud neexistují vážné problémy s knihovnou CRT.

Existují dva další typy bloků paměti, které se nikdy neobjevují v sestavách nevracení paměti. *Bezplatný blok* je paměť, která byla uvolněna, takže podle definice nedojde k úniku. *Blok Ignore* je paměť, která je výslovně označena pro vyloučení ze sestavy nevracení paměti.

Předchozí postupy identifikují nevracení paměti přidělené paměti pomocí standardní funkce CRT `malloc` . Pokud program přiděluje paměť pomocí `new` operátoru jazyka C++, může se ale zobrazit jenom název souboru a číslo řádku, kde `operator new` `_malloc_dbg` jsou volání v sestavě nevracení paměti. Chcete-li vytvořit užitečnější sestavu nevracení paměti, můžete napsat makro, jako je například následující, aby se nahlásil řádek, který přidělení provedl:

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

Nyní můžete `new` operátor nahradit pomocí `DBG_NEW` makra ve vašem kódu. V sestavení ladění `DBG_NEW` používá přetížení globální `operator new` , které pro typ bloku, soubor a číslo řádku přijímá další parametry. Přetížení `new` volání `_malloc_dbg` pro záznam dalších informací. Sestavy nevracení paměti zobrazují název souboru a číslo řádku, kde byly nevrácené objekty přiděleny. Sestavení vydaných verzí stále používají výchozí hodnotu `new` . Tady je příklad techniky:

```cpp
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```

Při spuštění tohoto kódu v ladicím programu sady Visual Studio se volání `_CrtDumpMemoryLeaks` generuje sestava v okně **výstup** , které vypadá podobně jako:

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Tento výstup hlásí, že nevrácené přidělení bylo na řádku 20 *DEBUG_NEW. cpp*.

>[!NOTE]
>Nedoporučujeme vytvářet makro preprocesoru s názvem `new` nebo jakékoli jiné klíčové slovo jazyka.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Nastavení zarážek pro číslo přidělení paměti

Číslo přidělení paměti vás upozorní, když se přidělil blok nevrácené paměti. Blok s číslem přidělení paměti 18 je například 18 blok paměti přidělený během spuštění aplikace. Sestava CRT počítá všechna přidělení bloků paměti během spuštění, včetně přidělení pomocí knihovny CRT a dalších knihoven, jako je například MFC. Proto blok přidělení paměti číslo 18 pravděpodobně není 18 blok paměti přidělený vaším kódem.

K nastavení zarážky při přidělování paměti lze použít číslo přidělení.

**Nastavení zarážky přidělení paměti pomocí okno Kukátko:**

1. Nastavte zarážku poblíž začátku aplikace a spusťte ladění.

1. Když se aplikace zastaví na zarážce, otevřete okno **kukátka** tak, že vyberete **ladění**  >  **Windows**  >  **kukátko 1** (nebo **Sledujte 2**, **Sledujte 3**nebo **Sledujte 4**).

1. V okně **kukátko** zadejte `_crtBreakAlloc` sloupec **název** .

   Pokud používáte vícevláknovou DLL verzi knihovny CRT (možnost/MD), přidejte operátor kontextu: `{,,ucrtbased.dll}_crtBreakAlloc`
   
   Ujistěte se, že jsou načteny symboly ladění. V opačném případě `_crtBreakAlloc` bude hlášena jako *neidentifikovaný*.

1.  Stiskněte **Enter**.

   Ladicí program vyhodnotí volání a umístí výsledek do sloupce **Value (hodnota** ). Tato hodnota bude **-1** , pokud jste nenastavili žádné zarážky při přidělování paměti.

1. Ve sloupci **hodnota** nahraďte hodnotu číslem přidělení přidělení paměti, kde má být ladicí program přerušen.

Po nastavení zarážky pro číslo přidělení paměti pokračujte v ladění. Ujistěte se, že je spuštěný za stejných podmínek, takže se nemění číslo přidělení paměti. Když je program rozdělen do zadaného přidělení paměti, použijte okno **zásobník volání** a další okna ladicího programu k určení podmínek, za kterých byla paměť přidělena. Pak můžete pokračovat v provádění, abyste zjistili, co se stane s objektem, a zjistit, proč není správně uvolněn.

Nastavení datové zarážky u objektu může být také užitečné. Další informace najdete v tématu [použití zarážek](../debugger/using-breakpoints.md).

V kódu můžete také nastavit zarážky přidělení paměti. Můžete nastavit:

```cpp
_crtBreakAlloc = 18;
```

 nebo:

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Porovnání stavů paměti

Další technika pro vyhledání nevracení paměti zahrnuje pořizování snímků stavu paměti aplikace na klíčových místech. Chcete-li pořídit snímek stavu paměti v daném bodě aplikace, vytvořte `_CrtMemState` strukturu a předejte ji do `_CrtMemCheckpoint` funkce.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

`_CrtMemCheckpoint`Funkce vyplní strukturu pomocí snímku aktuálního stavu paměti.

Chcete-li vytvořit výstup obsahu `_CrtMemState` struktury, předejte strukturu `_ CrtMemDumpStatistics` funkci:

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` Vypíše výpis stavu paměti, který vypadá takto:

```cmd
0 bytes in 0 Free Blocks.
0 bytes in 0 Normal Blocks.
3071 bytes in 16 CRT Blocks.
0 bytes in 0 Ignore Blocks.
0 bytes in 0 Client Blocks.
Largest number used: 3071 bytes.
Total allocations: 3764 bytes.
```

Chcete-li zjistit, zda došlo k úniku paměti v části kódu, můžete pořizovat snímky stavu paměti před a za sekcí a potom použít `_ CrtMemDifference` k porovnání těchto dvou stavů:

```cpp
_CrtMemCheckpoint( &s1 );
// memory allocations take place here
_CrtMemCheckpoint( &s2 );

if ( _CrtMemDifference( &s3, &s1, &s2) )
   _CrtMemDumpStatistics( &s3 );
```

`_CrtMemDifference` Porovná stavy paměti `s1` a `s2` a vrátí výsledek v ( `s3` ), který je rozdíl mezi `s1` a `s2` .

Jedna z technik pro vyhledání nevrácené paměti začíná vložením `_CrtMemCheckpoint` volání na začátku a konci vaší aplikace a následným použitím `_CrtMemDifference` k porovnání výsledků. Pokud se `_CrtMemDifference` zobrazí nevrácená paměť, můžete přidat další `_CrtMemCheckpoint` volání k rozdělení programu pomocí binárního vyhledávání, dokud nebudete mít zdroj netěsnosti.

## <a name="false-positives"></a>Falešně pozitivní

 `_CrtDumpMemoryLeaks` může poskytnout falešně indikaci nevracení paměti, pokud se v knihovně místo bloků CRT nebo klientských bloků označí interní přidělení jako normální bloky. V takovém případě `_CrtDumpMemoryLeaks` není schopen určit rozdíl mezi přidělením uživatele a interním přidělením knihovny. Pokud jsou globální destruktory pro přidělení knihovny spouštěny po místě, kde je volána `_CrtDumpMemoryLeaks` , každé interní přidělení knihovny je hlášeno jako nevracení paměti. Verze standardní knihovny šablon starší než Visual Studio .NET mohou způsobit `_CrtDumpMemoryLeaks` hlášení takových falešně pozitivních hodnot.

## <a name="see-also"></a>Viz také

- [Podrobnosti haldy ladění CRT](../debugger/crt-debug-heap-details.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
