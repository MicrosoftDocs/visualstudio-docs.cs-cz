---
title: Analýza odezvy uživatelského rozhraní HTML v aplikacích UPW | Dokumenty společnosti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- JavaScript
helpviewer_keywords:
- performance, JavaScript [UWP apps]
- performance tools, JavaScript [UWP apps]
- UI Responsiveness Profiler [JavaScript]
- profiler, UI responsiveness [JavaScript]
- profiler, JavaScript [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: a483d1382ea1f67c14aa4674016331bfe0f76e7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189371"
---
# <a name="analyze-html-ui-responsiveness-in-universal-windows-apps"></a>Analýza odezvy uživatelského rozhraní HTML v univerzálních aplikacích pro Windows
Toto téma popisuje, jak izolovat problémy s výkonem v aplikacích pomocí profileru odezvy uživatelského rozhraní, což je nástroj pro výkon, který je k dispozici pro univerzální aplikace pro Windows Apps.

 Profiler odezvy uživatelského rozhraní vám může pomoci izolovat problémy, jako jsou problémy s odezvou uživatelského rozhraní nebo vedlejší účinky platformy, které se obvykle vyskytují s těmito příznaky:

- Nedostatečná odezva v uživatelském rozhraní. Aplikace může být pomalé reagovat, pokud vlákno uživatelského rozhraní je stále blokován. Některé věci, které mohou blokovat vlákno uživatelského rozhraní, zahrnují nadměrný synchronní kód JavaScript, nadměrné rozložení CSS nebo výpočet CSS, synchronní požadavky XHR, uvolňování odpadků, nadměrné časy malování nebo kód JavaScript unavovaný procesorem.

- Pomalá doba načítání aplikace nebo stránky. To je obvykle způsobeno nadměrným časem stráveným načítáním prostředků.

- Vizuální aktualizace, které jsou méně časté, než bylo očekáváno. K tomu dochází, pokud je vlákno uživatelského rozhraní příliš zaneprázdněno, aby udrželo hladký kmitočet snímků. Pokud je například vlákno uživatelského rozhraní zaneprázdněno, mohou být rámce vynechány. Některé jiné vlákno mimo uživatelské rozhraní, jako jsou síťové požadavky, dekódování obrázků a malby, mohou také omezit frekvenci vizuálních aktualizací. (Ne všechny malování se provádí ve vlákně uživatelského rozhraní.)

## <a name="run-the-html-ui-responsiveness-tool"></a>Spuštění nástroje odezvy uživatelského rozhraní HTML
 Nástroj odezvy uživatelského rozhraní HTML můžete použít, když máte v sadě Visual Studio otevřenou funkční aplikaci UPW.

1. Pokud aplikaci spouštěte z Visual Studia, vyberte na panelu nástrojů **Standard** v seznamu **Spustit ladění** cíl nasazení, například **Místní počítač** nebo **Zařízení**.

2. V nabídce **Ladění** zvolte **Performance Profiler**.

     Pokud chcete změnit cíl analýzy pro profiler, zvolte **Změnit cíl**.

     ![Cíl analýzy změn](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Pro cíl analýzy jsou k dispozici následující možnosti:

    - **Spuštění projektu**. Tuto možnost zvolte, chcete-li analyzovat aktuální projekt spuštění. Pokud aplikaci spouštěte na vzdáleném počítači nebo zařízení, musíte použít toto nastavení, což je výchozí hodnota.

    - **Spuštění aplikace**. Tuto možnost vyberte, chcete-li vybrat aplikaci UPW ze seznamu spuštěných aplikací. Tuto možnost nelze použít, pokud aplikaci spouštěte na vzdáleném počítači nebo zařízení.

         Tuto možnost můžete použít k analýze výkonu aplikací spuštěných v počítači, když nemáte přístup ke zdrojovému kódu.

    - **Nainstalovaná aplikace**. Tuto možnost vyberte nainstalovanou aplikaci, kterou chcete analyzovat. Tuto možnost nelze použít, pokud aplikaci spouštěte na vzdáleném počítači nebo zařízení.

         Tuto možnost můžete použít k analýze výkonu aplikací nainstalovaných v počítači, když nemáte přístup ke zdrojovému kódu. Tato možnost může být užitečná také v případě, že chcete analyzovat výkon libovolné aplikace mimo vývoj vlastní aplikace.

3. V **možnostech Dostupné nástroje**vyberte možnost **Odezva uživatelského rozhraní HTML**a pak zvolte **Start**.

4. Při spuštění profileru odezvy uživatelského rozhraní může okno Řízení uživatelských účtů požadovat vaše oprávnění ke spuštění souboru Visual Studio ETW Collector.exe. Zvolte **Ano**.

     Interakci s aplikací otestujte relevantní scénář výkonu. Podrobný pracovní postup naleznete v [tématu Izolovat problém s odezvou uživatelského rozhraní](#Workflow) a [izolovat problém vizuální propustnosti](#IsolateVisualThroughput).

5. Přepněte do sady Visual Studio stisknutím kláves Alt+Tab.

6. Chcete-li zastavit profilování aplikace a zobrazit data, která shromáždil profiler, zvolte **Zastavit shromažďování**.

## <a name="isolate-an-issue"></a>Izolujte problém
 V následující části jsou uvedeny návrhy, které vám pomohou izolovat problémy s výkonem. Podrobné vysvětlení, jak identifikovat a opravit problémy s výkonem pomocí ukázkové aplikace pro testování výkonu, [najdete v návodu: Zlepšení odezvy uživatelského rozhraní (HTML).](html-ui-responsiveness.md)

### <a name="isolate-a-ui-responsiveness-problem"></a><a name="Workflow"></a>Izolujte problém s odezvou uživatelského rozhraní
 Tyto kroky poskytují navrhovaný pracovní postup, který vám může pomoci efektivněji používat profiler odezvy uživatelského rozhraní:

1. Otevřete aplikaci ve Visual Studiu.

2. Otestujte aplikaci kvůli problémům s odezvou uživatelského rozhraní. (Stisknutím **klávesy Ctrl**+**F5** spusťte aplikaci bez ladění.)

     Pokud zjistíte problém, pokračujte v testování a pokuste se zúžit časový rámec, ve kterém k problému dochází, nebo se pokuste identifikovat aktivační události, které způsobují chování.

3. Přepněte do Visual Studia (stiskněte **klávesu Alt**+**Tab)** a zastavte aplikaci **(Shift**+**F5).**

4. Volitelně můžete do kódu přidat uživatelské značky pomocí [kódu Mark pro analýzu](#ProfileMark).

    > [!TIP]
    > Uživatelské značky vám mohou pomoci identifikovat problém s odezvou při prohlížení dat profileru. Můžete například přidat značku uživatele na začátku a na konci části kódu, která způsobuje problém s odezvou.

5. Spusťte profiler odezvy uživatelského rozhraní podle pokynů v předchozí části.

6. Uveďte aplikaci do stavu, který má za následek problém s odezvou uživatelského rozhraní.

7. Přepněte do sady Visual Studio (stiskněte alt+tab) a na kartě profileru profileru profileru zvolte **Zastavit kolekci.**

8. Pokud jste přidali uživatelské značky, zobrazí se v [časové ose Zobrazit diagnostickou relaci](#Ruler) profileru. Následující obrázek znázorňuje značku jednoho uživatele, která slouží k určení určité operace v kódu.

     ![Pravítko diagnostiky zobrazující značku uživatele](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")

9. Identifikujte oblast zájmu v časové ose a grafech profileru pomocí uživatelských značek, událostí životního cyklu aplikace nebo dat viditelných v grafech. Zde jsou některé pokyny, které vám pomohou analyzovat a používat data v grafech:

    - Pomocí [zobrazení časové osy diagnostické relace](#Ruler) můžete zobrazit [kód Označení pro analýzu](#ProfileMark), události životního cyklu aplikace a přidruženou časovou osu pro tyto události a časovou osu pro data v ostatních grafech.

    - Graf [využití procesoru](#CPUUtilization) slouží k zobrazení obecných informací o aktivitě procesoru a typu práce, kterou zpracovává během určitého časového období. Období nadměrné aktivity procesoru s větší pravděpodobností za následek problémy s odezvou a vynechání rámců.

    - Pokud vyvíjíte hru nebo aplikaci rich media, použijte [vizuální propustnost zobrazení (FPS)](#VisualThroughput) k identifikaci časových období, ve kterých snímková frekvence klesla.

10. Vyberte oblast zájmu v jednom z grafů klepnutím na část grafu a přetažením ukazatele pro výběr (nebo pomocí kláves y Tab a kláves se šipkami). Když vyberete časové období provedením výběru, graf podrobností časové osy v dolním podokně profileru se změní tak, aby zobrazoval pouze vybrané časové období.

     Následující obrázek znázorňuje graf využití procesoru se zvýrazněnou oblastí zájmu.

     ![Graf využití procesoru](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")

11. Pomocí [podrobností o časové ose zobrazení](#TimelineDetails) získáte podrobné informace o událostech, které jsou spuštěny příliš často nebo jejich dokončení trvá příliš dlouho. Podívejte se například na následující:

    - Posluchače událostí, časovače a zpětná volání snímků animace. V závislosti na konkrétní události mohou poskytnutá data zahrnovat ID modifikovaných prvků DOM, název modifikovaných vlastností CSS, odkaz na zdrojové umístění a název přidružené události nebo funkce zpětného volání.

    - Události rozložení nebo skriptování, které vedly k `window.getComputedStyles`vykreslování prvků, jako jsou například volání . Přidružený prvek DOM pro událost je k dispozici.

    - Stránky nebo prostředky adresy URL načtené aplikací, například vyhodnocení skriptů pro události analýzy HTML. Je k dispozici název souboru nebo prostředek.

    - Další události zadané v [odkazu na událost Profiler](#profiler-event-reference).

    > [!TIP]
    > Většina použitelných informací v profileru se zobrazí v grafu podrobností časové osy.

12. Pokud je v grafu využití procesoru nebo vizuální propustnost (FPS) vybraná oblast, zvolte **Přiblížit** (tlačítko nebo kontextovou nabídku), abyste získali podrobnější informace. Časová osa grafu se změní tak, aby zobrazovala pouze vybrané časové období.

13. Při přiblížení vyberte část grafu využití procesoru nebo vizuální propustnost. Když provedete výběr, graf podrobností časové osy v dolním podokně profileru se změní tak, aby zobrazoval pouze vybrané časové období.

### <a name="isolate-a-visual-throughput-problem"></a><a name="IsolateVisualThroughput"></a>Izoluje problém s vizuální propustností
 Období nadměrného využití procesoru může mít za následek nízké nebo nekonzistentní snímkové frekvence. Pokud vyvíjíte bohaté mediální aplikace a hry, graf vizuální propustnosti může poskytovat důležitější data než graf využití procesoru.

 Chcete-li izolovat problém s propustností vizuálu, postupujte podle kroků popsaných v předchozí části, ale jako jeden z klíčových datových bodů použijte graf vizuální propustnost.

### <a name="mark-code-for-analysis"></a><a name="ProfileMark"></a>Označit kód pro analýzu
 Chcete-li izolovat část kódu aplikace, která je přidružená k datům, která se zobrazí v grafech, můžete do aplikace přidat volání funkce, které instruktuje profileru, aby v častimeline vložil značku uživatele – obrácený trojúhelník – v okamžiku, kdy se funkce spustí. Každá přidaná značka uživatele se zobrazí na časové ose pro graf využití procesoru, graf vizuální propustnosti a graf podrobností časové osy.

 Chcete-li přidat značku uživatele, přidejte do aplikace následující kód. Tento příklad používá "získávání dat" jako popis události.

```javascript
if (performance && performance.mark) {
    performance.mark("getting data");
}

```

 Popis události se zobrazí jako popis, když položíte ukazatel myši na značku uživatele. Můžete přidat tolik uživatelských značek, kolik potřebujete.

> [!NOTE]
> `console.timeStamp`, příkaz Chromu, se také zobrazí jako značka uživatele.

 Následující obrázek znázorňuje pravítko diagnostiky se značkou jednoho uživatele a jeho popis.

 ![Pravítko diagnostiky zobrazující značku uživatele](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")

 Můžete také vytvořit události generované nástrojem v zobrazení podrobností časové osy a zobrazit tak dobu, která uplyne mezi dvěma uživatelskými značkami. Následující kód přidá druhou značku uživatele a měření času, který uplyne mezi spuštěním dvou uživatelských značek (předchozí kód zobrazuje první značku uživatele).

```javascript
if (performance.mark && performance.measure) {
    performance.mark("data retrieved");
    performance.measure("data measure", "getting data", "data retrieved");
}
```

 Pokud není zadána druhá značka `performance.measure` uživatele, použije časové razítko jako druhou značku uživatele. Je vyžadována první značka uživatele.

 Měření doby trvání se zobrazí jako událost **měření uživatele** v zobrazení podrobností časové osy a při výběru zobrazí podrobné informace.

 ![Událost měření uživatele v zobrazení podrobností časové osy](../profiling/media/js_htmlvizprofiler_user_measure.png "JS_HTMLVizProfiler_User_Measure")

## <a name="analyze-data"></a>Analýza dat
 Následující části poskytují informace, které pomáhají interpretovat data, která se zobrazí v profileru.

### <a name="view-the-diagnostic-session-timeline"></a><a name="Ruler"></a>Zobrazení časové osy diagnostické relace
 Pravítko v horní části profileru zobrazuje časovou osu profilovaných informací. Tato časová osa platí pro graf využití procesoru i pro graf vizuální propustnosti.

 Tady je, jak vypadá časová osa diagnostické relace s popisem pro několik událostí životního cyklu aplikace:

 ![Pravítko diagnostické relace](../profiling/media/js_htmlvizprof_ruler.png "JS_HTMLVizProf_Ruler")

 Časová osa zobrazuje, kdy dojde k událostem životního cyklu aplikace, jako je událost aktivace, a zobrazuje uživatelské značky (trojúhelníky uživatelských značek), které můžete přidat do kódu. Můžete vybrat události, které chcete zobrazit popisky s dalšími informacemi. Další informace o uživatelských značkách najdete v [tématu Označení kódu pro analýzu](#ProfileMark) v tomto tématu.

 Události životního cyklu aplikace se zobrazují jako diamantové symboly. Jedná se o události DOM, které zahrnují následující:

- `DOMContentLoaded`a `Load` události, které se obvykle vyskytují v obslužné rutině aktivované události ve vašem kódu. Popis pro událost zobrazuje konkrétní událost a adresu URL.

- Navigační událost, ke které dochází při přechodu na jinou stránku. Popispro událost zobrazuje adresu URL cílové stránky.

### <a name="view-cpu-utilization"></a><a name="CPUUtilization"></a>Zobrazit využití procesoru
 Graf využití procesoru umožňuje identifikovat období, ve kterých je nadměrná aktivita procesoru. Poskytuje informace o průměrné spotřebě procesoru aplikace za určité časové období. Informace jsou barevně odlišeny tak, aby představovaly následující konkrétní kategorie: **Načítání**, **Skriptování**, uvolňování paměti (**GC**), **Styling**, **Vykreslování**a **Dekódování obrazu**. Další informace o těchto kategoriích najdete v [tématu Odkaz na událost Profiler](#profiler-event-reference) dále v tomto tématu.

 Graf využití procesoru zobrazuje množství času stráveného ve všech vláknech aplikace a kombinuje hodnoty využití procesoru pro jeden nebo více procesorů do hodnoty jednoho procenta. Hodnota využití procesoru může překročit 100 procent, pokud je používán více než jeden procesor.

> [!NOTE]
> Využití GPU se v grafu nezobrazuje.

 Tento příklad ukazuje, jak vypadá graf využití procesoru:

 ![Graf využití procesoru](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")

 Tento graf slouží k:

- Identifikujte obecné oblasti zájmu.

- Zvolte konkrétní časové období, které se má zobrazit v grafu podrobností časové osy. Chcete-li zvolit časové období, vyberte část grafu a tažením ukazatele proveďte výběr.

- Zvolte tlačítko **Přiblížit** si podrobnější zobrazení vybraného časového období.

  Další informace o používání grafu najdete v [tématu Izolovat problém odezvy uživatelského rozhraní](#Workflow) v tomto tématu.

### <a name="view-visual-throughput-fps"></a><a name="VisualThroughput"></a>Zobrazení vizuální propustnost (FPS)
 Graf vizuální propustnosti umožňuje identifikovat časové úseky, ve kterých kmitočet snímků klesl. Zobrazuje snímky za sekundu (FPS) pro aplikaci. Tento graf je nejužitečnější pro vývoj her a multimediálních aplikací.

 Zobrazená hodnota FPS se může lišit od skutečného kmitočetu snímků. Při zkoumání dat v tomto grafu mějte na paměti tyto informace:

- Graf ukazuje FPS, že aplikace je schopna dosáhnout v určitém čase. Když je aplikace nečinná, FPS je stejný jako obnovovací frekvence monitoru.

- Graf zobrazuje skutečné FPS, pokud aplikace dělá práci, která vyžaduje vizuální aktualizace.

- Graf zobrazuje nulovou hodnotu, pokud jsou rámce vynechány.

  Tento příklad ukazuje, jak vypadá graf vizuální propustnost:

  ![Graf vizuální propustnosti](../profiling/media/js_htmlvizprof_vizthru.png "JS_HTMLVizProf_VizThru")

  Graf vizuální propustnosti slouží k:

- Identifikujte obecné oblasti zájmu.

- Zvolte konkrétní časové období, které se má zobrazit v grafu podrobností časové osy. Chcete-li zvolit časové období, vyberte část grafu a tažením ukazatele proveďte výběr.

- Zvolte tlačítko **Přiblížit** si podrobnější zobrazení vybraného časového období.

### <a name="view-timeline-details"></a><a name="TimelineDetails"></a>Zobrazení podrobností o časové ose
 Graf podrobností časové osy se zobrazí v dolním podokně profileru odezvy uživatelského rozhraní. Poskytuje sekvenční a hierarchické informace o událostech, které během vybraných časových období spotřebovávaly nejvíce času procesoru. Tento graf vám může pomoci určit, co spustilo konkrétní událost a u některých událostí, jak se událost mapuje zpět na zdrojový kód. Tento graf také pomáhá určit čas potřebný k malování vizuálníaktualizace na obrazovce.

 Graf ukazuje práci podprocesu uživatelského rozhraní a práci na vláknech na pozadí, které mohou přispět k pomalé vizuální aktualizace. Graf nezobrazuje javascriptovou JIT práci, asynchronní práci GPU, práci prováděnou mimo hostitelský proces (například RuntimeBroker.exe a dwm.exe work) nebo práci pro oblasti modulu Windows Runtime, které ještě nebyly instrumentovány pro profilování (například vstupně-to).

> [!TIP]
> Když dojde k události ve vlákně na pozadí, ID vlákna se zobrazí v závorkách vedle názvu události.

 Tento příklad ukazuje, jak vypadá graf podrobností časové osy, když je vybrán posluchač události pro událost kliknutí DOM:

 ![Graf podrobností časové osy](../profiling/media/js_htmlvizprof_timelinedet.png "JS_HTMLVizProf_TimelineDet")

 Na tomto obrázku je obslužná rutina události **spinAction** ve **sloupci Název události** odkaz, který vás při výběru přenese na obslužnou rutinu události ve zdrojovém kódu. V pravém podokně poskytuje vlastnost **funkce zpětného volání** stejný odkaz na zdrojový kód. Další vlastnosti také poskytují informace o události, jako je například přidružený prvek DOM.

 Pokud vyberete část časové osy pro graf využití procesoru a vizuální propustnosti (FPS), graf podrobností časové osy zobrazí podrobné informace pro vybrané časové období.

 Události v grafu podrobností časové osy jsou barevně odlišeny tak, aby představovaly stejné kategorie práce, které jsou zobrazeny v grafu využití procesoru. Další informace o kategoriích událostí a konkrétních událostech najdete v [tématu Odkaz na událost Profileru](#profiler-event-reference) v tomto tématu.

 Pomocí grafu podrobností časové osy:

- Zobrazení přibližných časů zahájení, doby trvání a ukončení události v zobrazení časové osy a mřížky. Graf podrobností časové osy může v závislosti na stavu zvětšení zobrazit periody v rozsahu od 30 milisekund do 30 sekund v zobrazení mřížky. Pro hodnoty doby trvání:

  - Včetně doby představují dobu trvání události, včetně podřízené události. V zobrazení mřížky se tato hodnota zobrazí jako první.

  - Exkluzivní časy představují dobu trvání akce, bez dětí události. V zobrazení mřížky se tato hodnota zobrazí v závorce.

- Rozbalte událost v hierarchii a zobrazte podřízené objekty události. Podřízené události jsou jiné události, které jsou vyvolány nadřazené události. Například událost DOM může mít posluchače událostí, které se zobrazují jako podřízené. Naslouchací proces události může mít jiné události, které z něj vyplývají, jako je událost rozložení.

- Seřaďte události podle počátečního času (výchozí) nebo doby trvání. Pomocí seznamu **Seřadit podle** vyberte metodu řazení.

- Zobrazit podrobnosti pro každou událost v podokně podrobností (v pravém podokně). Vlastnosti se liší v závislosti na konkrétní události, jak ukazují tyto příklady:

  - Pro časovače, posluchače událostí (události modelu DOM) a zpětná volání snímků animace vlastnost **funkce zpětného volání** poskytuje odkaz na umístění zdrojového kódu spolu s názvem obslužné rutiny události nebo funkce zpětného volání.

  - U časovačů, posluchačů událostí (události modelu DOM), událostí rozložení a zpětných volání snímků animace se barevně odlišený souhrn vybrané události a všechny její podřízené položky zobrazí v části **Souhrn času včetně** (barevně kódovaný kroužek). Každý barevně rozlišený řez obrazu představuje typ události. Popisy poskytují název typu události.

  > [!TIP]
  > Graf podrobností časové osy a **souhrn včetně času** vám mohou pomoci určit oblasti optimalizace. Pokud některý z těchto zobrazení zobrazuje velký počet malých úkolů, událost může být kandidátem pro optimalizaci. Aplikace může být například časté aktualizace prvků DOM, což má za následek velký počet událostí analýzy rozložení a HTML. Je možné optimalizovat výkon dávkováním této práce.

### <a name="filter-timeline-details"></a><a name="FilterTimelineDetails"></a>Filtrování podrobností časové osy
 Zobrazení v podrobnostech časové osy můžete filtrovat na konkrétní událost výběrem **možnosti Filtr ovat událost** z kontextové nabídky pro určitou událost. Pokud zvolíte tuto možnost, časové osy a zobrazení mřížky jsou vymezeny na vybranou událost. Výběr v grafu využití procesoru také obory na konkrétní událost.

 ![Filtrování časové osy na událost](../profiling/media/js_htmlvizprofiler_filtertoevent.png "JS_HTMLVizProfiler_FilterToEvent")

### <a name="filter-events"></a><a name="FilterEvents"></a>Filtrování událostí
 Některé události můžete odfiltrovat z grafu podrobností časové osy, abyste snížili šum v datech nebo eliminovali data, která nejsou zajímavá pro váš scénář výkonu. Můžete filtrovat podle názvu události nebo doby trvání události nebo podle konkrétních filtrů popsaných zde.

 Chcete-li odfiltrovat dekódování obrázků, spekulativní stahování a události gc, zrušte zaškrtnutí možnosti **Aktivita na pozadí** z ikony filtru v dolním podokně. Vzhledem k tomu, že tyto události nejsou příliš žalovatelné, jsou ve výchozím nastavení skryté.

 ![Filtrování událostí na časové ose](../profiling/media/js_htmlvizprofiler_event_filter.png "JS_HTMLVizProfiler_Event_Filter")

 Chcete-li odfiltrovat události požadavku HTTP, zrušte zaškrtnutí možnosti **Síťový provoz** na ikoně filtru v dolním podokně. Ve výchozím nastavení jsou tyto události zobrazeny v grafu podrobností časové osy.

 Chcete-li odfiltrovat aktivitu vlákna uživatelského rozhraní, zrušte zaškrtnutí možnosti **aktivity uživatelského rozhraní.**

> [!TIP]
> Zrušte zaškrtnutí této možnosti a vyberte možnost Síťový provoz, chcete-li prozkoumat problémy související s latencí sítě.

 Chcete-li odfiltrovat uživatelská měřítka, zrušte zaškrtnutí možnosti **Míry uživatele.** Uživatelská měřítka jsou události nejvyšší úrovně bez podřízených akcí.

### <a name="group-events-by-frame"></a><a name="GroupFrames"></a>Seskupení událostí podle snímků
 Události, které se zobrazí v zobrazení podrobností časové osy, můžete seskupit do jednotlivých snímků. Tyto události rámce jsou události generované nástrojem a představují kontejnery událostí nejvyšší úrovně pro všechny práce podprocesu uživatelského rozhraní, ke kterým dochází mezi událostmi malování. Chcete-li toto zobrazení povolit, vyberte **možnost Seskupit události nejvyšší úrovně podle rámců**.

 ![Seskupit události nejvyšší úrovně podle svatozu](../profiling/media/js_htmlvizprofiler_frame_grouping_button.png "JS_HTMLVizProfiler_Frame_Grouping_Button")

 Když seskupíte události podle snímek, události nejvyšší úrovně v podrobnostech časové osy představují každý snímek.

 ![Události časové osy seskupené podle snímků](../profiling/media/js_htmlvizprofiler_frame_grouping.png "JS_HTMLVizProfiler_Frame_Grouping")

## <a name="save-a-diagnostic-session"></a>Uložení diagnostické relace
 V sadě Visual Studio můžete uložit diagnostickou relaci při zavření karty, která je přidružena k relaci. Uložené relace lze znovu otevřít později.

## <a name="profiler-event-reference"></a>Odkaz na událost profileru
 Události profileru jsou kategorizovány a barevně odlišeny v profileru odezvy uživatelského rozhraní. Toto jsou kategorie událostí:

- **Načítání.** Označuje čas strávený načítáním prostředků aplikace a analýzou HTML a CSS při prvním načtení aplikace. To může zahrnovat síťové požadavky.

- **Skriptování.** Označuje čas strávený analýzou a spuštěním JavaScriptu. To zahrnuje události MODELU DOM, časovače, vyhodnocení skriptu a práci s rámcem animace. Obsahuje kód uživatele i kód knihovny.

- **Gc.** Označuje čas strávený na uvolňování paměti.

- **Styling.** Označuje čas strávený analýzou CSS a výpočtem prezentace a rozvržení prvku.

- **Vykreslování.** Označuje čas strávený malováním obrazovky.

- **Dekódování obrazu.** Označuje čas strávený dekomprezací a dekódováním obrazů.

  Pro skript a styl kategorie profileru odezvy uživatelského rozhraní může poskytnout data, která můžete použít v grafu podrobností časové osy. Pokud identifikujete problémy se skriptováním jako problém, můžete spustit profiler vzorkování procesoru pomocí profileru odezvy uživatelského rozhraní. Případně můžete použít profiler funkce sady Visual Studio k získání podrobnějších dat. Další informace naleznete v [tématu JavaScript Memory](../profiling/javascript-memory.md).

  Pro ostatní kategorie událostí můžete identifikovat vedlejší účinky platformy, které vyplývají z přidání funkcí do aplikace, ale v těchto případech nemusí být možné vyřešit konkrétní problémy s výkonem pomocí profileru odezvy uživatelského rozhraní.

  V této tabulce jsou uvedeny události a jejich popisy:

|Událost|Kategorie události|Nastane, když|
|-----------|--------------------|-----------------|
|Analýza CSS|Načítání|Byl zjištěn nový obsah CSS a došlo k pokusu o analýzu obsahu CSS.|
|Analýza HTML|Načítání|Byl zjištěn nový obsah HTML a byl proveden pokus o analýzu obsahu do uzlů a vložení obsahu do stromu dom.|
|Požadavek HTTP|Načítání|V režimu dom byl nalezen vzdálený prostředek nebo byl vytvořen požadavek XMLHttpRequest, který vyústil v požadavek HTTP.|
|Spekulativní stahování|Načítání|Obsah HTML stránky byl vyhledán požadované prostředky, takže následné požadavky HTTP pro prostředky mohly být naplánovány rychle.|
|Funkce zpětného volání snímků animace|Skriptování|Prohlížeč se chystal vykreslit jiný snímek, a to spustilo funkci zpětného volání poskytované aplikací.|
|Událost DOM|Skriptování|Došlo k události dom a byl proveden.<br /><br /> Vlastnost `context` události DOM, například `DOMContentLoaded` `click`nebo , je zobrazena v závorce.|
|Posluchač události|Skriptování|Posluchač události byl volán a proveden.|
|Naslouchací proces dotazu na média|Skriptování|Registrovaný mediální dotaz byl zrušen, což vedlo k provedení jeho přidruženého posluchače.|
|Pozorovatel mutace|Skriptování|Jeden nebo více pozorovaných prvků DOM byly změněny, což vedlo k provedení mutationObserver přidružené zpětné volání.|
|Vyhodnocení skriptu|Skriptování|V objektu DOM byl nalezen nový element SCRIPT a byl proveden pokus o analýzu a spuštění skriptu.|
|Časovač|Skriptování|Vypršel a uplynul naplánovaný časovač, což vedlo k provedení přidružené funkce zpětného volání.|
|Funkce asynchronního zpětného volání prostředí Windows Runtime|Skriptování|Asynchronní operace, `Promise` která spustila funkci zpětného volání, byla dokončena objektem prostředí Windows Runtime.|
|Událost prostředí Windows Runtime|Skriptování|Událost, ke které došlo v objektu prostředí Windows Runtime, spustila registrovaný naslouchací proces.|
|Uvolnění paměti|Uvolňování paměti|Čas byl strávený shromažďovánípaměti pro objekty, které již nebyly používány.|
|Výpočet CSS|Použití stylů|Byly provedeny změny do dom, které vyžadovaly vlastnosti stylu všech ovlivněných prvků, které mají být přepočítány.|
|Rozložení|Použití stylů|Byly provedeny změny dodo, které vyžadovaly velikost a / nebo umístění všech postižených prvků, které mají být přepočítány.|
|Malovat|Vykreslování|Byly provedeny vizuální změny v dom a byl proveden pokus o re-render části stránky.|
|Vykreslit vrstvu|Vykreslování|Vizuální změny byly provedeny na nezávisle vykreslen fragment DOM (tzv vrstva) a změny vyžadovaly část stránky, které mají být vykresleny.|
|Dekódování obrazu|Dekódování obrázku|Obraz byl zahrnut do do dom a byl proveden pokus o dekompresi a dekódování obrazu z původního formátu do bitmapy.|
|Rámec|Není dostupné.|Byly provedeny vizuální změny do dom, které vyžadují všechny ovlivněné části stránky, které mají být překresleny. Toto je událost generovaná nástrojem používaná pro seskupení.|
|Uživatelská míra|Není dostupné.|Scénář specifický pro aplikaci `performance.measure` byl měřen pomocí metody. Toto je událost generovaná nástrojem používaná pro analýzu kódu.|

## <a name="additional-information"></a>Další informace

- Podívejte se na [toto video](https://channel9.msdn.com/Events/Build/2013/3-316) z konference Build 2013 o profileru odezvy uživatelského rozhraní.

- Přečtěte si tipy pro výkon aplikací UPW vytvořených pro Windows pomocí JavaScriptu. Další informace najdete [v tématu Doporučené postupy pro výkon aplikací UPW pomocí JavaScriptu](/previous-versions/windows/apps/hh465194\(v\=win.10\)).

- Informace o modelu spuštění kódu s jedním vláknem a výkonu naleznete [v tématu Executing code](/previous-versions/windows/apps/hh781217\(v\=win.10\)).

## <a name="see-also"></a>Viz také
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
