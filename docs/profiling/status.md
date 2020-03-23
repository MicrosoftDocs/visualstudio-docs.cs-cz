---
title: Stav | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bf5e0fdf478e067f61b1d0e259cb1624380e4f02
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778242"
---
# <a name="status"></a>Status
**Možnost** *Stav VSPerfCmd.exe* zobrazuje informace o stavu profileru a všech procesech, které jsou aktuálně profilovány.

 Možnost **Stav** musí být jedinou možností určenou na příkazovém řádku. Před zobrazením libovolného stavu musí být inicializován profiler pomocí možnosti *Start v programu VSPerfCmd.exe.* **Start**

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>Parametry
 Žádný

## <a name="remarks"></a>Poznámky
 Možnost **Stav** zobrazí následující informace o stavu pro profiler.

 **Název výstupního souboru** Cesta a název souboru aktuálního datového souboru profileru.

 **Režim kolekce** VZOREK NEBO TRACE

 **Maximální počet procesů** Maximální počet procesů, které lze profilovat najednou a počet aktuálně aktivních procesů.

 **Maximální počet vláken** Maximální počet podprocesů, které lze profilovat najednou.

 **Počet vyrovnávacích pamětí** Počet vyrovnávacích pamětí vyhrazených pro zápis dat profilování.

 **Velikost vyrovnávacích pamětí** Velikost v bajtů vyrovnávací paměti.

 Možnost **Stav** zobrazí následující informace o stavu pro každý proces, který je právě profilován.

 **Proces** Název profilovaného procesu.

 **ID procesu** Identifikátor systému procesu.

 **Vlákna výčtu** Počet vláken, které jsou aktuálně spuštěny.

 **Počet start/stop** Primární počet interních profilerů pro řízení shromažďování dat pro tento proces. Počet musí být rovna jedné shromažďovat data. Počet Start/Stop lze manipulovat pomocí rozhraní API profileru a vsperfcmd možnosti **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**a **ThreadOff**.

 **Pozastavit/obnovit počet** Sekundární počet interních profilerů pro řízení shromažďování dat pro tento proces. Počet musí být menší nebo rovna nule shromažďovat data. Počet **Pozastavení/Obnovení** lze manipulovat pouze pomocí api profileru.

 **Uživatelé s přístupovými právy ke sledování** Uvádí jména uživatelů, kteří mají přístup k profileru. Dalším uživatelům lze udělit přístup pomocí možnosti **Správce** VSPerfCmd.exe

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
