---
title: Výkon XSLT
description: Přečtěte si o profileru XSLT v aplikaci Visual Studio, který vytváří podrobné sestavy výkonu XSLT, které vám pomůžou optimalizovat výkon kódu XSLT.
ms.custom: SEO-VS-2020
ms.date: 11/11/2020
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: f2214ab4d66dcad1ee92eda7d7acbb94b89e8eb6
ms.sourcegitcommit: 83a39d48b00c6c351e5c1707942633b7f73aaad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2020
ms.locfileid: "94531885"
---
# <a name="the-xslt-profiler"></a>Profiler XSLT

Profiler XSLT vytvoří podrobné sestavy výkonu XSLT, které vám pomůžou měřit, vyhodnocovat a cílit na problémy související s výkonem v kódu XSLT. Profiler XSLT obsahuje užitečné rady pro optimalizace stylů XSL a XSLT. Pro aplikace XSLT, které vyžadují maximální výkon, může být tento nástroj nezbytný.

Profiler XSLT je součástí sady Visual Studio a je k dispozici v nabídce **XML** .

![Profiler XSLT](../xml-tools/media/profile-xslt-menu.png "Snímek obrazovky s položkami nabídky XML v aplikaci Visual Studio 2017")

> [!NOTE]
> Profiler XSLT je k dispozici pouze v edici Enterprise sady Visual Studio 2017.

## <a name="create-a-performance-report"></a>Vytvoření sestavy výkonu

1. Otevřete dokument XSLT v aplikaci Visual Studio 2017.

2. Na panelu nabídek vyberte **XML**  >  **profil XSLT**.

3. Zadejte vstupní dokument XML. Pokud dokument XML již není otevřen, budete vyzváni k zadání souboru.

   Spustí se analýza a indikátor průběhu zobrazí průběh v editoru. Výstup XSLT je také viditelný.

4. Po ukončení relace výkonu si Projděte sestavu výkon a analyzujte výkon XSLT.

## <a name="get-all-available-views"></a>Získat všechna dostupná zobrazení

1. Kliknutím na rozevírací seznam **aktuální zobrazení** zobrazíte všechna dostupná zobrazení.

2. V rozevíracím seznamu **aktuální zobrazení** vyberte možnost **souhrnné zobrazení** . Ve výchozím nastavení se sestava o výkonu zobrazuje v **souhrnném zobrazení**. Toto zobrazení je počátečním bodem pro určení potíží s výkonem s dokumenty XSLT. **Souhrnné zobrazení** obsahuje následující datové body:

   - Nejvíce volané funkce

   - Funkce s největší individuální prací

   - Funkce, které přebírají nejdelší čas spuštění

   Ve výchozím nastavení jsou pro každý datový bod tři sloupce: název funkce, počet volání v absolutní hodnotě a procentuální hodnota pojmenované funkce pro celkové volání funkcí. Z každého datového bodu v **souhrnném zobrazení** můžete přejít k podrobnějším zobrazením kliknutím pravým tlačítkem na datové body funkce.

3. V rozevíracím seznamu **aktuální zobrazení** vyberte možnost **zobrazení funkce** . **Funkce** zobrazuje seznam funkcí volaných během profilace. Data můžete seřadit kliknutím na název sloupce. Ve výchozím nastavení jsou zobrazené sloupce:

    - **Název funkce**

    - **Uplynulý celkový čas**

    - **Uplynulý výhradní čas**

    - **Celková doba aplikace**

    - **Výhradní čas aplikace**

    - **Number of Calls**

   Všechny sloupce s časem jsou zobrazeny v absolutních hodnotách i v procentech. Termín **Exclusive** odkazuje na celkovou dobu, kterou funkce strávila vykonání, bez času stráveného jinými funkcemi, které jsou volány během provádění této funkce.

   Termín **včetně** odkazuje na celkovou dobu, kterou funkce strávila, včetně doby provádění všech funkcí, které volaly, a toho, zda kterákoli z těchto funkcí volala jiné funkce.

