---
title: Služby ladicího programu mají nedostatek paměti | Microsoft Docs
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 12215f9c740e68c4f2749a51b06c09a1385dae1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737845"
---
# <a name="debugger-services-running-out-of-memory"></a>Službám ladicího programu začíná docházet paměť
Služba Debugging Services nemá dostatek paměti a způsobila ukončení relace ladění.

## <a name="to-investigate-this-error-on-windows"></a>Chcete-li tuto chybu prozkoumat ve Windows
- V okně **diagnostické nástroje** můžete sledovat graf paměti procesu a zjistit, jestli má cílová aplikace velký nárůst velikosti paměti. V takovém případě použijte nástroj **využití paměti** k diagnostice základního problému, viz téma [Analýza využití paměti](../profiling/memory-usage.md).

- Pokud cílová aplikace nespotřebovává spoustu paměti, použijte okno **Správce úloh** k rezervaci využití paměti sady Visual Studio (devenv. exe), pracovního procesu (Msvsmon. exe) nebo vs Code (vsdbg. exe/vsdbg-UI. exe), abyste zjistili, jestli se jedná o problém ladicího programu. Pokud je proces s nedostatkem paměti nástrojem devenv. exe, zvažte snížení počtu spuštěných rozšíření aplikace Visual Studio.

## <a name="see-also"></a>Viz také:
- [Blogový příspěvek: analýza procesoru a paměti během ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [O správě paměti](/windows/win32/memory/about-memory-management)
