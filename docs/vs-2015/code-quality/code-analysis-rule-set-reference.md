---
title: Referenční dokumentace sady pravidel analýzy kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e480869d5b13ecc051deaa97b0bfd2532519d18f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535717"
---
# <a name="code-analysis-rule-set-reference"></a>Referenční dokumentace sady pravidel nástroje Analýza kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při konfiguraci analýzy kódu pro projekty spravovaného kódu v [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] , [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] nebo [!INCLUDE[vsPro](../includes/vspro-md.md)] se zobrazí seznam předdefinovaných *sad pravidel*. Můžete použít jednu ze standardních sad pravidel nebo sadu pravidel upravit a přizpůsobit ji požadavkům projektu.

## <a name="available-rule-sets"></a>Dostupné sady pravidel
 V následující tabulce jsou uvedeny výchozí sady pravidel:

|Položka|Hodnota|
|-|-|
|[Sada pravidel Všechna pravidla](../code-quality/all-rules-rule-set.md)|Tato sada pravidel obsahuje všechna pravidla. Spuštění této sady pravidel může způsobit, že se nahlásí velký počet upozornění. Tato sada pravidel se používá k získání přehledu o všech problémech v kódu. To vám může pomáhat při rozhodování, které z lépe zaměřené sady pravidel jsou nejvhodnější pro spuštění pro vaše projekty.|
|[Sada pravidel Základní pravidla správnosti pro spravovaný kód](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Tato pravidla se zaměřují na logické chyby a běžné chyby provedené v použití rozhraní API rozhraní .NET Framework. Zahrňte tuto sadu pravidel, abyste ji rozbalíte na seznam upozornění hlášených minimálními doporučenými pravidly.|
|[Sada pravidel Základní pravidla obecných zásad návrhu pro spravovaný kód](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Tato pravidla se zaměřují na vynucování osvědčených postupů, které usnadňují pochopení a používání kódu. Zahrňte tuto sadu pravidel, pokud váš projekt obsahuje kód knihovny nebo pokud chcete vymáhat osvědčené postupy pro snadno udržovatelný kód.|
|[Sada pravidel Rozšířená pravidla správnosti pro spravovaný kód](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Tato pravidla rozšiřují základní pravidla správnosti, aby bylo možné maximalizovat logiku a chyby využití architektury, které jsou hlášeny. Další důraz je kladen na konkrétní scénáře, jako je komunikace s objekty COM a mobilní aplikace. Zvažte zahrnutí této sady pravidel, pokud se jeden z těchto scénářů vztahuje na váš projekt nebo pokud chcete najít další problémy v projektu.|
|[Sada pravidel Rozšířená pravidla pokynů návrhu pro spravovaný kód](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Tato pravidla rozšiřují základní pravidla obecných zásad návrhu, aby se maximalizovala chyba použitelnosti a udržovatelnosti, které jsou hlášeny. Dodatečné zdůraznění se řídí pokyny pro pojmenování. Zvažte zahrnutí této sady pravidel, pokud váš projekt obsahuje kód knihovny nebo pokud chcete vymáhat nejvyšší standardy pro zápis udržovatelného kódu.|
|[Sada pravidel Pravidla globalizace pro spravovaný kód](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Tato pravidla se zaměřují na problémy, které zabraňují správnému zobrazení dat v aplikaci při použití v různých jazycích, národních prostředích a jazykových verzích. Zahrňte tuto sadu pravidel, pokud je vaše aplikace lokalizovaná nebo globální.|
|[Sada pravidel Spravovaná minimální pravidla pro spravovaný kód](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Tato pravidla se zaměřují na nejdůležitější problémy v kódu, pro které je analýza kódu nejpřesnější.  Tato pravidla jsou malá v čísle a jsou určena pouze pro běh v omezeném vydání sady Visual Studio.  Použijte MinimumRecommendedRules. ruleset s ostatními edicemi sady Visual Studio.|
|[Sada pravidel Spravovaná doporučená pravidla pro spravovaný kód](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Tato pravidla se zaměřují na nejdůležitější problémy v kódu, včetně možných bezpečnostních otvorů, chyb aplikací a dalších důležitých chyb logiky a návrhu. Tuto sadu pravidel byste měli zahrnout v jakékoli vlastní sadě pravidel, kterou vytvoříte pro vaše projekty.|
|[Sada pravidel Smíšená minimální pravidla](../code-quality/mixed-minimum-rules-rule-set.md)|Tato pravidla se zaměřují na nejdůležitější problémy v projektech C++, které podporují modul CLR (Common Language Runtime), včetně možných bezpečnostních děr a chyb aplikací. Tuto sadu pravidel byste měli zahrnout v jakékoli vlastní sadě pravidel, kterou vytvoříte pro projekty C++, které podporují modul CLR (Common Language Runtime).|
|[Sada pravidel Smíšená doporučená pravidla](../code-quality/mixed-recommended-rules-rule-set.md)|Tato pravidla se zaměřují na nejběžnější a kritické problémy v projektech C++, které podporují modul CLR (Common Language Runtime), včetně možných bezpečnostních děr, chyb aplikací a dalších důležitých chyb logiky a návrhu. Tuto sadu pravidel byste měli zahrnout v jakékoli vlastní sadě pravidel, kterou vytvoříte pro projekty C++, které podporují modul CLR (Common Language Runtime).  Tento RuleSet je navržený tak, aby byl nakonfigurovaný s edicí Visual Studio Professional a vyšší.|
|[Sada pravidel Nativní minimální pravidla](../code-quality/native-minimum-rules-rule-set.md)|Tato pravidla se soustředí na nejdůležitější problémy v nativním kódu, včetně možných bezpečnostních děr a selhání aplikace. Tuto sadu pravidel byste měli zahrnout v jakékoli vlastní sadě pravidel, kterou vytvoříte pro vaše nativní projekty.|
|[Sada pravidel Nativní doporučená pravidla](../code-quality/native-recommended-rules-rule-set.md)|Tato pravidla se zaměřují na nejdůležitější a běžné problémy v nativním kódu, včetně možných bezpečnostních děr a chyb aplikací.  Tuto sadu pravidel byste měli zahrnout v jakékoli vlastní sadě pravidel, kterou vytvoříte pro vaše nativní projekty.  Tato RuleSet je navržená tak, aby spolupracovala s edicí Visual Studio Professional a vyšší.|
|[Sada pravidel Pravidla zabezpečení pro spravovaný kód](../code-quality/security-rules-rule-set-for-managed-code.md)|Tato sada pravidel obsahuje všechna pravidla zabezpečení společnosti Microsoft. Zahrňte tuto sadu pravidel, aby se maximalizoval počet potenciálních chyb zabezpečení, které jsou hlášeny.|
