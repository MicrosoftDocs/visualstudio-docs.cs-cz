---
title: Odezva uživatelského rozhraní HTML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: af2b71dd2169500b1c4a75ed59292779959d31a0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299669"
---
# <a name="html-ui-responsiveness"></a>Rychlost odezvy uživatelského rozhraní (HTML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje, jak v aplikacích izolovat problémy s výkonem pomocí profileru odezvy uživatelského rozhraní, který je dostupný pro univerzální aplikace pro Windows.  
  
 Profiler odezvy uživatelského rozhraní vám může pomáhat izolovat problémy, jako jsou například problémy s odezvou uživatelského rozhraní nebo vedlejší efekty platformy, které se obvykle vyskytují s těmito příznaky:  
  
- Chybějící odezva v uživatelském rozhraní. Pokud je vlákno uživatelského rozhraní blokované, může aplikace reagovat pomalu. Mezi věci, které mohou blokovat vlákno uživatelského rozhraní, patří nadměrné synchronní kódování JavaScriptu, nadměrné rozložení šablon stylů CSS nebo práce se zpracováním šablon stylů CSS, synchronní požadavky XHR, uvolňování paměti, nadměrné doby vybarvení nebo kód JavaScriptu náročný na procesor.  
  
- Čas zpomalení načítání aplikace nebo stránky. To je obvykle způsobeno nadměrným časem načítání prostředků.  
  
- Aktualizace vizuálů, které jsou méně časté, než bylo očekáváno. K tomu dochází, pokud je vlákno uživatelského rozhraní příliš zaneprázdněné, aby se zachovala plynulá frekvence snímků. Například pokud je vlákno uživatelského rozhraní zaneprázdněno, mohou být rámce vyřazeny. Některé pracovní procesy bez uživatelského rozhraní, jako jsou třeba síťové požadavky, dekódování obrázků a malování, mohou také omezit četnost vizuálních aktualizací. (Ne všechny kresby se provádí ve vlákně uživatelského rozhraní.)  
  
## <a name="RunningProfiler"></a>Spusťte nástroj pro odezvu uživatelského rozhraní HTML.  
 Nástroj pro odezvu uživatelského rozhraní HTML můžete použít, když máte fungující aplikaci pro Windows (Universal nebo Windows Store) otevřenou v aplikaci Visual Studio nebo nainstalovanou na počítači se systémem Windows 8 nebo novějším.  
  
1. Pokud spouštíte aplikaci ze sady Visual Studio, na panelu nástrojů **standardní** v seznamu **Spustit ladění** vyberte cíl nasazení, jako je například jeden z emulátorů Windows Phone, **místní počítač**, **simulátor**nebo **vzdálený počítač**.  
  
2. V nabídce **ladění** vyberte možnost **Profiler výkonnosti...** .  
  
     Pokud chcete změnit cíl analýzy pro Profiler, klikněte na tlačítko**změnit cíl**.  
  
     ![Změnit cíl analýzy](../profiling/media/js-tools-target.png "JS_Tools_Target")  
  
     Pro cíl analýzy jsou k dispozici následující možnosti:  
  
    - **Spouštěný projekt**. Tuto možnost vyberte, pokud chcete analyzovat aktuální spouštěný projekt. Pokud aplikaci spouštíte na vzdáleném počítači nebo zařízení, musíte použít toto nastavení, což je výchozí hodnota.  
  
    - **Spouští se aplikace**. Tuto možnost vyberte, pokud chcete ze seznamu spuštěných aplikací vybrat aplikaci pro Windows Store. Tuto možnost nemůžete použít, když aplikaci spouštíte na vzdáleném počítači nebo zařízení.  
  
         Tuto možnost můžete použít k analýze výkonu aplikací, které jsou spuštěny v počítači, pokud nemáte přístup ke zdrojovému kódu.  
  
    - **Nainstalovaná aplikace**. Tuto možnost vyberte, pokud chcete vybrat nainstalovanou aplikaci, kterou chcete analyzovat. Tuto možnost nemůžete použít, když aplikaci spouštíte na vzdáleném počítači nebo zařízení.  
  
         Tuto možnost můžete použít k analýze výkonu aplikací, které jste nainstalovali v počítači, když nemáte přístup ke zdrojovému kódu. Tato možnost může být užitečná také v případě, že chcete pouze analyzovat výkon jakékoli aplikace mimo vlastní vývoj aplikací.  
  
