---
description: Služba Debugging Services nemá dostatek paměti a způsobila ukončení relace ladění.
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
ms.openlocfilehash: d881248652d644e9a82725b0d083d095ff72f885
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147039"
---
# <a name="debugger-services-running-out-of-memory"></a>Službám ladicího programu začíná docházet paměť
Služba Debugging Services nemá dostatek paměti a způsobila ukončení relace ladění.

## <a name="to-investigate-this-error-on-windows"></a>Chcete-li tuto chybu prozkoumat ve Windows
- V okně **diagnostické nástroje** můžete sledovat graf paměti procesu a zjistit, jestli má cílová aplikace velký nárůst velikosti paměti. V takovém případě použijte nástroj **využití paměti** k diagnostice základního problému, viz téma [Analýza využití paměti](../profiling/memory-usage.md).

- Pokud cílová aplikace nespotřebovává spoustu paměti, použijte okno **Správce úloh** k rezervaci využití paměti sady Visual Studio (devenv.exe), pracovního procesu (msvsmon.exe) nebo VS Code (vsdbg.exe/vsdbg-ui.exe) k určení, jestli se jedná o problém ladicího programu. Pokud je devenv.exe nedostatku paměti, zvažte snížení počtu spuštěných rozšíření aplikace Visual Studio.

## <a name="see-also"></a>Viz také
- [Blogový příspěvek: analýza procesoru a paměti během ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [O správě paměti](/windows/win32/memory/about-memory-management)
