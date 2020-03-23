---
title: 'Postup: Shromažďování údajů o vzorkování na úrovni řádku | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f64040c9180a152650de16b23276ab0e65cc9ead
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776355"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Postup: Shromažďování údajů o vzorkování na úrovni řádku
Vzorkování na úrovni řádku je schopnost profileru určit, kde v kódu funkce náročné na procesor, jako je například funkce, která má vysoké výhradní vzorky, procesor musí strávit většinu svého času.

## <a name="overview"></a>Přehled
 Pro vzorkování na úrovni řádku profileru prochází zásobník volání programu v nastavených intervalech a agreguje tyto výsledky. Tyto výsledky ukazují, jaké pokyny procesor prováděl při odběru vzorků. Shromážděná data o výhradní vzorky je pak analyzována k identifikaci řádky kódu a ukazatel instrukce (IP).

 Vzorkování na úrovni řádku funguje pro spravovaný i nativní kód. Sestavy výkonu, které zobrazují tato data, zahrnují zobrazení čáry a moduly.

 Informace o začátku/konci znaku nejsou k dispozici pro nativní kód. Pro víceřádkové příkazy nejsou informace o zahájení řádku k dispozici pro nativní kód; k dispozici jsou pouze informace o koncovém řádku.

### <a name="available-data"></a>Dostupné údaje
 Dostupné údaje o odběru vzorků na úrovni linky zahrnují tyto informace:

- Název funkce.

- Adresa funkce.

- Řádky začínají - číslo řádku vzorkovaného kódu.

- Konec řádku - koncové číslo řádku zdroje. To je obecně stejné jako data "Line begin" s výjimkou případů, kdy jeden příkaz programu zahrnuje více řádků zdrojového kódu.

- Znaky začínají - počáteční sloupec souhrnného vzorku. Toto je obecně 0 s výjimkou, pokud jeden řádek obsahuje více příkazů programu.

- Konec znaku - koncový sloupec souhrnného vzorku.

- IP - adresa, kde byl odebrán souhrnný vzorek (pouze zobrazení IP).

  V zobrazení **Moduly,** pokud funkce má statistiky na úrovni řádku, statistiky jsou vnořeny pod každou funkci. Kromě toho jsou uvedeny statistiky na úrovni IP, které jsou vnořeny pod každý řádek jsou uvedeny.

### <a name="turn-off-line-level-sampling-for-managed-code"></a>Vypnutí vzorkování na úrovni řádku pro spravovaný kód
 Ve výchozím nastavení je vzorkování na úrovni řádku zapnuto. Shromažďování dat na úrovni řádku pro spravovaný kód můžete vypnout pomocí jednoho z následujících příkazů:

- Před profilováním zadejte **VSPerfCLREnv /samplelineoff**. To má vliv na aplikace i služby.

     — nebo —

- Při spuštění aplikace zadejte **VSPerfCmd \</lineoff další argumenty>**.

## <a name="see-also"></a>Viz také
- [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
- [Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)
