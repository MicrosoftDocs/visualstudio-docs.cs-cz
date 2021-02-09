---
title: Spuštění testování částí v podobě 64bitového procesu
description: Naučte se spouštět testy jednotek a zachytit informace o pokrytí kódu jako 64 proces. Musíte mít 64 počítač.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 184ea2250732bfa37f1740fadfa85616d83a88cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917545"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Spuštění testování částí v podobě 64bitového procesu

Pokud máte 64 počítač, můžete spustit testy jednotek a zachytit informace o pokrytí kódu jako 64 proces.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Spuštění testu jednotek jako 64ho procesu

1. Pokud byl váš kód nebo testy zkompilován jako 32bitový/x86, ale nyní je chcete spouštět jako 64 proces, zkompilujte je znovu jako **jakýkoli procesor**.

   ::: moniker range="vs-2017"
   Případně můžete také zkompilovat projekt jako **64-bit** v aplikaci Visual Studio 2017.
   ::: moniker-end

    > [!TIP]
    > Pro zajištění maximální flexibility zkompilujte testovací projekty s **libovolnou konfigurací procesoru** . Pak můžete spustit na 32 i 64 bitových agentů. Není k dispozici žádná výhoda pro kompilování projektů testů s **64** konfigurací, pokud nevoláte kód, který je podporován pouze na 64-bit.

2. Nastavte testy jednotek tak, aby se spouštěly jako 64 proces.

   ::: moniker range=">=vs-2019"
   V nabídce aplikace Visual Studio zvolte možnost **test** a pak zvolte možnost **Architektura procesoru pro projekty anycpu**. Zvolením možnosti **x64** spustíte testy jako 64 proces.
   ::: moniker-end
   ::: moniker range="vs-2017"
   V nabídce aplikace Visual Studio zvolte možnost **test**, zvolte možnost **nastavení testu** a pak zvolte možnost **Architektura procesoru**. Zvolením možnosti **x64** spustíte testy jako 64 proces.
   ::: moniker-end

   \- ani

   Zadejte `<TargetPlatform>x64</TargetPlatform>` v souboru *. runsettings* . Výhodou této metody je, že můžete určit skupiny nastavení v různých souborech a rychle přepínat mezi různými nastaveními. Můžete také kopírovat nastavení mezi řešeními. Další informace najdete v tématu [konfigurace testů jednotek pomocí souboru. runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Viz také

- [Spouštění testů částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
