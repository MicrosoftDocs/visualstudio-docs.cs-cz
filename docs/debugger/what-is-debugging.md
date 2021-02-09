---
title: Co je ladění?
description: Vysvětlení toho, co znamená ladění aplikace
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3435b7a270d89dc38f5ff10a1350418a24f91c0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883932"
---
# <a name="what-is-debugging"></a>Co je ladění?

Ladicí program sady Visual Studio je výkonný nástroj. Než si ukážeme, jak ho používat, chceme mluvit o některých pojmech, jako je například *ladicí program*, *ladění* a *režim ladění*. V takovém případě budeme mluvit o tom, co se chystáme najít a opravit chyby.

## <a name="debugger-vs-debugging"></a>Ladicí program vs. ladění

Termín *ladění* může znamenat spoustu různých věcí, ale nejvíce doslova znamená odebrání chyb z kódu. Nyní existuje mnoho způsobů, jak to provést. Můžete například ladit kontrolou kódu, který hledá překlepy, nebo pomocí analyzátoru kódu. Můžete ladit kód pomocí profileru výkonu. Nebo může ladit pomocí *ladicího programu*.

Ladicí program je vysoce specializovaný vývojářský nástroj, který se připojuje ke svojí spuštěné aplikaci a umožňuje vám kontrolovat váš kód. V dokumentaci ladění pro Visual Studio je to obvykle to, co znamenáme, když říkáme "ladění".

## <a name="debug-mode-vs-running-your-app"></a>Režim ladění vs. spuštění aplikace

Při prvním spuštění aplikace v sadě Visual Studio je možné ji spustit stisknutím zeleného tlačítka se šipkou ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů (nebo **F5**). Ve výchozím nastavení se hodnota **ladění** zobrazí v rozevíracím seznamu vlevo. Pokud se sadou Visual Studio ještě nepoužíváte, může to zůstat dojem, že ladění vaší aplikace má něco dělat, když máte spuštěnou aplikaci – to ale má zásadní význam dvou velmi odlišných úloh.

![Vybrat sestavení pro ladění](../debugger/media/what-is-debugging-debug-build.png)

Hodnota **ladění** označuje konfiguraci ladění. Při spuštění aplikace (stiskněte zelenou šipku nebo **F5**) v konfiguraci ladění spustíte aplikaci v *režimu ladění*, což znamená, že máte spuštěnou aplikaci s připojeným ladicím programem. To umožňuje úplnou sadu funkcí ladění, které vám pomůžou najít chyby ve vaší aplikaci.

Pokud máte projekt otevřený, vyberte rozevírací selektor, kde říká **ladění** , a vyberte místo toho možnost **vydat** .

![Vybrat Build pro vydání](../debugger/media/what-is-debugging-release-build.png)

Když přepnete toto nastavení, změníte projekt z konfigurace ladění na konfiguraci vydané verze. Projekty sady Visual Studio mají samostatné konfigurace vydaných verzí a ladění pro váš program. Sestavíte ladicí verzi pro ladění a verzi Release pro konečnou distribuci vydaných verzí. Sestavení pro vydání je optimalizováno pro výkon, ale sestavení ladění je vhodnější pro ladění.

## <a name="when-to-use-a-debugger"></a>Kdy použít ladicí program

Ladicí program je základním nástrojem pro hledání a opravy chyb ve vašich aplikacích. Kontext je však krále a je důležité využít všechny nástroje na více než jedno, což vám pomůže rychle eliminovat chyby nebo chyby. V některých případech se může jednat o lepší postup při kódování. Když se naučíte používat ladicí program vs. nějaký jiný nástroj, naučíte se také, jak použít ladicí program efektivněji.

## <a name="next-steps"></a>Další kroky

V tomto článku jste se dozvěděli o několika obecných konceptech ladění. Dále můžete začít s učením, jak ladit se sadou Visual Studio a jak psát kód s méně chybami. Následující články ukazují příklady kódu C#, ale koncepty platí pro všechny jazyky, které podporuje Visual Studio.

> [!div class="nextstepaction"]
> [Ladění pro naprosté začátečníky](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [Techniky ladění a související nástroje](../debugger/write-better-code-with-visual-studio.md)
