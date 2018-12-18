---
title: Spuštění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbecc61e5203495e33aa4417e954607d8cdf6be8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676527"
---
# <a name="start"></a>Spustit
**Start** volba je *VSPerfCmd.exe* možnost, která inicializuje možnost profileru zadané metodě profilování.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Method`  
 Musí být jedna z následujících klíčových slov:  
  
-   **TRASOVÁNÍ** -určuje metody instrumentace.  
  
-   **Ukázka** -určuje metody vzorkování.  
  
-   **POKRYTÍ** -určuje pokrytí kódu.  
  
-   **SOUBĚŽNOST** -určuje metodu kolize prostředků.  
  
## <a name="required-options"></a>Požadované možnosti  
 **Výstup** možnost musí být zadán při **Start** je zadán v příkazovém řádku.  
  
 **Výstup:** `filename`  
 Určuje název výstupního souboru.  
  
## <a name="exclusive-options"></a>Výhradní možnosti  
 Tyto možnosti lze použít pouze s **Start** možnost příkazového řádku.  
  
 **CrossSession**&#124;**CS**  
 Umožňuje procesy profilace. Názvy možností **CrossSession** a **CS** jsou podporovány.  
  
 **Uživatel:**[`domain\`]`username`  
 Umožňuje přístup klienta k monitoru ze zadaného účtu.  
  
 **WinCounter:** `Path` [**Automark**:`n`]  
 **WinCounter** určuje čítač výkonu Windows zahrnout jako značky v souboru dat profilování. **AutoMark** Určuje interval v milisekundách mezi kolekcemi datového souboru.  
  
## <a name="invalid-options"></a>Neplatné možnosti  
 Tyto možnosti nelze použít s **Start** možnost příkazového řádku.  
  
 **Status**  
 **Stav** se vztahuje na tyto procesy, které jsou profilovány. Vypíše procesy a vlákna a jejich aktuální stavy profilu (zapnuto/vypnuto). Například, pokud proces zastavená **stav** nebude to znamenat v sestavě. **Stav** se zobrazí, že je buď profilována procesu nebo ne.  
  
 **Vypnutí**[**:**`Timeout`]  
 Vypne profilování.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití *VSPerfCmd.exe* **Start** možnost pro inicializaci profileru.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Viz také:  
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [Samostatné aplikace profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil služby](../profiling/command-line-profiling-of-services.md)