---
title: Optimalizace a ladění JIT | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12752acf75da70fa30666f9b1780256c94bde859
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731625"
---
# <a name="jit-optimization-and-debugging"></a>Optimalizace a ladění JIT
**Jak optimalizace fungují v rozhraní .NET:** Pokud se pokoušíte ladit kód, je snazší, **Pokud není tento kód optimalizován.** Důvodem je, že když je kód optimalizován, kompilátor a modul runtime provádí změny ve vygenerovaném kódu procesoru, aby běžely rychleji, ale má méně přímé mapování na původní zdrojový kód. To znamená, že ladicí program často nemůže sdělit hodnotu místních proměnných a krokování kódu a zarážky nemusí fungovat podle očekávání.

Obvykle konfigurace sestavení vydaných verzí vytvoří optimalizovaný kód a konfigurace ladění sestavení ne. Vlastnost `Optimize` MSBuild určuje, zda má kompilátor k optimalizaci kódu.

V ekosystému .NET se kód přepíná ze zdroje na PROCESORové instrukce v procesu se dvěma kroky: za prvé převede C# kompilátor text, který zadáte do zprostředkujícího binárního formátu s názvem MSIL, a zapíše tento výstup do souborů. dll. Později modul runtime .NET převede tento jazyk MSIL na instrukce procesoru. Oba kroky lze optimalizovat do určité míry, ale druhý krok prováděný modulem runtime .NET provádí významnější optimalizace.

**Možnost potlačit optimalizaci JIT při načtení modulu (pouze spravované):** Ladicí program zpřístupňuje možnost, která určuje, co se stane, když je knihovna DLL, která je zkompilována s povolenými optimalizacemi, načtena uvnitř cílového procesu. Pokud tato možnost není zaškrtnuta (výchozí stav), pak pokud modul runtime .NET zkompiluje kód jazyka MSIL do kódu procesoru, ponechá optimalizace zapnuté. Pokud je tato možnost zaškrtnutá, ladicí program požaduje, aby byly optimalizace zakázané.

Chcete-li najít možnost **potlačit optimalizaci JIT při načtení modulu (pouze spravované)** , vyberte **nástroje**  > **Možnosti**a poté vyberte stránku **Obecné** pod uzlem **ladění** .

**Když byste měli zaškrtnout tuto možnost:** Tuto možnost můžete zaškrtnout, pokud jste stáhli knihovny DLL z jiného zdroje, jako je například balíček NuGet, a chcete ladit kód v této knihovně DLL. Aby to fungovalo, musíte také najít soubor symbolů (. pdb) pro tuto knihovnu DLL.

Pokud vás zajímá pouze ladění kódu, který vytváříte místně, je nejlepší ponechat tuto možnost nezaškrtnutou, protože v některých případech povolení této možnosti výrazně zpomaluje ladění. Existují dva důvody zpomalení:

* Optimalizovaný kód běží rychleji. Pokud vypnete optimalizace pro spoustu kódu, může dopad na výkon přidat.
* Pokud máte povoleno Pouze můj kód, ladicí program nebude ani pokoušet o načtení symbolů pro knihovny DLL, které jsou optimalizovány. Hledání symbolů může trvat dlouhou dobu.

**Omezení této možnosti:** Existují dvě situace, kdy tato možnost nebude **fungovat:**

1. V situacích, kdy připojujete ladicí program k již běžícímu procesu, tato možnost nebude mít žádný vliv na moduly, které již byly načteny v době, kdy byl ladicí program připojen.
2. Tato možnost nemá žádný vliv na knihovny DLL, které byly předem kompilovány (a. k. a ngen'ed) do nativního kódu. Můžete však zakázat použití předkompilovaného kódu spuštěním procesu s proměnnou prostředí ' COMPlus_ZapDisable ' nastavenou na ' 1 '.

## <a name="see-also"></a>Viz také:
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md)
- [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Proces spravovaného spuštění](/dotnet/standard/managed-execution-process)
