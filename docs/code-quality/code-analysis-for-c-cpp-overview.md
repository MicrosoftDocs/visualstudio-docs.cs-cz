---
title: Přehled Analýzy kódu pro C/C++
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 35f694d9cc397800249dd9b4acd86bf63d22ad93
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320706"
---
# <a name="code-analysis-for-cc-overview"></a>Analýza kódu pro C/C++ – přehled

Nástroj Analýza kódu C/C++ poskytuje informace o možných chyb ve zdrojovém kódu C/C++. Běžné chyby kódování, kterou nástroj hlásí zahrnout přetečení vyrovnávací paměti, neinicializované paměti, přístupů přes ukazatel, ukazatel s hodnotou null a nevracení paměti a prostředků. Nástroj můžete spustit také kontroly proti [podle dokumentu C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integrace integrovaného vývojového prostředí (IDE)

Nástroj pro analýzu kódu je plně integrovaná v integrovaném vývojovém prostředí sady Visual Studio.

Během procesu sestavování všechna upozornění vygenerované pro zdrojový kód se zobrazí v seznamu chyb. Můžete přejít na zdrojový kód, který způsobil toto upozornění, a můžete zobrazit další informace o příčině a řešení problému.

## <a name="command-line-support"></a>Podporu příkazového řádku.

Můžete také použít nástroj analýzy z příkazového řádku, jak je znázorněno v následujícím příkladu:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 verze 15.7 nebo novější** nástroj můžete spustit z příkazového řádku s jakýmkoliv systémem sestavení včetně CMake.

## <a name="pragma-support"></a>Podpora #pragma

Můžete použít `#pragma` směrnice zpracovávat upozornění jako chyby; povolit nebo zakázat upozornění a potlačení upozornění pro jednotlivé řádky kódu. Další informace najdete v tématu [postupy: nastavení vlastností analýzy kódu pro projekty C/C++](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Podpora poznámky

Poznámky zlepšit přesnost analýzy kódu. Poznámky poskytují další informace o provedení před instrumentací a po podmínky na funkčních parametrů a návratové typy. Další informace najdete v tématu [postupy: určení dalších informací o kódu pomocí __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Spusťte nástroj pro analýzu jako součást zásady vrácení se změnami

Můžete chtít vyžadovat, aby všechny zdrojový kód vrácení se změnami splňovala určitá kritéria. Zejména budete chtít Ujistěte se, že analýza byla spuštěna jako krok pro nejnovější sestavení místní. Další informace o povolení zásady analýzy kódu vrácení se změnami naleznete v tématu [vytváření a používání vrácení se změnami zásad analýzy kódu](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Integrace týmového sestavení

Můžete použít integrované funkce systému sestavení ke spuštění jako krok pro nástroj pro analýzu kódu [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] procesu sestavení. Další informace najdete v tématu [kanály Azure](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Viz také:

- [Rychlý start: Analýza kódu pro C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Návod: Analýza závad kódu C/C++](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Upozornění Analýzy kódu pro C/C++](code-analysis-for-c-cpp-warnings.md)
- [Použití kontrolních mechanismů C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [Referenční dokumentace pro kontrolu požadovaných součástí C++ Core Guidelines](code-analysis-for-cpp-corecheck.md)
- [Určení pravidel C++, která se mají spustit, pomocí sad pravidel](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analýza kvality ovladač pomocí nástrojů pro analýzu kódu](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Ovladače upozornění analýzy kódu pro](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
