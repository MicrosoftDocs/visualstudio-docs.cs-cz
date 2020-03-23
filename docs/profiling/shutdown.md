---
title: Vypnutí | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 89a08808387067b934bfd826feb2dcfbcf949aab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778281"
---
# <a name="shutdown"></a>Shutdown
Možnost **Vypnutí** čeká na ukončení nebo odpojení libovolného aktuálně profilovaného procesu a potom vypne profiler a zavře datový soubor profilování. Možnost **Vypnutí** musí být posledním příkazem spuštění profilování.

 Pokud není zadán parametr časového omezení, možnost **Vypnutí** čeká neomezeně dlouho. Pokud je zadán parametr časového času, možnost vrátí po zadaném počtu sekund bez vypnutí profileru nebo zavření datového souboru.

 Možnost **Vypnutí** musí být jedinou možností určenou na příkazovém řádku.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Parametry
`Timeout`
- (Nepovinné) Pokud je zadán, možnost vrátí po zadaném počtu sekund bez vypnutí profileru nebo zavření profilování datového souboru.

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
