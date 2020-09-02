---
title: VSPerfASPNetCmd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9cb81f17abd1e7891dc3f78a85d6d1276991f070
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145273"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj příkazového řádku **VSPerfASPNetCmd.exe** umožňuje profilovat weby ASP.NET, aniž byste museli nastavovat proměnné prostředí nebo restartovat počítač. Když vytváříte profilování ASP.NET websites, můžete místo [VSPerfCmd](../profiling/vsperfcmd.md) použít **VSPerfASPNetCmd.exe** a nepotřebujete další funkce, které poskytuje **VSPerCmd**. Další informace o **VSPerfASPNETCmd**najdete v tématu [rychlé profilování webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNETCmd** je preferovaný nástroj příkazového řádku, který se použije při použití samostatného profileru k profilování webu ASP.NET.  
  
## <a name="syntax"></a>Syntax  
 **VSPerfASPNETCmd** [/*Možnosti*] *Web*  
  
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Sample** nebo   **/s**|Na webu profily pomocí metody vzorkování. **/Sample** je výchozí metoda. /Sample nelze použít s **/Trace**.|  
|**/Trace** nebo   **/t**|Na webu profily pomocí metody instrumentace. /Trace nelze použít s **/Sample**.|  
|**/Memory**[**:** `Type` ] nebo **/m**[**:**{**a**&#124;**l**}]|Profily – přidělení paměti a volitelné profily životnosti objektů (uvolňování paměti). **/Memory** se dá použít s metodou vzorkování nebo instrumentace.<br /><br /> *Typ* může být jeden z následujících:<br /><br /> -   **alokace** **(nebo)** shromažďuje pouze data o přidělování paměti.<br />-   **Doba života** (nebo **l**) shromažďuje data o přidělování paměti a životnosti objektů.<br /><br /> Výchozí hodnota `Type` je **přidělení**.|  
|**/Tip** nebo   **/i**|Přidá podrobné informace o žádosti ASP.NET a informace o volání ADO.NET do dat profilace. **/Tip** se dá použít s metodou vzorkování nebo instrumentace a dá se použít s možností **/Memory** .|  
|**/Output:** `File` nebo   **/o:**`File`|Určuje cestu a název souboru dat profilování (. vsp).|  
|**/Nowait** nebo   **/n**|Vrátí příkazový řádek okamžitě, aby bylo možné použít další příkazy v okně příkazového řádku. Chcete-li zapnout profilování, je nutné zadat **VSPerfASPNETCmd/Shutdown** na samostatném příkazovém řádku.|  
|**/PackSymbols**[: {**on**&#124;**off**} nebo   **/p**[: {**on**&#124;**off**}|Vloží symboly (funkce a názvy parametrů atd.) do souboru dat profilování (. vsp).|  
|**/Shutdown:** `Website` nebo   **/d:**`Website`|Zapne profilaci. Použijte jako jedinou možnost na příkazovém řádku po použití možnosti **/nowait** ke spuštění profilování nebo pokud profiler neočekávaně skončí. Zadejte stejnou adresu URL, jakou jste použili v původním příkazu **VSPerfASPNETCmd** .|  
|`Website`|Adresa URL webu, který se má profilovat|  
  
## <a name="see-also"></a>Viz také  
 [Rychlé profilování webu pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
