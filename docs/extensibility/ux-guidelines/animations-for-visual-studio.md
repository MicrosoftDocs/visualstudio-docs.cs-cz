---
title: Animace pro Visual Studio | Microsoft Docs
description: Seznamte se s pravidly, která vám pomůžou zajistit konzistentní a uživatelsky přívětivé styly animace napříč prostředím IDE sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c86b033986511100415989e76f4f1e6ef7702f10
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715948"
---
# <a name="animations-for-visual-studio"></a>Animace pro Visual Studio
## <a name="animation-fundamentals"></a>Základní informace o animacích

### <a name="animation-best-practices-in-visual-studio"></a>Osvědčené postupy animace v aplikaci Visual Studio
Použijte tato pravidla, abyste zajistili konzistentní a uživatelsky přívětivé styly animace v rámci integrovaného vývojového prostředí sady Visual Studio.

- **Být selektivní.** Omezí animace na ty, které slouží k určitým účelům.

- **Načasování a rychlost jsou důležité** k zajištění toho, aby přechody byly rychlé a přirozené:

  - Dokončete animované přechody během jedné poloviny sekundy (500 milisekund).

  - Animace, ke kterým by došlo často, musí být dostatečně rychlé, aby nedošlo k přerušení pracovního postupu uživatele. Podívejte se na animaci ve smyčce a upravte časování, dokud nebude napravo.

  - Animace by neměly být tak rychlé nebo jarring, že je obtížné porozumět, ale ne tak zpomalit, aby byl přechod dokončen.

  - K zdůraznění důležitosti použijte proměnné časování. Například při procházení posloupnosti položek v diagramu tříd, rychlost přepínání mezi položkami a pak zpomalit fokus na důležité položky.

- **Použijte postupný nelineární náběh** a vývoj z jednoho stavu do druhého, což dává smysl Calm a přirozený pohyb.

- Pokud je to možné, použijte k označení interaktivních prvků pod myší **nepoužitou animaci při najetí myší** .

- Pokud jste se sami spoléhali na animace ve vašich funkcích, **Poskytněte jim způsob, jak je** vypnout místně (pro všechny vaše funkce) jako možnost v dialogovém okně **nástroje > možnosti** .

- **V jednu chvíli by se měla objevit jenom jedna animace** a vyjádřit jenom jednu informaci. Více než jeden objekt přesouvá nebo se pokouší vyjádřit více věcí, může být matoucí.

- **Subtlety je důležité.** Ve většině případů animace nemusí vyžadovat pozornost uživatele, aby mohla poskytovat svůj účel. Malé změny časování, sekvencování a chování mohou výrazně ovlivnit vnímání a mohou způsobit rozdíl mezi efektivní a neúčinnou animací.

- Při použití animace k navýšení pozornosti na něco se **ujistěte, že stojí za to, že je možné přerušit** vlaky uživatele v myšlenkách.

- **Při zobrazování průběhu nebo stavu** prostřednictvím animace:

  - Ukončí zobrazování pohybu průběhu, když se základní proces nemění.

  - Rozlišuje neurčité procesy od procesů zrušení ukončení.

  - Ujistěte se, že animace má identifikovatelné stavy dokončování a selhání.

  - Minimalizujte používání animací efektu, které zobrazují stav, a ujistěte se, že mají skutečnou hodnotu tím, že poskytují dodatečné informace o skutečném využití. Příklady zahrnují přechodné změny stavu a mimořádné události.

#### <a name="animation-donts"></a>Don'ts animace:

- Nepoužívejte malé přesuny (pohyb v malých objemech). Preferovat zmizení a změny nad přesunutím objektů.

- Nepoužívejte animace, které probíhají přes velkou oblast obrazovky. Bez ohledu na velikost je tento styl animace uživateli odvolán.

- Nepoužívejte animace nesouvisející s objektem, na který se uživatel aktuálně zaměřuje nebo který s ním pracuje.

- Nepoužívejte animace, které vyžadují interakci s uživatelem, a obnovte stav, jako je vynucení reakce uživatele na blikání oznámení, aby bylo možné zastavit jeho bliknutí. Interakce s nimi by měla být dostačující k jejich zavření.

