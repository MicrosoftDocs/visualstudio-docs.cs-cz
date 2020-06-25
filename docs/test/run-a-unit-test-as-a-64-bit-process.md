---
title: Spuštění testování částí v podobě 64bitového procesu
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 04895e3dd72a7cb4f0373c970db0f12582506ef9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285553"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Spuštění testování částí v podobě 64bitového procesu

Pokud máte 64 počítač, můžete spustit testy jednotek a zachytit informace o pokrytí kódu jako 64 proces.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Spuštění testu jednotek jako 64ho procesu

1. Pokud byl váš kód nebo testy zkompilován jako 32bitový/x86, ale nyní je chcete spouštět jako 64 proces, zkompilujte je znovu jako **jakýkoli procesor**.

   ::: moniker range="vs-2017"
   Případně můžete také zkompilovat projekt jako **64-bit**v aplikaci Visual Studio 2017.
   ::: moniker-end

    > [!TIP]
    > Pro zajištění maximální flexibility zkompilujte testovací projekty s **libovolnou konfigurací procesoru** . Pak můžete spustit na 32 i 64 bitových agentů. Neexistují žádné výhody kompilace testovacích projektů s **64** konfigurací.

2. Nastavte testy jednotek tak, aby se spouštěly jako 64 proces.

   ::: moniker range=">=vs-2019"
   V nabídce aplikace Visual Studio zvolte možnost **test**a pak zvolte možnost **Architektura procesoru pro projekty anycpu**. Zvolením možnosti **x64** spustíte testy jako 64 proces.
   ::: moniker-end
   ::: moniker range="vs-2017"
   V nabídce aplikace Visual Studio zvolte možnost **test**, zvolte možnost **nastavení testu**a pak zvolte možnost **Architektura procesoru**. Zvolením možnosti **x64** spustíte testy jako 64 proces.
   ::: moniker-end

   \-ani

   Zadejte `<TargetPlatform>x64</TargetPlatform>` v souboru *. runsettings* . Výhodou této metody je, že můžete určit skupiny nastavení v různých souborech a rychle přepínat mezi různými nastaveními. Můžete také kopírovat nastavení mezi řešeními. Další informace najdete v tématu [konfigurace testů jednotek pomocí souboru. runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Viz také

- [Spouštění testů částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
