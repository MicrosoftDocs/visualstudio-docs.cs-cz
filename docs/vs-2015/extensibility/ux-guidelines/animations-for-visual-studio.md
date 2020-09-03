---
title: Animace
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c07fb0887ae01ec917b39f5d7537d5a78fb5a4c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825357"
---
# <a name="animations-for-visual-studio"></a>Animace pro Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Základní informace o animacích

### <a name="animation-best-practices-in-visual-studio"></a>Osvědčené postupy animace v aplikaci Visual Studio
 Použijte tato pravidla, abyste zajistili konzistentní a uživatelsky přívětivé styly animace napříč IDE sady Visual Studio.

- **Být selektivní.** Omezí animace na ty, které slouží k určitým účelům.

- **Načasování a rychlost jsou důležité** k zajištění toho, aby přechody byly rychlé a přirozené:

  - Dokončete animované přechody během jedné poloviny sekundy (500 milisekund).

  - Animace, ke kterým by došlo často, musí být dostatečně rychlé, aby nedošlo k přerušení pracovního postupu uživatele.

  - Animace by neměly být tak rychlé ani jarring, že je obtížné porozumět, ale ne tak zpomalit, aby byl přechod dokončen.

  - K zdůraznění důležitosti použijte proměnné časování. Například při procházení posloupnosti položek v diagramu tříd, rychlost přepínání mezi položkami a pak zpomalit fokus na důležité položky.

- **Použijte postupný nelineární náběh** a vývoj z jednoho stavu do druhého, což dává smysl Calm a přirozený pohyb

- Pokud je to možné, použijte k označení interaktivních prvků pod myší **nepoužitou animaci při najetí myší** .

- Pokud jste se sami spoléhat na animace ve vašich funkcích, **Poskytněte jim způsob, jak je** vypnout místně (pro všechny vaše funkce) jako možnost v dialogovém okně **Možnosti nástrojů >** .

- **V jednu chvíli by se měla objevit jenom jedna animace** a vyjádřit jenom jednu informaci.

- **Subtlety je důležité.** Ve většině případů animace nemusí vyžadovat pozornost pro uživatele, aby mohla poskytovat svůj účel. Malé změny časování, sekvencování a chování mohou výrazně ovlivnit vnímání a mohou způsobit rozdíl mezi efektivní a neúčinnou animací.

- Při použití animace k napodobení pozornosti k něčemu se **ujistěte, že stojí za to, že je možné přerušit**vlaky uživatele v myšlenkách.

- **Při zobrazování průběhu nebo stavu** prostřednictvím animace:

  - Ukončí zobrazování pohybu průběhu, když se původní proces nemění.

  - Rozlišuje neurčité procesy od procesů zrušení ukončení.

  - Ujistěte se, že animace má identifikovatelné stavy dokončování a selhání.

  - Minimalizujte používání animací efektu, které zobrazují stav, a ujistěte se, že mají skutečnou hodnotu tím, že poskytují dodatečné informace o skutečném využití. Příklady zahrnují přechodné změny stavu a mimořádné události.

#### <a name="do-not"></a>Ne:

- Používání malých pohybů (pohyb v malých prostorech), předchází a změny nad přesunutím objektů.

- Používejte animace, které probíhají v rámci velké oblasti obrazovky. Bez ohledu na velikost je tento styl animace uživateli odvolán.

- Používejte animace, které nesouvisí s objektem, na kterém je uživatel aktuálně zaměřen na nebo v interakci.

