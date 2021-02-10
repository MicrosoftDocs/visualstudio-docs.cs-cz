---
title: Stav | Microsoft Docs
description: Přečtěte si, jak možnost stav VSPerfCmd.exe zobrazuje informace o stavu profileru a všech procesech, které se momentálně profilují.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 894afcbf8827fe0b5d5662a4c20e302f8224263f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960036"
---
# <a name="status"></a>Status
Možnost  **stav** VSPerfCmd.exezobrazuje informace o stavu profileru a všech procesech, které jsou právě profilované.

 Možnost **stavu** musí být jedinou možností zadanou v příkazovém řádku. Aby bylo možné zobrazit libovolný stav, musí být profiler inicializován s možností *VSPerfCmd.exe* **Start** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>Parametry
 Žádné

## <a name="remarks"></a>Poznámky
 Možnost **stav** zobrazuje pro Profiler následující informace o stavu.

 **Název výstupního souboru** Cesta a název souboru aktuálního datového souboru profileru.

 **Režim shromažďování** Ukázka nebo trasování

 **Maximální počet procesů** Maximální počet procesů, které lze profilovat najednou, a počet aktuálně aktivních procesů.

 **Maximální počet vláken** Maximální počet vláken, která lze profilovat najednou.

 **Počet vyrovnávacích pamětí** Počet vyrovnávacích pamětí vyhrazených pro zápis dat profilování.

 **Velikost vyrovnávacích pamětí** Velikost vyrovnávací paměti v bajtech.

 Možnost **stav** zobrazuje následující informace o stavu pro každý proces, který je právě profilace.

 **Zpracování** Název profilované procesu.

 **ID procesu** Systémový identifikátor procesu

 **Počet vláken** Počet aktuálně prováděných vláken.

 **Spustit/zastavit počet** Počet primárních vnitřních profilerů pro řízení shromažďování dat pro tento proces. Aby bylo možné shromažďovat data, musí být počet rovno jedné. Na počet spuštění/zastavení se můžou manipulovat pomocí rozhraní API profileru a možností VSPerfCmd **GlobalOn**, **globaloff**, **ProcessOn**, **ProcessOff**, **ThreadOn** a **ThreadOff**.

 **Počet pozastavení/obnovení** Sekundární interní profilerový počet pro řízení shromažďování dat pro tento proces. Pro shromažďování dat musí být počet menší nebo roven nule. Počet operací **pozastavit/pokračovat** může být manipulován pouze pomocí rozhraní API profileru.

 **Uživatelé s přístupovými právy k monitorování** Zobrazuje jména uživatelů, kteří mají přístup k profileru. Dalším uživatelům se dá udělit přístup pomocí možnosti VSPerfCmd.exe **správce** .

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
