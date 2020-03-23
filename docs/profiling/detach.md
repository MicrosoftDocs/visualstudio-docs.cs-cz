---
title: Odpojit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b151e3ede34d0c8fa3a863d7a4e7474431ae6f4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777387"
---
# <a name="detach"></a>Odpojit
Možnost VSPerfCmd.exe **Odpojit** odpojí profiler od zadaných procesů nebo všech procesů, pokud nejsou zadány žádné. Profilování musí být inicializováno pomocí metody vzorkování.

 Profilování, které bylo spuštěno buď **spuštění** nebo **připojit** možnosti lze odpojit s **Odřadit**. Profiler lze reattched pomocí následné **Attach** příkazy.

 **Odpojení** nezavře datový soubor profilování. Pomocí možnosti **Vypnutí** ukončete profilování a zavřete datový soubor.

> [!NOTE]
> Pokud byla možnost **Start** zadána s možností **Crosssession,** všechna volání **VSPerfCmd /Attach** nebo **VSPerfCmd /Detach** musí také zadat **Crosssession**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Parametry
 `PIDs|ProcessNames``PID` - Číselný systém identifer jednoho nebo více procesů.

 `ProcessNames`- název procesu. Pokud je spuštěno více instancí pojmenovaného procesu, výsledky jsou nepředvídatelné.

 Oddělte více procesů čárkou.

 Pokud není zadán žádný proces, profiler je odpojen od všech profilovaného procesu.

## <a name="valid-options"></a>Platné možnosti
 Následující volby **VSPerfCmd** lze kombinovat s možností **Připojit** na jednom příkazovém řádku.

 **Křížová relace** Umožňuje profilování aplikací v jiných relacích než v relaci přihlášení. Povinné, pokud byla možnost **Start** zadána s možností **Mezirelace.**

## <a name="example"></a>Příklad
 V tomto příkladu příkaz **Odpojit** pozastaví profilování a příkaz **Vypnutí** zavře datový soubor profileru.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