- Pomocí animací, které vyžadují interakci s uživatelem, můžete stav resetovat, například vynutí, aby uživatel reagoval na blikající oznámení, aby zastavil blikání. Interakce s nimi by měla být dostačující k jejich zavření.

  Další informace o aplikacích pro tyto osvědčené postupy najdete v tématu [vzory animace](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Metriky animace

- Systém by měl viditelně reagovat na gesta uživatele během méně než 10 milisekund.

- Dokončení animovaných přechodů by nemělo trvat déle než 500 milisekund.

- Jedním ze způsobů, jak kompenzovat přechody, které vyžadují delší dobu, je oddělení IT do dvou částí. první část animace může být například prázdný kontejner obsahu (až 500 milisekund) následovaný obsahem v kontejneru (až 500 milisekund).

- Pro dobu načítání, která může být vypočítána, je upřednostňován indikátor průběhu determinantu (ukazatel průběhu v procentech).

- Pro dobu načítání, která nelze vypočítat, je vhodný indikátor, jako je kurzor nebo vložená animovaná animace (načítání nebo pracovní indikátor).

### <a name="animation-as-communicator"></a>Animace jako Communicator
 V uživatelském rozhraní sady Visual Studio funkce animace funguje pouze jako komunikační nástroj.  Slouží ke sdělování nejrůznějších informací, jako jsou strukturální změny v uživatelském rozhraní. například při otevření nebo zavření nabídky. Animace může přispět k vizualizaci chování složitých systémů, jako je například vizualizace průběhu instalace nebo použití, k upoutání pozornosti výstrah a oznámení.

 Animace uživatelského rozhraní obvykle fungují čtyřmi způsoby: vizualizace, přilákat pozornost, simulovat a označovat dobu odezvy a průběh.

#### <a name="visualize"></a>Vizualizace
 Animace může zdůraznit trojrozměrného charakteru objektů a usnadnit uživatelům vizualizaci jejich prostorové struktury. K dosažení této situace může animace potřebovat otočit objekt v plné kružnici, pomalu ho znovu zapnout a vypnout nebo objekt přiblížit a mírně zvýšit jeho velikost, aby se zdůraznila výměna nebo fokus.

 Přestože trojrozměrné objekty lze přesunout pomocí uživatelského ovládacího prvku, Návrhář by měl předem určit (programově nebo ručně), jak nejlépe animovat pohyb, který poskytuje optimální porozumění objektu. Tuto programovou animaci pak může aktivovat uživatel umístěním ukazatele myši na objekt, zatímco uživatelem kontrolované pohyby vyžadují, aby uživatel pochopil, jak objekt manipulovat. Omezte pohyb na jednu osu nebo orientaci v čase. Můžete buď škálovat, otáčet, nebo překládat, ale neprovádět více než jednu současně.

 Kategorie vizualizovat zahrnuje aspekty dat, vztahů, stavu, struktury, sekvence a času.

##### <a name="data"></a>Data
 Ilustraci komplexních a proměnných informací:

- Pohyb prostřednictvím vizualizací informací, jako jsou grafy a grafy

- Krokování sekvencí, průvodcem a stránkováním

- Podrobnosti o volání, ukazující a zvýraznění konkrétních informací

- Překrytí podrobností a dalších informací nad prvkem s fokusem

- Polymorfismuing z jedné strukturální nebo organizační reprezentace do jiné

- Reprezentace změn v průběhu času pomocí posuvníků času, běhu kol a přenosových mechanismů (přehrát, zastavit a pozastavit).

##### <a name="relationships"></a>Relace

- Ilustruje, jak se položky vztahují na jednu jinou nebo které položky se vztahují k dané položce.

- Zobrazit hierarchie a vztahy nadřazenosti a podřízenosti nebo na stejné úrovni

- Jeden element vytvářený další

- Jeden prvek se minimalizuje na jiný element.

- Jeden prvek, který je připojený k jinému

##### <a name="state"></a>Stav

- Aktualizace obsahu:

- Fokus a výběr uživatele

- Průběh

- Chyby

##### <a name="structure"></a>Struktura

- Překlopení struktury na jednom uzlu

- Přeorientování

- Minimalizace a maximalizace nebo rozbalení a sbalení

##### <a name="sequence"></a>Sequence

- Sekvence prezentace

- Překlápění obrázků

##### <a name="time"></a>Čas

- Zobrazit změnu v čase, časové prodlevě a záznam dění na pozadí

- Přesunout na odpadkový koš, zpět a znovu

- Obnovit historický stav

#### <a name="attract-attention"></a>Pozornost přilákat
 Pokud je cílem nakreslit pozornost uživatele na jeden prvek z několika nebo upozornit uživatele na aktualizované informace, může být animace vhodná. Například úvodní stránka vaší aplikace může použít tlačítko Začínáme, které se snímky na místo načte po načtení stránky.

 Jako pravidlo se poslední přesunutí elementu na obrazovce připraví pozornost uživatele.  V řadě animovaných prvků bude pozornost uživatele následovat za posledním přesunutým objektem.

##### <a name="alert"></a>Výstrahy

- Upozornit uživatele, získat pozornost, zobrazit průběh

- Ukáže, že se něco dělá správně nebo není správně nebo se zobrazuje průběh nebo průběh.

- Vyzvat uživatele během úkolu, například najít další informace online nebo získat informace o aktuální úloze

##### <a name="notifications"></a>Oznámení

- Upozorní uživatele na chybovou podmínku.

- Přerušit uživatele, aby viděli, jestli se chce zúčastnit nějakého jiného

- Jemně Informujte uživatele, že se proces dokončil nebo změnil, například když se stažení dokončí.

#### <a name="simulate"></a>Simulovat
 Tato kategorie se týká fyzického a dimenzionálního.

- Ilustrovat místo, odkud pocházejí objekty z nebo kam přejít

- Rozbalit a sbalit nebo otevřít a zavřít

- Posunování, posouvání a zobrazování stránek

- Skládání a řazení z

- Karusel a přiznávání

- Překlopení a otočení uživatelského rozhraní

#### <a name="response-and-progress-indicators"></a>Indikátory odezvy a postupu
 Indikátory průběhu mají několik významných výhod:

- Jak ukončit a neurčitý indikátor průběhu znovu zaručí uživateli, že došlo k chybě systému a na problému pracuje.

- Indikátory zrušení ukončení poskytují uživateli představu o tom, jak daleko v rámci akce probíhá, a nemůžete se dostat blíž k dokončení.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Vzorce animace

### <a name="overview"></a>Přehled
 Animace v aplikaci Visual Studio jsou určeny k obsluze konkrétní funkce a nebrání produktivitě uživatelů. Mezi obecné charakteristiky animace, které se mají dodržet:

- Malý a nenápad

- Přirozené a realistické

- Jemný a subdued

- Rychlé a efektivní

- Uvolněno, není hurried

  Následující ilustrace znázorňuje styly animace doporučené pro použití v aplikaci Visual Studio. Nejčastěji používané nejsou žádné animace a jemné animace, jako je například rozzvolna nebo Zeslabit. Existují omezené aplikace pro přesun animací, jako je například rozbalení a kontrakt, změna pozice X a Y a rotace.

  ![Doporučené styly animace pro Visual Studio](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202 – a_VSAnimStyles")

  **Doporučené styly animace pro Visual Studio**

#### <a name="appear-and-disappear"></a>Zobrazí se a zmizí
 V tomto modelu se element přepne z viditelnosti na mimo zobrazení a zpátky bez animace přechodu:

 ![Zobrazí&#47;zmizí animace v aplikaci Visual Studio.](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202 – b_AppearAndDisappear")

##### <a name="correct-usage"></a>Správné použití
 Nové prvky uživatelského rozhraní, které se musí okamžitě zobrazit nebo zmizet, aby uživatel nebyl ani nerušivý ani nepřesný. Kromě toho může být pomalé přesunutí animací možné vnímat jako ukazatel výkonu, který se neobjeví se stylem zobrazení a zmizení.

##### <a name="incorrect-usage"></a>Nesprávné použití
 Případy, kdy se uživatelské rozhraní objeví tak náhlé, že uživatel nenápadí, co se stalo, a Přidání animace by vám pomohly kontextové porozumění.

##### <a name="animation-properties"></a>Vlastnosti animace
 Časová prodleva je všeobecně nula sekund.

##### <a name="examples"></a>Příklady

- Automaticky skrývat okna nástrojů

- Editor aktivovaných klávesnicí – uživatelské rozhraní, například IntelliSense a parametr help

- Rozbalení oblastí kódu a jejich sbalení

#### <a name="fade-in-and-fade-out"></a>Zmizení a rozmizet
 V tomto modelu se prvky uživatelského rozhraní přechází z neviditelného (0% opacity) na viditelné (100% opacity) nebo naopak:

 ![Rozzvolna&#45;v&#47;zeslabení animace&#45;ven v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202 – c_FadeInFadeOut")

##### <a name="correct-usage"></a>Správné použití
 Toto je nejčastěji doporučená animace uživatelského rozhraní. Nejedná se o jemný efekt, který přináší úroky bez přerušení toku. V některých případech se může stát, že uživatel ani nezjistí, že je k dispozici animace a jednoduše vyplynulě vyhlazuje systém uživatelského rozhraní.

##### <a name="animation-properties"></a>Vlastnosti animace

- Počáteční krytí: 0% pro zmizení, 100% pro rozběhu

- Ukončení neprůhlednosti: 100% pro zmizení, 0% pro rozběhu

- Doba trvání: 200 milisekund samostatné, 100 milisekund při použití jako součást kombinace animační sekvence

- Náběh Style: sinus InOut

##### <a name="examples"></a>Příklady

- Automaticky skrývat okna nástrojů

- Nabídka otevřít a zavřít

- Přechody na pozadí a na kartě popředí

#### <a name="color-blend-from-a-to-b"></a>Barevný Blend z A do B
 V tomto modelu se prvek uživatelského rozhraní změní z barvy A na Color B:

 ![Animace prolnutí barev v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202 – d_ColorBlend")

##### <a name="correct-usage"></a>Správné použití
 Jako animovaný přechod, pokud prvek uživatelského rozhraní změní barvu z jednoho kontextu nebo stavu na jiný.

##### <a name="animation-properties"></a>Vlastnosti animace

- Počáteční barva: specifické pro uživatelské rozhraní

- Koncová barva: specifické pro uživatelské rozhraní

- Doba trvání: 200 milisekund samostatné, 100 milisekund při použití jako součást kombinace animační sekvence

- Náběh Style: sinus InOut

##### <a name="examples"></a>Příklady

- Přechody stavu okna dokumentu (aktivní, poslední aktivní a neaktivní)

- Přechody stavu okna nástroje (cílené a nevybrané)

#### <a name="expand-and-contract"></a>Rozbalit a kontrakt
 V tomto modelu se prvky uživatelského rozhraní rozšiřují do X, Y nebo obou směrů:

 ![Rozbalení&#47;animace kontraktu v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202 – e_ExpandContract")

##### <a name="correct-usage"></a>Správné použití
 Jako animovaný přechod, pokud prvek uživatelského rozhraní změní velikost z jednoho kontextu do jiného.

##### <a name="animation-properties"></a>Vlastnosti animace

- Měřítko X:% nebo konkrétní dimenze (v pixelech)

- Měřítko Y:% nebo konkrétní dimenze (v pixelech)

- Pozice kotvy: všeobecně vlevo nahoře (pro jazyky zleva doprava) nebo vpravo nahoře (pro jazyky se zápisem zprava doleva)

- Doba trvání: 200 milisekund samostatné, 100 milisekund při použití jako součást kombinace animační sekvence

##### <a name="examples"></a>Příklady

- Rozbalení a sbalení panelu Průzkumníka architektury

- Rozbalit a sbalit položku úvodní stránky

#### <a name="x-y-position-change"></a>Změna pozice X-Y
 V tomto vzoru prvek uživatelského rozhraní změní svou polohu X nebo Y nebo obojí:

 ![Animace změny pozice X&#47;Y v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202 – f_XYPositionChange")

##### <a name="correct-usage"></a>Správné použití
 Jako animovaný přechod, pokud prvek uživatelského rozhraní změní polohu z jednoho kontextu do jiného.

##### <a name="animation-properties"></a>Vlastnosti animace

- Počáteční pozice X a Y: specifické pro uživatelské rozhraní

- Koncová pozice X a Y: specifické pro uživatelské rozhraní

- Cesta pohybu: žádné

- Doba trvání: 200 milisekund samostatné, 100 milisekund při použití jako součást kombinace animační sekvence

- Náběh Style: sinus InOut

##### <a name="example"></a>Příklad
 Změna pořadí karet

#### <a name="rotate"></a>Otočit
 V tomto modelu se prvek uživatelského rozhraní otočí:

 ![Otočení animace v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202 – g_Rotate")

##### <a name="correct-usage"></a>Správné použití
 Pouze pro indikátor neurčitého průběhu.

##### <a name="animation-properties"></a>Vlastnosti animace

- Stupeň rotace: 360

- Rotační centrum: střed objektu

- Trvání: průběžné

##### <a name="example"></a>Příklad
 Neurčitý indikátor průběhu (otáčející se)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Běžné akce uživatelského rozhraní prostředí a doporučené animace

#### <a name="tab-open"></a>Otevřená karta

- Style: zobrazí se

- Doba trvání: nula sekund

  ![Otevřená animace na kartě v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202 – h_TabOpen")

#### <a name="tab-close"></a>Zavřít kartu

- Styl: Změna pozice X

- Doba trvání: 200 milisekund

  ![Animace zavření tabulátoru v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202 – i_TabClose")

#### <a name="tab-reorder"></a>Změna pořadí karet

- Styl: Změna pozice X

- Doba trvání: 200 milisekund

  ![Změna pořadí animací v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202 – j_TabReorder")

#### <a name="close-floating-document"></a>Zavřít plovoucí dokument

- Style: zobrazí se

- Doba trvání: 200 milisekund

  ![Zavření plovoucí animace dokumentů v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202 – k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>Přechod stavu okna

- Styl: Chcete-li být konzistentní s jinými okny, nechte aktuální operační systém definovat animaci zavřít dokument.

- Doba trvání: 200 milisekund

  ![Animace přechodu na stav okna v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202 – l_WindowStateTransition")

#### <a name="menu-open"></a>Nabídka otevřená

- Style: zeslabit

- Doba trvání: 200 milisekund

  ![Nabídka otevřít animaci v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202 – m_MenuOpen")

#### <a name="menu-close"></a>Zavřít nabídku

- Styl: rozmizet

- Doba trvání: 200 milisekund

  ![Zavřít nabídku animace v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202 – n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>Automaticky skrývat zobrazení oken nástrojů

- Style: zobrazí se

- Doba trvání: nula sekund

  ![Automatické&#45;skrytí animace oken nástrojů v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202 – o_AutoHideToolWindowReveal")
