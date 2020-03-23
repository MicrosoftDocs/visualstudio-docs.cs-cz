---
title: PF | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07ec6d636ec087386fdc9462ae09db55400957a9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778411"
---
# <a name="pf"></a>PF
*Možnost VSPerfCmd.exe* **PF** nastaví událost profilování, která je vzorkována na chyby stránky, a volitelně změní počet chyb stránky v intervalu vzorkování z výchozí hodnoty 10.

> [!NOTE]
> **PF** nelze použít v 64bitových systémech.

**Pf** lze použít pouze v příkazovém řádku, který obsahuje také **možnost Spustit** nebo **Připojit.**

 Ve výchozím nastavení je událost vzorkování nastavena na nezastavené cykly hodin procesoru a interval vzorkování je nastaven na 10 000 000. Možnosti **Časovač**, **PF**, **Sys**a **Čítač** umožňují nastavit vzorkovací událost a interval vzorkování. Možnost **GC** shromažďuje data paměti .NET při každé události přidělení a uvolňování paměti. Na příkazovém řádku lze zadat pouze jednu z těchto možností.

 Vzorkovací událost a interval vzorkování lze nastavit pouze v prvním příkazovém řádku, který obsahuje možnost **Spustit** nebo **Připojit.**

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>Parametry
 `Events`Celá hodnota, která určuje počet událostí poruchy stránky v intervalu vzorkování. Pokud `Events` není zadán, interval je nastaven na 10.

## <a name="required-options"></a>Požadované možnosti
 **Pf** lze zadat pouze na příkazovém řádku, který obsahuje jednu z následujících možností.

 **Spuštění:** `AppName` Spustí profiler a aplikaci určenou AppName.

 **Připojit:** `PID` Připojí profiler k procesu určenému AppName.

## <a name="invalid-options"></a>Neplatné možnosti
 Následující možnosti nelze zadat na stejném příkazovém řádku jako **PF**.

 **Časovač**[**:**`Cycles`] Nastaví událost vzorkování na cykly `Cycles`hodin procesoru a volitelně nastaví interval vzorkování na . Výchozí interval časovače je 10 000 000.

 **Sys**[**:**`Events`] Nastaví událost vzorkování na volání z profilované aplikace do jádra operačního `Events`systému (syscalls) a volitelně nastaví interval vzorkování na . Výchozí interval Sys je 10.

 **Čítač:** `Name`[`,Reload`[`,FriendlyName`]] Nastaví událost `Name` vzorkování na `Reload`čítač výkonu procesoru určený a nastaví interval vzorkování na .

 **GC**[**:****{ Allocation**&#124;**Lifetime**}] Shromažďuje data paměti .NET. Ve výchozím nastavení (**Přidělení**) jsou data shromažďována při každé události přidělení paměti. Když je zadán parametr **Životnost,** data jsou také shromažďována při každé události uvolňování paměti.

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak nastavit ukázkovou událost profilování na chyby stránky a nastavit interval vzorkování na 20 chyb stránky.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
