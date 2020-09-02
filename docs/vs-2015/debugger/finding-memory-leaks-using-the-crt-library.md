---
title: Vyhledání nevrácené paměti pomocí knihovny CRT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 831cae8d83bc26e05b80d6948a3168a6e6a387c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682425"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>Hledání nevrácené paměti pomocí knihovny CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nevrácená paměť, která je definována jako selhání pro správné uvolnění paměti, která byla dříve přidělena, je v aplikacích C/C++ mezi nejrozšířenějšími a nezjistitelnými chybami. Je možné, že by se nemusely narazit na malou nevracení paměti, ale v průběhu času může nevracení paměti způsobit příznaky, které mají vliv na snížený výkon, když aplikace vyčerpá paměť. Horší, netěsná aplikace, která používá veškerou dostupnou paměť, může způsobit zhroucení jiné aplikace a nejasnosti, se kterou je aplikace zodpovědná. I zdánlivě neškodné nevracení paměti může být příznaky z jiných problémů, které by se měly opravit.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Ladicí program a knihovny jazyka C run-time (CRT) poskytují prostředky pro zjišťování a identifikaci nevracení paměti.  
  
## <a name="enabling-memory-leak-detection"></a>Povolení detekce nevracení paměti  
 Primární nástroje pro zjišťování nevracení paměti jsou ladicí program a funkce haldy ladění CRT (C Runtime Libraries).  
  
 Chcete-li povolit funkce ladění haldy, zahrňte do programu následující příkazy:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 Aby funkce CRT fungovaly správně, `#include` musí příkazy následovat po uvedeném pořadí.  
  
 Včetně souboru Crtdbg. h mapuje `malloc` funkce a [bezplatné](https://msdn.microsoft.com/library/74ded9cf-1863-432e-9306-327a42080bb8) funkce na jejich ladicí verze [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) a `free` , které sledují přidělování a navracení paměti. Toto mapování probíhá pouze v sestavení ladění, které mají `_DEBUG` . Sestavení vydaných verzí využívají běžné `malloc` `free` funkce a.  
  
 `#define`Příkaz mapuje základní verzi funkcí haldy CRT na odpovídající ladicí verzi. Vynecháte `#define` -li příkaz, bude výpis nevracení paměti méně podrobný.  
  
 Po povolení funkcí ladění haldy pomocí těchto příkazů můžete umístit volání do `_CrtDumpMemoryLeaks` před bodem ukončení aplikace, aby při ukončení aplikace zobrazila zprávu o nevracení paměti:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Pokud má aplikace více ukončení, nemusíte ručně umístit volání [_CrtDumpMemoryLeaks](https://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) v každém bodu ukončení. Volání na `_CrtSetDbgFlag` začátek vaší aplikace způsobí automatické volání do `_CrtDumpMemoryLeaks` každého bodu ukončení. Je nutné nastavit dvě bitová pole, která jsou zobrazena zde:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Ve výchozím nastavení `_CrtDumpMemoryLeaks` výstup zprávy o nevracení paměti do podokna **ladění** okna **výstup** . Můžete použít `_CrtSetReportMode` k přesměrování sestavy do jiného umístění.  
  
 Použijete-li knihovnu, knihovna může obnovit výstup do jiného umístění. V takovém případě můžete nastavit umístění výstupu zpět do okna **výstup** , jak je znázorněno zde:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Interpretace sestavy nevracení paměti  
 Pokud vaše aplikace nedefinuje `_CRTDBG_MAP_ALLOC` , [_CrtDumpMemoryLeaks](https://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) zobrazí sestavu nevracení paměti, která vypadá takto:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Pokud vaše aplikace definuje `_CRTDBG_MAP_ALLOC` , bude sestava nevracení paměti vypadat takto:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
 normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Rozdílem je, že druhá sestava zobrazuje název souboru a číslo řádku, ve kterém je nevrácená paměť nejprve přidělena.  
  
 Bez ohledu na to, jestli definujete `_CRTDBG_MAP_ALLOC` nebo ne, se v sestavě nevracení paměti zobrazí následující informace:  
  
- Číslo přidělení paměti, které je `18` v tomto příkladu  
  
- [Typ bloku](https://msdn.microsoft.com/e2f42faf-0687-49e7-aa1f-916038354f97), který je `normal` v tomto příkladu.  
  
- Umístění v šestnáctkové paměti, které je `0x00780E80` v tomto příkladu.  
  
- Velikost bloku, `64 bytes` v tomto příkladu.  
  
- Prvních 16 bajtů dat v bloku, v šestnáctkovém tvaru.  
  
  Sestava nevracení paměti identifikuje blok paměti jako normální, klient nebo CRT. *Normální blok* je běžná paměť přidělená vaším programem. *Klientský blok* je speciální typ bloku paměti, který používají programy MFC pro objekty, které vyžadují destruktor. Operátor MFC `new` vytvoří buď normální blok, nebo klientský blok, který je vhodný pro vytvoření objektu. *Blok CRT* je přidělen knihovnou CRT pro vlastní použití. Knihovna CRT zpracovává dealokaci pro tyto bloky. Proto je pravděpodobné, že se zobrazí v sestavě nevracení paměti, pokud něco není podstatně špatné, například knihovna CRT je poškozená.  
  
  Existují dva další typy bloků paměti, které se nikdy neobjevují v sestavách nevracení paměti. *Bezplatný blok* je paměť, která byla uvolněna. To znamená, že nedojde k úniku podle definice. *Blok Ignore* je paměť, která je explicitně označena pro vyloučení ze sestavy nevracení paměti.  
  
  Tyto techniky fungují pro paměť přidělenou pomocí standardní `malloc` funkce CRT. Pokud program přiděluje paměť pomocí `new` operátoru jazyka C++, může se ale zobrazit pouze soubor a číslo řádku, kde implementace globálních `operator new` volání `_malloc_dbg` v sestavě nevracení paměti. Vzhledem k tomu, že toto chování není velmi užitečné, můžete ho změnit tak, aby nahlásilo řádek, který provedl přidělení, pomocí makra, které vypadá takto: 
 
```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Nyní můžete `new` operátor nahradit pomocí `DBG_NEW` makra ve vašem kódu. V sestavení ladění používá rozhraní přetížení globální `operator new` , které přijímá další parametry pro typ bloku, soubor a číslo řádku. Toto přetížení `new` volání `_malloc_dbg` pro záznam dalších informací. Když použijete `DBG_NEW` , sestavy nevracení paměti zobrazí název souboru a číslo řádku, kde byly nevrácené objekty přiděleny. V maloobchodních sestaveních používá výchozí `new` . (Nedoporučujeme vytvářet makro preprocesoru s názvem `new` nebo jakékoli jiné klíčové slovo jazyka.) Tady je příklad techniky:  
  
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
  
Při spuštění tohoto kódu v ladicím programu v aplikaci Visual Studio, volání `_CrtDumpMemoryLeaks` vygeneruje sestavu v okně **výstup** , která vypadá podobně jako toto:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Tím se dozvíte, že nevrácené přidělení bylo na řádku 20 debug_new. cpp.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Nastavení zarážek pro číslo přidělení paměti  
 Číslo přidělení paměti vás upozorní, když se přidělil blok nevrácené paměti. Blok s číslem přidělení paměti 18 je například 18 blok paměti přidělený během spuštění aplikace. Sestava CRT počítá všechna přidělení bloků paměti během spuštění. To zahrnuje přidělení pomocí knihovny CRT a dalších knihoven, jako je například MFC. Proto blok s číslem přidělení paměti 18 nemusí být 18 blok paměti přidělený vaším kódem. Obvykle to nebude.  
  
 K nastavení zarážky při přidělování paměti lze použít číslo přidělení.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>Nastavení zarážky přidělení paměti pomocí okno Kukátko  
  
1. Nastavte zarážku poblíž začátku aplikace a pak spusťte aplikaci.  
  
2. V případě, že je aplikace rozdělena na zarážku, okno **kukátka** .  
  
3. V okně **kukátko** zadejte `_crtBreakAlloc` sloupec **název** .  
  
    Pokud používáte vícevláknovou DLL verzi knihovny CRT (možnost/MD), zahrňte kontextový operátor: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4. Stiskněte tlačítko **vrátit**.  
  
    Ladicí program vyhodnotí volání a umístí výsledek do sloupce **Value (hodnota** ). Pokud jste nastavili žádné zarážky na přidělení paměti, bude tato hodnota – 1.  
  
5. Ve sloupci **hodnota** nahraďte hodnotu zobrazenou číslem přidělení přidělené paměti, kde chcete přerušit.  
  
   Po nastavení zarážky pro číslo přidělení paměti můžete pokračovat v ladění. Buďte opatrní, abyste spustili program za stejných podmínek jako v předchozím spuštění, aby se pořadí přidělení paměti neměnilo. Když je program rozdělen do zadaného přidělení paměti, můžete použít okno **zásobník volání** a další okna ladicího programu k určení podmínek, za kterých byla paměť přidělena. Pak můžete pokračovat v provádění, abyste zjistili, co se stane s objektem, a zjistit, proč není správně vyčleněn.  
  
   Nastavení datové zarážky u objektu může být také užitečné. Další informace najdete v tématu [použití zarážek](../debugger/using-breakpoints.md).  
  
   V kódu můžete také nastavit zarážky přidělení paměti. Toto lze provést dvěma způsoby:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 nebo:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Porovnávání stavů paměti  
 Další technika pro vyhledání nevracení paměti zahrnuje pořizování snímků stavu paměti aplikace na klíčových místech. Chcete-li pořídit snímek stavu paměti v daném bodě aplikace, vytvořte strukturu **_CrtMemState** a předejte ji do `_CrtMemCheckpoint` funkce. Tato funkce vyplní strukturu pomocí snímku aktuálního stavu paměti:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` vyplní strukturu pomocí snímku aktuálního stavu paměti.  
  
 Chcete-li vytvořit výstup obsahu **_CrtMemState** struktury, předejte strukturu `_ CrtMemDumpStatistics` funkci:  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` Vypíše výpis stavu paměti, který vypadá takto:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Chcete-li zjistit, zda došlo k úniku paměti v části kódu, můžete pořizovat snímky stavu paměti před a za sekcí a potom použít `_ CrtMemDifference` k porovnání těchto dvou stavů:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` Porovná stavy paměti `s1` a `s2` a vrátí výsledek v ( `s3` ), který je rozdílem `s1` a `s2` .  
  
 Jedna z technik pro vyhledání nevrácené paměti začíná vložením `_CrtMemCheckpoint` volání na začátku a konci aplikace a následným použitím `_CrtMemDifference` k porovnání výsledků. Pokud se `_CrtMemDifference` zobrazí nevrácená paměť, můžete přidat další `_CrtMemCheckpoint` volání k rozdělení programu pomocí binárního vyhledávání, dokud nebudete mít zdroj netěsnosti.  
  
## <a name="false-positives"></a>Falešně pozitivní  
 V některých případech `_CrtDumpMemoryLeaks` může poskytnout falešný náznak nevracení paměti. Tato situace může nastat, pokud použijete knihovnu, která označuje interní přidělení jako _NORMAL_BLOCKs namísto `_CRT_BLOCK` s nebo `_CLIENT_BLOCK` s. V takovém případě `_CrtDumpMemoryLeaks` není schopen určit rozdíl mezi přidělením uživatele a interním přidělením knihovny. Pokud jsou globální destruktory pro přidělení knihovny spouštěny po místě, kde je volána `_CrtDumpMemoryLeaks` , každé interní přidělení knihovny je hlášeno jako nevracení paměti. Starší verze standardní knihovny šablon, starší než Visual Studio .NET, způsobily `_CrtDumpMemoryLeaks` nahlášení takových falešně pozitivních hodnot, ale byly opraveny v posledních vydaných verzích.  
  
## <a name="see-also"></a>Viz také  
 [Podrobnosti haldy ladění CRT](../debugger/crt-debug-heap-details.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)
