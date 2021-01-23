---
title: ThreadOn a ThreadOff | Microsoft Docs
description: Přečtěte si, jak jsou dílčí příkazy VSPerfCmd.exe ThreadOff a ThreadOn dostupné jenom v relacích profilování příkazového řádku, které používají metodu instrumentace.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f8b2e51857fc799c7b60f7650b823b77c9c6a283
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718769"
---
# <a name="threadon-and-threadoff"></a>ThreadOn a ThreadOff
Dílčí příkazy *VSPerfCmd.exe* **ThreadOff** a **ThreadOn** jsou k dispozici pouze v relacích profilování příkazového řádku, které používají metodu instrumentace. **ThreadOff** a **ThreadOn** pozastavení a obnovení profilování pro zadané vlákno. **ThreadOff** zastaví profilaci vlákna a **ThreadOn** spustí profilaci vlákna.

 Ve většině případů zadáte **ThreadOn** nebo **ThreadOff** jako jedinou možnost v příkazovém řádku *VSPerfCmd.exe* , ale lze je kombinovat i s dílčími příkazy **GlobalOn**, **globaloff**, **ProcessOn** a **ProcessOff** .

 Podpříkazy **ThreadOn** a **ThreadOff** komunikují s dílčími příkazy **GlobalOn** a **globaloff** , které řídí shromažďování dat pro všechny procesy v relaci profilace příkazového řádku, a dílčí příkazy **ProcessOn** a **ProcessOff** , které řídí shromažďování dat pro zadaný proces.

 Dílčí příkazy **ThreadOff** a **ThreadOn** také ovlivňují počet spuštění nebo zastavení vlákna, který je manipulován funkcemi rozhraní API profileru.

- **ThreadOff** okamžitě nastaví počet spuštění/zastavení vlákna na hodnotu 0, takže profilování pozastaví.

- **ThreadOn** okamžitě nastaví počet spuštění/zastavení vlákna na 1, takže obnoví profilování.

  Další informace najdete v tématu [rozhraní API nástrojů pro profilaci](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>Parametry
 `TID` Celočíselný identifikátor vlákna, který se má spustit nebo zastavit.

## <a name="valid-options"></a>Platné možnosti
 **ThreadOn** a **ThreadOff** lze zadat na příkazovém řádku, který obsahuje také následující dílčí příkazy.

 **Začátek:** `Method` Inicializuje relaci profilování z příkazového řádku a nastaví určenou metodu profilace.

 **GlobalOff**&#124;**GlobalOn** zastaví nebo spustí profilaci pro všechny procesy v relaci profilace z příkazového řádku.

 {**ProcessOff**&#124;**ProcessOn**} **:**`TID` Zastaví nebo spustí profilování pro zadaný proces.

## <a name="example"></a>Příklad
 V tomto příkladu se k zastavení shromažďování dat profilace používá dílčí příkaz **ThreadOff** , aby se shromáždila jenom spouštěcí data aplikace.

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
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
