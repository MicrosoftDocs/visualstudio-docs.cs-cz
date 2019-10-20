---
title: 'Návod: Profiler XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7ee6665aea98edf7cb701f5fdfe07d293887bac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669529"
---
# <a name="walkthrough-xslt-profiler"></a>Návod: Profiler XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profiler XSLT vytvoří podrobné sestavy výkonu XSLT, které vám pomůžou měřit, vyhodnocovat a cílit na problémy související s výkonem v kódu XSLT. Profiler XSLT obsahuje užitečné rady pro optimalizace stylů XSL a XSLT. Pro aplikace XSLT, které vyžadují maximální výkon, může být tento nástroj nezbytný.

## <a name="prerequisites"></a>Požadavky
 Postupy v následujícím návodu vyžadují Visual Studio 2010 and.NET Framework verze 4,0. Profiler XSLT je k dispozici pouze v případě, že je v systému Microsoft Visual Studio tým nainstalován Nástroje pro profilaci.

### <a name="create-the-performance-report"></a>Vytvoření sestavy výkonu

1. Otevřete dokument XSLT v aplikaci Visual Studio.

2. Klikněte na možnost **profil XSLT** , která je k dispozici v nabídce XML.

3. Zadejte vstupní dokument XML. Pokud dokument XML již není otevřen, budete vyzváni k zadání souboru.

4. Spustí se analýza a indikátor průběhu zobrazí průběh v editoru.

5. Výstup XSLT je viditelný v podokně výstup.

6. Po ukončení relace výkonu si prohlédněte sestavu výkon. Data uložená v sestavě o výkonu umožňují zobrazit a analyzovat výkon XSLT.

### <a name="get-all-the-available-views"></a>Získat všechna dostupná zobrazení

1. Kliknutím na rozevírací seznam **aktuální zobrazení** zobrazíte všechna dostupná zobrazení.

2. V rozevíracím seznamu **aktuální zobrazení** vyberte možnost **souhrnné zobrazení** . Ve výchozím nastavení se sestava o výkonu zobrazuje v **souhrnném zobrazení**. Toto zobrazení je počátečním bodem pro určení potíží s výkonem s dokumenty XSLT. **Souhrnné zobrazení** obsahuje následující datové body:

    - Nejvíce volané funkce

    - Funkce s největší individuální prací

    - Funkce, které přebírají nejdelší čas spuštění

3. Ve výchozím nastavení jsou pro každý datový bod tři sloupce: název funkce, počet volání v absolutní hodnotě a procentuální hodnota pojmenované funkce pro celkové volání funkcí. Z každého datového bodu v **souhrnném zobrazení**můžete přejít k podrobnějším zobrazením kliknutím pravým tlačítkem na datové body funkce.

4. V rozevíracím seznamu **aktuální zobrazení** vyberte možnost **zobrazení funkce** . **Funkce** zobrazuje seznam funkcí volaných během profilace. Data můžete seřadit kliknutím na název sloupce. Ve výchozím nastavení jsou zobrazené sloupce:

    - **Název funkce**

    - **Uplynulý celkový čas**

    - **Uplynulý výhradní čas**

    - **Celková doba aplikace**

    - **Výhradní čas aplikace**

    - **Počet volání**

5. Všechny sloupce s časem jsou zobrazeny v absolutních hodnotách i v procentech. Termín **Exclusive** odkazuje na celkovou dobu, kterou funkce strávila vykonání, bez času stráveného jinými funkcemi, které jsou volány během provádění této funkce.

6. Termín **včetně** odkazuje na celkovou dobu, kterou funkce strávila, včetně doby provádění všech funkcí, které volaly, a toho, zda kterákoli z těchto funkcí volala jiné funkce.

### <a name="select-callercallee-view"></a>Vybrat zobrazení volající/volaný

1. V rozevíracím seznamu **aktuální zobrazení** vyberte zobrazení **volající/volaný** .

2. Zobrazení **volající/volaný** má následující tři samostatné části:

    - **Funkce, které jsou volány**: všechny funkce, které se nazývají konkrétní funkce, jsou uvedeny v horní části zobrazení.

    - **Aktuální funkce**: konkrétní funkce, která byla volána, je uvedena v prostřední části zobrazení.

    - **Funkce, které byly volány** : všechny funkce, které byly volány určitou funkcí, jsou uvedeny v dolní části zobrazení.

3. Pokud se funkce s názvem `SyncToNavigator` zobrazí v prostřední části zobrazení, zobrazí se v horní části zobrazení všechny funkce označované jako funkce `SyncToNavigator` a všechny funkce, které byly volány `SyncToNavigator`, se zobrazí v dolní části zobrazení.

4. Funkci v prostřední části zobrazení můžete změnit dvojitým kliknutím na kteroukoli z funkcí uvedených v dalších dvou částech zobrazení. Zobrazení se pak aktualizuje, aby se změny projevily automaticky.

5. Data můžete také seřadit kliknutím na názvy sloupců.

### <a name="select-calltree-view"></a>Vybrat zobrazení stromu volání

1. V rozevíracím seznamu **aktuální zobrazení** vyberte **zobrazení stromu volání** . Toto zobrazení je stromovým zobrazením provádění programu.

2. **Zobrazení stromu volání** ukazuje kořen stromu jako název procesu. Funkce jsou uzly stromu. Toto zobrazení umožňuje přejít k podrobnostem o specifických trasováních volání a analyzovat, která trasování mají největší dopad na výkon. Zobrazení je podobné **zobrazení zásobníku volání** , které je k dispozici během ladění. Kromě sloupců v **zobrazení funkce**je ve **stromovém zobrazení volání**k dispozici další sloupec pro zobrazení **názvu modulu**.

3. V rozevíracím seznamu **aktuální zobrazení** vyberte možnost **značky** .

4. V profileru SLT jsou značky, které se zobrazí v datovém proudu shromažďování dat s přidruženým komentářem. Značky jsou místo v kódu, který má čítače. Když oznámíte profileru XSLT shromažďování čítačů výkonu XSLT, čítače se shromažďují při každém spuštění některého z těchto značek. Data se zobrazí v tabulce, která obsahuje **ID značky**, **označení názvu** (**spouštěcí program**, **koncový program**) a **časové razítko**. Značky nejsou agregované a zobrazují se v chronologickém pořadí v **zobrazení značek** sestavy výkonu.

### <a name="select-modules-in-the-current-view"></a>Vybrat moduly v aktuálním zobrazení

1. V rozevíracím seznamu **aktuální zobrazení** vyberte **moduly** .

2. Zobrazení modulů je plochý seznam všech funkcí agregovaných na úroveň modulu. Rozbalte nebo sbalte název modulu pro zobrazení nebo zavření zobrazení dat výkonu modulu. Data můžete seřadit kliknutím na název sloupce. Ve výchozím nastavení jsou k dispozici jak absolutní hodnoty, tak procentuální čísla pro **uplynulý celkový čas**, **uplynulý výhradní čas**, **Application zahrnující čas**, **výhradní čas aplikace**a **Počet volání**.

3. V rozevíracím seznamu **aktuální zobrazení** vyberte **proces** .

4. V zobrazení procesu se zobrazí tabulka, která obsahuje **ID procesu**, **název procesu**, **čas zahájení**a **čas ukončení**. Data je možné seřadit kliknutím na názvy sloupců.

## <a name="see-also"></a>Viz také
 [Návod: Používání hierarchie XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