Další informace o aplikacích pro tyto osvědčené postupy najdete v tématu [vzory animace](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Metriky animace

- Systém by měl viditelně reagovat na gesta uživatele během méně než 10 milisekund.

- Dokončení animovaných přechodů by nemělo trvat déle než 500 milisekund.

- Jedním ze způsobů, jak kompenzovat přechody, které vyžadují delší dobu, je oddělení IT do dvou částí. První část animace může být například prázdný kontejner obsahu (až 500 milisekund) následovaný obsahem do kontejneru (až 500 milisekund).

- Pro dobu načítání, která může být vypočítána, je upřednostňován indikátor průběhu determinantu (ukazatel průběhu v procentech).

- Pro dobu načítání, která se nedá vypočítat, je vhodné indikátor zaneprázdněnosti, jako je kurzor nebo vložená animace (načítání nebo pracovní indikátor), být vhodný.

### <a name="animation-as-communicator"></a>Animace jako Communicator
V uživatelském rozhraní sady Visual Studio funguje animace pouze jako komunikační nástroj.  Slouží ke sdělování různých informací, jako jsou strukturální změny v uživatelském rozhraní (například při otevření nebo zavření nabídky). Animace může přispět k vizualizaci chování složitých systémů závislých na čase, jako je vizualizace průběhu instalace. Animace můžete použít také k upoutání pozornosti s výstrahami a oznámeními.

 Animace uživatelského rozhraní obvykle fungují čtyřmi způsoby: vizualizace, přilákat pozornost, simulovat a doby odezvy nebo indikátory průběhu.

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

- Reprezentace změn v průběhu času pomocí posuvníků času, běhu kol a přenosových mechanismů (přehrávání, zastavení a pozastavení)

##### <a name="relationships"></a>Relace

- Ilustruje, jak se položky vztahují na jednu jinou nebo které položky se vztahují k dané položce.

- Zobrazit hierarchie a vztahy nadřazenosti a podřízenosti nebo na stejné úrovni

- Jeden element vytvářený další

- Jeden prvek se minimalizuje na jiný element.

- Jeden prvek, který je připojený k jinému

##### <a name="state"></a>Stav

- Aktualizace obsahu

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
Pokud je cílem nakreslit pozornost uživatele na jeden prvek z několika nebo upozornit uživatele na aktualizované informace, může být vhodná animace. Například úvodní stránka aplikace může použít tlačítko Začínáme, které se snímky na místo načte po načtení stránky.

Jako pravidlo se poslední přesunutí elementu na obrazovce připraví pozornost uživatele.  V řadě animovaných prvků bude pozornost uživatele následovat za posledním přesunutým objektem.

##### <a name="alert"></a>Výstrahy

- Upozornit uživatele, získat pozornost, zobrazit průběh

- Ukáže, že se něco dělá správně nebo není správně nebo se zobrazuje průběh nebo průběh.

- Vyzvat uživatele během úkolu, třeba najít další informace online nebo získat informace o aktuálním úkolu

##### <a name="notifications"></a>Oznámení

- Upozorní uživatele na chybovou podmínku.

- Přerušit uživatele, aby viděli, jestli se chce zúčastnit nějakého jiného

- Jemně Informujte uživatele, že se proces dokončil nebo změnil, například po dokončení stahování.

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
Animace v aplikaci Visual Studio mají sloužit k poskytování konkrétní funkce bez překážky produktivity uživatelů. Obvykle by animace v aplikaci Visual Studio měly být:

- Malý a nenápad

- Přirozené a realistické

- Jemný a subdued

- Rychlé a efektivní

- Uvolněno, není hurried

Tento obrázek znázorňuje styly animace, které doporučujeme pro Visual Studio. Nejčastěji používané nejsou žádné animace ani jemné animace, jako je zmizení nebo zeslabení. Existují omezené aplikace pohybu, jako je například rozbalení a kontrakt, změna pozice X a Y a rotace.

![Doporučené styly animace pro Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202 – a_VSAnimStyles")<br />Doporučené styly animace pro Visual Studio

#### <a name="appear-and-disappear"></a>Zobrazí se a zmizí
V tomto modelu se element přepne z viditelnosti na mimo zobrazení a zpátky bez animace přechodu.

![Zobrazení a zmizení animace](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202 – b_AppearAndDisappear")<br />Zobrazení a zmizení animace

##### <a name="correct-usage"></a>Správné použití
Nové prvky uživatelského rozhraní, které se musí okamžitě zobrazit nebo zmizet, aby uživatel nebyl ani nerušivý ani nepřesný. Kromě toho se může pomalým přesunutím animací objevit jako ukazatel výkonu, který se neobjeví se stylem zobrazení a zmizení.

##### <a name="incorrect-usage"></a>Nesprávné použití
Případy, kdy se uživatelské rozhraní objeví tak náhlé, že uživatel nenápadí, co se stalo, a Přidání animace by vám pomohly kontextové porozumění.

##### <a name="animation-properties"></a>Vlastnosti animace
Časová prodleva je všeobecně nula sekund.

##### <a name="examples"></a>Příklady
- Automaticky skrývat okna nástrojů

- Editor aktivovaných klávesnicí – uživatelské rozhraní, například IntelliSense a parametr help

- Rozbalení oblastí kódu a jejich sbalení

#### <a name="fade-in-and-fade-out"></a>Zmizení a rozmizet
V tomto modelu se prvky uživatelského rozhraní přechází z neviditelného (0% opacity) na viditelné (100% opacity) nebo naopak.

![Animace zmizení a zmizení](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202 – c_FadeInFadeOut")<br />Animace zmizení a zmizení

##### <a name="correct-usage"></a>Správné použití
Toto je nejčastěji doporučená animace uživatelského rozhraní. Je to jemný efekt, který přináší úroky bez přerušení toku. V některých případech se uživatel nemusí ani si uvědomit, že se jedná o animaci a vnímaný systém uživatelského rozhraní s hladkým a tokem.

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
V tomto modelu se prvek uživatelského rozhraní změní z barvy A na Color B.

![Animace míchání barev](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202 – d_ColorBlend")<br />Animace míchání barev

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
V tomto modelu se prvky uživatelského rozhraní rozšiřují v obou směrech X, Y nebo obou.

![Rozbalit a sbalit animaci](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202 – e_ExpandContract")<br />Rozbalit a sbalit animaci

##### <a name="correct-usage"></a>Správné použití
Jako animovaný přechod, pokud prvek uživatelského rozhraní změní velikost z jednoho kontextu do jiného.

##### <a name="animation-properties"></a>Vlastnosti animace

- Měřítko X:% nebo konkrétní dimenze (v pixelech)

- Měřítko Y:% nebo konkrétní dimenze (v pixelech)

- Pozice kotvy: všeobecně vlevo nahoře (pro jazyky zleva doprava) nebo vpravo nahoře (pro jazyky se zápisem zprava doleva)

- Doba trvání: 200 milisekund samostatné, 100 milisekund při použití jako součást kombinace animační sekvence

##### <a name="examples"></a>Příklady

- Rozbalení a sbalení panelu Průzkumníka architektury

- Visual Studio 2017 začátek položky stránky pro rozbalení a sbalení

#### <a name="x-y-position-change"></a>Změna pozice X-Y
V tomto vzoru prvek uživatelského rozhraní změní svou polohu X nebo Y nebo obojí.

![Animace změny pozice X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202 – f_XYPositionChange")<br />Animace změny pozice X-Y

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
V tomto modelu se prvek uživatelského rozhraní otočí.

![Animace otočení elementu uživatelského rozhraní](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202 – g_Rotate")<br />Animace otočení elementu uživatelského rozhraní

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
![Otevřená animace karty](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202 – h_TabOpen")<br />Otevřená animace karty

- Style: zobrazí se

- Doba trvání: nula sekund

#### <a name="tab-close"></a>Zavřít kartu
![Animace zavření tabulátoru](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202 – i_TabClose")<br />Animace zavření tabulátoru

- Styl: Změna pozice X

- Doba trvání: 200 milisekund

#### <a name="tab-reorder"></a>Změna pořadí karet
![Změna pořadí animací v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202 – j_TabReorder")<br />Animace Změna pořadí karet

- Styl: Změna pozice X

- Doba trvání: 200 milisekund

#### <a name="close-floating-document"></a>Zavřít plovoucí dokument
![Zavřít plovoucí animaci dokumentu](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202 – k_CloseFloatingDocument")<br />Zavřít plovoucí animaci dokumentu

- Style: zobrazí se

- Doba trvání: 200 milisekund

#### <a name="window-state-transition"></a>Přechod stavu okna
![Animace přechodu na stav okna](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202 – l_WindowStateTransition")<br />Animace přechodu na stav okna

- Styl: Chcete-li být konzistentní s jinými okny, nechte aktuální operační systém definovat animaci zavřít dokument.

- Doba trvání: 200 milisekund

#### <a name="menu-open"></a>Nabídka otevřená
![Nabídka otevřít animaci](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202 – m_MenuOpen")<br />Nabídka otevřít animaci

- Style: zeslabit

- Doba trvání: 200 milisekund

#### <a name="menu-close"></a>Zavřít nabídku
![Animace zavření nabídky](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202 – n_MenuClose")<br />Animace zavření nabídky

- Styl: rozmizet

- Doba trvání: 200 milisekund

#### <a name="auto-hide-tool-window-reveal"></a>Automaticky skrývat zobrazení oken nástrojů
![Automaticky skrývat okno nástrojů zobrazit animaci](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202 – o_AutoHideToolWindowReveal")<br />Automaticky skrývat okno nástrojů zobrazit animaci

- Style: zobrazí se

- Doba trvání: nula sekund
