---
title: Připojení nástrojů pro sledování výkonu ke spuštěným procesům
description: Naučte se používat profiler sady Visual Studio k připojení nebo odpojení od spuštěného procesu, abyste mohli provádět vzorkování a shromažďování dat o výkonu.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 9cccad7f47a26396612264280926b7b26e431879
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801159"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Postupy: Připojení nástrojů pro měření výkonu ke spuštěným procesům a jejich odpojení
Profiler se dá použít k připojení k běžícímu procesu nebo k jeho odpojení a k usnadnění vzorkování a shromažďování dat o výkonu. Tuto metodu můžete použít k profilování procesu, pokud se chcete vyhnout shromažďování dat o době načítání aplikace, nebo ke sledování výkonu procesu po dosažení určitého stavu.

> [!NOTE]
> Následující postup se týká připojení a odpojení procesů v rámci [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] integrovaného vývojového environmnent (IDE). Informace o tom, jak používat nástroje příkazového řádku, najdete v tématu [profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md). Informace o tom, jak profilovat služby, najdete v tématu [profilové služby](../profiling/command-line-profiling-of-services.md).

 Procesy, které jsou k dispozici pro profil, závisí na uživatelských oprávněních, která jsou nastavena správcem počítače. Uživatelský účet může mít například oprávnění k některým z následujících způsobů:

- Pokročilé funkce profilování, pokud správce nastavil ovladač a službu tak, aby se spouštěly.

- Pouze profilace vzorků (Domain Users).

- Odepřete přístup k profilování pro každého.

  Další informace najdete v tématech [profilace a zabezpečení systému Windows Vista](../profiling/profiling-and-windows-vista-security.md) a možnosti správy v [VSPerfCmd](../profiling/vsperfcmd.md).

### <a name="to-attach-to-a-running-process"></a>Připojení ke spuštěnému procesu

1. V nabídce **ladění** přejděte na **Profiler** a pak **prohlížeč výkonu** a pak klikněte na **připojit**.

     Zobrazí se dialogové okno **Připojit profiler k procesu** .

2. Klikněte na název procesu, ke kterému se chcete připojit.

3. Klikněte na **připojit**.

### <a name="to-detach-from-a-running-process"></a>Odpojení od běžícího procesu

1. v nabídce **ladění** přejděte na **Profiler** a pak **prohlížeč výkonu** a potom klikněte na **Odpojit**.

     Zobrazí se dialogové okno **Připojit profiler k procesu** .

2. Klikněte na název bitové kopie, ze které chcete odpojit.

3. Klikněte na **Odpojit**.

## <a name="see-also"></a>Viz také
- [Řízení shromažďování dat](../profiling/controlling-data-collection.md)
- [Přehled výkonnostní relace](../profiling/performance-session-overview.md)
- [Postupy: spuštění a ukončení shromažďování dat výkonu](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Profilace a zabezpečení systému Windows Vista](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
