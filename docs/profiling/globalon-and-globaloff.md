---
title: GlobalOn a GlobalOff | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74776963"
---
# <a name="globalon-and-globaloff"></a>GlobalOn a GlobalOff
*VSPerfCmd. exe* **globaloff** a **GlobalOn** možnosti pro pozastavení a obnovení profilování pro všechny procesy a vlákna v relaci profilace z příkazového řádku.

 Můžete zadat **GlobalOn** a **globaloff** jako jediné možnosti v příkazovém řádku *VSPerfCmd. exe* , nebo je můžete zahrnout do příkazových řádků, které obsahují také možnosti **Spustit**, **Spustit**nebo **připojit** .

 **GlobalOn** a **globaloff** lze také kombinovat s možnostmi **ProcessOn**, **ProcessOff**, **ThreadOn**a **ThreadOff** .

 Možnosti **GlobalOn** a **globaloff** pracují s možnostmi **ProcessOn** a **ProcessOff** , které řídí shromažďování dat pro zadaný proces, a s možnostmi **ThreadOn** a **ThreadOff** , které řídí shromažďování dat pro zadané vlákno.

 Možnosti **globaloff** a **GlobalOn** mají vliv také na globální počet spuštění/zastavení, který je zpracován funkcemi rozhraní API profileru.

- **Globaloff** hned nastaví globální počet spuštění/zastavení na hodnotu 0, a proto pozastaví profilaci.

- **GlobalOn** hned nastaví globální počet spuštění/zastavení na 1, takže obnoví profilování.

  Další informace najdete v tématu [rozhraní API nástrojů pro profilaci](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /{GlobalOff|GlobalOn}

VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]

VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]
```

#### <a name="parameters"></a>Parametry
 Žádné

## <a name="valid-options"></a>Platné možnosti
 **GlobalOn** a **globaloff** lze zadat na příkazovém řádku, který obsahuje také následující možnosti.

 **Start:** `Method` inicializuje relaci profileru příkazového řádku a nastaví určenou metodu profilace.

 **Spustit:** `AppName` spustí zadanou aplikaci a zahájí profilaci pomocí metody vzorkování.

 **Připojit:** `PID` zahájí profilování zadaného procesu.

 {**ProcessOff**&#124;**ProcessOn**} **:** `PID` zastaví nebo spustí profilaci pro zadaný proces.

 {**ThreadOff**&#124;**ThreadOn**} **:** `TID` zastaví nebo spustí profilaci pro zadaný proces (pouze metoda instrumentace).

## <a name="example"></a>Příklad
 V tomto příkladu se používají možnosti **globaloff** a **GlobalOn** k tomu, abyste se vyhnuli shromažďování dat profilace pro spuštění a vypnutí aplikace.

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

## <a name="see-also"></a>Viz také:
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
