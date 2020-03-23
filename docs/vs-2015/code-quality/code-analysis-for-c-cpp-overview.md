---
title: Analýza kódu pro C-C++ Přehled | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
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
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 1ce41cd1c0dabc94658b83aa5e2bcdc08d005fdb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77275368"
---
# <a name="code-analysis-for-cc-overview"></a>Přehled Analýzy kódu pro C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj c/c++ analýzy kódu poskytuje vývojářům informace o možných vadách ve zdrojovém kódu C/C++. Běžné chyby kódování hlášené nástrojem zahrnují přetečení vyrovnávací paměti, neinicializovanou paměť, dereference ukazatele null a nevracení paměti a prostředků.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integrace IDE (integrované vývojové prostředí)  
 Aby bylo přirozené, že vývojáři používají analytický nástroj, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je plně integrován do integrovaného vývojového prostředí. Během procesu sestavení se všechna upozornění generovaná pro zdrojový kód zobrazí v seznamu chyb. Můžete přejít na zdrojový kód, který způsobil upozornění a můžete zobrazit další informace o příčině a možných řešeních problému.  
  
## <a name="pragma-support"></a>podpora #pragma  
 Vývojáři mohou `#pragma` použít direktivu k tomu, aby s upozorněními zacházeli jako s chybami. povolit nebo zakázat upozornění a potlačit upozornění pro jednotlivé řádky kódu. Další informace naleznete v [tématu How to: Enable and Disable Code Analysis for Specific C/C++ Warnings](https://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Podpora poznámky  
 Anotace zlepšují přesnost analýzy kódu. Poznámky poskytují další informace o předa post-podmínky na parametry funkce a návratové typy. Další informace naleznete v [tématu How to: Specify Additional Code Information by Using __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Spustit analytický nástroj jako součást zásad vrácení se změnami  
 Můžete chtít požadovat, aby všechny vrácení se změnami zdrojového kódu splňovalo určité zásady. Zejména chcete zajistit, že analýza byla spuštěna jako krok nejnovější místní sestavení. Další informace o povolení zásad vrácení se změnami analýzy kódu naleznete v [tématu Vytváření a použití zásad vrácení se změnami analýzy kódu.](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Integrace sestavení týmu  
 Integrované funkce systému sestavení můžete použít ke spuštění nástroje pro [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] analýzu kódu jako krok procesu sestavení. Další informace naleznete [v tématu Sestavení aplikace](/azure/devops/pipelines/index).  
  
## <a name="command-line-support"></a>Podpora příkazového řádku  
 Kromě úplné integrace v rámci vývojového prostředí mohou vývojáři také použít analytický nástroj z příkazového řádku, jak je znázorněno v následujícím příkladu:  
  
 `C:\>cl /analyze Sample.cpp`
