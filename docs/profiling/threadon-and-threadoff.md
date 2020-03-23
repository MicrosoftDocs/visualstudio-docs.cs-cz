---
title: ThreadOn a ThreadOff | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 906629eb24f6be097f3e24dfca3e6a231f42357f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778151"
---
# <a name="threadon-and-threadoff"></a>ThreadOn a ThreadOff
*Podpříkazy VSPerfCmd.exe* **ThreadOff** a **ThreadOn** jsou k dispozici pouze v relacích profilování příkazového řádku, které používají metodu instrumentace. **ThreadOff** a **ThreadOn** pozastavit a obnovit profilování pro zadané vlákno. **ThreadOff** zastaví profilování podprocesu a **ThreadOn** začne profilování podprocesu.

 Ve většině případů zadáte **ThreadOn** nebo **ThreadOff** jako jedinou možnost v příkazovém řádku *VSPerfCmd.exe,* ale mohou být také kombinovány s podpříkazy **GlobalOn**, **GlobalOff**, **ProcessOn**a **ProcessOff.**

 **Podpříkazy ThreadOn** a **ThreadOff** interagují s podpříkazy **GlobalOn** a **GlobalOff,** které řídí sběr dat pro všechny procesy v relaci profilování příkazového řádku, a podpříkazy **ProcessOn** a **ProcessOff,** které řídí sběr dat pro zadaný proces.

 Podpříkazy **ThreadOff** a **ThreadOn** také ovlivňují počet spuštění a zastavení podprocesu, který je manipulován funkcemi rozhraní API profileru.

- **ThreadOff** okamžitě nastaví počet spuštění a zastavení podprocesu na 0 a proto pozastaví profilování.

- **ThreadOn** okamžitě nastaví počet spuštění a zastavení vlákna na 1 a proto pokračuje v profilování.

  Další informace naleznete v [tématu Profilování nástrojů API](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>Parametry
 `TID`Identifikátor celéčíslo vlákna pro spuštění nebo zastavení.

## <a name="valid-options"></a>Platné možnosti
 **ThreadOn** a **ThreadOff** lze zadat na příkazových řádcích, které také obsahují následující podpříkazy.

 **Start:** `Method` Inicializuje relaci profilování příkazového řádku a nastaví zadanou metodu profilování.

 **GlobalOff**&#124;**GlobalOn** zastaví nebo spustí profilování pro všechny procesy v relaci profilování příkazového řádku.

 {**ProcessOff**&#124;**ProcessOn**} **:** `TID` Zastaví nebo spustí profilování pro zadaný proces.

## <a name="example"></a>Příklad
 V tomto příkladu podpříkaz **ThreadOff** se používá k zastavení shromažďování dat profilování tak, aby byla shromažďována pouze data spuštění aplikace.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the thread after startup.
VSPerfCmd.exe /ThreadOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
