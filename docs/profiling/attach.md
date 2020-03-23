---
title: Připojit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 634169607a7d581de1b1332d78e8d5abde1a722e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773736"
---
# <a name="attach"></a>Připojit
Možnost *VSPerfCmd.exe* **Attach** zahájí profilování ukázkového profilu spuštěného procesu určeného ID procesu (PID).

 Chcete-li použít možnost **Připojit,** musíte zadat metodu **Vzorku** v možnosti Start.

> [!NOTE]
> Pokud byla možnost **Start** zadána s možností **Crosssession,** všechna volání **VSPerfCmd /Attach** nebo **VSPerfCmd /Detach** musí také zadat **Crosssession**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>Parametry
 `ProcessID`ID procesu (PID) spuštěného procesu. Číslo PID spuštěného procesu je uvedeno na kartě Procesy ve Správci úloh systému Windows.

## <a name="valid-options"></a>Platné možnosti
 Následující volby **VSPerfCmd** lze kombinovat s možností **Připojit** na jednom příkazovém řádku.

 **Křížová relace** Umožňuje profilování aplikací v jiných relacích než v relaci přihlášení. Povinné, pokud byla možnost **Start** zadána s možností **Mezirelace.**

 **Start:** `Method` Inicializuje relaci profileru příkazového řádku a nastaví zadanou metodu profilování.

 **Cílclr** Určuje verzi rozhraní CLR rozhraní .NET Framework Common Language Runtime (CLR) pro profil, pokud je v relaci profilování načteno více než jedna verze. Ve výchozím nastavení je profilována první načtená verze.

 **GlobalOn GlobalOff** Obnoví (**GlobalOn**) nebo pozastaví (**GlobalOff**) profilování, ale neukončí relaci profilování.

 **ProcessOn:** `PID` **ProcessOff:** `PID` Obnoví **(ProcessOn)** nebo pozastaví **(ProcessOff)** profilování pro zadaný proces.

## <a name="interval-options"></a>Možnosti intervalu
 Jednu z následujících možností intervalu vzorkování lze zadat na příkazovém řádku Připojit. Výchozí interval vzorkování je 10 000 000 cyklů hodin procesoru.

 **Časovač**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**`FriendlyName`[<strong>:</strong>Události]**Čítač**[**:**`Name`,`Reload`, ] Určuje počet a typ intervalu vzorkování.

- **Timer** - `Cycles` Vzorky každý procesor hodiny cykly. Není-li `Cycles` zadán, použije se 10 000 000 cyklů.

- **PF** - `Events` Vzorky každé stránky chyby. Pokud `Events` není zadán, jsou použity 10 chyb stránky.

- **Sys** - `Events` Vzorky každé volání do operačního systému. Pokud `Events` není zadán, 10 systémových volání se používají.

- **Čítač** – ukažuje `Reload` `Name`každý počet čítač výkonu procesoru určený . Volitelně `FriendlyName` můžete zadat řetězec, který se má použít jako záhlaví sloupce v sestavách profileru.

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak připojit k spuštěné instanci aplikace s ID procesu 12345.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
