---
title: Argumenty | Microsoft Docs
description: Použijte možnost ARGS VSPerfCmd.exe k předání seznamu argumentů cílové aplikaci spouštěcího dílčího příkazu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ff16d67d0c7168524ff145183f49a662e1f660f0
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205707"
---
# <a name="args"></a>Args
Možnost VSPerfCmd.exe **args** určuje seznam argumentů, které jsou předány cílové aplikaci **spouštěného** dílčího příkazu.

 **Argumenty** lze použít pouze v případě, že je v příkazovém řádku uveden také příkaz **Spustit** . **Argumenty** jsou volitelné, pokud je zadán parametr **Launch** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Parametry
 `Arguments` Seznam argumentů cílové aplikace příkazu pro **spuštění** .

## <a name="required-options"></a>Požadované možnosti
 **Spustit:** `AppName` Spustí zadanou aplikaci a zahájí profilaci pomocí metody vzorkování.

## <a name="example"></a>Příklad
 Následující příklad používá možnost **args** k předání argumentů TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Služby profilace](../profiling/command-line-profiling-of-services.md)
