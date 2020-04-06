---
title: Oznámení a průběh pro Visual Studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f6a7ddd5d1a5a7257617b03098722e1341017b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699886"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Oznámení a průběh pro Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a>Oznamovací systémy

### <a name="overview"></a>Přehled
 Existuje několik způsobů, jak informovat uživatele o tom, co se děje v sadě Visual Studio, o jejich úlohách vývoje softwaru.

 Při provádění jakéhokoli oznámení:

- **Udržujte počet oznámení na minimální** efektivní číslo. Oznamovací zprávy by se měly vztahovat na většinu uživatelů sady Visual Studio nebo na uživatele určité oblasti funkcí a funkcí. Nadměrné používání oznámení může uživatele odsouvat do cesty nebo snížit vnímanou snadnost používání systému.

- **Ujistěte se, že prezentujete jasné, žalovatelné zprávy,** které uživatel může použít k vyvolání příslušného kontextu pro provádění složitějších voleb a provedení dalších opatření.

- **Prezentovat synchronní a asynchronní zprávy odpovídajícím způsobem.** Synchronní oznámení označují, že něco vyžaduje okamžitou pozornost, například při selhání webové služby nebo je vyvolána výjimka kódu. Uživatel by měl být o těchto situacích informován ihned způsobem, který vyžaduje jejich vstup, například v modálním dialogu. Asynchronní oznámení jsou ty, které by měl uživatel vědět, ale nemusí být nutné jednat okamžitě, například při dokončení operace sestavení nebo dokončení nasazení webu. Tyto zprávy by měly být více okolí a nesmí přerušit tok úloh uživatele.

- **Modální dialogová okna používejte pouze v případě, že je to nutné, aby uživatel nemohl provést další akci** před potvrzením zprávy nebo rozhodnutím uvedeným v dialogovém okně.

- **Odeberte okolní oznámení, pokud již nejsou platná.** Nevyžadovat, aby uživatel zamítl oznámení, pokud již podniklkroky k řešení problému, na který byl upozorněn.

- **Uvědomte si, že oznámení může vést k falešné korelace.** Uživatelé se mohou domnívat, že jedna nebo více jejich akcí spustilo oznámení, když ve skutečnosti nedošlo k příčinné souvislosti. V oznámení o kontextu, aktivační události a zdroji oznámení se oznamte.

### <a name="choosing-the-right-method"></a>Výběr správné metody
 Tato tabulka vám pomůže při výběru správné metody upozornění uživatele na vaši zprávu.

