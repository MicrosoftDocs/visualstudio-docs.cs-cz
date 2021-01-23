---
title: Použití pravidel výkonu k analýze dat | Microsoft Docs
description: Zjistěte, jak upozornění na výkon sady Visual Studio Nástroje pro profilaci indikují problémy v profilované aplikaci, která může zpomalit spuštění programu.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9a896e128f949897b64fd6a273784f39543a9663
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721135"
---
# <a name="use-performance-rules-to-analyze-data"></a>Použití pravidel výkonu k analýze dat
Upozornění na výkon [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci indikují problémy v profilované aplikaci, která může zpomalit spuštění programu. Upozornění mohou také indikovat, že možná budete muset změnit metody kolekce a shromažďovat tak užitečnější data. Upozornění na výkon se generují automaticky v relaci profilace. Při otevření datového souboru profilování v aplikaci Visual Studio se v okně **Seznam chyb** zobrazí upozornění. V okně **Seznam chyb** můžete najít zdrojový kód problému a můžete zobrazit podrobné informace o chybě, například informace o tom, jak tento problém vyřešit. Můžete také zakázat upozornění, u kterých nejste zajímat.

> [!NOTE]
> Upozornění výkonu profileru jsou generována dynamickou analýzou spuštění programu a jsou nezávislá na upozorněních analýzy kódu. Analýza kódu může také generovat upozornění na výkon pro spravovaný kód na základě statické analýzy zdrojového kódu. Další informace najdete v tématu [Analýza kvality spravovaného kódu](../code-quality/code-analysis-for-managed-code-overview.md) a [Upozornění výkonu](/dotnet/fundamentals/code-analysis/quality-rules/performance-warnings).

## <a name="in-this-section"></a>V této části
- [Postupy: zobrazení upozornění výkonu](../profiling/how-to-view-performance-warnings.md)

 Poskytuje informace o tom, jak otevřít okno **Seznam chyb** pro zobrazení upozornění výkonu profileru.

- [Postupy: Konfigurace pravidel výkonu](../profiling/how-to-configure-performance-rules.md)

 Poskytuje informace o tom, jak zapnout nebo vypnout jednotlivá upozornění na výkon.

- [Referenční dokumentace pravidel výkonu](../profiling/performance-rules-reference.md)

 Poskytuje podrobné informace o upozorněních týkajících se výkonu profileru.
