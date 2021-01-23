---
title: QueryCounters | Microsoft Docs
description: Přečtěte si, jak možnost QueryCounters vypisuje čítače výkonu procesoru (hardware), které jsou k dispozici v počítači.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d33b6fe42f786218bf78825a356a25edff2b31ae
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720433"
---
# <a name="querycounters"></a>QueryCounters
Možnost **QueryCounters** vypisuje čítače výkonu procesoru (hardware), které jsou k dispozici v počítači.

 **QueryCounters** musí být jedinou možností na příkazovém řádku.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /QueryCounters
```

#### <a name="parameters"></a>Parametry
 Žádné

## <a name="remarks"></a>Poznámky
 Při použití metody instrumentace může Profiler shromažďovat hodnoty jednoho nebo více čítačů výkonu procesoru při každé události shromažďování dat. Při použití metody profilace vzorkování můžete zadat jednu událost čítače a počet výskytů událostí, které se mají použít jako interval vzorkování.

 Různé procesory zveřejňují různé čítače výkonu procesoru. Profiler definuje sadu generických čítačů, které lze použít na téměř všech procesorech. Možnost **QueryCounters** vypisuje jak názvy obecných čítačů, tak názvy čítačů, které jsou specifické pro procesor.

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
