---
title: Řešení potíží s nástroji pro výkon | Microsoft Docs
description: Seznamte se s různými informacemi, které se mohou vyskytnout při odstraňování potíží s nástroji pro zvýšení výkonu, například když nejsou shromažďována žádná data pomocí nástrojů pro profilaci.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d371384d70c6a6a7a57620839eca2c41c292d0b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922049"
---
# <a name="troubleshoot-performance-tools-issues"></a>Řešení potíží s nástroji pro výkon
Při použití Nástroje pro profilaci se může vyskytnout některý z následujících problémů:

- [Nástroje pro profilaci neshromažďují žádná data.](#no-data-is-collected-by-the-profiling-tools)

- [Zobrazení výkonu a sestavy zobrazují čísla pro názvy funkcí](#performance-views-and-reports-display-numbers-for-function-names)

## <a name="no-data-is-collected-by-the-profiling-tools"></a>Nástroje pro profilaci neshromažďují žádná data.
 Po vytvoření profilu aplikace se data profilace (.*soubor VSP*) není vytvořen a v okně **výstup** nebo v příkazovém okně se zobrazí následující upozornění:

 PRF0025: nebyla shromážděna žádná data.

 Tento problém může být způsoben několika problémy:

- Proces, který byl profilace pomocí metody vzorkování nebo paměti .NET, spouští podřízený proces, který se stává procesem, který provádí práci aplikace. Některé aplikace například přečtou příkazový řádek a určí, zda byly spuštěny jako aplikace systému Windows nebo jako aplikace příkazového řádku. Pokud se požaduje aplikace pro Windows, původní proces spustí nový proces nakonfigurovaný jako aplikaci pro Windows a pak se původní proces ukončí. Vzhledem k tomu, že Nástroje pro profilaci neshromažďují automaticky data pro podřízené procesy, nejsou shromažďována žádná data.

     Pokud chcete v této situaci shromažďovat data profilace, Připojte profiler k podřízenému procesu místo spuštění aplikace v profileru. Další informace najdete v tématu [Postup: připojení a odpojení nástrojů výkonu ke spouštění procesů](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) a [připojení (VSPerfCmd)](../profiling/attach.md) .

## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Zobrazení výkonu a sestavy zobrazují čísla pro názvy funkcí
 Po profilování aplikace uvidíte čísla místo názvů funkcí v sestavách a zobrazeních.

 Příčinou tohoto problému je, že modul analýzy Nástroje pro profilaci nedokáže najít. soubory *PDB* , které obsahují informace o symbolech, které mapují informace o zdrojovém kódu, například názvy funkcí a čísla řádků zkompilovaného souboru. Ve výchozím nastavení kompilátor vytvoří. soubor *PDB* , když je sestaven soubor aplikace. Odkaz na místní adresář. soubor *PDB* je uložený v kompilované aplikaci. Analytický modul hledá v odkazovaném adresáři. soubor *PDB* a potom v souboru, který aktuálně obsahuje soubor aplikace. Pokud. soubor *PDB* nebyl nalezen, modul analýzy používá posun funkcí místo názvů funkcí.

 Problém můžete vyřešit jedním ze dvou způsobů:

- Vyhledejte. soubory *PDB* a umístí je do stejného adresáře jako soubory aplikace.

- Vložte informace o symbolech do dat profilace (.*VSP*) soubor. Další informace najdete v tématu [ukládání informací o symbolech pomocí datových souborů výkonu](../profiling/saving-symbol-information-with-performance-data-files.md).

> [!NOTE]
> Analytický modul vyžaduje, aby. soubor *PDB* má stejnou verzi jako kompilovaný soubor aplikace. Určitého. soubor *PDB* z dřívějšího nebo pozdějšího sestavení souboru aplikace nebude fungovat.
