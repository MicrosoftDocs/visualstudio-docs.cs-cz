---
title: Animace
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b74a283a4142cea7753db6e04d922517ae32afe9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052097"
---
# <a name="animations-for-visual-studio"></a>Animace pro sadu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Základy animace

### <a name="animation-best-practices-in-visual-studio"></a>Osvědčené postupy animace v sadě Visual Studio
 Postupujte podle těchto pravidel zajistit konzistentní a uživatelsky přívětivé animace, styly v integrovaném vývojovém prostředí sady Visual Studio.

-   **Pečlivě.** Omezit animací na ty, které mají konkrétní účely.

-   **Načasování a rychlost jsou důležité** zajistit, že přechody pocit, že rychlé a přirozené:

    -   Dokončení animovaný přechodů v rámci jedné půl sekundy (500 milisekund).

    -   Animace, které by tomu bylo, často je potřeba dostatečně rychle, že jejich není přerušení pracovního postupu uživatele.

    -   Animace by neměl být tak rychlé nebo jarring, že je obtížné porozumět, ale ne tak pomalé, že je jeden netrpělivý pro přechod na Dokončit.

    -   Pomocí proměnné časování zdůraznění důležitosti. Během procházení posloupnost položek v diagramu tříd, rychlost prostřednictvím přechody mezi položkami pak zpomalit soustředit na důležité položky.

-   **Použití postupné nelineárních usnadnění** z jednoho stavu do druhého, dává smysl klidné a přirozené pohybu

-   Pokud je to možné, **použijte drobným animaci při najetí myší** udávajících interaktivní prvky pod myší.

-   Pokud se spoléháte silně na animace v funkce potom **prostředkem, chcete-li vypnout** místně (pro všechny funkce) jako možnost v **nástroje > Možnosti** dialogového okna.

-   **Pouze jedné animace se budou objevovat v čase** a sdělit pouze jednu část informací.

-   **Subtlety je důležité.** Ve většině případů animace nemusí pozornost uživatele vyžádání její účel. Malých změn časování, pořadí a chování může významně ovlivnit vnímání a může být rozdíl mezi animace efektivní a neefektivní.

-   Při použití animace k přitažení pozornosti ke něco, **Ujistěte se, že je vhodné by to ovlivnilo uživatele**společnosti myšlenek.

-   **Při zobrazení stav nebo průběh** prostřednictvím animace:

    -   Přestane zobrazovat text průběhu přesunu, pokud není posunutí základního procesu.

    -   Neurčitá procesy odlišili od determinate procesy.

    -   Zajistěte, aby animace identifikovatelné stavy ukončení a selhání.

    -   Minimalizujte použití animací efekt, které zobrazují stav a ujistěte se, jestli obsahují skutečné hodnoty tím, že poskytuje další informace o skutečném použití. Mezi příklady patří přechodný stav se změní a nouzové situace co

#### <a name="do-not"></a>Ne:

- Použít malé pohybů plb typu (pohyb v malé náklady), preferují sníží (zesvětlí) a změny v průběhu přesouvání objektů.

- Použití animací probíhat přes velké části plochy obrazovky. Bez ohledu na velikost je tento styl animace rušivé uživateli.

- Použití animací, které nesouvisí se objekt, který uživatel právě fokus na nebo interakci s.

