---
title: Konzola | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b70c44f72d8f9d8fb25eb1c459946797cfb97913
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331572"
---
# <a name="console"></a>Konzola
Možnost **konzoly** VSPerfCmd.exe spustí zadanou aplikaci v novém okně příkazového řádku. **Konzolu** lze použít pouze s možností **spuštění** VSPerfCmd. Pokud aplikace není aplikace příkazového řádku, **Konzola** nemá žádný vliv.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametry
 Žádná

## <a name="required-options"></a>Požadované možnosti
 **Konzolu** lze zadat pouze v příkazovém řádku, který obsahuje také možnost **spuštění** .

 **Spustit:** `AppName` Spustí Profiler a aplikaci určenou nástrojem `AppName` .

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
