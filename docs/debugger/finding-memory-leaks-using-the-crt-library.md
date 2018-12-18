---
title: Vyhledání nevrácené paměti pomocí knihovny CRT | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b797e8c8068523b4c782c4d7f02a3853c1d37d1
ms.sourcegitcommit: 12d6398c02e818de4fbcb4371bae9e5db6cf9509
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050103"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Hledání nevrácené paměti pomocí knihovny CRT

Nevracení paměti jsou mezi na maximum a současně lákavé obtížné zjistit chyby v aplikacích jazyka C/C++. Výsledek z neschopnost správně zrušit přidělení paměti, která byla dříve přidělena nevracení paměti. Malé přetečení paměti, nemohou být zpočátku, ale v čase, může způsobit příznaky od sníženého výkonu k chybám při spuštění aplikace nedostatek paměti. Unikající aplikaci, která spotřebovává všechnu dostupnou paměť může způsobit zhroucení jiné aplikace, což vytvoří zmatek, která aplikace je zodpovědný. Dokonce i neškodné nevracení paměti může znamenat další problémy, které by měly být opraveny.  

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ladicího programu a knihovny Run-time jazyka C (CRT) vám umožňují zjišťování a identifikaci nevracení paměti.  

## <a name="enable-memory-leak-detection"></a>Povolení rozpoznávání nevracení paměti  

Primární nástroje pro zjištění nevracení paměti jsou ladicí program jazyka C/C++ a C Run-time Library (CRT) ladicí funkce haldy.  

Pokud chcete povolit všechny funkce ladění haldy, vložte následující příkazy v programu C++, v uvedeném pořadí:  

```cpp
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  

`#define` Příkaz mapuje základní verze funkcí haldy CRT pro korespondující verzi ladicího. Pokud vynecháte `#define` prohlášení, bude výpis paměti [méně podrobné](#interpret-the-memory-leak-report).  

Včetně *souboru crtdbg.h* mapuje `malloc` a `free` funkce na jejich ladicí verze [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) a [_free_dbg –](/cpp/c-runtime-library/reference/free-dbg), které sledují paměti přidělování a navracení zpět. Toto mapování se vyskytuje pouze v sestavení ladění, které mají `_DEBUG`. Verze sestavení používají běžné `malloc` a `free` funkce.  

Po povolení funkce ladění haldy pomocí předchozích příkazů, umístěte volání [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) před bodem ukončení aplikaci pro zobrazení sestava nevracení paměti při ukončení aplikace.  

```cpp
_CrtDumpMemoryLeaks();  
```  

Pokud vaše aplikace obsahuje několik výstupů, není nutné ručně umístit `_CrtDumpMemoryLeaks` v každém bodu vstupu. Způsobí automatické volání `_CrtDumpMemoryLeaks` v každém bodu ukončení uskutečňovat volání `_CrtSetDbgFlag` na začátku aplikace s využitím bitová pole zde uvedená:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  

Ve výchozím nastavení `_CrtDumpMemoryLeaks` výstupy sestava nevracení paměti **ladění** podokně **výstup** okna. Pokud používáte knihovnu, knihovna může obnovit výstup do jiného umístění. 

Můžete použít `_CrtSetReportMode` k přesměrování sestavy do jiného umístění nebo zpět **výstup** okna, jak je znázorněno zde:  

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  

## <a name="interpret-the-memory-leak-report"></a>Interpretace sestavy nevracení paměti  

Pokud vaše aplikace nedefinuje `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) zobrazí sestava nevracení paměti, bude vypadat takto:  

```cmd
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

Pokud vaše aplikace definuje `_CRTDBG_MAP_ALLOC`, sestava nevracení paměti vypadá jako:  

