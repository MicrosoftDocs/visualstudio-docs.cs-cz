---
title: VSPerfMon | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 50519554f7ec71e277dc776b05bc2967c1071f52
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779893"
---
# <a name="vsperfmon"></a>VSPerfMon
Nástroj VSPerfMon můžete použít ke shromažďování údajů o výkonu pro aplikaci. Tento nástroj je obvykle spouštěn nástrojem *VSPerfCmd. exe*. VSPerfMon zobrazí další informace o připojení a odpojení procesu, které není k dispozici pomocí nástroje VSPerfCmd. Pokud si chcete zobrazit tyto informace, spusťte VSPerfMon v samostatném okně. K vyvolání VSPerfMon použijte následující syntaxi:

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 Následující tabulka popisuje možnosti nástroje VSPerfMon:

|Možnosti|Popis|
|-------------|-----------------|
|**H**|Přesměrovaný výstup konzoly je zapsaný jako Unicode.  Musí se jednat o první zadanou možnost.|
|**Výstup:** `<` *název souboru* `>`|Přesměruje výstup na zadaný název souboru.|
|**Přehled**|Spustí sledování výkonu pro instrumentované profilování.|
|**VZORKU**|Spustí monitorování výkonu pro profilaci vzorkování.|
|**Přehled**|Spustí sledování výkonu pro kolekci pokrytí kódu.|
|**CONCURRENCY**|Spustí sledování výkonu pro profilaci kolizí prostředků.|
|**Uživatel:** `[` *doména* `\]` *uživatelské jméno*|Umožňuje klientovi přístup ke sledování výkonu ze zadaného účtu.|
|**CROSSSESSION**|Povoluje profilování mezi jednotlivými relacemi.|
|`:cfg` **čítače**|Když se použije metoda profilace instrumentace (TRACE), určuje čítač PROCESORů, které se mají shromáždit v každém bodu instrumentace. Můžete shromáždit více dat čítače zadáním více možností čítače.<br /><br /> K určení dat čítače (*cfg*) použijte následující syntax:<br /><br /> **CounterName** [ **, reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** je název čítače vráceného příkazem VSPerfCmd/QueryCounters.<br />-   **opětovného načtení** je interval vzorkování události čítače. Nepoužívejte metodu *Loading* s metodou instrumentace.<br />-Je-li zadán parametr **FriendlyName** , nahradí **CounterName** v nástroje pro profilaci názvy sloupců sestav.|
|**WINCOUNTER** `:path`|Určuje čítač výkonu systému Windows, který má být zahrnut do dat značek. `path` je řetězec čítače výkonu systému Windows ve formátu cesty čítače PDH. Příklad:<br /><br /> \Processor (0)\\% času procesoru<br /><br /> Přepínače \System\Context/s|
|`:n` automatického **označování**|Určuje časový interval (v milisekundách) mezi automatickými značkami při použití přepínače/WINCOUNTER. ZAOKROUHLOVÁNO. Zaokrouhlí se na nejbližší 500 ms.<br /><br /> Chcete-li zakázat automatické značky, použijte hodnotu 0. (výchozí = 500 ms je-li Neurčeno)|

## <a name="see-also"></a>Viz také:
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Zobrazení sestav výkonu](../profiling/performance-report-views.md)
