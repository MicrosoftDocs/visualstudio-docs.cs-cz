---
title: 'Postupy: Konfigurace pravidel výkonu | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779009"
---
# <a name="how-to-configure-performance-rules"></a>Postupy: Konfigurace pravidel výkonu
Upozornění na výkon aplikace Visual Studio Nástroje pro profilaci indikují problémy v profilované aplikaci, která může zpomalit spuštění programu. Upozornění mohou také indikovat, že možná budete muset změnit metody kolekce a shromažďovat tak užitečnější data. Upozornění na výkon jsou generována automaticky v relaci profilace a zobrazí se v okně **Seznam chyb** při otevření datového souboru profilování v [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Některá upozornění se nemusí vztahovat na scénáře, které vás zajímají, a některá upozornění můžou být nesprávně vyvolaná. Upozornění výkonu můžete nakonfigurovat tak, aby se zobrazila nebo skryla konkrétní upozornění.

### <a name="to-configure-profiler-performance-warnings"></a>Konfigurace upozornění výkonu profileru

1. V nabídce **nástroje** klikněte na příkaz **Možnosti**.

2. Rozbalte položku **Nástroje pro sledování výkonu**a pak klikněte na možnost **pravidla**.

3. Pokud chcete povolit nebo zakázat upozornění, zaškrtněte nebo zrušte zaškrtnutí políčka vedle **ID** a názvu upozornění.

4. Pokud chcete zadat úroveň Warring pravidla, klikněte na buňku **Akce** vedle pravidla a potom klikněte na úroveň upozornění.

    - **Disabled** – zakáže pravidlo (Toto je stejné jako při zrušení zaškrtnutí políčka vedle ID pravidla).

    - **Upozornění** – zobrazí pravidlo jako upozornění.

    - **Chyba** – zastaví provádění profilování a zobrazí pravidlo jako chybu.

    - **Information** – zobrazí pravidlo pouze jako informace.
