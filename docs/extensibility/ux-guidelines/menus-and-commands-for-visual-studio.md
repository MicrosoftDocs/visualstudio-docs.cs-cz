---
title: Nabídky a příkazy pro Visual Studio | Microsoft Docs
description: Přečtěte si, jak panely příkazů umožňují flexibilitu uživatelského rozhraní při vytváření nových funkcí pro Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef66123e1a4d62f89fc1c69b81bcb780d0b294f0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902095"
---
# <a name="menus-and-commands-for-visual-studio"></a>Nabídky a příkazy pro Visual Studio
## <a name="command-usage"></a>Použití příkazů

### <a name="overview"></a>Přehled
 Na systém Microsoft Office, což je sada, která se skládá z mnoha samostatných produktů, obsahuje Visual Studio mnoho produktů, z nichž každý přispívá svými sadami příkazů do globálního Visual Studio IDE. Integrované vývojové prostředí (IDE) spravuje složitost tisíců příkazů filtrováním funkcí dostupných pro uživatele na základě kontextu.

 Když se kontext uživatele změní – například přepnutí z okna návrhu na okno pro úpravy kódu – funkce, které nesouvisejí s novým kontextem, zmizí. Zároveň se zobrazí nové funkce společně se souvisejícími dynamickými informacemi, jako jsou vlastnosti a možnosti panelu nástrojů. Uživatel by si neměl všimnout prohození dostupné sady příkazů. Pokud je uživatel rušivých nebo zaměněn zobrazením nebo zmizením příkazů, je potřeba návrh uživatelského rozhraní upravit. Aktuální kontext uživatele je vždy označen jedním nebo více způsoby, například v záhlaví integrovaného vývojového prostředí (IDE), okno Vlastnosti nebo v dialogovém okně Stránky vlastností.

 Panely příkazů umožňují flexibilitu v uživatelském rozhraní. Jediné struktury příkazů, které jsou Visual Studio prostředí, jsou hlavní nabídka a hlavní panel příkazů, které lze přizpůsobit i dokonce skrýt. Další panely příkazů se zobrazí a zmizí v závislosti na stavu aplikace. Okna nástrojů a editory dokumentů mohou také obsahovat vložené panely nástrojů v rámci jejich okrajů.

#### <a name="basic-guidelines"></a>Základní pokyny

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Pokud je to možné, používejte existující sdílené příkazy, skupiny příkazů a nabídky.
 Vzhledem k tomu, že se příkazy obvykle zobrazují na základě kontextu, použití existujících sdílených nabídek a skupin příkazů zajišťuje, že struktura příkazů zůstává mezi změnami v kontextu relativně stabilní. Opětovné použití sdílených příkazů a umístění nových příkazů blízko souvisejících sdílených příkazů také snižuje složitost integrovaného vývojového prostředí (IDE) a vytváří uživatelsky přívětivější prostředí. Pokud je potřeba definovat nový příkaz, zkuste ho umístit do existující sdílené skupiny příkazů. Pokud je potřeba definovat novou skupinu, před vytvořením nové nabídky nejvyšší úrovně ji umístěte do existující sdílené nabídky blízko související skupiny příkazů.

##### <a name="do-not-create-icons-for-every-command"></a>Nevytvářejte ikony pro každý příkaz.
 Než vytvoříte ikonu příkazu, pečlivě si to rozmyslete. Ikony by se měly vytvářet jenom pro příkazy, které:

- se zobrazí na výchozím panelu nástrojů.

- budou uživatelé pravděpodobně přidáni na panel nástrojů prostřednictvím **dialogového okna** Přizpůsobit.

- Mít ikonu přidruženou ke stejné akci v jiném produktu Microsoftu.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Omezení přidávání klávesových zkratek
 Velká většina uživatelů využívá malý zlomek všech dostupných zástupců. Pokud nemáte pochybnosti, nevážete funkci na klávesovou zkratku. Než přidáte nové klávesové zkratky, pracujte s týmem uživatelského prostředí.

