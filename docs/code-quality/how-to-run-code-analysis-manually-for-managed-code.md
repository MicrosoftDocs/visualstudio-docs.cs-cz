---
title: 'Postup: Ruční spuštění analýzy kódu pro spravovaný kód'
ms.date: 11/04/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5fdeb56a0c0f4c5904a00ec53d64dae87aa4e9a5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431381"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Postup: Ruční spuštění analýzy kódu pro spravovaný kód (vyžaduje Visual Studio 2019 verze 16.5 nebo novější)
Ve výchozím nastavení analyzátory kódu .NET Compiler Platform ("Roslyn") analyzátory kódu analyzovat váš kód Jazyka C# nebo Visual Basic při psaní provádí živé analýzy, stejně jako během sestavení. Proto byste za normálních okolností nevyžadovali ruční aktivaci analýzy kódu. Existují však některé scénáře, kde můžete chtít ručně spustit analýzu kódu:

- Ve výchozím nastavení spustí analýza živého kódu analyzátory pouze pro otevřené soubory v sadě Visual Studio. Může však být zájem o zobrazení upozornění analýzy kódu pro všechny soubory v konkrétním projektu nebo řešení. Pokud ano, měli byste spustit analýzu kódu jednou na projektu nebo řešení. Alternativně můžete povolit nepřetržitou analýzu živého kódu pro spuštění celého řešení. Další informace naleznete v [tématu Postup: Konfigurace oboru analýzy živého kódu pro spravovaný kód](./configure-live-code-analysis-scope-managed-code.md).
- Můžete dát přednost pracovnímu postupu provádění analýzy kódu na vyžádání před průběžnou analýzou živého provozu nebo analýzou v době sestavení. Pokud ano, můžete zakázat spuštění analyzátoru během živé analýzy nebo sestavení. Informace o zakázání analýzy naleznete v tématu [Jak zakázat analýzu zdrojového kódu](disable-code-analysis.md). Pak byste chtěli ručně aktivovat analýzu kódu jednou na projektu nebo řešení. 

### <a name="run-code-analysis-manually"></a>Ruční spuštění analýzy kódu

1. V **Průzkumníku řešení**klikněte na projekt.

2. V nabídce **Analyzovat** klepněte na **položku Spustit analýzu kódu v nabídce** *Název projektu*.

Analýza kódu se spustí na pozadí. Měli byste vidět zprávu **Spuštění \<analýzy kódu pro> projektu...** ve stavovém řádku sady Visual Studio směrem k levému dolnímu rohu. Po dokončení analýzy kódu se stavová zpráva změní na **Analýzu kódu \<dokončenou pro>projektu **. Seznam chyb se brzy obnoví se všemi diagnostikami analýzy kódu.
