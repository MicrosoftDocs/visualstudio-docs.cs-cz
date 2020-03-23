---
title: WinCounter | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9455d596e27526f6075ad3b667ac441b12511d58
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779841"
---
# <a name="wincounter"></a>WinCounter
**WinCounter** možnost určuje čítač výkonu systému Windows nebo aplikace shromažďovat v nastavených intervalech během spuštění profilu. Čítače výkonu systému Windows a aplikací jsou uvedeny jako značky v datovém souboru profilování. Můžete zadat více čítačů výkonu, které chcete shromažďovat v samostatných možnostech.

 Ve výchozím nastavení jsou čítače shromažďovány každých 500 milisekund. Pomocí možnosti **Automatické označení** můžete zadat jiný interval kolekce.

 Je použita pouze jedna možnost **automatického označení.** Pokud je zadáno více možností **automatického označení,** použije se poslední možnost.

 **Možnost WinCounter** lze použít pouze s možností **Start.**

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]
```

#### <a name="parameters"></a>Parametry
 `Path`Čítač výkonu systému Windows ve formátu cesty čítače PDH.

## <a name="required-options"></a>Požadované možnosti
 **Možnost WinCounter** lze použít pouze s možností **Start.**

 **Start:** `Method` Možnost **Start** inicializuje profiler na zadanou metodu profilování.

## <a name="exclusive-options"></a>Exkluzivní možnosti
 Možnost **automatického označení** lze použít pouze s možností **WinCounter.**

 **Automatické pořizování:** `Milliseconds` Určuje počet milisekund mezi shromažďováním dat čítače výkonu systému Windows.

## <a name="example"></a>Příklad
 V následujícím příkladu jsou určeny dva čítače výkonu systému Windows, které mají být shromažďovány v intervalu 1000 milisekund.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