##### <a name="give-commands-a-default-menu-placement"></a>Dejte příkazům výchozí umístění nabídky.
 Je třeba mít na paměti, že vaše příkazy budou přizpůsobeny ostatními uživateli a navrhovat je odpovídajícím způsobem. Nic takového jako skrytý příkaz neexistuje. Všechny Visual Studio se zobrazí v dialogovém okně Nástroje **>** Přizpůsobit, v příkazovém okně, v automatickém dokončení, v dialogovém okně Nástroje > Možnosti > Klávesnice **a** v prostředí Vývojových nástrojů (DTE). Nezapomeňte dejte příkazům název a popis v souboru .ctc, aby je uživatelé snadno našli.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Na vloženém panelu nástrojů neduplikujte sdílené příkazy.
 Příkazy je vhodné umístit v těsné blízkosti oblasti, na které se uživatel zaměřuje. Jedním ze způsobů, jak to provést, je vytvořit vložený panel nástrojů v horní části okna nástroje nebo editoru dokumentů. Příkazy umístěné na panelu nástrojů by měly být specifické pro oblast obsahu v rámci okna. Na těchto panelech nástrojů neduplikujte sdílené příkazy. Na vložený panel nástrojů například nikdy neumiste ikonu Uložit.

### <a name="content-and-command-visibility"></a>Obsah a viditelnost příkazů
 Příkazy existují v následujících oborech: **Environment (Prostředí),** **Hierarchy**(Hierarchie) **a Document (Dokument).** Znát každý obor, aby měl jistotu při umísťování příkazů.

 Příkazy v oboru **prostředí vytvoří** primární kontext a jsou sdíleny mezi více kontexty. Mění viditelnost nebo uspořádání dokumentů a oken nástrojů. Mezi příkazy v oboru prostředí patří New **Project**(Nový projekt), **Connect to Server**(Připojit k serveru), Attach **Process**(Připojit proces), **Cut**(Vyjmout), **Copy**(Kopírovat), **Paste**(Vložit), Find (Najít), **Options**(Možnosti), **Customize**(Přizpůsobit), **New Window**(Nové okno) a **View Help (Zobrazit nápovědu).** 

 Příkazy v oboru **Hierarchie** spravují hierarchie v Visual Studio, **včetně projektů,** **týmů** a **dat**. Souvisí s dílčím kontextem projektu– například **Ladění,** **Sestavení,** **Testování,** **Architektura** nebo **Analýza**. Mezi příkazy v oboru hierarchie patří Přidání nové **položky,** Nový **dotaz,** **Nastavení projektu,** Přidání nového zdroje **dat,** Průvodce spuštěním **výkonu** a **Nový diagram.**

 Příkazy v **oboru dokumentu** pracují s obsahem dokumentu, jako je kód, návrh nebo dotaz na pracovní položku (WIQ). Slouží také k zobrazení okna nástroje nebo jsou pro toto okno nástroje jinak specifické. Příkazy oboru dokumentu také působí na objekty souborů, které jsou samy specifické pro hierarchii, například **Odebrat z projektu**. Mezi příkazy v oboru dokumentu patří **refaktoring >,** vytvoření **kopie** pracovní **položky,** rozbalení všech, **sbalení** všech a **vytvoření uživatelské úlohy**.

