---
title: ProcessOn a ProcessOff | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 62c16c2d578a38187b4a58958466597a5e4d297d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778385"
---
# <a name="processon-and-processoff"></a>ProcessOn a ProcessOff
Podpříkazy VSPerfCmd.exe **ProcessOff** a **ProcessOn** pozastaví a obnoví profilování pro zadaný proces v relaci profilování příkazového řádku. **ProcessOff** zastaví profilování procesu a **ProcessOn** spustí profilování procesu.

 Ve většině případů zadáte **ProcessOn** nebo **ProcessOff** jako jedinou možnost v příkazovém řádku VSPerfCmd.exe, ale mohou být také kombinovány s podpříkazy **GlobalOn**, **GlobalOff**, **ThreadOn**a **ThreadOff.**

 Podpříkazy **ProcessOn** a **ProcessOff** interagují s podpříkazy **GlobalOn** a **GlobalOff,** které řídí sběr dat pro všechny procesy v relaci profilování příkazového řádku, a podpříkazy **ThreadOn** a **ThreadOff,** které řídí sběr dat pro zadané vlákno.

 Podpříkazy **ProcessOff** a **ProcessOn** také ovlivňují počet zahájení a zastavení procesu, který je manipulován funkcemi rozhraní API profileru.

- **ProcessOff** okamžitě nastaví počet spuštění a zastavení procesu na 0 a proto pozastaví profilování.

- **ProcessOn** okamžitě nastaví počet spuštění a zastavení procesu na 1 a proto pokračuje v profilování.

  Další informace naleznete [v tématu Profilování nástrojů API](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]

```

#### <a name="parameters"></a>Parametry
 `PID`Identifikátor celéčíslo procesu spustit nebo zastavit. ID procesů jsou uvedena na kartě **Proces** správce úloh systému Windows.

## <a name="required-subcommands"></a>Povinné dílčí příkazy
 Žádný

## <a name="valid-subcommands"></a>Platné podpříkazy
 **ProcessOn** a **ProcessOff** lze zadat na příkazových řádcích, které také obsahují následující podpříkazy.

 **Start:** `Method` Inicializuje relaci profilování příkazového řádku a nastaví zadanou metodu profilování.

 **Spuštění:** `AppName` Spustí zadanou aplikaci a začne profilování metodou vzorkování.

 **Připojit:** `PID` Zahájí profilování zadaného procesu.

 **GlobalOff**&#124;**GlobalOn** zastaví nebo spustí profilování pro všechny procesy v relaci profilování příkazového řádku.

 {**ThreadOff**&#124;**ThreadOn**} **:** `TID` Zastaví nebo spustí profilování pro zadaný podproces (pouze metoda instrumentace).

## <a name="example"></a>Příklad
 V tomto příkladu **processoff** podpříkaz se používá ke shromažďování dat profilování pro spuštění aplikace.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the process after startup.
VSPerfCmd.exe /ProcessOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
