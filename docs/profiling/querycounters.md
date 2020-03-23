---
title: Čítače dotazů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 24379a720ccaa3405cbe5c127f3b8abaf12e49aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771906"
---
# <a name="querycounters"></a>QueryCounters
**QueryCounters** možnost uvádí čítače výkonu procesoru (hardware), které jsou k dispozici v počítači.

 **QueryCounters** musí být jedinou možností na příkazovém řádku.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /QueryCounters
```

#### <a name="parameters"></a>Parametry
 Žádný

## <a name="remarks"></a>Poznámky
 Pokud používáte metodu instrumentace profiler můžete shromažďovat hodnoty jednoho nebo více čítačů výkonu procesoru na každé události shromažďování dat. Pokud používáte metodu profilování vzorkování, můžete zadat jednu událost čítače a počet výskytů událostí, které mají být použity jako interval vzorkování.

 Různé procesory vystavit různé čítače výkonu procesoru. Profiler definuje sadu obecných čítačů, které lze použít na téměř všechny procesory. **QueryCounters** možnost uvádí názvy obecných čítačů a názvy čítačů, které jsou specifické pro procesor.

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
