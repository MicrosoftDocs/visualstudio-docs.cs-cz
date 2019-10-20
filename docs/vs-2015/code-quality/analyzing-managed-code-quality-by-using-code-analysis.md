---
title: Analýza kvality spravovaného kódu pomocí analýzy kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d5f0646f26226e9895414db512681e0a7a71faa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671119"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analýza kvality spravovaného kódu pomocí nástroje Analýza kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li zjistit možná rizika v kódu, jako je například nezabezpečený přístup k datům, narušení ochrany použití a problémy návrhu, můžete použít nástroje pro analýzu kódu sady Visual Studio. Analýza kódu funguje na .NET Framework, nativních (C C++a) a databázových aplikacích. Analýza kódu pro spravovaný kód organizuje pravidla v *sadách pravidel* , která cílí na konkrétní problémy s kódováním.

## <a name="common-tasks"></a>Obecné úlohy

|Obecné úlohy|Podpůrný obsah|
|------------------|------------------------|
|**Získat praktickou praxi:** Seznamte se se základy analýzy kódu opravou vad v jednoduché aplikaci .NET Framework.|-   [Návod: Analýza spravovaného kódu pro vady kódu](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|
|**Konfigurace analýzy kódu pro projekt:** Pravidla pro spravovaný kód jsou uspořádána do sad pravidel, které cílí na konkrétní oblasti, jako je například zabezpečení a návrh. Můžete použít jednu ze standardních sad pravidel společnosti Microsoft nebo vytvořit vlastní.|[Přehled analýzy kódu -    pro spravovaný kód](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [použití sad pravidel k seskupení pravidel analýzy kódu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [potlačit upozornění pomocí atributu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|
|**Spustit analýzu kódu:** Můžete určit, aby se analýza kódu spouštěla automaticky pokaždé, když je sestavena konfigurace projektu, a můžete spustit analýzu kódu ručně v projektu.|-   [Postupy: povolení a zákaz automatické analýzy kódu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Postupy: ruční spuštění analýzy kódu](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|
|**Analyzovat výsledky analýzy kódu:** Upozornění analýzy kódu a chyby jsou uvedeny v okně Analýza kódu. Můžete zvolit upozornění nebo název chyby pro zobrazení dalších informací o upozornění a pro zobrazení a zvýraznění řádku zdrojového kódu, který pravidlo vyvolalo. Můžete zvolit ID upozornění pro zobrazení podrobných informací v knihovně MSDN, která obsahuje informace a příklady, jak tento problém vyřešit.|-   [Postupy: zobrazení vad spravovaného kódu](../code-quality/how-to-view-managed-code-defects.md)<br />[upozornění analýzy kódu -    pro spravovaný kód](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [upozornění podle CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [anonymní metody a analýza kódu](../code-quality/anonymous-methods-and-code-analysis.md)|
|**Integrace analýzy kódu s životním cyklem vývoje:** Zásady vrácení se změnami v [!INCLUDE[esprscc](../includes/esprscc-md.md)] umožňují vývojovým týmům zajistit, aby všechna vrácení se změnami kódu splňovala společnou sadu standardů pro analýzu kódu. Vytvoření pracovní položky pro porušení pravidla analýzy kódu je jednoduchý postup, který lze provést v okně Seznam chyb.|-   [zvyšování kvality kódu pomocí zásad vracení zpět se změnami týmového projektu](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Postupy: synchronizace sady pravidel projektu kódu se zásadou vrácení se změnami týmového projektu](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Postupy: vytvoření pracovní položky pro vadu spravovaného kódu](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
