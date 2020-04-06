---
title: Animace pro visual studio | Dokumenty společnosti Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc11eb7bab69728be5ceaa55143f56e93cd1fca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698607"
---
# <a name="animations-for-visual-studio"></a>Animace pro Visual Studio
## <a name="animation-fundamentals"></a>Základy animace

### <a name="animation-best-practices-in-visual-studio"></a>Doporučené postupy animace v sadě Visual Studio
Postupujte podle těchto pravidel, abyste zajistili konzistentní a uživatelsky přívětivé styly animací v rozhraní IDE sady Visual Studio.

- **Buďte selektivní.** Omezte animace na ty, které slouží konkrétním účelům.

- **Načasování a rychlost jsou důležité** pro zajištění toho, aby přechody byly rychlé a přirozené:

  - Dokončení animovaných přechodů během jedné půlsekundy (500 milisekund).

  - Animace, které by se vyskytují často musí být dostatečně rychlé, aby nepřerušily pracovní postup uživatele. Sledujte animaci ve smyčce a upravte časování, dokud se nebude cítit správně.

  - Animace by neměly být tak rychlé nebo prudké, že je obtížné pochopit, ale ne tak pomalé, že to dělá jeden netrpělivý pro přechod až do konce.

  - Použití proměnné časování zdůraznit důležitost. Například při procházení posloupnost položek v diagramu třídy, rychlost přes přechody mezi položkami pak zpomalit zaměřit se na důležité položky.

- **Používejte postupné nelineární uvolňování** z jednoho stavu do druhého, což dává pocit klidu a přirozeného pohybu.

- Pokud je to možné, **použijte jemnou animaci při najetí myší** k označení interaktivních prvků pod myší.

- Pokud ve svých funkcích silně spoléháte na animace, **poskytněte prostředky k jejich místnímu vypnutí** (pro všechny funkce) jako možnost v dialogovém okně **Nástroje > možnosti.**

- **Pouze jedna animace by měla nastat najednou** a sdělit pouze jednu část informace. Více než jeden objekt pohybující se nebo pokus udělit více věcí může být matoucí.

- **Jemnost je důležitá.** Ve většině případů animace nemusí vyžadovat pozornost uživatele sloužit svému účelu. Jemné změny v časování, sekvencování a chování může výrazně ovlivnit vnímání a může být rozdíl mezi efektivní a neefektivní animace.

- Pokud používáte animaci, abyste na něco **upozornili, ujistěte se, že stojí za to přerušit**myšlenkový pochod uživatele.

- **Při zobrazování průběhu nebo stavu** prostřednictvím animace:

  - Ukončení zobrazování pohybu průběhu, když základní proces nepostupuje.

  - Rozlišujte neurčité procesy od určitých procesů.

  - Ujistěte se, že animace má identifikovatelné dokončení a selhání stavy.

  - Minimalizujte využití animací efektů, které zobrazují stav, a ujistěte se, že mají skutečnou hodnotu, a to poskytnutím dalších informací o skutečném použití. Příklady zahrnují přechodné změny stavu a nouzové situace

#### <a name="animation-donts"></a>Animace nedělají:

- Nepoužívejte malé pohyby (pohyb v malém půdorysu). Upřednostňujte zeslabení a změny před pohybujícími se objekty.

- Nepoužívejte animace, které se konají na velké ploše obrazovky nemovitostí. Bez ohledu na velikost je tento styl animace pro uživatele rušivý.

- Nepoužívejte animace, které nesouvisejí s objektem, na který je uživatel aktuálně zaměřen nebo se kterým je interakce.

- Nepoužívejte animace, které vyžadují interakci uživatele k obnovení stavu, jako je vynucení uživatele reagovat na blikající oznámení, aby přestalo blikat. Interakce s nimi v žádném případě by měla být dostatečná k jejich propuštění.

