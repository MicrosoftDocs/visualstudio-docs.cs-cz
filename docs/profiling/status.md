---
title: Stav | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cd721dc6682057519821ee155ac8a5d803769dc
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676006"
---
# <a name="status"></a>Stav
*VSPerfCmd.exe* **stav** možnost zobrazí informace o stavu profileru a všechny procesy, které jsou právě profilována.  
  
 **Stav** možnost musí být zadán v příkazovém řádku jedinou možností. Profiler je nutné inicializovat s *VSPerfCmd.exe* **Start** možnost před zobrazením libovolný stav.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="remarks"></a>Poznámky  
 **Stav** možnost se zobrazí následující informace o stavu pro profiler.  
  
 **Název výstupního souboru**  
 Název a cesta k souboru aktuální datového souboru profilování.  
  
 **Režim kolekce**  
 UKÁZKOVÝ nebo trasování  
  
 **Maximum procesů**  
 Maximální počet procesů, které jde Profilovat najednou a počet aktuálně aktivních procesů.  
  
 **Maximální počet vláken**  
 Maximální počet vláken, které jde Profilovat najednou.  
  
 **Počet vyrovnávacích pamětí**  
 Počet vyrovnávacích pamětí, které jsou vyhrazené pro zápis dat profilování.  
  
 **Velikost vyrovnávací paměti**  
 Velikost v bajtech vyrovnávací paměti.  
  
 **Stav** možnost se zobrazí následující informace o stavu pro každý proces, který je právě profilována.  
  
 **Proces**  
 Název profilovaný proces.  
  
 **ID procesu**  
 Identifikátor systému procesu.  
  
 **Počet vláken**  
 Počet vláken v tuto chvíli.  
  
 **Počet operací spustit/zastavit**  
 Počet primární interní profiler k řízení shromažďování dat pro tento proces. Počet musí být rovna jedné shromažďovat data. Počet operací spustit/zastavit lze ovládat pomocí rozhraní API profileru a možnosti, VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**, a **ThreadOff**.  
  
 **Počet operací pozastavit/pokračovat**  
 Počet sekundárních interní profiler řízení shromažďování dat pro tento proces. Počet musí být menší než nebo rovna hodnotě nula, pokud chcete shromažďovat data. **Pozastavit/Pokračovat** počet může být používán pouze rozhraní API profileru.  
  
 **Uživatelé s přístupovými oprávněními k monitoru**  
 Obsahuje seznam uživatelů, kteří mají přístup k profileru. Další uživatelé lze udělit přístup pomocí VSPerfCmd.exe **správce** možnost  
  
## <a name="see-also"></a>Viz také:  
 [Nástroj VSPerfCmd](../profiling/vsperfcmd.md)   
 [Samostatné aplikace profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Webové aplikace ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil služby](../profiling/command-line-profiling-of-services.md)