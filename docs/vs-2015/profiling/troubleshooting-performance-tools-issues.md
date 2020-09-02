---
title: Řešení potíží s nástroji pro výkon | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: troubleshooting
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 575f17c641eb057dc01fb3302098bd9f8b47f9c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815505"
---
# <a name="troubleshooting-performance-tools-issues"></a>Řešení potíží s nástroji pro měření výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při použití Nástroje pro profilaci se může vyskytnout některý z následujících problémů:  
  
- [Nástroje pro profilaci neshromažďuje žádná data.](#NoDataCollected)  
  
- [Zobrazení výkonu a sestavy zobrazují čísla pro názvy funkcí](#NoSymbols)  
  
## <a name="no-data-is-collected-by-the-profiling-tools"></a><a name="NoDataCollected"></a> Nástroje pro profilaci neshromažďuje žádná data.  
 Po vytvoření profilu aplikace se nevytvoří soubor dat profilování (. vsp) a v okně výstup nebo v příkazovém okně se zobrazí následující upozornění:  
  
 PRF0025: nebyla shromážděna žádná data.  
  
 Tento problém může být způsoben několika problémy:  
  
- Proces, který byl profilace pomocí metody vzorkování nebo paměti .NET, spouští podřízený proces, který se stává procesem, který provádí práci aplikace. Některé aplikace například přečtou příkazový řádek a určí, zda byly spuštěny jako aplikace systému Windows nebo jako aplikace příkazového řádku. Pokud se požaduje aplikace pro Windows, původní proces spustí nový proces nakonfigurovaný jako aplikaci pro Windows a pak se původní proces ukončí. Vzhledem k tomu, že Nástroje pro profilaci neshromažďují automaticky data pro podřízené procesy, nejsou shromažďována žádná data.  
  
     Pokud chcete v této situaci shromažďovat data profilace, Připojte profiler k podřízenému procesu místo spuštění aplikace v profileru. Další informace najdete v tématu [Postup: připojení a odpojení nástrojů výkonu ke spouštění procesů](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) a [připojení (VSPerfCmd)](../profiling/attach.md) .  
  
## <a name="performance-views-and-reports-display-numbers-for-function-names"></a><a name="NoSymbols"></a> Zobrazení výkonu a sestavy zobrazují čísla pro názvy funkcí  
 Po profilování aplikace uvidíte čísla místo názvů funkcí v sestavách a zobrazeních.  
  
 Příčinou tohoto problému je, že modul analýzy Nástroje pro profilaci nedokáže najít soubory. pdb, které obsahují informace o symbolech, které mapují informace o zdrojovém kódu, například názvy funkcí a čísla řádků zkompilovaného souboru. Ve výchozím nastavení kompilátor vytvoří soubor. pdb při sestavení souboru aplikace. Odkaz na místní adresář souboru. pdb je uložený v kompilované aplikaci. Analytický modul vyhledá odkazovaný adresář pro soubor. pdb a pak v souboru, který v současné době obsahuje soubor aplikace. Pokud soubor. pdb nebyl nalezen, používá modul analýzy posun funkcí místo názvů funkcí.  
  
 Problém můžete vyřešit jedním ze dvou způsobů:  
  
- Vyhledejte soubory. pdb a umístěte je do stejného adresáře jako soubory aplikace.  
  
- Vložte informace o symbolech do souboru dat profilování (. vsp). Další informace najdete v tématu [ukládání informací o symbolech pomocí datových souborů výkonu](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
> Analytický modul vyžaduje, aby byl soubor. pdb stejná jako verze kompilovaného souboru aplikace. Soubor. pdb ze staršího nebo pozdějšího sestavení souboru aplikace nebude fungovat.
