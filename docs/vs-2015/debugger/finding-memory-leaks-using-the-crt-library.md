---
title: Hledání nevrácené paměti pomocí knihovny CRT | Dokumentace Microsoftu
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
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eca7af1cb572714214f264cac35b488fba993bdd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726564"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>Hledání nevrácené paměti pomocí knihovny CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nevracení paměti, definovaná jako neschopnost správně zrušit přidělení paměti, která byla dříve přidělena, patří mezi nejnenápadnější a obtížné zjistit chyby v aplikacích jazyka C/C++. Malé přetečení paměti, nemohou být na první, ale v čase, progresivní přetečení paměti může způsobit příznaky od sníženého výkonu selhání, když má aplikace nedostatek paměti. Horší že všechnu dostupnou paměť aplikace může způsobit zhroucení, jiné aplikace vytvoří zmatek ohledně toho, která zodpovídá aplikace. I zdánlivě neškodné nevracení paměti mohou být napraveny jiné problémy, které by měly být opraveny.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ladicího programu a knihovny Run-Time C (CRT) vám poskytují prostředky pro zjištění a identifikaci nevracení paměti.  
  
## <a name="enabling-memory-leak-detection"></a>Povolení rozpoznávání nevracení paměti  
 Primární nástroje pro zjištění nevracení paměti jsou ladicí program a knihovny Run-Time C (CRT) ladicí funkce haldy.  
  
 Pokud chcete povolit funkce ladění haldy, patří ve svém programu následující příkazy:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 Funkce CRT pracovaly správně `#include` příkazy musí odpovídat zde uvedenému pořadí.  
  
 Zahrnutí souboru crtdbg.h namapuje `malloc` a [bezplatné](http://msdn.microsoft.com/library/74ded9cf-1863-432e-9306-327a42080bb8) funkce na jejich ladicí verze [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) a `free`, které sledují přidělování a vracení paměti. Toto mapování se vyskytuje pouze v sestavení ladění, které mají `_DEBUG`. Verze sestavení používají běžné `malloc` a `free` funkce.  
  
 `#define` Příkaz mapuje základní verze funkcí haldy CRT pro korespondující verzi ladicího. Vynecháte-li `#define` prohlášení, bude výpis paměti méně podrobný.  
  
 Po povolení funkce ladění haldy pomocí těchto příkazů lze uskutečňovat volání `_CrtDumpMemoryLeaks` před bodem ukončení aplikace pro zobrazení sestava nevracení paměti při ukončení aplikace:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Pokud aplikace obsahuje více východů, není nutné ručně umístit volání [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) v každém bodu vstupu. Volání `_CrtSetDbgFlag` na začátku aplikace způsobí automatické volání `_CrtDumpMemoryLeaks` na každém bodu ukončení. Je nutné nastavit dvě bitová pole zde uvedená:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Ve výchozím nastavení `_CrtDumpMemoryLeaks` výstupy sestava nevracení paměti **ladění** podokně **výstup** okna. Můžete použít `_CrtSetReportMode` k přesměrování sestavy do jiného umístění.  
  
 Pokud používáte knihovnu, knihovna může obnovit výstup do jiného umístění. V takovém případě můžete nastavit umístění výstupu zpět **výstup** okna, jak je znázorněno zde:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Interpretace sestavy nevracení paměti  
 Pokud vaše aplikace nedefinuje `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) zobrazí sestava nevracení paměti, která vypadá takto:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Pokud vaše aplikace definuje `_CRTDBG_MAP_ALLOC`, sestava nevracení paměti vypadá takto:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
 normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Rozdíl je, že druhá sestava zobrazuje název souboru a číslo řádku kde je nevrácená paměť nejprve přidělena.  
  
 Ať už definujete `_CRTDBG_MAP_ALLOC` nebo Ne, nevrácená paměť sestavy se zobrazí následující informace:  
  
- Číslo přidělení paměti, což je `18` v tomto příkladu  
  
- [Typ bloku](http://msdn.microsoft.com/en-us/e2f42faf-0687-49e7-aa1f-916038354f97), což je `normal` v tomto příkladu.  
  
- Umístění paměti v šestnáctkové soustavě, což je `0x00780E80` v tomto příkladu.  
  
- Velikost bloku, `64 bytes` v tomto příkladu.  
  
- Prvních 16 bajtů dat v bloku, v šestnáctkovém formátu.  
  
  Sestava nevracení paměti určuje blok paměti jako normální, klient nebo CRT. A *Normální blok* je běžné přidělené programem paměti. A *klientský blok* je speciální typ bloku paměti používaný programy MFC pro objekty, které vyžadují destruktor. MFC `new` operátor vytvoří normální blok nebo blok klienta, v závislosti na vytvářený objekt. A *blok CRT* je přidělen knihovnou CRT pro její vlastní použití. Knihovna CRT zpracovává navracení zpět pro tyto bloky. Je tedy nepravděpodobné, že uvidíte tyto sestavy nevracení paměti Pokud není něco výrazně špatně, například Knihovna CRT je poškozena.  
  
  Existují dva další typy paměťových bloků, které se nikdy objeví v sestavách nevracení paměti. A *volný blok* je paměť, která byla uvolněna. To znamená, že není úniku podle definice. *Blok ignore* je paměť, která byla explicitně označena pro vyloučení ze sestavy nevracení paměti.  
  
  Tyto techniky fungují pro paměť přidělenou pomocí standardní CRT `malloc` funkce. Pokud váš program přiděluje paměť pomocí jazyka C++ `new` operátoru, ale uvidíte pouze souboru a číslo řádku kde provádění globální `operator new` volání `_malloc_dbg` v sestavě nevracení paměti. Protože toto chování není velmi užitečné, můžete změnit tak, na řádku, který provedl přidělení pomocí makra, který vypadá takto: 
 
```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Teď můžete nahradit `new` operátorem pomocí `DBG_NEW` – makro ve vašem kódu. V sestavení ladění, tento mechanismus využívá přetížení globální `operator new` , která přijímá další parametry pro typ bloku, souboru a číslo řádku. Toto přetížení `new` volání `_malloc_dbg` zaznamenávat dodatečné informace. Při použití `DBG_NEW`, nevracení paměti sestavy zobrazit název souboru a číslo řádku, kde byly přiděleny uniklé objekty. V prodejní buildy, použije výchozí `new`. (Není doporučeno vytvořit preprocesorové makro s názvem `new`, nebo žádné další klíčové slovo jazyka.) Tady je příklad techniky:  
  
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
  
Při spuštění tohoto kódu v ladicím programu v sadě Visual Studio, volání `_CrtDumpMemoryLeaks` generuje sestavy v **výstup** okno, které vypadá nějak takto:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Znamená to, že uniklé přidělení se týkalo na řádku 20 debug_new.cpp.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Nastavení zarážek na číslo přidělení paměti  
 Číslo přidělení paměti označuje, kdy byl přidělen blok nevrácené paměti. Například blok s číslem přidělení paměti 18 je 18. blok paměti přidělené během spuštění aplikace. Sestava CRT počítá všechny alokace bloku paměti během spuštění. Jedná se o přidělení podle knihovny CRT a dalších knihoven, jako je například knihovny MFC. Blok s číslem přidělení paměti 18 proto nemusí být 18. blok paměti přidělený vaším kódem. Obvykle nebude.  
  
 Chcete-li nastavit zarážku na přidělení paměti můžete použít číslo přidělení.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>Chcete-li nastavit zarážku přidělení paměti používání okna kukátka  
  
1. Nastavit zarážku v okolí spuštění aplikace a spusťte aplikaci.  
  
2. Když se aplikace zastaví u zarážky, **Watch** okna.  
  
3. V **Watch** okno, zadejte `_crtBreakAlloc` v **název** sloupce.  
  
    Pokud používáte vícevláknovou DLL verzi knihovny CRT (možnost/MD), zahrňte operátor kontextu: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4. Stisknutím klávesy **vrátit**.  
  
    Ladicí program vyhodnotí volání a výsledek umístí do **hodnotu** sloupce. Pokud jste nenastavili žádné zarážky na přidělení paměti, bude tato hodnota – 1.  
  
5. V **hodnotu** sloupce, nahraďte hodnotu číslem přidělení pro přidělení paměti ukazuje, kde chcete provést přerušení.  
  
   Po nastavení zarážky na číslo přidělení paměti, můžete pokračovat k ladění. Buďte opatrní při spouštění programu za stejných podmínek jako při předchozím spuštění, aby se nezměnilo pořadí přidělení paměti. Když se program zasekne při přidělení zadané paměti, můžete použít **zásobník volání** okno a dalších oknech ladicího programu k určení podmínek, za kterých byla přidělena paměť. Potom můžete pokračovat v provádění a sledovat, co se stane objektu a zjistit, proč není dealokován správně.  
  
   Nastavením zarážky data objektu může být také užitečné. Další informace najdete v tématu [pomocí zarážek](../debugger/using-breakpoints.md).  
  
   Můžete také nastavit zarážky přidělení paměti v kódu. Toto lze provést dvěma způsoby:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 nebo:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Porovnání stavů paměti  
 Jiná metoda vyhledání přetečení paměti zahrnuje pořizování snímků stavu paměti aplikace na klíčových místech. Pořídit snímek stavu paměti v daném místě ve vaší aplikaci, vytvořte **_CrtMemState** struktury a předáním `_CrtMemCheckpoint` funkce. Tato funkce vyplní strukturu pomocí snímku aktuálního stavu paměti:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` vyplní strukturu pomocí snímku aktuálního stavu paměti.  
  
 Výstup obsahu **_CrtMemState** struktury, předejte strukturu `_ CrtMemDumpStatistics` funkce:  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` Vytvoří výstup výpisu stavu paměti, který vypadá takto:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Pokud chcete zjistit, zda došlo k nevracení paměti v části kódu, můžete pořizovat snímky stavu paměti před a po části a pak použít `_ CrtMemDifference` k porovnání dvou stavů:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` porovnává stavy paměti `s1` a `s2` a vrací rozdíl v (`s3`), který je rozdíl mezi `s1` a `s2`.  
  
 Jedna z technik pro vyhledání nevrácené paměti začíná umístěním `_CrtMemCheckpoint` volání na začátku a na konci vaší aplikace, pak použijte `_CrtMemDifference` jak porovnat výsledky. Pokud `_CrtMemDifference` vykazuje nevracení paměti, můžete přidat další `_CrtMemCheckpoint` volání a rozdělit program pomocí binárního vyhledávání, dokud nenaleznete zdroj nevracení paměti.  
  
## <a name="false-positives"></a>Počet falešně pozitivních výsledků  
 V některých případech `_CrtDumpMemoryLeaks` můžete poskytnout nepravdivé údaje o nevracení paměti. Tato situace může nastat, pokud používáte knihovnu, která označuje interní přidělení jako _normal_block namísto `_CRT_BLOCK`s nebo `_CLIENT_BLOCK`s. V takovém případě `_CrtDumpMemoryLeaks` nemůže zjistit rozdíl mezi přiděleními uživatelů a vnitřními přiděleními knihovny. Pokud globální destruktory pro přidělení knihovny běží i po okamžiku, kdy zavoláte `_CrtDumpMemoryLeaks`, každé vnitřní přidělení knihovny se hlásí jako nevracení paměti. Starší verze standardní knihovny šablon, starší než Visual Studio .NET, způsobil `_CrtDumpMemoryLeaks` hlásila takovéto falešné poplachy, ale tento Opravili jsme v nedávno vydané aktualizace.  
  
## <a name="see-also"></a>Viz také  
 [Podrobnosti haldy ladění CRT](../debugger/crt-debug-heap-details.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)