```cmd
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

Druhá sestava zobrazuje název souboru a číslo řádku, kde je nevrácená paměť nejprve přidělena.  

Určuje, jestli můžete definovat `_CRTDBG_MAP_ALLOC`, sestava nevracení paměti:  

- Číslo přidělení paměti, což je `18` v příkladu  
- Typ bloku `normal` v příkladu.  
- Umístění paměti v šestnáctkové soustavě `0x00780E80` v příkladu.  
- Velikost bloku, `64 bytes` v příkladu.  
- Prvních 16 bajtů dat v bloku, v šestnáctkovém formátu.  

Typy bloků paměti jsou *normální*, *klienta*, nebo *CRT*. A *Normální blok* je běžné přidělené programem paměti. A *klientský blok* je speciální typ bloku paměti používaný programy MFC pro objekty, které vyžadují destruktor. MFC `new` operátor vytvoří normální blok nebo blok klienta, v závislosti na vytvářený objekt. 

A *blok CRT* je přidělen knihovnou CRT pro její vlastní použití. Knihovna CRT zpracovává navracení zpět pro tyto bloky, takže CRT bloky se nezobrazí v sestavě nevracení paměti pouze v případě závažných problémů s knihovnou CRT.  

Existují dva další typy paměťových bloků, které se nikdy objeví v sestavách nevracení paměti. A *volný blok* je paměť, která byla uvolněna, takže podle definice není úniku. *Blok ignore* je paměť, která jste explicitně označena pro vyloučení ze sestavy nevracení paměti.  

Předchozí techniky identifikaci nevracení paměti pro paměť přidělenou pomocí standardní CRT `malloc` funkce. Pokud váš program přiděluje paměť pomocí jazyka C++ `new` operátoru, ale uvidíte pouze název souboru a číslo řádku kde `operator new` volání `_malloc_dbg` v sestavě nevracení paměti. Pokud chcete vytvořit další užitečné sestavy nevracení paměti, můžete napsat – makro takto hlášení řádku, který provedl přidělení paměti: 

```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  

Teď můžete nahradit `new` operátorem pomocí `DBG_NEW` – makro ve vašem kódu. V ladicím buildu `DBG_NEW` používá přetížení globální `operator new` , která přijímá další parametry pro typ bloku, souboru a číslo řádku. Přetížení `new` volání `_malloc_dbg` zaznamenávat dodatečné informace. Sestavy nevracení paměti zobrazit název souboru a číslo řádku, kde byly přiděleny uniklé objekty. Verze sestavení stále používá výchozí `new`. Tady je příklad techniky:  

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

Při spuštění tohoto kódu v sadě Visual Studio ladicího programu, volání `_CrtDumpMemoryLeaks` generuje sestavy v **výstup** okno, které vypadá podobně jako:  