3. Z **dostupných nástrojů**vyberte možnost **odezva uživatelského rozhraní HTML**a pak zvolte možnost **Spustit**.  
  
4. Když spustíte Profiler odezvy uživatelského rozhraní, může okno Řízení uživatelských účtů požádat o vaše oprávnění ke spuštění sady Visual Studio ETW. exe. Zvolte **Ano**.  
  
     V interakci s aplikací otestujete relevantní scénář výkonu. Podrobný pracovní postup najdete v tématu [izolování problému s odezvou uživatelského rozhraní](#Workflow) a [izolování problému s vizuální propustností](#IsolateVisualThroughput).  
  
5. Přepněte do sady Visual Studio stisknutím kláves ALT + TAB.  
  
6. Pokud chcete zastavit profilaci aplikace a zobrazit data shromážděná profilerem, klikněte na **Zastavit shromažďování**.  
  
## <a name="IsolateAnIssue"></a>Izolovat problém  
 V následující části najdete návrhy, které vám pomůžou izolovat problémy s výkonem. Podrobné vysvětlení, jak identifikovat a opravit problémy s výkonem pomocí ukázkové aplikace testování výkonu, najdete v tématu [Návod: vylepšení odezvy uživatelského rozhraní (HTML)](../profiling/walkthrough-improving-ui-responsiveness-html.md).  
  
### <a name="Workflow"></a>Izolace problému s odezvou uživatelského rozhraní  
 Tyto kroky poskytují navrhovaný pracovní postup, který vám může pomáhat efektivně používat profiler odezvy uživatelského rozhraní:  
  
1. Otevřete aplikaci v aplikaci Visual Studio.  
  
2. Otestujte svoji aplikaci pro problémy s odezvou uživatelského rozhraní. (Stisknutím kombinace kláves CTRL + F5 spustíte aplikaci bez ladění.)  
  
     Pokud narazíte na problém, pokračujte v testování a pokuste se zúžit časový rámec, ve kterém k problému dojde, nebo se pokuste identifikovat triggery, které způsobují chování.  
  
3. Přepněte do sady Visual Studio (stiskněte klávesy ALT + TAB) a zastavte aplikaci (Shift + F5).  
  
4. Volitelně můžete do kódu přidat značky uživatelů pomocí [značky Code pro analýzu](#ProfileMark).  
  
    > [!TIP]
    > Uživatelské značky vám můžou při prohlížení dat profileru pomáhat identifikovat problém s odezvou. Například můžete přidat značku uživatele na začátku a konec části kódu, která způsobuje problém s odezvou.  
  
5. Postupujte podle pokynů v předchozí části a spusťte Profiler odezvy uživatelského rozhraní.  
  
6. Uložte aplikaci do stavu, který vede k potížím s odezvou uživatelského rozhraní.  
  
7. Přepněte do sady Visual Studio (stiskněte ALT + TAB) a zvolte **Zastavit shromažďování** na kartě profiler profileru odezvy uživatelského rozhraní.  
  
8. Pokud jste přidali uživatelské značky, zobrazí se v [zobrazení časové osy diagnostické relace](#Ruler) v profileru. Následující ilustrace znázorňuje jeden uživatelský symbol použitý k určení konkrétní operace ve vašem kódu.  
  
     ![Pravítko pro diagnostiku znázorňující značku uživatele](../profiling/media/js-htmlvizprofiler-usermark.png "JS_HTMLVizProfiler_UserMark")  
  
9. Identifikujte oblast zájmu na časové ose a grafy profileru pomocí značek uživatele, událostí životního cyklu aplikace nebo dat zobrazených v grafech. Tady jsou některé pokyny, které vám pomůžou s analýzou a používáním dat v grafech:  
  
    - Pomocí [zobrazení časové osy diagnostické relace](#Ruler) můžete zobrazit [kód pro analýzu](#ProfileMark), události životního cyklu aplikace a přidruženou časovou osu pro tyto události a časovou osu pro data v ostatních grafech.  
  
    - Pomocí [grafu využití CPU](#CPUUtilization) můžete zobrazit obecné informace o aktivitě procesoru a typu práce, kterou zpracovává během konkrétního časového období. Doby nadměrné aktivity procesoru mají za následek problémy s odezvou a vynechané snímky.  
  
    - Pokud vyvíjíte herní nebo bohatou mediální aplikaci, použijte [zobrazení snímků vizuální propustnost (FPS)](#VisualThroughput) k identifikaci časových úseků, ve kterých se snížila frekvence snímků.  
  
10. Vyberte oblast zájmu v jednom z grafů kliknutím na část grafu a přetažením ukazatele myši provedete výběr (nebo pomocí klávesy TAB a kláves se šipkami). Když vyberete časové období vyplněním výběru, graf podrobností časové osy v dolním podokně profileru se změní tak, aby zobrazoval pouze vybrané časové období.  
  
     Na následujícím obrázku vidíte graf využití procesoru s oblastí, která je zvýrazněna z hlediska zájmu.  
  
     ![Graf využití procesoru](../profiling/media/js-htmlvizprof-cpu-util.png "JS_HTMLVizProf_CPU_Util")  
  
11. Pomocí [podrobností Zobrazit časovou osu](#TimelineDetails) získáte podrobné informace o událostech, které jsou spuštěny příliš často nebo příliš dlouho k dokončení. Podívejte se například na následující:  
  
    - Naslouchací procesy událostí, časovače a zpětná volání snímků animace. V závislosti na konkrétní události může poskytnutá data zahrnovat ID upravených elementů modelu DOM, název změněných vlastností šablon stylů CSS, odkaz na zdrojové umístění a název související funkce Event nebo callback.  
  
    - Události rozložení nebo skriptování, které vedly k vykreslování prvků, jako jsou například volání `window.getComputedStyles`. K dispozici je přidružený element modelu DOM pro událost.  
  
    - Stránky nebo prostředky URL, které jsou načteny aplikací, například vyhodnocení skriptů pro události analýzy HTML. Je zadaný název souboru nebo prostředek.  
  
    - Další události zadané v [odkazu na událost profileru](#ProfilerEvents).  
  
    > [!TIP]
    > Většina užitečných informací v profileru se zobrazí v grafu podrobnosti časové osy.  
  
12. Pokud chcete získat podrobnější informace, vyberte oblast vybranou v grafu využití procesoru nebo vizuální propustnost (FPS) a klikněte na tlačítko **přiblížit** (buď na tlačítko, nebo v kontextové nabídce). Časová osa grafu se změní tak, aby zobrazovala pouze vybrané časové období.  
  
13. Když se přiblížíte, vyberte část využití procesoru nebo graf vizuální propustnost. Když provedete výběr, graf podrobností časové osy v dolním podokně profileru se změní tak, aby zobrazoval pouze vybrané časové období.  
  
### <a name="IsolateVisualThroughput"></a>Izolace problému s vizuální propustností  
 Intervaly nadměrného využití procesoru můžou mít za následek nízké nebo nekonzistentní kmitočty snímků. Při vývoji bohatých mediálních aplikací a her může graf propustnosti vizuálů poskytovat důležitější data než graf využití procesoru.  
  
 Chcete-li izolovat problém s vizuální propustností, postupujte podle kroků popsaných v předchozí části, ale použijte graf vizuální propustnost jako jeden z klíčových datových bodů.  
  
### <a name="ProfileMark"></a>Označit kód k analýze  
 Pro lepší izolaci oddílu kódu aplikace, který je spojen s daty, která se zobrazí v grafech, můžete do aplikace přidat volání funkce, které dává profileru pokyn, aby vložil uživatelskou značku – na časové ose v okamžiku, kdy se funkce spustí. Jakékoli uživatelské značky, které přidáte, se zobrazí na časové ose pro graf využití procesoru, graf vizuální propustnost a graf podrobností časové osy.  
  
 Pokud chcete přidat značku uživatele, přidejte do aplikace následující kód. V tomto příkladu se jako popis události používá "získávání dat".  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("getting data");  
}  
  
```  
  
 Popis události se zobrazí jako popisek při umístění ukazatele myši na značku uživatele. Můžete přidat tolik uživatelských značek, kolik potřebujete.  
  
> [!NOTE]
> `console.timeStamp`– příkaz pro Chrome se zobrazí také jako značka uživatele.  
  
 Následující obrázek znázorňuje diagnostické pravítko s jedním uživatelským značkou a jeho popisem.  
  
 ![Pravítko pro diagnostiku znázorňující značku uživatele](../profiling/media/js-htmlvizprofiler-usermark.png "JS_HTMLVizProfiler_UserMark")  
  
 Můžete také vytvořit události vygenerované nástrojem v zobrazení Details Timeline a zobrazit tak dobu trvání, která uplyne mezi dvěma uživatelskými značkami. Následující kód přidá druhou značku uživatele a měření času, který uplyne mezi provedením dvou uživatelských značek (předchozí kód ukazuje první znak uživatele).  
  
```javascript  
if (performance.mark && performance.measure) {  
    performance.mark("data retrieved");  
    performance.measure("data measure", "getting data", "data retrieved");  
}  
```  
  
 Pokud není zadán druhý uživatelský symbol, `performance.measure` jako druhý znak uživatele používá časové razítko. První značka uživatele je povinná.  
  
 Měření doby trvání se zobrazí jako událost **míry uživatele** v zobrazení Details Timeline a při výběru se zobrazí podrobné informace.  
  
 ![Událost míry uživatele v zobrazení podrobností časové osy](../profiling/media/js-htmlvizprofiler-user-measure.png "JS_HTMLVizProfiler_User_Measure")  
  
## <a name="AnalyzeData"></a>Analyzovat data  
 Následující části obsahují informace, které vám pomůžou interpretovat data zobrazená v profileru.  
  
### <a name="Ruler"></a>Zobrazit časovou osu diagnostické relace  
 Pravítko v horní části profileru zobrazuje časovou osu pro profilované informace. Tato časová osa se vztahuje na graf využití procesoru i pro graf vizuální propustnost.  
  
 Tady je postup, jak vypadá časová osa relace diagnostiky s popisem zobrazeným pro několik událostí životního cyklu aplikace:  
  
 ![Pravítko pro relaci diagnostiky](../profiling/media/js-htmlvizprof-ruler.png "JS_HTMLVizProf_Ruler")  
  
 Časová osa ukazuje, kdy dojde k událostem lifecyle aplikace, jako je aktivační událost, a zobrazuje uživatelské značky (trojúhelníky značek uživatele), které můžete přidat do kódu. Můžete vybrat události, pro které se mají zobrazit popisy tlačítek, a další informace. Další informace o uživatelských značkách naleznete v části [označení kódu k analýze](#ProfileMark) v tomto tématu.  
  
 Události životního cyklu aplikace se zobrazují jako kosočtvercové symboly. Jedná se o události modelu DOM, které zahrnují následující:  
  
- události `DOMContentLoaded` a `Load`, ke kterým obvykle dochází v obslužné rutině aktivované události ve vašem kódu. Popis události pro událost zobrazuje konkrétní událost a adresu URL.  
  
- Navigační událost, která nastane, když přejdete na jinou stránku. Popis události zobrazuje adresu URL cílové stránky.  
  
### <a name="CPUUtilization"></a>Zobrazení využití procesoru  
 Graf využití procesoru vám umožňuje identifikovat časová období, ve kterých se nachází nadměrné aktivity CPU. Poskytuje informace o průměrném využití procesoru aplikace v časovém intervalu. Informace jsou barevně kódované, aby představovaly následující konkrétní kategorie: **načítání**, **skriptování**, uvolňování paměti (**GC**), **stylování**, **vykreslování**a **dekódování obrázku**. Další informace o těchto kategoriích najdete v části [referenční informace k události profileru](#ProfilerEvents) dále v tomto tématu.  
  
 Graf využití procesoru zobrazuje množství času stráveného ve všech vláknech aplikací a kombinaci hodnot využití procesoru pro jeden nebo více procesorů do jedné procentuální hodnoty. Hodnota využití CPU může překročit 100%, pokud se používá více než jeden procesor.  
  
> [!NOTE]
> Využití GPU se v grafu nezobrazí.  
  
 Tento příklad ukazuje, co vypadá graf využití procesoru:  
  
 ![Graf využití procesoru](../profiling/media/js-htmlvizprof-cpu-util.png "JS_HTMLVizProf_CPU_Util")  
  
 Tento graf použijte k těmto akcím:  
  
- Identifikujte obecné oblasti, které se týkají.  
  
- Vyberte konkrétní časové období, které se má zobrazit v grafu podrobností časové osy. Chcete-li zvolit časové období, vyberte část grafu a přetáhněte ukazatel myši a proveďte výběr.  
  
- Podrobnější zobrazení vybraného časového období získáte tak, že kliknete na tlačítko **přiblížení** .  
  
  Další informace o používání grafu najdete v části [izolování problému s odezvou uživatelského rozhraní](#Workflow) v tomto tématu.  
  
### <a name="VisualThroughput"></a>Zobrazit propustnost vizuálů (FPS)  
 Graf propustnosti vizuálů vám umožní určit časové úseky, ve kterých se přetáhla snímková frekvence. Zobrazuje počet snímků za sekundu (FPS) pro aplikaci. Tento graf je nejužitečnější pro vývoj her a bohatých mediálních aplikací.  
  
 Zobrazená hodnota FPS se může lišit od skutečné frekvence snímků. Při zkoumání dat v tomto grafu Pamatujte na tyto informace:  
  
- V grafu se zobrazuje FPS, který může aplikace dosáhnout v určitou dobu. Pokud je aplikace nečinná, FPS je stejná jako obnovovací frekvence monitorování.  
  
- Graf zobrazuje skutečnou FPS, pokud aplikace provádí práci, která vyžaduje vizuální aktualizace.  
  
- Graf zobrazuje hodnotu nula, pokud se snímky vynechává.  
  
  Tento příklad ukazuje, jak vypadá graf vizuální propustnost:  
  
  ![Graf propustnosti vizuálů](../profiling/media/js-htmlvizprof-vizthru.png "JS_HTMLVizProf_VizThru")  
  
  Pomocí grafu vizuální propustnost:  
  
- Identifikujte obecné oblasti, které se týkají.  
  
- Vyberte konkrétní časové období, které se má zobrazit v grafu podrobností časové osy. Chcete-li zvolit časové období, vyberte část grafu a přetáhněte ukazatel myši a proveďte výběr.  
  
- Podrobnější zobrazení vybraného časového období získáte tak, že kliknete na tlačítko **přiblížení** .  
  
### <a name="TimelineDetails"></a>Zobrazit podrobnosti časové osy  
 Graf podrobností časové osy se zobrazí v dolním podokně profileru odezvy uživatelského rozhraní. Poskytuje sekvenční a hierarchické informace o událostech, které spotřebují nejvíce času procesoru během zvolených časových období. Tento graf vám pomůže určit, co aktivoval konkrétní událost, a pro některé události, jak se událost mapuje zpět do zdrojového kódu. Tento graf vám také pomůže určit dobu potřebnou k malování vizuálních aktualizací na obrazovce.  
  
 Graf zobrazuje práci vlákna uživatelského rozhraní a pracuje na vláknech na pozadí, které mohou přispět k pomalým vizuálním aktualizacím. Graf nezobrazuje práci JIT JavaScriptu, asynchronní práci s grafickým procesorem, práci provedenou mimo hostitelský proces (například RuntimeBroker. exe a DWM. exe Work) nebo funguje pro oblasti prostředí Windows Runtime, které ještě nebyly instrumentované pro profilaci (například v/v disku).  
  
> [!TIP]
> V případě, že dojde k události ve vlákně na pozadí, ID vlákna se zobrazí v závorkách vedle názvu události.  
  
 Tento příklad ukazuje, jak vypadá graf podrobností časové osy, když je vybraná událost posluchače události Click modelu DOM:  
  
 ![Graf podrobností časové osy](../profiling/media/js-htmlvizprof-timelinedet.png "JS_HTMLVizProf_TimelineDet")  
  
 Na tomto obrázku je obslužná rutina události **spinAction** ve sloupci **název události** odkaz, který, pokud je vybrána, přejde do obslužné rutiny události ve zdrojovém kódu. V pravém podokně vlastnost **funkce zpětného volání** poskytuje stejný odkaz na zdrojový kód. Další vlastnosti také poskytují informace o události, jako je například přidružený prvek modelu DOM.  
  
 Pokud vyberete část časové osy pro graf využití CPU a vizuální propustnost (FPS), zobrazí se v grafu podrobnosti časové osy podrobné informace o vybraném časovém období.  
  
 Události v grafu podrobností časové osy jsou barevně zakódované tak, aby představovaly stejné kategorie práce, které se zobrazují v grafu využití CPU. Další informace o kategoriích událostí a konkrétních událostech najdete v části [referenční informace k události profileru](#ProfilerEvents) v tomto tématu.  
  
 Graf podrobností časové osy použijte k těmto akcím:  
  
- Zobrazí přibližné časy spuštění, trvání a čas ukončení události v zobrazení Časová osa a mřížka. Graf podrobností časové osy může zobrazit období v rozsahu od 30 milisekund do 30 sekund v zobrazení mřížky v závislosti na stavu přiblížení. Pro hodnoty doby trvání:  
  
  - Celková doba představuje dobu trvání události, včetně podřízených událostí. V zobrazení mřížky se tato hodnota zobrazí jako první.  

  - Exkluzivní doba představuje dobu trvání události, včetně podřízených událostí. V zobrazení mřížky se tato hodnota zobrazí v závorkách.  
  
- Rozbalením události v hierarchii zobrazíte podřízené objekty události. Podřízené události jsou další události, které jsou vyvolány nadřazenou událostí. Například událost modelu DOM může mít naslouchací procesy událostí, které se zobrazí jako podřízené objekty. Naslouchací proces události může mít další události, které jsou výsledkem, například událost rozložení.  
  
- Seřadit události podle času spuštění (výchozí nastavení) nebo trvání. Pomocí seznamu **Seřadit podle** vyberte metodu řazení.  
  
- Zobrazit podrobnosti o každé události v podokně podrobností (pravé podokno). Vlastnosti se liší v závislosti na konkrétní události, jak ukazují tyto příklady:  
  
  - Pro časovače, posluchače událostí (události modelu DOM) a zpětná volání snímků animace poskytuje vlastnost **funkce zpětného volání** odkaz na umístění zdrojového kódu spolu s názvem obslužné rutiny události nebo funkce zpětného volání.  

  - Pro časovače, posluchače událostí (události modelu DOM), události rozložení a zpětná volání snímků animace se barevně kódovaným souhrnem vybrané události a všech jejích podřízených položek zobrazí v oddílu celková celková **Časová** část (barva – kódovaný prstenec). Každý barevně kódovaný řez obrázku představuje typ události. Popisky obsahují název typu události.  

  > [!TIP]
  > Souhrn grafu podrobností časové osy a **celkového času** vám může pomáhat při identifikaci oblastí pro optimalizaci. Pokud některé z těchto zobrazení zobrazuje velký počet malých úloh, může být událost kandidátem na optimalizaci. Například aplikace může často obnovovat prvky modelu DOM, což vede k velkým počtům událostí rozložení a analýzám HTML. Je možné, že dávkování této práce optimalizuje výkon.  

### <a name="FilterTimelineDetails"></a>Podrobnosti o filtru časové osy  
 Zobrazení můžete filtrovat v podrobnostech časové osy na konkrétní událost výběrem možnosti **Filtr na událost** z kontextové nabídky pro konkrétní událost. Pokud zvolíte tuto možnost, bude časová osa a zobrazení mřížky vymezeno na vybranou událost. Výběr v grafu využití CPU také obory na konkrétní událost.  
  
 ![Filtrování časové osy na událost](../profiling/media/js-htmlvizprofiler-filtertoevent.png "JS_HTMLVizProfiler_FilterToEvent")  
  
### <a name="FilterEvents"></a>Filtrovat události  
 Můžete vyfiltrovat některé události z grafu podrobností časové osy, abyste snížili šum v datech nebo vyloučili data, která nejsou zajímavá pro váš scénář výkonu. Můžete filtrovat podle názvu události nebo trvání události nebo podle konkrétního filtru popsaného tady.  
  
 Pokud chcete vyfiltrovat dekódování obrázku, spekulativní stahování a události GC, vymažte možnost **aktivita na pozadí** z ikony filtru v dolním podokně. Vzhledem k tomu, že tyto události nejsou velmi napadnutelné, jsou ve výchozím nastavení skryté.  
  
 ![Filtrování událostí na časové ose](../profiling/media/js-htmlvizprofiler-event-filter.png "JS_HTMLVizProfiler_Event_Filter")  
  
 Pokud chcete vyfiltrovat události požadavku HTTP, zrušte zaškrtnutí políčka **síťový provoz** z ikony filtru v dolním podokně. Ve výchozím nastavení jsou tyto události zobrazeny v grafu podrobnosti časové osy.  
  
 Chcete-li odfiltrovat aktivitu vlákna uživatelského rozhraní, zrušte zaškrtnutí možnosti **aktivita uživatelského rozhraní** .  
  
> [!TIP]
> Zrušte zaškrtnutí této možnosti a vyberte možnost síťového provozu a prozkoumejte problémy související s latencí sítě.  
  
 Chcete-li vyfiltrovat míry uživatele, zrušte zaškrtnutí možnosti **míry uživatele** . Uživatelské míry jsou události nejvyšší úrovně bez podřízených objektů.  
  
### <a name="GroupFrames"></a>Seskupit události podle rámce  
 Události, které se zobrazují v zobrazení Details Timeline, můžete seskupit do jednotlivých snímků. Tyto události rámce jsou události vygenerované nástrojem a představují kontejnery událostí nejvyšší úrovně pro veškerou práci vlákna uživatelského rozhraní, ke které dochází mezi událostmi vykreslování. Chcete-li povolit toto zobrazení, vyberte možnost **Seskupit události nejvyšší úrovně podle rámců**.  
  
 ![Seskupit události nejvyšší úrovně podle rámce](../profiling/media/js-htmlvizprofiler-frame-grouping-button.png "JS_HTMLVizProfiler_Frame_Grouping_Button")  
  
 Když seskupete události podle rámce, události nejvyšší úrovně v zobrazení Details Timeline každý představuje rámec.  
  
 ![Události časové osy seskupené podle rámce](../profiling/media/js-htmlvizprofiler-frame-grouping.png "JS_HTMLVizProfiler_Frame_Grouping")  
  
## <a name="SaveSession"></a>Uložit relaci diagnostiky  
 V aplikaci Visual Studio můžete relaci diagnostiky uložit, když zavřete kartu, která je přidružena k relaci. Uložené relace je možné znovu otevřít později.  
  
## <a name="ProfilerEvents"></a>Reference k události profileru  
 Události profileru jsou rozdělené do kategorií a barevně kódované v profileru odezvy uživatelského rozhraní. Jedná se o kategorie událostí:  
  
- **Načítá.** Označuje čas strávený načítáním prostředků aplikace a analýzou kódu HTML a CSS při prvním načtení aplikace. To může zahrnovat síťové požadavky.  
  
- **Prostředí.** Označuje dobu strávenou analýzou a spuštěním JavaScriptu. To zahrnuje události modelu DOM, časovače, vyhodnocení skriptu a práci s rámcem animace. Zahrnuje kód uživatele i knihovny.  
  
- **GC.** Označuje dobu strávenou uvolňováním paměti.  
  
- **Používání stylů.** Označuje dobu strávenou analýzou šablon stylů CSS a výpočtem prezentace a rozložení prvku.  
  
- **Vykreslování.** Označuje čas strávený vykreslováním obrazovky.  
  
- **Dekódování obrázku.** Označuje dobu strávenou dekomprimací a dekódováním obrázků.  
  
  Pro kategorie skriptu a stylů může Profiler odezvy uživatelského rozhraní poskytnout data, která můžete v grafu podrobností časové osy použít. Pokud identifikujete problémy skriptování jako problém, můžete spustit Profiler vzorkování procesoru s profilem odezvy uživatelského rozhraní. Alternativně můžete k získání podrobnějších dat použít Profiler funkcí sady Visual Studio. Další informace najdete v tématu [Analýza dat časování funkcí JavaScriptu](https://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b).  
  
  U ostatních kategorií událostí může být možné identifikovat vedlejší účinky platformy, které jsou výsledkem přidávání funkcí do aplikace, ale v těchto případech možná nebudete schopni vyřešit konkrétní problémy s výkonem pomocí profileru odezvy uživatelského rozhraní.  
  
  Tato tabulka zobrazuje události a jejich popisy:  
  
|Událost|Kategorie události|Nastane, když|  
|-----------|--------------------|-----------------|  
|Analýza šablon stylů CSS|Načítá|Byl zjištěn nový obsah CSS a byl proveden pokus o analýzu obsahu CSS.|  
|Analýza kódu HTML|Načítá|Byl nalezen nový obsah HTML a byl proveden pokus o analýzu obsahu na uzly a vložení obsahu do stromu modelu DOM.|  
|Požadavek HTTP|Načítá|V modelu DOM se našel vzdálený prostředek nebo se vytvořil objekt XMLHttpRequest, který způsobil požadavek HTTP.|  
|Spekulativní stahování|Načítá|V obsahu HTML stránky se vyhledaly požadované prostředky, aby bylo možné rychle naplánovat následné požadavky HTTP pro prostředky.|  
|Funkce zpětného volání snímku animace|Skriptování|V prohlížeči se vykreslil další snímek, který aktivoval funkci zpětného volání poskytnutou aplikací.|  
|Událost modelu DOM|Skriptování|Došlo k události modelu DOM a byla provedena.<br /><br /> Vlastnost `context` pro událost DOM, například `DOMContentLoaded` nebo `click`, je uvedena v závorkách.|  
|Naslouchací proces událostí|Skriptování|Byl volán a proveden naslouchací proces událostí.|  
|Naslouchací proces dotazů na média|Skriptování|Registrovaný dotaz na média byl neověřen, což vedlo k provedení jeho přidružených naslouchacího procesu (ů).|  
|Pozorovatel mutací|Skriptování|Jeden nebo více pozorovaných elementů modelu DOM bylo upraveno, což vedlo k provedení MutationObserver přidruženého zpětného volání.|  
|Vyhodnocení skriptu|Skriptování|V modelu DOM byl nalezen nový prvek skriptu a byl proveden pokus o analýzu a spuštění skriptu.|  
|Časovač|Skriptování|Naplánovaný časovač uplynul a výsledkem je spuštění přidružené funkce zpětného volání.|  
|prostředí Windows Runtime funkce asynchronního zpětného volání|Skriptování|Asynchronní operace, která aktivovala funkci zpětného volání `Promise`, byla dokončena objektem prostředí Windows Runtime.|  
|Událost prostředí Windows Runtime|Skriptování|Událost, ke které došlo u prostředí Windows Runtimeho objektu, aktivovala zaregistrovaný naslouchací proces.|  
|Uvolnění paměti|Uvolňování paměti|Čas strávil shromažďování paměti pro objekty, které se již nepoužívají.|  
|Výpočet CSS|Použití stylů|V modelu DOM byly provedeny změny, které vyžadovaly přepočítání vlastností stylu všech ovlivněných elementů.|  
|Rozložení|Použití stylů|V modelu DOM byly provedeny změny, které vyžadovaly přepočítání velikosti a/nebo umístění všech ovlivněných elementů.|  
|Barva|Vykreslování|V modelu DOM byly provedeny vizuální změny a byl proveden pokus o opětovné vykreslení částí stránky.|  
|Vykreslit vrstvu|Vykreslování|Byly provedeny vizuální změny nezávislého vykresleného fragmentu modelu DOM (označovaného jako vrstva) a změny, které jsou požadovány pro vykreslení části stránky.|  
|Dekódování obrázku|Dekódování obrázku|V modelu DOM byl obsažen obrázek a byl proveden pokus o dekompresi a dekódování obrázku z jeho původního formátu do rastrového obrázku.|  
|Rámec|Není k dispozici|V modelu DOM byly provedeny vizuální změny, které vyžadovaly překreslení všech ovlivněných částí stránky. Jedná se o událost generovanou nástrojem použitou k seskupení.|  
|Míra uživatele|Není k dispozici|Scénář specifický pro aplikaci byl měřen pomocí metody `performance.measure`. Toto je událost generovaná nástrojem, která se používá pro analýzu kódu.|  
  
## <a name="Tips"></a>Další informace  
  
- Podívejte se na [Toto video](https://channel9.msdn.com/Events/Build/2013/3-316) z konference Build 2013 o profileru odezvy uživatelského rozhraní.  
  
- Přečtěte si tipy ke zvýšení výkonu pro aplikace pro Windows Store sestavené pro Windows pomocí JavaScriptu. Další informace najdete v tématu [osvědčené postupy výkonu pro aplikace pro Windows Store pomocí JavaScriptu](https://msdn.microsoft.com/library/windows/apps/hh465194.aspx).  
  
- Informace o modelu spuštění kódu s jedním vláknem a výkonu najdete v tématu [spouštění kódu](https://msdn.microsoft.com/library/windows/apps/hh781217.aspx).  
  
## <a name="see-also"></a>Viz také  
 [Analýza výkonu aplikace](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)
