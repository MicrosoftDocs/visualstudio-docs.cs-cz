---
title: Příkaz VSPerfASPNetCmd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9b175cb5dd0c555aeaaafb30b7927c3fc81bff4
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281755"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
**VSPerfASPNetCmd.exe** nástroj příkazového řádku vám umožní profilu technologie ASP.Net webové servery bez nutnosti nastavit proměnné prostředí nebo restartovat počítač. Použití **VSPerfASPNetCmd.exe** místo [VSPerfCmd](../profiling/vsperfcmd.md) Pokud profilujete webů ASP.NET a není nutné další funkce poskytovaná modulem **VSPerfCmd**. Další informace o **VSPerfASPNetCmd**, naleznete v tématu [profilace pohotová webových stránek pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **Příkaz VSPerfASPNetCmd** je upřednostňovaný příkazového řádku nástroje pro použití při použití samostatného profileru Profilovat webu ASP.NET.  
  
## <a name="syntax"></a>Syntaxe  
 **příkaz vsperfaspnetcmd** [/*možnosti*] *webu*  
  
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ Ukázkové** nebo **/s**|Profily webu pomocí metody vzorkování. **/ Ukázkové** je výchozí metodou. / Ukázkové nelze použít s **/Trace**.|  
|**/ Trasování** nebo **/t**|Profily webu pomocí metody instrumentace. / Trasování nelze použít s **/Sample**.|  
|**Či na disku paměti**[**:**`Type`] nebo **/m**[**:**{**a**&#124;**l**}]|Profily přidělení paměti a volitelně profily správu životnosti objektů (uvolnění paměti). **/ Paměti** jde použít s vzorkování nebo metody instrumentace.<br /><br /> *Typ* může být jedna z následujících akcí:<br /><br /> -   **přidělení** (nebo **a**) shromažďuje jenom data přidělení paměti.<br />-   **Doba života** (nebo **l**) shromažďuje data o přidělování a objekt životním cyklu paměti.<br /><br /> Výchozí hodnota `Type` je **přidělení**.|  
|**/ Tip** nebo **/i**|Přidá podrobné žádosti ASP.NET a informace o volání ADO.NET data profilace. **/ Tip** jde použít s vzorkování nebo instrumentace metody a je možné s **Memory** možnost.|  
|**/ Output:** `File` nebo   **/o:**`File`|Určuje cestu a název souboru dat profilování (. *Vsp*) soubor.|  
|**/ NoWait** nebo **/n**|Vrátí příkaz výzva okamžitě tak, aby další příkazy lze použít v okně příkazového řádku. Je nutné zadat **příkaz VSPerfASPNETCmd/Shutdown** na samostatný příkazový řádek vypnout profilování.|  
|**/ PackSymbols**[: {**na**&#124;**vypnout**} nebo **/p**[: {**na**&#124;**vypnout**}|Vloží symboly (názvy funkce a parametrů, atd.) v profilaci dat (. *Vsp*) soubor.|  
|**/ Shutdown:** `Website`nebo   **/d:**`Website`|Zapne profilaci vypnout. Použijte parametr příkazového řádku po použití **/nowait** možnosti spuštění profilace, nebo pokud profiler neočekávaně ukončí. Zadejte stejnou adresu url, kterou jste použili v původním **VSPerfASPNETCmd** příkazu.|  
|`Website`|Adresu url webu, který má být profilována.|  
  
## <a name="see-also"></a>Viz také:  
 [Pohotová profilace stránek pomocí VSPerfASPNETCmd webových](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
