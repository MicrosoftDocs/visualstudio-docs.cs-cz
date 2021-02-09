---
title: Zobrazení vláken v Vizualizátor souběžnosti | Microsoft Docs
description: Seznamte se s tím, že v zobrazení vláken můžete určit, která vlákna spouští kód během spouštěcího segmentu.
ms.date: 11/04/2018
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 77655e2e040b6a14a5c82151dac451e8373ea674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876976"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Zobrazení vláken v Vizualizátor souběžnosti

Zobrazení **vlákna** je nejpodrobnější zobrazení a funkce s bohatou funkcí v Vizualizátor souběžnosti. V zobrazení **vláken** můžete určit, která vlákna spouští kód během spouštěcího segmentu, a analyzovat, zda jsou vlákna spouštěna nebo blokována z důvodu synchronizace, vstupně-výstupních operací nebo z jiných důvodů. V sestavách zobrazení **vlákna** je také možné profilovat volání – spuštění stromu zásobníku a odblokování vláken.

I když jsou vlákna spuštěná, Vizualizér souběžnosti shromažďuje ukázky. Když vlákno zastavilo zpracování, Vizualizér prověřuje všechny události kontextového přepínače operačního systému pro vlákno. Přepínače kontextu mohou nastat z těchto důvodů:

- Vlákno je blokováno v rámci synchronizačního primitiva.
- Doba platnosti vlákna vyprší.
- Vlákno provádí blokující požadavek na vstupně-výstupní operace.

Vizualizátor souběžnosti zařadí vlákna a události kontextového přepínače a vyhledá v zásobníku volání vláken pro známá blokující rozhraní API. Zobrazuje kategorie vláken v aktivní legendě vlevo dole v zobrazení **vláken** . Ve většině případů můžete identifikovat hlavní příčinu blokující události zkoumáním zásobníků volání, které odpovídají událostem kontextu přepínače.

Pokud se neshoduje zásobník volání, Vizualizér souběžnosti použije důvod čekání, který poskytuje [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] . [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]Kategorie ale může být založená na podrobnostech implementace a nemusí odrážet záměr uživatele. Například [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] hlásí důvod čekání pro blokování na nativním zámku funkce Slim Reader jako vstup/výstup namísto synchronizace.

Zobrazení **vlákna** také zobrazuje závislosti mezi vlákny. Například pokud identifikujete vlákno blokované na objektu synchronizace, můžete najít vlákno, které ho odblokoval. Můžete kontrolovat zásobník volání pro odblokování vlákna v okamžiku, kdy odblokuje druhý.

Zobrazení **vláken** můžete použít k těmto akcím:

- Identifikujte důvody, proč uživatelské rozhraní (UI) aplikace nereaguje během určitých fází provádění.
- Určete množství času stráveného blokováním při synchronizaci, vstupně-výstupních chyb stránek a dalších událostí.
- Zjištění míry rušení z jiných procesů, které jsou spuštěny v systému.
- Identifikujte problémy s vyrovnáváním zatížení pro paralelní spuštění.
- Vyhledá důvody pro optimální nebo neexistující škálovatelnost. Například proč výkon paralelní aplikace není lepší, pokud jsou k dispozici více logických jader.
- Pochopení stupně souběžnosti v aplikaci, aby bylo možné lépe rozumělost.
- Identifikujte závislosti mezi pracovními vlákny a kritickými cestami provádění.

## <a name="use-threads-view"></a>Použít zobrazení vláken

Chcete-li spustit Vizualizér souběžnosti, vyberte možnost **analyzovat**  >  **Vizualizátor souběžnosti** a pak vyberte některou z možností, jako je například **spuštění nového procesu**.

Vizualizátor souběžnosti spustí aplikaci a shromáždí trasování, dokud nevyberete **Zastavit shromažďování**. Vizualizér potom analyzuje trasování a zobrazí výsledky na stránce sestavy trasování.

Kliknutím na kartu **vlákna** vlevo nahoře v sestavě otevřete zobrazení **vlákna** .

![Zobrazení vláken](../profiling/media/threadsviewnarrowing.png "zobrazení vláken")

Vyberte časové intervaly a vlákna pro spuštění analýzy výkonu.

## <a name="timeline-analysis"></a>Analýza časové osy

Horní část zobrazení **vláken** je časová osa. Časová osa zobrazuje aktivitu všech vláken v procesu a všechna zařízení fyzických disků v hostitelském počítači. Zobrazuje také události GPU a aktivity značek.

Na časové ose osa x je čas a na ose y je několik kanálů:

- Dva vstupně-výstupní kanály pro každou diskovou jednotku v systému, jeden kanál pro čtení a jeden pro zápis.
- Kanál pro každé vlákno v procesu.
- Kanály značek, pokud se v trasování nacházejí události značek. Kanály značek se zpočátku zobrazí pod kanály vláken, které tyto události vygenerovaly.
- Kanály GPU.

Zpočátku jsou vlákna seřazena v pořadí, ve kterém jsou vytvořena, takže hlavní vlákno aplikace je nejprve. Vyberte jinou možnost v rozevíracím seznamu **Řadit podle** a seřaďte vlákna podle jiného kritéria, například **provedení**.

