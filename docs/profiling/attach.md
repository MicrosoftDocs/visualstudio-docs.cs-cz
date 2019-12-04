---
title: Připojit | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773736"
---
# <a name="attach"></a>Připojit
Možnost **připojit** *VSPerfCmd. exe* spustí ukázku profilace spuštěného procesu určeného ID procesu (PID).

 Chcete-li použít možnost **připojit** , je nutné zadat **ukázkovou** metodu v možnosti Spustit.

> [!NOTE]
> Pokud byla možnost **Start** zadána s možností **CrossSession** , musí být jakákoli volání **VSPerfCmd/attach** nebo **VSPerfCmd/detach** také určovat **CrossSession**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>Parametry
 `ProcessID` ID procesu (PID) spuštěného procesu. PID spuštěného procesu najdete na kartě procesy ve Správci úloh systému Windows.

## <a name="valid-options"></a>Platné možnosti
 Následující možnosti **VSPerfCmd** lze kombinovat s možností **připojit** na jednom příkazovém řádku.

 **CrossSession** Povoluje profilování aplikací v jiných relacích než v přihlašovací relaci. Vyžaduje se, pokud byla zadána možnost **Start** s možností **CrossSession** .

 **Start:** `Method` inicializuje relaci profileru příkazového řádku a nastaví určenou metodu profilace.

 **TargetCLR** Určuje verzi modulu .NET Framework Common Language Runtime (CLR), která má být profilovaná v případě, že je v relaci profilace načtena více než jedna verze. Ve výchozím nastavení je první načtená verze profilovaná.

 **GlobalOn globaloff** Obnoví profil (**GlobalOn**) nebo pozastaví (**globaloff**), ale neukončí relaci profilování.

 **ProcessOn:** `PID` **ProcessOff:** `PID` obnoví profilování (**ProcessOn**) nebo pozastaví (**ProcessOff**) pro zadaný proces.

## <a name="interval-options"></a>Možnosti intervalu
 Jednu z následujících možností intervalu vzorkování lze zadat na příkazovém řádku připojit. Výchozí interval vzorkování je 10 000 000 hodinových cyklů procesoru.

 **Timer**[ **:** `Cycles`]**PF**[ **:** `Events`]**sys**[<strong>:</strong>Events]**čítač**[ **:** `Name`,`Reload`,`FriendlyName`] Určuje počet a typ intervalu vzorkování.

- **Timer** – ukázky všech `Cycles` hodinových cyklů procesoru. Pokud není zadán `Cycles`, budou použity cykly 10 000 000.

- **PF** – ukázky každé chyby stránky `Events`. Není-li zadán `Events`, jsou použity 10 chyb stránky.

- **Sys** – ukázky každé `Events` volání do operačního systému. Pokud není zadaný `Events`, použijí se 10 volání systému.

- **Counter** -Samples každých `Reload` počet ČÍTAČŮ výkonu procesoru určených `Name`. Volitelně můžete `FriendlyName` zadat řetězec, který se použije jako záhlaví sloupce v sestavách profileru.

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak se připojit ke spuštěné instanci aplikace s ID procesu 12345.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>Viz také:
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
