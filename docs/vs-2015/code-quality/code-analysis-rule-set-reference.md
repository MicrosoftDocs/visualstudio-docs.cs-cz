---
title: Referenční dokumentace sady pravidel nástroje Analýza kódu | Dokumentace Microsoftu
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
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 928b838a4172537ec12937b02c3deab2cf666ddd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279159"
---
# <a name="code-analysis-rule-set-reference"></a>Referenční dokumentace sady pravidel nástroje Analýza kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při konfiguraci analýzy kódu pro projekty spravovaného kódu v [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], nebo [!INCLUDE[vsPro](../includes/vspro-md.md)], zobrazí se seznam předdefinovaných *sad pravidel*. Můžete použít jednu ze standardních sad pravidel nebo sadu pravidel upravit a přizpůsobit ji požadavkům projektu.  
  
## <a name="available-rule-sets"></a>Sad pravidel k dispozici  
 V následující tabulce jsou uvedeny výchozí sady pravidel:  
  
|||  
|-|-|  
|[Sada pravidel Všechna pravidla](../code-quality/all-rules-rule-set.md)|Tato sada pravidel obsahuje všechna pravidla. Spuštění této sady pravidel může mít za následek velké množství hlášených upozornění. Pomocí tohoto pravidla nastavena na získání úplné představy o všech problémech v kódu. To může pomoct při rozhodování, které z více zaměřených pravidlo sady jsou nejvhodnější pro spuštění pro vaše projekty.|  
|[Sada pravidel Základní pravidla správnosti pro spravovaný kód](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Tato pravidla se soustředí na logické chyby a obvyklé omyly při používání architektury API. Zahrnout tuto sadu rozšířit seznam upozornění hlášených Minimální doporučená pravidla pravidel.|  
|[Sada pravidel Základní pravidla obecných zásad návrhu pro spravovaný kód](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Tato pravidla se soustředí na prosazování osvědčených postupů, které umožní váš kód snadno pochopitelný a. Zahrnout tuto sadu Pokud váš projekt zahrnuje kód knihovny nebo pokud chcete vynutit doporučené postupy pro snadno udržovatelný kód pravidel.|  
|[Sada pravidel Rozšířená pravidla správnosti pro spravovaný kód](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Tato pravidla rozšiřují základní pravidla správnosti pro maximalizaci logiku a framework chyby využití, které jsou hlášeny. Je kladen zvláštní důraz na konkrétní scénáře, jako jsou spolupráce a mobilní aplikace modelu COM. Zvažte zahrnutí této sady, pokud jeden z těchto scénářů vztahuje k vašemu projektu nebo pro nalezení dalších problémů ve vašem projektu pravidel.|  
|[Sada pravidel Rozšířená pravidla pokynů návrhu pro spravovaný kód](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Tato pravidla rozšiřují základní návrhu pravidla obecných zásad pro maximalizaci problémů použitelnosti a udržovatelnosti, které jsou hlášeny. Je kladen zvláštní důraz na pokyny pro pojmenování. Zvažte zahrnutí této sady, pokud váš projekt zahrnuje kód knihovny nebo pokud chcete zajistit nejvyšší standardy pro psaní udržovatelného kódu pravidel.|  
|[Sada pravidel Pravidla globalizace pro spravovaný kód](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Tato pravidla se soustředí na problémy, které brání datům v aplikaci správnému zobrazování při použití v různých jazycích, národních prostředích a jazykových verzí. Zahrnout tuto sadu, pokud je vaše aplikace lokalizována nebo globalizována pravidel.|  
|[Sada pravidel Spravovaná minimální pravidla pro spravovaný kód](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Tato pravidla se soustředí na nejdůležitější problémy ve vašem kódu, pro kterou je analýza kódu nejpřesnější.  Tato pravidla jsou malá v číslech a jsou určeny pouze pro spuštění v omezené edice sady Visual Studio.  Použijte MinimumRecommendedRules.ruleset s jinými edicemi Visual Studia.|  
|[Sada pravidel Spravovaná doporučená pravidla pro spravovaný kód](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Tato pravidla se soustředí na nejdůležitější problémy v kódu, včetně možných bezpečnostních děr, selhání aplikace a jiných důležitých chyb logiky a návrhu. Měli byste zahrnout tuto sadu pravidel v jakékoli vlastní sadě pravidel, že kterou vytvoříte pro vaše projekty.|  
|[Sada pravidel Smíšená minimální pravidla](../code-quality/mixed-minimum-rules-rule-set.md)|Tato pravidla se soustředí na nejdůležitější problémy v projektech C++, které podporují modul Common Language Runtime, včetně možných bezpečnostních děr a selhání aplikace. Měli byste zahrnout tuto sadu pravidel v jakékoli vlastní sadě pravidel, že kterou vytvoříte pro vaše projekty C++, které podporují modul Common Language Runtime.|  
|[Sada pravidel Smíšená doporučená pravidla](../code-quality/mixed-recommended-rules-rule-set.md)|Tato pravidla se soustředí na nejběžnějších a kritické problémy v projektech C++, které podporují modul Common Language Runtime, včetně možných bezpečnostních děr, selhání aplikace a jiných důležitých chyb logiky a návrhu. Měli byste zahrnout tuto sadu pravidel v jakékoli vlastní sadě pravidel, že kterou vytvoříte pro vaše projekty C++, které podporují modul Common Language Runtime.  Tato sada pravidel je navržena ke konfiguraci s edicí sady Visual Studio Professional a vyšší.|  
|[Sada pravidel Nativní minimální pravidla](../code-quality/native-minimum-rules-rule-set.md)|Tato pravidla se soustředí na nejdůležitější problémy v nativním kódu, včetně možných bezpečnostních děr a selhání aplikace. Měli byste zahrnout tuto sadu pravidel v jakékoli vlastní sadě pravidel, že kterou vytvoříte pro vaše nativní projekty.|  
|[Sada pravidel Nativní doporučená pravidla](../code-quality/native-recommended-rules-rule-set.md)|Tato pravidla se soustředí na nejdůležitější a běžné problémy v nativním kódu, včetně možných bezpečnostních děr a selhání aplikace.  Měli byste zahrnout tuto sadu pravidel v jakékoli vlastní sadě pravidel, že kterou vytvoříte pro vaše nativní projekty.  Tato sada pravidel je navržena pro práci s edici sady Visual Studio Professional a vyšší.|  
|[Sada pravidel Pravidla zabezpečení pro spravovaný kód](../code-quality/security-rules-rule-set-for-managed-code.md)|Tato sada pravidel obsahuje všechna pravidla zabezpečení společnosti Microsoft. Zahrnout tuto sadu pro maximalizaci počtu možných problémů se zabezpečením, které jsou hlášeny pravidel.|



