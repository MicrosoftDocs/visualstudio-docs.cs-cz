---
title: VSPerfMon | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779893"
---
# <a name="vsperfmon"></a>VSPerfMon
Nástroj VSPerfMon můžete použít ke shromažďování dat o výkonu pro aplikaci; obvykle tento nástroj je spuštěn *VSPerfCmd.exe*. VSPerfMon zobrazí další informace o procesu připojit nebo odpojit, který není k dispozici pomocí nástroje VSPerfCmd. Chcete-li zobrazit tyto informace, spusťte VSPerfMon v samostatném okně. Chcete-li vyvolat VSPerfMon, použijte následující syntaxi:

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 Následující tabulka popisuje volby nástroje VSPerfMon:

|Možnosti|Popis|
|-------------|-----------------|
|**U**|Přesměrovaný výstup konzoly je zapsán jako Unicode.  Toto musí být první zadaná možnost.|
|**VÝSTUP:** `<` *název souboru*`>`|Přesměruje výstup na zadaný název souboru.|
|**Trasování**|Spustí sledování výkonu pro instrumentované profilování.|
|**Ukázka**|Spustí monitorování výkonu pro profilování vzorkování.|
|**Pokrytí**|Spustí sledování výkonu pro kolekci pokrytí kódu.|
|**Souběžnost**|Spustí sledování výkonu pro profilování konfliktů prostředků.|
|**UŽIVATEL:** `[` *uživatelské jméno* *domény* `\]`|Umožňuje klientovi přístup ke sledování výkonu ze zadaného účtu.|
|**KŘÍŽOVÁ RELACE**|Umožňuje profilování mezi relacemi.|
|**POČÍTADLO**`:cfg`|Při použití metody profilování instrumentace (TRACE) určuje čítač procesoru, který má být shromažďován v každém bodě instrumentace. Zadáním více možností čítače můžete shromáždit více dat čítače.<br /><br /> K určení dat čítače (*cfg*) použijte následující syntaxi:<br /><br /> **CounterName** [**,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** je název čítače vráceného příkazem VSPerfCmd /QueryCounters.<br />-   **Opětovné načtení** je interval vzorkování událostí čítače. Nepoužívejte *Reload* s metodou instrumentace.<br />- Pokud je zadán, **FriendlyName** nahradí **CounterName** v profilování nástroje názvy sloupců sestavy.|
|**WINCOUNTER**`:path`|Určuje čítač výkonu systému Windows, který má být zahrnut s daty značek. `path`je řetězec čítače výkonu systému Windows ve formátu cesty čítače PDH. Například:<br /><br /> \Procesor(0)\\% času procesoru<br /><br /> \Systémové\Kontextové přepínače/s|
|**AUTOMATICKÁ ZNAČKA**`:n`|Určuje časový interval (v milisekundách) mezi automatickými značkami při použití parametru /WINCOUNTER. Zaokrouhleno nahoru na nejbližších 500 ms.<br /><br /> K zakázání automatických značek použijte 0. (default =500ms-li nespecifikovaný)|

## <a name="see-also"></a>Viz také
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Zobrazení sestavy výkonu](../profiling/performance-report-views.md)
