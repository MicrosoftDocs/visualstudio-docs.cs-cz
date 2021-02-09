---
title: Oznámení a průběh pro Visual Studio | Microsoft Docs
description: Seznamte se s různými způsoby, jak informovat uživatele o tom, co se děje v aplikaci Visual Studio ohledně jejich úloh vývoje softwaru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bac47ee29029bdcccb5c248bc8e366376b5aed0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931653"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Oznámení a průběh pro Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Systémy oznámení

### <a name="overview"></a>Přehled
 Existuje několik způsobů, jak uživatele informovat o tom, co se děje v aplikaci Visual Studio v souvislosti se svými úlohami vývoje softwaru.

 Při implementaci libovolného typu oznámení:

- **Ponechte počet oznámení na minimální** platné číslo. Oznamovací zprávy by se měly vztahovat na většinu uživatelů sady Visual Studio nebo na uživatele konkrétní funkce nebo oblasti funkcí. Nadměrné používání oznámení může sidetrack uživatele nebo snížit přehlednost tohoto systému.

- **Ujistěte se, že prezentujete jasné, napadnutelné zprávy** , které může uživatel použít k vyvolání příslušného kontextu pro složitější volby a provedení dalších akcí.

- **Správné zobrazení synchronních a asynchronních zpráv.** Synchronní oznámení označují, že něco potřebuje okamžitou pozornost, například když dojde k chybě webové služby nebo když je vyvolána výjimka kódu. Uživatel by měl být informován o těchto situacích hned způsobem, který vyžaduje jejich vstup, například v modálním dialogovém okně. Asynchronní oznámení jsou ta, o kterých by měl uživatel znát, ale nemusí být nutný k okamžitému jednání, například při dokončení operace sestavení nebo dokončení nasazení webu. Tyto zprávy by měly být více okolní a nesmí přerušit tok úkolů uživatele.

- **Modální dialogová okna používejte jenom v případě, že je to nutné, aby uživatel** před potvrzením zprávy nebo rozhodnutím prezentovaný v dialogovém okně přebíral další akce.

- **Odebrat okolní oznámení, pokud už nejsou platná.** Nevyžadují, aby uživatel zavedl oznámení, pokud již učinil akci k vyřešení problému, ke kterému byly upozorněny.

- **Mějte na paměti, že oznámení mohou vést k nepravdivým korelačním relacím.** Uživatelé se mohou domnívat, že jedna nebo více akcí spustilo oznámení, když se ve skutečnosti neobjevila žádná z příčinných vztahů. V oznamovací zprávě o kontextu, triggeru a zdroji oznámení zrušte zaškrtnutí.

### <a name="choosing-the-right-method"></a>Výběr správné metody
 Tato tabulka vám pomůže vybrat správnou metodu upozornění uživatele na vaši zprávu.

