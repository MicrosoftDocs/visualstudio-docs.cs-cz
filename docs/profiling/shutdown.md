---
title: Vypnutí | Microsoft Docs
description: Přečtěte si, jak možnost vypnutí čeká na ukončení nebo odpojení jakéhokoli aktuálně profilované procesu, a pak vypne Profiler a zavře soubor dat profilování.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c7a0bf796c91ce339c82f7f698ed63afe90f9c1c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720069"
---
# <a name="shutdown"></a>Vypnutí
Možnost **vypnutí** čeká na ukončení nebo odpojení jakéhokoli aktuálně profilované procesu a pak vypne Profiler a zavře soubor dat profilování. Možnost **vypnutí** musí být posledním příkazem pro spuštění profilace.

 Pokud není zadán parametr časového limitu, bude možnost **vypnutí** čekat na neomezenou dobu. Pokud je zadán parametr časového limitu, možnost se vrátí po zadaném počtu sekund bez vypnutí profileru nebo zavření datového souboru.

 Možnost **vypnutí** musí být jedinou možností zadanou v příkazovém řádku.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Parametry
`Timeout`
- Volitelné Když se tato možnost zadá, vrátí se po zadaném počtu sekund, bez vypnutí profileru nebo zavřením souboru dat profilování.

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
