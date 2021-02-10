---
title: Konzola | Microsoft Docs
description: Pomocí možnosti konzoly VSPerfCmd.exe spusťte zadanou aplikaci v novém okně příkazového řádku. Je nutné ji použít s možností spuštění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 242a5234c2b7368a992676e12ecbdcd5ea36219f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955408"
---
# <a name="console"></a>Konzola
Možnost **konzoly** VSPerfCmd.exe spustí zadanou aplikaci v novém okně příkazového řádku. **Konzolu** lze použít pouze s možností **spuštění** VSPerfCmd. Pokud aplikace není aplikace příkazového řádku, **Konzola** nemá žádný vliv.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametry
 Žádné

## <a name="required-options"></a>Požadované možnosti
 **Konzolu** lze zadat pouze v příkazovém řádku, který obsahuje také možnost **spuštění** .

 **Spustit:** `AppName` Spustí Profiler a aplikaci určenou nástrojem `AppName` .

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
