---
title: Oznámení a postup pro Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aee6e5656142d0597ff6101da5e2e5f690f8fcc5
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863946"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Oznámení a postup pro Visual Studio
##  <a name="BKMK_NotificationSystems"></a> Systémy oznámení  
  
### <a name="overview"></a>Přehled  
 Existuje několik způsobů, jak uživatele informovat, co se děje v sadě Visual Studio týkající se jejich úloh vývoje softwaru.  
  
 Při implementaci jakýkoli druh oznámení:  
  
-   **Snažte se oznámení na minimum** platné číslo. Upozornění by se měly používat pro většinu uživatelů sady Visual Studio nebo na uživatele na konkrétní funkce nebo funkci oblast. Nadměrné používání oznámení může sidetrack uživatele nebo oslabí vnímaná snadnost použití systému.  
  
-   **Ujistěte se nabízí ten samý přehledy, vymazat zprávy** , že uživatel může použít k vyvolání odpovídající kontext složitější rozhodování a provádění dalších akcí.  
  
-   **K dispozici synchronní a asynchronní zprávy odpovídajícím způsobem.** Synchronní oznámení, označení, že něco vyžaduje okamžitou pozornost, třeba když dojde k chybě webové služby nebo kód je vyvolána výjimka. Uživatel by měla vycházet z těchto situací hned způsobem, který vyžaduje svůj vstup, jako například v modální dialogové okno. Asynchronní oznámení jsou ty, které uživatel byste měli znát, ale nebudou požadované k provedení akce s okamžitou, jako je po dokončení operace sestavení nebo nasazení webu dokončí. Tyto zprávy by měl být více okolí a přerušit tok úkolů uživatele.  
  
-   **Použít pouze v případě, že je nutné zabránit uživateli v spustíte další akci modální dialogová okna** před potvrdil zprávy nebo rozhodování zobrazí v dialogovém okně.  
  
-   **Odeberte okolí upozornění, když již nejsou platné.** Uživatel, který chcete oznámení zavřít, pokud se už udělali akce k vyřešení problému, který bylo odesláno oznámení o nevyžadují.  
  
-   **Mějte na paměti, že oznámení může vést k false korelace.** Uživatelé můžou přesvědčeni, že jeden nebo více z jejich akcí spustil oznámení při ve skutečnosti se žádný příčinnou vztah. Možné vymazat ve zprávě oznámení o kontextu, aktivační události a zdroj oznámení.  
  
### <a name="choosing-the-right-method"></a>Výběr správné – metoda  
 Pomocí této tabulce vám pomohou při výběru správnou metodu pro upozornění pro uživatele zprávu.  
  
