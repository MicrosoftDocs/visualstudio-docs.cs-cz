---
title: Odpojit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1b35765614f57350cdace560aa61c721cc831581
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64794167"
---
# <a name="detach"></a>Odpojit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost VSPerfCmd.exe **odpojení** odpojí Profiler od zadaných procesů nebo všech procesů, pokud nejsou zadány žádné. Profilování je nutné inicializovat pomocí metody vzorkování.  
  
 Profilace, která byla spuštěna buď pomocí **spuštění** , nebo možností **připojení** , lze odpojit pomocí možnosti **Odpojit**. Profiler se dá reattched pomocí dalších příkazů **připojit** .  
  
 Při **odpojení** se soubor dat profilování nezavře. Pro ukončení profilování a zavření datového souboru použijte možnost **vypnutí** .  
  
> [!NOTE]
> Pokud byla možnost **Start** zadána s možností **CrossSession** , musí být jakákoli volání **VSPerfCmd/attach** nebo **VSPerfCmd/detach** také určovat **CrossSession**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### <a name="parameters"></a>Parametry  
 `PIDs|ProcessNames`  
 `PID` – Číselný systém identifikátorem jednoho nebo více procesů.  
  
 `ProcessNames` – název procesu. Pokud je spuštěno více instancí pojmenovaného procesu, výsledky mohou být nepředvídatelné.  
  
 Více procesů oddělte čárkami.  
  
 Pokud není zadán žádný proces, Profiler je odpojen od všech profilování procesu.  
  
## <a name="valid-options"></a>Platné možnosti  
 Následující možnosti **VSPerfCmd** lze kombinovat s možností **připojit** na jednom příkazovém řádku.  
  
 **CrossSession**  
 Povoluje profilování aplikací v jiných relacích než v přihlašovací relaci. Vyžaduje se, pokud byla zadána možnost **Start** s možností **CrossSession** .  
  
## <a name="example"></a>Příklad  
 V tomto příkladu příkaz **Odpojit** pozastaví profilaci a příkaz pro **vypnutí** zavře datový soubor profileru.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
