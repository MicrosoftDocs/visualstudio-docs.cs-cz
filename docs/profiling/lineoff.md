---
title: LineOff | Microsoft Docs
description: Přečtěte si, jak možnost VSPerfCmd LineOff zakáže shromažďování dat pro číslo řádku, když se pro spuštění aplikace VSPerfCmd používá.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a141e713dd03f99db6ce47224c64236a0219cdd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917899"
---
# <a name="lineoff"></a>LineOff
Ve výchozím nastavení Profiler shromažďuje číslo řádku zdrojového kódu a čísla řádků posunu při použití metody profilace vzorkování. Možnost VSPerfCmd **LineOff** zakáže shromažďování dat pro číslo řádku, když se k spuštění aplikace VSPerfCmd používá. Data profilování se shromažďují na úrovni funkce, když je zadaný **LineOff** .

 **LineOff** můžete použít jenom s možností **spuštění** a jenom v případě, že Profiler byl inicializován pro vzorkování pomocí možnosti **Start**:**Sample** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Parametry
 Žádné

## <a name="required-options"></a>Požadované možnosti
 Možnost **LineOff** lze použít pouze na příkazovém řádku, který obsahuje možnost **spuštění** .

 **Spustit:** `AppName` Spustí zadanou aplikaci a zahájí profilaci pomocí metody vzorkování.

## <a name="example"></a>Příklad
 V tomto příkladu se spustí aplikace a Profiler a zakáže vzorkování na úrovni řádků.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
