---
title: GlobalOn a GlobalOff | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 518f41557809cdeaaae9f9e1ac79e3797a854395
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776963"
---
# <a name="globalon-and-globaloff"></a>GlobalOn a GlobalOff
*Možnosti VSPerfCmd.exe* **GlobalOff** a **GlobalOn** pozastavují a obnovují profilování pro všechny procesy a vlákna v relaci profilování příkazového řádku.

 Můžete zadat **GlobalOn** a **GlobalOff** jako jediné možnosti v příkazovém řádku *VSPerfCmd.exe,* nebo je můžete zahrnout do příkazových řádků, které také obsahují možnosti **Start**, **Launch**nebo **Attach.**

 **GlobalOn** a **GlobalOff** lze také kombinovat s **ProcessOn**, **ProcessOff**, **ThreadOn**a **ThreadOff** možnosti.

 **Možnosti GlobalOn** a **GlobalOff** interagují s **processon** a **ProcessOff** možnosti, které řídí shromažďování dat pro zadaný proces a s **ThreadOn** a **ThreadOff** možnosti, které řídí sběr dat pro zadané vlákno.

 **Možnosti GlobalOff** a **GlobalOn** také ovlivňují globální počet start/stop, který je manipulován funkcemi rozhraní API profileru.

- **GlobalOff** okamžitě nastaví globální start/stop počet 0 a proto pozastaví profilování.

- **GlobalOn** okamžitě nastaví globální start/stop počet na 1 a proto pokračuje profilování.

  Další informace naleznete v [tématu Profilování nástrojů API](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /{GlobalOff|GlobalOn}

VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]

VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]
```

#### <a name="parameters"></a>Parametry
 Žádný

## <a name="valid-options"></a>Platné možnosti
 **GlobalOn** a **GlobalOff** lze zadat na příkazových řádcích, které také obsahují následující možnosti.

 **Start:** `Method` Inicializuje relaci profileru příkazového řádku a nastaví zadanou metodu profilování.

 **Spuštění:** `AppName` Spustí zadanou aplikaci a začne profilování metodou vzorkování.

 **Připojit:** `PID` Zahájí profilování zadaného procesu.

 {**ProcessOff**&#124;**ProcessOn**} **:** `PID` Zastaví nebo spustí profilování pro zadaný proces.

 {**ThreadOff**&#124;**ThreadOn**} **:** `TID` Zastaví nebo spustí profilování pro zadaný proces (pouze metoda instrumentace).

## <a name="example"></a>Příklad
 V tomto příkladu **GlobalOff** a **GlobalOn** možnosti se používají, aby se zabránilo shromažďování dat profilování pro spuštění a vypnutí aplikace.

```cmd
; Initialize the profiler with profiling stopped.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff
; Start an instrumented application and wait for it to warm up.
; Start profiling.
VSPerfCmd.exe /GlobalOn
; Exercise the application functionality that you want to profile.
; Stop profiling.
VSPerfCmd.exe /GlobalOff
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
