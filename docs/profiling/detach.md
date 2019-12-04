---
title: Odpojit | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777387"
---
# <a name="detach"></a>Odpojit
Možnost **Odpojit** VSPerfCmd. exe odpojí Profiler od zadaných procesů nebo všech procesů, pokud nejsou zadány žádné. Profilování je nutné inicializovat pomocí metody vzorkování.

 Profilace, která byla spuštěna buď pomocí **spuštění** , nebo možností **připojení** , lze odpojit pomocí možnosti **Odpojit**. Profiler se dá reattched pomocí dalších příkazů **připojit** .

 Při **odpojení** se soubor dat profilování nezavře. Pro ukončení profilování a zavření datového souboru použijte možnost **vypnutí** .

> [!NOTE]
> Pokud byla možnost **Start** zadána s možností **CrossSession** , musí být jakákoli volání **VSPerfCmd/attach** nebo **VSPerfCmd/detach** také určovat **CrossSession**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Parametry
 `PIDs|ProcessNames` `PID` – číselná systémová identifikátorem jednoho nebo více procesů.

 `ProcessNames` – název procesu. Pokud je spuštěno více instancí pojmenovaného procesu, výsledky mohou být nepředvídatelné.

 Více procesů oddělte čárkami.

 Pokud není zadán žádný proces, Profiler je odpojen od všech profilování procesu.

## <a name="valid-options"></a>Platné možnosti
 Následující možnosti **VSPerfCmd** lze kombinovat s možností **připojit** na jednom příkazovém řádku.

 **CrossSession** Povoluje profilování aplikací v jiných relacích než v přihlašovací relaci. Vyžaduje se, pokud byla zadána možnost **Start** s možností **CrossSession** .

## <a name="example"></a>Příklad
 V tomto příkladu příkaz **Odpojit** pozastaví profilaci a příkaz pro **vypnutí** zavře datový soubor profileru.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>Viz také:
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
