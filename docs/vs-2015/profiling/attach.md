---
title: Připojit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 136ee79c8fc7a3c6d627d186cb2f0dd0266b7a42
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727322"
---
# <a name="attach"></a>Připojit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **připojit** možnost zahájení profilace vzorku spuštěný proces zadaný pomocí ID procesu (PID).  
  
 Použít **připojit** možnost, je nutné zadat **ukázka** metoda ve variantě pro spuštění.  
  
> [!NOTE]
>  Pokud **Start** s byl zadán příkaz **Crosssession** možnost, všechna volání do **VSPerfCmd /Attach** nebo **VSPerfCmd/Detach** musí také zadejte **Crosssession**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `ProcessID`  
 ID procesu (PID) spuštěného procesu. Na kartě procesy ve Správci úloh Windows je uvedena PID spuštěnému procesu.  
  
## <a name="valid-options"></a>Platné možnosti  
 Následující **VSPerfCmd** možnosti lze kombinovat s **připojit** možnost v jednom příkazovém řádku.  
  
 **Crosssession**  
 Umožňuje profilování aplikace v relacích než přihlašovací relace. Požadováno pokud **Start** s byl zadán příkaz **Crosssession** možnost.  
  
 **Spusťte:** `Method`  
 Inicializuje relaci příkazového řádku profileru a nastaví zadané metodě profilování.  
  
 **TargetCLR**  
 Určuje verzi nástroje rozhraní .NET Framework CLR Common Language Runtime () do profilu načtena více než jedna verze v relaci profilování. Ve výchozím nastavení je Profilovat první načtené verze.  
  
 **GlobalOn GlobalOff**  
 Obnoví (**GlobalOn**) nebo pozastavení (**GlobalOff**) profilace, ale nemá na konci relace profilování.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Obnoví (**ProcessOn**) nebo pozastavení (**ProcessOff**) profilace pro zadaný proces.  
  
## <a name="interval-options"></a>Možnosti intervalu  
 Jeden z následujících možností interval vzorkování se dá nastavit na příkazovém řádku připojit. Výchozí interval vzorkování je 10 000 000 hodinových cyklů procesoru.  
  
 **Časovač**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[<strong>:</strong> Události]**čítač**[**:**`Name`,`Reload`,`FriendlyName`]  
 Určuje počet a typ použitého intervalu vzorkování.  
  
-   **Časovač** – ukázky každý `Cycles` hodinových cyklů procesoru. Pokud `Cycles` není zadán, 10 000 000 cykly se používají.  
  
-   **PF** – ukázky každý `Events` chyby stránek. Pokud `Events` není zadán, 10 chyb stránky se používají.  
  
-   **Sys** – ukázky každý `Events` volání do operačního systému. Pokud `Events` není zadán, 10 volání systému se používají.  
  
-   **Čítač** – ukázky každý `Reload` počet výkon procesoru čítač určené `Name`. Volitelně můžete `FriendlyName` můžete zadejte řetězec, který se použije jako záhlaví sloupce v sestavy profileru.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak se připojit ke spuštěné instanci aplikace s ID procesu 12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilace webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)



