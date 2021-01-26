---
title: GC (VSPerfCmd) | Microsoft Docs
description: Přečtěte si možnost GC v nástroji VSPerfCmd.exe. Možnost GC umožňuje shromažďování .NET Framework přidělování paměti a dat o životnosti objektů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7245e75ac38d650bb40f9c21dc0a0ab642e0c721
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801354"
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

 **Spustit:** `AppName` Spustí zadanou aplikaci a zahájí profilaci pomocí metody vzorkování.

## <a name="example"></a>Příklad
 V následujícím příkladu se spustí aplikace a shromáždí .NET Framework data o přidělování paměti.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