Další informace o aplikacích pro tyto osvědčené postupy naleznete [v tématu Vzory animace](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Metriky animace

- Systém by měl viditelně reagovat na gesta uživatele za méně než 10 milisekund.

- Animované přechody by neměly trvat déle než 500 milisekund.

- Jedním ze způsobů, jak kompenzovat přechody, které vyžadují delší dobu, je rozdělit je na dvě části. První částí animace může být například prázdný kontejner obsahu (až 500 milisekund), následovaný obsahem, který do kontejneru vybledne (až 500 milisekund).

- Pro časy zatížení, které lze vypočítat, je upřednostňován indikátor určujícího průběhu (procentuální indikátor průběhu).

- Pro časy načítání, které nelze vypočítat, je vhodný indikátor zaneprázdnění, jako je kurzor nebo vložená animace otáčení (indikátor načítání nebo práce).

### <a name="animation-as-communicator"></a>Animace jako komunikátor
V uživatelském rozhraní sady Visual Studio animace funguje pouze jako komunikační nástroj.  Používá se ke komunikaci různých informací, jako jsou strukturální změny v ui (například při otevření nebo zavření nabídky). Animace může pomoci vizualizovat časově závislé chování složitých systémů, jako je vizualizace průběhu instalace. Animace lze také přitáhnout pozornost pomocí výstrah a oznámení.

 Animace uživatelského rozhraní obvykle fungují čtyřmi způsoby: vizualizovat, přitahovat pozornost, simulovat a časy odezvy /indikátory průběhu.

#### <a name="visualize"></a>Vizualizace
Animace může zdůraznit trojrozměrný charakter objektů a usnadnit uživatelům vizualizaci jejich prostorové struktury. K dosažení tohoto cíle může být nutné, aby animace otáčela objekt v plném kruhu, pomalu jej otáčela tam a zpět nebo objekt přibližovala a mírně zvětšovala jeho velikost, aby se zvýraznila změna nebo fokus.

Přestože trojrozměrné objekty mohou být přesunuty s uživatelským ovládacím prvkem, návrhář by měl předem určit (programově nebo ručně), jak nejlépe animovat pohyb, který poskytuje optimální pochopení objektu. Tato naprogramovaná animace pak může být aktivována uživatelem umístěním kurzoru nad objekt, zatímco uživatelem řízené pohyby vyžadují, aby uživatel pochopil, jak s objektem manipulovat. Omezte pohyb na jednu osu nebo orientaci najednou; měnit velikost, otáčet nebo překládat, ale neprovázejte více než jeden současně.

Kategorie Vizualizujte zahrnuje aspekty dat, vztahů, stavu, struktury, sekvence a času.

##### <a name="data"></a>Data
Ilustrují komplexní a variabilní informace:

- Procházení vizualizací informací, jako jsou grafy a grafy

- Krokování po sekvenci, prohlídka s průvodcem a stránkování

- Vyzvučování podrobností, ukazování a zvýraznění konkrétních informací

- Překrytí podrobností a dalších informací nad cíleným prvkem

- Morfing z jedné strukturální nebo organizační reprezentace do jiného

- Reprezentace změn v průběhu času pomocí posuvníků času, kol jog-and-shuttle a dopravních ovládacích prvků (přehrávání, zastavení a pozastavení)

##### <a name="relationships"></a>Relace

- Ilustrujte, jak se položky vzájemně vztahují nebo které položky se vztahují k dané položce.

- Zobrazit hierarchie a vztahy nadřazený podřízený nebo na stejné úrovni

- Jeden prvek spouští další

- Jeden prvek minimalizuje na jiný prvek

- Jeden prvek přivázaný k jinému

##### <a name="state"></a>Stav

- Aktualizace obsahu

- Zaměření a výběr uživatele

- Průběh

- chyby

##### <a name="structure"></a>Struktura

- Otočení struktury na jednom uzlu

- Přeorientování

- Minimalizace a maximalizace nebo rozbalení a sbalení

##### <a name="sequence"></a>Sequence

- Sekvence prezentace

- Listování obrázky

##### <a name="time"></a>Time

- Zobrazení změn v čase, časového intervalu a vysílání obrazovky

- Přesunutí do koše, zrušení a opakování

- Obnovit historický stav

#### <a name="attract-attention"></a>Upoutejte pozornost
Pokud je cílem upozornit uživatele na jeden prvek z několika nebo upozornit uživatele na aktualizované informace, může být vhodné animace. Úvodní stránka aplikace může například použít tlačítko Začínáme, které se po načtení stránky posune na místo.

Poslední pohyblivý prvek na obrazovce zpravidla přitahuje pozornost uživatele.  V sérii animovaných prvků bude pozornost uživatele sledovat poslední pohybující se objekt.

##### <a name="alert"></a>Výstrahy

- Upozornit uživatele, upoutat pozornost, ukázat pokrok

- Ukažte, že se něco děje správně nebo nesprávně, nebo zobrazte průběh nebo změny průběhu

- Vyzvat uživatele během úkolu, například najít další informace online nebo se dozvědět o aktuálním úkolu

##### <a name="notifications"></a>Oznámení

- Upozornit uživatele na chybový stav

- Přerušte uživatele, abyste zjistili, zda se chtějí věnovat něčemu jinému

- Jemně informujte uživatele, že proces byl dokončen nebo změněn, například po dokončení stahování.

#### <a name="simulate"></a>Simulovat
Tato kategorie zahrnuje tělesnost a dimenzionalitu.

- Ilustrujte, odkud objekty pocházejí nebo kam se

- Rozbalení a sbalení nebo otevření a zavření

- Posouvání, posouvání a otočení stránky

- Stohování a objednávání z

- Kolotoč a akordeon

- Převrácení a otočení ui

#### <a name="response-and-progress-indicators"></a>Ukazatele reakce a pokroku
Ukazatele pokroku mají několik významných výhod:

- Indikátory určitého i neurčitého průběhu ujišťují uživatele, že systém nehavaroval a pracuje na problému.

- Určité indikátory dávají uživateli pocit, jak daleko podél akce postupuje, stejně jako pocit, jak se blíží k cíli.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a>Vzory animace

### <a name="overview"></a>Přehled
Animace v sadě Visual Studio jsou určeny k poskytování určité funkce bez bránění produktivitě uživatelů. Obecně by animace v sadě Visual Studio měly být:

- Malé a nenápadné

- Přírodní a realistické

- Jemné a tlumené

- Rychlé a efektivní

- Uvolněná, ne uspěchaná

Tento obrázek znázorňuje styly animace, které doporučujeme pro Visual Studio. Nejčastěji se nepoužívají žádné animace ani jemné animace, jako je zeslabení/zeslabování. Existuje omezená aplikace pohybových animací, jako je rozbalení a smršťování, změna polohy X a Y a rotace.

![Doporučené styly animace pro Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Doporučené styly animace pro Visual Studio

#### <a name="appear-and-disappear"></a>Zobrazit a zmizet
S tímto vzorem prvek přepne z viditelné na out-of-view a zpět bez animace přechodu.

![Zobrazit a zmizet animace](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Zobrazit a zmizet animace

##### <a name="correct-usage"></a>Správné použití
Čerstvé prvky uživatelského rozhraní, které je třeba okamžitě zobrazit nebo zmizet, aby uživatel nebyl rozptylován ani blokován. Kromě toho mohou být pomalé animace vnímány jako odpor, ke kterému nedojde ve stylu zobrazení a zmizení.

##### <a name="incorrect-usage"></a>Nesprávné použití
Případy, ve kterých uživatelské rozhraní se zobrazí tak náhle uživatel nemá ponětí, co se stalo a přidání animace by pomohlo s kontextové porozumění.

##### <a name="animation-properties"></a>Vlastnosti animace
Časové zpoždění je obecně nula sekund.

##### <a name="examples"></a>Příklady
- Automatické skrytí oken nástrojů

- UI editoru aktivovaného klávesnicí, jako je IntelliSense a nápověda k parametrům

- Rozbalit a sbalit oblasti kódu

#### <a name="fade-in-and-fade-out"></a>Zeslabení a zeslabení
S tímto vzorem prvek ui přechody z není viditelné (0 % krytí) na viditelné (100 % krytí) nebo naopak.

![Animace zeslabení a zeslabení](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animace zeslabení a zeslabení

##### <a name="correct-usage"></a>Správné použití
Toto je nejčastěji doporučená animace uživatelského rozhraní. Je to jemný efekt, který zvyšuje zájem bez přerušení toku. V některých případech si uživatel nemusí ani uvědomit, že existuje animace, která vnímá hladký a plynulý systém uživatelského rozhraní.

##### <a name="animation-properties"></a>Vlastnosti animace

- Počáteční krytí: 0 % pro vyblednutí, 100 % pro vyblednutí

- Ukončení krytí: 100 % pro zeslabení, 0 % pro vyblednutí

- Doba trvání: 200 milisekund samostatně, 100 milisekund při použití jako součást kombinované sekvence animace

- Styl náběhu/doběhu: Sine InOut

##### <a name="examples"></a>Příklady

- Automatické skrytí oken nástrojů

- Nabídka otevřená a zavření

- Přechody na kartě Pozadí a popředí

#### <a name="color-blend-from-a-to-b"></a>Prolnutí barev od A do B
S tímto vzorkem se prvek ui změní z barvy A na barvu B.

![Animace prolnutí barev](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animace prolnutí barev

##### <a name="correct-usage"></a>Správné použití
Jako animovaný přechod, když prvek rozhraní změní barvu z jednoho kontextu nebo stavu do jiného.

##### <a name="animation-properties"></a>Vlastnosti animace

- Počáteční barva: Specifické pro uI

- Koncová barva: Specifické pro uI

- Doba trvání: 200 milisekund samostatně, 100 milisekund při použití jako součást kombinované sekvence animace

- Styl náběhu/doběhu: Sine InOut

##### <a name="examples"></a>Příklady

- Přechody stavu okna dokumentu (aktivní, poslední aktivní a neaktivní)

- Přechody stavu okna nástroje (zaostřené a nezaostřené)

#### <a name="expand-and-contract"></a>Rozšířit a uzavřít smlouvu
S tímto vzorem se prvek uživatelského rozhraní rozbalí v X, Y nebo v obou směrech.

![Rozbalit a zakázat animaci](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Rozbalit a zakázat animaci

##### <a name="correct-usage"></a>Správné použití
Jako animovaný přechod, když prvek rozhraní změní velikost z jednoho kontextu do druhého.

##### <a name="animation-properties"></a>Vlastnosti animace

- Měřítko X: % nebo specifický rozměr (v obrazových bodech)

- Měřítko Y: % nebo určitý rozměr (v obrazových bodech)

- Kotevní pozice: obvykle vlevo nahoře (pro jazyky zleva doprava) nebo vpravo nahoře (pro jazyky se zprava doleva)

- Doba trvání: 200 milisekund samostatně, 100 milisekund při použití jako součást kombinované sekvence animace

##### <a name="examples"></a>Příklady

- Panel Průzkumník architektury se rozbalí a sbalí

- Rozbalit a sbalit položku úvodní stránky Visual Studia 2017

#### <a name="x-y-position-change"></a>Změna polohy X-Y
Pomocí tohoto vzoru změní prvek uživatelského rozhraní svou polohu X nebo Y nebo obojí.

![Animace změny polohy X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animace změny polohy X-Y

##### <a name="correct-usage"></a>Správné použití
Jako animovaný přechod, když prvek rozhraní změní pozici z jednoho kontextu do druhého.

##### <a name="animation-properties"></a>Vlastnosti animace

- Počáteční pozice X a Y: specifické pro uživatelské ui

- Koncová pozice X a Y: Specifické pro uživatelské ui

- Cesta pohybu: žádná

- Doba trvání: 200 milisekund samostatně, 100 milisekund při použití jako součást kombinované sekvence animace

- Styl náběhu/doběhu: Sine InOut

##### <a name="example"></a>Příklad
Změna pořadí tabulátoru

#### <a name="rotate"></a>Otočit
S tímto vzorem se prvek ui otáčí.

![Animace otáčení prvku uživatelského rozhraní](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animace otáčení prvku uživatelského rozhraní

##### <a name="correct-usage"></a>Správné použití
Pouze pro indikátor neurčitého průběhu otáčení.

##### <a name="animation-properties"></a>Vlastnosti animace

- Stupeň rotace: 360

- Střed otáčení: uprostřed objektu

- Doba trvání: souvislá

##### <a name="example"></a>Příklad
Indikátor neurčitého průběhu (odstřeďování)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Běžné akce uživatelského rozhraní prostředí a doporučené animace

#### <a name="tab-open"></a>Otevřít tabulátor
![Animace otevření tabulátorem](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animace otevření tabulátorem

- Styl: objeví se

- Doba trvání: nula sekund

#### <a name="tab-close"></a>Zavření tabulátoru
![Animace zavření tabulátoru](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animace zavření tabulátoru

- Styl: X změna polohy

- Doba trvání: 200 milisekund

#### <a name="tab-reorder"></a>Pořadí při objednání tabulátoru
![Animace při objednání tabulátorů v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animace při objednání tabulátoru

- Styl: X změna polohy

- Doba trvání: 200 milisekund

#### <a name="close-floating-document"></a>Zavřít plovoucí dokument
![Zavřít animaci plovoucího dokumentu](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Zavřít animaci plovoucího dokumentu

- Styl: objeví se

- Doba trvání: 200 milisekund

#### <a name="window-state-transition"></a>Přechod stavu okna
![Animace přechodu stavu okna](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animace přechodu stavu okna

- Styl: Chcete-li být konzistentní s ostatními okny, nechte aktuální operační systém definovat animaci zavření dokumentu.

- Doba trvání: 200 milisekund

#### <a name="menu-open"></a>Nabídka otevřena
![Nabídka otevřít animaci](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Nabídka otevřít animaci

- Styl: zeslabuje

- Doba trvání: 200 milisekund

#### <a name="menu-close"></a>Zavření nabídky
![Animace zavření nabídky](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animace zavření nabídky

- Styl: zeslabuje

- Doba trvání: 200 milisekund

#### <a name="auto-hide-tool-window-reveal"></a>Automatické skrytí okna nástroje
![Automatické skrytí okna nástroje odhaluje animaci](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Automatické skrytí okna nástroje odhaluje animaci

- Styl: objeví se

- Doba trvání: nula sekund
