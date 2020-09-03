---
title: ProcessOn a ProcessOff | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778385"
---
# <a name="processon-and-processoff"></a>ProcessOn a ProcessOff
Dílčí příkazy VSPerfCmd.exe **ProcessOff** a **ProcessOn** pozastaví a obnoví profilování pro zadaný proces v relaci profilace z příkazového řádku. **ProcessOff** zastaví profilování procesu a **ProcessOn** spustí profilování procesu.

 Ve většině případů zadáte **ProcessOn** nebo **ProcessOff** jako jedinou možnost v příkazovém řádku VSPerfCmd.exe, ale lze je kombinovat i s dílčími příkazy **GlobalOn**, **globaloff**, **ThreadOn**a **ThreadOff** .

 Podpříkazy **ProcessOn** a **ProcessOff** komunikují s dílčími příkazy **GlobalOn** a **globaloff** , které řídí shromažďování dat pro všechny procesy v relaci profilace příkazového řádku, a dílčí příkazy **ThreadOn** a **ThreadOff** , které řídí shromažďování dat pro zadané vlákno.

 Dílčí příkazy **ProcessOff** a **ProcessOn** také ovlivňují počet spuštění/zastavení procesu, který je zpracováván funkcemi rozhraní API profileru.

- **ProcessOff** okamžitě nastaví počet spuštění/zastavení procesu na hodnotu 0, takže profilování pozastaví.

- **ProcessOn** okamžitě nastaví počet spuštění/zastavení procesu na 1, takže obnoví profilování.

  Další informace najdete v tématu [rozhraní API pro nástroje pro profilaci](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]

```

#### <a name="parameters"></a>Parametry
 `PID` Celočíselný identifikátor procesu, který se má spustit nebo zastavit. ID procesů jsou uvedena na kartě **proces** ve Správci úloh systému Windows.

## <a name="required-subcommands"></a>Požadované dílčí příkazy
 Žádné

## <a name="valid-subcommands"></a>Platné dílčí příkazy
 **ProcessOn** a **ProcessOff** lze zadat na příkazovém řádku, který obsahuje také následující dílčí příkazy.

 **Začátek:** `Method` Inicializuje relaci profilování z příkazového řádku a nastaví určenou metodu profilace.

 **Spustit:** `AppName` Spustí zadanou aplikaci a zahájí profilaci pomocí metody vzorkování.

 **Připojit:** `PID` Spustí profilování zadaného procesu.

 **GlobalOff**&#124;**GlobalOn** zastaví nebo spustí profilaci pro všechny procesy v relaci profilace z příkazového řádku.

 {**ThreadOff**&#124;**ThreadOn**} **:**`TID` Zastaví nebo spustí profilování pro zadané vlákno (pouze metoda instrumentace).

## <a name="example"></a>Příklad
 V tomto příkladu se pro shromažďování dat profilování pro spuštění aplikace používá dílčí příkaz **ProcessOff** .

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
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
