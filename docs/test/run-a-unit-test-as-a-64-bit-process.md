---
title: Spuštění testování částí v podobě 64bitového procesu
ms.date: 03/10/2020
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d6c6839f8c4702d88d1022116231c6f22b5dbf21
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093912"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Spuštění testování částí v podobě 64bitového procesu

Pokud máte 64bitový počítač, můžete spustit testy částí a zachytit informace o pokrytí kódu jako 64bitový proces.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Spuštění testu částí jako 64bitového procesu

1. Pokud váš kód nebo testy byly zkompilovány jako 32bitový/x86, ale nyní je chcete spustit jako 64bitový proces, překompilujte je jako **libovolný procesor**.

   ::: moniker range="vs-2017"
   Alternativně v Sadě Visual Studio 2017 můžete také zkompilovat projekt jako **64bitový**.
   ::: moniker-end

    > [!TIP]
    > Pro maximální flexibilitu zkompilujte testovací projekty pomocí konfigurace **libovolného procesoru.** Pak můžete spustit na 32bitové i 64bitové agenty. Kompilace testovacích projektů s **64bitovou** konfigurací nemá žádnou výhodu.

2. Nastavte testy částí tak, aby byly spuštěny jako 64bitový proces.

   ::: moniker range=">=vs-2019"
   Z nabídky Visual Studio zvolte **Testovat**a pak zvolte **Architektura procesoru pro projekty libovolného procesoru**. Zvolte **x64** pro spuštění testů jako 64bitový proces.
   ::: moniker-end
   ::: moniker range="vs-2017"
   V nabídce Visual Studio zvolte **Testovat**, pak zvolte **Testovat nastavení**a pak zvolte **Architektura procesoru**. Zvolte **x64** pro spuštění testů jako 64bitový proces.
   ::: moniker-end

   \-nebo -

   Zadejte `<TargetPlatform>x64</TargetPlatform>` v souboru *.runsettings.* Výhodou této metody je, že můžete určit skupiny nastavení v různých souborech a rychle přepínat mezi různými nastaveními. Můžete také kopírovat nastavení mezi řešeními. Další informace naleznete [v tématu Konfigurace testů částí pomocí souboru .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Viz také

- [Spouštění testování částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
