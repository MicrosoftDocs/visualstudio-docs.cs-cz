---
title: Konzola | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6ec56665b546f962e8b3f4fd35460715390aee30
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777813"
---
# <a name="console"></a>Konzola
Možnost **konzoly** VSPerfCmd. exe spustí zadanou aplikaci v novém okně příkazového řádku. **Konzolu** lze použít pouze s možností **spuštění** VSPerfCmd. Pokud aplikace není aplikace příkazového řádku, **Konzola** nemá žádný vliv.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametry
 Žádné

## <a name="required-options"></a>Požadované možnosti
 **Konzolu** lze zadat pouze v příkazovém řádku, který obsahuje také možnost **spuštění** .

 **Spustit:** `AppName` spustí Profiler a aplikaci určenou v `AppName`.

## <a name="see-also"></a>Viz také:
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
