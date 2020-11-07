---
title: Ruční spuštění analýzy kódu pro .NET
ms.date: 09/02/2020
description: Naučte se, jak ručně spustit analýzu kódu v aplikaci Visual Studio 2019 verze 16,5 nebo novější. Přečtěte si, jak spustit analyzátory Roslyn v jazyce C# nebo Visual Basic kódu.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2eb4beff76d602bb4ce6182fab6091c7cd2a0096
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348720"
---
# <a name="run-code-analysis-manually-for-net"></a>Ruční spuštění analýzy kódu pro .NET
Ve výchozím nastavení analyzátory .NET Compiler Platform ("Roslyn") analyzují kód C# nebo Visual Basic při psaní pomocí živé analýzy a také při sestavování. Proto byste normálně nemuseli aktivovat analýzu kódu ručně. Existují však situace, kdy lze chtít ručně aktivovat analýzu kódu:

> [!NOTE]
> Ruční spuštění analýzy kódu vyžaduje Visual Studio 2019 verze 16,5 nebo novější.

- Ve výchozím nastavení provádí dynamická analýza kódu analyzátory pouze pro otevřené soubory v aplikaci Visual Studio. Můžete ale zajímat zobrazení upozornění analýzy kódu pro všechny soubory v konkrétním projektu nebo řešení. Pokud ano, chcete aktivovat analýzu kódu jednou na projektu nebo řešení. Alternativně můžete povolit průběžnou živou analýzu kódu pro spuštění v celém řešení. Další informace naleznete v tématu [How to: Configure Live Code Analysis Scope for Managed Code](./configure-live-code-analysis-scope-managed-code.md).
- Můžete preferovat pracovní postup provádění analýzy kódu na vyžádání přes průběžnou analýzu za provozu nebo analýzu doby sestavení. V takovém případě můžete vypnout spuštění analyzátoru během analýzy za provozu nebo sestavení. Informace o zakázání analýzy najdete v tématu [Jak zakázat analýzu zdrojového kódu](disable-code-analysis.md). Pak byste chtěli ručně aktivovat analýzu kódu na projektu nebo řešení.

### <a name="run-code-analysis-manually"></a>Ruční spuštění analýzy kódu

1. V **Průzkumník řešení** vyberte projekt.

2. V nabídce **analyzovat** vyberte možnost **Spustit analýzu kódu pro** *název projektu*.

Analýza kódu začne spouštět na pozadí. V levém dolním rohu by se měla zobrazit zpráva **spuštění analýzy kódu pro \<project> ...** ve stavovém řádku sady Visual Studio. Po dokončení analýzy kódu se stavová zpráva změní na **analýzu kódu dokončenou pro \<project>**. Seznam chyb bude brzy aktualizován všemi diagnostikami analýzy kódu.
