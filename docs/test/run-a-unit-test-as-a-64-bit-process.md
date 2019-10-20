---
title: Spuštění testování částí v podobě 64bitového procesu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 3971fe0513c98cb957d8013cdad932aa0c04bed1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646627"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Spuštění testování částí v podobě 64bitového procesu

Pokud máte 64 počítač, můžete spustit testy jednotek a zachytit informace o pokrytí kódu jako 64 proces.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Spuštění testu jednotek jako 64ho procesu

1. Pokud byl váš kód nebo testy kompilován jako 32bitový/x86, ale nyní je chcete spouštět jako 64 proces, je třeba je znovu zkompilovat jako **Libovolný procesor**nebo případně jako **64-bit**.

    > [!TIP]
    > Pro zajištění maximální flexibility zkompilujte testovací projekty s **libovolnou konfigurací procesoru** . Pak můžete spustit na 32 i 64 bitových agentů. Neexistují žádné výhody kompilace testovacích projektů s **64** konfigurací.

2. V nabídce aplikace Visual Studio zvolte možnost **test**, zvolte možnost **Nastavení**a potom zvolte možnost **Architektura procesoru**. Zvolením možnosti **x64** spustíte testy jako 64 proces.

   - ani

   Zadejte `<TargetPlatform>x64</TargetPlatform>` v souboru *. runsettings* . Výhodou této metody je, že můžete určit skupiny nastavení v různých souborech a rychle přepínat mezi různými nastaveními. Můžete také kopírovat nastavení mezi řešeními. Další informace najdete v tématu [konfigurace testů jednotek pomocí souboru. runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Viz také:

- [Spouštění testování částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
