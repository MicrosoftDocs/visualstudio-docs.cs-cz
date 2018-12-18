---
title: Animace pro sadu Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f28e4d6f9ae1a0af060723047621b3e205d012c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148935"
---
# <a name="animations-for-visual-studio"></a>Animace pro sadu Visual Studio
## <a name="animation-fundamentals"></a>Základy animace  
  
### <a name="animation-best-practices-in-visual-studio"></a>Osvědčené postupy animace v sadě Visual Studio  
Postupujte podle těchto pravidel zajistit konzistentní a uživatelsky přívětivý animace styly v prostředí Visual Studio IDE.  
  
-   **Být selektivní.** Omezit animací na ty, které obsluhují konkrétní účely.  
  
-   **Načasování a rychlost jsou důležité** zajistit, že přechody působí rychlý a přirozené:  
  
    -   Dokončení animované přechody v rámci jedné půl sekundy (500 v milisekundách).  
  
    -   Animace, které by tomu bylo, často musí být dostatečně rychlé, že se nebudete přerušení pracovního postupu uživatele. Podívejte se na animace ve smyčce a upravit načasování, dokud se domnívá, vpravo. 
  
    -   Animace nesmí být tak rychlé ani jarring, že je obtížné zjistit, ale není tak pomalé, umožňuje jeden netrpělivý pro přechod na Dokončit.  
  
    -   Ke zdůraznění důležitosti pomocí proměnné časování. Například při procházení posloupnost položek v diagramu tříd, urychlí prostřednictvím přechody mezi položkami pak zpomalit a zaměřit se na důležité položky.  
  
-   **Pomocí postupného bez lineární zmírnit** z jednoho stavu do jiného, udělíte dojem Klidná a přirozené pohybu.  
  
-   Pokud je to možné, **použít jemně animace při přechodu myší** udávajících interaktivní prvky pod myší.  
  
-   Pokud byste tedy spoléhat výraznou na animací funkcí, pak **poskytují prostředky pro jejich vypnutím** místně (pro všechny součásti) jako možnost v **nástroje > Možnosti** dialogové okno.  
  
-   **Pouze jeden animace provedeno současně** a předávaným právě jednu část informací. Více než jeden objekt přesunutí nebo při pokusu o několik věcí nesou může být matoucí. 
  
-   **Subtlety je důležité.** Ve většině případů animace nemá na vyžádání uživatele pozornost jeho účel. Malých změn v načasování, sekvencování a chování může významně ovlivnit dojem a můžete provést rozdíl mezi efektivní a neúčinná animace.  
  
-   Při použití animace k upozornění na něco, **Ujistěte se, že je vhodné přerušení uživatele**na train myšlenku.  
  
-   **Při zobrazení stavu nebo průběhu** prostřednictvím animace:  
  
    -   Zastavte znázorňující průběh přesunutí, pokud není posunutí v podkladovém procesu. 
  
    -   Neurčitém procesů odlišení od determinate procesy.  
  
    -   Zajistěte, aby animace osobní stavu dokončení a selhání.  
  
    -   Minimalizujte použití animace vliv, které ukazují stav a ujistěte se, zda mají skutečné hodnoty tím, že poskytuje další informace o skutečném použití. Mezi příklady patří přechodný stav se změní a naléhavých případech  
  
#### <a name="animation-donts"></a>Animace proti:
  
-   Nepoužívejte malé pohybů (pohyb v malé nároky). Dáváte přednost stmívačkami a změn v průběhu přesun objektů.  
  
-   Nepoužívejte animace, které přes velké oblasti obrazovky nemovitosti probíhaly. Bez ohledu na velikost je tento styl animace rušivě uživateli.  
  
-   Nepoužívejte animace, který nesouvisí se objekt, který uživatel aktuálně se zaměřuje na nebo interakci s.  
  
-   Nepoužívejte animace, které vyžadují zásah uživatele Chcete-li obnovit stav, například vynucení uživatele blikající oznámení, aby bylo možné zastavit blikat reagovat. Interakce s nimi žádným způsobem by mělo být dostatečné pro jejich zamítnutí.  
  
