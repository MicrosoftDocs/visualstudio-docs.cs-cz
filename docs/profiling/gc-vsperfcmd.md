---
title: GC (VSPerfCmd) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776976"
---
# <a name="gc-vsperfcmd"></a>Uvolňování paměti (VSPerfCmd)
Možnost **GC** umožňuje shromažďování dat paměti rozhraní .NET Framework a životnosti objektu. Možnost **GC** lze použít pouze s metodou profilování vzorkování a pouze s možností **Spuštění.**

 Pokud používáte **možnost GC,** příkaz VSPerfClrEnv **/sampleon** není vyžadován.

 Pokud nejsou zadány žádné parametry nebo pokud je zadán parametr **Allocation,** jsou shromažďována pouze data přidělení paměti rozhraní .NET Framework. Pokud je zadán parametr **Životnost,** jsou shromažďována data o paměti rozhraní .NET Framework i o životnosti objektu rozhraní .NET Framework.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Parametry
 **Přidělení** Výchozí. Shromažďuje data přidělení paměti rozhraní .NET Framework.

 **Životnost** Shromažďuje data přidělení paměti rozhraní .NET Framework i data životnosti objektu rozhraní .NET Framework.

## <a name="required-options"></a>Požadované možnosti
 Možnost **GC** lze použít pouze s možností **Spustit.**

 **Spuštění:** `AppName` Spustí zadanou aplikaci a začne profilování metodou vzorkování.

## <a name="example"></a>Příklad
 Následující příklad spustí aplikaci a shromáždí data přidělení paměti rozhraní .NET Framework.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