Barvy časové osy označují stav vlákna v daném čase. Zelené segmenty jsou spouštěny, pro synchronizaci jsou blokovány červené segmenty, žluté segmenty jsou přerušeny a fialové segmenty jsou zapojeny do vstupně-výstupních operací zařízení.

Přiblížením můžete zobrazit další podrobnosti nebo oddálení a zobrazit delší časový interval. Vyberte segmenty a body v grafu, abyste získali podrobnosti o kategoriích, časech zahájení, zpoždění a stavu zásobníku volání.

Použijte časovou osu k prohlédnutí mezi vlákny, které jsou zapojeny do paralelní smyčky, nebo v souběžných úlohách. Pokud dokončení jednoho vlákna trvá déle než ostatní, je možné, že je tato práce nevyvážená. Můžete zvýšit výkon aplikace tím, že rozdistribuujete práci více než do vláken.

Pokud se v určitém časovém okamžiku spouští jenom jedno vlákno, aplikace nemusí plně využít výhod souběžnosti v systému. Pomocí grafu časové osy můžete prozkoumávat závislosti mezi vlákny a dočasné vztahy mezi blokujícími a blokovanými vlákny. Chcete-li změnit uspořádání vláken, vyberte vlákno a pak na panelu nástrojů vyberte ikonu nahoru nebo dolů.

Můžete skrýt vlákna, která nedělají práci nebo jsou zcela zablokovaná, protože jejich statistiky nejsou důležité a mohou CLOG sestavy. Skryjte vlákna tak, že vyberete jejich názvy a pak vyberete **Skrýt vybraná vlákna** nebo **Skrýt vše kromě vybraných ikon vláken** na panelu nástrojů. Chcete-li identifikovat vlákna, která mají být skryta, vyberte odkaz na **souhrnný podproces** v levém dolním rohu. Vlákna, která nemají žádnou aktivitu, můžete skrýt v grafu **souhrnu jednotlivých vláken** .

### <a name="thread-execution-details"></a>Podrobnosti spuštění vlákna
Chcete-li získat podrobnější informace o segmentu spuštění, vyberte bod na zeleném segmentu časové osy. Vizualizér souběžnosti zobrazuje černý blikající kurzor nad vybraným bodem a zobrazuje jeho zásobník volání na **aktuální** kartě v dolním podokně. V segmentu spuštění můžete vybrat více bodů.

>[!NOTE]
>Vizualizátor souběžnosti nemusí být schopný vyřešit výběr v segmentu spuštění, pokud je doba trvání segmentu menší než 1 milisekunda.

Chcete-li získat profil spuštění pro všechna neskrytá vlákna v aktuálně vybraném časovém rozsahu, vyberte možnost **spuštění** v legendě vlevo dole.

### <a name="thread-blocking-details"></a>Podrobnosti o blokování vláken
Chcete-li získat informace o konkrétní oblasti ve vlákně, umístěte ukazatel myši na tuto oblast na časové ose a zobrazte tak popis. Popis obsahuje informace, jako je kategorie, čas zahájení a zpoždění. Vyberte oblast, ve které se má **v daném okamžiku** v dolním podokně Zobrazit zásobník volání. Podokno také ukazuje kategorii, zpoždění a blokující rozhraní API, pokud existuje, a odblokuje vlákno, pokud je nějaký. Prozkoumáním zásobníku volání můžete určit základní důvody pro události blokující vlákny.

Cesta spuštění může obsahovat několik blokujících událostí. Pokud je chcete prostudovat blokováním kategorie a hledáním problematických oblastí rychleji, vyberte kategorii blokování v legendě vlevo.

### <a name="dependencies-between-threads"></a>Závislosti mezi vlákny
Vizualizátor souběžnosti zobrazuje závislosti mezi vlákny, takže můžete určit, co se zablokované vlákno snažilo a jaké má jiné vlákno povoleno.

Chcete-li určit, které vlákno odblokuje jiné vlákno, vyberte blokující segment na časové ose. Pokud Vizualizér souběžnosti může určit vlákno odblokování, nakreslí čáru mezi podprocesem odblokování a zpracovávaným segmentem, který následuje po blokujícím segmentu. Vyberte kartu **Zásobník odblokování** v dolním podokně, abyste viděli příslušný zásobník volání.

## <a name="profile-reports"></a>Sestavy profilů
Pod grafem časová osa je podokno se **sestavou sestavy profilu**, **aktuální** a **odblokování** karet sestavy zásobníku. Sestavy se automaticky aktualizují, když změníte časovou osu a výběry vláken. V případě rozsáhlých trasování může být podokno sestavy během výpočtu aktualizací dočasně nedostupné.

### <a name="profile-report-tab"></a>Karta sestava profilu

**Sestava profilu** má dva filtry:

- Chcete-li odfiltrovat položky stromu volání, kde bylo málo času stráveno, zadejte hodnotu filtru v rozsahu 0 až 99 procent v poli **snížení šumu na hodnotě** . Výchozí hodnota je 2%.
- Chcete-li zobrazit stromy volání pouze pro váš kód, zaškrtněte políčko **pouze můj kód** . Chcete-li zobrazit všechny stromy volání, zrušte zaškrtnutí políčka.

