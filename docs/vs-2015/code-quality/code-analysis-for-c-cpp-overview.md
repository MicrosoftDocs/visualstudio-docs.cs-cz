---
title: Analýza kódu pro C / C++ – přehled | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f7261b0bab423aa851b44ec725ca1c2818da9319
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763583"
---
# <a name="code-analysis-for-cc-overview"></a>Přehled Analýzy kódu pro C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj Analýza kódu C/C++ poskytuje informace pro vývojáře o možných chyb v jejich zdrojový kód C/C++. Běžné chyby kódování, kterou nástroj hlásí zahrnout přetečení vyrovnávací paměti, neinicializovaná paměť, přístupů přes ukazatel, ukazatel s hodnotou null a nevracení paměti a prostředků.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integrace integrovaného vývojového prostředí (IDE)  
 Chcete-li přirozené vývojáři mohou použít nástroj pro analýzu, je plně integrovaná v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí. Během procesu sestavování všechna upozornění vygenerované pro zdrojový kód se zobrazí v seznamu chyb. Můžete přejít na zdrojový kód, který způsobil toto upozornění, a můžete zobrazit další informace o příčině a řešení problému.  
  
## <a name="pragma-support"></a>#pragma podpory  
 Vývojáři mohou použít `#pragma` směrnice zpracovávat upozornění jako chyby; povolit nebo zakázat upozornění a potlačení upozornění pro jednotlivé řádky kódu. Další informace najdete v tématu [postupy: povolení a zakázání upozornění analýzy kódu pro konkrétní C/C++](http://msdn.microsoft.com/en-us/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Podpora poznámky  
 Poznámky zlepšit přesnost analýzy kódu. Poznámky poskytují další informace o provedení před instrumentací a po podmínky na funkčních parametrů a návratové typy. Další informace najdete v tématu [postupy: určení dalších informací o kódu pomocí __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Spusťte nástroj pro analýzu jako součást zásady vrácení se změnami  
 Můžete chtít vyžadovat, aby všechny zdrojový kód vrácení se změnami splňovala určitá kritéria. Zejména budete chtít Ujistěte se, že analýza byla spuštěna jako krok pro nejnovější sestavení místní. Další informace o povolení zásady analýzy kódu vrácení se změnami naleznete v tématu [vytváření a používání vrácení se změnami zásad analýzy kódu](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Integrace týmového sestavení  
 Můžete použít integrované funkce systému sestavení ke spuštění jako krok pro nástroj pro analýzu kódu [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] procesu sestavení. Další informace najdete v tématu [sestavte aplikaci](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Nástroje příkazového řádku  
 Kromě úplné integrace v rámci vývojového prostředí vývojáři použít také nástroj pro analýzu z příkazového řádku, jak je znázorněno v následujícím příkladu:  
  
 `C:\>cl /analyze Sample.cpp`



