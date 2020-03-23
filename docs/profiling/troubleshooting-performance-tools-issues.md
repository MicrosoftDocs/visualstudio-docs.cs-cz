---
title: Poradce při potížích s nástroji pro sledování výkonu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 514b910f2c19822dc821b8c9a52ae96b8aac80f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778099"
---
# <a name="troubleshoot-performance-tools-issues"></a>Poradce při potížích s nástroji pro výkon
Při použití nástrojů profilování může dojít k jednomu z následujících problémů:

- [Pomocí nástrojů profilování nejsou shromažďována žádná data.](#no-data-is-collected-by-the-profiling-tools)

- [Zobrazení výkonu a sestavy zobrazují čísla pro názvy funkcí](#performance-views-and-reports-display-numbers-for-function-names)

## <a name="no-data-is-collected-by-the-profiling-tools"></a>Pomocí nástrojů profilování nejsou shromažďována žádná data.
 Po profilování aplikace, profilování data (.* vsp*) soubor není vytvořen a zobrazí se následující upozornění v okně **Výstup** nebo v příkazovém okně:

 PRF0025: Nebyly shromážděny žádné údaje.

 Tento problém může být způsoben několika problémy:

- Proces, který byl profilován pomocí vzorkování nebo metody paměti .NET spustí podřízený proces, který se stane procesem, který provádí práci aplikace. Některé aplikace například čtou příkazový řádek a zjišťují, zda byly spuštěny jako aplikace systému Windows nebo jako aplikace příkazového řádku. Pokud byla požadována aplikace systému Windows, původní proces spustí nový proces nakonfigurovaný jako aplikace systému Windows a potom původní proces ukončí. Vzhledem k tomu, že nástroje profilování neshromažďují automaticky data pro podřízené procesy, nejsou shromažďována žádná data.

     Chcete-li shromažďovat data profilování v této situaci, připojte profiler k podřízenému procesu namísto spuštění aplikace s profilem. Další informace naleznete v [tématu Jak: Připojení a odpojení nástrojů pro sledování výkonu ke spuštěným procesům](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) a [připojení (VSPerfCmd)](../profiling/attach.md)

## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Zobrazení výkonu a sestavy zobrazují čísla pro názvy funkcí
 Po profilování aplikace se v sestavách a zobrazeních zobrazují čísla namísto názvů funkcí.

 Tento problém je způsoben profilování nástroje analýzy motoru nelze najít . *pdb* soubory, které obsahují informace o symbolu, který mapuje informace o zdrojovém kódu, takové názvy funkcí a čísla řádků do zkompilovaného souboru. Ve výchozím nastavení kompilátor vytvoří . *pdb* souboru, když je soubor aplikace vytvořen. Odkaz na místní adresář rozhraní . *pdb* soubor je uložen v kompilované aplikaci. Modul analýzy vyhledá v odkazovaném adresáři pro . *pdb* a potom v souboru, který aktuálně obsahuje soubor aplikace. Pokud . *pdb* soubor nebyl nalezen, modul analýzy používá funkce posuny namísto názvy funkcí.

 Problém můžete vyřešit jedním ze dvou způsobů:

- Najít . *pdb* soubory a umístěte je do stejného adresáře jako soubory aplikace.

- Vložte informace o symbolu do dat profilování (.* vsp*). Další informace naleznete v [tématu Ukládání informací o symbolech pomocí datových souborů výkonu](../profiling/saving-symbol-information-with-performance-data-files.md).

> [!NOTE]
> Modul analýzy vyžaduje, aby . *PDB* soubor je stejná verze jako zkompilovaný soubor aplikace. A. *pdb* soubor z dřívějšího nebo novějšího sestavení souboru aplikace nebude fungovat.
