---
title: Rychlost odezvy HTML UI | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- performance, JavaScript [Windows Store apps]
- performance tools, JavaScript [Windows Store apps]
- UI Responsiveness Profiler [JavaScript]
- profiler, UI responsiveness [JavaScript]
- profiler, JavaScript [Windows Store apps]
ms.assetid: da13070a-ba40-47dd-a846-ad72eed70d0b
caps.latest.revision: 52
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63027ccfffde0aa3b62bae6c1529826fd9b26c71
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760722"
---
# <a name="html-ui-responsiveness"></a>Rychlost odezvy HTML UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje, jak izolovat problémy s výkonem ve svých aplikacích pomocí Profiler odezvy uživatelského rozhraní, nástroj výkon, který je k dispozici pro aplikace Windows Universal.  
  
 Profiler odezvy uživatelského rozhraní, pomůže vám izolovat problémy, například problémy rychlosti odezvy uživatelského rozhraní nebo platformu vedlejší účinky, které obvykle mohou u těchto příznaků:  
  
-   Nedostatek odezvy v uživatelském rozhraní. Aplikace může být pomalá reakce, pokud vlákno uživatelského rozhraní je blokovaný. Pár věcí, které může zablokovat vlákno uživatelského rozhraní zahrnovat nadměrné synchronního kódu jazyka JavaScript, nadměrné rozložení šablon stylů CSS nebo pracovní výpočtu šablon stylů CSS, synchronní žádosti XHR, uvolňování paměti, nadměrné malířského časy nebo náročné na procesor kódu jazyka JavaScript.  
  
-   Snížit dobu načítání pro aplikaci nebo pro stránku. To je obvykle způsobeno nadměrný čas strávený načítání prostředků.  
  
-   Vizuální aktualizace, které jsou méně časté, než se očekávalo. K tomu dochází, pokud vlákno uživatelského rozhraní je příliš zaneprázdněn a nemůže spravovat smooth snímkovou frekvenci. Například pokud vlákno uživatelského rozhraní je zaneprázdněný, snímků může dojít ke ztrátě. Některá vlákna bez uživatelského rozhraní pracovat, jako jsou síťové požadavky. dekódování obrázku, a barvy může také omezit četnost aktualizace sady visual. (Ne všechny Malování se provádí na vlákně UI).  
  
##  <a name="RunningProfiler"></a> Spusťte nástroj rychlost odezvy uživatelského rozhraní HTML  
 Nástroj rychlost odezvy UI HTML můžete použít, když máte funkční aplikaci Windows Store nebo Windows Universal otevřít v sadě Visual Studio nebo nainstalovat na počítač se systémem Windows 8 nebo novější.  
  
1.  Pokud používáte aplikaci z aplikace Visual Studio na **standardní** nástrojů v **spustit ladění** , zvolte cíl nasazení, například jeden z emulátory Windows Phone **místního počítače** , **Simulátor**, nebo **vzdálený počítač**.  
  
2.  Na **ladění** nabídce zvolte **Profiler výkonu...** .  
  
     Pokud chcete změnit cíl analýzy profileru, zvolte**změnit cíl**.  
  
     ![Změnit cíl analýzy](../profiling/media/js-tools-target.png "JS_Tools_Target")  
  
     Tyto možnosti jsou k dispozici pro cíl analýzy:  
  
    -   **Projekt po spuštění**. Tato možnost slouží k analýze aktuální spouštěcí projekt. Pokud aplikaci spouštíte ve vzdáleném počítači nebo zařízení, musíte použít toto nastavení, což je výchozí hodnota.  
  
    -   **Spuštění aplikace**. Výběrem této možnosti vyberte Windows Store aplikaci ze seznamu spuštěných aplikací. Tuto možnost nelze použít, když aplikaci spouštíte na vzdáleném počítači či zařízení.  
  
         Tuto možnost můžete použít k analýze výkonu aplikace, které jsou spuštěny v počítači, pokud nemáte přístup ke zdrojovému kódu.  
  
    -   **Nainstalované aplikace**. Tato možnost slouží k výběru nainstalované aplikace, kterou chcete analyzovat. Tuto možnost nelze použít, když aplikaci spouštíte na vzdáleném počítači či zařízení.  
  
         Tuto možnost můžete použít k analýze výkonu aplikace, které jste nainstalovali v počítači, pokud nemáte přístup ke zdrojovému kódu. Tato možnost může být také užitečné, chcete-li pouze k analýze výkonu všech aplikací mimo váš vlastní vývoj aplikací.  
  
