---
title: Analýza kvality spravovaného kódu pomocí nástroje Analýza kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e034db6fc7383ea5f944900713dffe1cc3e78473
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263885"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analýza kvality spravovaného kódu pomocí nástroje Analýza kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li zjistit možná rizika v kódu, jako je například nezabezpečený přístup k datům, narušení ochrany použití a problémy návrhu, můžete použít nástroje pro analýzu kódu sady Visual Studio. Analýza kódu funguje v rozhraní .NET Framework, nativní (C a C++) a databázových aplikací. Pravidla analýzy kódu pro spravovaný kód slouží k uspořádání *sad pravidel* využívajících konkrétní chyby kódu.  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Obecné úlohy|Podpůrný obsah|  
|------------------|------------------------|  
|**Získání praktických postupů:** Seznamte se se základy analýzy kódu za účelem opravy chyb v jednoduché aplikace rozhraní .NET Framework.|-   [Návod: Analýza spravovaného kódu na výskyt závad kódu](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Konfigurace analýzy kódu pro projekt:** pravidla pro spravovaný kód jsou uspořádány do sady pravidel, které se zaměřují na konkrétní oblasti, jako je zabezpečení a návrh. Můžete použít jednu z Microsoft nastaví standardních pravidel nebo si vytvořte svoje vlastní.|-   [Analýza kódu pro spravovaný kód přehled](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Použití sad pravidel k seskupování pravidel analýzy kódu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Potlačení upozornění použitím atributu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Spuštění analýzy kódu:** zadáte analýza kódu ke spuštění automaticky pokaždé, když je sestavena konfigurace projektu a je možné ruční spuštění analýzy kódu na projektu.|-   [Postupy: povolení a zákaz automatické analýzy kódu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Postupy: ruční spuštění analýzy kódu](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analyzujte výsledky analýzy kódu:** upozornění analýzy kódu a chyby jsou uvedené v okně analýzy kódu. Můžete vybrat upozornění nebo nadpisech chyba zobrazíte další informace o upozornění a k zobrazení a zvýraznit řádky zdrojového kódu, která aktivuje pravidlo. Můžete použít id upozornění zobrazíte podrobné informace v knihovně MSDN, který obsahuje informace a příklady toho, jak problém vyřešit.|-   [Postupy: zobrazování defektů spravovaného kódu](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Analýza kódu pro spravovaný kód upozornění](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Upozornění podle CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Anonymní metody a analýza kódu](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Integrace analýzy kódu se váš životní cyklus vývoje:** zásady vrácení se změnami v [!INCLUDE[esprscc](../includes/esprscc-md.md)] umožňují vývojovým týmům Ujistěte se, že všechny kódu vrácení se změnami splňovala veškeré běžné standardy analýzy kódu. Vytvoření pracovní položky pro porušení pravidel analýzy kódu je jednoduchý postup, který lze provést v okně Seznam chyb.|-   [Zlepšení kvality kódu pomocí zásady vracení se změnami projektu týmu](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Postupy: synchronizace sad pravidel projektu kódu pomocí zásady vracení se změnami projektu týmu](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Postupy: vytvoření pracovní položky pro vadu spravovaného kódu](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|



