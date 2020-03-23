---
title: Připojení nástrojů pro výkon ke spuštěných procesům
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4c4ae54d6b90166de31c338a5e606eaf31ecd6cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779165"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Postupy: Připojení nástrojů pro měření výkonu ke spuštěným procesům a jejich odpojení
Profiler lze připojit nebo odpojit od spuštěného procesu, aby vzorkování a shromažďování dat výkonu jednodušší. Tuto metodu můžete použít k profilování procesu, pokud chcete vyhnout shromažďování dat o době načítání aplikace nebo ke sledování výkonu procesu po dosažení určitého stavu.

> [!NOTE]
> Následující kroky platí pro připojení a odpojení procesů [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] z integrovaného vývojového prostředí (IDE). Informace o použití nástrojů příkazového řádku naleznete [v tématu Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md). Informace o tom, jak profilovat služby, naleznete [v tématu Profilové služby](../profiling/command-line-profiling-of-services.md).

 Procesy, které jsou k dispozici pro profil, závisí na oprávněních přístupu uživatelů, která jsou nastavena správcem počítače. Uživatelský účet může mít například oprávnění pro některou z následujících možností:

- Rozšířené funkce profilování, pokud správce nastavil spuštění ovladače a služby.

- Ukázkové profilování pouze (uživatelé domény).

- Odepřej přístup k profilování všem.

  Další informace naleznete [v tématu Profilování a zabezpečení systému Windows Vista](../profiling/profiling-and-windows-vista-security.md) a možnosti ADMIN v [aplikaci VSPerfCmd](../profiling/vsperfcmd.md).

### <a name="to-attach-to-a-running-process"></a>Připojení ke spuštěnému procesu

1. V nabídce **Ladění** přejděte na **položku Profiler**, potom na **položku Průzkumník výkonu**a klepněte na tlačítko **Připojit**.

     Zobrazí se dialogové okno **Připojit profiler k procesu.**

2. Klikněte na název procesu, ke kterému chcete připojit.

3. Klepněte na **tlačítko Připojit**.

### <a name="to-detach-from-a-running-process"></a>Odpojení od spuštěného procesu

1. n v nabídce **Ladění** přejděte na **položku Profiler**, potom na **průzkumník výkonu**a klepněte na tlačítko **Odřadit**.

     Zobrazí se dialogové okno **Připojit profiler k procesu.**

2. Klikněte na název obrázku, od kterého chcete odpojit.

3. Klepněte na **položku Odřadit**.

## <a name="see-also"></a>Viz také
- [Řízení shromažďování dat](../profiling/controlling-data-collection.md)
- [Přehled relace výkonu](../profiling/performance-session-overview.md)
- [Postup: Shromažďování dat o výkonu zahájení a ukončení](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Profilace a zabezpečení systému Windows Vista](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
