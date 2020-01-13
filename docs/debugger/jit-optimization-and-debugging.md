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
ms.openlocfilehash: ae11860aaa64448cd4d23b5602cf4c2da1575ce3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916229"
---
# <a name="jit-optimization-and-debugging"></a>Optimalizace a ladění JIT
Pokud se pokoušíte ladit kód, je snazší, **Pokud není tento kód optimalizován.** Když je kód optimalizován, kompilátor a modul runtime provádí změny ve vygenerovaném kódu procesoru, aby běžely rychleji, ale má méně přímé mapování na původní zdrojový kód. Pokud mapování je méně přímé, ladicí program často nemůže sdělit hodnotu místních proměnných a krokování kódu a zarážky nemusí fungovat podle očekávání.

> [!NOTE]
> Další informace o ladění JIT (just in time) najdete v [této dokumentaci](../debugger/debug-using-the-just-in-time-debugger.md).

## <a name="how-optimizations-work-in-net"></a>Jak optimalizace fungují v rozhraní .NET 
Obvykle konfigurace sestavení vydaných verzí vytvoří optimalizovaný kód a konfigurace ladění sestavení ne. Vlastnost `Optimize` MSBuild určuje, zda má kompilátor k optimalizaci kódu.

V ekosystému .NET je kód od zdroje až po instrukce pro procesor v procesu se dvěma kroky: za prvé převede C# kompilátor text, který zadáte do zprostředkujícího binárního formátu s názvem MSIL a zapíše do souborů. dll soubory MSIL. Později modul runtime .NET převede tento jazyk MSIL na instrukce procesoru. Oba kroky lze optimalizovat do určité míry, ale druhý krok prováděný modulem runtime .NET provádí významnější optimalizace.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>Možnost potlačit optimalizaci JIT při načtení modulu (pouze spravované)
Ladicí program zpřístupňuje možnost, která určuje, co se stane, když je knihovna DLL, která je zkompilována s povolenými optimalizacemi, načtena uvnitř cílového procesu. Pokud tato možnost není zaškrtnuta (výchozí stav), pak pokud modul runtime .NET zkompiluje kód jazyka MSIL do kódu procesoru, ponechá optimalizace zapnuté. Pokud je tato možnost zaškrtnutá, ladicí program požaduje, aby byly optimalizace zakázané.

Chcete-li najít možnost **potlačit optimalizaci JIT při načtení modulu (pouze spravované)** , vyberte **nástroje** > **Možnosti**a poté vyberte stránku **Obecné** pod uzlem **ladění** .

![Potlačit optimalizaci JIT](../debugger/media/suppress-jit-tool-options.png "Potlačit optimalizaci JIT")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>Kdy byste měli zaškrtnout možnost potlačit optimalizaci JIT?
Tuto možnost můžete zaškrtnout, pokud jste stáhli knihovny DLL z jiného zdroje, jako je například balíček NuGet, a chcete ladit kód v této knihovně DLL. Aby potlačení fungovalo, musíte také najít soubor symbolů (. pdb) pro tuto knihovnu DLL.

Pokud vás zajímá pouze ladění kódu, který vytváříte místně, je nejlepší ponechat tuto možnost nezaškrtnutou, protože v některých případech povolení této možnosti výrazně zpomaluje ladění. Existují dva důvody zpomalení:

* Optimalizovaný kód běží rychleji. Pokud vypnete optimalizace pro spoustu kódu, může dopad na výkon přidat.
* Pokud máte povolené Pouze můj kód, ladicí program se ani nepokusí načíst symboly pro knihovny DLL, které jsou optimalizované. Hledání symbolů může trvat dlouhou dobu.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>Omezení pro možnost potlačit optimalizaci JIT 
Při zapnutí této možnosti **nebudou fungovat dvě** situace:

1. V situacích, kdy připojujete ladicí program k již běžícímu procesu, tato možnost nebude mít žádný vliv na moduly, které již byly načteny v době, kdy byl ladicí program připojen.
2. Tato možnost nemá žádný vliv na knihovny DLL, které byly předem kompilovány (a. k. a ngen'ed) do nativního kódu. Můžete však zakázat použití předkompilovaného kódu spuštěním procesu s proměnnou prostředí **' COMPlus_ReadyToRun '** nastavenou na hodnotu **' 0 '** . Díky tomu bude modul runtime .NET Core moci zakázat použití předkompilovaných imagí, což vynucuje kód rozhraní kompilování modulu runtime JIT. 

    > [!IMPORTANT]
    > Pokud cílíte .NET Framework nebo starší verze .NET Core (2. x nebo nižší), přidejte taky proměnnou prostředí COMPlus_ZapDisable a nastavte ji na 1.

    **Nastavení proměnné prostředí pro projekt .NET Core v sadě Visual Studio:**
    1. V **Průzkumník řešení**klikněte **pravým tlačítkem myši na** soubor projektu a vyberte možnost **vlastnosti**.
    2. Přejděte na kartu **ladění** a v části **proměnné prostředí**klikněte na tlačítko **Přidat** .
    3. Nastavte název (klíč) na **COMPlus_ReadyToRun** a nastavte hodnotu na **0**.

    ![Nastavit COMPlus_ReadyToRun proměnnou prostředí](../debugger/media/environment-variables-debug-menu.png "Nastavit COMPlus_ReadyToRun proměnnou prostředí")

## <a name="see-also"></a>Viz také:
- [Jak ladit zdroj rozhraní DotNET Framework](../debugger/how-to-debug-dotnet-framework-source.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md)
- [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Proces spravovaného spuštění](/dotnet/standard/managed-execution-process)
