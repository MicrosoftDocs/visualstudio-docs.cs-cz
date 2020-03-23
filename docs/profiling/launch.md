---
title: Spuštění | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9834c10c58fb343de0707fa0b805586a6cdebcb3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778606"
---
# <a name="launch"></a>Spuštění
Možnost **Spuštění** spustí profiler pomocí metody vzorkování a také spustí zadanou aplikaci.

 Chcete-li použít volbu **Spustit,** musíte zadat metodu **Ukázka** v možnosti **Start.**

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName [Options]
```

#### <a name="parameters"></a>Parametry
 `AppName`Název aplikace ke spuštění. Úplné a částečné cesty z aktuálního adresáře jsou podporovány.

## <a name="valid-options"></a>Platné možnosti
 Následující volby VSPerfCmd lze kombinovat s možností **Spustit** na jednom příkazovém řádku.

 **Start:** `Method` Inicializuje relaci profileru příkazového řádku a nastaví zadanou metodu profilování.

 **GlobalOn** a **GlobalOff** obnoví (**GlobalOn**) nebo pozastaví (**GlobalOff**) profilování, ale neukončí relaci profilování.

 **ProcessOn:** `PID` a **ProcessOff**:`PID` Obnoví **(ProcessOn)** nebo pozastaví **(ProcessOff)** profilování pro zadaný proces.

 **Cílclr** Určuje verzi rozhraní CLR rozhraní .NET Framework Common Language Runtime (CLR) pro profil, pokud je v relaci profilování načteno více než jedna verze. Ve výchozím nastavení je profilována první načtená verze.

## <a name="exclusive-options"></a>Exkluzivní možnosti
 Následující možnosti lze použít pouze s možností **Spustit.**

 **Konzola** Spustí zadanou aplikaci příkazového řádku v novém okně.

 **Args:** `ArgList` Určuje seznam argumentů, které mají být předávány aplikaci.

 **Lineoff** Zakáže shromažďování dat profilování na úrovni řádku.

## <a name="sampling-options"></a>Možnosti vzorkování
 Na příkazovém řádku **Spuštění** lze zadat jednu z následujících možností intervalu vzorkování. Výchozí interval vzorkování je 10 000 000 cyklů hodin procesoru.

 **Časovač**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:**`Events`]**Čítač**[**:**`Name`,`Reload`,`FriendlyName`]**GC**[:**přidělení**&#124;**životnost**] Určuje počet a typ intervalu vzorkování.

- **Timer** - `Cycles` Vzorky každý non-zastavil procesor hodiny cykly. Není-li `Cycles` zadán, použije se 10 000 000 cyklů.

- **PF** - `Events` Vzorky každé stránky chyby. Pokud `Events` není zadán, 10 chyb stránky.

- **Sys** - `Events` Vzorky každé volání do operačního systému. Pokud `Events` není zadán, 10 systémových volání se používají.

- **Čítač** – ukažuje `Reload` `Name`každý počet čítač výkonu procesoru určený . Volitelně `FriendlyName` můžete zadat řetězec, který se má použít jako záhlaví sloupce v sestavách profileru.

- **GC** - Shromažďuje data paměti .NET. Ve výchozím nastavení (**přidělení**) jsou data shromažďována při každé události přidělení paměti. Pokud je zadán parametr **životnosti,** data jsou také shromažďována při každé události uvolňování paměti.

## <a name="example"></a>Příklad
 Tento příklad ukazuje použití **spuštění** ke spuštění aplikace.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
