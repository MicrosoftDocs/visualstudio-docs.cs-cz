---
title: Nabídky a příkazy pro Visual Studio | Microsoft Docs
description: Přečtěte si, jak panely příkazů umožňují flexibilitu v uživatelském rozhraní při vytváření nových funkcí sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d28242b70c0c9808cc7eb066341cd2973d2372a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971580"
---
# <a name="menus-and-commands-for-visual-studio"></a>Nabídky a příkazy pro Visual Studio
## <a name="command-usage"></a>Použití příkazu

### <a name="overview"></a>Přehled
 Na rozdíl od systém Microsoft Office, což je sada, která zahrnuje mnoho samostatných produktů, sada Visual Studio obsahuje mnoho produktů, které každý přispívá ke svým sadám příkazů globálnímu integrovanému vývojovém prostředí sady Visual Studio. Rozhraní IDE spravuje složitost tisíc příkazů filtrováním funkcí dostupných uživateli na základě kontextu.

 Když se změní kontext uživatele – například přepnutí z okna návrhu na okno pro úpravu kódu – funkce nesouvisející s novým kontextem zmizí. Současně nové funkční plochy společně se souvisejícími dynamickými informacemi, jako jsou vlastnosti a možnosti sady nástrojů. Uživatel by neměl poznamenat záměnu dostupné sady příkazů. Pokud je uživatel odvolán nebo zaměněno pomocí příkazů, které se zobrazují nebo zmizí, pak návrh uživatelského rozhraní vyžaduje úpravu. Aktuální kontext uživatele je vždy označen jedním nebo více způsoby, například v záhlaví IDE, okno Vlastnosti nebo dialogovém okně vlastností stránky.

 Panely příkazů umožňují flexibilitu v uživatelském rozhraní. Jedinou strukturou příkazu, která je součástí prostředí sady Visual Studio, jsou hlavní nabídka a hlavní panel příkazů, které lze přizpůsobit i dokonce skrýt. Další panely příkazů se zobrazí a zmizí na základě stavu aplikace. Okna nástrojů a editory dokumentů mohou také obsahovat vložené panely nástrojů v rámci jejich okrajů oken.

#### <a name="basic-guidelines"></a>Základní pokyny

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Pokud je to možné, používejte existující sdílené příkazy, skupiny příkazů a nabídky.
 Vzhledem k tomu, že jsou příkazy obvykle zobrazeny v závislosti na kontextu, použití stávajících sdílených nabídek a skupin příkazů zajistí, že struktura příkazu zůstane relativně stabilní mezi změnami v kontextu. Opětovné použití sdílených příkazů a umístění nových příkazů blízko k souvisejícím sdíleným příkazům také snižuje složitost IDE a vytváří uživatelsky přívětivé prostředí. Pokud je potřeba definovat nový příkaz, zkuste ho umístit do existující skupiny sdílených příkazů. Pokud je potřeba definovat novou skupinu, umístěte ji do existující sdílené nabídky blízko k související skupině příkazů před vytvořením nové nabídky na nejvyšší úrovni.

##### <a name="do-not-create-icons-for-every-command"></a>Nevytvářejte ikony pro každý příkaz.
 Před vytvořením ikony příkazu si pečlivě promyslete. Ikony by se měly vytvářet jenom pro příkazy, které:

- zobrazí se na výchozím panelu nástrojů.

- budou pravděpodobně přidány uživateli do panelu nástrojů v dialogovém okně **přizpůsobit...** .

- mít ikonu přidruženou ke stejné akci v jiném produktu společnosti Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Omezení přidání klávesových zkratek
 Velká většina uživatelů používá malý zlomek všech dostupných klávesových zkratek. V případě nejistých funkcí nevytvářejte vazby na klávesovou zkratku. Než přidáte nové zástupce, pracujte s týmem uživatelského prostředí.

##### <a name="give-commands-a-default-menu-placement"></a>Zadejte příkazy pro výchozí umístění nabídky.
 Mějte na paměti, že vaše příkazy se přizpůsobují ostatním uživatelům a budou je navrhovat odpovídajícím způsobem. Neexistuje žádná taková věc jako skrytý příkaz. Všechny příkazy sady Visual Studio se zobrazí v dialogovém okně **nástroje > přizpůsobení** , příkazového okna, automatické dokončování, **nástrojích > možnosti >** dialogové okno klávesnice a vývojové nástroje prostředí (DTE). Nezapomeňte zadat název a popis tlačítka v souboru. CTC, aby je uživatelé mohli snadno najít.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Neduplikujte sdílené příkazy na vložený panel nástrojů.
 Je vhodné umístit příkazy do blízkosti oblasti fokusu uživatele. Jedním ze způsobů, jak to provést, je vytvořit vložený panel nástrojů v horní části okna nástrojů nebo editoru dokumentů. Příkazy, které jsou umístěny na panelu nástrojů, by měly být specifické pro oblast obsahu v rámci okna. Na těchto panelech nástrojů Neduplikujte sdílené příkazy. Například nikdy neumísťujete ikonu Uložit v rámci vloženého panelu nástrojů.

