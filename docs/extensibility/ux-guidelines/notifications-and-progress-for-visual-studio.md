---
title: Oznámení a průběh Visual Studio | Microsoft Docs
description: Seznamte se s několika způsoby, jak informovat uživatele o tom, co se Visual Studio v souvislosti s jejich úkoly vývoje softwaru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 994a315d04b06d1998a8c8e0c4291b6a4c54cb61
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902238"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Oznámení a průběh pro Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Systémy oznámení

### <a name="overview"></a>Přehled
 Existuje několik způsobů, jak informovat uživatele o tom, co se děje Visual Studio svých úlohách vývoje softwaru.

 Při implementaci jakéhokoli druhu oznámení:

- **Udržte počet oznámení na minimální efektivní** číslo. Zprávy s oznámením by se měly vztahovat Visual Studio uživatelů nebo uživatelů konkrétní oblasti funkcí. Nadměrné používání oznámení může uživatele sledovat na straně uživatele nebo zmenšovat vnímané snadné používání systému.

- **Ujistěte se, že prezentujete** jasné a použitelné zprávy, které může uživatel použít k vyvolání vhodného kontextu pro provádění složitějších voleb a provádění dalších akcí.

- **Vhodně prezentovat synchronní a asynchronní zprávy.** Synchronní oznámení indikují, že něco vyžaduje okamžitou pozornost, například když dojde k chybě webové služby nebo je vyvolána výjimka kódu. Uživatel by měl být o těchto situacích hned informován způsobem, který vyžaduje zadání, například v modálním dialogovém okně. Asynchronní oznámení jsou ta, o které by měl uživatel vědět, ale nemusí okamžitě jednat, například po dokončení operace sestavení nebo dokončení nasazení webu. Tyto zprávy by měly být více ambientní a neměly by přerušovat tok úlohy uživatele.

- **Modální dialogy používejte jenom** v případě potřeby, abyste uživateli zabránili v provedení dalších akcí před potvrzením zprávy nebo provedením rozhodnutí v dialogovém okně.

- **Odeberte ambientní oznámení, pokud už nejsou platná.** Nepožadovat, aby uživatel zamítl oznámení, pokud už udělal akci k řešení problému, na který byl upozorněn.

- **Uvědomte si, že oznámení mohou vést k nepravdivým korelacím.** Uživatelé se můžou domnívát, že jedna nebo více svých akcí aktivoval oznámení, když ve skutečnosti nebyl žádný kauzální vztah. Ve zprávě s oznámením o kontextu, triggeru a zdroji oznámení buďte jasné.

### <a name="choosing-the-right-method"></a>Výběr správné metody
 Tato tabulka vám pomůže vybrat správnou metodu, která uživatele upozorní na vaši zprávu.

