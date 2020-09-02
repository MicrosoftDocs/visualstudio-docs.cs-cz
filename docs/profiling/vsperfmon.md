---
title: VSPerfMon | Microsoft Docs
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ee2423f552c6931b0c8b62181dc44186053c9460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329970"
---
# <a name="vsperfmon"></a>VSPerfMon
Nástroj VSPerfMon můžete použít ke shromažďování údajů o výkonu pro aplikaci. Tento nástroj se obvykle spouští pomocí *VSPerfCmd.exe*. VSPerfMon zobrazí další informace o připojení a odpojení procesu, které není k dispozici pomocí nástroje VSPerfCmd. Pokud si chcete zobrazit tyto informace, spusťte VSPerfMon v samostatném okně. K vyvolání VSPerfMon použijte následující syntaxi:

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 Následující tabulka popisuje možnosti nástroje VSPerfMon:

|Možnosti|Popis|
|-------------|-----------------|
|**U**|Přesměrovaný výstup konzoly je zapsaný jako Unicode.  Musí se jednat o první zadanou možnost.|
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
