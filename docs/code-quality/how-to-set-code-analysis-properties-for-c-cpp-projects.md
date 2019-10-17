---
title: 'Postupy: Nastavení vlastností analýzy kódu pro projekty C/C++'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 27f3d68d28b8d1799c52fcf83c6a00dc5f81f48a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448913"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Postupy: Nastavení vlastností analýzy kódu pro projekty C/C++

Můžete nakonfigurovat, která pravidla Nástroj pro analýzu kódu používá pro analýzu kódu v každé konfiguraci projektu. Kromě toho můžete směrovat analýzu kódu pro potlačení upozornění z kódu, který byl vygenerován a přidán do projektu nástrojem třetí strany.

## <a name="code-analysis-property-page"></a>Stránka vlastností analýzy kódu

Stránka vlastností **Analýza kódu** obsahuje všechna nastavení konfigurace analýzy kódu pro projekt MSBuild. Chcete-li otevřít stránku vlastností analýzy kódu pro projekt v **Průzkumník řešení**, klikněte pravým tlačítkem myši na projekt a potom klikněte na příkaz **vlastnosti**. Dále rozbalte položku **Vlastnosti konfigurace** a vyberte kartu **Analýza kódu** .

## <a name="project-configuration-and-platform"></a>Konfigurace a platforma projektu

Seznam **konfigurací** a seznam **platforem** v horní části okna umožňuje použít různá nastavení analýzy kódu pro různé konfigurace projektu a kombinace platforem. Například můžete směrovat analýzu kódu a použít jednu sadu pravidel pro projekt pro sestavení pro ladění a jinou sadu pro sestavení vydaných verzí.

## <a name="enabling-code-analysis"></a>Povolení analýzy kódu

Můžete povolit analýzu kódu pro váš projekt přepnutím na možnost **Povolit analýzu kódu společnosti Microsoft** a **Povolit možnosti Clang-uklizený** a dále konfigurovat, pokud se spustí na buildu výběrem možnosti **Povolit analýzu kódu při sestavení**. V kombinaci se seznamem **konfigurací** můžete například rozhodnout zakázat analýzu kódu pro sestavení ladění a povolit ji pro sestavení vydaných verzí.

Analýza kódu je navržena tak, aby vám pomohla zlepšit kvalitu kódu a vyhnout se běžným nástrah. Proto pečlivě zvažte, zda chcete zakázat analýzu kódu. Je obvykle lepší zakázat sady pravidel, jednotlivá pravidla nebo jednotlivé kontroly, které nechcete použít pro váš projekt.

## <a name="cmake-configuration"></a>Konfigurace CMake

V projektech CMake změňte hodnotu `enableMicrosoftCodeAnalysis` a klíče `enableClangTidyCodeAnalysis` v rámci `CMakeSettings.json` pro povolení nebo zakázání analýzy kódu. Další informace najdete [v tématu použití Clang-uklizený v aplikaci Visual Studio](../code-quality/clang-tidy.md) .

## <a name="see-also"></a>Viz také:

- [Analýza kvality spravovaného kódu](../code-quality/code-analysis-for-managed-code-overview.md)
- [Upozornění Analýzy kódu pro C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)
- [Sady pravidel pro C++ kód](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Použití Clang-uklizený](../code-quality/clang-tidy.md)
