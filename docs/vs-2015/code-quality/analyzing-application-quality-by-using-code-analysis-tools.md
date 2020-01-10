---
title: Analýza kvality aplikace pomocí nástrojů pro analýzu kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d4e45ade24ce792999d1f9b0f52d9c82703fc5a0
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849883"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analýza kvality aplikace pomocí nástrojů pro analýzu kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V této části [Analýza spravovaného](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) kódu sada Visual Studio Code Analysis pro spravovaný kód poskytuje informace o spravovaných sestaveních, jako jsou porušení pravidel programování a návrhu stanovených v pokynech pro návrh Microsoft .NET Framework. Varovné zprávy identifikují relevantní problémy s programováním a návrhem a, pokud je to možné, poskytují informace o tom, jak tento problém vyřešit.

 [Analýza kvality kóduC++ c/kódu pomocí nástroje Analýza kódu](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) nástroj CC++ /Code Analysis poskytuje vývojářům informace o možných chybách v kódu C/C++ source. Běžné chyby kódování hlášené nástrojem zahrnují přetečení vyrovnávací paměti, neinicializovaná paměť, zpětné odkazy na ukazatel s hodnotou null a paměti a nevrácené prostředky.

 [Použití sad pravidel k seskupení pravidel analýzy kódu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Vyberte a vytvořte *sady pravidel* , které chcete použít pro váš projekt.

 [Chyby aplikace analýzy kódu](../code-quality/code-analysis-application-errors.md) Opravte chyby ve funkci analýzy kódu.

 [Zvýšení kvality kódu pomocí zásad vracení zpět se změnami týmového projektu](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) Při použití Správa verzí Team Foundation (TFVC) můžete vytvořit zásady vracení se změnami pro týmové projekty, které vynutily postupy, které vedou k lepšímu kódu a efektivnějšímu vývoji skupin. Zásady vrácení se změnami jsou pravidla, která se nastavují na úrovni týmového projektu a vynutila v vývojářských počítačích před tím, než se kód může vrátit se změnami.

### <a name="code-analysis-for-drivers"></a>Analýza kódu pro ovladače
 Nástroje pro analýzu kódu mohou pomoci zlepšit stabilitu a spolehlivost svého ovladače systematickou analýzou zdrojového kódu ovladače.

 [Analýza kvality ovladače pomocí nástrojů pro analýzu kódu](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) Analýza kódu pro ovladače je nástroj pro statické ověření při kompilaci, který detekuje základní chyby kódování v jazyce C C++ a programech a obsahuje specializovaný modul, který je určen k detekci chyb v (primárně) kódu ovladače režimu jádra. SDV (static Driver Verifier) je statický ověřovací nástroj, který systematicky analyzuje zdrojový kód ovladačů režimu jádra systému Windows. SDV Určuje, zda ovladač správně spolupracuje s jádrem operačního systému Windows.

 [Upozornění analýzy kódu pro ovladače](https://msdn.microsoft.com/library/windows/hardware/ff550572(v=VS.85).aspx) Popisuje upozornění, která analyzuje kód pro ovladače, když detekuje možnou chybu v kódu ovladače.

## <a name="related-tasks"></a>Související úlohy
 [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Sem vložte popis.

 [Testování částí kódu](../test/unit-test-your-code.md) Sem vložte popis.
