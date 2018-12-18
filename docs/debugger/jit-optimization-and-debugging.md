---
title: JIT optimalizace a ladění | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a9b18ab38c7c19fa5208d34439bd3133099e8bc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477352"
---
# <a name="jit-optimization-and-debugging"></a>Optimalizace a ladění JIT
**Jak fungují optimalizace v rozhraní .NET:** Pokud se pokoušíte ladění kódu, je jednodušší při zda kód je **není** optimalizované. Je to proto, že při optimalizaci kódu kompilátoru a prostředí runtime měnit kód emitovaného procesoru, aby rychleji spustí, ale má méně přímé mapování na původní zdrojový kód. To znamená, že jsou často nelze zjistíte hodnotu místní proměnné a kód, krokování ladicí programy a zarážky nemusí fungovat podle očekávání.

Obvykle je konfigurace sestavení verze vytvoří optimalizovaný kód a konfiguraci sestavení ladění neexistuje. `Optimize` MSBuild vlastnost určuje, zda je kompilátor sdělili optimalizovat kód.

V ekosystému .NET kód bude převedena ze zdroje na pokyny procesoru ve dvou krocích: nejdřív kompilátor jazyka C# převede text, který zadáte do formuláře zprostředkující binární názvem MSIL a zapíše tento pro soubory .dll. Modul Runtime rozhraní .NET později, převede tento MSIL pokyny procesoru. Oba kroky můžete optimalizovat do určité míry, ale druhý krok provádí modul Runtime rozhraní .NET provede větších optimalizace.

**Možnost optimalizace potlačit JIT na načtení modulu (pouze spravované):** zpřístupní možnost, která určuje, co se stane, když se načte knihovnu DLL, kterou je kompilovat s povolenými optimalizacemi uvnitř tento cílový proces ladicího programu. Pokud tato možnost je zaškrtnuté políčko (výchozí stav), pak když modul Runtime rozhraní .NET kompilovaný kód MSIL do kódu procesoru, zůstanou povolenými optimalizacemi. Pokud je zaškrtnutí možnost ladicího programu požadavků zakázat optimalizace.

**JIT potlačit optimalizaci pro načtení modulu (pouze spravované)** možnost najdete na **Obecné** v části **ladění** uzel v **možnosti** dialogové okno.

**Pokud by měl zaškrtnete tuto možnost:** zaškrtnete tuto možnost, když jste si stáhli knihovny DLL z jiného zdroje, jako je balíček nuget, a chcete ladit kód v této knihovny DLL. Aby tato možnost fungovala musíte taky najít soubor symbolu (.pdb) pro tuto knihovnu DLL.

Pokud vás zajímá pouze při ladění kódu, který vytváříte místně, je nejlepší nechte nezaškrtnuté, tuto možnost, jak v některých případech, povolením této možnosti bude výrazně zpomalit ladění. Existují dvě důvodem zpomalit:

* Optimalizovaný kód spustí rychleji. Pokud jsou vypnutí optimalizace pro velké množství kódu, můžete dohromady dopad na výkon.
* Pokud máte pouze můj kód povolené, ladicího programu ani zkuste a načíst symboly pro knihovny DLL, která jsou optimalizována. Hledání symbolů může trvat dlouhou dobu.

**Omezení této možnosti:** dvou případech, kde bude tato možnost **není** fungovat:

1. V situacích, kde připojování ladicí program k již spuštěných procesů tato možnost nebude mít žádný vliv na moduly, které již byly načteny v době, kdy byl připojen ladicí program.
2. Tato možnost nemá žádný vliv na knihovny DLL, které byly předem zkompilovat (známé jako ngen'ed) do nativního kódu. Můžete však zakázat použití předem zkompilovaný kód od procesu prostředí, ve kterém proměnné 'COMPlus_ZapDisable' nastaven na '1'.

## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md)   
 [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Proces spravovaného spuštění](/dotnet/standard/managed-execution-process)