3.  Z **dostupných nástrojů**vyberte **rychlosti odezvy uživatelského rozhraní HTML**a klikněte na tlačítko **Start**.  
  
4.  Když spustíte Profiler odezvy uživatelského rozhraní, může vyžádat okno Řízení uživatelských účtů ke spuštění Collector.exe trasování událostí pro Windows Visual Studio. Zvolte **Ano**.  
  
     Interakci s aplikací k otestování tohoto scénáře relevantní výkonu. Podrobný postup najdete v části [izolovat problém rychlosti odezvy uživatelského rozhraní](#Workflow) a [izolovat problém vizuální propustnost](#IsolateVisualThroughput).  
  
5.  Přepnout do sady Visual Studio stisknutím klávesy Alt + Tab.  
  
6.  Chcete-li zastavit profilování aplikace a zobrazení data, která shromažďují profiler, zvolte **zastavit shromažďování**.  
  
##  <a name="IsolateAnIssue"></a> Izolovat problém  
 V následujících částech najdete návrhy můžete izolovat problémy s výkonem. Podrobné vysvětlení toho, jak identifikovat a opravit problémy s výkonem pomocí ukázkové aplikace pro testování výkonu najdete v tématu [názorný postup: odezvy zlepšení uživatelského rozhraní (HTML)](../profiling/walkthrough-improving-ui-responsiveness-html.md).  
  
###  <a name="Workflow"></a> Izolovat problém rychlosti odezvy uživatelského rozhraní  
 Tyto kroky obsahují navrhované pracovního postupu, které můžou pomoct efektivněji využívat Profiler odezvy uživatelského rozhraní:  
  
1.  Otevření aplikace v sadě Visual Studio.  
  
2.  Testování aplikací pro problémy rychlosti odezvy uživatelského rozhraní. (Stisknutím kláves Ctrl + F5 aplikaci spustit bez ladění.)  
  
     Pokud narazíte na problém, pokračujte v testování a zkuste zúžit časový rámec, ve kterém se tomuto problému dochází, nebo zkuste k určení aktivačních událostí, které způsobí, že chování.  
  
3.  Přepněte do aplikace Visual Studio (stisknutím klávesy Alt + Tab) a ukončení vaší aplikace (Shift + F5).  
  
4.  Volitelně můžete přidat uživatelské značky pro kódu pomocí [označit kód pro analýzu](#ProfileMark).  
  
    > [!TIP]
    >  Uživatelské značky pomáhají identifikovat problém rychlost odezvy při zobrazení dat profileru. Můžete například přidat uživatelskou značku na začátku a konci části kódu, který je příčinou problém s rychlostí odezvy.  
  
5.  Spusťte Profiler odezvy uživatelského rozhraní podle pokynů uvedených v předchozí části.  
  
6.  Přidejte aplikaci do stavu, která vede problém s rychlostí odezvy uživatelského rozhraní.  
  
7.  Přepněte do aplikace Visual Studio (stisknutím klávesy Alt + Tab) a zvolte **zastavit shromažďování** profiler kartě Profiler odezvy uživatelského rozhraní.  
  
8.  Pokud jste přidali uživatelské značky, se zobrazí v [zobrazit časovou osu relace diagnostiky](#Ruler) profileru. Následující obrázek znázorňuje jeden uživatel označit lze určit konkrétní operace ve vašem kódu.  
  
     ![Zobrazuje uživatelská značka pravítka diagnostiky](../profiling/media/js-htmlvizprofiler-usermark.png "JS_HTMLVizProfiler_UserMark")  
  
9. Identifikujte oblasti zájmu v časové ose a grafy profileru pomocí uživatelské značky, události životního cyklu aplikace nebo data zobrazená v grafu. Tady jsou některé pokyny, které vám usnadní analýzu a použití dat v grafu:  
  
    -   Použití [zobrazit časovou osu relace diagnostiky](#Ruler) zobrazíte [označit kód pro analýzu](#ProfileMark), události životního cyklu aplikací a přidružených časovou osu pro tyto události a časová osa pro data v jiných grafech.  
  
    -   Použití [graf využití procesoru](#CPUutilization) Chcete-li zobrazit obecné informace o aktivity procesoru a na typu práce je zpracování během konkrétního časového období. Období aktivity nadměrnému využití procesoru je větší pravděpodobnost dojít k problémům s rychlost odezvy a vyřadit snímků.  
  
    -   Pokud vytváříte hru nebo bohatý mediální aplikace, použijte [zobrazení vizuální propustnost (FPS)](#VisualThroughput) k identifikaci období čas, ve kterém Snímková frekvence vyřadit.  
  
10. Vyberte oblast zájmu v jednom grafy, kliknutím na část grafu a tažením provést výběr (nebo pomocí klávesy Tab a klávesy se šipkami). Když vyberete časové období tím, že výběr, časová osa grafu podrobnosti v dolním podokně okna profilování se změní na zobrazit jenom vybrané časové období.  
  
     Graf využití procesoru k oblasti zájmu zvýrazněný na následujícím obrázku.  
  
     ![Graf využití procesoru](../profiling/media/js-htmlvizprof-cpu-util.png "JS_HTMLVizProf_CPU_Util")  
  
11. Použití [zobrazit podrobnosti časové osy](#TimelineDetails) a získat podrobné informace o událostech, které se spouští příliš často nebo trvá příliš dlouho pro dokončení. Například vyhledejte následující:  
  
    -   Naslouchacích procesů událostí, časovače a zpětná volání snímků animace. V závislosti na konkrétní události může zahrnovat data poskytnutá ID změněné prvky modelu DOM, název změněné vlastnosti šablon stylů CSS, odkaz na zdrojové umístění a název přidružené události nebo zpětného volání funkce.  
  
    -   Rozložení nebo skriptování události, jejichž výsledkem vykreslování prvků, jako například volání `window.getComputedStyles`. Je k dispozici přidruženého prvku modelu DOM pro událost.  
  
    -   Stránky nebo adresa URL zdroje, které jsou načteny aplikací, jako jsou hodnocení skriptu HTML analýzu událostí. Název souboru nebo prostředku je k dispozici.  
  
    -   Další události podle [události odkaz na Profiler](#ProfilerEvents).  
  
    > [!TIP]
    >  Většina využitelné informace v profileru se zobrazí v grafu podrobnosti časové osy.  
  
12. K oblasti vybraných v využití procesoru nebo grafu vizuální propustnost (FPS), zvolte **přiblížit** (tlačítko nebo místní nabídka) Chcete-li získat podrobnější informace. Časová osa grafu se změny zobrazit jenom vybrané časové období.  
  
13. Při přiblížení, vyberte část využití procesoru nebo vizuální propustnost grafu. Pokud provedete výběr, časová osa grafu podrobnosti v profileru dolní podokno se změní a objeví pouze vybrané časové období.  
  
###  <a name="IsolateVisualThroughput"></a> Izolovat problém vizuální propustnost  
 Období nadměrné využití výkonu procesoru může vést k frekvenci snímků střední nebo nekonzistentní. Pokud vyvíjíte bohatý mediální aplikace a hry, graf vizuální propustnost mohou poskytnout další důležitá data než graf využití procesoru.  
  
 Chcete izolovat problém vizuální propustnost, postupujte podle kroků popsaných v předchozí části, ale použít graf vizuální propustnost jako jeden z klíčových datových bodů.  
  
###  <a name="ProfileMark"></a> Označit kód pro analýzu  
 Snažte se určit části kódu aplikace, který je spojen s daty, která se zobrazí v grafech, můžete přidat volání funkce ve vaší aplikaci, která informuje profiler vložit uživatelská značka – obrácenou trojúhelník – na časové ose v tuto chvíli se provede funkci. Uživatelská značka, které přidáte, zobrazí se na časové ose pro graf využití procesoru a podrobnosti o grafu časová osa grafu vizuální propustnost.  
  
 Chcete-li přidat uživatelskou značku, přidejte následující kód do vaší aplikace. Tento příklad používá "získávání dat" jako popis události.  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("getting data");  
}  
  
```  
  
 Popis události se zobrazí jako popisek při umístění ukazatele myši nad uživatelskou značku. Můžete přidat tolik uživatelské značky, podle potřeby.  
  
> [!NOTE]
>  `console.timeStamp`, příkaz Chrome se rovněž zobrazuje jako značku uživatele.  
  
 Následující obrázek znázorňuje pravítka diagnostiky značkou jednoho uživatele a jeho popis.  
  
 ![Zobrazuje uživatelská značka pravítka diagnostiky](../profiling/media/js-htmlvizprofiler-usermark.png "JS_HTMLVizProfiler_UserMark")  
  
 Události vygenerované nástroje můžete také vytvořit v podrobném zobrazení časové osy a zobrazit doba, po který uplyne mezi dvěma značkami uživatele. Následující kód přidává druhý uživatelskou značku a měření času, který uplyne mezi provádění dva uživatelské značky (předchozí kód ukazuje značku první uživatel).  
  
```javascript  
if (performance.mark && performance.measure) {  
    performance.mark("data retrieved");  
    performance.measure("data measure", "getting data", "data retrieved");  
}  
```  
  
 Pokud není zadán druhý uživatelskou značku, `performance.measure` používá časové razítko jako druhý uživatelskou značku. První uživatelská značka je povinný.  
  
 Měření doby trvání se zobrazí jako **uživatelské míry** zobrazení podrobností události na časové ose a jsou uvedeny podrobné informace při výběru.  
  
 ![Zobrazení podrobností události míru uživatele na časové ose](../profiling/media/js-htmlvizprofiler-user-measure.png "JS_HTMLVizProfiler_User_Measure")  
  
##  <a name="AnalyzeData"></a> Analýza dat  
 Následující části obsahují informace, které pomáhají interpretovat data, která se zobrazí v profileru.  
  
###  <a name="Ruler"></a> Zobrazit časovou osu relace diagnostiky  
 Pravítko v horní části okna profilování ukazuje časovou osu profilovaných informací. Tato časová osa platí pro graf využití procesoru a vizuální propustnost grafu.  
  
 Tady je vypadá časová osa diagnostiky se popisek zobrazí několik události životního cyklu aplikace:  
  
 ![Relace diagnostiky pravítka](../profiling/media/js-htmlvizprof-ruler.png "JS_HTMLVizProf_Ruler")  
  
 Ukazuje časové osy, pokud dojde k události lifecyle aplikace, jako je aktivační událost, a zobrazí značky uživatelů (uživatele označit trojúhelníky), který můžete přidat do vašeho kódu. Můžete vybrat události, které chcete zobrazit popisy tlačítek s dalšími informacemi. Další informace o uživatelské značky, naleznete v tématu [označit kód pro analýzu](#ProfileMark) v tomto tématu.  
  
 Události životního cyklu aplikace se zobrazí jako kosočtverce symboly. Toto jsou události modelu DOM, které zahrnují následující:  
  
-   `DOMContentLoaded` a `Load` události, ke kterým obvykle dochází v obslužné rutině aktivované události ve vašem kódu. Popis pro událost zobrazuje určité události a adresu URL.  
  
-   Událost navigace, která nastane, pokud přejdete na jinou stránku. Popisek pro událost ukazuje na cílovou adresu URL stránky.  
  
###  <a name="CPUUtilization"></a> Zobrazení procesoru využití  
 Graf využití procesoru umožňuje určit dobu, ve kterém se aktivity nadměrnému využití procesoru. Poskytuje informace o průměr spotřeby procesoru aplikaci po určitou dobu. Informace, které jsou rozlišené představují následující konkrétní kategorie: **načítání**, **skriptování**, uvolňování paměti (**GC**), **stylu**, **Vykreslování**, a **dekódování obrázku**. Další informace o těchto kategorií naleznete v tématu [události odkaz na Profiler](#ProfilerEvents) dále v tomto tématu.  
  
 Graf využití procesoru ukazuje množství čas strávený na všech vláknech aplikace kombinování hodnoty využití procesoru pro jeden nebo více procesorů do jednoho procentuální hodnotu. Hodnota využití procesoru může překročit 100 % jeho obsahu, když se používá více než jeden procesor.  
  
> [!NOTE]
>  Využití GPU se nezobrazují v grafu.  
  
 Tento příklad ukazuje, jak vypadá graf využití procesoru:  
  
 ![Graf využití procesoru](../profiling/media/js-htmlvizprof-cpu-util.png "JS_HTMLVizProf_CPU_Util")  
  
 Pomocí tohoto grafu pro:  
  
- Určete obecné oblastí zájmu.  
  
- Zvolte konkrétní časové období pro zobrazení v grafu podrobnosti časové osy. Vyberte časové období, vyberte část grafu a přetažením ukazatele chcete provést výběr.  
  
- Získejte podrobnější přehled o vybrané časové období výběrem **přiblížit** tlačítko.  
  
  Další informace o používání grafu najdete v tématu [izolovat problém rychlosti odezvy uživatelského rozhraní](#Workflow) v tomto tématu.  
  
###  <a name="VisualThroughput"></a> Zobrazení vizuální propustnost (FPS)  
 Vizuální propustnost graf umožňuje určit dobu, ve kterém Snímková frekvence vyřadit. Zobrazuje počet snímků za sekundu (FPS) pro aplikaci. Tento graf je nejužitečnější pro vývoj her a bohatý mediální aplikace.  
  
 Zobrazená hodnota snímků za Sekundu může lišit od skutečné Snímková frekvence. Mějte tyto informace při zkoumání dat v tomto grafu:  
  
- Graf ukazuje snímků za Sekundu, že aplikace bude schopné dosáhnout v konkrétním okamžiku. Při nečinnosti aplikaci, snímků za Sekundu je stejný jako obnovovací frekvence monitorování.  
  
- Graf zobrazuje skutečné snímků za Sekundu, pokud aplikace pracuje, který vyžaduje aktualizace sady visual.  
  
- Graf zobrazuje hodnota nula, pokud rámce jsou vyřazována.  
  
  Tento příklad ukazuje, jak vypadá graf vizuální propustnost:  
  
  ![Vizuální propustnost grafu](../profiling/media/js-htmlvizprof-vizthru.png "JS_HTMLVizProf_VizThru")  
  
  Použití rozhraní graph vizuální propustnost na:  
  
- Určete obecné oblastí zájmu.  
  
- Zvolte konkrétní časové období pro zobrazení v grafu podrobnosti časové osy. Vyberte časové období, vyberte část grafu a přetažením ukazatele chcete provést výběr.  
  
- Získejte podrobnější přehled o vybrané časové období výběrem **přiblížit** tlačítko.  
  
###  <a name="TimelineDetails"></a> Podrobnosti zobrazení časové osy  
 Časová osa grafu podrobností se zobrazí v dolním podokně Profiler odezvy uživatelského rozhraní. Poskytuje sekvenční a hierarchické informace o událostech, které spotřebovávají nejvíce času procesoru během vybraných časových období. Tento graf vám pomohou určit, co vyvolalo určité události a pro některé události, jak mapy událostí zpět ke zdrojovému kódu. Tento graf také vám pomůže určit čas potřebný k vykreslení vizuální aktualizace na obrazovce.  
  
 Graf zobrazuje pracovní vlákno uživatelského rozhraní a práce na pozadí podprocesů, které může přispět ke zpomalení aktualizace sady visual. Grafu nezobrazí JavaScript JIT práce, asynchronní práce GPU, prováděné mimo hostitelského procesu (jako je například RuntimeBroker.exe a dwm.exe pracovní) nebo práce pro oblasti modulu Windows Runtime, které ještě nebyly byla instrumentována pro profilaci (například vstupně-výstupních operací disku).  
  
> [!TIP]
>  Při výskytu události na vlákně na pozadí, zobrazí se v závorkách vedle názvu události ID vlákna.  
  
 Tento příklad ukazuje, jaké na časové ose grafu podrobností vypadá po kliknutí na naslouchací proces událostí pro modelu DOM událost vybrat:  
  
 ![Časová osa grafu podrobnosti](../profiling/media/js-htmlvizprof-timelinedet.png "JS_HTMLVizProf_TimelineDet")  
  
 Na tomto obrázku **spinAction** obslužné rutině událostí ve **název události** sloupec je odkaz, pokud je vybráno, přejdete k obslužné rutině událostí ve zdrojovém kódu. V pravém podokně klikněte **funkce zpětného volání** vlastnost poskytuje stejným propojením ke zdrojovému kódu. Další vlastnosti, také poskytují informace o události, jako je například přidruženého prvku modelu DOM.  
  
 Pokud vyberete část časové osy pro využití výkonu procesoru a vizuální propustnost (FPS) grafu, podrobnosti o grafu časová osa zobrazuje detailní informace pro vybrané časové období.  
  
 Události v časové osy grafu podrobnosti jsou rozlišené představují stejné kategorie práce, které jsou uvedeny v graf využití procesoru. Další informace o určité události a kategorie událostí, naleznete v tématu [události odkaz na Profiler](#ProfilerEvents) v tomto tématu.  
  
 Pomocí časové osy grafu podrobnosti:  
  
-   Zobrazit v zobrazení časové osy a mřížky přibližné spuštění, dobu trvání a koncový čas pro událost. Podrobnosti o grafu časová osa můžete zobrazit období od 30 milisekund do 30 sekund v mřížkovém zobrazení, v závislosti na stavu přiblížení. Pro hodnoty typu duration:  
  
    -   Inkluzivní časy představují dobu trvání události, včetně podřízených prvků události. V zobrazení mřížky tato hodnota se zobrazí první.  
  
    -   Výhradní čas představují dobu trvání události bez zahrnutí podřízené položky události. V zobrazení mřížky tato hodnota se zobrazí v závorkách.  
  
-   Rozbalte události v hierarchii k zobrazení podřízených prvků události. Podřízené objekty událostí jsou ostatní události, které jsou generovány události nadřazené. Události modelu DOM může mít například naslouchacích procesů událostí, které se zobrazují jako podřízené objekty. Naslouchací proces událostí může mít jiné události, které vznikají, jako je rozložení události.  
  
-   Řazení událostí ve start time (výchozí) nebo dobu trvání. Použití **řadit** seznam a vyberte metodu řazení.  
  
-   Zobrazit podrobnosti pro každou jednotlivou událost v podokně podrobností (pravé podokno). Vlastnosti se liší v závislosti na konkrétní události, jak ukazují tyto příklady:  
  
    -   Časovače, naslouchacích procesů událostí (události modelu DOM) a zpětná volání snímků animace **funkce zpětného volání** vlastnost obsahuje odkaz na umístění zdrojového kódu spolu s názvem události obslužné rutiny nebo zpětného volání funkce.  
  
    -   Pro časovače, naslouchacích procesů událostí (události modelu DOM), rozložení události a zpětná volání snímků animace, joinkind barevně souhrn vybrané události a všechny její podřízené **souhrn celkové doby** oddílu (barevně okruhu). Každou barevně řezu obrázku představuje typ události. Popisy tlačítek zadejte název typu události.  
  
    > [!TIP]
    >  Podrobnosti o grafu časové osy a **souhrn celkové doby** může pomoct najít pro optimalizaci. Pokud některý z těchto zobrazení zobrazuje velký počet malých úlohy, události může být Release candidate pro optimalizaci. Například aplikace může být aktualizace elementů modelu DOM často, což vede k velkým počtem rozložení a analýza událostí HTML. Je možné optimalizovat výkon tím, že tuto práci do dávek.  
  
###  <a name="FilterTimelineDetails"></a> Filtrovat podrobnosti časové osy  
 Zobrazení podrobnosti časové osy na určitou událost můžete filtrovat výběrem **filtru na události** z místní nabídky pro určité události. Když vyberete tuto možnost, mají rozsah zobrazení časové osy a mřížky pro zvolenou událost. Výběr v graf využití procesoru, také obory na konkrétní události.  
  
 ![Filtrování časové osy s událostí](../profiling/media/js-htmlvizprofiler-filtertoevent.png "JS_HTMLVizProfiler_FilterToEvent")  
  
###  <a name="FilterEvents"></a> Umožňuje filtrovat události  
 Můžete filtrovat některé události z časové osy grafu podrobnosti ke snížení šumu v datech, nebo chcete-li odstranit data, která nejsou zajímavé pro váš scénář výkonu. Můžete filtrovat podle názvu události nebo trvání události, nebo konkrétní filtry, které jsou zde popsané.  
  
 Pokud chcete vyfiltrovat dekódování obrázku, spekulativní stahování a události uvolňování paměti, zrušte **aktivitu na pozadí** možnost na ikonu filtru v dolním podokně. Vzhledem k tomu, že tyto události nejsou velmi užitečné, že jsou ve výchozím nastavení skryje.  
  
 ![Filtrování událostí na časové ose](../profiling/media/js-htmlvizprofiler-event-filter.png "JS_HTMLVizProfiler_Event_Filter")  
  
 Pokud chcete vyfiltrovat události požadavku protokolu HTTP, zrušte **přenos v síti** možnost na ikonu filtru v dolním podokně. Ve výchozím nastavení tyto události jsou uvedeny v grafu podrobnosti časové osy.  
  
 Chcete-li filtrovat aktivity vlákno uživatelského rozhraní, zrušte **aktivita uživatelského rozhraní** možnost.  
  
> [!TIP]
>  Zrušte zaškrtnutí tohoto políčka a vyberte možnost provoz sítě k prozkoumání problémů souvisejících s latencí sítě.  
  
 Pokud chcete vyfiltrovat uživatelské míry, zrušte **uživatelské míry** možnost. Uživatelské míry jsou události nejvyšší úrovně s žádné podřízené položky.  
  
###  <a name="GroupFrames"></a> Skupiny událostí podle rámce  
 Můžete seskupit události, které se zobrazují v podrobném zobrazení časové osy pro jednotlivé snímky. Tyto události snímků jsou události vygenerované nástroj a představují kontejnery události nejvyšší úrovně pro všechny pracovní vlákno uživatelského rozhraní, nacházející se mezi událostmi Malování. Chcete-li povolit toto zobrazení, vyberte **Seskupit události nejvyšší úrovně podle rámců**.  
  
 ![Seskupit události nejvyšší úrovně podle rámce](../profiling/media/js-htmlvizprofiler-frame-grouping-button.png "JS_HTMLVizProfiler_Frame_Grouping_Button")  
  
 Při seskupování událostí podle rámce události nejvyšší úrovně v podrobnostech časová osa zobrazení jednotlivých představují rámce.  
  
 ![Časová osa událostí seskupených podle rámce](../profiling/media/js-htmlvizprofiler-frame-grouping.png "JS_HTMLVizProfiler_Frame_Grouping")  
  
##  <a name="SaveSession"></a> Uložit diagnostické relace  
 V sadě Visual Studio můžete uložit diagnostické relace při uzavření kartu, která je přidružená k relaci. Později můžete znovu otevřít uložených relací.  
  
##  <a name="ProfilerEvents"></a> Profiler události – přehled  
 Profiler události jsou zařazené do kategorií a barevné označení v Profiler odezvy uživatelského rozhraní. Toto jsou kategorie události:  
  
- **Načítání.** Označuje dobu strávenou načítání prostředků aplikací a parsování HTML a CSS, při prvním načtení aplikace. To může být zahrnuté síťové žádosti.  
  
- **Skriptování.** Označuje čas strávený parsování a spuštění JavaScriptu. To zahrnuje události modelu DOM, časovače, vyhodnocení skriptů a pracovní snímků animace. Obsahuje uživatelský kód a kód knihovny.  
  
- **GC.** Zobrazuje čas strávený při uvolňování paměti.  
  
- **Práce se styly.** Označuje čas strávený analýzou šablon stylů CSS a výpočtu prezentace a rozložení elementů.  
  
- **Vykreslování.** Označuje čas strávený vykreslováním obrazovky.  
  
- **Dekódování obrázku.** Označuje dobu strávenou dekomprimací a dekódováním obrázků.  
  
  Profiler odezvy uživatelského rozhraní pro používání stylů pro kategorie a skript zadat data, která se dají dále rozvíjet v grafu podrobnosti časové osy. Pokud jako problém identifikovat problémy skriptování, můžete spustit profiler vzorkování procesoru s Profiler odezvy uživatelského rozhraní. Alternativně můžete použít funkci profileru sady Visual Studio získat podrobnější údaje. Další informace najdete v tématu [data analyzovat časování funkcí jazyka JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b).  
  
  Pro další kategorie událostí je možné identifikovat platformy vedlejší účinky, které jsou výsledkem přidání funkce do vaší aplikace, ale v těchto případech nemusí být schopni vyřešit problémy s konkrétní výkonem s použitím Profiler odezvy uživatelského rozhraní.  
  
  Tato tabulka zobrazuje události a jejich popis:  
  
|Událost|Kategorie události|Nastane, když|  
|-----------|--------------------|-----------------|  
|Analýza CSS|Načítání|Nový obsah CSS byl nalezen a byl učiněn pokus analyzovat obsah šablony stylů CSS.|  
|Analýza HTML|Načítání|Byl nalezen nový obsah HTML a analyzovat obsah do uzlů a vložit obsah do stromové struktuře modelu DOM byl proveden pokus o.|  
|Požadavek HTTP|Načítání|V modelu DOM byl nalezen vzdálený prostředek nebo se vytvořil objekt XMLHttpRequest, jejímž výsledkem požadavku HTTP.|  
|Spekulativní stahování|Načítání|Obsah HTML stránky se hledá požadované prostředky tak, aby následné žádosti HTTP pro prostředky, které mohou být naplánovány rychle.|  
|Funkce zpětného volání snímku animace|Skriptování|Můru prohlížeče k vykreslení jiný rámec a to aktivuje funkce poskytované aplikací zpětného volání.|  
|Události modelu DOM|Skriptování|Události modelu DOM došlo k chybě a byl spuštěn.<br /><br /> `context` Vlastnost pro události modelu DOM, jako například `DOMContentLoaded` nebo `click`, je uveden v závorkách.|  
|Naslouchací proces událostí|Skriptování|Naslouchací proces událostí byl vyvolávány a spuštěny.|  
|Naslouchací proces dotazů na média|Skriptování|Registrovaný dotaz na média byla zrušena, což vedlo k provedení jeho přidružených naslouchacích procesů.|  
|Objekt mutation observer|Skriptování|Jeden nebo více zjištěno, že DOM se změnil, což vedlo ke spuštění přidružené zpětné volání MutationObserver.|  
|Vyhodnocení skriptu|Skriptování|Nový element SCRIPT byl nalezen v modelu DOM a byl proveden pokus o analýzu a spusťte tento skript.|  
|Časovač|Skriptování|Naplánované časovače vypršel, a to vedlo k provedení jeho přidružené zpětné volání funkce.|  
|Funkce zpětného volání pro asynchronní modulu Windows Runtime|Skriptování|Asynchronní operace, která aktivuje `Promise` objekt prostředí Windows Runtime dokončil funkce zpětného volání.|  
|Událost prostředí Windows Runtime|Skriptování|Událost, která na objekt prostředí Windows Runtime došlo k aktivaci zaregistrovaný naslouchací proces.|  
|Uvolnění paměti|Uvolňování paměti|Byl stráven čas shromažďování paměti pro objekty, které již byly použity.|  
|Výpočet šablon stylů CSS|Práce se styly|Byly provedeny změny v modelu DOM, který vyžaduje všech ovlivněných elementů proto bylo nutné přepočítat vlastnosti stylu.|  
|Rozložení|Práce se styly|Byly provedeny změny v modelu DOM, které vyžadovaly velikost nebo pozice všech ovlivněných elementů proto bylo nutné přepočítat.|  
|Malování|vykreslování|V modelu DOM byly provedeny vizuální změny a byl proveden pokus o opětovné vykreslování části stránky.|  
|Vykreslit vrstvu|vykreslování|Byly provedeny vizuální změny nezávisle vykreslovaného fragmentu modelu DOM (označovaného jako vrstva) a změny potřebné část stránky k vykreslení.|  
|Dekódování obrázku|Dekódování obrázku|Image byla zahrnuta v modelu DOM a byl proveden pokus o pro dekompresi a dekódování obrázku z původního formátu na rastrový obrázek.|  
|Rámec|Není k dispozici|Byly provedeny vizuální změny v modelu DOM, který stránky, které vyžadovaly překreslení všech ovlivněných částí. Toto je nástroj vygeneruje událost pro seskupení.|  
|Uživatelské míry|Není k dispozici|Scénáři specifické pro aplikaci byl měřen pomocí metody `performance.measure` metody. Toto je událost vygenerována nástroj použít pro analýzu kódu.|  
  
##  <a name="Tips"></a> Další informace  
  
-   Sledování [toto video](http://channel9.msdn.com/Events/Build/2013/3-316) z konference Build 2013 o Profiler odezvy uživatelského rozhraní.  
  
-   Přečtěte si tipy ke zvýšení výkonu pro aplikace Windows Store, které jsou vytvořené pro Windows pomocí jazyka JavaScript. Další informace najdete v tématu [osvědčené postupy z hlediska výkonu pro aplikace Windows Store využívající jazyk JavaScript](http://msdn.microsoft.com/library/windows/apps/hh465194.aspx).  
  
-   Informace o modelu provádění kódu s jedním vláknem a výkonu najdete v tématu [provádění kódu](http://msdn.microsoft.com/library/windows/apps/hh781217.aspx).  
  
## <a name="see-also"></a>Viz také  
 [Analýza výkonu aplikace](http://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)



