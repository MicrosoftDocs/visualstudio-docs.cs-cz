---
title: Ruční spuštění analýzy kódu pro spravovaný kód
ms.date: 11/04/2019
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 874d95b65b99af4b5a6b00d45101236f62db3df1
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769364"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Postupy: ruční spuštění analýzy kódu pro spravovaný kód (vyžaduje Visual Studio 2019 verze 16,5 nebo novější)
Ve výchozím nastavení .NET Compiler Platform ("Roslyn") analyzátory kódu analyzují kód C# nebo Visual Basic při psaní, a to pomocí živé analýzy a také během sestavování. Proto byste normálně nemuseli aktivovat analýzu kódu ručně. Existují však situace, kdy lze chtít ručně aktivovat analýzu kódu:

- Ve výchozím nastavení provádí dynamická analýza kódu analyzátory pouze pro otevřené soubory v aplikaci Visual Studio. Můžete ale zajímat zobrazení upozornění analýzy kódu pro všechny soubory v konkrétním projektu nebo řešení. Pokud ano, chcete aktivovat analýzu kódu jednou na projektu nebo řešení. Alternativně můžete povolit průběžnou živou analýzu kódu pro spuštění v celém řešení. Další informace naleznete v tématu [How to: Configure Live Code Analysis Scope for Managed Code](./configure-live-code-analysis-scope-managed-code.md).
- Můžete preferovat pracovní postup provádění analýzy kódu na vyžádání přes průběžnou analýzu za provozu nebo analýzu doby sestavení. V takovém případě můžete vypnout spuštění analyzátoru během analýzy za provozu nebo sestavení. Informace o zakázání analýzy najdete v tématu [Jak zakázat analýzu zdrojového kódu](disable-code-analysis.md). Pak byste chtěli ručně aktivovat analýzu kódu na projektu nebo řešení. 

### <a name="run-code-analysis-manually"></a>Ruční spuštění analýzy kódu

1. V **Průzkumník řešení**klikněte na projekt.

2. V nabídce **analyzovat** klikněte na možnost **Spustit analýzu kódu na** *název projektu*.

Analýza kódu začne spouštět na pozadí. V levém dolním rohu by se měla zobrazit zpráva **spuštění analýzy kódu pro \<project> ...** ve stavovém řádku sady Visual Studio. Po dokončení analýzy kódu se stavová zpráva změní na **analýzu kódu dokončenou pro \<project> **. Seznam chyb bude brzy aktualizován všemi diagnostikami analýzy kódu.