### <a name="content-and-command-visibility"></a>Viditelnost obsahu a příkazu
 Příkazy existují v následujících oborech: **prostředí**, **hierarchie** a **dokument**. Každý obor si poznáte, abyste měli jistotu při umísťování příkazů.

 Příkazy v oboru **prostředí** vytvářejí primární kontext a jsou sdíleny mezi více kontexty. Mění viditelnost nebo uspořádání dokumentů a nástrojů v oknech. Mezi příkazy v rozsahu prostředí patří **Nový projekt**, **připojení k serveru**, **připojení procesu**, **vyjmutí**, **kopírování**, **vložení**, **hledání**, **Možnosti**, **přizpůsobení**, **nové okno** a **zobrazení pomocníka**.

 Příkazy v oboru **hierarchie** spravují hierarchie v aplikaci Visual Studio, včetně **projektů**, **týmů** a **dat**. Vztahují se k podkontextu projektu, například **ladit**, **sestavovat**, **testovat**, **architekturu** nebo **analyzovat**. Mezi příkazy v oboru hierarchie patří **Přidat novou položku**, **Nový dotaz**, **nastavení projektu**, **Přidat nový zdroj dat**, **Spustit Průvodce výkonem** a **Nový diagram**.

 Příkazy v oboru **dokumentu** fungují na obsahu dokumentu, jako je například kód, návrh nebo dotaz na pracovní položku (wiq). Také pracují se zobrazením okna nástroje nebo jsou jinak specifické pro toto okno nástroje. Příkazy oboru dokumentu také fungují s objekty souborů, které jsou specifické pro konkrétní hierarchii, jako je například **Odebrat z projektu**. Mezi příkazy v oboru dokumentu se **refaktoruje > přejmenovat**, **vytvořit kopii pracovní položky**, **Rozbalit** vše, **Sbalit vše** a **vytvořit uživatelskou úlohu**.

