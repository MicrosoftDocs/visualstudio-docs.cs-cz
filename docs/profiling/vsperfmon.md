---
title: VSPerfMon | Microsoft Docs
description: Přečtěte si, jak můžete pomocí nástroje VSPerfMon shromažďovat data o výkonu pro aplikaci. Tento nástroj se obvykle spouští nástrojem VSPerfCmd.exe.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 663bb5d1e126aa7ebc17f6720d81ac8eafd1e265
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911471"
---
# <a name="vsperfmon"></a>VSPerfMon
Nástroj VSPerfMon můžete použít ke shromažďování údajů o výkonu pro aplikaci. Tento nástroj se obvykle spouští pomocí *VSPerfCmd.exe*. VSPerfMon zobrazí další informace o připojení a odpojení procesu, které není k dispozici pomocí nástroje VSPerfCmd. Pokud si chcete zobrazit tyto informace, spusťte VSPerfMon v samostatném okně. K vyvolání VSPerfMon použijte následující syntaxi:

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 Následující tabulka popisuje možnosti nástroje VSPerfMon:

|Možnosti|Description|
|-------------|-----------------|
|**H**|Přesměrovaný výstup konzoly je zapsaný jako Unicode.  Musí se jednat o první zadanou možnost.|
|**Výstup:** `<` *název souboru*`>`|Přesměruje výstup na zadaný název souboru.|
|**Přehled**|Spustí sledování výkonu pro instrumentované profilování.|
|**SAMPLE**|Spustí monitorování výkonu pro profilaci vzorkování.|
|**Přehled**|Spustí sledování výkonu pro kolekci pokrytí kódu.|
|**CONCURRENCY**|Spustí sledování výkonu pro profilaci kolizí prostředků.|
|**Uživatel:** `[` *doména* `\]` *uživatelské jméno*|Umožňuje klientovi přístup ke sledování výkonu ze zadaného účtu.|
|**CROSSSESSION**|Povoluje profilování mezi jednotlivými relacemi.|
|**Čítač**`:cfg`|Když se použije metoda profilace instrumentace (TRACE), určuje čítač PROCESORů, které se mají shromáždit v každém bodu instrumentace. Můžete shromáždit více dat čítače zadáním více možností čítače.<br /><br /> K určení dat čítače (*cfg*) použijte následující syntax:<br /><br /> **CounterName** [**, reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** je název čítače vráceného příkazem VSPerfCmd/QueryCounters.<br />-   **Opětovné načtení** je interval vzorkování události čítače. Nepoužívejte metodu *Loading* s metodou instrumentace.<br />-Je-li zadán parametr **FriendlyName** , nahradí **CounterName** v nástroje pro profilaci názvy sloupců sestav.|
|**WINCOUNTER**`:path`|Určuje čítač výkonu systému Windows, který má být zahrnut do dat značek. `path` je řetězec čítače výkonu systému Windows ve formátu cesty čítače PDH. Příklad:<br /><br /> \Processor (0) \\ % času procesoru<br /><br /> Přepínače \System\Context/s|
|Automatického **označení**`:n`|Určuje časový interval (v milisekundách) mezi automatickými značkami při použití přepínače/WINCOUNTER. ZAOKROUHLOVÁNO. Zaokrouhlí se na nejbližší 500 ms.<br /><br /> Chcete-li zakázat automatické značky, použijte hodnotu 0. (výchozí = 500 ms je-li Neurčeno)|

## <a name="see-also"></a>Viz také
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Zobrazení sestav výkonu](../profiling/performance-report-views.md)
