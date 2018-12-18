---
title: 'Návod: Profiler XSLT | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4f401d253c81385dc197e912a7f9cc7d6156e393
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229447"
---
# <a name="walkthrough-xslt-profiler"></a>Návod: Profiler XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Profiler XSLT chyb vytváří detailní zprávy XSLT výkonu, které pomůže měřit, vyhodnotit a řešit problémy související s výkonem v kódu XSLT. Profiler XSLT zahrnuje užitečných rad pro XSL a XSLT optimalizace list stylu. Pro aplikace XSLT tento požadavek maximální výkon, tento nástroj může být nezbytné.  
  
## <a name="prerequisites"></a>Požadavky  
 Postupy v následující návod vyžadují Visual Studio 2010 and.NET Framework verze 4.0. Profiler XSLT dostupná pouze Microsoft Visual Studio Team System pomocí nástrojů pro profilaci sady nainstalované.  
  
### <a name="create-the-performance-report"></a>Vytvoření sestavy výkonu  
  
1.  Otevření dokumentu XSLT v sadě Visual Studio.  
  
2.  Klikněte na **profilu XSLT** možnost, která je k dispozici v nabídce XML.  
  
3.  Zadejte vstupní dokument XML. Pokud dokument XML již není otevřen, zobrazí se výzva k zadání soubor.  
  
4.  Spuštění analýzy a indikátoru průběhu zobrazí průběh v editoru.  
  
5.  Výstup XSLT je viditelný v podokně výstup.  
  
6.  Po ukončení relace výkonu, zkontrolujte zprávu o výkonu. Data uložená v sestavě výkonu umožňuje zobrazit a analyzovat výkon XSLT.  
  
### <a name="get-all-the-available-views"></a>Získání všech dostupných zobrazení  
  
1.  Klikněte na **aktuální zobrazení** rozevíracího seznamu zobrazíte všechny dostupné zobrazení.  
  
2.  Vyberte **souhrnné zobrazení** možnost **aktuální zobrazení** rozevíracího seznamu. Ve výchozím nastavení, zobrazí se sestava výkonu v **souhrnné zobrazení**. Toto zobrazení je výchozím bodem k určení problémů s výkonem pomocí XSLT dokumentů. **Souhrnné zobrazení** uvádí těchto datových bodů:  
  
    -   Nejvíce volané funkce  
  
    -   Funkce s většinou jednotlivé práce  
  
    -   Funkce beroucí nejdéle ke spuštění  
  
3.  Ve výchozím nastavení, existují tři sloupce pro každý datový bod: název funkce, počet volání v absolutní hodnota a procentuální hodnotu s názvem funkce, která se celkový počet funkce volání. Z každého datového bodu **souhrnné zobrazení**, můžete přejít na podrobnější zobrazení kliknutím pravým tlačítkem myši na funkci datových bodů.  
  
4.  Vyberte **zobrazení funkce** možnost **aktuální zobrazení** rozevíracího seznamu. **Zobrazení funkce** seznam funkcí, volá se během profilace. Data lze seřadit klepnutím na název sloupce. Sloupce zobrazí ve výchozím nastavení jsou:  
  
    -   **Název funkce**  
  
    -   **Uplynulý celkový čas**  
  
    -   **Uplynulý výhradní čas**  
  
    -   **Celkový čas aplikace**  
  
    -   **Výhradní čas aplikace**  
  
    -   **Počet volání**  
  
5.  Všechny sloupce času jsou zobrazeny v absolutní hodnoty a procenta. Termín **exkluzivní** odkazuje na celkový čas strávený provádění bez času spotřebovaného přidělenými jiné funkce volá se během provádění této funkce funkce.  
  
6.  Termín **celkový čas** odkazuje na celkovou dobu funkce stráven spouštěním, včetně spuštění všech funkcí názvem a určuje, zda některé z těchto volat funkce volá jiné funkce.  
  
### <a name="select-callercallee-view"></a>Vyberte zobrazení volající/volaný  
  
1.  Vyberte **volající/volaný** zobrazit **aktuální zobrazení** rozevíracího seznamu.  
  
2.  **Volající/volaný** zobrazení má následující tři samostatné části:  
  
    -   **Funkce, které volaly**: všechny funkce, které volaly konkrétní funkce je uvedený na horní část zobrazení.  
  
    -   **Aktuální funkce**: určitou funkci, která byla volána je uveden v prostřední části zobrazení.  
  
    -   **Funkce, které byly volány** : všechny funkce, které byly volány konkrétní funkce jsou uvedeny v dolní části zobrazení.  
  
3.  Pokud funkci s názvem `SyncToNavigator` se zobrazí v prostřední části zobrazíte všechny funkce, které volá `SyncToNavigator` funkce se zobrazí v horní části zobrazení a všechny funkce, které byly volány `SyncToNavigator` se zobrazí v dolní části zobrazení.  
  
4.  Funkce ve střední části zobrazení můžete změnit poklepáním na některé z funkcí uvedených v dalších částech dvě zobrazení. Zobrazení se pak aktualizuje tak, aby odrážely změny automaticky.  
  
5.  Data můžete také řadit kliknutím názvy sloupců.  
  
### <a name="select-calltree-view"></a>Vyberte zobrazení stromu volání  
  
1.  Vyberte **zobrazení stromu volání** v **aktuální zobrazení** rozevíracího seznamu. Toto zobrazení je stromové zobrazení provádění programu.  
  
2.  **Zobrazení stromu volání** ukazuje kořen stromu jako název procesu. Funkce jsou uzly stromu. Toto zobrazení můžete přejít k podrobnostem konkrétní volání trasování a analyzovat trasování, které mají největší dopad na výkon. Zobrazení se podobá **zobrazení zásobníku volání** dostupný během ladění. Kromě sloupce v **zobrazení funkce**v **zobrazení stromu volání**, existuje další sloupec, který se zobrazí **název modulu**.  
  
3.  Vyberte **značky** v **aktuální zobrazení** rozevíracího seznamu.  
  
4.  S Profiler SLT jsou značky, které se zobrazí v datovém proudu kolekce s přidružené komentář. Značky jsou místa v kódu, které mají čítače. Pokud dáte Profiler XSLT se získat čítače výkonu XSLT, získat čítače shromažďují pokaždé, když se provede jednu z těchto značek. Data se zobrazí v tabulce obsahující **ID značky**, **název značky** (**spustit Program**, **ukončit Program**) a  **Časové razítko**. Značky se agregují a zobrazují se v chronologickém pořadí v **zobrazení značky** sestavy výkonu.  
  
### <a name="select-modules-in-the-current-view"></a>Vyberte moduly v aktuálním zobrazení  
  
1.  Vyberte **moduly** v **aktuální zobrazení** rozevíracího seznamu.  
  
2.  Zobrazení modulů je plochý seznam všech funkcí, které agregují na úrovni modulu. Rozbalit nebo sbalit název modulu pro zobrazení nebo zobrazení dat výkonu modulu zavřít. Data lze seřadit klepnutím na název sloupce. Ve výchozím nastavení, jsou hodnoty absolutní a procentuální čísla **uplynulý celkový čas**, **uplynulý výhradní čas**, **celkový čas aplikace**, **Výhradní čas aplikace**, a **počet volání**.  
  
3.  Vyberte **procesu** v **aktuální zobrazení** rozevíracího seznamu.  
  
4.  Zobrazení procesů zobrazí tabulku, která zahrnuje **ID procesu**, **název procesu**, **začít čas**a **koncový čas**. Data lze seřadit klepnutím na názvy sloupců.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Používání hierarchie XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)