|Metoda|Použití|Nepoužívejte|  
|------------|---------|----------------|  
|[Dialogová okna modální chybová zpráva](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Použití vyžaduje odpověď uživatele. než budete pokračovat.|Nepoužívejte při není nutné a zablokovat ho přerušit jejich toku. Vyhněte se použití modální dialogová okna, pokud je to možné zobrazit zprávu jiného, teď míň obtěžující způsobem.|  
|[Stavový řádek IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Použijte v případě, že existuje okolí textové informace týkající se stavu procesu.|Nepoužívejte samostatně. Nejlepší používá ve spojení s jiný mechanismus zpětné vazby.|  
|[Vložený informačním panelu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|V panelu nástrojů nebo okna dokumentu pomocí oznámení o průběhu, stav chyby, výsledky a/nebo užitečné informace.|Nepoužívejte Pokud informace nejsou relevantní pro umístění, ve kterém je umístí informační panel.<br /><br /> Nepoužívejte mimo okno dokumentu nebo nástroje.|  
|[Změní se kurzor myši](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Může použít k upozornění, že se proces děje. Také použít k upozornění, že dojde ke změně stavu v myši, například v průběhu, který při přetažení myší do je v určitém režimu, jako je například režim kreslení.|Nepoužívejte krátká probíhající změny, nebo pokud fluttering z kurzor je pravděpodobně (například když vázána k různým částem delší spuštěný proces místo pro celý proces).|  
|[Indikátory průběhu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Použijte, pokud potřebujete informace o průběhu (determinate nebo neurčitý). Existuje řada různých typů indikátor průběhu a pro každou konkrétní použití. Zobrazit [indikátory průběhu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Okno Visual Studio oznámení](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Okno oznámení není veřejně rozšiřitelný. Však se používá ke komunikaci se širokou škálou zprávy o sadě Visual Studio, včetně kritických problémů s licencí a informační upozornění na aktualizace sady Visual Studio nebo k balíčkům.|Nepoužívejte pro další typy oznámení.|  
|[Seznam chyb](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Pokud se problém týká přímo uživatele se vyskytl problém (Chyba/upozornění a informace) aktuálně otevřené řešení, může být nutné provést určitou akci u kódu.<br /><br /> To zahrnuje, například:<br /><br /> -Kompilátoru zpráv (Chyba/upozornění a informace)<br /><br /> -Code Analyzer, diagnostické zprávy o kódu<br /><br /> -Vytvoření zprávy<br /><br /> Může být vhodné pro problémy týkající se soubory projektu nebo řešení, ale nejprve zvažte uvedení Průzkumníku řešení.|Nepoužívejte pro položky, které nemají žádné relace uživatele kódu otevřeného řešení.|  
|Oznámení editoru: žárovky|Použijte, když máte k dispozici k nápravě problému, který existuje v otevřeném souboru opravu.<br /><br /> Mějte na paměti, že žárovky by měl také použít k hostování rychlé akce, které jsou provedeny v kódu uživatele na vyžádání, jako je refaktoring, ale v takovém případě se už nebude "oznámení style."|Nepoužívejte pro položky, které nemají žádné relace na otevřený soubor.|  
|Oznámení editoru: podtržení vlnovkou|Použijte k upozornění uživatele na problém s konkrétní rozsah jejich otevřete kód (například červenou vlnovkou u chyb).|Nepoužívejte pro položky, které nesouvisí se konkrétní rozsah jejich otevřete kód.|  
|[Vložený stavové řádky](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Slouží k zadání stavu týkající se obsahu nebo procesu v rámci kontextu okna konkrétní nástroje, okno dokumentu nebo dialogového okna.|Nepoužívejte pro obecnou oznámení, procesy nebo položky, které nemají žádnou relaci k obsahu v rámci konkrétní okno.|  
|[Oznámení na hlavním panelu Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Slouží k poskytování oznámení pro procesy v režimu out-of-proc nebo doprovodné aplikace.|Nepoužívejte pro oznámení, která jsou relevantní pro rozhraní IDE.|  
|[Bubliny oznámení](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Upozorňovat na vzdálený proces nebo změnit **mimo** rozhraní IDE.|Nepoužívejte jako prostředek pro upozornění uživatele procesy **v rámci** integrovaného vývojového prostředí.|  
  
### <a name="notification-methods"></a>Metody oznámení  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a> Dialogová okna modální chybová zpráva  
 Dialogové okno modální chybová zpráva se používá k zobrazení chybové zprávy, která vyžaduje potvrzení nebo akce uživatele.  
  
 ![Modální zpráva](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 01_ModalErrorMessage")  
  
 **Dialogové okno modální chyba zprávy upozornění uživatele Neplatný připojovací řetězec k databázi**  
  
####  <a name="BKMK_IDEStatusBar"></a> Stavový řádek IDE  
 Pravděpodobnost, že uživatelé Všimněte si, že text stavového řádku souvisí s jejich všeobecnými počítačem a konkrétním prostředí s platformou Windows. Visual Studio zákaznická základna spíše zkušení v obou oblastech, ale ještě nebyl dobře informovaný Windows uživatelé přijít o změny ve stavovém řádku. Proto stavový řádek je nejvhodnější pro informační účely nebo jako redundantní upozornění pro informace zobrazí někde jinde. V dialogovém okně nebo v panelu nástrojů oznámení musí být zadána jakýkoli druh důležité informace, které uživatel musí vyřešit okamžitě.  
  
 Stavový řádek sady Visual Studio je navržena k umožnění pro několik typů informací, který se má zobrazit. Je rozdělený do oblasti pro zpětnou vazbu, návrháři, indikátor průběhu, animace a klienta.  
  
 Oblast zpětnou vazbu a návrháře oblasti jsou vždycky viditelná. Indikátor průběhu a animace oblasti jsou vždy dynamických webů a závislosti na kontextu uživatele. Oblasti návrháře má statické šířku, určuje délku řetězce, které pocházejí z doprovodných prostředku pro textové zprávy. To umožňuje lokalizace pro změnu velikosti šířku bez nutnosti provádění změn kódu. Pro angličtinu šířka tento řetězec je přibližně 220 pixelů. Oblasti návrháře se bude chovat normálně a zpětnou vazbu oblasti absorbují zbývající místo.  
  
 Stavový řádek je také obarveny přidat vizuální přitažlivost a funkční hodnotu tím, že komunikaci různé změny stavu integrovaného vývojového prostředí jako je například, pokud je prostředí IDE v režimu ladění.  
  
 ![Integrované vývojové prostředí stavového řádku změny barev](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 02_IDEStatusBar")  
  
 **Integrované vývojové prostředí stav panelu barev**  
  
####  <a name="BKMK_EmbeddedInfobar"></a> Vložený informačním panelu  
 Informačního panelu je možné v horní části okna dokumentu nebo panel nástrojů informovat uživatele o stavu nebo podmínku. Můžete také nabízí příkazy tak, aby uživatel může mít způsob, jak snadno provést akci. Informační panel je ovládací prvek standardní prostředí. Vyhněte se vytváření vlastní, které se chovají a zobrazují se nekonzistentní s jinými uživateli v integrovaném vývojovém prostředí. Zobrazit [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) implementace podrobnosti a informace o používání.  
  
 ![Vložené informační panel](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 03_EmbeddedInfobar")  
  
 **Informačního panelu vložený v okně dokumentu upozornění uživatele, který rozhraní IDE je v režimu historické ladění a editor nebude odpovídat stejným způsobem jako ve standardním režimu ladění.**  
  
####  <a name="BKMK_MouseCursorChanges"></a> Změní se kurzor myši  
 Při přechodu myší do pomocí barev, které jsou vázané na službu VSColor a jsou již přidruženy kurzor. Změní se kurzor lze použít pro probíhající operaci, jakož i přístupů zóny, kde je uživatel najede myší cíl, který můžete přetáhnout, přetaženy nebo použít k výběru objektu.  
  
 Použijte myš zaneprázdněný/wait pouze v případě, že všechny dostupné čas procesoru musí být vyhrazen pro operaci brání vyjádření jakýkoli další vstup uživatele. Ve většině případů s kvalitně napsané pomocí multithreadingu aplikacemi musí být výjimečných časy, kdy uživatelům bránit v provádění dalších operací.  
  
 Uvědomte si, že změní se kurzor jsou užitečné, protože redundantní startovací informace zobrazí někde jinde. Nespoléhejte na změnu kurzor jako komunikovat s uživateli, zejména v případě, že chcete sdělit něco jediný způsob, jakým je velmi důležité, že uživatel musí vyřešit.  
  
####  <a name="BKMK_NotSysProgressIndicators"></a> Indikátory průběhu  
 Indikátory průběhu jsou důležité pro poskytování zpětné vazby uživatelů během procesů, které trvat déle než několik sekund na dokončení. Mohou být zobrazeny indikátory průběhu na místě (téměř výchozím bodem probíhající akce), vložené stavového řádku, modální dialogové okno nebo stavový řádek sady Visual Studio. Postupujte podle pokynů v [indikátory průběhu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) týkající se jejich použití a implementaci.  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a> Okno Visual Studio oznámení  
 V okně Visual Studio oznámení upozorní vývojáře týkající se licencování, prostředí (Visual Studio), rozšíření a aktualizace. Uživatelé můžou zavřít jednotlivá oznámení nebo můžete rozhodnout ignorovat určité typy oznámení. Seznam ignorovaná oznámení se spravuje **nástroje > Možnosti** stránky.  
  
 Okno oznámení není aktuálně rozšiřitelný.  
  
 ![Okno Visual Studio oznámení](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 06_VSNotificationsWindow")  
  
 **Panel nástrojů Visual Studio oznámení**  
  
####  <a name="BKMK_ErrorList"></a> Seznam chyb  
 Oznámení v seznamu chyb označení chyb a upozornění, která došlo k chybě při kompilaci a proces sestavení a umožňuje uživatelům pro navigaci v kódu pro tento konkrétní kód chyby.  
  
 ![Seznam chyb](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 08_ErrorList")  
  
 **Seznam chyb v sadě Visual Studio**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a> Vložený stavové řádky  
 Protože stavový řádek IDE je dynamická, s jeho kontextu oblast klienta nastavena na aktivního okna dokumentu a informace o aktualizaci v kontextu uživatele a/nebo odpovědí systému, je obtížné udržovat průběžné zobrazení informací nebo přiřadit stav na dlouhodobé asynchronní procesy. Například stavový řádek IDE není vhodná pro oznámení o výsledku testovacího běhu pro více běhů nebo okamžitě jich položku Možnosti. Je důležité zachovat tyto informace o stavu v kontextu okna dokumentu nebo nástroj, kde uživatel provede výběr nebo spustí proces.  
  
 ![Vložený stavový řádek](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 09_EmbeddedStatusBar")  
  
 **Vložený stavového řádku v sadě Visual Studio**  
  
####  <a name="BKMK_WindowsTray"></a> Oznámení na hlavním panelu Windows  
 Hodiny, Windows, se vedle systému oznamovací oblasti na hlavním panelu Windows. Mnoho nástrojů a softwarové součásti poskytují ikony v této oblasti tak, aby uživatel lze získat kontextové nabídky pro celý systém úkoly, jako je změna rozlišení obrazovky nebo získávání aktualizací softwaru.  
  
 Oznámení na úrovni prostředí by měl být prezentované v centru oznámení Visual Studio, není oznamovací oblasti Windows.  
  
####  <a name="BKMK_NotificationBubbles"></a> Bubliny oznámení  
 Oznámení bubliny se mohou objevit jako informační v editoru nebo návrháře nebo jako součást Windows oznamovací oblasti. Uživatel vnímá těchto bublin jako problémy, které můžete vyřešit později, což je výhoda pro Nekritická oznámení. Bubliny jsou nevhodné pro důležité informace, které uživatel musí vyřešit okamžitě. Pokud používáte bubliny oznámení v sadě Visual Studio, postupujte [Windows Desktop pokyny pro oznámení bubliny](/windows/desktop/uxguide/mess-notif).  
  
 ![Bublinu oznámení](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 07_NotificationBubbles")  
  
 **Bublinu oznámení v oblasti oznámení Windows pro Visual Studio**  
  
##  <a name="BKMK_ProgressIndicators"></a> Indikátory průběhu  
  
### <a name="overview"></a>Přehled  
 Indikátory průběhu jsou důležitou součástí systému oznámení pro poskytování zpětné vazby uživatelů. Jejich říct uživatelům, když se dokončí operace a procesy. Indikátor známé typy zahrnují indikátory průběhu, pokryjte kurzory a animovaný ikony. Typ a umístění indikátor průběhu, závisí na kontextu, včetně nahlašována co a jak dlouho proces nebo operace bude trvat dokončení.  
  
#### <a name="factors"></a>Faktory  
 Aby bylo možné zjistit, jaký typ ukazatele je vhodné, je nutné určit následující faktory.  
  
1.  **Časování:** doba operace bude trvat.  
  
2.  **Modalitě:** Určuje, zda je operace modální prostředí (uzamčení uživatelského rozhraní až do dokončení procesu)  
  
3.  **Trvalé nebo přechodné:** konečný výsledek průběh, jestli musí být ohlášené a/nebo zobrazit později  
  
4.  **Determinate/Neurčitost:** Určuje, zda je možné vypočítat čas ukončení operace a průběh  
  
5.  **Umístění obrázku/Textual:** Určuje, zda průběh nebo procesu je zachycená vložené v textu zprávy, nebo konkrétní ovládací prvek, jako je například ovládací prvek stromu  
  
6.  **Vzdálenost:** Určuje, zda by měl být průběh v těsné blízkosti uživatelského rozhraní, která souvisí s. (Například může být ve stavovém řádku, což může být daleko, nebo má být vedle tlačítka, které spustí proces?)  
  
#### <a name="determinate-progress"></a>Determinate průběh  
  
|Typ průběhu|Kdy a jak používat|Poznámky|  
|-------------------|-------------------------|-----------|  
|Indikátor průběhu (determinate)|Očekávané trvání > 5 sekund.<br /><br /> Může zahrnovat textový popis podrobnosti o procesu.|**Není** vložení textu do animace.|  
|Informační panel|Zasílání zpráv přidružené kontextové uživatelského rozhraní. Zobrazit [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Může zahrnovat textový popis podrobnosti o procesu.|**Není** použít více infobars, když budete potřebovat k označení více procesů. Místo toho použijte pruhy skládané průběh.|  
|Okno Výstup|Přechodné oznámení: procesu na úrovni aplikace chcete tomuto uživateli **zkontrolujte** podrobnosti po dokončení.|**Není** použijte, pokud uživatel bude muset později odkazovat na data.|  
|Soubor protokolu|Spárovaná s intransient oznámení v případech, když je potřeba **Uložit** podrobnosti po dokončení.||  
|Stavový řádek|Přechodné oznámení: procesu na úrovni aplikace tohoto uživatele bude **není nutné** podrobnosti po dokončení.<br /><br /> Obsahuje vložené indikátor průběhu.<br /><br /> Může zahrnovat textový popis podrobnosti o procesu.||  
  
#### <a name="indeterminate-progress"></a>Neurčitého průběhu  
  
|Typ průběhu|Kdy a jak používat|Poznámky|  
|-------------------|-------------------------|-----------|  
|Indikátor průběhu (neurčitý)|Očekávané trvání > 5 sekund.<br /><br /> Může zahrnovat textový popis podrobnosti o procesu.|**Není** vložení textu do animace.|  
|Rámeček (animovaný vodorovné tečky)|Latence na server.<br /><br /> Umístit near bodu kontextu horním okraji nadřazeného kontejneru.|**Není** použijte, pokud není nadřazena celého kontejneru.|  
|Číselník (průběh kanál)|Proces přidružené kontextové v uživatelském rozhraní nebo kde místa je potřeba.<br /><br /> Může zahrnovat textový popis podrobnosti o procesu.||  
|Informační panel|Zasílání zpráv přidružené kontextové uživatelského rozhraní. Zobrazit [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Není** použít více infobars, když budete potřebovat k označení více procesů. Místo toho použijte pruhy skládané průběh.|  
|Okno Výstup|Přechodné oznámení: procesu na úrovni aplikace daného uživatele budete chtít **zkontrolujte** podrobnosti po dokončení.|**Není** informace, které je potřeba uchovávat napříč relacemi.|  
|Soubor protokolu|Spárovaná s intransient oznámení v případech, když je potřeba **Uložit** podrobnosti po dokončení.||  
|Stavový řádek|Přechodné oznámení: procesu na úrovni aplikace tohoto uživatele bude **není nutné** podrobnosti po dokončení.<br /><br /> Obsahuje vložené indikátor průběhu.<br /><br /> Může zahrnovat textový popis podrobnosti o procesu.||  
  
### <a name="progress-indicator-types"></a>Typy indikátor průběhu  
  
#### <a name="progress-bars"></a>Indikátory průběhu  
  
##### <a name="indeterminate"></a>Neurčitá  
 ![Indikátor neurčitého průběhu](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 04_Indeterminate")  
  
 **Indikátor neurčitého průběhu**  
  
 "Neurčitý" znamená, že celkový průběh operace nebo proces nelze určit. Pomocí panelů neurčitého průběhu pro operace, které vyžadují neomezené množství času nebo které přistupují k neznámé počet objektů. Používejte textový popis vyvíjený, co se děje. Pomocí vypršení časových limitů přidělit hranice založené na čase operace. Indikátory neurčitého průběhu pomocí animací můžete zobrazit, že je k pokroku, ale neposkytují žádné informace. Neklikejte indikátor neurčitého průběhu založen pouze na případné nedostatky přesnost samostatně.  
  
##### <a name="determinate"></a>Determinate  
 ![Indikátor průběhu determinate](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 05_Determinate")  
  
 **Indikátor průběhu determinate**  
  
 "Determinate" znamená, že operace nebo proces vyžaduje ohraničené množství času, i v případě, že množství času nemůže být předpovězen přesně. Jasně označuje dokončení. Nenechte indikátor průběhu, přejděte na 100 % jeho obsahu, pokud bude dokončena operace. Panel Animace determinate průběhu přesune zleva doprava od 0 do 100 %.  
  
 Indikátor průběhu během operace zpět se nikdy nepřesouvají. Na panelu byste posunout vpřed neustále při zahájení operace a Oslovte 100 % při jeho ukončení. Bod indikátor průběhu je poskytnout uživateli představu, jak dlouho trvá celá operace, bez ohledu na to, kolik kroky souvisejí.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Souběžné vytváření sestav (skládaný indikátory)  
 Pokud operace bude trvat dlouhou dobu – například může sloužit několika minut – a indikátory průběhu dvou, jednu, která zobrazuje celkový průběh operace a druhý pro průběh aktuální krok. Například pokud instalační program je kopírování mnoho souborů, pak jeden indikátor průběhu slouží k označení, jak dlouho trvá celý proces, zatímco druhý můžete určit, jaké je procento aktuálního souboru nebo adresáře kopírování. Neoznamují se více než pěti souběžných operací nebo procesy pomocí pruhy skládané průběh. Pokud máte víc než pěti souběžných operací nebo procesů do sestavy, pomocí modálního dialogového okna tlačítko Storno a sestava podrobnosti o průběhu do okna výstup.  
  
##### <a name="textual-descriptions"></a>Textový popis  
 Použijte textový popis vyvíjený, co se děje a odhadovaný čas dokončení. Pokud je možné určit, jak dlouho bude trvat operace, je vhodnější pro poskytování zpětné vazby může být animovaný ikonu spíše než indikátor průběhu.  
  
 Visual Studio poskytuje standardní průběh panel ve stavovém řádku, který může používat libovolný produkt integrované do sady Visual Studio. Textový popis co se děje, když je animovaný indikátor průběhu je možné aktualizovat text stavového řádku.  
  
#### <a name="other-progress-indicators"></a>Další indikátory průběhu  
  
##### <a name="ants-animated-horizontal-dots"></a>Rámeček (animovaný vodorovné tečky)  
 ![Průběh rámeček](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 01_Ants")  
  
 "Rámeček," animovaný vodorovné tečky, poskytují vizuální informace pro proces neurčitý odezvy serveru.  
  
##### <a name="spinner-progress-ring"></a>Číselník (průběh kanál)  
 ![Průběh rotujícího indikátoru průběhu](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 02_Spinner")  
  
 Číselník (označované také jako "okruhu průběh") je indikátorem neurčitého průběhu primárně používá ve vztahu k kontextové uživatelského rozhraní. V těsné blízkosti jeho související obsah, jako je například textové kategorie záhlaví, zasílání zpráv nebo ovládací prvek zobrazí číselník a požadavek.  
  
##### <a name="cursor-feedback"></a>Zpětná vazba kurzoru  
 Pro operace, které trvat přibližně 2 – 7 sekund poskytnout zpětnou vazbu kurzoru. Obvykle to znamená použití kurzor pro čekání v operačním systému k dispozici. Pokyny najdete v článku na webu MSDN [Cursors.Wait vlastnost](/dotnet/api/system.windows.input.cursors.wait).  
  
#### <a name="progress-indicator-locations"></a>Umístění indikátoru průběhu  
  
##### <a name="status-bar"></a>Stavový řádek  
 Stavový řádek poskytuje místo, kde můžete zobrazit zprávy a užitečné informace pro uživatele bez přerušení práce pro uživatele vaší aplikace. Obvykle se zobrazí v dolní části okna, stav průběh bude podokno tip nástroj, který obsahuje zprávu o měřítkem pokroku v kombinaci s panel indikátor průběhu.  
  
 ![Stavový řádek s indikátor průběhu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 03_StatusBarProgressBar")  
  
 **Stavový řádek s indikátor průběhu**  
  
 ![Stavový řádek se zasíláním zpráv](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 04_StatusBarMessage")  
  
 **Stavový řádek s textový popis**  
  
##### <a name="infobar"></a>Informační panel  
 Podobně jako na stavovém řádku informačního panelu poskytuje kontextové oznámení a zasílání zpráv, které může také být párována s typem ukazatele neurčitého průběhu, jako je například indikátor průběhu nebo rotujícího indikátoru průběhu. Informačního panelu by neměl poskytují podrobné úrovni průběh nebo označení determinate průběh. Zobrazit [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Informační panel s zasílání zpráv a indikátor průběhu](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 05_InfoBar")  
  
 **Informační panel s indikátor průběhu a textový popis**  
  
 ![Informační panel uvnitř okna](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 06_InfoBarInWindow")  
  
##### <a name="inline"></a>vložené  
 Označení inline průběhu může být reprezentována jakýkoli z typů zavaděč průběh. Obvykle je indikátor průběhu spojená se zasíláním zpráv, ale to není povinné.  
  
 ![Vložené průběh rotujícího indikátoru průběhu](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 07_InlineSpinner")  
  
 **V kombinaci s textový popis číselník**  
  
 ![Vložené skládaný indikátory průběhu](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 08_InlineStackedProgress")  
  
 **Indikátory průběhu determinate skládaný**  
  
 ![Zasílání zpráv průběhu vložené](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 09_InlineText")  
  
 **Vložený text Průzkumníka serveru: aktualizace...**  
  
##### <a name="tool-windows"></a>Nástroje systému windows  
 Globální průběh údaj představuje indikátor neurčitého průběhu umístěna přímo pod panelu nástrojů.  
  
 ![Globální neurčitého průběhu](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 23_GlobalIndeterminate")  
  
 **Team Explorer globální neurčitého průběhu panelu**  
  
##### <a name="dialogs"></a>Dialogová okna  
 Dialogová okna může obsahovat jakýkoli z typů zavaděč průběh. Indikátory průběhu můžou být párována s zasílání zpráv i v kombinaci s více úrovněmi indikaci průběhu představují detailní a dílčí procesy.  
  
 ![Dialogové okno s více typy indikátor průběhu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 11_Dialog")  
  
 **Visual Studio dialogové okno s souběžných procesů a více typů indikátor průběhu**  
  
 ![Dialogové okno s zasílání zpráv a průběh zavaděč](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 12_Dialog2")  
  
 **Visual Studio dialogové okno s zavaděč průběh a vložených příkazů pro zasílání zpráv**  
  
##### <a name="document-well"></a>Dobře dokumentu  
 Dokument také můžete zobrazit více typů zavaděč průběh v kombinaci s ovládacími prvky.  
  
 ![Zasílání zpráv v dokumentu a průběh](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 13_DocumentWell")  
  
 **Indikátor neurčitého průběhu pod nástrojů**  
  
##### <a name="output-window"></a>Okno Výstup  
 V okně výstupu je vhodný pro zpracování procesu průběh a stav průběžného postupu prostřednictvím vloženého textové zprávy. Měli byste použít stavový řádek spolu s jakékoli vykazování průběhu výstupní okno.  
  
 ![Průběh zasílání zpráv v okně výstupu](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 14_OutputWindow")  
  
 **Výstupní okno se stavem probíhající proces a počkejte zasílání zpráv**  
  
##  <a name="BKMK_Infobars"></a> Infobars  
  
### <a name="overview"></a>Přehled  
 Infobars dát uživateli indikátor blízko bodem jejich pozornost a pomocí ovládacího prvku sdílené informační panel zajišťuje konzistenci v vizuálního vzhledu a interakce.  
  
 ![Infobar](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")  
  
 **Infobars v sadě Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>Vhodné pro použití pro informačního panelu  
  
-   Aby uživatel, avšak důležitou neblokující zpráva relevantní pro aktuální kontext  
  
-   Označuje, že uživatelské rozhraní v určitých stavu nebo podmínku, která provede některé interakce důsledky, jako je například historické ladění  
  
-   Upozornit uživatele, že systém zjistil problémy, například když rozšíření způsobuje problémy s výkonem  
  
-   Poskytuje způsob, jak snadno provedení akce, třeba když se zjistí, že soubor se smíšenými karty a mezery editoru uživateli  
  
##### <a name="do"></a>Proveďte:  
  
-   Text zprávy informačního panelu zachovat krátké a výstižně.  
  
-   Zachovejte text na odkazy a tlačítka stručné.  
  
-   Ujistěte se, že jsou minimální, zobrazující pouze požadované akce, které poskytnete uživatelům možnosti "action".  
  
##### <a name="dont"></a>Ne:  
  
-   Použijte informačního panelu nabízí standardní příkazy, které mají být umístěny do panelu nástrojů.  
  
-   Použijte informačního panelu místo modální dialogové okno.  
  
-   Vytvořte zprávu s plovoucí desetinnou čárkou mimo časové období.  
  
-   Použití více infobars v několika umístěních v rámci stejné období.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Můžete zobrazit více infobars ve stejnou dobu?  
 Ano, můžete zobrazit více infobars ve stejnou dobu. Zobrazí se v první přijde, dřív pořadí s první informační panel zobrazuje v horní a další infobars zobrazující níže.  
  
 Uživateli se zobrazí maximálně tři infobars najednou, po který, pokud další infobars jsou k dispozici, oblast informační panel se stanou posuvný.  
  
### <a name="creating-an-infobar"></a>Vytvoření informačního panelu  
 Informační panel obsahuje čtyři oddíly, zleva doprava:  
  
-   **Ikona:** to je, kde můžete přidávat libovolnou ikonu se má zobrazit pro informační panel, jako je například ikona upozornění.  
  
-   **Text:** přidat, je text k popisu uživatelské scénáře nebo situace, spolu s odkazy v rámci textu, podle potřeby. Nezapomeňte si zachovat stručné text.  
  
-   **Akce:** tento oddíl by měl obsahovat odkazy a tlačítka pro akce, které uživateli umožňuje pořizovat vaše informačním panelu.  
  
-   **Tlačítko Zavřít:** poslední část vpravo může mít tlačítko pro uzavření.  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>Vytváření standardních informační panel ve spravovaném kódu  
 Třída InfoBarModel slouží k vytvoření zdroje dat pro informačního panelu. Použijte jednu z těchto čtyř konstruktory:  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
```  
  
 Tady je příklad, který vytváří InfoBarModel s nějakým text hypertextového odkazu, tlačítko akce a ikonu.  
  
 ![Informační panel s hypertextovým odkazem](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 02_InfobarHyperlink")  
  
```  
var infoBar = new InfoBarModel(  
    textSpans: new[]  
    {  
        new InfoBarTextSpan("This is a "),  
        new InfoBarHyperlink("hyperlink"),  
        new InfoBarTextSpan(" InfoBar.")  
    },  
    actionItems: new[]  
    {  
        new InfoBarButton("Click Me")  
    },  
    image: KnownMonikers.StatusInformation,  
    isCloseButtonVisible: true);  
  
```  
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>Vytvoření standardní informační panel v nativním kódu  
 Implementovat rozhraní The IVsInfoBar negace informačního panelu z nativního kódu.  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Získávání informačního panelu UIElement z informačního panelu  
 Implementace InfoBarModel nebo IVsInfoBar jsou datové modely, které musí být nastavená na prvku UIElement, aby bylo možné zobrazit v uživatelském rozhraní. Objekt SVsInfoBarUIFactory/IVsInfoBarUIFactory službou se dá načíst prvku UIElement.  
  
```  
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)  
{  
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;  
    if (infoBarUIFactory == null)  
    {  
        uiElement = null;  
        return false;  
    }  
  
    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);  
    return uiElement != null;  
}  
```  
  
### <a name="placement"></a>umístění  
 Infobars lze zobrazit v jedné nebo více z následujících umístění:  
  
-   Nástroje systému windows  
  
-   V rámci kartu dokumentu  
  
> [!IMPORTANT]
>  Je možné umístit informačního panelu podávat zprávy o globální kontext. Tím se zobrazí mezi panely nástrojů a dobře dokumentu. To se nedoporučuje, protože to způsobuje problémy s "jump a jerk" rozhraní IDE a mělo by se vyhnout, není-li naprosto nezbytné a vhodné.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Umístění ToolWindowPane informačního panelu  
 Metoda ToolWindowPane.AddInfoBar(IVsInfoBar) slouží k přidání informačního panelu do panelu nástrojů. Toto rozhraní API můžete přidat buď IVsInfoBar (které InfoBarModel je výchozí implementace), nebo IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Uvedení v dokumentu nebo jiné třídy ToolWindowPane informačního panelu  
 Informačního panelu se umístí do jakékoli IVsWindowFrame, pomocí vlastnost VSFPROPID_InfoBarHost zobrazíte IVsInfoBarHost rámce a poté přidejte informační panel UIElement.  
  
```  
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)  
{  
    IVsInfoBarHost infoBarHost;  
    if (TryGetInfoBarHost(frame, out infoBarHost))  
    {  
        infoBarHost.AddInfoBar(uiElement);  
    }  
}  
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)  
{  
    object infoBarHostObj;  
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))  
    {  
        infoBarHost = null;  
        return false;  
    }  
  
    infoBarHost = infoBarHostObj as IVsInfoBarHost;  
    return infoBarHost != null;  
}  
  
```  
  
#### <a name="placing-an-infobar-in-the-main-window"></a>V hlavním okně uvedení informačního panelu  
 Umístit informačního panelu v hlavním okně, použít k získání hlavního okna IVsInfoBarHost VSSPROPID_MainWindowInfoBarHost IVsShell služby a potom k němu přidejte informační panel UIElement.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Poznám, že uživatel provede akci Moje informačním?  
 Ano, vrátíme každá akce, události autorovi informační panel. Pak je až Autor informační panel k akci v integrovaném vývojovém prostředí na základě výběru uživatelem na informačním panelu. Infobars se automaticky odebere z hostitele došlo ke kliknutí na tlačítko, jejichž zavřít, ale další práce je nutná, pokud jiné infobars potřeba odebrat po zavření. Telemetrická data také muset být nezávisle na sobě zapsané podle jednotlivých informační panel.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Příjem událostí informační panel ve třídy ToolWindowPane  
 Třídy ToolWindowPane má dvě události pro infobars. Událost InfoBarClosed je vyvolána při zavření informačního panelu v třídy ToolWindowPane. InfoBarActionItemClicked událost je aktivována, když se klikne na hypertextový odkaz nebo tlačítko uvnitř informační panel.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Přijímání událostí informačním panelu přímo z UIElement  
 IVsInfoBarUIElement.Advise lze použít k přihlášení k odběru událostí přímo z prvku UIElement informačním panelu. Implementace IVsInfoBarUIEvents vám umožní Autor přijímat zavřít a klikněte na události.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a> Chyba ověření  
 Když uživatel zadá informace, které není přijatelné, například když se přeskočila povinné pole nebo data je zadána v nesprávném formátu, je lepší pro ověření pomocí ovládacího prvku nebo zpětnou vazbu v ovládacím prvku místo blokování chybové dialogové okno automaticky otevíraného okna.  
  
### <a name="field-validation"></a>Ověřování polí  
 Ověření pole na formulář se skládá ze tří součástí: ovládací prvek, ikonu a popis. Během několika typy ovládacích prvků může být využit, textové pole se použije jako příklad.  
  
 ![Kontrola polí &#40;prázdné&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 01_FieldValidation")  
  
 Když toto pole je povinné, měl by existovat vodoznak s informacemi o tom text  **\<požadované >** a pozadí pole by měla být světla žlutý (VSColor: `Environment.ControlEditRequiredBackground`) a popředí by měl být šedé (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Pole s popiskem "Povinné" ověření](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 02_FieldValidationRequired")  
  
 Program můžete určit, že je ve stavu *neplatný obsah, zadaný* když fokus se přesune na jiný ovládací prvek nebo když uživatel klikne na tlačítko potvrzení změn [OK] nebo když uživatel uloží dokument nebo formuláře.  
  
 Pokud je určen neplatný stav obsahu, se zobrazí ikona uvnitř ovládacího prvku nebo vedle ní. Popis popisující chybu, kterou by se zobrazit při najetí myší na ikonu nebo ovládací prvek. Kromě toho 1 pixelu ohraničení by se zobrazit kolem ovládacího prvku, který vytváří v neplatném stavu.  
  
 ![Pole Specifikace rozložení ověření](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 03_LayoutSpecs")  
  
 **Specifikace rozložení pro ověřování polí**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Přijatelné variace pro umístění ikony  
 Existuje nespočet výjimečných případů, ve kterých uživatelé musí být informována o chyby ověření. Vzhledem k tomu – typ ovládacího prvku a konfiguraci, uživatelského rozhraní zvolte umístění ikony, která je vhodná pro vaši situaci.  
  
 ![Přijatelné umístění pro umístění ikony](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 04_IconLocation")  
  
 **Přijatelné variace pro umístění ikony ověření pole**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Ověření vyžadující výměnu zpráv pro připojení k serveru nebo sítě  
 V některých případech odezvy serveru je potřeba Ověřte obsah a bylo by potřeba zobrazit průběh uživatelského, ověření a chybové stavy licencí. Následující obrázek znázorňuje příklad tento případ a doporučené uživatelského rozhraní.  
  
 ![Ověření zahrnující odezvy serveru](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 05_RoundTrip")  
  
 **Ověření zahrnující odezvy serveru**  
  
 Všimněte si, že aby mohla pojmout text "Ověřování..." a "Opakování" musí být zadaná dostatek místa k dispozici napravo od ovládacího prvku.  
  
#### <a name="in-place-warning-text"></a>Text upozornění na místě  
 Když je k dispozici pro umístění chybová zpráva blízko ovládacího prvku ve stavu chyby volného místa, je to vhodnější než použít samotný popisek.  
  
 ![V&#45;umístit upozornění](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 06_InPlaceWarning")  
  
 **Text upozornění na místě**  
  
#### <a name="watermarks"></a>Vodoznaky  
 Někdy celý ovládací prvek nebo okna je v chybovém stavu. V takovém případě použijte k označení chyby vodoznak.  
  
 ![Watermark](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")  
  
 **Ověřování polí vodoznak**