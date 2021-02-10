---
title: QueryCounters | Microsoft Docs
description: Přečtěte si, jak možnost QueryCounters vypisuje čítače výkonu procesoru (hardware), které jsou k dispozici v počítači.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e93546c97b2ddec0e944314c51c87da05a725db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950166"
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