|Metoda|Použití|Nepoužívat|
|------------|---------|----------------|
|[Dialogová okna modálních chybových zpráv](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Použijte v případě, že před pokračováním potřebujete odpověď uživatele.|Nepoužívejte, pokud není potřeba zablokovat uživatele a přerušit jeho tok. Nepoužívejte modální dialogová okna, pokud je možné zprávu zobrazit v jiném, méně rušivým způsobem.|
|[Stavový řádek IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Použijte v případě, že se jedná o okolní textové informace týkající se stavu procesu.|Nepoužívejte samostatně. Nejlépe se používá ve spojení s jiným mechanismem zpětné vazby.|
|[Vložený informační panel](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|V okně nástroje nebo okně dokumentu použijte nástroj k upozorňování na průběh, chybový stav, výsledky nebo informace, které lze provést.|Nepoužívejte, pokud informace nejsou relevantní pro umístění, kde se nachází informační panel.<br /><br /> Nepoužívejte mimo okno dokumentu/nástroje.|
|[Změny kurzoru myši](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Dá se použít k upozorňování na to, že proces prochází. Slouží také k oznamování, že došlo ke změně stavu myši, například když probíhá přetažení nebo když se ukazatel myši nachází v určitém režimu, jako je například režim kreslení.|Nepoužívejte pro krátké změny průběhu nebo pokud je fluttering ukazatele pravděpodobná (například při vázání na části delšího spuštěného procesu namísto celého procesu).|
|[Indikátory průběhu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Použijte v případě, že potřebujete nahlásit průběh (buď zrušení ukončení, nebo neurčitý). Existují různé typy ukazatelů průběhu a konkrétní použití pro každý z nich. Zobrazit [indikátory průběhu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)||
|[Okno oznámení sady Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Okno oznámení není veřejně rozšiřitelné. Používá se však ke sdělování řady zpráv o aplikaci Visual Studio, včetně kritických problémů s licencí a informativními oznámeními aktualizací sady Visual Studio nebo balíčků.|Nepoužívejte pro jiné typy oznámení.|
|[Seznam chyb](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Pokud se problém týká přímo k aktuálně otevřenému řešení, které má problém (chyba/upozornění/informace), může být nutné provést akci s kódem.<br /><br /> Patří mezi ně například:<br /><br /> – Zprávy kompilátoru (chyba/upozornění/informace)<br /><br /> – Analyzátor kódu/diagnostické zprávy týkající se kódu<br /><br /> – Zprávy sestavení<br /><br /> Může být vhodné pro problémy související se soubory projektu nebo řešení, ale nejprve zvažte indikaci Průzkumník řešení.|Nepoužívejte pro položky, které nemají žádný vztah k otevřenému kódu řešení uživatele.|
|Oznámení editoru: žárovka|Použijte v případě, že máte k dispozici opravu k nápravě problému, který existuje v otevřeném souboru.<br /><br /> Všimněte si, že žárovka by měla být také používána pro hostování rychlých akcí, které se na vyžádání týkají kódu uživatele, například refaktoringu, ale v takovém případě se nezobrazí "styl oznámení".|Nepoužívejte pro položky, které nemají žádný vztah k otevřenému souboru.|
|Oznámení editoru: vlnovky|Slouží k upozornění uživatele na problém s určitým rozsahem svého otevřeného kódu (například červená vlnovka pro chyby).|Nepoužívejte pro položky, které se nevztahují na konkrétní rozpětí svého otevřeného kódu.|
|[Vložené Stavové řádky](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Slouží k poskytnutí stavu souvisejícího s obsahem nebo procesem v kontextu konkrétního panelu nástrojů, okna dokumentu nebo dialogového okna.|Nepoužívejte pro obecná oznámení produktů, procesy nebo položky, které nemají žádný vztah k obsahu v rámci konkrétního okna.|
|[Oznámení na panelu Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Použijte k obmnožství oznámení pro procesy mimo proc nebo doprovodné aplikace.|Nepoužívejte pro oznámení, která jsou relevantní pro rozhraní IDE.|
|[Bubliny oznámení](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Slouží ke upozorňování na vzdálený proces nebo změnu **mimo** rozhraní IDE.|Nepoužívejte jako způsob upozorňování uživatele na procesy **v rámci** integrovaného vývojového prostředí (IDE).|

### <a name="notification-methods"></a>Metody oznámení

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Dialogová okna modálních chybových zpráv
 Dialogové okno modální chybové zprávy slouží k zobrazení chybové zprávy, která vyžaduje potvrzení nebo akci uživatele.

 ![Modální chybová zpráva](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 – 01_ModalErrorMessage")

 **Dialogové okno modální chybové zprávy upozorňující uživatele na Neplatný připojovací řetězec k databázi**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> Stavový řádek IDE
 Pravděpodobnost, že text stavového řádku je v souvislosti s platformou systému Windows v souvislosti s okolním prostředím počítače a konkrétním prostředím. Základ zákazníka sady Visual Studio je v obou oblastech, a to i v případě, že si uživatelé systému Windows můžou přijít o změny ve stavovém řádku. Proto se stavový řádek nejlépe používá pro informativní účely nebo jako redundantní hromádka pro informace, které jsou uvedeny jinde. Jakýkoli druh důležitých informací, které uživatel musí okamžitě vyřešit, by měl být uveden v dialogovém okně nebo v okně nástroje oznámení.

 Stavový řádek sady Visual Studio je navržen tak, aby umožňoval zobrazení několika typů informací. Je rozdělena do oblastí pro zpětnou vazbu, návrháře, indikátor průběhu, animaci a klienta.

 Oblast pro zpětnou vazbu a oblast návrháře jsou vždy viditelné. Indikátory průběhu a oblasti animace jsou vždy dynamické a na základě kontextu uživatele. Oblast návrháře má statickou šířku určenou délkou řetězce, který je načten z doprovodného prostředku pro textovou zprávu. To umožňuje lokalizaci změnit velikost šířky bez nutnosti změny kódu. V případě angličtiny má šířka tohoto řetězce přibližně 220 pixelů. Oblast návrháře se bude chovat normálně a v oblasti zpětné vazby dojde ke absorbanci zbývajícího místa.

 Na stavovém řádku je také zabarvení pro přidání vizuálního zájmu a funkční hodnoty tím, že komunikují různé změny stavu IDE, například když je IDE v režimu ladění.

 ![Změny barev na stavovém řádku IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 – 02_IDEStatusBar")

 **Barvy stavového řádku IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Vložený informační panel
 Informační panel se dá použít v horní části okna dokumentu nebo nástroje k informování uživatele o stavu nebo stavu. Může také nabízet příkazy, aby uživatel mohl snadno provést akci. Informační panel je standardním ovládacím prvkem prostředí. Vyhněte se vytváření vlastního, který bude fungovat a bude se zobrazovat jako nekonzistentní s ostatními v integrovaném vývojovém prostředí. Podrobnosti o implementaci a pokyny k používání najdete v tématu [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) .

 ![Vložený informační panel](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 – 03_EmbeddedInfobar")

 **Informační panel vložený v okně dokumentu upozorňující uživatele, že rozhraní IDE je v historickém režimu ladění a Editor nebude reagovat stejným způsobem jako v režimu standardního ladění.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Změny kurzoru myši
 Při změně kurzoru myši použijte barvy, které jsou svázané se službou VSColor a jsou již přidruženy k tomuto ukazateli. Změny kurzoru se dají použít k označení probíhající operace a také zón přístupů, kde se uživatel najede myší na cíl, který se dá přetáhnout, přesunout na nebo použít k výběru objektu.

 Použijte ukazatel myši na zaneprázdněné/čekací dobu jenom v případě, že je k dispozici veškerý dostupný čas procesoru pro operaci a zabránit tak uživateli v vyjádření dalšího vstupu. Ve většině případů s dobře zapsanými aplikacemi, které používají multithreading, časy, kdy se uživatelům zabrání v provádění jiných operací, by nemělo být vzácné.

 Pamatujte, že změny kurzoru jsou užitečné pro informace, které jsou k dispozici jinde, jako redundantní hromádka. Nespoléhá se na změnu kurzoru jako jediným způsobem komunikace s uživatelem, zejména když se snažíte sdělit něco, co je důležité, aby uživatel musel adresovat.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Indikátory průběhu
 Indikátory průběhu jsou důležité pro poskytování zpětné vazby uživatelů během procesů, které dokončí více než několik sekund. Indikátory průběhu se můžou zobrazit na místě (v blízkosti bodu spuštění zpracovávané akce), ve vloženém stavovém řádku, v modálním dialogovém okně nebo ve stavovém řádku sady Visual Studio. Postupujte podle pokynů v části [indikátory průběhu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) týkající se jejich použití a implementace.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Okno oznámení sady Visual Studio
 Okno oznámení sady Visual Studio upozorňuje vývojáře na licencování, prostředí (Visual Studio), rozšíření a aktualizace. Uživatelé můžou zavřít jednotlivá oznámení nebo se můžou rozhodnout ignorovat určité typy oznámení. Seznam ignorovaných oznámení se spravuje na stránce **možnosti > nástrojů** .

 Okno oznámení není aktuálně rozšiřitelné.

 ![Okno oznámení sady Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 – 06_VSNotificationsWindow")

 **Okno nástroje oznámení sady Visual Studio**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Seznam chyb
 Oznámení v seznamu chyb indikuje chyby a varování, ke kterým došlo během kompilace nebo procesu sestavení, a umožňuje uživateli přejít v kódu k této chybě konkrétního kódu.

 ![Seznam chyb](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 – 08_ErrorList")

 **Seznam chyb v aplikaci Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Vložené Stavové řádky
 Vzhledem k tomu, že stavový řádek IDE je dynamický, má kontext oblasti klienta nastavené na aktivní okno dokumentu a aktualizuje informace v kontextu uživatele a/nebo systémových odpovědích, je obtížné udržovat průběžné zobrazování informací nebo poskytovat stav dlouhodobých asynchronních procesů. Například stavový řádek IDE není vhodný pro oznámení výsledků testovacího běhu pro vícenásobné spuštění a/nebo okamžitě vhodné výběry položek. Je důležité uchovávat tyto informace o stavu v kontextu dokumentu nebo nástroje, kde uživatel provede výběr nebo spustí proces.

 ![Vložený stavový řádek](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 – 09_EmbeddedStatusBar")

 **Vložený stavový řádek v aplikaci Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Oznámení na panelu Windows
 Oznamovací oblast systému Windows je vedle systémových hodin na hlavním panelu systému Windows. Řada nástrojů a softwarových součástí poskytuje ikony v této oblasti, takže uživatel může získat kontextovou nabídku pro úlohy v rámci systému, jako je například změna rozlišení obrazovky nebo získání aktualizací softwaru.

 Oznámení na úrovni prostředí by se měla nacházet v centru oznámení sady Visual Studio, nikoli v oznamovací oblasti systému Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Bubliny oznámení
 Bubliny oznámení se mohou zobrazovat jako informativní v editoru nebo Návrháři nebo jako součást oznamovací oblasti systému Windows. Uživatel tyto bubliny sestaví jako problémy, které mohou později vyřešit, což je výhodou pro Nekritická oznámení. Bubliny jsou nevhodné pro kritické informace, které uživatel musí hned vyřešit. Pokud používáte bubliny oznámení v aplikaci Visual Studio, postupujte podle [pokynů pro stolní počítače Windows pro oznamovací bubliny](/windows/desktop/uxguide/mess-notif).

 ![Bublina oznámení](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 – 07_NotificationBubbles")

 **Bublina oznámení v oznamovací oblasti systému Windows používané pro Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Indikátory průběhu

### <a name="overview"></a>Přehled
 Indikátory průběhu jsou důležitou součástí systému oznámení pro poskytování zpětné vazby uživatele. Upozorní uživatele, když budou dokončeny procesy a operace. Mezi známé typy ukazatelů patří indikátory průběhu, otáčející se kurzory a animované ikony. Typ a umístění indikátoru průběhu závisí na kontextu, včetně informací o tom, co je hlášeno a jak dlouho bude trvat dokončení procesu nebo operace.

#### <a name="factors"></a>Skutečnosti
 Aby bylo možné určit, který typ ukazatele je vhodný, je nutné určit následující faktory.

1. **Časování:** doba trvání operace

2. **Modální způsob:** zda je operace pro prostředí modální (uzamkne uživatelské rozhraní, dokud se proces nedokončí)

3. **Trvalé/přechodné:** , zda konečný výsledek průběhu musí být uveden a/nebo zobrazitelný později

4. Zrušení **ukončení/neurčité:** určuje, jestli se dá vypočítat čas ukončení operace a průběh.

5. **Graphic/textové umístění:** určuje, zda je průběh nebo proces zachycen vloženě, v těle zprávy nebo konkrétní ovládací prvek, jako je například ovládací prvek stromu.

6. **Blízkost:** určuje, jestli se má průběh uzavřít do blízkosti uživatelského rozhraní, ke kterému se vztahuje. (Například může být ve stavovém řádku, který může být daleko pryč nebo musí být poblíž tlačítka, které proces spustil?)

#### <a name="determinate-progress"></a>Průběh zrušení ukončení

|Typ průběhu|Kdy a jak používat|Poznámky|
|-------------------|-------------------------|-----------|
|Indikátor průběhu (zrušení ukončení)|Očekávaná doba trvání >5 sekund.<br /><br /> Může obsahovat textový popis podrobností o procesu.|**Nevkládat text** do animace|
|Řádku|Zasílání zpráv přidružených k kontextovému uživatelskému rozhraní Viz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Může obsahovat textový popis podrobností o procesu.|Pokud potřebujete označit více procesů, **nepoužívejte více** infobars. Místo toho použijte skládané indikátory průběhu.|
|Okno Výstup|Přechodné oznámení: proces na úrovni aplikace, který uživatel potřebuje ke **kontrole** podrobností po dokončení.|**Nepoužívejte,** Pokud bude uživatel později potřebovat odkaz na data.|
|Soubor protokolu|Spárováno s nepřechodným oznámením v případech, kdy je důležité **Uložit** podrobnosti po dokončení.||
|Stavový řádek|Přechodné oznámení: proces na úrovni aplikace, který uživatel nebude po dokončení **potřebovat** podrobnosti.<br /><br /> Zahrnuje vložený indikátor průběhu.<br /><br /> Může obsahovat textový popis podrobností o procesu.||

#### <a name="indeterminate-progress"></a>Neurčitý průběh

|Typ průběhu|Kdy a jak používat|Poznámky|
|-------------------|-------------------------|-----------|
|Indikátor průběhu (neurčitelné)|Očekávaná doba trvání >5 sekund.<br /><br /> Může obsahovat textový popis podrobností o procesu.|**Nevkládat text** do animace|
|ANTS (animované vodorovné tečky)|Vykolete cestu k serveru.<br /><br /> Umístěn poblíž bodu kontextu mezi horním prvkem nadřazeného kontejneru.|**Nepoužívejte,** Pokud není nadřazený celým kontejnerem.|
|Číselník (kruh průběhu)|Proces přidružený k kontextovému uživatelskému rozhraní nebo místa, kde je důležité zvážit.<br /><br /> Může obsahovat textový popis podrobností o procesu.||
|Řádku|Zasílání zpráv přidružených k kontextovému uživatelskému rozhraní Viz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|Pokud potřebujete označit více procesů, **nepoužívejte více** infobars. Místo toho použijte skládané indikátory průběhu.|
|Okno Výstup|Přechodné oznámení: proces na úrovni aplikace, který uživatel bude chtít **zkontrolovat** podrobnosti po dokončení.|**Nepoužívejte pro** informace, které je potřeba uchovat napříč relacemi.|
|Soubor protokolu|Spárováno s nepřechodným oznámením v případech, kdy je důležité **Uložit** podrobnosti po dokončení.||
|Stavový řádek|Přechodné oznámení: proces na úrovni aplikace, který uživatel nebude po dokončení **potřebovat** podrobnosti.<br /><br /> Zahrnuje vložený indikátor průběhu.<br /><br /> Může obsahovat textový popis podrobností o procesu.||

### <a name="progress-indicator-types"></a>Typy ukazatelů průběhu

#### <a name="progress-bars"></a>Indikátory průběhu

##### <a name="indeterminate"></a>Definované
 ![Neurčitý indikátor průběhu](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 – 04_Indeterminate")

 **Neurčitý indikátor průběhu**

 Neurčitý znamená celkový průběh operace nebo procesu nelze určit. Použijte neurčité indikátory průběhu pro operace, které vyžadují neohraničený čas nebo které přistupují k neznámému počtu objektů. Použijte textový popis, abyste mohli doprovázet, co se děje. Pomocí časových limitů můžete přidělit meze operacím založeným na čase. Neurčité ukazatele průběhu používají animace k zobrazení tohoto průběhu, ale neposkytují žádné další informace. Nevybírejte indikátor průběhu pouze na základě možného nedostatku samotného typu.

##### <a name="determinate"></a>Zrušit ukončení
 ![Indikátor průběhu zrušení ukončení](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 – 05_Determinate")

 **Indikátor průběhu zrušení ukončení**

 Možnost "Zrušit ukončení" znamená, že operace nebo proces vyžaduje určenou dobu, a to i v případě, že tuto dobu nelze přesně předpovědět. Jasně uveďte dokončení. Nenechte ukazatel průběhu přejít na 100%, pokud se operace nedokončí. Animace indikátoru indikátoru ukončení se pohybuje zleva doprava z 0 do 100%.

 Nikdy během operace Nepřesouvat ukazatel průběhu zpět. Čára by se měla při zahájení operace a dosažení 100% po skončení přesunout do budoucna. Hlavním bodem průběhu je poskytnout uživateli představu o tom, jak dlouho celá operace trvá, bez ohledu na to, kolik kroků se týká.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Souběžné generování sestav (skládané indikátory průběhu)
 Bude-li operace trvat dlouhou dobu, například několik minut, mohou být použity dva indikátory průběhu, jeden, který ukazuje celkový průběh operace a druhý pro průběh aktuálního kroku. Například pokud instalační program kopíruje mnoho souborů, pak se jeden indikátor průběhu dá použít k určení, jak dlouho celý proces trvá, zatímco druhý může indikovat, jaké procento aktuálního souboru nebo adresáře se právě kopíruje. Nesestavujte více než pět souběžných operací nebo procesů pomocí skládaných pruhů průběhu. Pokud máte více než pět souběžných operací nebo procesů k sestavování, použijte modální dialogové okno s tlačítkem Storno a sestavte podrobnosti o průběhu na okno Výstup.

##### <a name="textual-descriptions"></a>Textové popisy
 Použijte textový popis k naplnění toho, co se děje, a odhadovaný čas dokončení. Pokud není možné určit, jak dlouho bude operace trvat, může být lepší volbou pro poskytnutí zpětné vazby animovaná ikona místo indikátoru průběhu.

 Visual Studio poskytuje standardní indikátor průběhu ve stavovém řádku, který může být použit jakýmkoli produktem integrovaným do sady Visual Studio. V případě textových popisů toho, co se děje, když je indikátor průběhu animovaný, se text stavového řádku dá aktualizovat.

#### <a name="other-progress-indicators"></a>Další indikátory průběhu

##### <a name="ants-animated-horizontal-dots"></a>ANTS (animované vodorovné tečky)
 ![ANTS průběhu](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 – 01_Ants")

 "ANTS", animované horizontální tečky, poskytují vizuální odkaz na neurčitý proces serveru Round-Trip.

##### <a name="spinner-progress-ring"></a>Číselník (kruh průběhu)
 ![Číselník průběhu](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 – 02_Spinner")

 Číselník (označuje se také jako "okruh průběhu") je neurčitý indikátor průběhu, který se primárně používá ve vztahu k kontextovému uživatelskému rozhraní. Zobrazí číselník v blízkosti blízkosti jeho souvisejícího obsahu, jako je například textové záhlaví kategorie, zasílání zpráv nebo řízení.

##### <a name="cursor-feedback"></a>Váš názor na kurzor
 Pro operace, které trvá mezi 2-7 sekundami, zadejte zpětnou vazbu kurzoru. Obvykle to znamená, že se používá čekací ukazatel poskytovaný operačním systémem. Pokyny najdete v článku [vlastnosti čekání](/dotnet/api/system.windows.input.cursors.wait)na webu MSDN.

#### <a name="progress-indicator-locations"></a>Umístění ukazatelů průběhu

##### <a name="status-bar"></a>Stavový řádek
 Stavový řádek poskytuje aplikaci místo pro zobrazení zpráv a užitečných informací uživateli, aniž by přerušil práci uživatele. Stav pro průběh se obvykle zobrazuje v dolní části okna s popisem nástroje, který obsahuje zprávu o míře průběhu v kombinaci s indikátorem indikátoru průběhu.

 ![Stavový řádek s indikátorem průběhu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 – 03_StatusBarProgressBar")

 **Stavový řádek s indikátorem průběhu**

 ![Stavový řádek s zasíláním zpráv](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 – 04_StatusBarMessage")

 **Stavový řádek s textovým popisem**

##### <a name="infobar"></a>Řádku
 Podobně jako stavový řádek, informační panel poskytuje kontextové oznámení a zasílání zpráv, které lze také spárovat s neurčitými indikátory průběhu, jako je indikátor průběhu nebo číselník. Informační panel by neměl poskytovat podrobný průběh detailní úrovně nebo ukončení indikace průběhu. Viz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Informační panel s indikátorem průběhu a zasíláním zpráv](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 – 05_InfoBar")

 **Informační panel s ukazatelem průběhu a textovým popisem**

 ![Informační panel uvnitř okna](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 – 06_InfoBarInWindow")

##### <a name="inline"></a>Přiřazený
 Vložené indikace průběhu může představovat libovolný typ zavaděče průběhu. Indikátor průběhu se obvykle spáruje s zasíláním zpráv, ale to není požadavek.

 ![Vnitřní číselník průběhu](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 – 07_InlineSpinner")

 **Číselník v kombinaci s textovým popisem**

 ![Vložené skládané indikátory průběhu](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 – 08_InlineStackedProgress")

 **Zrušit ukončení skládaných pruhů průběhu**

 ![Vkládání zpráv o průběhu](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 – 09_InlineText")

 **Průzkumník serveru vložený text: Probíhá aktualizace...**

##### <a name="tool-windows"></a>Okna nástrojů
 Globální indikace průběhu je reprezentován neurčitým indikátorem průběhu umístěným přímo pod panelem nástrojů.

 ![Globální neurčitý indikátor průběhu](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 – 23_GlobalIndeterminate")

 **Team Explorer globální neurčitý indikátor průběhu**

##### <a name="dialogs"></a>Dialogy
 Dialogová okna mohou obsahovat libovolný typ zavaděče průběhu. Indikátory průběhu se můžou párovat se zasíláním zpráv a také kombinovat s několika úrovněmi průběhu indikace, aby představovaly podrobné a dílčí procesy.

 ![Dialog s více typy indikátor průběhu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 – 11_Dialog")

 **Dialog sady Visual Studio se souběžnými procesy a různými typy ukazatelů průběhu**

 ![Dialogové okno s zavaděčem průběhu a zasíláním zpráv](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 – 12_Dialog2")

 **Dialog sady Visual Studio se zavaděčem průběhu a vloženými příkazy zasílání zpráv**

##### <a name="document-well"></a>Dobře zdokumentovat
 Dokumentace dokumentu může v kombinaci s ovládacími prvky Zobrazit více typů zavaděče průběhu.

 ![Zpráva o průběhu v dokumentu](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 – 13_DocumentWell")

 **Neurčitý indikátor průběhu pod panelem nástrojů**

##### <a name="output-window"></a>Okno Výstup
 Okno výstup je vhodné pro zpracování průběhu procesu a průběžného stavu postupu prostřednictvím vloženého textového zasílání zpráv. Měli byste použít stavový řádek spolu s jakýmkoli vytvářením sestav o průběhu výstupního okna.

 ![Doručování zpráv o průběhu okno Výstup](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 – 14_OutputWindow")

 **okno Výstup s probíhajícím stavem procesu a čekáním na zprávy**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Infobars

### <a name="overview"></a>Přehled
 Infobars uživateli poskytnout ukazatel blízko ke svému bodu pozornosti a použití sdíleného informačního panelu zajišťuje konzistenci vizuálního vzhledu a interakce.

 ![Řádku](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904 – 01_Infobar")

 **Infobars v aplikaci Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Vhodná použití pro informační panel

- Pokud chcete uživateli poskytnout neblokující, ale důležitou zprávu, která je relevantní pro aktuální kontext.

- Pro indikaci, že uživatelské rozhraní je v určitém stavu nebo stavu, který přináší některé důsledky interakce, jako je například historické ladění

- Upozorní uživatele, že systém zjistil problémy, například když rozšíření způsobuje problémy s výkonem.

- Aby mohl uživatel poskytnout způsob, jak snadno provést akci, například když Editor zjistí, že soubor obsahuje smíšené karty a mezery

##### <a name="do"></a>Postup

- Ponechte text zprávy na informačním panelu krátký a k bodu.

- Ponechte text na odkazech a tlačítkách stručně.

- Ujistěte se, že možnosti "akce", které uživatelům poskytnete, jsou minimální a zobrazují se jenom požadované akce.

##### <a name="dont"></a>Ne:

- Pomocí informačního panelu můžete nabízet standardní příkazy, které by měly být umístěny na panelu nástrojů.

- Místo modálního dialogu použijte informační panel.

- Vytvoří plovoucí zprávu mimo okno.

- V jednom okně použijte více infobars v několika umístěních.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Může se ve stejnou dobu zobrazovat více infobars?
 Ano, více infobars se může zobrazit ve stejnou dobu. Budou se zobrazovat v prvním řádku s prvními dodanými informacemi a prvním zobrazeným informačním panelem, který ukazuje nahoře a další infobars.

 Uživatel uvidí maximálně tři infobars v čase, a pokud bude k dispozici více infobars, bude se oblast informačního panelu zobrazovat jako posouvatelné.

### <a name="creating-an-infobar"></a>Vytvoření informačního panelu
 Informační panel obsahuje čtyři části zleva doprava:

- **Ikona:** Do tohoto místa přidáte libovolné ikony, které byste chtěli zobrazit pro informační panel, jako je například ikona upozornění.

- **Text:** Můžete přidat text popisující scénář/situaci, kdy se uživatel nachází v, spolu s odkazy v textu, pokud je to potřeba. Nezapomeňte text stručně zachovat.

- **Akce:** Tato část by měla obsahovat odkazy a tlačítka pro akce, které může uživatel provést na svém informačním panelu.

- **Tlačítko Zavřít:** Poslední část vpravo může obsahovat tlačítko Zavřít.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Vytvoření standardního informačního panelu ve spravovaném kódu
 Třídu InfoBarModel lze použít k vytvoření zdroje dat pro informační panel. Použijte jeden z těchto čtyř konstruktorů:

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

 Tady je příklad, který vytvoří InfoBarModel s nějakým textem s hypertextovým odkazem, tlačítkem akce a ikonou.

 ![Informační panel s hypertextovým odkazem](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 – 02_InfobarHyperlink")

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Vytvoření standardního informačního panelu v nativním kódu
 Implementujte rozhraní IVsInfoBar, aby poskytoval informační panel z nativního kódu.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Získání prvku UIElement z informačního panelu
 Implementace InfoBarModel nebo IVsInfoBar jsou datové modely, které musí být přeměněny do prvku UIElement, aby je bylo možné zobrazit v uživatelském rozhraní. UIElement lze načíst pomocí služby objekt svsinfobaruifactory/IVsInfoBarUIFactory.

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

### <a name="placement"></a>Umístění
 Infobars může být zobrazeno v jednom nebo několika následujících umístěních:

- Okna nástrojů

- Na kartě dokumentu

> [!IMPORTANT]
> Je možné umístit informační panel a poskytnout zprávu o globálním kontextu. To by se mohlo zobrazit mezi panely nástrojů a dokumentem dokumentu. To se nedoporučuje, protože způsobuje problémy se "skokem a Jerk" prostředí IDE a mělo by se jim vyhýbat, pokud není nezbytně nutné a vhodné.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Vložení informačního panelu do třídy ToolWindowPane
 Metoda třídy ToolWindowPane. AddInfoBar (IVsInfoBar) se dá použít k přidání informačního panelu do okna nástroje. Toto rozhraní API může přidat IVsInfoBar (z kterého InfoBarModel je výchozí implementace) nebo IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Vložení informačního panelu do dokumentu nebo jiného typu než třídy ToolWindowPane
 Chcete-li umístit informační panel do libovolného metoda IVsWindowFrame, použijte vlastnost VSFPROPID_InfoBarHost pro získání IVsInfoBarHost pro rámec a pak přidejte prvek UIElement informačního panelu.

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

#### <a name="placing-an-infobar-in-the-main-window"></a>Umístění informačního panelu do hlavního okna
 Pokud chcete umístit informační panel do hlavního okna, pomocí VSSPROPID_MainWindowInfoBarHost služby IVsShell Získejte IVsInfoBarHost hlavního okna a potom do něj přidejte prvek UIElement informačního panelu.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Dozvíi se, že uživatel provede akci na svém informačním panelu?
 Ano, vrátíme všechny akce události pro autora informačního panelu. Na základě výběru uživatele na informačním panelu se pak až do autora informačního panelu provede akce v integrovaném vývojovém prostředí. Infobars se automaticky odebere z hostitele, u kterého se kliknulo na tlačítko Zavřít, ale pokud je potřeba po zavření další Infobars odebrat, vyžaduje se další práce. Telemetrii je také potřeba protokolovat nezávisle na každém informačním panelu.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Příjem událostí informačního panelu v třídy ToolWindowPane
 Třídy ToolWindowPane má dvě události pro infobars. Událost InfoBarClosed se vyvolá, když se zavře informační panel v třídy ToolWindowPane. Událost InfoBarActionItemClicked se vyvolá při kliknutí na hypertextový odkaz nebo tlačítko uvnitř informačního panelu.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Příjem událostí informačního panelu přímo z prvku UIElement
 IVsInfoBarUIElement. Advise se dá použít k přihlášení k odběru událostí přímo z prvku UIElement informačního panelu. Implementace IVsInfoBarUIEvents umožní autorovi přijímat události zavření a kliknutí.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> Chyba ověřování
 Pokud uživatel zadá informace, které nejsou přijatelné, například když je povinné pole vynecháno nebo když jsou data zadána v nesprávném formátu, je vhodnější použít ověřování ovládacího prvku nebo zpětné vazby v ovládacím prvku namísto použití blokujícího chybového dialogového okna.

### <a name="field-validation"></a>Ověřování polí
 Ověřování formuláře a pole se skládá ze tří součástí: ovládacího prvku, ikony a popisu tlačítka. I když lze použít několik typů ovládacích prvků, textové pole bude použito jako příklad.

 ![Ověřování polí &#40;prázdné&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 – 01_FieldValidation")

 Pokud je pole povinné, měl by být uveden text vodoznaku **\<Required>** a pozadí pole by mělo být světle žluté (VSColor: `Environment.ControlEditRequiredBackground` ) a popředí by mělo být šedé (VSColor: `Environment.ControlEditRequiredHintText` ):

 ![Ověřování pole s popiskem "požadováno"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 – 02_FieldValidationRequired")

 Program může určit, že se ovládací prvek nachází ve stavu *neplatného obsahu* , a to buď při přesunutí fokusu na jiný ovládací prvek, nebo když uživatel klikne na tlačítko pro potvrzení [OK] nebo když uživatel dokument nebo formulář uloží.

 Pokud je určena neplatný stav obsahu, zobrazí se ikona v ovládacím prvku nebo pouze vedle ní. Popis, který popisuje chybu, by se měl zobrazit při najetí myší buď na ikonu, nebo na ovládací prvek. Kromě toho by se mělo kolem ovládacího prvku, který vytváří neplatný stav, zobrazit ohraničení o velikosti 1 pixelu.

 ![Specifikace rozvržení pro ověřování polí](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 – 03_LayoutSpecs")

 **Specifikace rozložení pro ověřování polí**

#### <a name="acceptable-variations-for-icon-location"></a>Přijatelné odchylky pro umístění ikony
 Existují dlouhé jedinečné případy, kdy si uživatelé musí být informováni o chybách ověřování. V úvahách o typu ovládacího prvku a konfiguraci uživatelského rozhraní vyberte umístění ikon odpovídající vaší situaci.

 ![Přijatelná umístění pro umístění ikony](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 – 04_IconLocation")

 **Přijatelné odchylky pro umístění ikon ověřování polí**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Ověření požadavku na připojení k serveru nebo síťovému připojení
 V některých případech se k ověření obsahu vyžaduje zpáteční cesta k serveru a je důležité zobrazit stav uživatele, ověřit a chybové stavy. Následující obrázek ukazuje příklad tohoto případu a doporučené uživatelské rozhraní.

 ![Ověření, které zahrnuje zpáteční cestu k serveru](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 – 05_RoundTrip")

 **Ověření, které zahrnuje zpáteční cestu k serveru**

 Všimněte si, že musí být k dispozici dostatečný prostor napravo od ovládacího prvku, aby bylo možné přizpůsobit "ověřování...". a "opakovat" text.

#### <a name="in-place-warning-text"></a>Místní výstražný text
 Pokud je k dispozici místo pro vložení chybové zprávy blízko ovládacího prvku ve stavu chyby, je vhodnější použít pouze popisek.

 ![&#45;upozornění na místo](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 – 06_InPlaceWarning")

 **Místní výstražný text**

#### <a name="watermarks"></a>Vodoznaky
 Někdy je celý ovládací prvek nebo okno v chybovém stavu. V takovém případě k indikaci chyby použijte vodoznak.

 ![Meze](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905 – 07_Watermark")

 **Ověření pole meze**
