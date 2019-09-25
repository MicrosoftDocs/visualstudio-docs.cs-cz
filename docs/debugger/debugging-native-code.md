---
title: Ladění nativního kódu | Microsoft Docs
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8115d16b64096af343adb918ba4855d9655d4df0
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211156"
---
# <a name="debugging-native-code"></a>Ladění nativního kódu
Oddíl popisuje některé běžné problémy s laděním a techniky pro nativní aplikace. Techniky popsané v této části jsou techniky na vysoké úrovni. Informace o mechanismu používání ladicího programu sady Visual Studio naleznete v tématu [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>V tomto oddílu
 [Postupy: Ladění optimalizovaného](../debugger/how-to-debug-optimized-code.md) kódu poskytuje tipy pro ladění optimalizovaného kódu, konkrétně o tom, proč byste měli ladit neoptimalizovanou verzi programu, výchozí nastavení optimalizace pro konfigurace ladění a vydání a tipy pro hledání chyb, které pouze zobrazí se v optimalizovaném kódu (zapnutí optimalizace v konfiguraci sestavení ladění).

 [DebugBreak a __debugbreak](../debugger/debugbreak-and-debugbreak.md) Popisuje funkci Win32 `DebugBreak` a poskytuje odkaz na své referenční téma v sadě SDK platformy. Popisuje `__debugbreak` také vnitřní.

 [VýrazyC++ ](../debugger/c-cpp-assertions.md) kontrolního výrazu probírají příkazy kontrolního výrazu, jak fungují, výhody jejich použití (zachycení chyb logiky, kontrola výsledků operace a testování chybových podmínek), jejich interakce s `_DEBUG`a typy kontrolních výrazů. podporováno v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 [Postupy: Ladění vloženého kódu](../debugger/how-to-debug-inline-assembly-code.md) sestavení poskytuje krátké pokyny k použití okna zpětného překladu k zobrazení instrukcí sestavení a okna Registry k zobrazení obsahu registru a obsahuje odkazy na témata týkající se těchto oken.

 [Techniky ladění MFC](../debugger/mfc-debugging-techniques.md) Odkazuje na techniky ladění pro programy MFC, včetně: afxDebugBreak, makro TRACE, detekce nevracení paměti v prostředí MFC, kontrolní výrazy MFC a omezení velikosti sestavení ladění knihovny MFC.

 [Techniky ladění CRT](../debugger/crt-debugging-techniques.md) Odkazuje na techniky ladění pro knihovnu run-time jazyka C, včetně použití knihovny ladění CRT, maker pro vytváření sestav, rozdílů mezi sestavením a _malloc_dbg, zápisem funkcí vidlice ladění a haldy ladění CRT.

 [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md) Poskytuje odpovědi na nejčastější dotazy týkající se ladění vizuálních C++ programů.

 [Ladění modelu COM a ActiveX](../debugger/com-and-activex-debugging.md) Obsahuje informace o ladění aplikací modelu COM a ActiveX, včetně nástrojů, které lze použít pro ladění modelu COM a ActiveX.

 [Postupy: Ladění vloženého kódu](../debugger/how-to-debug-injected-code.md) poskytuje pokyny k ladění kódu, který používá atributy. Pokyny zahrnují, jak zapnout anotaci zdroje, jak zobrazit vložený kód a jak zobrazit kód zpětného překladu v aktuálním bodu spuštění.

 [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md) popisuje, jak použít okna **paralelních úkolů** a **paralelních zásobníků** k ladění paralelní aplikace.

## <a name="related-sections"></a>Související oddíly
 [Typy C++ vizuálního projektu](../debugger/debugging-preparation-visual-cpp-project-types.md) poskytují odkazy na témata, která popisují, jak ladit typy nativních projektů vytvořené šablonami Visual C++ Project.

 [Ladění projektů knihovny DLL](../debugger/debugging-dll-projects.md) Poskytuje informace o tom, jak ladit nativní a spravované knihovny DLL.

 [První pohled na ladicí program](../debugger/debugger-feature-tour.md) Obsahuje odkazy na větší části dokumentace ladění. Informace zahrnují novinky v ladicím programu, nastavení a přípravu, zarážky, zpracování výjimek, úpravy a pokračování, ladění spravovaného kódu, ladění nativního kódu, ladění SQL a odkazy na uživatelské rozhraní.

## <a name="see-also"></a>Viz také

- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění v sadě Visual Studio](../debugger/index.yml)