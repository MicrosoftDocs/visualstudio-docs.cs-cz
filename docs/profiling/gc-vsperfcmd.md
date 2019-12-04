---
title: GC (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e14fef1cfdc2dfc5f0d737ac09a08d90ab1de309
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74776976"
---
# <a name="gc-vsperfcmd"></a>Uvolňování paměti (VSPerfCmd)
Možnost **GC** umožňuje shromažďování .NET Framework přidělování paměti a dat o životnosti objektů. Možnost **GC** se dá použít jenom s metodou profilace vzorkování a jenom s možností **spuštění** .

 Pokud používáte možnost **GC** , není příkaz VSPerfCLREnv **/sampleon** povinný.

 Nejsou-li zadány žádné parametry nebo je-li zadán parametr **přidělení** , jsou shromažďována pouze .NET Framework data o přidělení paměti. Je-li zadán parametr **životnosti** , jsou shromažďována jak .NET Framework přidělování paměti, tak data o životnosti objektů .NET Framework.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Parametry
 **Přidělení** Výchozí. Shromažďuje .NET Framework data o přidělování paměti.

 **Doba života** Shromažďuje data přidělování .NET Framework paměti a data o životnosti objektů .NET Framework.

## <a name="required-options"></a>Požadované možnosti
 Možnost **GC** se dá použít jenom s možností **spuštění** .

 **Spustit:** `AppName` spustí zadanou aplikaci a zahájí profilaci pomocí metody vzorkování.

## <a name="example"></a>Příklad
 V následujícím příkladu se spustí aplikace a shromáždí .NET Framework data o přidělování paměti.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Viz také:
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