### <a name="command-placement-decisions"></a>Rozhodnutí o umístění příkazů
 Jakmile se rozhodnete vytvořit příkaz, budete muset určit jeho vhodné umístění a vytvořit klávesovou zkratku. Podle této rozhodovací cesty určete, kam se má příkaz umístit:

 ![Graf rozhodování o umístění příkazu](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501 – a_CommandPlacement")

 **Rozhodovací cesta k umístění příkazu v aplikaci Visual Studio**

### <a name="command-placement-in-menus"></a>Umístění příkazů v nabídkách

#### <a name="main-menu-bar"></a>Hlavní panel nabídek
 Hlavní panel nabídek by měl být standardní umístění pro příkazy všech balíčků nabídek specifických pro konkrétní kontext, které přispívají k uživatelskému rozhraní. Hlavní panel nabídek se liší od ostatních struktur příkazů v tom, že ho prostředí používá k řízení, které příkazy jsou viditelné. Všechny ostatní panely příkazů jednoduše zakazují příkazy, které jsou mimo kontext bez ohledu na to, jestli jsou umístěné v nabídce nebo na panelu nástrojů.

 Prostředí definuje sadu příkazů integrovaných do hlavního řádku nabídek, které jsou společné napříč celým prostředím IDE a více doménami úloh. Tyto příkazy jsou vždy viditelné bez ohledu na to, které sady VSPackage jsou načteny do prostředí. I když VSPackage mohou tuto sadu příkazů zvětšit, sada příkazů z každého produktu a umístění jejich příkazů je zodpovědností každého týmu.

 Strukturu hlavní nabídky sady Visual Studio lze rozdělit do následujících kategorií nabídky:

##### <a name="core-menus"></a>Základní nabídky

- Soubor

- Upravit

- Zobrazit

- nástroje

- Okno

- Nápověda

##### <a name="project-specific-menus"></a>Nabídky specifické pro projekt

- Project

- Sestavení

- Ladění

##### <a name="context-specific-menus"></a>Konkrétní kontextové nabídky

- Tým

- Data

- Test

- Architektura

- Analýza

##### <a name="document-specific-menus"></a>Nabídky specifické pro dokument

- Formát

- Tabulka

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Při navrhování hlavních nabídek dodržovat tato pravidla:

- Nepřekračuje 25 položek nejvyšší úrovně v daném kontextu.

- Nabídky by nikdy neměly překročit 600 pixelů na výšku.

- Vyhodnoťte hlavní nabídku v několika kontextech, jako je například v položce Ultimate SKU a obecného profilu.

- Jsou přijatelné rozevírací nabídky.

- Vyskakovací nabídky by měly obsahovat alespoň tři položky a nesmí být větší než sedm.

- Místní nabídky by měly jít jenom o jednu úroveň hluboko – některé položky nabídky sady Visual Studio mají kaskádové podnabídky, ale tento model se nedoporučuje.

- Nepoužívejte více než šest oddělovačů. Seskupení by mělo splňovat následující ilustrace:

     ![Pokyny pro seskupování hlavních nabídek](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501 – b_MainMenus")

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

     ![Rozdělit tlačítka v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501 – c_SplitButtons")

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

 ![Nabídka Formát sady Visual Studio s popisky](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501 – d_FormatMenu")

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

     ![Nabídka Formát sady Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502 – a_FormatMenu")

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

- **Klávesové zkratky** většinou používají řízení (CTRL) a funkce (FN) Key Sequence. Jsou určené pro pokročilé uživatele a pomáhají při produktivitě. Jsou přiřazeny pouze k nejčastěji používaným příkazům a umožňují rychlý přístup při obejít hlavní nabídku. Klávesové zkratky mají být zapamatovaných a z tohoto důvodu musí být přiřazeny v souladu se schématem profilu. Schémata klávesových zkratek se můžou lišit od profilu k profilování. Uživatel může přizpůsobovat klávesové zkratky prostřednictvím **nástrojů > možností > klávesnice**.

### <a name="assigning-access-keys"></a>Přiřazování přístupových klíčů
 Přístupové klíče se skládají z ALT plus alfanumerických kláves (y). Přiřaďte přístupový klíč k jednotlivým položkám nabídky bez výjimky. Při přiřazování přístupových klíčů použijte Windows a běžné konvence. například přístupová klávesa pro **soubor > New** by měla být vždy **ALT, F, N**.

 Nepoužívejte písmena s jednou šířkou písmen, jako je i (velkými písmeny nebo malými písmeny) nebo malé písmeno l, a vyhněte se použití znaků se spodními body (g, j, p, q a y), protože je obtížné je odlišit.

 Vyhněte se použití duplicitních klíčů, pokud je to možné. V případech, kdy je duplikování duplicit nevyhnutelné, systém nabídek zpracovává konflikty cyklicky pomocí všech příkazů, které používají klíč. Příkladem pro hypotetický příkaz "Number" v nabídce soubor, který duplikuje přístupový klíč "N **", vytvoří** nový soubor a **ALT, f, n, n,** provede příkaz "Number".

### <a name="assigning-shortcut-keys"></a>Přiřazování klávesových zkratek
 Vyhněte se přiřazování nových klávesových zkratek, protože nejsou vyžadovány pro každý příkaz a daň systému (a paměť uživatelů), pokud je tato funkce přepoužívána. Data z program Zlepšování softwaru a služeb na základě zkušeností uživatelů (CEIP) označují, že uživatelé sady Visual Studio používají pouze malou podmnožinu integrovaných zástupců.

 Při definování klávesových zkratek použijte tato pravidla:

- **Použijte řídicí sekvence (CTRL) a Function (FN).**

- **Zachovat často používané zkratky** Udržujte nejoblíbenější zkratky.

- **Snadnější psaní klávesových zkratek editoru** Připojte se k příkazům, které vývojáři potřebují při psaní kódu, snadno typové zkratky. Například **Edit. InvokeSmartTag** musí mít rychlou klávesovou zkratku, jako je CTRL +/a NOT ALT + SHIFT + F10.

- **Snažte se používat konzistentní zkratky motivů.**

- **Podle pokynů pro Windows určete, které modifikační klávesy se mají použít.** Použijte kombinaci kláves CTRL pro příkazy, které mají rozsáhlé efekty, například příkazy, které se vztahují na celý dokument. Použijte kombinaci kláves SHIFT pro příkazy, které rozšíří nebo doplňují akce standardní klávesové zkratky. Nepoužívejte kombinace CTRL + ALT.

- **Odeberte nadbytečné zkratky.** Pokud máte starší verzi funkce, zvažte odebrání klávesových zkratek, které jsou používány s extrémními nemožnostmi (méně než desetkrát z dat programu CEIP), nebo střední nečetnost (méně než 100 časů z dat programu CEIP), pokud přístupová klávesa poskytuje rychlý přístup ke stejnému příkazu. Například: ALT, H, C otevře nápovědu/obsah.

  Není k dispozici jednoduchý způsob, jak kontrolovat dostupnost klávesových zkratek. Chcete-li přidat zástupce, postupujte podle následujících kroků:

1. Podívejte se na seznam [zástupců Visual Studio 2013](http://visualstudioshortcuts.com/2013/) , abyste zjistili, jestli jsou k dispozici podobné příkazy pro seskupení.

2. V **nabídce nástroje > možnosti > prostředí > klávesnice** a otestujte zástupce. Zaškrtněte u každého schématu mapování klávesnice uvedené v části "použít následující další schéma mapování klávesnice". V profilech obecné, C#, VB a C++ se podívejte na tyto jedinečné zkratky pro sdílení. Zástupce je k dispozici, pokud není namapován v žádném z těchto umístění.
