---
title: Odpojit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91b93eb99b1068e1695e26136eacc6abf2886774
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764488"
---
# <a name="detach"></a>Odpojit
VSPerfCmd.exe **odpojení** možnost-li zadán žádný odpojí profileru z zadaný procesy nebo všechny procesy. Profilace musí mít inicializovány pomocí metody vzorkování.  
  
 Profilace, která byla spuštěna s buď **spusťte** nebo **Attach** možnosti můžete odpojit s **odpojení**. Profileru může být reattched pomocí dalších **Attach** příkazy.  
  
 **Odpojení** nezavře profilování datového souboru. Použití **vypnutí** možnost ukončení profilování a zavřete soubor data.  
  
> [!NOTE]
>  Pokud **spustit** s byla zadána možnost **Crosssession** možnost, všechny volání **VSPerfCmd /Attach** nebo **VSPerfCmd /Detach** musí zadat také **Crosssession**.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### <a name="parameters"></a>Parametry  
 `PIDs|ProcessNames`  
 `PID` Identifikátor-číselné systému jeden nebo více procesů.  
  
 `ProcessNames` -Název procesu. Pokud používáte systém více instancí procesu s názvem, mohou být nepředvídatelné výsledky.  
  
 Více procesů oddělujte čárkami.  
  
 Pokud není zadaný žádný proces, je odpojit od všech procesů PROFILOVANÉHO profileru.  
  
## <a name="valid-options"></a>Platné možnosti.  
 Následující **VSPerfCmd** možnosti mohou být kombinovány s **Attach** možnost na jednoho příkazového řádku.  
  
 **Crosssession**  
 Umožňuje profilace – aplikace v relacích než přihlašovací relace. Požadováno pokud **spustit** s byla zadána možnost **Crosssession** možnost.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu **odpojení** příkaz pozastaví profilace a **vypnutí** příkaz zavře datový soubor profileru.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## <a name="see-also"></a>Viz také:  
 [Vsperfcmd –](../profiling/vsperfcmd.md)   
 [Profil samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil služby](../profiling/command-line-profiling-of-services.md)