|Metoda|Použití|Nepoužívejte|
|------------|---------|----------------|
|[Modální dialogová okna chybových zpráv](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Před pokračováním použijte, když je vyžadována odpověď uživatele.|Nepoužívejte, pokud není nutné blokovat uživatele a přerušit jeho tok. Nepoužívejte modální dialogová okna, pokud je možné zobrazit zprávu jiným, méně rušivou cestou.|
|[Stavový řádek ide](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Použijte, pokud existují okolní textové informace týkající se stavu procesu.|Nepoužívejte samostatně. Nejlépe se používá ve spojení s jiným mechanismem zpětné vazby.|
|[Vložený informační panel](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|V okně nástroje nebo v okně dokumentu slouží k upozornění na průběh, stav chyb, výsledky a/nebo informace, které lze použít k použití.|Nepoužívejte, pokud informace nejsou relevantní pro místo, kde je informační panel umístěn.<br /><br /> Nepoužívejte mimo okno dokumentu/nástroje.|
|[Změny kurzoru myši](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Může být použit k oznámení, že proces probíhá. Používá se také k upozornění, že došlo ke změně stavu myši, například když probíhá přetažení nebo že je kurzor myši v určitém režimu, například v režimu kreslení.|Nepoužívejte pro krátké změny průběhu nebo pokud je pravděpodobné vlající kurzor (například při svázané s částmi delšího spuštěného procesu namísto celého procesu).|
|[Ukazatele pokroku](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Použijte, když potřebujete hlásit průběh (buď určitý nebo neurčitý). Existuje celá řada typů indikátoru průběhu a specifické použití pro každý. Viz [ukazatele průběhu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Okno Oznámení sady Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Oznámení okno není veřejně rozšiřitelné. Používá se však ke komunikaci řadu zpráv o sadě Visual Studio, včetně kritických problémů s licencí a informační oznámení o aktualizacích sady Visual Studio nebo balíčky.|Nepoužívejte pro jiné typy oznámení.|
|[Seznam chyb](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Pokud se problém týká přímo aktuálně otevřeného řešení uživatele s problémem (chyba/ upozornění/ informace), může být nutné provést akci s kódem.<br /><br /> To by zahrnovalo například:<br /><br /> - Kompilátor zprávy (chyba / varování / info)<br /><br /> - Analyzátor kódu / diagnostické zprávy o kódu<br /><br /> - Stavět zprávy<br /><br /> Může být vhodné pro problémy týkající se projektu nebo soubory řešení, ale zvažte informace Průzkumníka řešení jako první.|Nepoužívejte pro položky, které nemají žádný vztah k otevřenému kódu řešení uživatele.|
|Oznámení editoru: Žárovka|Použijte, pokud máte k dispozici opravu k odstranění problému, který existuje v otevřeném souboru.<br /><br /> Všimněte si, že žárovka by měla být také použita pro hostování rychlých akcí, které jsou prováděny v kódu uživatele na vyžádání, jako je například refaktoring, ale v takovém případě se nezobrazí "styl oznámení".|Nepoužívejte pro položky, které nemají žádný vztah k otevřenému souboru.|
|Oznámení editoru: Klikyháky|Slouží k upozornění uživatele na problém s určitým rozsahem jejich otevřeného kódu (například červená vlnovka na chyby).|Nepoužívejte pro položky, které se nevztahují k určitému rozsahu jejich otevřeného kódu.|
|[Vložené stavové panely](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Slouží k poskytnutí stavu souvisejícího s obsahem nebo procesem v kontextu konkrétního okna nástroje, okna dokumentu nebo dialogového okna.|Nepoužívejte pro obecná oznámení produktu, procesy nebo položky, které nemají žádný vztah k obsahu v konkrétním okně.|
|[Oznámení na panelu Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Slouží k povrchu oznámení pro mimo-of-proc procesy nebo doprovodné aplikace.|Nepoužívejte pro oznámení, které jsou relevantní pro ide.|
|[Bubliny oznámení](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Slouží k upozornění na vzdálený proces nebo změnu **mimo** ide.|Nepoužívejte jako prostředek pro informování uživatele o procesech **v rámci** rozhraní IDE.|

### <a name="notification-methods"></a>Metody oznamování

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>Modální dialogová okna chybových zpráv
 Modální dialogové okno s chybovou zprávou se používá k zobrazení chybové zprávy, která vyžaduje potvrzení nebo akci uživatele.

 ![Modální chybová zpráva](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Dialogové okno modální chybové zprávy upozorňující uživatele na neplatný připojovací řetězec k databázi**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>Stavový řádek ide
 Pravděpodobnost, že si uživatelé všimnou textu stavového řádku, koreluje s jejich všestranným počítačovým prostředím a specifickými zkušenostmi s platformou Windows. Visual Studio zákaznická základna inklinuje být zkušený v obou oblastech, i když i znalí uživatelé systému Windows může chybět změny ve stavovém řádku. Proto stavový řádek se nejlépe používá pro informační účely nebo jako redundantní podnět pro informace prezentované jinde. Jakýkoli druh důležité informace, které musí uživatel vyřešit okamžitě by měly být poskytnuty v dialogovém okně nebo v okně nástroje oznámení.

 Stavový řádek sady Visual Studio je navržen tak, aby umožňoval zobrazení několika typů informací. Je rozdělena do oblastí pro zpětnou vazbu, návrháře, indikátoru průběhu, animace a klienta.

 Oblast zpětné vazby a oblast návrháře jsou vždy viditelné. Indikátor průběhu a oblasti animace jsou vždy dynamické a založené na kontextu uživatele. Oblast návrháře má statickou šířku určenou délkou řetězce, který je vyžádán z doprovodného prostředku pro textovou zprávu. To umožňuje lokalizaci změnit velikost šířky bez nutnosti změny kódu. Pro angličtinu je šířka tohoto řetězce zhruba 220 pixelů. Oblast návrháře se bude chovat normálně a oblast zpětné vazby absorbuje zbývající prostor.

 Stavový řádek je také obarven přidat vizuální zájem a funkční hodnotu tím, že komunikuje různé změny stavu IDE, jako když je ide v režimu ladění.

 ![Změny barev stavového řádku ide](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Barvy stavového řádku ide**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>Vložený informační panel
 Informační panel lze použít v horní části okna dokumentu nebo okna nástroje k informování uživatele o stavu nebo stavu. Může také nabídnout příkazy, takže uživatel může mít způsob, jak snadno provést akci. Informační panel je standardní ovládací prvek prostředí. Vyhněte se vytváření vlastní, který bude jednat a zobrazí se v rozporu s ostatními v ide. Podrobnosti o implementaci a pokyny k použití najdete v tématu [Informační panely.](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)

 ![Vložený informační panel](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Informační panel vložený v okně dokumentu, který uživatele upozorní, že rozhraní IDE je v historickém režimu ladění a editor nebude reagovat stejným způsobem jako ve standardním režimu ladění.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>Změny kurzoru myši
 Při změně kurzoru myši použijte barvy, které jsou svázané se službou VSColor a jsou již přidruženy k kurzoru. Změny kurzoru lze použít k označení probíhající operace, stejně jako zóny přístupů, kde uživatel je najet myší na cíl, který lze přetáhnout na nebo použít k výběru objektu.

 Kurzor myši zaneprázdněný/čekání používejte pouze v případě, že veškerý dostupný čas procesoru musí být vyhrazen pro operaci, což uživateli zabrání vyjádřit další vstup. Ve většině případů s dobře napsané aplikace pomocí multithreading, časy, kdy uživatelé jsou zabráněno dělat jiné operace by měly být vzácné.

 Mějte na paměti, že změny kurzoru jsou užitečné jako redundantní podnět pro informace prezentované jinde. Nespoléhejte na změnu kurzoru jako jediný způsob komunikace s uživatelem, zejména při pokusu o předání něco, co je důležité, že uživatel musí adresu.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>Ukazatele pokroku
 Ukazatele průběhu jsou důležité pro poskytování zpětné vazby od uživatelů během procesů, které trvá déle než několik sekund. Ukazatele průběhu lze zobrazit na místě (v blízkosti spouštěcího bodu probíhající akce), ve vloženém stavovém řádku, v modálním dialogu nebo ve stavovém řádku sady Visual Studio. Postupujte podle pokynů v [ukazatelích programu Progress](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) týkajících se jejich používání a provádění.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Okno Oznámení sady Visual Studio
 Okno Oznámení sady Visual Studio upozorní vývojáře na licencování, prostředí (Visual Studio), rozšíření a aktualizace. Uživatelé mohou jednotlivá oznámení zamítnout nebo se mohou rozhodnout ignorovat určité typy oznámení. Seznam ignorovaných oznámení je spravován na stránce **Možnosti > nástrojů.**

 Okno Oznámení není aktuálně rozšiřitelné.

 ![Okno Oznámení sady Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Okno nástroje Oznámení sady Visual Studio**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a>Seznam chyb
 Oznámení v seznamu chyb označují chyby a upozornění, ke kterým došlo během kompilace a nebo sestavení procesu a umožňuje uživateli přejít v kódu na tuto konkrétní chybu kódu.

 ![Seznam chyb](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Seznam chyb v sadě Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>Vložené stavové panely
 Vzhledem k tomu, že stavový řádek IDE je dynamický, s kontextem oblasti klienta nastaveným na okno aktivního dokumentu a aktualizací informací o kontextu uživatele nebo systémových odpovědích, je obtížné udržovat nepřetržité zobrazení informací nebo poskytnout stav na dlouhodobých asynchronních procesech. Například stavový řádek IDE není vhodný pro oznámení výsledků spuštění testu pro více spuštění nebo okamžitě žalovatelné výběry položek. Je důležité zachovat tyto informace o stavu v kontextu okna dokumentu nebo nástroje, kde uživatel provede výběr nebo zahájí proces.

 ![Vložený stavový řádek](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Vložený stavový řádek v sadě Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Oznámení na panelu Windows
 Oznamovací oblast systému Windows se nachází vedle systémových hodin na hlavním panelu systému Windows. Mnoho nástrojů a softwarových součástí poskytuje ikony v této oblasti, takže uživatel může získat místní nabídku pro úlohy celého systému, jako je změna rozlišení obrazovky nebo získání aktualizací softwaru.

 Oznámení na úrovni prostředí by měla být krejprve v centru Oznámení sady Visual Studio, nikoli v oznamovací oblasti systému Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>Bubliny oznámení
 Bubliny oznámení se mohou zobrazit jako informační v editoru nebo návrháři nebo jako součást oblasti Windows Notification. Uživatel vnímá tyto bubliny jako problémy, které mohou vyřešit později, což je výhoda pro nekritická oznámení. Bubliny jsou nevhodné pro důležité informace, které uživatel musí vyřešit hned. Pokud používáte bubliny oznámení v sadě Visual Studio, postupujte podle pokynů pro [windows desktop pro bubliny oznámení](/windows/desktop/uxguide/mess-notif).

 ![Bublina oznámení](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Bublina oznámení v oznamovací oblasti Windows používaná pro Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>Ukazatele pokroku

### <a name="overview"></a>Přehled
 Ukazatele pokroku jsou důležitou součástí systému oznamování pro poskytování zpětné vazby od uživatelů. Informují uživatele o dokončení procesů a operací. Mezi známé typy indikátorů patří indikátory průběhu, rotující kurzory a animované ikony. Typ a umístění indikátoru průběhu závisí na kontextu, včetně toho, co je hlášeno a jak dlouho bude proces nebo operace trvat.

#### <a name="factors"></a>Faktory
 Chcete-li určit, který typ ukazatele je vhodný, musíte určit následující faktory.

1. **Časování:** doba, po kterou bude operace trvat

2. **Modalita:** zda je operace modální pro prostředí (uzamkne výrobní prostředí, dokud nebude proces dokončen)

3. **Perzistentní/přechodný:** zda konečný výsledek pokroku musí být včas vykazován a/nebo zobrazitelný

4. **Určitý/neurčitý:** zda lze vypočítat čas ukončení operace a průběh

5. **Grafické/textové umístění:** zda je průběh nebo proces zachycen v textu zprávy nebo v určitém ovládacím prvku, například stromový ovládací prvek

6. **Blízkost:** zda by měl být pokrok v těsné blízkosti uj., se kterým souvisí. (Například může být ve stavovém řádku, který může být daleko, nebo to musí být v blízkosti tlačítka, které spustilo proces?)

#### <a name="determinate-progress"></a>Určitý pokrok

|Typ průběhu|Kdy a jak používat|Poznámky|
|-------------------|-------------------------|-----------|
|Indikátor průběhu (určitý)|Předpokládaná doba trvání >5 sekund.<br /><br /> Může obsahovat textový popis podrobností procesu.|**Nevkládejte** text do animace.|
|Informační panel|Zasílání zpráv přidružené k kontextovému ui. Viz [Informační panely](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Může obsahovat textový popis podrobností procesu.|**Nepoužívejte** více informačních panelů, když potřebujete označit více procesů. Místo toho použijte skládané indikátory průběhu.|
|Okno Výstup|Přechodné oznámení: proces na úrovni aplikace, který uživatel chce **zkontrolovat** podrobnosti po dokončení.|**Nepoužívejte,** pokud uživatel bude muset odkazovat na data později.|
|Soubor protokolu|Spárováno s nepřechodným oznámením v případech, kdy je důležité **uložit** podrobnosti po dokončení.||
|Stavovém|Přechodné oznámení: proces na úrovni aplikace, o který uživatel **nebude po** dokončení potřebovat podrobnosti.<br /><br /> Obsahuje vložený indikátor průběhu.<br /><br /> Může obsahovat textový popis podrobností procesu.||

#### <a name="indeterminate-progress"></a>Neurčitý průběh

|Typ průběhu|Kdy a jak používat|Poznámky|
|-------------------|-------------------------|-----------|
|Indikátor průběhu (neurčitý)|Předpokládaná doba trvání >5 sekund.<br /><br /> Může obsahovat textový popis podrobností procesu.|**Nevkládejte** text do animace.|
|Mravenci (animované vodorovné tečky)|Zpáteční cesta na server.<br /><br /> Umístěn v blízkosti bodu kontextu přes nadřazený kontejner.|**Nepoužívejte,** pokud není nadřazený celý kontejner.|
|Číselník (indikátor průběhu)|Proces přidružený k kontextové muziky nebo kde je důležité místo.<br /><br /> Může obsahovat textový popis podrobností procesu.||
|Informační panel|Zasílání zpráv přidružené k kontextovému ui. Viz [Informační panely](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Nepoužívejte** více informačních panelů, když potřebujete označit více procesů. Místo toho použijte skládané indikátory průběhu.|
|Okno Výstup|Přechodné oznámení: proces na úrovni aplikace, který uživatel bude chtít **zkontrolovat** podrobnosti po dokončení.|**Nepoužívejte** pro informace, které je třeba zachovat napříč relacemi.|
|Soubor protokolu|Spárováno s nepřechodným oznámením v případech, kdy je důležité **uložit** podrobnosti po dokončení.||
|Stavovém|Přechodné oznámení: proces na úrovni aplikace, o který uživatel **nebude po** dokončení potřebovat podrobnosti.<br /><br /> Zahrnuje vložený indikátor průběhu.<br /><br /> Může obsahovat textový popis podrobností procesu.||

### <a name="progress-indicator-types"></a>Typy indikátorů průběhu

#### <a name="progress-bars"></a>Indikátory průběhu

##### <a name="indeterminate"></a>Neurčitý
 ![Pruh neurčitého průběhu](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Pruh neurčitého průběhu**

 "Neurčitý" znamená, že nelze určit celkový průběh operace nebo procesu. Panely neurčitého průběhu použijte pro operace, které vyžadují neomezené množství času nebo které přistupují k neznámému počtu objektů. Co se děje, použijte textový popis. Pomocí časových časových opovenek můžete poskytnout hranice operacím založeným na čase. Indikátory neurčitého průběhu používají animace k zobrazení průběhu, ale neposkytují žádné další informace. Nevybírejte indikátor neurčitého průběhu pouze na základě možného nedostatku přesnosti.

##### <a name="determinate"></a>Určitý
 ![Indikátor určitého průběhu](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Indikátor určitého průběhu**

 "Determinate" znamená, že operace nebo proces vyžaduje ohraničené množství času, i když toto množství času nelze přesně předpovědět. Jasně uveďte dokončení. Nedovolte, aby indikátor průběhu přešel na 100 procent, pokud operace nebyla dokončena. Animace indikátoru určitého průběhu se přesune zleva doprava z 0 na 100 %.

 Nikdy nepohybujte indikátorem průběhu dozadu během operace. Tyč by se měla neustále pohybovat vpřed, když operace začíná, a po ukončení operace dosáhnout 100%. Bod indikátoru průběhu je poskytnout uživateli představu o tom, jak dlouho trvá celá operace, bez ohledu na to, kolik kroků jsou zapojeny.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Souběžné vytváření sestav (skládané indikátory průběhu)
 Pokud operace bude trvat dlouhou dobu - možná několik minut - pak mohou být použity dva indikátory průběhu, jeden, který ukazuje celkový pokrok pro operaci a druhý pro průběh aktuálního kroku. Pokud například instalační program kopíruje mnoho souborů, lze jeden indikátor průběhu použít k označení, jak dlouho trvá celý proces, zatímco sekunda může určit, jaké procento aktuálního souboru nebo adresáře se kopíruje. Nevykazují více než pět souběžných operací nebo procesů pomocí skládaný průběh pruhy. Pokud máte více než pět souběžných operací nebo procesů k nahlášení, použijte modální dialogové okno s tlačítkem Storno a oznamte podrobnosti průběhu do okna Výstup.

##### <a name="textual-descriptions"></a>Textové popisy
 K tomu, co se děje, a odhadovanému čase do dokončení použijte textový popis. Pokud není možné určit, jak dlouho bude operace trvat, může být lepší volbou pro poskytnutí zpětné vazby spíše animovaná ikona než indikátor průběhu.

 Visual Studio poskytuje standardní indikátor průběhu ve stavovém řádku, který může používat libovolný produkt integrovaný do sady Visual Studio. Pro textové popisy toho, co se děje při animování indikátoru průběhu, lze aktualizovat text stavového řádku.

#### <a name="other-progress-indicators"></a>Další ukazatele pokroku

##### <a name="ants-animated-horizontal-dots"></a>Mravenci (animované vodorovné tečky)
 ![Pokrok mravenci](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Mravenci", animované vodorovné tečky, poskytují vizuální referenci pro neurčitý proces serveru round-trip.

##### <a name="spinner-progress-ring"></a>Číselník (indikátor průběhu)
 ![Průběh číselníku](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 Číselník (označovaný také jako "indikátor průběhu") je indikátor neurčitého průběhu, který se používá především ve vztahu k kontextovému uj. Zobrazte číselník v těsné blízkosti souvisejícího obsahu, například záhlaví textové kategorie, zasílání zpráv nebo ovládací prvek.

##### <a name="cursor-feedback"></a>Zpětná vazba kurzoru
 Pro operace, které trvat mezi 2-7 sekund, poskytnout zpětnou vazbu kurzoru. Obvykle to znamená použití kurzorčekání poskytované operačním systémem. Pokyny naleznete v článku MSDN [Cursors.Wait Property](/dotnet/api/system.windows.input.cursors.wait).

#### <a name="progress-indicator-locations"></a>Umístění indikátorů průběhu

##### <a name="status-bar"></a>Stavovém
 Stavový řádek poskytuje aplikaci místo pro zobrazení zpráv a užitečných informací pro uživatele bez přerušení práce uživatele. Obvykle se zobrazí v dolní části okna, stav průběhu bude podokno tip nástroje, který obsahuje zprávu o míře pokroku v kombinaci s indikátorem indikátoru indikátoru průběhu.

 ![Stavový řádek s indikátorem průběhu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Stavový řádek s indikátorem průběhu**

 ![Stavový řádek se zasíláním zpráv](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Stavový řádek s textovým popisem**

##### <a name="infobar"></a>Informační panel
 Podobně jako stavový řádek poskytuje informační panel kontextové oznámení a zasílání zpráv, které lze také spárovat s indikátory neurčitého průběhu, jako je indikátor průběhu nebo číselník. Informační panel by neměl poskytovat podrobný průběh úrovně nebo indikaci určitého průběhu. Viz [Informační panely](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Informační panel s indikátorem průběhu a zasíláním zpráv](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Informační panel s indikátorem průběhu a textovým popisem**

 ![Informační panel uvnitř okna](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Přiřazený
 Inline indikace průběhu může být reprezentována libovolným typem zavaděče průběhu. Indikátor průběhu je obvykle spárován se zasíláním zpráv, ale to není požadavek.

 ![Číselník inline průběhu](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Číselník v kombinaci s textovým popisem**

 ![Vložkované skládané indikátory průběhu](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Indikátory určitého sklápění průběhu**

 ![Zasílání zpráv o průběhu vřádí](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Vázakový text Průzkumníka serveru: Aktualizace...**

##### <a name="tool-windows"></a>Okna nástrojů
 Globální indikace průběhu je reprezentována pruhem neurčitého průběhu umístěným přímo pod panelem nástrojů.

 ![Globální indikátor neurčitého průběhu](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Panel globálního neurčitého průběhu průzkumníka týmu**

##### <a name="dialogs"></a>Dialogy
 Dialogová okna mohou obsahovat některý z typů zavaděče průběhu. Indikátory průběhu mohou být spárovány se zasíláním zpráv a kombinovány s více úrovněmi indikace průběhu, které představují podrobné a dílčí procesy.

 ![Dialog s více typy indikátorů průběhu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Dialogové okno Visual Studio s souběžnými procesy a více typy indikátorů průběhu**

 ![Dialog s zavaděcem průběhu a zasíláním zpráv](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Dialogové okno Visual Studio s zavaděcem průběhu a příkazy vsazení vsazení vsazení vsazení zpráv**

##### <a name="document-well"></a>Dobře dokumentujte
 Dobře dokumentu může zobrazit více typů zavaděče průběhu v kombinaci s ovládacími prvky.

 ![Předávání zpráv o průběhu v dokumentu](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Pruh neurčitého průběhu pod panelem nástrojů**

##### <a name="output-window"></a>Okno Výstup
 Okno Výstup je vhodné pro zpracování průběhu procesu a stavu probíhajícího průběhu prostřednictvím vřádících textových zpráv. Měli byste použít stavový řádek spolu s případnými zprávami o průběhu výstupního okna.

 ![Zasílání zpráv průběhu ve výstupním okně](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Výstupní okno se stavem probíhajícího procesu a čekáním na zasílání zpráv**

## <a name="infobars"></a><a name="BKMK_Infobars"></a>Informační panely

### <a name="overview"></a>Přehled
 Informační panely poskytují uživateli indikátor v blízkosti bodu pozornosti a použití sdíleného ovládacího prvku informačního panelu zajišťuje konzistenci vizuálního vzhledu a interakce.

 ![Informační panel](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Informační panely v sadě Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Vhodné použití informačního panelu

- Chcete-li dát uživateli neblokující, ale důležitou zprávu relevantní pro aktuální kontext

- Označení, že je ui v určitém stavu nebo stavu, který má některé důsledky interakce, jako je například historické ladění

- Upozornit uživatele, že systém zjistil problémy, například když rozšíření způsobuje problémy s výkonem

- Poskytnout uživateli způsob, jak snadno provést akci, například když editor zjistí, že soubor má smíšené karty a mezery

##### <a name="do"></a>Do:

- Text zprávy v informačním panelu zkraťte a přejděte k věci.

- Udržujte text na odkazy a tlačítka stručné.

- Ujistěte se, že možnosti "akce", které uživatelům poskytnete, jsou minimální a zobrazují pouze požadované akce.

##### <a name="dont"></a>Ne:

- Pomocí informačního panelu můžete nabídnout standardní příkazy, které by měly být umístěny na panelu nástrojů.

- Místo modálního dialogu použijte informační panel.

- Vytvořte plovoucí zprávu mimo okno.

- Použijte více informačních panelů na několika místech ve stejném okně.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Může se zobrazit více informačních panelů současně?
 Ano, může se zobrazit více informačních panelů současně. Zobrazí se v pořadí "kdo dřív přijde, je dřív na řadě" s prvním informačním panelem, který se zobrazuje nahoře, a dalšími informačními panely, které jsou uvedeny níže.

 Uživateli se zobrazí maximálně tři informační panely najednou, po kterých, pokud je k dispozici více informačních panelů, bude oblast informačního panelu posuvná.

### <a name="creating-an-infobar"></a>Vytvoření informačního panelu
 Informační panel má čtyři části zleva doprava:

- **Ikona:** Toto je místo, kde chcete přidat libovolnou ikonu, kterou chcete zobrazit na informačním panelu, například ikonu upozornění.

- **Text:** Můžete přidat text popisující scénář/situaci, ve které se uživatel nachází, spolu s odkazy v textu, v případě potřeby. Nezapomeňte, aby text stručné.

- **Akce:** Tato část by měla obsahovat odkazy a tlačítka pro akce, které může uživatel provést na informačním panelu.

- **Tlačítko Zavřít:** Poslední část vpravo může mít tlačítko zavřít.

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

 Zde je příklad, který vytvoří InfoBarModel s nějakým textem s hypertextovým odkazem, tlačítkem akce a ikonou.

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
 Implementujte rozhraní IVsInfoBar, abyste mohli poskytnout informační panel z nativního kódu.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Získání informačního panelu UIElement z informačního panelu
 InfoBarModel nebo IVsInfoBar implementace jsou datové modely, které musí být převedeny na UIElement, aby se zobrazí v ui. UIElement lze načíst pomocí služby SVsInfoBarUIFactory/IVsInfoBarUIFactory.

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
 Informační panely lze zobrazit na jednom nebo více z následujících umístění:

- Okna nástrojů

- Na kartě dokumentu

> [!IMPORTANT]
> Je možné umístit informační panel a předat zprávu o globálním kontextu. To by se objevilo mezi panely nástrojů a dokumentem dobře. To se nedoporučuje, protože způsobuje problémy s "skok a trhnutí" ide a je třeba se vyhnout, pokud to není nezbytně nutné a vhodné.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Umístění informačního panelu do podokna ToolWindowPane
 ToolWindowPane.AddInfoBar(IVsInfoBar) metoda slouží k přidání informačního panelu do okna nástroje. Toto rozhraní API můžete buď přidat IVsInfoBar (z nichž InfoBarModel je výchozí implementace) nebo IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Umístění informačního panelu do dokumentu nebo jiného podokna než ToolWindowPane
 Chcete-li umístit informační panel do libovolného prvku IVsWindowFrame, použijte vlastnost VSFPROPID_InfoBarHost k získání vlastnosti IVsInfoBarHost pro rámec a pak přidejte informační panel UIElement.

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
 Chcete-li umístit informační panel v hlavním okně, použijte VSSPROPID_MainWindowInfoBarHost služby IVsShell získat hlavní okno IVsInfoBarHost a pak do něj přidejte informační panel UIElement.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Budu vědět, kdy uživatel provede akci na mém informačním panelu?
 Ano, každou akci události vrátíme autorovi informačního panelu. Je pak na autorovi informačního panelu, aby v rozhraní IDE podnikl kroky na základě výběru uživatele na informačním panelu. Informační panely budou automaticky odebrány z hostitele, na jehož tlačítko Zavřít bylo kliknuto, ale další práce je vyžadována, pokud je třeba po zavření odebrat další informační panely. Telemetrie také bude muset být zaznamenána nezávisle každý informační panel.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Příjem událostí informačního panelu v toolwindowpane
 ToolWindowPane má dvě události pro informační panely. Událost InfoBarClosed je vyvolána, když je informační panel v toolwindowpane uzavřen. Událost InfoBarActionItemClicked je vyvolána, když kliknete na hypertextový odkaz nebo tlačítko uvnitř informačního panelu.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Příjem událostí informačního panelu přímo z prvku UIElement
 IVsInfoBarUIElement.Advise lze přihlásit k odběru událostí přímo z uielement u informačního panelu. Implementace IVsInfoBarUIEvents umožní autorovi přijímat události zavřít a kliknout.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a>Ověření chyby
 Když uživatel zadá informace, které nejsou přijatelné, například při přeskočené povinné pole nebo při zadání dat v nesprávném formátu, je lepší použít ověření ovládacího prvku nebo zpětnou vazbu v blízkosti ovládacího prvku namísto použití dialogového okna blokování automaticky otevíraného okna.

### <a name="field-validation"></a>Ověřování polí
 Ověření formuláře a pole se skládá ze tří součástí: ovládacího prvku, ikony a popisku. Zatímco několik typů ovládacích prvků lze použít, textové pole bude použit jako příklad.

 ![Ověření pole &#40;prázdné&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Pokud je pole povinné, měl by být text vodoznaku s uvedením `Environment.ControlEditRequiredBackground` `Environment.ControlEditRequiredHintText` ** \<povinného>** a pozadí pole by mělo být světle žluté (VSColor: ) a popředí by mělo být šedé (VSColor: ):

 ![Ověření pole s popiskem Povinné](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Program může určit, že ovládací prvek je ve stavu *neplatného obsahu zadaného* buď při přesunutí fokusu do jiného ovládacího prvku, nebo když uživatel klepne na tlačítko potvrzení [OK] nebo když uživatel uloží dokument nebo formulář.

 Když je určen neplatný stav obsahu, zobrazí se ikona uvnitř ovládacího prvku nebo hned vedle ovládacího prvku. Popis popisující chybu by se měl objevit při najetí na ikonu nebo ovládací prvek. Kromě toho by se mělo zobrazit ohraničení 1 obrazových bodů kolem ovládacího prvku, který vytváří neplatný stav.

 ![Specifikace rozložení pro ověření pole](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Specifikace rozložení pro ověření pole**

#### <a name="acceptable-variations-for-icon-location"></a>Přijatelné varianty pro umístění ikony
 Existuje nespočet jedinečných případů, kdy uživatelé potřebují být informováni o chybách ověření. S ohledem na typ ovládacího prvku a konfiguraci ui, zvolte umístění ikony odpovídající vaší situaci.

 ![Přijatelná umístění pro umístění ikony](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Přijatelné varianty pro umístění ikon ověření pole**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Ověření vyžadující odezvu na server nebo síťové připojení
 V některých případech je k ověření obsahu vyžadována odezva na server a bylo by důležité zobrazit stavy průběhu, ověření a chyby uživatele. Níže uvedený obrázek ukazuje příklad tohoto případu a doporučené uI.

 ![Ověření zahrnující odezvu na server](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Ověření zahrnující odezvu na server**

 Všimněte si, že musí být k dispozici dostatek volného místa napravo od ovládacího prvku, aby se přizpůsobilo "Ověření..." a text "Opakovat".

#### <a name="in-place-warning-text"></a>Text upozornění na místě
 Pokud je k dispozici místo pro umístit chybovou zprávu v blízkosti ovládacího prvku ve stavu chyby, je to vhodnější použít pouze popisek.

 ![Na&#45;místě varování](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Text upozornění na místě**

#### <a name="watermarks"></a>Vodoznaky
 V některých obdobích je celý ovládací prvek nebo okno v chybovém stavu. V takovém případě použijte vodoznak k označení chyby.

 ![Vodoznak](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Ověření pole vodoznaku**
