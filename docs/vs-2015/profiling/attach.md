---
title: Připojit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b9adb5a0a47c1ee98e0e390cfaf8b3a6dc78146
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831152"
---
# <a name="attach"></a>Připojit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost VSPerfCmd.exe **připojit** spustí ukázku profilace spuštěného procesu určeného ID procesu (PID).  
  
 Chcete-li použít možnost **připojit** , je nutné zadat **ukázkovou** metodu v možnosti Spustit.  
  
> [!NOTE]
> Pokud byla možnost **Start** zadána s možností **CrossSession** , musí být jakákoli volání **VSPerfCmd/attach** nebo **VSPerfCmd/detach** také určovat **CrossSession**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `ProcessID`  
 IDENTIFIKÁTOR procesu (PID) spuštěného procesu. PID spuštěného procesu najdete na kartě procesy ve Správci úloh systému Windows.  
  
## <a name="valid-options"></a>Platné možnosti  
 Následující možnosti **VSPerfCmd** lze kombinovat s možností **připojit** na jednom příkazovém řádku.  
  
 **CrossSession**  
 Povoluje profilování aplikací v jiných relacích než v přihlašovací relaci. Vyžaduje se, pokud byla zadána možnost **Start** s možností **CrossSession** .  
  
 **Začátek:**`Method`  
 Inicializuje relaci profileru příkazového řádku a nastaví určenou metodu profilace.  
  
 **TargetCLR**  
 Určuje verzi modulu .NET Framework Common Language Runtime (CLR), která má být profilovaná v případě, že je v relaci profilace načtena více než jedna verze. Ve výchozím nastavení je první načtená verze profilovaná.  
  
 **GlobalOn GlobalOff**  
 Obnoví profil (**GlobalOn**) nebo pozastaví (**globaloff**), ale neukončí relaci profilování.  
  
 **ProcessOn:** `PID` **ProcessOff:**`PID`  
 Obnoví (**ProcessOn**) nebo pozastaví profilování (**ProcessOff**) pro zadaný proces.  
  
## <a name="interval-options"></a>Možnosti intervalu  
 Jednu z následujících možností intervalu vzorkování lze zadat na příkazovém řádku připojit. Výchozí interval vzorkování je 10 000 000 hodinových cyklů procesoru.  
  
 **Timer**[**:** `Cycles` ]**PF**[**:** `Events` ]**sys**[<strong>:</strong>Events]**čítač**[**:** `Name` , `Reload` , `FriendlyName` ]  
 Určuje počet a typ intervalu vzorkování.  
  
- **Timer** – ukázky všech `Cycles` hodinových cyklů procesoru. Pokud `Cycles` parametr není zadán, jsou použity cykly 10 000 000.  
  
- **PF** – ukázky všech `Events` chyb stránky. Pokud `Events` parametr není zadán, jsou použity 10 chyb stránky.  
  
- **Sys** – ukázky všech `Events` volání na operační systém. Pokud `Events` parametr není zadán, budou použity 10 volání systému.  
  
- **Counter** -Samples každý `Reload` počet čítačů výkonu procesoru určených parametrem `Name` . Volitelně `FriendlyName` můžete zadat řetězec, který se použije jako záhlaví sloupce v sestavách profileru.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak se připojit ke spuštěné instanci aplikace s ID procesu 12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací v ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
