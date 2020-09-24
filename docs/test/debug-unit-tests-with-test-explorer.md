---
title: Ladění testů částí pomocí Průzkumníka testů
description: Naučte se ladit testy jednotek pomocí Průzkumníka testů v aplikaci Visual Studio.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b811cc3538e3bbb108e50acf50c2fe7a977fe3d
ms.sourcegitcommit: da7f093db52df5dcd67e0a030e616b307f0dc2a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2020
ms.locfileid: "91211284"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>Ladění a analýza testů jednotek pomocí Průzkumníka testů

Pomocí Průzkumníka testů můžete spustit ladicí relaci pro testy. Krokování kódu pomocí ladicího programu sady Visual Studio plynule přebírá mezi testy jednotek a testovaným projektem zpět. Spuštění ladění:

1. V editoru sady Visual Studio nastavte zarážku v jedné nebo více testovacích metodách, které chcete ladit.

    > [!NOTE]
    > Vzhledem k tomu, že testovací metody lze spustit v libovolném pořadí, nastavte zarážky ve všech testovacích metodách, které chcete ladit.

::: moniker range="vs-2017"
2. V Průzkumníku testů vyberte zkušební metody a pak zvolte možnost **ladit vybrané testy** v nabídce kliknutím pravým tlačítkem myši.
::: moniker-end
::: moniker range=">=vs-2019"
2. V Průzkumníku testů vyberte zkušební metody a pak zvolte možnost **ladit** v místní nabídce.

   ![Podrobnosti spuštění testu](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   Další informace o ladicím programu naleznete v tématu [ladění v aplikaci Visual Studio](../debugger/debugger-feature-tour.md).

## <a name="diagnose-test-method-performance-issues"></a>Diagnostika problémů s výkonem testovacích metod

::: moniker range="vs-2017"
Chcete-li diagnostikovat, proč testovací metoda trvá příliš dlouho, vyberte metodu v Průzkumníku testů a pak zvolte možnost **profilovat vybraný test** v místní nabídce kliknutím pravým tlačítkem myši. Viz [Sestava profilace instrumentace](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true).
::: moniker-end

::: moniker range=">=vs-2019"
Chcete-li diagnostikovat, proč testovací metoda trvá příliš dlouho, vyberte metodu v Průzkumníku testů a pak zvolte možnost **profil** v nabídce kliknutím pravým tlačítkem myši. Viz [Sestava profilace instrumentace](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true).
::: moniker-end

> [!NOTE]
> Tato funkce se v současné době nepodporuje pro .NET Core.

## <a name="see-also"></a>Viz také

- [Testování částí kódu](../test/unit-test-your-code.md)
- [Spouštění testů částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)
- [Průzkumník testů – nejčastější dotazy](test-explorer-faq.md)