- Použití animací vyžadující interakci uživatele resetovat stav, jako je například vynucení uživatele blikající oznámení, aby bylo možné ho zastavit blikat reagovat. Interakce s nimi žádným způsobem by měla stačit zrušit je.

  Další informace o aplikacích pro tyto osvědčené postupy najdete v tématu [animace vzory](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Animace metriky

-   Systém by měl viditelně reakce na ně uživatel gesta v méně než 10 milisekund.

-   Animované přechody by neměl trvat déle než 500 milisekund do dokončení.

-   Jedním ze způsobů, aby se vykompenzovalo přechody, které vyžadují delší dobu je rozdělit do dvou částí; první část animace například může být prázdný obsah kontejner (až 500 milisekund) následované obsahu vyblednutí do kontejneru (až 500 milisekund).

-   Pro dobu načítání, které je možné vypočítat indikátor průběhu určujícím (v procentech průběhu) je upřednostňována.

-   Pro dobu načítání, které nelze vypočítat je vhodné indikátor zaneprázdnění například kurzoru nebo vložený pokryjte animace (pracovní ukazatele nebo načítání).

### <a name="animation-as-communicator"></a>Animace jako communicator
 V sadě Visual Studio UI animace funguje pouze jako nástroj pro komunikaci.  Používá se pro komunikaci širokou škálu informací, jako jsou například strukturální změny v uživatelském rozhraní; Když například nabídky otevře nebo zavře. Animace pomáhají vizualizovat chování závislé na čase komplexních systémů, jako je vizualizace průběhu instalace nebo použít k přitahují pozornost výstrahy a oznámení.

 Animace v uživatelském rozhraní funkce obvykle čtyři způsoby: vizualizace, upoutat pozornost, simulaci a označuje odpověď časy/průběh.

#### <a name="visualize"></a>Vizualizace
 Animace lze zvýraznění trojrozměrného povaze objektů a usnadňují uživatelům vizualizovat svá prostorová struktury. Za tím účelem animace může potřebovat aktivovat objekt v úplné kruh, pomalu zapnout vpřed a zpět, nebo Přenést blíž objekt a mírně se zvýší velikost zdůraznit výměny nebo fokus.

 I když trojrozměrné objekty mohou být přesunuty s uživatelský ovládací prvek, Návrhář ujasnit některé věci předem (prostřednictvím kódu programu nebo ručně) jak pro nejlepší animace pohybu, která poskytuje optimální Principy objektu. To naprogramovat animace může pak být uživatel aktivoval tím, že kurzor umístíte na objekt, zatímco řízené uživatelem pohybů plb typu vyžadovat, aby pochopit, jak pracovat s objektu. Omezit pohyb jednu osu nebo orientace najednou. buď škálování, otočit, nebo přeložit, ale neprovádějte více než jeden současně.

 Vizualizace kategorie zahrnuje aspekty dat, relace, stavu, struktura, pořadí a čas.

##### <a name="data"></a>Data
 Ukazuje proměnné a komplexní informace:

-   Procházení vizualizace informace, jako jsou tabulky a grafy

-   Krokování sekvenci, průvodce a stránkování

-   Volání podrobnosti, odkazující a zvýraznění konkrétních informací

-   Překryvné podrobnosti a další informace o element s fokusem

-   Morfingu prvku z jednoho znázornění strukturální nebo organizace do jiného

-   Představující změny v čase pomocí jezdců, rozsvítit shuttle kola a ovládací prvky pro přenos (přehrávání, zastavení a pozastavit).

##### <a name="relationships"></a>Relace

-   Ukazuje, jak k sobě vztahují položky nebo položky, které se vztahují na danou položku.

-   Zobrazení hierarchie a nadřazenosti a podřízenosti nebo na stejné úrovni vztahů

-   Jiné vytvoří jeden element.

-   Jeden element minimalizuje na jiný element

-   Jeden element připojeném do jiného

##### <a name="state"></a>Stav

-   Aktualizace obsahu.

-   Výběr a fokus uživatele

-   Průběh

-   Chyby

##### <a name="structure"></a>Struktura

-   Přesun konstrukce na jeden uzel

-   Převedení

-   Minimalizovat a maximalizovat, nebo rozbalit nebo sbalit

##### <a name="sequence"></a>Pořadí

-   Prezentace pořadí

-   Překlopení prostřednictvím obrázky

##### <a name="time"></a>čas

-   Zobrazení změn v průběhu času, časová prodleva a záznam dění na monitoru

-   Přesunout do koše, vrátit zpět a znovu:

-   Obnovit Historický stav

#### <a name="attract-attention"></a>Upoutat pozornost
 Pokud je cílem upozornit uživatele na jeden element z několika nebo o upozornění uživatele, aby aktualizované informace, může být vhodné animace. Úvodní stránky aplikace může například použít tlačítko Začínáme, který se posune na místě po načtení stránky.

 Poslední přesunutí prvek na obrazovce jako pravidlo, upoutat pozornost uživatele.  V řadě animované elementy postupujte podle uživatele pozornost poslední přesunutí objektu.

##### <a name="alert"></a>Upozornění

-   Upozornit uživatele, získejte pozornost, zobrazit průběh

-   Zobrazit, že něco se provádí správně nebo nesprávně nebo zobrazit průběh nebo probíhající změny

-   Dotázat se uživatele během úlohy, jako je například hledání další informace online nebo získávání informací o aktuální úloze

##### <a name="notifications"></a>Oznámení

-   Upozornit uživatele o chybovou podmínku

-   Přerušit uživatelům zobrazit, pokud se chcete věnovat jiné činnosti

-   Jemně uživatele informuje, že proces dokončí nebo změnit, jako je například po dokončení stahování.

#### <a name="simulate"></a>Simulace
 Tato kategorie zahrnuje physicality a dimenzionalitu.

-   Ukazuje, odkud pochází objekty nebo kde přejdou na

-   Rozbalení a sbalení nebo otevření a zavření

-   Posouvání, posouvání a stránku displeje

-   Překrývání a pořadí z-ordering

-   Prezentace a prvku typu accordion

-   Převracení a otáčení uživatelského rozhraní

#### <a name="response-and-progress-indicators"></a>Indikátory odpovědi a průběh
 Indikátory průběhu mají několik významné výhody:

-   Oba indikátory determinate a neurčitého průběhu ujišťovat uživatele, který systém nebyl došlo k chybě a pracuje na problém.

-   Determinate indikátory dát uživateli, který představu o tom, jak daleko podél akce probíhá, a také pocit blíž k dokončení.

##  <a name="BKMK_AnimationPatterns"></a> Vzory animace

### <a name="overview"></a>Přehled
 Animace v sadě Visual Studio mají sloužit konkrétní funkci a není překážkou snížení produktivity uživatelů. Obecné animace vlastnosti dodržovat patří:

- Malé a nerušivý

- Fyzická a realistické

- Tlumeném a současně lákavé

- Rychlé a efektivní

- Volný, ne hurried

  Následující obrázek znázorňuje styly animace doporučené pro použití v sadě Visual Studio. Například fade žádná animace a drobným animace / setmění se nejčastěji používají. Omezené aplikace pohybu animace například rozbalte a smlouvy, poloha změny a otáčení X a Y.

  ![Doporučuje se animace, styly pro Visual Studio](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202 a_VSAnimStyles")

  **Doporučené animace styly pro sadu Visual Studio**

#### <a name="appear-and-disappear"></a>Zobrazí a zmizí
 V tomto modelu přepne element z viditelné mimo zobrazení a zpět bez přechodu animace:

 ![Zobrazí&#47;zmizí animace v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202 b_AppearAndDisappear")

##### <a name="correct-usage"></a>Správné použití
 Nové prvky uživatelského rozhraní, které je potřeba okamžitě zobrazí nebo zmizí, takže uživatel odváděna ani nelze blokovat. Pomalé přesunutí animace kromě toho může být vnímané jako výkonu přetažení, která obnoví se stylem jsou zobrazeny a zmizí.

##### <a name="incorrect-usage"></a>Nesprávné použití
 Případy, ve kterých uživatelského rozhraní se zobrazí tak náhle že uživatel nemá žádné nápad co se stalo a přidání animace by pomohl s kontextové pochopení.

##### <a name="animation-properties"></a>Animace vlastností
 Doba zpoždění je obvykle nula sekund.

##### <a name="examples"></a>Příklady

-   Automatického skrytí oken nástrojů

-   Aktivovat klávesnice editor uživatelského rozhraní, jako je například technologie IntelliSense a parametru nápovědy

-   Oblasti rozbalení a sbalení kódu

#### <a name="fade-in-and-fade-out"></a>Vysouvaly a fade-out
 V tomto modelu prvek uživatelského rozhraní změní z nejsou viditelné (krytí 0 %) na viditelné (100 % neprůhlednost) nebo naopak:

 ![Fade&#45;v&#47;Fade&#45;si animace v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202 c_FadeInFadeOut")

##### <a name="correct-usage"></a>Správné použití
 Tato možnost se doporučuje nejčastěji animace uživatelského rozhraní. Je malý vliv, který přidá zájmu bez přerušení tok. V některých případech může uživatel nemusí i dobré si uvědomit, že je animace a jednoduše zjistí plynulé a na průchodu uživatelského rozhraní systému.

##### <a name="animation-properties"></a>Animace vlastností

-   Spouští se krytí: % 0 pro vysouvaly, 100 % po dobu fade-out

-   Koncová krytí: 100 % po dobu vysouvaly, 0 % fade-out

-   Doba trvání: 200 MS samostatné 100 milisekund, když se použije jako součást kombinaci animační sekvence.

-   Usnadnění style: InOut sinus

##### <a name="examples"></a>Příklady

-   Automatického skrytí oken nástrojů

-   Nabídka otevřít a zavřít

-   Na pozadí a popředí kartu přechody

#### <a name="color-blend-from-a-to-b"></a>Barva blendu od A do B
 V tomto modelu prvek uživatelského rozhraní změní z barev A barvu B:

 ![Barva blend animace v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202 d_ColorBlend")

##### <a name="correct-usage"></a>Správné použití
 Jako animovaný přechodu, když prvku uživatelského rozhraní změní barvu z kontextu nebo stavu do druhého.

##### <a name="animation-properties"></a>Animace vlastností

-   Počáteční barva: konkrétní uživatelského rozhraní

-   Koncová barva: konkrétní uživatelského rozhraní

-   Doba trvání: 200 MS samostatné 100 milisekund, když se použije jako součást kombinaci animační sekvence.

-   Usnadnění style: InOut sinus

##### <a name="examples"></a>Příklady

-   Zdokumentujte přechodů mezi stavy okno (aktivní, naposledy aktivní i neaktivní)

-   Nástroj přechodů mezi stavy okno (zaměření a bez fokusu)

#### <a name="expand-and-contract"></a>Rozbalte a smlouvy
 V tomto modelu se rozbalí prvku uživatelského rozhraní v X, Y nebo v obou směrech:

 ![Rozbalte&#47;smlouvy animace v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202 e_ExpandContract")

##### <a name="correct-usage"></a>Správné použití
 Jako animovaný přechodu, když prvku uživatelského rozhraní se změní velikost z jednoho kontextu do jiného.

##### <a name="animation-properties"></a>Animace vlastností

-   X rozsahu: % nebo konkrétní dimenzi (v pixelech)

-   Y rozsahu: % nebo konkrétní dimenzi (v pixelech)

-   Ukotvit pozice: obecně levou horní (pro jazyky zleva doprava) nebo pravém (pro jazyky zprava doleva)

-   Doba trvání: 200 MS samostatné 100 milisekund, když se použije jako součást kombinaci animační sekvence.

##### <a name="examples"></a>Příklady

-   Panel Průzkumníka architektuře, rozbalíte nebo sbalíte

-   Úvodní stránka položky rozbalit nebo sbalit

#### <a name="x-y-position-change"></a>X-Y pozice změn
 V tomto modelu prvek uživatelského rozhraní změní jeho pozice X nebo Y nebo obojí:

 ![X&#47;pozice Y Změna animace v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202 f_XYPositionChange")

##### <a name="correct-usage"></a>Správné použití
 Jako animovaný přechodu, když prvku uživatelského rozhraní se změní pozice v jednom kontextu do jiného.

##### <a name="animation-properties"></a>Animace vlastností

-   Spouští se X a Y pozice: konkrétní uživatelského rozhraní

-   Koncová X a Y pozice: konkrétní uživatelského rozhraní

-   Dráhu pohybu: žádné

-   Doba trvání: 200 MS samostatné 100 milisekund, když se použije jako součást kombinaci animační sekvence.

-   Usnadnění style: InOut sinus

##### <a name="example"></a>Příklad
 Změna pořadí karty

#### <a name="rotate"></a>Otočit
 V tomto modelu se otočí prvek uživatelského rozhraní:

 ![Otočit animace v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202 g_Rotate")

##### <a name="correct-usage"></a>Správné použití
 Pouze pro neurčitý rotující indikátor průběhu.

##### <a name="animation-properties"></a>Animace vlastností

-   Úhel otočení: 360

-   Otočení center: střední objektu

-   Doba trvání: průběžné

##### <a name="example"></a>Příklad
 Indikátor neurčitého průběhu (rotujících)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Běžné akce uživatelského rozhraní prostředí a doporučené animace

#### <a name="tab-open"></a>Otevřete kartu

- Style: Zobrazí

- Doba trvání: Nula sekund

  ![Karta otevřít animace v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202 h_TabOpen")

#### <a name="tab-close"></a>Zavřete kartu

- Styl: Změnit pozice X

- Doba trvání: 200 MS

  ![Karta zavřít animace v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202 i_TabClose")

#### <a name="tab-reorder"></a>Změnit pořadí karty

- Styl: Změnit pozice X

- Doba trvání: 200 MS

  ![Kartě animace přesunout v pořadí v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202 j_TabReorder")

#### <a name="close-floating-document"></a>Zavřít dokument s plovoucí desetinnou čárkou

- Style: Zobrazí

- Doba trvání: 200 MS

  ![Plovoucí dokument animace v sadě Visual Studio Zavřít](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202 k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>Okno přechod stavu

- Style: Pro zajištění konzistence s ostatními okny, umožňují definovat animace zavřít dokument aktuálního operačního systému.

- Doba trvání: 200 MS

  ![Okno stavu přechodu animace v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202 l_WindowStateTransition")

#### <a name="menu-open"></a>Otevřete nabídku

- Style: vysouvaly

- Doba trvání: 200 MS

  ![Nabídka animace otevřít v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202 m_MenuOpen")

#### <a name="menu-close"></a>Zavřete nabídku

- Style: Fade-out

- Doba trvání: 200 MS

  ![Nabídka zavřít animace v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202 n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>Zobrazit okno nástroje automatického schovávání

- Style: Zobrazí

- Doba trvání: Nula sekund

  ![Automatické&#45;skrýt animace okno nástroje v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")
