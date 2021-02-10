---
title: Ladění testů částí pomocí Průzkumníka testů
description: Naučte se ladit testy jednotek pomocí Průzkumníka testů v aplikaci Visual Studio.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09889839c9e2873810c78a5f0c3425820170b68d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964378"
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