Další informace o aplikacích pro tyto doporučené postupy najdete v tématu [animace vzory](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### <a name="animation-metrics"></a>Metriky animace  
  
-   Systém by měl viditelně reagovat na gesta uživatel v menší než 10 milisekund.  
  
-   Animovaný přechody by neměl trvat déle než 500 milisekund pro dokončení.  
  
-   Jedním ze způsobů kompenzovat přechody, které vyžadují delší doby je rozdělit do dvou částí. První část animace může být například prázdný obsahu kontejneru (až 500 v milisekundách), za nímž následuje obsahu směrem do kontejneru (až 500 v milisekundách).  
  
-   Pro dobu zatížení, které lze vypočítat je upřednostňovanou indikátor průběhu určujícím (probíhá v procentech ukazatele).  
  
-   Pro dobu zatížení, které nelze vypočítat je vhodné zaneprázdněn indikátor jako kurzor nebo vložené roztočený animace (načítání nebo pracovní indikátor).  
  
### <a name="animation-as-communicator"></a>Animace jako communicator  
Ve Visual Studiu animace funguje pouze jako nástroj pro komunikaci.  Použije se pro komunikaci celou řadu informací, jako v uživatelském rozhraní (například když nabídky otevře nebo ukončení) ke změnám struktury. Animace může pomoci vizualizovat chování závislá na čase složitých systémů, jako je vizualizace průběhu instalace. Animace lze také přitahují pozornost s výstrahy a oznámení.  
  
 Animace uživatelského rozhraní funkce obvykle čtyři způsoby: vizualizovat, přitahují pozornost, simulaci, a časy odezvy/průběh indikátory.  
  
#### <a name="visualize"></a>Vizualizace  
Animace můžete zdůraznit trojrozměrné povaha objekty a usnadňují uživatelům vizualizovat jejich prostorových struktury. Jak toho docílit, animace může potřebovat k číselníku objekt v úplné kruh, pomalu zapnout a zpět, nebo přenese objekt blíž a mírně zvětšete jeho velikost zdůraznit výměny či fokus.  
  
I když trojrozměrné objekty mohou být přesunout s uživatelský ovládací prvek, návrháře by měl zjistit předem (prostřednictvím kódu programu nebo ručně) jak pro nejlepší použije animaci přesunu, která poskytuje optimální Principy objektu. To naprogramovaný tak animace může potom aktivovat uživatel umístěním kurzoru přes objekt, zatímco uživatelem řízená pohybů vyžadovat, aby uživatel pochopit, jak k manipulaci s objektu. Omezit pohyb na jednom osy nebo orientaci najednou. buď škálování, otáčení, nebo přeložit, ale nedělají nic více než jeden současně.  
  
Kategorie vizualizovat zahrnuje aspekty dat, relace, stav, struktura, pořadí a času.  
  
##### <a name="data"></a>Data  
Ilustruje informace o komplexní a proměnné:  
  
-   Procházení vizualizace informace jako tabulky a grafy  
  
-   Procházení pořadí, průvodce a stránkování  
  
-   Volání na podrobnosti, přechodem a zvýraznění konkrétní informace  
  
-   Překrytí podrobnosti a další informace o nad cílených element
  
-   Přechází z jedné strukturální nebo organizace reprezentace do jiného  
  
-   Představující změny v čase pomocí posuvníků čas, souborů Wheel posuvný a kyvadlové a ovládací prvky přenosu (play, zastavení a pozastavení) 
  
##### <a name="relationships"></a>Relace  
  
-   Ilustraci, jak se k sobě vztahují položky nebo položky, které se týkají daná položka
  
-   Zobrazit vztahy hierarchie a nadřazený podřízený nebo na stejné úrovni
  
-   Jeden element vytvoří jiné
  
-   Jeden element minimalizuje na jiný element
  
-   Jeden element uvazována do jiného
  
##### <a name="state"></a>Stav  
  
-   Aktualizace obsahu
  
-   Fokus uživatele a výběr  
  
-   Průběh  
  
-   Chyby  
  
##### <a name="structure"></a>Struktura  
  
-   Přesun strukturu na jednom uzlu  
  
-   Změna orientace  
  
-   Minimalizovat a maximalizovat, nebo rozbalení a sbalení  
  
##### <a name="sequence"></a>Pořadí  
  
-   Prezentace pořadí  
  
-   Překlopení prostřednictvím obrázky  
  
##### <a name="time"></a>Čas  
  
-   Zobrazení změn v průběhu času, časová prodleva a záznam dění na monitoru  
  
-   Přesun Koš, vrátit zpět a znovu:  
  
-   Obnovení historických stavu  
  
#### <a name="attract-attention"></a>Přitahují pozornost  
Pokud je cílem upozornit uživatele na jeden element mimo několik nebo o upozornění uživatele k aktualizované informace, může být vhodné animace. Úvodní stránku aplikace může například použít tlačítko Začínáme, které snímky do místní po načtení stránky.  
  
Platí poslední přesunutí elementu na obrazovce upoutat pozornost uživatele.  V řadě animovaných elementů bude pozornost uživatele podle poslední přesunutí objektu.  
  
##### <a name="alert"></a>Výstrahy  
  
-   Upozornit uživatele, získat pozornost, ukázat průběh  
  
-   Zobrazit, že něco probíhá správně nebo nesprávně nebo zobrazovat průběh nebo probíhající změny  
  
-   Vyzvat uživatele během úlohy, jako je hledání další informace online nebo získávání informací o aktuální úlohy  
  
##### <a name="notifications"></a>Oznámení  
  
-   Upozornění uživatele o chybový stav  
  
-   Přerušení uživatelům zobrazit, pokud by chtěli jim věnovat pozornost něco jiného  
  
-   Jemně uživatele informuje, že dokončení procesu nebo změnit, jako jsou po dokončení stahování.  
  
#### <a name="simulate"></a>Simulovat  
Tato kategorie zahrnuje physicality a dimenzionalitu.  
  
-   Ilustrují, kde objekty pocházet z nebo kde přejde na  
  
-   Rozbalení a sbalení nebo otevírají a zavírají  
  
-   Posouvání, posouvání a stránku změní  
  
-   Překrývání a pořadí z-ordering  
  
-   Karuselu a accordion  
  
-   Převracení a otáčení uživatelského rozhraní  
  
#### <a name="response-and-progress-indicators"></a>Odpověď a průběh ukazatele  
Indikátory průběhu mít několik významné výhody:  
  
-   Obě indikátory průběhu determinate a neurčitém ujišťovat uživatel, který nebyl došlo k chybě systému a pracuje na problém.  
  
-   Determinate indikátory zadejte uživatele, kterého pokročíte představu o tom, jak daleko podél akce, a také pocit získání blíže dokončit.  
  
##  <a name="BKMK_AnimationPatterns"></a> Vzory animace  
  
### <a name="overview"></a>Přehled  
Animace v sadě Visual Studio jsou určené k obsluze konkrétní funkce bez brání snížení produktivity uživatelů. Obecně platí by měla být animace v sadě Visual Studio:  
  
-   Drobné a  
  
-   Přirozené a realistické  
  
-   Jemně a tlumeném  
  
-   Rychlé a efektivní  
  
-   Volný, není hurried  
  
Tento obrázek ukazuje animace stylů, že doporučujeme, abyste pro sadu Visual Studio. Žádná animace nebo jemně animací jako objevovat se / objevovat nejčastěji používá. Je omezená aplikace přesun animací jako rozbalte a smlouvy, poloha změny a oběh X a Y. 
  
![Doporučená animace styly pro sadu Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202 a_VSAnimStyles")<br />Doporučené animace styly pro sadu Visual Studio
  
#### <a name="appear-and-disappear"></a>Zobrazovat a zmizí  
Pomocí tohoto vzoru přepíná element z viditelné, se na zobrazení a zpět bez přechodu animace.  
  
![Zobrazovat a zmizí animace](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202 b_AppearAndDisappear")<br />Zobrazovat a zmizí animace  
  
##### <a name="correct-usage"></a>Správné použití  
Novou prvky uživatelského rozhraní, který muset okamžitě zobrazí nebo zmizí tak, aby uživatel je odváděna ani nelze blokovat. Přesunutí zpomalit animací, kromě toho může považovat za přetáhněte výkonu, která nebude nastat se stylem se zobrazil a zmizí.  
  
##### <a name="incorrect-usage"></a>Nesprávné použití  
Případy, ve kterých uživatelského rozhraní se zobrazuje proto náhle že uživatel nemá žádné nápad co se stalo a přidání animace by usnadní kontextové pochopení.  
  
##### <a name="animation-properties"></a>Vlastnosti animace  
Doba zpoždění je obecně nula sekund.  
  
##### <a name="examples"></a>Příklady    
-   Automaticky skrýt okna nástrojů  
  
-   Aktivovat klávesnice editor uživatelského rozhraní, jako IntelliSense a pomáhají parametr  
  
-   Rozbalení a sbalení kódu oblasti  
  
#### <a name="fade-in-and-fade-out"></a>Vysouvaly a fade-out  
Pomocí tohoto vzoru prvku uživatelského rozhraní přechází z nejsou viditelné (krytí 0 %) na viditelné (100 % krytí) a naopak.  
  
![Animace vysouvaly a fade-out](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202 c_FadeInFadeOut")<br />Vysouvaly a fade-out animace  
  
##### <a name="correct-usage"></a>Správné použití  
Toto nastavení se doporučuje nejčastěji animace uživatelského rozhraní. Je jemný efekt, který přidává zájmu bez přerušení toku. V některých případech uživatel nemusí i Uvědomte si, zda je animace, vnímání plynulého a předávaných uživatelského rozhraní systému.  
  
##### <a name="animation-properties"></a>Vlastnosti animace  
  
-   Spouštění krytí: % 0 pro vysouvaly, 100 % pro fade-out  
  
-   Koncová krytí: 100 % pro vysouvaly, 0 % pro fade-out  
  
-   Doba trvání: 200 MS samostatně, 100 milisekund, pokud se používá jako součást kombinace animační sekvence.  
  
-   Usnadnění styl: InOut sinus  
  
##### <a name="examples"></a>Příklady  
  
-   Automaticky skrýt okna nástrojů  
  
-   Nabídka otevřít a zavřít  
  
-   Karta přechody popředí a na pozadí  
  
#### <a name="color-blend-from-a-to-b"></a>Barva blend z A do B  
Pomocí tohoto vzoru prvku uživatelského rozhraní změní z barev A na barvu B.  
  
![Barva přizpůsobte animace](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202 d_ColorBlend")<br />Barva blend animace  
  
##### <a name="correct-usage"></a>Správné použití  
Jako animovaný přechodu, když se prvku uživatelského rozhraní změní barvu z kontextu minimálně stavu do jiného.  
  
##### <a name="animation-properties"></a>Vlastnosti animace  
  
-   Počáteční barva: specifické uživatelského rozhraní  
  
-   Koncová barva: specifické uživatelského rozhraní  
  
-   Doba trvání: 200 MS samostatně, 100 milisekund, pokud se používá jako součást kombinace animační sekvence.  
  
-   Usnadnění styl: InOut sinus  
  
##### <a name="examples"></a>Příklady  
  
-   Zdokumentujte přechodů mezi stavy okno (aktivní, poslední aktivní i neaktivní)  
  
-   Nástroj přechodů mezi stavy okno (cílených a nezaostřená)  
  
#### <a name="expand-and-contract"></a>Rozbalte a smlouvy  
Pomocí tohoto vzoru rozšíří prvku uživatelského rozhraní v X, Y nebo v obou směrech.  
  
![Rozbalte a smlouvy animace](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202 e_ExpandContract")<br />Rozbalte a smlouvy animace  
  
##### <a name="correct-usage"></a>Správné použití  
Jako animovaný přechodu, když se prvku uživatelského rozhraní změní velikost z jednoho kontextu na jiný.  
  
##### <a name="animation-properties"></a>Vlastnosti animace  
  
-   X škálování: % nebo konkrétní dimenzi (v pixelech)  
  
-   Škálování Y: % nebo konkrétní dimenzi (v pixelech)  
  
-   Pozice ukotvení: obecně (pro jazyky zleva doprava) levém horním a pravém (pro jazyky zprava doleva)  
  
-   Doba trvání: 200 MS samostatně, 100 milisekund, pokud se používá jako součást kombinace animační sekvence.  
  
##### <a name="examples"></a>Příklady  
  
-   Architektura Explorer panely rozbalení a sbalení  
  
-   Úvodní stránka položky rozbalení a sbalení  
  
#### <a name="x-y-position-change"></a>X-Y pozice změn  
Pomocí tohoto vzoru prvku uživatelského rozhraní změní jeho pozice X nebo Y, nebo obojí.  
  
![Pozice X-Y změnit animace](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202 f_XYPositionChange")<br />X-Y pozice změnu animace  
  
##### <a name="correct-usage"></a>Správné použití  
Jako animovaný přechodu, když se prvku uživatelského rozhraní změní pozici z jednoho kontextu na jiný.  
  
##### <a name="animation-properties"></a>Vlastnosti animace  
  
-   Spouštění X a Y pomyslného: specifické uživatelského rozhraní  
  
-   Koncová X a Y pomyslného: specifické uživatelského rozhraní  
  
-   Cesta pohybu: žádné  
  
-   Doba trvání: 200 MS samostatně, 100 milisekund, pokud se používá jako součást kombinace animační sekvence.  
  
-   Usnadnění styl: InOut sinus  
  
##### <a name="example"></a>Příklad  
Změna pořadí karet  
  
#### <a name="rotate"></a>Otočit  
Pomocí tohoto vzoru otočí element uživatelského rozhraní.  
  
![Animace otočení element uživatelského rozhraní](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202 g_Rotate")<br />Animace otočení element uživatelského rozhraní  
  
##### <a name="correct-usage"></a>Správné použití  
Pouze pro neurčitém roztočený indikátor průběhu.  
  
##### <a name="animation-properties"></a>Vlastnosti animace  
  
-   Úhel otočení: 360  
  
-   Otočení center: střední objektu  
  
-   Doba trvání: průběžné  
  
##### <a name="example"></a>Příklad  
Indikátor průběhu neurčitou (roztočený)  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>Běžné akce prostředí uživatelského rozhraní a doporučené animace  
  
#### <a name="tab-open"></a>Otevřete kartu  
![Kartě otevřete animace](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202 h_TabOpen")<br />Karta otevřete animace  
    
-   Styl: Zobrazit  
  
-   Doba trvání: nula sekund  

#### <a name="tab-close"></a>Zavřete kartu  
![Kartě zavřít animace](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202 i_TabClose")<br />Karta zavřít animace  
  
-   Styl: Změnit pozice X  
  
-   Doba trvání: 200 MS  
  
#### <a name="tab-reorder"></a>Změnit pořadí karet  
![Kartě změnit pořadí animace v sadě Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202 j_TabReorder")<br />Karta změnit pořadí animace

-   Styl: Změnit pozice X  
  
-   Doba trvání: 200 MS  
    
#### <a name="close-floating-document"></a>Zavřít plovoucí dokumentu  
![Plovoucí animace dokument zavřít](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202 k_CloseFloatingDocument")<br />Zavřít plovoucí animace dokumentu  
   
-   Styl: Zobrazit  
  
-   Doba trvání: 200 MS   
 
#### <a name="window-state-transition"></a>Okno přechod stavu  
![Animace přechod stavu okno](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202 l_WindowStateTransition")<br />Animace přechod stavu okna  
    
-   Styl: aby byl konzistentní s jinými, umožňují definovat zavřít animace dokumentu v aktuálním operačním systému.  
  
-   Doba trvání: 200 MS  
  
#### <a name="menu-open"></a>Nabídka Otevřít  
![Otevřete animace nabídky](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202 m_MenuOpen")<br />Otevřete animace nabídky  
    
-   Styl: vysouvaly  
  
-   Doba trvání: 200 MS  
  
#### <a name="menu-close"></a>Zavřete nabídky  
![Zavřít animace nabídky](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202 n_MenuClose")<br />Zavřít animace nabídky  
    
-   Styl: fade-out  
  
-   Doba trvání: 200 MS  
  
#### <a name="auto-hide-tool-window-reveal"></a>Zobrazení okna automatické skrytí nástroj  
![Automaticky skrýt nástroj okno zobrazení animace](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")<br />Automaticky skrýt nástroj okno zobrazení animace  

-   Styl: Zobrazit  
  
-   Doba trvání: nula sekund