|Metoda|Použití|Nepou ít|
|------------|---------|----------------|
|[Modální dialogová okna s chybovou zprávou](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Používá se, když se vyžaduje odpověď uživatele, než budete pokračovat.|Nepoužívejte ho, pokud není nutné blokovat uživatele a přerušit jeho tok. Nepoužívejte modální dialogová okna, pokud je možné zobrazit zprávu jiným, méně rušiivým způsobem.|
|[Stavový řádek integrovaného vývojového prostředí (IDE)](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Používá se v případě, že jsou k dispozici ambientní textové informace týkající se stavu procesu.|Nepoužívejte samostatně. Nejlepší použití ve spojení s jiným mechanismem zpětné vazby.|
|[Vložený informační panel](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|V okně nástroje nebo v okně dokumentu použijte k upozornění na průběh, stav chyby, výsledky a/nebo informace s akcemi.|Nepoužívejte, pokud informace nejsou relevantní pro umístění, kde je informační panel umístěný.<br /><br /> Nepoužívejte mimo okno dokumentu nebo nástroje.|
|[Změny kurzoru myši](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Lze použít k upozornění, že proces se děje. Používá se také k upozornění, že v myši došlo ke změně stavu, například když probíhá přetahování nebo že kurzor myši je v určitém režimu, například v režimu kreslení.|Nepoužívejte pro krátké změny průběhu nebo pokud je fluttering kurzoru pravděpodobný (například při svázání s částmi déle běžícího procesu místo s celým procesem).|
|[Indikátory průběhu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Tuto možnost použijte, když potřebujete nahlásit průběh (určení nebo neurčité). Pro každý z nich existuje celá řada typů indikátorů průběhu a jejich konkrétní využití. Viz [indikátory průběhu.](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)||
|[Visual Studio oznámení](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Okno Oznámení není veřejně rozšiřitelné. Používá se ale ke komunikaci řady zpráv o službě Visual Studio, včetně kritických problémů s licencí a informačních oznámení o aktualizacích Visual Studio nebo balíčkům.|Nepoužívejte pro jiné typy oznámení.|
|[Seznam chyb](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Pokud problém souvisí přímo s aktuálně otevřeným řešením uživatele (chyba, upozornění nebo informace), možná bude muset s kódem provést akci.<br /><br /> Patří sem například:<br /><br /> – Zprávy kompilátoru (chyba, upozornění nebo informace)<br /><br /> – Zprávy analyzátoru kódu / diagnostické zprávy o kódu<br /><br /> – Vytváření zpráv<br /><br /> Může být vhodná pro problémy související se soubory projektu nebo řešení, ale nejprve Průzkumník řešení indikaci.|Nepoužívejte pro položky, které nemají žádný vztah k otevřenému kódu řešení uživatele.|
|Oznámení editoru: Žárovka|Tuto možnost použijte, když máte k dispozici opravu, která napraví problém, který existuje v otevřeném souboru.<br /><br /> Všimněte si, že žárovka by se měla použít také pro hostování rychlých akcí provedených na vyžádání v kódu uživatele, jako jsou refaktoringy, ale v takovém případě se nezobrazí jako "styl oznámení".|Nepoužívejte pro položky, které nemají žádný vztah k otevřenému souboru.|
|Oznámení editoru: Squiggles|Slouží k upozorní uživatele na problém s konkrétním rozsahem jeho otevřeného kódu (například červenouquiggle pro chyby).|Nepoužívejte pro položky, které nesouvisí s konkrétním rozsahem jejich otevřeného kódu.|
|[Vložené stavové pruhy](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Slouží k poskytování stavu souvisejícího s obsahem nebo procesem v kontextu konkrétního okna nástroje, okna dokumentu nebo dialogového okna.|Nepoužívejte pro obecná oznámení produktu, procesy nebo položky, které nemají žádný vztah k obsahu v konkrétním okně.|
|[Oznámení na hlavním panelu Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Slouží k oznamování pro neschůdné procesy nebo doprovodné aplikace.|Nepoužívejte pro oznámení, která jsou relevantní pro integrované vývojové prostředí (IDE).|
|[Bubliny oznámení](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Slouží k upozornění na vzdálený proces nebo ke změně **mimo** integrované vývojové prostředí(IDE).|Nepoužívejte jako způsob, jak upozornit uživatele na procesy v **rámci integrovaného vývojového** prostředí.|

### <a name="notification-methods"></a>Metody oznámení

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Modální dialogová okna s chybovou zprávou
 Modální dialogové okno chybové zprávy slouží k zobrazení chybové zprávy, která vyžaduje potvrzení nebo akci uživatele.

 ![Modální chybová zpráva](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 – 01_ModalErrorMessage")

 **Modální dialogové okno s chybovou zprávou upozorující uživatele na neplatný připojovací řetězec pro databázi**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> Stavový řádek integrovaného vývojového prostředí (IDE)
 Pravděpodobnost, že si uživatelé všimne textu stavového řádku, koreluje s prostředím celého počítače a konkrétním prostředím s platformou Windows. Zákaznická Visual Studio má tendenci být zkušení v obou oblastech, i když i zkušení uživatelé Windows můžou ve stavovém řádku promeškat změny. Proto se stavový řádek nejlépe používá pro informační účely nebo jako redundantní podnět k informacím prezentovaných jinde. Jakýkoli druh důležitých informací, které musí uživatel okamžitě přeložit, by měl být k dispozici v dialogovém okně nebo v okně nástroje Oznámení.

 Stavový Visual Studio je navržený tak, aby umožnil zobrazení několika typů informací. Je rozdělený do oblastí pro zpětnou vazbu, návrháře, indikátor průběhu, animaci a klienta.

 Oblast zpětné vazby a oblast návrháře jsou vždy viditelné. Oblasti indikátoru průběhu a animace jsou vždy dynamické a jsou založené na kontextu uživatele. Oblast návrháře má statickou šířku určenou délkou řetězce, který je stažen z doprovodného prostředku pro textovou zprávu. To umožňuje lokalizaci změnit šířku bez nutnosti změny kódu. Pro angličtinu je šířka tohoto řetězce přibližně 220 pixelů. Oblast návrháře se bude chovat normálně a zbývající místo bude absorbovat oblast zpětné vazby.

 Stavový řádek je také barevně barevně zabarvením, aby se přidávají vizuální zájmy a funkční hodnoty, protože komunikují různé změny stavu integrovaného vývojového prostředí (IDE), například když je integrované vývojové prostředí (IDE) v režimu ladění.

 ![Změny barev stavového řádku integrovaného vývojového prostředí](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 – 02_IDEStatusBar")

 **Barvy stavového řádku integrovaného vývojového prostředí (IDE)**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Vložený informační panel
 Informační panel můžete použít v horní části okna dokumentu nebo panelu nástrojů k informování uživatele o stavu nebo podmině. Může také nabízet příkazy, aby uživatel mohl mít možnost snadno provést akci. Informační panel je standardní ovládací prvek prostředí. Vyhněte se vytváření vlastních, které budou fungovat a budou vypadat nekonzistentní s ostatními v integrovaném vývojovém prostředí. Podrobnosti [o implementaci a pokyny](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) k použití najdete na informačním panelu.

 ![Vložený informační panel](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 – 03_EmbeddedInfobar")

 **Informační panel vložený v okně dokumentu upozorní uživatele, že integrované vývojové prostředí (IDE) je v režimu historického ladění a editor nebude odpovídat stejným způsobem jako ve standardním režimu ladění.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Změny kurzoru myši
 Při změně kurzoru myši použijte barvy, které jsou svázané se službou VSColor a jsou již přidruženy k kurzoru. Změny kurzoru můžete použít k označení probíhající operace a také k zobrazení zón, kde uživatel najede myší na cíl, který se může přetáhnout, přetáhnout nebo použít k výběru objektu.

 Ukazatel myši busy/wait použijte pouze v případě, že je pro operaci nutné rezervovat veškerý dostupný čas procesoru, což uživateli brání v vyjádření jakéhokoli dalšího vstupu. Ve většině případů u dobře napsaných aplikací využívajících multithreading by měly být doby, kdy je uživatelům znemožněno provádět jiné operace, výjimečných.

 Mějte na paměti, že změny kurzoru jsou užitečné jako redundantní podnět k informacím prezentovaných jinde. Nespoléhejte na změnu kurzoru, protože jediný způsob komunikace s uživatelem, zejména při pokusu sdělit něco, co je důležité, aby se uživatel musel zabývat.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Indikátory průběhu
 Indikátory průběhu jsou důležité pro poskytování zpětné vazby uživatelů během procesů, které se dokončí déle než několik sekund. Indikátory průběhu lze zobrazit místě (blízko spouštěcího bodu probíhající akce), ve vloženém stavovém řádku, v modálním dialogovém okně nebo na Visual Studio řádku. Postupujte podle pokynů v [indikátorech průběhu týkajících](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) se jejich použití a implementace.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio oznámení
 Okno Visual Studio oznámení upozorní vývojáře na licencování, prostředí (Visual Studio, rozšíření a aktualizace. Uživatelé mohou jednotlivá oznámení zavřít nebo se rozhodnout ignorovat určité typy oznámení. Seznam ignorováných oznámení se spravuje na stránce Nástroje **> možnosti.**

 Okno Oznámení není aktuálně rozšiřitelné.

 ![Visual Studio oznámení](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio okna nástroje Oznámení**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Seznam chyb
 Oznámení v seznamu chyb indikuje chyby a upozornění, ke kterým došlo během kompilace nebo procesu sestavení, a umožňuje uživateli přejít v kódu na tuto konkrétní chybu kódu.

 ![Seznam chyb](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Seznam chyb v Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Vložené stavové pruhy
 Vzhledem k tomu, že stavový řádek integrovaného vývojového prostředí (IDE) je dynamický a kontext oblasti klienta je nastavený na aktivní okno dokumentu a informace se aktualizují v kontextu nebo odpovědích systému uživatele, je obtížné udržovat průběžné zobrazování informací nebo u dlouhodobých asynchronních procesů poskytnout stav. Například stavový řádek integrovaného vývojového prostředí (IDE) není vhodný pro oznámení výsledků spuštění testů pro více spuštění nebo pro výběry položek s okamžitou akcí. Tyto informace o stavu je důležité uchovávat v kontextu dokumentu nebo okna nástroje, kde uživatel provede výběr nebo spustí proces.

 ![Vložený stavový řádek](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Vložený stavový řádek v Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Oznámení na hlavním panelu Windows
 Oznamovací oblast windows se nachází vedle systémových hodin na hlavním panelu Windows. Mnoho nástrojů a softwarových komponent poskytuje v této oblasti ikony, aby uživatel mohl získat místní nabídku pro úlohy v rámci celého systému, jako je změna rozlišení obrazovky nebo získávání aktualizací softwaru.

 Oznámení na úrovni prostředí by se měla zobrazit v centru oznámení Visual Studio, nikoli v oznamovací oblasti systému Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Bubliny oznámení
 Bubliny oznámení se mohou zobrazovat jako informační v editoru nebo návrháři nebo jako součást oznamovací oblasti systému Windows. Uživatel vnímá tyto bubliny jako problémy, které může vyřešit později, což je výhoda pro nekritická oznámení. Bubliny nejsou vhodné pro důležité informace, které musí uživatel vyřešit hned. Pokud bubliny oznámení používáte v Visual Studio, postupujte podle pokynů k bublinám oznámení v [Desktopu pro Windows.](/windows/desktop/uxguide/mess-notif)

 ![Bublina oznámení](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Bublina oznámení v oznamovací oblasti windows používané pro Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Indikátory průběhu

### <a name="overview"></a>Přehled
 Indikátory průběhu jsou důležitou součástí systému oznámení pro poskytování zpětné vazby uživateli. Uživateli sdělí, kdy se dokončí procesy a operace. Mezi známé typy indikátorů patří indikátory průběhu, rotující kurzory a animované ikony. Typ a umístění indikátoru průběhu závisí na kontextu, včetně toho, co se hlásí a jak dlouho bude trvat dokončení procesu nebo operace.

#### <a name="factors"></a>Faktory
 Pokud chcete určit, který typ indikátoru je vhodný, musíte určit následující faktory.

1. **Načasování:** doba, po která operace bude trvat

2. **Modality:** jestli je operace modální pro prostředí (uzamkne uživatelské rozhraní, dokud se proces nedokoní)

3. **Trvalé/přechodné:** Určuje, jestli se konečný výsledek průběhu musí hlásit nebo zobrazit později.

4. **Determinate/Indeterminate :** Určuje, jestli je možné vypočítat koncový čas a průběh operace.

5. **Grafické/textové umístění:** Určuje, jestli se průběh nebo proces zachytá v textu zprávy, nebo v konkrétním ovládacím prvku, jako je například ovládací prvek Strom.

6. **Bezkontaktní** přístup: Jestli má být průběh v těsné blízkosti uživatelského rozhraní, se kterou souvisí. (Může být například ve stavovém řádku, který může být daleko, nebo musí být blízko tlačítka, které proces spustilo?)

#### <a name="determinate-progress"></a>Určení průběhu

|Typ průběhu|Kdy a jak používat|Poznámky|
|-------------------|-------------------------|-----------|
|Indikátor průběhu (určení)|Očekávaná doba trvání >5 sekund.<br /><br /> Může obsahovat textový popis podrobností procesu.|**Nevkládat** text do animace.|
|Informační panel|Zasílání zpráv přidružené k kontextové uživatelskému rozhraní Viz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Může obsahovat textový popis podrobností procesu.|**Nepoužívejte více** informačních panelů, pokud potřebujete indikovat více procesů. Místo toho použijte skládané indikátory průběhu.|
|Okno Výstup|Přechodné oznámení: Proces na úrovni aplikace, u kterého chce uživatel **zkontrolovat** podrobnosti o dokončení.|**NEPOUŽÍVEJTE,** pokud bude uživatel potřebovat odkazovat na data později.|
|Soubor protokolu|Spárováno s oznámením o netransientech v případech, kdy je **důležité po** dokončení uložit podrobnosti.||
|Stavovém|Přechodné oznámení: Proces na úrovni aplikace, o který uživatel **nebude po** dokončení potřebovat podrobnosti.<br /><br /> Obsahuje vložený indikátor průběhu.<br /><br /> Může obsahovat textový popis podrobností procesu.||

#### <a name="indeterminate-progress"></a>Neurčitý průběh

|Typ průběhu|Kdy a jak používat|Poznámky|
|-------------------|-------------------------|-----------|
|Indikátor průběhu (neurčitý)|Očekávaná doba trvání >5 sekund.<br /><br /> Může obsahovat textový popis podrobností procesu.|**Nevkládat** text do animace.|
|Ants (animované vodorovné tečky)|Zpáteční cesta na server.<br /><br /> Umístí se do blízkosti bodu kontextu nad nadřazeným kontejnerem.|**Nepoužívejte, pokud** není nadřazený celým kontejnerem.|
|Číselník (průběh)|Proces přidružený k kontextové uživatelskému rozhraní nebo kde je třeba vzít v úvahu prostor.<br /><br /> Může obsahovat textový popis podrobností procesu.||
|Informační panel|Zasílání zpráv přidružené k kontextové uživatelskému rozhraní Viz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Nepoužívejte více** informačních panelů, pokud potřebujete indikovat více procesů. Místo toho použijte skládané indikátory průběhu.|
|Okno Výstup|Přechodné oznámení: proces na úrovni aplikace, který uživatel bude chtít **zkontrolovat** podrobnosti po dokončení.|**Nepoužívejte pro** informace, které je potřeba uchovat napříč relacemi.|
|Soubor protokolu|Spárováno s nepřechodným oznámením v případech, kdy je důležité **Uložit** podrobnosti po dokončení.||
|Stavový řádek|Přechodné oznámení: proces na úrovni aplikace, který uživatel nebude po dokončení **potřebovat** podrobnosti.<br /><br /> Zahrnuje vložený indikátor průběhu.<br /><br /> Může obsahovat textový popis podrobností o procesu.||

### <a name="progress-indicator-types"></a>Typy ukazatelů průběhu

#### <a name="progress-bars"></a>Indikátory průběhu

##### <a name="indeterminate"></a>Definované
 ![Neurčitý indikátor průběhu](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Neurčitý indikátor průběhu**

 Neurčitý znamená celkový průběh operace nebo procesu nelze určit. Použijte neurčité indikátory průběhu pro operace, které vyžadují neohraničený čas nebo které přistupují k neznámému počtu objektů. Použijte textový popis, abyste mohli doprovázet, co se děje. Pomocí časových limitů můžete přidělit meze operacím založeným na čase. Neurčité ukazatele průběhu používají animace k zobrazení tohoto průběhu, ale neposkytují žádné další informace. Nevybírejte indikátor průběhu pouze na základě možného nedostatku samotného typu.

##### <a name="determinate"></a>Zrušit ukončení
 ![Indikátor průběhu zrušení ukončení](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

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
 ![ANTS průběhu](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "ANTS", animované horizontální tečky, poskytují vizuální odkaz na neurčitý proces serveru Round-Trip.

##### <a name="spinner-progress-ring"></a>Číselník (kruh průběhu)
 ![Číselník průběhu](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 Číselník (označuje se také jako "okruh průběhu") je neurčitý indikátor průběhu, který se primárně používá ve vztahu k kontextovému uživatelskému rozhraní. Zobrazí číselník v blízkosti blízkosti jeho souvisejícího obsahu, jako je například textové záhlaví kategorie, zasílání zpráv nebo řízení.

##### <a name="cursor-feedback"></a>Váš názor na kurzor
 Pro operace, které trvá mezi 2-7 sekundami, zadejte zpětnou vazbu kurzoru. Obvykle to znamená, že se používá čekací ukazatel poskytovaný operačním systémem. Pokyny najdete v článku [vlastnosti čekání](/dotnet/api/system.windows.input.cursors.wait)na webu MSDN.

#### <a name="progress-indicator-locations"></a>Umístění ukazatelů průběhu

##### <a name="status-bar"></a>Stavový řádek
 Stavový řádek poskytuje aplikaci místo pro zobrazení zpráv a užitečných informací uživateli, aniž by přerušil práci uživatele. Stav pro průběh se obvykle zobrazuje v dolní části okna s popisem nástroje, který obsahuje zprávu o míře průběhu v kombinaci s indikátorem indikátoru průběhu.

 ![Stavový řádek s indikátorem průběhu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Stavový řádek s indikátorem průběhu**

 ![Stavový řádek s zasíláním zpráv](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Stavový řádek s textovým popisem**

##### <a name="infobar"></a>Řádku
 Podobně jako stavový řádek, informační panel poskytuje kontextové oznámení a zasílání zpráv, které lze také spárovat s neurčitými indikátory průběhu, jako je indikátor průběhu nebo číselník. Informační panel by neměl poskytovat podrobný průběh detailní úrovně nebo ukončení indikace průběhu. Viz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Informační panel s indikátorem průběhu a zasíláním zpráv](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Informační panel s ukazatelem průběhu a textovým popisem**

 ![Informační panel uvnitř okna](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Přiřazený
 Vložené indikace průběhu může představovat libovolný typ zavaděče průběhu. Indikátor průběhu se obvykle spáruje s zasíláním zpráv, ale to není požadavek.

 ![Vnitřní číselník průběhu](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Číselník v kombinaci s textovým popisem**

 ![Vložené skládané indikátory průběhu](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Zrušit ukončení skládaných pruhů průběhu**

 ![Vkládání zpráv o průběhu](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Průzkumník serveru vložený text: Probíhá aktualizace...**

##### <a name="tool-windows"></a>Okna nástrojů
 Globální indikace průběhu je reprezentován neurčitým indikátorem průběhu umístěným přímo pod panelem nástrojů.

 ![Globální neurčitý indikátor průběhu](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer globální neurčitý indikátor průběhu**

##### <a name="dialogs"></a>Dialogy
 Dialogová okna mohou obsahovat libovolný typ zavaděče průběhu. Indikátory průběhu se můžou párovat se zasíláním zpráv a také kombinovat s několika úrovněmi průběhu indikace, aby představovaly podrobné a dílčí procesy.

 ![Dialog s více typy indikátor průběhu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Dialog sady Visual Studio se souběžnými procesy a různými typy ukazatelů průběhu**

 ![Dialogové okno s zavaděčem průběhu a zasíláním zpráv](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Dialog sady Visual Studio se zavaděčem průběhu a vloženými příkazy zasílání zpráv**

##### <a name="document-well"></a>Dobře zdokumentovat
 Dokumentace dokumentu může v kombinaci s ovládacími prvky Zobrazit více typů zavaděče průběhu.

 ![Zpráva o průběhu v dokumentu](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Neurčitý indikátor průběhu pod panelem nástrojů**

##### <a name="output-window"></a>Okno Výstup
 Okno výstup je vhodné pro zpracování průběhu procesu a průběžného stavu postupu prostřednictvím vloženého textového zasílání zpráv. Měli byste použít stavový řádek spolu s jakýmkoli vytvářením sestav o průběhu výstupního okna.

 ![Doručování zpráv o průběhu okno Výstup](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **okno Výstup s probíhajícím stavem procesu a čekáním na zprávy**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Infobars

### <a name="overview"></a>Přehled
 Infobars uživateli poskytnout ukazatel blízko ke svému bodu pozornosti a použití sdíleného informačního panelu zajišťuje konzistenci vizuálního vzhledu a interakce.

 ![Řádku](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

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

 ![Informační panel s hypertextovým odkazem](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

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

 ![Ověřování polí &#40;prázdné&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Pokud je pole povinné, měl by být uveden text vodoznaku **\<Required>** a pozadí pole by mělo být světle žluté (VSColor: `Environment.ControlEditRequiredBackground` ) a popředí by mělo být šedé (VSColor: `Environment.ControlEditRequiredHintText` ):

 ![Ověřování pole s popiskem "požadováno"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Program může určit, že se ovládací prvek nachází ve stavu *neplatného obsahu* , a to buď při přesunutí fokusu na jiný ovládací prvek, nebo když uživatel klikne na tlačítko pro potvrzení [OK] nebo když uživatel dokument nebo formulář uloží.

 Pokud je určena neplatný stav obsahu, zobrazí se ikona v ovládacím prvku nebo pouze vedle ní. Popis, který popisuje chybu, by se měl zobrazit při najetí myší buď na ikonu, nebo na ovládací prvek. Kromě toho by se mělo kolem ovládacího prvku, který vytváří neplatný stav, zobrazit ohraničení o velikosti 1 pixelu.

 ![Specifikace rozvržení pro ověřování polí](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Specifikace rozložení pro ověřování polí**

#### <a name="acceptable-variations-for-icon-location"></a>Přijatelné odchylky pro umístění ikony
 Existují dlouhé jedinečné případy, kdy si uživatelé musí být informováni o chybách ověřování. V úvahách o typu ovládacího prvku a konfiguraci uživatelského rozhraní vyberte umístění ikon odpovídající vaší situaci.

 ![Přijatelná umístění pro umístění ikony](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Přijatelné odchylky pro umístění ikon ověřování polí**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Ověření požadavku na připojení k serveru nebo síťovému připojení
 V některých případech se k ověření obsahu vyžaduje zpáteční cesta k serveru a je důležité zobrazit stav uživatele, ověřit a chybové stavy. Následující obrázek ukazuje příklad tohoto případu a doporučené uživatelské rozhraní.

 ![Ověření, které zahrnuje zpáteční cestu k serveru](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Ověření, které zahrnuje zpáteční cestu k serveru**

 Všimněte si, že musí být k dispozici dostatečný prostor napravo od ovládacího prvku, aby bylo možné přizpůsobit "ověřování...". a "opakovat" text.

#### <a name="in-place-warning-text"></a>Místní výstražný text
 Pokud je k dispozici místo pro vložení chybové zprávy blízko ovládacího prvku ve stavu chyby, je vhodnější použít pouze popisek.

 ![&#45;upozornění na místo](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Místní výstražný text**

#### <a name="watermarks"></a>Vodoznaky
 Někdy je celý ovládací prvek nebo okno v chybovém stavu. V takovém případě k indikaci chyby použijte vodoznak.

 ![Meze](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Ověření pole meze**
