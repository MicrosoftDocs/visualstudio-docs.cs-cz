---
title: Spustit test jednotky jako 64 proces | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 27
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc379f522d119e76ef8be8ba60a4cc1482e57fd1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660469"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Spuštění testování částí v podobě 64bitového procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud máte 64 počítač, můžete spustit testy jednotek a zachytit informace o pokrytí kódu jako 64 proces.

## <a name="running-a-unit-test-as-a-64-bit-process"></a>Spuštění testu jednotek jako 64ho procesu

#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Spuštění testu jednotek jako 64ho procesu

1. Pokud byl váš kód nebo testy kompilován jako 32bitový/x86, ale nyní je chcete spouštět jako 64 proces, je třeba je znovu zkompilovat jako **Libovolný procesor**nebo případně jako **64-bit**.

    > [!TIP]
    > Pro maximální flexibilitu byste měli kompilovat testovací projekty s libovolnou konfigurací **procesoru** . Pak můžete spustit na obou bitových agentech 32 a 64. Není k dispozici žádná výhoda pro kompilování testovacích projektů s **64** konfigurací.

2. V nabídce aplikace Visual Studio zvolte možnost **test**, zvolte možnost **Nastavení**a potom zvolte možnost **Architektura procesoru**. Zvolením možnosti **x64** spustíte testy jako 64 proces.

     \- nebo-

     Zadejte `<TargetPlatform>x64</TargetPlatform>` v souboru. runsettings. Výhodou této metody je, že můžete určit skupiny nastavení v různých souborech a rychle přepínat mezi různými nastaveními. Můžete také kopírovat nastavení mezi řešeními. Další informace najdete v tématu [konfigurace testů jednotek pomocí souboru. runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Viz také
 [Spustit testy jednotek pomocí testu jednotek Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md) [váš kód](../test/unit-test-your-code.md) [Určuje nastavení testu pro testy sady Visual Studio](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)
