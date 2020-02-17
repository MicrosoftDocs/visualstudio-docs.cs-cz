---
title: 'Postupy: nastavení vlastností analýzy kódu proC++ projekty v jazyce C | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b2fb3cb81b49fd4b8cc83e0548110d2025c7488d
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277983"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Postupy: Nastavení vlastností analýzy kódu pro projekty C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nakonfigurovat, která pravidla Nástroj pro analýzu kódu používá pro analýzu kódu v každé konfiguraci projektu. Kromě toho můžete směrovat analýzu kódu pro potlačení upozornění z kódu, který byl vygenerován a přidán do projektu nástrojem třetí strany.  
  
## <a name="code-analysis-property-page"></a>Stránka vlastností analýzy kódu  
 Stránka vlastností **Analýza kódu** obsahuje všechna nastavení konfigurace analýzy kódu pro projekt. Chcete-li otevřít stránku vlastností analýzy kódu pro projekt v **Průzkumník řešení**, klikněte pravým tlačítkem myši na projekt a potom klikněte na příkaz **vlastnosti**. Dále rozbalte položku **Vlastnosti konfigurace** a vyberte kartu **Analýza kódu** .  
  
## <a name="project-configuration-and-platform"></a>Konfigurace a platforma projektu  
 Seznam **konfigurací** a seznam **platforem** umožňuje použít různá nastavení analýzy kódu pro různé konfigurace projektu a kombinace platforem. Například můžete směrovat analýzu kódu a použít jednu sadu pravidel pro projekt pro sestavení pro ladění a jinou sadu pro sestavení vydaných verzí.  
  
## <a name="enabling-code-analysis"></a>Povolení analýzy kódu  
 Můžete se rozhodnout, jestli chcete pro svůj projekt povolit analýzu kódu, a to tak, že vyberete **možnost povolit analýzu kódu pro sestavení C/C++ on**. V kombinaci se seznamem **konfigurací** můžete například rozhodnout zakázat analýzu kódu pro sestavení ladění a povolit ji pro sestavení vydaných verzí.  
  
 Pokud projekt obsahuje spravovaný kód, můžete rozhodnout, zda chcete povolit nebo zakázat analýzu kódu výběrem možnosti **Povolit analýzu kódu při sestavení**.  
  
 Analýza kódu je navržena tak, aby vám pomohla zlepšit kvalitu kódu a vyhnout se běžným nástrah. Proto pečlivě zvažte, zda chcete zakázat analýzu kódu. Obvykle je lepší zakázat sady pravidel nebo jednotlivá pravidla, která nechcete použít pro váš projekt.  
  
## <a name="generated-code"></a>Generovaný kód  
 Vývojáři často používají nástroje k rychlému vývoji aplikací. Tyto nástroje mohou vygenerovat kód, který je přidán do projektu. Je možné, že budete chtít zobrazit porušení pravidel, která analýza kódu zjistí v generovaném kódu. Můžete je však nechtít zobrazit, pokud nechcete kód zachovat.  
  
 Zaškrtávací políčko **Potlačit výsledky z vygenerovaného kódu** na stránce **Obecné** vlastnosti umožňuje vybrat, zda chcete zobrazit upozornění analýzy kódu ze spravovaného kódu, který je generován nástrojem třetí strany.  
  
## <a name="rule-sets"></a>Sady pravidel  
 Pokud projekt obsahuje spravovaný kód, můžete vybrat pravidla, která se mají použít při analýze kódu výběrem sady pravidel ze seznamu **Spustit sadu pravidel** .  
  
## <a name="see-also"></a>Viz také  
 [Analýza spravovaného kódu  kvality](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 [Upozornění Analýzy kódu pro C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)
