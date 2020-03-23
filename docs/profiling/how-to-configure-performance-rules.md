---
title: 'Postup: Konfigurace pravidel výkonu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c9bb9b07a0ae1fa19ae48408aa34a9dfb6577b6e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779009"
---
# <a name="how-to-configure-performance-rules"></a>Postup: Konfigurace pravidel výkonu
Upozornění výkonu nástroje profilování visual studio označují problémy v profilované aplikace, které mohou zpomalit spuštění programu. Upozornění může také znamenat, že budete muset změnit metody shromažďování shromažďovat další užitečná data. Upozornění na výkon jsou generována automaticky v relaci profilování a zobrazují se v [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]okně Seznam **chyb** při otevření datového souboru profilování v aplikaci . Některá upozornění nemusí platit pro scénáře, které vás zajímají a některá upozornění mohou být vyvolána nepřesně. Upozornění na výkon můžete nakonfigurovat tak, aby zobrazovala nebo skryla konkrétní upozornění.

### <a name="to-configure-profiler-performance-warnings"></a>Konfigurace upozornění na výkon profileru

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. Rozbalte **nástroje výkonu**a klepněte na **položku Pravidla**.

3. Chcete-li upozornění povolit nebo zakázat, zaškrtněte nebo zrušte zaškrtnutí políčka vedle **ID** upozornění a názvu.

4. Chcete-li určit úroveň válčící pravidla, klepněte na buňku **Akce** vedle pravidla a potom klepněte na úroveň upozornění.

    - **Zakázáno** - zakáže pravidlo (toto je stejné jako zrušení zaškrtnutí políčka vedle ID pravidla).

    - **Upozornění** - zobrazí pravidlo jako upozornění.

    - **Chyba** - zastaví profilování provádění a zobrazí pravidlo jako chybu.

    - **Informace** - zobrazí pravidlo pouze jako informace.