Karta **Sestava profilu** zobrazuje sestavy pro kategorie a odkazy v legendě. Chcete-li zobrazit sestavu, vyberte jednu z položek vlevo:

- **Provádění** Sestava **spuštění** zobrazuje rozpis času stráveného prováděním aplikace.

  Chcete-li najít řádek kódu, v němž je doba provádění vyčerpána, rozbalte strom volání a v místní nabídce položky stromu volání vyberte možnost **Zobrazit zdroj** nebo **Zobrazit weby volání**. **Zdroj zobrazení** vyhledá spouštěný řádek kódu. **Zobrazení lokality volání** vyhledá řádek kódu, který se nazývá spuštěný řádek. Pokud existuje pouze jeden řádek webu volání, je zvýrazněn jeho kód. Pokud existuje několik webů volání, vyberte požadovanou položku v dialogovém okně a pak vyberte **Přejít ke zdroji**. Je často užitečné najít web volání, který má nejvíce instancí, nejvíce času nebo obojího. Další informace najdete v tématu [Sestava profilu spuštění](../profiling/execution-profile-report.md).

- **Synchronizace** Zpráva o **synchronizaci** zobrazuje volání, která jsou zodpovědná za bloky synchronizace, spolu s celkovými dobami blokování každého zásobníku volání. Další informace najdete v tématu [čas synchronizace](../profiling/synchronization-time.md).

- **I/O** Sestava **i/o** zobrazuje volání, která jsou zodpovědná za vstupně-výstupní bloky, spolu s celkovými dobami blokování každého zásobníku volání. Další informace naleznete v části [vstupně-výstupní čas (zobrazení vláken)](../profiling/i-o-time-threads-view.md).

- **Režim spánku** Sestava **režimu spánku** zobrazuje volání, která jsou zodpovědná za bloky režimu spánku, spolu s celkovými dobami blokování každého zásobníku volání. Další informace najdete v tématu [Doba spánku](../profiling/sleep-time.md).

- **Správa paměti** Sestava **správy paměti** zobrazuje volání, kde došlo k blokům správy paměti, spolu s celkovými dobami blokování každého zásobníku volání. Tyto informace slouží k identifikaci oblastí, které mají nadměrné problémy stránkování nebo uvolňování paměti.  Další informace najdete v tématu [čas správy paměti](../profiling/memory-management-time.md).

- **Přerušení** Sestava **přerušení** ukazuje, kde procesy v systému zrušily aktuální proces, a jednotlivá vlákna, která nahradila vlákna v aktuálním procesu. Tyto informace můžete použít k identifikaci procesů a vláken, která jsou nejvíc zodpovědná za přerušení. Další informace najdete v tématu [čas přerušení](../profiling/preemption-time.md).

- **Zpracování uživatelského rozhraní** Sestava **zpracování uživatelského rozhraní** zobrazuje volání, která jsou zodpovědná za bloky zpracování uživatelského rozhraní, spolu s celkovými dobami blokování každého zásobníku volání. Další informace najdete v tématu [Doba zpracování uživatelského rozhraní](../profiling/ui-processing-time.md).

- **Souhrn podle vláken** Výběrem **souhrnu na jeden podproces** zobrazíte graf zobrazující stav vláken pro aktuálně vybraný časový interval. Barevně kódované sloupce zobrazují celkový čas každého vlákna stráveného v běhu, blokovaném, vstupně-výstupních a dalších stavech. Vlákna jsou označena v dolní části. Když upravíte úroveň přiblížení v grafu časové osy, tento graf se automaticky aktualizuje.

  V některých úrovních přiblížení nemusí být některá vlákna v grafu zobrazená. V takovém případě se zobrazí tři tečky (**...**) vpravo. Pokud se požadované vlákno nezobrazí, můžete skrýt další vlákna. Další informace naleznete v tématu [Souhrnná sestava jednotlivých vláken](../profiling/per-thread-summary-report.md).

- **Diskové operace** Vyberte **operace disku** , aby se zobrazily procesy a vlákna zapojená do vstupně-výstupních operací disku pro aktuální proces, soubory, které se dotkly (například knihovny DLL, které načetly), počet čtených bajtů a další informace. Tuto sestavu můžete použít k vyhodnocení času stráveného přístupu k souborům během provádění, zejména v případě, že se váš proces jeví jako vázané na vstupně-výstupní operace. Další informace najdete v tématu [Sestava diskových operací](../profiling/disk-operations-report-threads-view.md).

### <a name="current-tab"></a>Aktuální karta
Tato karta zobrazuje zásobník volání pro vybraný bod na segmentu vlákna v grafu časové osy. Zásobníky volání jsou oříznuty, aby se zobrazila pouze aktivita, která souvisí s vaší aplikací.

### <a name="unblocking-stack-tab"></a>Odblokování karty zásobníku
Tato karta zobrazuje, které vlákno odblokuje vybrané vlákno, a zásobník volání odblokování.

## <a name="see-also"></a>Viz také
- [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)