```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  

Tento výstup sestav, že uniklé přidělení se týkalo na řádku 20 *debug_new.cpp*.  

>[!NOTE]
>Nedoporučujeme vytvářet preprocesorové makro s názvem `new`, nebo žádné další klíčové slovo jazyka. 

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Nastavení zarážek na číslo přidělení paměti  

Číslo přidělení paměti označuje, kdy byl přidělen blok nevrácené paměti. Například blok s číslem přidělení paměti 18 je 18. blok paměti přidělené během spuštění aplikace. Sestava CRT počítá všechny alokace bloku paměti během spuštění, včetně přidělení podle knihovny CRT a dalších knihoven, jako je například knihovny MFC. Paměť přidělení bloku číslo 18 proto pravděpodobně není 18. blok paměti přidělený vaším kódem. 

Chcete-li nastavit zarážku na přidělení paměti můžete použít číslo přidělení.  

**Nastavení zarážku přidělení paměti používání okna kukátka:**  

1. Nastavit zarážku v okolí spuštění aplikace a spusťte ladění.  
   
1. Při aplikaci pozastavení na zarážce, otevřete **Watch** okna tak, že vyberete **ladění** > **Windows** > **kukátko 1** (nebo **sledovat 2**, **podívejte se na 3**, nebo **podívejte se 4**).  
   
1. V **Watch** okno, zadejte `_crtBreakAlloc` v **název** sloupce.  
   
   Pokud používáte vícevláknovou DLL verzi knihovny CRT (možnost/MD), přidejte operátor kontextu: `{,,ucrtbased.dll}_crtBreakAlloc`  
   
1. Stisknutím klávesy **zadejte**.  
   
   Ladicí program vyhodnotí volání a výsledek umístí do **hodnotu** sloupce. Tato hodnota bude **-1** Pokud jste nenastavili žádné zarážky na přidělení paměti.  
   
1. V **hodnotu** sloupce, nahraďte hodnotu číslem přidělení pro přidělení paměti, kde chcete přerušení ladicího programu.  

Po nastavení zarážky na číslo přidělení paměti, pokračujte v ladění. Ujistěte se, že ke spuštění za stejných podmínek, takže nedojde ke změně číslo přidělení paměti. Když se program zasekne při přidělení zadané paměti, použijte **zásobník volání** okno a dalších oknech ladicího programu k určení podmínek, za kterých byla přidělena paměť. Potom můžete pokračovat v provádění a sledovat, co se stane objektu a zjistit, proč není dealokován správně.  

Nastavením zarážky data objektu může být také užitečné. Další informace najdete v tématu [pomocí zarážek](../debugger/using-breakpoints.md).  

Můžete také nastavit zarážky přidělení paměti v kódu. Můžete nastavit:  

```cpp
_crtBreakAlloc = 18;  
```  

 nebo:  

```cpp
_CrtSetBreakAlloc(18);  
```  

## <a name="compare-memory-states"></a>Porovnání stavů paměti  
 Jiná metoda vyhledání přetečení paměti zahrnuje pořizování snímků stavu paměti aplikace na klíčových místech. Pořídit snímek stavu paměti v daném místě ve vaší aplikaci, vytvořte `_CrtMemState` struktury a předáním `_CrtMemCheckpoint` funkce. 

```cpp
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
```  

`_CrtMemCheckpoint` Funkce vyplní strukturu pomocí snímku aktuálního stavu paměti.  

Výstup obsahu `_CrtMemState` struktury, předejte strukturu `_ CrtMemDumpStatistics` funkce:  

```cpp
_CrtMemDumpStatistics( &s1 );  
```  

`_ CrtMemDumpStatistics` Vytvoří výstup výpisu stavu paměti, bude vypadat takto:  

```cmd
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
```  

Pokud chcete zjistit, zda došlo k nevracení paměti v části kódu, můžete pořizovat snímky stavu paměti před a po části a pak použít `_ CrtMemDifference` k porovnání dvou stavů:  

```cpp
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  

if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  

`_CrtMemDifference` porovnává stavy paměti `s1` a `s2` a vrací rozdíl v (`s3`), který je rozdíl mezi `s1` a `s2`.  

Jedna z technik pro vyhledání nevrácené paměti začíná umístěním `_CrtMemCheckpoint` volání na začátku a na konci vaší aplikace, pak pomocí `_CrtMemDifference` jak porovnat výsledky. Pokud `_CrtMemDifference` vykazuje nevracení paměti, můžete přidat další `_CrtMemCheckpoint` volání a rozdělit program pomocí binárního vyhledávání, dokud jste samostatný zdroj nevracení paměti.  

## <a name="false-positives"></a>Počet falešně pozitivních výsledků  
 `_CrtDumpMemoryLeaks` můžete poskytnout nepravdivé údaje o nevracení paměti, pokud knihovnu označuje interní přidělení jako normální bloky místo CRT bloky a bloky klienta. V takovém případě `_CrtDumpMemoryLeaks` nemůže zjistit rozdíl mezi přiděleními uživatelů a vnitřními přiděleními knihovny. Pokud globální destruktory pro přidělení knihovny běží i po okamžiku, kdy zavoláte `_CrtDumpMemoryLeaks`, každé vnitřní přidělení knihovny se hlásí jako nevracení paměti. Verze dříve, než může způsobit, že Visual Studio .NET Standard Template Library `_CrtDumpMemoryLeaks` hlášení takový počet falešně pozitivních výsledků.  

## <a name="see-also"></a>Viz také:  
 [Podrobnosti haldy ladění CRT](../debugger/crt-debug-heap-details.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)