## <a name="select-callercallee-view"></a>Vybrat zobrazení volající/volaný

V rozevíracím seznamu **aktuální zobrazení** vyberte zobrazení **volající/volaný** . Zobrazení **volající/volaný** má následující tři samostatné části:

- **Funkce, které jsou volány** : všechny funkce, které se nazývají konkrétní funkce, jsou uvedeny v horní části zobrazení.

- **Aktuální funkce** : konkrétní funkce, která byla volána, je uvedena v prostřední části zobrazení.

- **Funkce, které byly volány** : všechny funkce, které byly volány určitou funkcí, jsou uvedeny v dolní části zobrazení.

Pokud je funkce s názvem `SyncToNavigator` zobrazena v prostřední části zobrazení, všechny funkce, které se nazývají funkce, `SyncToNavigator` se zobrazí v horní části zobrazení a všechny funkce, které byly volány, `SyncToNavigator` se zobrazí v dolní části zobrazení.

- Funkci v prostřední části zobrazení můžete změnit dvojitým kliknutím na kteroukoli z funkcí uvedených v dalších dvou částech zobrazení. Zobrazení se pak aktualizuje, aby se změny projevily automaticky.

- Data můžete také seřadit kliknutím na názvy sloupců.

## <a name="select-call-tree-view"></a>Vybrat zobrazení stromu volání

- V rozevíracím seznamu **aktuální zobrazení** vyberte **zobrazení stromu volání** . Toto zobrazení je stromovým zobrazením provádění programu.

   **Zobrazení stromu volání** ukazuje kořen stromu jako název procesu. Funkce jsou uzly stromu. Toto zobrazení umožňuje přejít k podrobnostem o specifických trasováních volání a analyzovat, která trasování mají největší dopad na výkon. Zobrazení je podobné **zobrazení zásobníku volání** , které je k dispozici během ladění. Kromě sloupců v **zobrazení funkce** je ve **stromovém zobrazení volání** k dispozici další sloupec pro zobrazení **názvu modulu**.

- V rozevíracím seznamu **aktuální zobrazení** vyberte možnost **značky** .

   V profileru XSLT jsou značky, které se zobrazí v datovém proudu shromažďování dat s přidruženým komentářem. Značky jsou místo v kódu, který má čítače. Když oznámíte profileru XSLT shromažďování čítačů výkonu XSLT, čítače se shromažďují při každém spuštění některého z těchto značek. Data se zobrazí v tabulce, která obsahuje **ID značky** , **označení názvu** ( **spouštěcí program** , **koncový program** ) a **časové razítko**. Značky nejsou agregované a zobrazují se v chronologickém pořadí v **zobrazení značek** sestavy výkonu.

## <a name="select-modules-in-the-current-view"></a>Vybrat moduly v aktuálním zobrazení

- V rozevíracím seznamu **aktuální zobrazení** vyberte **moduly** .

   Zobrazení modulů je plochý seznam všech funkcí agregovaných na úroveň modulu. Rozbalte nebo sbalte název modulu pro zobrazení nebo zavření zobrazení dat výkonu modulu. Data můžete seřadit kliknutím na název sloupce. Ve výchozím nastavení jsou k dispozici jak absolutní hodnoty, tak procentuální čísla pro **uplynulý celkový čas** , **uplynulý výhradní čas** , **Application zahrnující čas** , **výhradní čas aplikace** a **Počet volání**.

- V rozevíracím seznamu **aktuální zobrazení** vyberte **proces** .

   V zobrazení procesu se zobrazí tabulka, která obsahuje **ID procesu** , **název procesu** , **čas zahájení** a **čas ukončení**. Data je možné seřadit kliknutím na názvy sloupců.

## <a name="see-also"></a>Viz také:

- [Návod: použití hierarchie XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
