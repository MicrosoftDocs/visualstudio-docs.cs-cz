---
title: Přehled Analýzy kódu pro C/C++
ms.date: 04/28/2018
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 493db26aed1a4e5f41acdd054dba266577159809
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018486"
---
# <a name="code-analysis-for-cc-overview"></a>Analýza kódu pro C/C++ přehled

Nástroj Analýza kóduC++ v jazyce c/a poskytuje informace o možných chybách ve vašemC++ kódu C/source. Běžné chyby kódování hlášené nástrojem zahrnují přetečení vyrovnávací paměti, neinicializovaná paměť, zpětné odkazy na ukazatel s hodnotou null a paměti a nevrácené prostředky. Nástroj může také spustit kontroly se [ C++ základními pokyny](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integrace integrovaného vývojového prostředí (IDE)

Nástroj pro analýzu kódu je plně integrovaný v rámci integrovaného vývojového prostředí (IDE) sady Visual Studio.

Během procesu sestavení se všechna upozornění vygenerovaná pro zdrojový kód zobrazí v Seznam chyb. Můžete přejít ke zdrojovému kódu, který způsobil upozornění, a můžete si Zobrazit další informace o příčině a možných řešeních problému.

## <a name="command-line-support"></a>Podpora příkazového řádku

Nástroj pro analýzu můžete použít také z příkazového řádku, jak je znázorněno v následujícím příkladu:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 verze 15,7 a novější** Nástroj můžete spustit z příkazového řádku s libovolným systémem sestavení včetně CMake.

## <a name="pragma-support"></a>Podpora #pragma

Pomocí direktivy `#pragma` můžete zacházet s upozorněními jako s chybami. Povolit nebo zakázat upozornění a potlačit upozornění pro jednotlivé řádky kódu. Další informace naleznete v tématu [direktivy pragma a klíčové slovo __pragma](https://docs.microsoft.com/cpp/preprocessor/pragma-directives-and-the-pragma-keyword).

## <a name="annotation-support"></a>Podpora poznámek

Poznámky zlepšují přesnost analýzy kódu. Poznámky poskytují další informace o parametrech funkce a návratových typech pro podmínky a ujednání. Další informace najdete v tématu [Použití poznámek SAL ke snížení vad CC++ /kódu](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md).

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Spustit nástroj pro analýzu jako součást zásady vracení se změnami

Možná budete chtít vyžadovat, aby všechna vrácení se změnami zdrojového kódu splňovala určité zásady. Konkrétně je potřeba zajistit, aby byla analýza spuštěna jako krok posledního místního sestavení. Další informace o povolení zásad vrácení se změnami analýzy kódu naleznete v tématu [vytváření a používání zásad vrácení se změnami analýzy kódu](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integrace sestavení týmu

Pomocí integrovaných funkcí systému sestavení lze nástroj pro analýzu kódu spustit jako krok procesu sestavení [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Další informace najdete v tématu [kanály Azure](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Viz také:

- [Rychlý start: Analýza kódu pro C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Návod: Analyzovat C/C++ kód pro vady @ no__t-1
- [Upozornění Analýzy kódu pro C/C++](code-analysis-for-c-cpp-warnings.md)
- [Použití kontrolních mechanismů C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [C++Reference k základní kontrole – referenční pokyny](code-analysis-for-cpp-corecheck.md)
- [Určení pravidel C++, která se mají spustit, pomocí sad pravidel](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analýza kvality ovladače pomocí nástrojů pro analýzu kódu](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Upozornění analýzy kódu pro ovladače](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
