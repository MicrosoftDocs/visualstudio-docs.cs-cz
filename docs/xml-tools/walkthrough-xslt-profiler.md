---
title: 'Návod: Profiler XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14abf52e65a796325d4af8bd95f5434c105c3fa3
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693796"
---
# <a name="walkthrough-xslt-profiler"></a>Návod: Profiler XSLT

Profileru XSLT vytvoří podrobné sestavy XSLT výkonu, které pomáhají měr, hodnocení a cíle problémy související s výkonem v kódu XSLT. Profileru XSLT zahrnuje užitečné pomocné parametry pro XSL a XSLT optimalizace na list stylu. Pro aplikace XSLT této vyžádání maximální výkon, tento nástroj může být nezbytné.

## <a name="prerequisites"></a>Požadavky

Postupy v následující návod vyžadují Visual Studio a rozhraní .NET Framework verze 4.0 nebo novější.

### <a name="create-the-performance-report"></a>Vytvoření sestavy výkon

1.  Otevřete dokument XSLT v sadě Visual Studio.

2.  Klikněte na **profil XSLT** možnost, která je k dispozici v nabídce XML.

3.  Zadejte vstupní dokument XML. Pokud dokument XML ještě není otevřené, zobrazí se výzva k souboru.

4.  Analýza se spustí, a zobrazí se průběh v editoru indikátor průběhu.

5.  Výstup XSLT je zobrazen v podokně výstup.

6.  Po skončení výkonnostní relace, zkontrolujte Sestava výkonu. Data uložená v sestavě výkonu umožňuje zobrazit a analyzovat výkon XSLT.

### <a name="get-all-the-available-views"></a>Získání všech dostupných zobrazení

1.  Klikněte na **aktuální zobrazení** rozevíracího seznamu zobrazíte všechna zobrazení k dispozici.

2.  Vyberte **zobrazení souhrnu** možnost **aktuální zobrazení** rozevíracího seznamu. Ve výchozím nastavení je sestava výkonu zobrazí v **zobrazení souhrnu**. Toto zobrazení je výchozí bod pro určení problémy s výkonem s dokumenty XSLT. **Zobrazení souhrnu** uvádí těchto datových bodů:

    -   Většina volaných funkcí

    -   Funkce s nejvíce jednotlivé pracovní

    -   Funkce nejdelší doba k provedení

3.  Ve výchozím nastavení, existují tři sloupce pro každý datový bod: název funkce, počet volání v absolutní hodnota a procentuální hodnoty funkci s názvem na celkový funkce volání. Z každého datového bodu v **zobrazení souhrnu**, můžete přejít na podrobnější zobrazení kliknutím pravým tlačítkem na základě funkce datových bodů.

4.  Vyberte **funkce – zobrazení** možnost **aktuální zobrazení** rozevíracího seznamu. **Funkce – zobrazení** obsahuje seznam funkcí, volá se během vytváření profilů. Data můžete seřadit kliknutím na název sloupce. Sloupce zobrazené ve výchozím nastavení jsou:

    -   **Název funkce**

    -   **Uplynulý čas (včetně).**

    -   **Uplynulá doba výhradní**

    -   **Doba aplikace (včetně).**

    -   **Výhradní doba aplikace**

    -   **Počet volání**

5.  Absolutní hodnoty a procenta jsou zobrazeny všechny sloupce čas. Termín **výhradní** odkazuje na celkový čas strávený provádění bez ohledu na času stráveného jiných funkcí volaná během provádění této funkce funkce.

6.  Termín **vnitřní** odkazuje na celkovou dobu funkci potřebná k provedení, včetně čas provádění všech funkcí, se nazývá a jestli některý z těchto volat funkce s názvem dalších funkcí.

### <a name="select-callercallee-view"></a>Vyberte volající/volaný – zobrazení

1.  Vyberte **volající/volaný** zobrazit v **aktuální zobrazení** rozevíracího seznamu.

2.  **Volající/volaný** zobrazení má následující tři samostatné části:

    -   **Funkce, které volá**: všechny funkce, které volá konkrétní funkce jsou uvedeny v horní část zobrazení.

    -   **Funkci Current**: určitou funkci, která byla volána, je uvedena ve střední část zobrazení.

    -   **Funkce, které byly volány** : všechny funkce, které byly volány konkrétní funkce jsou uvedeny v dolní části zobrazení.

3.  Pokud funkci s názvem `SyncToNavigator` se zobrazí v zobrazení všechny funkce, které volá střední část `SyncToNavigator` funkce se zobrazí v horní část zobrazení a všechny funkce, které byly volány `SyncToNavigator` se zobrazí v dolní části zobrazení.

4.  Funkce pro střední část zobrazení můžete změnit dvojitým kliknutím na soubor funkce uvedené v další dvě části tohoto zobrazení. Zobrazení je pak aktualizovat tak, aby odrážely změny automaticky.

5.  Data můžete také řadit podle klikejte na názvy sloupců.

### <a name="select-call-tree-view"></a>Vyberte zobrazení stromu volání

1.  Vyberte **zobrazení stromu volání** v **aktuální zobrazení** rozevíracího seznamu. Toto zobrazení je stromové zobrazení spuštění programu.

2.  **Zobrazení stromu volání** ukazuje kořenu stromu jako název procesu. Funkce se uzly stromu. Toto zobrazení můžete rozbalit konkrétní volání trasování a analyzovat, které trasování mít největší vliv výkon. Zobrazení je podobná **zobrazení zásobník volání** dostupné během ladění. Kromě sloupce v **funkce – zobrazení**v **zobrazení stromu volání**, je další sloupec, který se zobrazí **název modulu**.

3.  Vyberte **značky** v **aktuální zobrazení** rozevíracího seznamu.

4.  Profileru SLT jsou značky, které se zobrazí v datovém proudu kolekce s přidružené komentář. Značky jsou místa v kódu, které mají čítače. Když se zjistit XSLT profileru ke shromažďování čítačů výkonu XSLT, získat čítače shromažďují pokaždé, když získá provést jednu z těchto značek. Data se zobrazí v tabulce obsahující **ID značky**, **název značky** (**spustit Program**, **End Program**) a  **Časové razítko**. Značky ve nejsou agregovány a v chronologickém pořadí v se zobrazují **značky zobrazení** výkonu sestavy.

### <a name="select-modules-in-the-current-view"></a>Vybrat modul v aktuálním zobrazení

1.  Vyberte **moduly** v **aktuální zobrazení** rozevíracího seznamu.

2.  Zobrazení modulů je plochý seznam všech funkcí agregován na úroveň modulu. Rozbalit nebo sbalit na název modulu k zobrazení nebo zobrazení dat výkonu modulu zavřít. Data můžete seřadit kliknutím na název sloupce. Ve výchozím nastavení, jsou absolutní hodnoty a procento čísla pro **uplynulý čas včetně**, **uplynulý čas výhradní**, **aplikace včetně čas**, **Výhradní doba aplikace**, a **počet volání**.

3.  Vyberte **proces** v **aktuální zobrazení** rozevíracího seznamu.

4.  Zobrazení procesů zobrazí tabulku, která zahrnuje **ID procesu**, **název procesu**, **čas zahájení**a **koncový čas**. Data lze seřadit kliknutím na názvy sloupců.

## <a name="see-also"></a>Viz také:

- [Návod: Použití hierarchie XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)