### <a name="command-placement-decisions"></a>Rozhodnutí o umístění příkazů
 Jakmile se rozhodli vytvořit příkaz, budete muset určit jeho vhodné umístění a to, jestli chcete vytvořit klávesovou zkratku. Postupujte podle této rozhodovací cesty a vytvořte, kam příkaz umístit:

 ![Rozhodovací graf umístění příkazů](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Rozhodovací cesta pro umístění příkazu v Visual Studio**

### <a name="command-placement-in-menus"></a>Umístění příkazů v nabídkách

#### <a name="main-menu-bar"></a>Hlavní řádek nabídek
 Hlavní řádek nabídek by měl být standardním umístěním pro příkazy všech balíčků místní nabídky, které přispívají do uživatelského rozhraní. Hlavní řádek nabídek se od ostatních struktur příkazů liší tím, že ho prostředí používá k řízení, které příkazy jsou viditelné. Všechny ostatní panely příkazů jednoduše zaknuly příkazy, které nejsou kontextové, ať už jsou umístěné v nabídce nebo na panelu nástrojů.

 Prostředí definuje sadu příkazů integrovaných do hlavního řádku nabídek, které jsou společné v celém integrovaném vývojovém prostředí (IDE) a několika doménách úloh. Tyto příkazy jsou vždy viditelné bez ohledu na to, které balíčky VSPackage jsou načteny do prostředí. I když balíčky VSPackage rozšiřují tuto sadu příkazů, příkaz nastavený z každého produktu a umístění jejich příkazů je zodpovědností každého týmu.

 Strukturu hlavní nabídky Visual Studio rozdělit do následujících kategorií nabídek:

##### <a name="core-menus"></a>Základní nabídky

- Soubor

- Upravit

- Zobrazit

- nástroje

- Okno

- Help

##### <a name="project-specific-menus"></a>Nabídky specifické pro projekt

- Project

- Sestavení

- Ladění

##### <a name="context-specific-menus"></a>Místní nabídky

- Tým

- Data

- Test

- Architektura

- Analyzovat

##### <a name="document-specific-menus"></a>Nabídky specifické pro dokument

- Formát

- Tabulka

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Při navrhování hlavních nabídek dodržujte tato pravidla:

- Nepřekračujte 25 položek nejvyšší úrovně v daném kontextu.

- Nabídky by nikdy neměly být větší než 600 pixelů.

- Vyhodnoťte hlavní nabídku ve více kontextech, například v ultimate SKU a obecném profilu.

- Kontextové nabídky jsou přijatelné.

- Kontextové nabídky by měly obsahovat alespoň tři položky a nesmí být delší než sedm.

- Kontextové nabídky by měly jít jen o jednu úroveň hluboko – některé Visual Studio kaskádové podnabídky mají kaskádové podnabídky, ale tento model se doporučuje.

- Nepoužívejte více než šest oddělovačů. Seskupení by měla splňovat následující obrázek:

     ![Pokyny pro seskupování hlavní nabídky](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- I když není nutné mít každé seskupení na obrázku, přidání dalších seskupení je omezeno.

- Každé seskupení by mělo mít dvě až sedm položek nabídky.

#### <a name="main-menu-ordering"></a>Pořadí hlavní nabídky
 Před přidáním nové položky nejvyšší úrovně zvažte umístění příkazu do existující nabídky na nejvyšší úrovni. Když přidáváte novou nabídku nejvyšší úrovně, nezapomeňte ji umístit do správného umístění. Rozhodněte, zda je nabídka specifická pro projekt, kontext nebo dokument. Ponechte název nabídky nejvyšší úrovně stručně a použijte pouze jedno slovo.

 Základní nabídky by měly zarážkuovat zbývající příkazy. Soubory, úpravy a zobrazení by měly být vždy vlevo a nástroje, okna a pomocníka by měly být vždy napravo.

#### <a name="context-menus"></a>Místní nabídky
 Umístění příliš velkého množství funkcí v místních nabídkách má za následek obtížné rozhraní. Všechny hlavní funkce by měly být k dispozici prostřednictvím hlavního panelu nabídek. Umístění příkazů by se mělo sjednotit se stávajícími příkazy, aby nedocházelo k duplicitním příkazům. V místních nabídkách prostředí definuje standardní skupiny nabídek, které by měly být zahrnuty v závislosti na tom, zda je kontextová nabídka určena pro řešení, uzel projektu nebo položku projektu.

 Při návrhu místních nabídek je třeba dodržovat stejná pravidla jako pro hlavní nabídku a navíc:

- Nepřekračuje 25 položek nabídky nejvyšší úrovně.

- Místní nabídky jsou přijatelné, ale nesmí přesáhnout jednu úroveň bez použití kaskádových flyouts.

- Nepoužívejte více než šest oddělovačů.

### <a name="command-placement-in-toolbars"></a>Umístění příkazu na panely nástrojů

#### <a name="general-toolbars"></a>Obecné panely nástrojů
 Při navrhování a uspořádávání panelů nástrojů postupujte podle těchto standardů:

- Nepoužívejte více než jednu operaci na tlačítko. Jedno tlačítko = jedna akce.

- Text spolu s ikonou používejte jenom v případě, že je potřeba ho posílit pomocí popisku.

- Pole se seznamem použijte výhradně pro vlastnosti, které se v jedné relaci několikrát přepnou. Jinak vystavte vlastnost jinde.

- Šířka pole se seznamem by měla být shodná s šířkou nejdelší položky v poli + 30%. Například pokud má nejdelší položka 200 pixelů, pole se seznamem by mělo být 260 pixelů na šířku.

- Omezte použití oddělovačů. Použití oddělovače vedle rozevíracího seznamu je anti-Pattern, protože tvar rozevíracího seznamu funguje jako vizuální oddělovač.

- Skupiny ikon by měly obsahovat tři až šest ikon.

- Pokud kvalifikátory způsobí více užitečných příkazů, použijte tlačítko rozdělení, které ukládá poslední nastavení:

     ![Rozdělit tlačítka v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Příklad tlačítka rozdělení Šest příkazů na levé straně se dá přizpůsobit jednomu tlačítku.**

#### <a name="product-specific-toolbars"></a>Panely nástrojů pro konkrétní produkt
 Každý produkt může poskytnout výchozí panel nástrojů, který obsahuje často používané a důležité příkazy, a výchozí panel nástrojů každého produktu by se měl zobrazit při prvním spuštění sady Visual Studio po instalaci produktu.

 Produkty by měly také využívat sdílené příkazové skupiny a nabídky poskytované rozhraním IDE. Každá sdílená skupina příkazů je umístěná ve sdílené nabídce určené k uspořádání souvisejících příkazů smysluplným způsobem pro uživatele. Je důležité využít tuto strukturu sdíleného příkazu, aby se snížila složitost.

#### <a name="global-toolbars"></a>Globální panely nástrojů
 Globální panely nástrojů se musí vejít na jeden řádek přímo v poli. Při vytváření nového globálního panelu nástrojů postupujte podle pokynů pro daný typ panelu nástrojů.

 **Obecné pokyny k panelu nástrojů:**

- Každý panel nástrojů má 24 pixelů v běžných ovládacích prvcích (úchyty, přetečení).

- Každé tlačítko panelu nástrojů má šířku 22 pixelů včetně odsazení. Ikona, která má tlačítko rozdělení, přidá další 11 pixelů šířky.

- Duplikování příkazů napříč panely nástrojů je povoleno.

  **Panely nástrojů specifické pro dokument** se zobrazí, když je určitý typ souboru aktivní a zmizí, když se jiný typ souboru aktivuje jako aktivní.

- Panely nástrojů specifické pro dokument nemohou mít více než 12 tlačítek.

- Celková šířka panelu nástrojů nesmí překročit 300 pixelů.

- Každý typ souboru může mít buď jeden vložený panel nástrojů, nebo jeden globální panel nástrojů specifický pro dokument, ale ne obojí.

  **Konkrétní kontextové panely nástrojů** se zobrazí, když je nastaven určitý kontext a v případě rozšířených období má zůstat aktivní.

- Omezení počtu tlačítek pro všechny panely nástrojů konkrétního kontextu je 18.

- Pokud většina uživatelů nebude konzistentně používat příkazy tohoto panelu nástrojů, když je kontext aktivní, pak tento panel nástrojů nepřidružte k kontextu.

- Ujistěte se, že panel nástrojů zmizí při ukončování kontextu. Při spuštění by se neměl zobrazovat žádný z těchto panelů nástrojů.

  **Panely nástrojů bez kontextu** se nikdy neobjevují automaticky. Zobrazují se pouze v případě, že je uživatel aktivuje. Maximální šířka ponechte 200 pixelů.

### <a name="general-organization-and-shell-defined-groups"></a>Obecné organizace a skupiny definované v prostředí
 Použijte existující sdílené příkazy, skupiny příkazů a nabídky. Pokud je potřeba definovat nový příkaz, zkuste ho umístit do existující skupiny sdílených příkazů. Pokud je potřeba definovat novou skupinu, zkuste ji umístit do existující sdílené nabídky blízko k související skupině příkazů před vytvořením nové nabídky na nejvyšší úrovni. Tím se snižuje složitost příkazů a přitom je zajištěno konzistentní umístění příkazů v integrovaném vývojovém prostředí.

 Nabídka sdíleného **formátu** , která se obvykle zobrazuje v kontextu oken dokumentu ve stylu návrháře, je znázorněna na následujícím obrázku:

 ![Nabídka Formát sady Visual Studio s popisky](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Skupiny nabídek v aplikaci Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Zmenšení a znovu použití příkazů
 Příkazy jsou obvykle zobrazeny v závislosti na kontextu, aby bylo možné snížit počet příkazů, které uživatel v daném okamžiku uvidí. Měli byste ale také znovu použít stávající sdílené nabídky a skupiny příkazů, abyste zajistili, že struktura příkazů zůstane relativně stabilní mezi změnami v kontextu.

 Opětovné použití sdílených příkazů a umístění nových příkazů blízko souvisejícím sdíleným příkazům snižuje složitost IDE a vytváří uživatelsky přívětivé prostředí.

## <a name="naming-commands"></a>Pojmenovávání příkazů

### <a name="naming-conventions"></a>Zásady vytváření názvů
 Konzistentní pojmenování příkazů je kritické, takže uživatelé můžou najít a spustit příkazy, a to buď pomocí příkazového řádku, nebo vazby na klávesovou zkratku. Názvy příkazů také pomůžou uživateli pochopit, k čemu příkaz slouží, když se zobrazí na panelu nástrojů nebo v místní nabídce.

#### <a name="when-naming-commands"></a>Při pojmenování příkazů:

- Sestavte text tak, aby byl snadno lokalizovatelný. Další informace o lokalizaci textu najdete v tématu věnovaném [osvědčeným postupům pro lokalizaci](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

- Je stručné. Příkazy by neměly používat více než tři slova.

- Použít velká a malá písmena: první písmeno každého slova by mělo být velkými písmeny. Další informace o formátování textu v aplikaci Visual Studio naleznete v tématu [style text](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Vezměte v úvahu, kde bude příkaz umístěn. Je to v nabídce nejvyšší úrovně nebo v informačním rámečku? Například při seskupování příkazů v informačním rámečku, by měl být příkaz nejvyšší úrovně "align" a příkazy pro informační rámeček by měly být "Left", "Right", "Center", "Zarovnat do bloku" atd. Pro pojmenování příkazů v informačním rámečku "Zarovnat doleva" nebo "Zarovnat vpravo" by bylo nadbytečné.

     ![Nabídka Formát sady Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Použití ikon s příkazy
 Používejte v příkazech párování ikon s příkazy, které jsou omezené. I když přidružíte k jedinečné imagi příkaz Hastens, aby uživatel identifikoval tento příkaz, nedocházelo k tomu, že dojde k nadměrnému využití obrázků a k neefektivitě. Následující pravidla vám pomůžou při rozhodování, zda má být vytvořena ikona příkazu.

#### <a name="use-an-icon-with-a-command-only-if"></a>Použijte ikonu s příkazem pouze v případě, že:

- Ke stejnému příkazu je přidružená ikona v jiném produktu společnosti Microsoft, jako je například jedna z systém Microsoft Office aplikací.

- Příkaz se umístí na výchozí panel nástrojů.

- Příkaz je speciální příkaz, který mohou uživatelé přidat do panelu nástrojů pomocí dialogového okna **přizpůsobit...** .

## <a name="access-and-shortcut-keys"></a>Přístup a klávesové zkratky

### <a name="overview"></a>Přehled
 K dispozici jsou dva druhy přiřazení kláves klávesnice:

- **Přístupové klíče** (označované také jako akcelerátory) umožňují přístup k klávesnici prostřednictvím nabídek pro příkazy a pro každý popisek v uživatelském rozhraní dialogového okna. Přístupové klíče jsou většinou pro účely usnadnění, jsou přiřazeny ke všem nabídkám a většině ovládacích prvků dialogového okna, nejsou určeny k zapamatovaných, ovlivnění pouze aktuálního okna a jsou lokalizovány.

- **Klávesové zkratky** většinou používají sekvence kláves Ctrl (Ctrl) a Funkce (Fn). Jsou navržené více pro pokročilé uživatele a zvyšují produktivitu. Přiřazují se jenom k nejčastěji používaným příkazům a umožňují rychlý přístup při obejití hlavní nabídky. Klávesové zkratky se mají zapamatovat a z tohoto důvodu musí být přiřazeny v souladu se schématem profilu. Schémata klávesových zkratek se mohou v jednotlivých profilech lišit. Uživatel může klávesové zkratky přizpůsobit pomocí nástrojů **> Options > Keyboard**.

### <a name="assigning-access-keys"></a>Přiřazení přístupových klíčů
 Přístupové klíče se skládají z alt a alfanumerických klíčů. Přiřaďte přístupový klíč ke každé položce nabídky bez výjimky. Při přiřazování přístupových klíčů dodržujte windows a běžné konvence. Například přístupový klíč pro File **(Soubor) > New (Nový) by** měl být **vždy Alt, F, N**.

 Nepoužívejte písmena s jednou šířkou pixelů, například "i" (velkými nebo malými písmeny) nebo malými písmeny "l", a nepoužívejte znaky se znaky (g, j, p, q a y), protože se obtížně rozlišují.

 Pokud je to možné, nepoužívejte duplicitní klíče. V případech, kdy je duplikace nevyhnutelná, zpracovává systém nabídek konflikty tím, že projde všemi příkazy, které klíč používají. Například pro hypotetický příkaz "Number" v nabídce Soubor, který duplikuje přístupovou klávesu "N", **by Alt, F, N** vytvořil nový soubor a **Alt, F, N, N** by příkaz "Number".

### <a name="assigning-shortcut-keys"></a>Přiřazení klávesových zkratek
 Vyhněte se přiřazování nových klávesových zkratek, protože nejsou vyžadovány pro každý příkaz a zdaní systém (a paměť uživatele), pokud jsou přeuovány. Data z program Zlepšování softwaru a služeb na základě zkušeností uživatelů (CEIP) značí, Visual Studio uživatelé používají pouze malou podmnožinu integrovaných zástupců.

 Při definování zástupců postupujte podle těchto pravidel:

- **Použijte sekvence kláves Ovládací prvek (Ctrl) a Funkce (Fn).**

- **Zachovat často používané klávesové zkratky** Udržujte nejoblíbenější klávesové zkratky.

- **Usnadňuje psaní klávesových zkratek v editoru.** Vytvořte vazbu snadno na typových zkratek k příkazům, které vývojáři při psaní kódu nejvíce potřebují. Například **Edit.InvokeSmartTag** musí mít rychlou klávesovou zkratku, jako je Ctrl+/, a ne Alt+Shift+F10.

- **Snažte se o trvale zamyšlené klávesové zkratky.**

- **Postupujte podle pokynů pro Windows a určete, které modifikační klíče se mají použít.** Pro příkazy, které mají rozsáhlé efekty, jako jsou příkazy, které platí pro celý dokument, použijte kombinace kláves Ctrl. Pro příkazy, které rozšiřují nebo doplňují akce standardní klávesové zkratky, použijte kombinace kláves Shift. Nepoužívejte kombinace Ctrl+Alt.

- **Odeberte zástupce, které jsou mimo aplikaci.** Pokud máte starší verzi funkce, zvažte odebrání zástupců, které se používají s extrémně málo častým obdobím (méně než 10krát z dat programu CEIP) nebo střední málo časté události (méně než 100krát z dat programu CEIP), pokud přístupový klíč poskytuje rychlý přístup ke stejnému příkazu. Příklad: Alt, H, C otevře nápovědu nebo obsah.

  Neexistuje jednoduchý způsob, jak zkontrolovat dostupnost zástupce. Pokud chcete přidat zástupce, postupujte takto:

1. Zkontrolujte seznam klávesových [zkratek Visual Studio 2013,](http://visualstudioshortcuts.com/2013/) abyste zjistili, jestli existují podobné příkazy pro seskupení vašich příkazů.

2. Přejděte na **Nástroje > možnosti > prostředí > klávesnice** a otestujte zástupce. Zkontrolujte každé schéma mapování klávesnice uvedené v části Použít následující další schéma mapování klávesnice. Zkontrolujte profily Obecné, C#, VB a C++, protože tyto profily sdílejí jedinečné zástupce. Zástupce je dostupný, pokud není na žádném z těchto míst namapovaný.
