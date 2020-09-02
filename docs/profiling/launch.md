---
title: Spustit | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778606"
---
# <a name="launch"></a>Spuštění
Možnost **spuštění** spustí Profiler pomocí metody vzorkování a spustí také zadanou aplikaci.

 Chcete-li použít možnost **spuštění** , je nutné zadat **ukázkovou** metodu v možnosti **Spustit** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName [Options]
```

#### <a name="parameters"></a>Parametry
 `AppName` Název aplikace, která se má spustit Jsou podporovány úplné a částečné cesty z aktuálního adresáře.

## <a name="valid-options"></a>Platné možnosti
 Následující možnosti VSPerfCmd lze kombinovat s možností **spuštění** na jednom příkazovém řádku.

 **Začátek:** `Method` Inicializuje relaci profileru příkazového řádku a nastaví určenou metodu profilace.

 **GlobalOn** a **globaloff** obnoví profilování (**GlobalOn**) nebo pozastaví (**globaloff**), ale neukončí relaci profilování.

 **ProcessOn:** `PID` a **ProcessOff**: `PID` obnovování (**ProcessOn**) nebo pozastavení (**ProcessOff**) profilování pro zadaný proces.

 **TargetCLR** Určuje verzi modulu .NET Framework Common Language Runtime (CLR), která má být profilovaná v případě, že je v relaci profilace načtena více než jedna verze. Ve výchozím nastavení je první načtená verze profilovaná.

## <a name="exclusive-options"></a>Exkluzivní možnosti
 Následující možnosti lze použít pouze s možností **spuštění** .

 **Konzola** nástroje Spustí zadanou aplikaci příkazového řádku v novém okně.

 **Argumenty:** `ArgList` Určuje seznam argumentů, které se mají předat aplikaci.

 **LineOff** Zakáže shromažďování dat profilace na úrovni řádků.

## <a name="sampling-options"></a>Možnosti vzorkování
 Na příkazovém řádku pro **spuštění** lze zadat jednu z následujících možností intervalu vzorkování. Výchozí interval vzorkování je 10 000 000 hodinových cyklů procesoru.

 **Timer**[**:** `Cycles` ]**PF**[**:** `Events` ]**sys**[**:** `Events` ]**čítač**[**:** `Name` , `Reload` , `FriendlyName` ]**GC**[:**přidělení**&#124;**životnost**] Určuje počet a typ intervalu vzorkování.

- **Timer** – ukázky všech `Cycles` nezastavených hodinových cyklů procesoru. Pokud `Cycles` parametr není zadán, jsou použity cykly 10 000 000.

- **PF** – ukázky všech `Events` chyb stránky. Pokud `Events` parametr není zadán, 10 chyb stránky.

- **Sys** – ukázky všech `Events` volání na operační systém. Pokud `Events` parametr není zadán, budou použity 10 volání systému.

- **Counter** -Samples každý `Reload` počet čítačů výkonu procesoru určených parametrem `Name` . Volitelně `FriendlyName` můžete zadat řetězec, který se použije jako záhlaví sloupce v sestavách profileru.

- **GC** – shromažďuje data paměti .NET. Ve výchozím nastavení (**přidělení**) se data shromažďují při každé události přidělení paměti. Při zadání parametru **životnosti** se data shromažďují také při každé události uvolňování paměti.

## <a name="example"></a>Příklad
 Tento příklad ukazuje použití **spuštění** pro spuštění aplikace.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
