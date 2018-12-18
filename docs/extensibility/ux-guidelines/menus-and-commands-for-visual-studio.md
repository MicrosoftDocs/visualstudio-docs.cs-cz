---
title: Nabídek a příkazů pro sadu Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f5686f96ce0125cac98ca08582e8407c4e1e926
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937951"
---
# <a name="menus-and-commands-for-visual-studio"></a>Nabídek a příkazů pro sadu Visual Studio
## <a name="command-usage"></a>Použití příkazu  
  
### <a name="overview"></a>Přehled  
 Na rozdíl od Microsoft Office, což je sada, která se skládá z mnoha samostatných produktů Visual Studio obsahuje mnoho produktů, každý tam jejich sady příkazů globální Visual Studio IDE. Rozhraní IDE spravuje složitost tisíce příkazy pomocí filtrování funkce, která je dostupná pro uživatele na základě kontextu.  
  
 Při změně kontextu uživatele – například přepínání okno pro úpravu kódu v okně návrhu – funkce nesouvisí se nový kontext zmizí. Ve stejnou dobu, nové funkce povrchy společně se související dynamických informací, jako jsou možnosti vlastnosti a sady nástrojů. Uživatel by neměl Všimněte si, že prohození sady příkazů dostupné. Pokud se uživatel odváděna nebo něco jiného než příkazy povolí, nebo zmizení, návrh uživatelského rozhraní třeba úpravy. Aktuální kontext uživatele je vždy uvedené v jeden nebo více způsoby, například v záhlaví rozhraní IDE, v okně Vlastnosti nebo dialogové okno stránky vlastností.  
  
 Panely příkazů umožňují flexibilitu v uživatelském rozhraní. Jediný příkaz struktury přináší Visual Studio prostředí jsou hlavní nabídky a panelu hlavního příkazu, který je i možné přizpůsobit a dokonce i skryté. Ostatní panely příkazů se zobrazí a zmizí závislosti na stavu aplikace. Okna nástrojů a editory dokumentu může také obsahovat vložený panelů nástrojů v rámci jejich okrajů okna.  
  
#### <a name="basic-guidelines"></a>Základní pokyny  
  
##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Použijte existující sdílené příkazy, pro skupinu příkazů a nabídek, kdykoli je to možné.  
 Protože příkazy jsou obvykle zobrazuje v kontextu, použití existující sdílené nabídky a skupiny příkaz zajišťuje, příkazovou strukturu zůstává relativně stabilními mezi změnami v kontextu. Opětovné použití sdílených příkazů a uvedení nové příkazy blízko související sdílené příkazy také snižuje složitost integrovaného vývojového prostředí a vytvoří lepší uživatelský zážitek. Pokud nový příkaz musí být definován, pokuste se umístit ve stávající skupině sdílené příkazu. Pokud se nová skupina musí být definován, umístěte ho do existující sdílené nabídky blízko skupinu souvisejícím příkazem před vytvořením nového nabídek nejvyšší úrovně.  
  
##### <a name="do-not-create-icons-for-every-command"></a>Nevytvářejte ikony pro každý příkaz.  
 Pečlivě před vytvořením ikona příkazu. Ikony by měl být vytvořen pouze pro příkazy, které:  
  
-   se zobrazí na panelu nástrojů výchozí.  
  
-   mohou uživatelé přidat do panelu nástrojů prostřednictvím **vlastní...**  dialogového okna.  
  
-   máte ikony přidružené k stejnou akci v jiném produktu společnosti Microsoft.  
  
##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limit přidání klávesových zkratek  
 Většinu uživatelů využívají zlomek všech dostupných klávesových zkratek. V případě pochybností si nechcete vytvořit vazbu vaši funkci klávesové zkratky. Práce s vaší uživatelské prostředí tým před přidáním nové klávesové zkratky.  
  
##### <a name="give-commands-a-default-menu-placement"></a>Výchozí umístění nabídky zadejte příkazy.  
 Mějte na paměti, že vaše příkazy ostatní uživatelé se budou přizpůsobovat a navrhování je odpovídajícím způsobem. Není k dispozici i skryté příkazu. Všechny příkazy sady Visual Studio se zobrazí v **nástroje > vlastní** dialogového okna, na příkazovém řádku automatického dokončování, **nástroje > Možnosti > klávesnice** dialogových oken a prostředí nástroje pro vývoj (DTE). Ujistěte se, že k příkazům zadejte název a popis v souboru .ctc tak, aby uživatelé moci snadno najít.  
  
##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Duplicitní není sdílený příkazy na integrovaném panelu nástrojů.  
 Je vhodné umístit příkazy v těsné blízkosti oblasti zaměření uživatele. Jeden způsob, jak to provést, je vytvoření integrovaném panelu nástrojů v horní části okna nástroje nebo dokumentu editoru. Příkazy, které jsou umístěny na panelu nástrojů by měl být specifické pro oblast obsahu okna. Duplicitní není sdílený příkazy na panely nástrojů. Například umístit nikdy ikonu "Save" v integrovaném panelu nástrojů.  
  
### <a name="content-and-command-visibility"></a>Viditelnost příkazů a obsahu  
 Příkazy existovat v následující obory: **prostředí**, **hierarchie**, a **dokumentu**. Pokud chcete mít přitom jistotu při umísťování příkaz vědět každý obor.  
  
 Příkazy v **prostředí** oboru vytvořit primární kontext a sdílejí mezi několika kontextech. Mění viditelnost nebo uspořádání dokumenty a okna nástrojů. Mezi příkazy v prostředí oboru jsou **nový projekt**, **připojit k serveru**, **připojit procesu**, **Vyjmout**,  **Kopírování**, **vložit**, **najít**, **možnosti**, **přizpůsobit**, **nové okno**, a **zobrazit nápovědu**.  
  
 Příkazy v **hierarchie** oboru Správa hierarchií v sadě Visual Studio včetně **projektu**, **týmu**, a **Data**. Jejich vztah k kontext projektu – například **ladění**, **sestavení**, **testovací**, **architektura**, nebo **analyzovat** . Mezi příkazy v hierarchii jsou oboru **přidat novou položku**, **nový dotaz**, **nastavení projektu**, **přidat nový zdroj dat**, **Spustit Průvodce výkonem**, a **nový Diagram**.  
  
 Příkazy v **dokumentu** act obor na obsah dokumentu, jako je kód, návrhu nebo dotazu na pracovní položku (WIQ). Jsou také fungovat pro zobrazení vlastností okna nástroje nebo jinak jsou specifické pro okno nástroje. Dokument oboru také příkazy v souboru objektů, které představují samy o sobě konkrétní hierarchie, například **odebrat z projektu**. Mezi příkazů v dokumentu jsou oboru **Refaktorovat > přejmenujte**, **vytvořit kopii pracovní položku**, **Rozbalit vše**, **Sbalit vše**, a **Vytvořit uživatelský úkol**.  
  
### <a name="command-placement-decisions"></a>Rozhodnutí o umístění příkazu  
 Jakmile jste se rozhodli vytvořit příkaz, musíte určit jeho vhodné umístění a jestli se mají vytvořit klávesové zkratky. Postupujte podle tohoto rozhodnutí stanovit kam umístit příkaz:  
  
 ![Příkaz umístění rozhodovací graf](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501 a_CommandPlacement")  
  
 **Rozhodnutí o cestu pro umístění příkazu v sadě Visual Studio**  
  
### <a name="command-placement-in-menus"></a>Umístění příkazového v nabídkách  
  
#### <a name="main-menu-bar"></a>Hlavní nabídek  
 Hlavním panelu nabídek by měl být standardní umístění pro všechny balíčky kontextové nabídky, které přispívají k uživatelské rozhraní a příkazů. Panel hlavní nabídky se liší od další příkaz struktury, prostředí, použije ho k řízení, které příkazy jsou viditelné. Všechny ostatní panely příkazů jednoduše zakázat příkazy, které jsou mimo kontext, zda jsou umístěny v nabídce nebo na panelu nástrojů.  
  
 Prostředí definuje sadu příkazů integrovaná v hlavním panelu nabídek, které jsou společné napříč celou integrovaného vývojového prostředí a více doménami úloh. Tyto příkazy jsou vždy viditelné bez ohledu na to z nich balíčky VSPackages načtou do prostředí. Ačkoli rozšíření VSPackages můžete rozšířit tuto sadu příkazů, příkaz sady z jednotlivých produktů a umístění jejich příkazy odpovídá každému týmu.  
  
 Struktura v hlavní nabídce sady Visual Studio můžete rozdělit do těchto kategorií nabídky:  
  
##### <a name="core-menus"></a>Základní nabídky  
  
-   Soubor  
  
-   Upravit  
  
-   Zobrazit  
  
-   Nástroje  
  
-   Okno  
  
-   Nápověda  
  
##### <a name="project-specific-menus"></a>Specifické pro projekt nabídky  
  
-   Projekt  
  
-   Sestavení  
  
-   Ladit  
  
##### <a name="context-specific-menus"></a>Kontextové nabídky  
  
-   Tým  
  
-   Data  
  
-   Test  
  
-   Architektura  
  
-   Analyzovat  
  
##### <a name="document-specific-menus"></a>Konkrétní dokumenty nabídky  
  
-   Formát  
  
-   Tabulka  
  
##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Při navrhování hlavní nabídky, dodržujte tato pravidla:  
  
-   Není delší než 25 položky nejvyšší úrovně v daném kontextu  
  
-   Nabídky by nikdy nepřekročí 600 pixelů na výšku.  
  
-   Vyhodnoťte hlavní nabídky v několika kontextech, například Ultimate SKU a profilu Obecné.  
  
-   Kontextová nabídka nabídky jsou přijatelné.  
  
-   Kontextová nabídka nabídky by měl obsahovat alespoň tři položky a více než sedm.  
  
-   Kontextová nabídka nabídky by měly patřit pouze jednu úroveň hlouběji – některé položky nabídky sady Visual Studio obsahují šablony podnabídky, ale tento model není podporováno.  
  
-   Použití více než šest oddělovače. Seskupení by měl splňovat následující obrázek:  
  
     ![Pokyny pro seskupení hlavní nabídky](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501 b_MainMenus")  
  
-   Když to není vyžadováno jednotlivá seskupení na obrázku, přidání dalších seskupení je omezen.  
  
-   Jednotlivá seskupení musí mít ze dvou sedm položek nabídky.  
  
#### <a name="main-menu-ordering"></a>Hlavní nabídka řazení  
 Před přidáním nové položky nejvyšší úrovně, zvažte umístění příkazu v existující nabídek nejvyšší úrovně. Při přidávání nových nabídek nejvyšší úrovně, je nutné umístit do správného umístění. Rozhodněte, jestli je specifické pro projekt, místní nebo dokumentu v nabídce. Zachovat název nabídek nejvyšší úrovně stručné a používat pouze jedno slovo.  
  
 Nabídky jádra by měl zarážku zbývající příkazy. Soubor, Edit a zobrazení by měl být vždy na levé straně a nástroje, okna, a nápovědu by vždycky měla být na pravé straně.  
  
#### <a name="context-menus"></a>Kontextové nabídky  
 Uvedení příliš mnoho funkcí v rámci kontextové nabídky výsledkem rozhraním obtížné informace. Všechny hlavní funkce musí být k dispozici prostřednictvím panelu hlavní nabídky. Umístění příkazů by měl být souhlasí s existující příkazy, aby se zabránilo duplicitní příkazy. Pro místní nabídky prostředí definuje standardní nabídky skupiny, které by měly být zahrnuty v závislosti na tom, zda je v místní nabídce pro řešení, uzel projektu nebo položky projektu.  
  
 Při navrhování kontextové nabídky, dodržujte stejná pravidla jako hlavní nabídky a navíc:  
  
-   Není delší než 25 položek nabídek nejvyšší úrovně.  
  
-   Kontextová nabídka nabídky jsou přijatelné, ale musí není delší než jednu úroveň – nikdy nepoužívejte kaskádové kontextové nabídky.  
  
-   Použití více než šest oddělovače.  
  
### <a name="command-placement-in-toolbars"></a>Umístění příkazového v panelech nástrojů  
  
#### <a name="general-toolbars"></a>Obecné panelů nástrojů  
 Při navrhování a uspořádání panelů nástrojů, postupujte podle těchto standardů:  
  
-   Nepoužívejte více než jeden příkaz na tlačítko. Jedno tlačítko = jednu akci.  
  
-   Použití textu vedle ikony pouze v případě, že je potřeba posílit s popiskem.  
  
-   Pole se seznamem použijte výhradně pro vlastnosti, které bude možné přepnout v jedné relaci více než jednou. Jinak zpřístupnit vlastnost jinde.  
  
-   Šířka pole se seznamem by se měl rovnat šířku nejdelší položky v rámci pole + 30 %. Například pokud je nejdelší položka 200 pixelů, pak pole se seznamem mělo 260 pixelů na šířku.  
  
-   Omezte použití oddělovače. Použití oddělovače vedle rozevíracího seznamu je odolné proti vzorek, protože tvar z rozevíracího seznamu sám funguje jako vizuálního oddělovače.  
  
-   Ikona skupiny by měl obsahovat na tři až šest ikony.  
  
-   Pokud kvalifikátory za následek více užitečné příkazů, použijte tlačítko rozdělení, který uchovává poslední nastavení:  
  
     ![Rozdělit tlačítka v sadě Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501 c_SplitButtons")  
  
     **Příklad tlačítko rozdělení. Šest příkazy na levé straně je místo toho můžete začlenit do jediné tlačítko.**  
  
#### <a name="product-specific-toolbars"></a>Specifické pro produkt panelů nástrojů  
 Každý produkt můžete zadat, že obsahuje často používá výchozí nástrojů a důležité příkazy a nástrojů výchozí každého produktu by se měla objevit při prvním spuštění sady Visual Studio po instalaci produktu.  
  
 Produkty by je měli využít také skupiny sdílených příkazů a nabídek poskytované rozhraní IDE. Každá skupina sdílené příkazu, nachází ve sdílené nabídky určené k uspořádání souvisejících příkazy srozumitelným způsobem pro daného uživatele. Je důležité využívají tuto strukturu sdílené příkaz za účelem snížení složitosti.  
  
#### <a name="global-toolbars"></a>Globální panelů nástrojů  
 Globální panely nástrojů se musí vejít na jeden řádek právo úprav. Při vytváření nových panelů nástrojů globální, postupujte podle pokynů pro daný typ panelu nástrojů.  
  
 **Panel nástrojů obecné pokyny:**  
  
- Každý panel nástrojů má 24 pixelů v běžných ovládacích prvků (úchytu, přetečení).  
  
- Tlačítko panelu nástrojů je 22 pixelů na šířku, včetně odsazení. Nastavování ikonu tlačítka rozdělení přidá další 11 pixelů šířky.  
  
- Duplikace příkazy mezi panely nástrojů je povolen.  
  
  **Panely nástrojů konkrétní dokumenty** zobrazí, když určitý typ souboru je aktivní a zmizet, když se stane aktivním jiným typem souboru.  
  
- Panely nástrojů konkrétní dokumenty nesmí mít více než 12 tlačítka.  
  
- Celková šířka panelu nástrojů nesmí překročit 300 pixelů.  
  
- Každý typ souboru může mít jeden integrovaném panelu nástrojů nebo jeden konkrétní dokumenty globální nástrojů, ale ne obojí.  
  
  **Panely nástrojů kontextové** zobrazí, když v určitém kontextu je nastavit a zpravidla zůstávají aktivní, delší dobu.  
  
- Tlačítko limit pro všechny panely nástrojů specifickým pro kontext je 18.  
  
- Pokud se většina uživatelů nebude využívat konzistentně příkazy tento panel nástrojů, když je aktivní kontext, není s kontextem Přidružte tento panel nástrojů.  
  
- Ujistěte se, že panelu nástrojů zmizí při ukončení kontextu. Žádná z těchto panelů nástrojů by se zobrazit při spuštění.  
  
  **Panely nástrojů s žádný kontext** nikdy nezobrazí automaticky. Tyto záznamy ukazují, pouze když uživatel aktivuje je. Ponechte maximální šířka pod 200 pixelů.  
  
### <a name="general-organization-and-shell-defined-groups"></a>Obecné organizace a prostředí definované skupiny  
 Použijte existující sdílené příkazy, pro skupinu příkazů a nabídek. Pokud nový příkaz musí být definován, pokuste se umístit ve stávající skupině sdílené příkazu. Pokud nové skupiny musí být definován, pokusí se jeho následné uložení do existující sdílené nabídky blízko skupinu souvisejícím příkazem před vytvořením nového nabídek nejvyšší úrovně. Tím se snižuje složitost příkaz přitom zajistit konzistentní příkaz umístění v integrovaném vývojovém prostředí.  
  
 Sdílený **formátu** nabídky, obvykle se zobrazí v kontextu okna návrháře stylu dokumentu je znázorněn na následujícím obrázku:  
  
 ![Visual Studio formátu nabídky s popisky](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501 d_FormatMenu")  
  
 **Skupiny nabídek v sadě Visual Studio**  
  
### <a name="reducing-and-reusing-commands"></a>Omezení a opětovné použití příkazů  
 Příkazy jsou obvykle zobrazuje v kontextu, pokud chcete snížit počet příkazů, které uživateli se zobrazí v daném okamžiku. Nicméně by měl také znovu použít stávající sdílenou nabídky a příkaz skupiny k zajištění, že příkazovou strukturu zůstává relativně stabilní mezi změnami v kontextu.  
  
 Opětovné použití sdílených příkazů a uvedení nové příkazy blízko související sdílené příkazy snižuje složitost integrovaného vývojového prostředí a vytvoří lepší uživatelský zážitek.  
  
## <a name="naming-commands"></a>Názvy příkazů  
  
### <a name="naming-conventions"></a>Zásady vytváření názvů  
 Příkaz konzistentní pojmenování je velmi důležité, aby uživatelé mohli najít a spustit příkazy z příkazového řádku nebo vytvoření vazby na klávesové zkratky. Názvy příkazů také pomoct pochopit, jaké účelu slouží příkaz, jakmile se zobrazí na panelu nástrojů nebo v nabídce CSS nebo kontextu uživatele.  
  
#### <a name="when-naming-commands"></a>Pojmenování příkazy, pokud:  
  
-   Vytvořte text tak, aby se snadno lokalizovatelný. Další informace o lokalizaci textu, naleznete v tématu [World připravenosti pro sadu Visual Studio](http://msdn.microsoft.com/en-us/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   Být stručné. Příkazy by měl používat více než tří slov.  
  
-   Použít první velká písmena malá a velká písmena: první písmeno každého slova musí být velkými písmeny. Další informace o formátování textu v sadě Visual Studio najdete v tématu [styl textu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Vzít v úvahu umístění příkazu. Je v nejvyšší úrovni nabídky nebo vyskakovacího informačního rámečku? Například při seskupení příkazů pro zarovnání v informační rámeček nejvyšší úrovně příkazu by měl být "Zarovnat" a kontextová nabídka příkazy by měl být "Vlevo" "Vpravo", "Centra", "bloku" a tak dále. By bylo nadbytečné název informační rámeček příkazy "Zarovnat doleva" nebo "Align Right."  
  
     ![Visual Studio formátu nabídky](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502 a_FormatMenu")  
  
### <a name="using-icons-with-commands"></a>Pomocí ikon s příkazy  
 Reserve být Sparing Table používá ikony párování s příkazy. I když přidružení jedinečnou image pomocí příkazu hastens uživateli možnost pro identifikaci tohoto příkazu, dojde k visual nepořádku a nedostatků se nadměrnému využití bitové kopie. Následující pravidla pomoct při rozhodování, jestli se má vytvořit ikona příkazu.  
  
#### <a name="use-an-icon-with-a-command-only-if"></a>Použijte ikonu s pouze pokud příkaz:  
  
-   Ten samý příkaz má ikonu s ním spojená v jiné viditelného produktu společnosti Microsoft, jako jsou například aplikace Microsoft Office.  
  
-   Příkaz budou umístěny na panelu nástrojů, výchozí.  
  
-   Příkaz je příkaz zaměření, které uživatelé můžou přidat do panelu nástrojů pomocí **"Upravit..."** dialogového okna.  
  
## <a name="access-and-shortcut-keys"></a>Přístup a místní klíče  
  
### <a name="overview"></a>Přehled  
 Existují dva typy přiřazení klávesových zkratek:  
  
-   **Přístupové klíče** (označované také jako akcelerátory) povolit přístup klávesnice prostřednictvím nabídky příkazů a každému popisku v dialogovém okně uživatelského rozhraní. Přístupové klíče jsou určeny pro účely usnadnění přístupu, jsou přiřazeny všechny nabídky a většina ovládací prvky dialogového okna, neměly by být zvyklí, vliv pouze na aktuální okno a jsou lokalizovány.  
  
-   **Klávesové zkratky** většinou používat ovládací prvek (Ctrl) a klíče sekvence – funkce (Fn). Jsou určeny více pro zkušené uživatele a podpory produktivity. Tyto jsou přiřazeny pouze pro většinu často používané příkazy a povolení rychlého přístupu při obcházení v hlavní nabídce. Klávesové zkratky jsou určeny k být zapamatovaných a k tomu třeba je přiřadit důvod konzistentní se schématem profilu. Místní klíčových systémů se můžou lišit profilu z profilu. Uživatel může přizpůsobení klávesových zkratek prostřednictvím **nástroje > Možnosti > klávesnice**.  
  
### <a name="assigning-access-keys"></a>Přiřazení přístupových kláves  
 Přístupové klíče se skládají z klávesy Alt a alfanumerické znaky. Přiřaďte přístupový klíč pro každou položku nabídky bez výjimky. Postupujte podle Windows a běžné konvence pro přiřazení přístupových kláves. například přístupový klíč pro **soubor > Nový** by měla být vždy **Alt, F, N**.  
  
 Nepoužívají písmena šířka v pixelech jedním, jako je "i" (v malá i velká) nebo malým "l" a vyhněte se použití znaků s dolní dotahy (g, j, p, q a y), jsou tyto obtížně rozlišovat.  
  
 Nepoužívejte duplicitní klíče, pokud je to možné. V případech, kdy nevyhnutelné duplicity systém nabídek řeší konflikty cyklického všechny příkazy, které používají klíče. Jako příklad pro hypotetické "Number" příkaz v nabídce Soubor, který duplikuje přístupový klíč "N" **Alt, F, N** by vytvořte nový soubor, a **Alt, F, N, N** by k provedení příkazu "Number".  
  
### <a name="assigning-shortcut-keys"></a>Přiřazení klávesových zkratek  
 Nepřiřazujte nové klávesové zkratky, protože nejsou požadována pro každý příkaz a pokud Nepromyšlené daňové systému (a uživatelské paměti). Data z zkušeností zlepšování Program uživatelů (CEIP) označuje, že uživatelům aplikace Visual Studio používat pouze malou podmnožinu integrované klávesové zkratky.  
  
 Při definování klávesové zkratky, postupujte podle těchto pravidel:  
  
- **Použití ovládacího prvku (Ctrl) a klíče sekvence – funkce (Fn).**  
  
- **Zachovat často používané klávesové zkratky.** Zachovat nejpopulárnější klávesové zkratky.  
  
- **Klávesové zkratky pro editory usnadňují typu.** Klávesové zkratky – typ svázat s příkazy, že vývojáři nepotřebuje většinu při psaní kódu. Například **Edit.InvokeSmartTag** musí mít rychlé místní klíč jako Ctrl +/ a ne Alt + Shift + F10.  
  
- **Snažte se o konzistentně s motivem klávesové zkratky.**  
  
- **Postupujte podle pokynů Windows k určení, které modifikační klávesy využívat.** Pomocí kombinace kláves Ctrl pro příkazy, které mají ve velkém měřítku účinky, jako je například příkazy, které platí pro celý dokument. Pomocí kombinace klávesy Shift pro příkazy, které rozšířit nebo doplnit akce standardní klávesovou zkratku. Nepoužívejte kombinace kláves Ctrl + Alt.  
  
- **Odeberte nadbytečné klávesové zkratky.** Pokud máte starší verzi funkce, zvažte odebrání klávesových zkratek, které se používají s extrémně infrequency (méně než 10 pokusech z dat programu CEIP) nebo střední infrequency (méně než 100krát z dat programu CEIP), pokud přístupový klíč poskytuje rychlý přístup k ten samý příkaz. Příklad: C Alt a H, otevře se obsah nápovědy /.  
  
  Není k dispozici jednoduchý způsob, jak zkontrolovat dostupnost místní. Pokud chcete přidat zástupce, postupujte podle těchto kroků:  
  
1.  Zkontrolujte seznam [klávesové zkratky v sadě Visual Studio 2013](http://visualstudioshortcuts.com/2013/) k určení, jestli jsou podobné příkazy do skupiny jenom s.  
  
2.  Přejděte na **nástroje > Možnosti > prostředí > klávesnice** a otestovat zástupce. Zkontrolujte, že každý schéma mapování klávesnice uvedené v části "Platí následující dodatečné schéma mapování klávesnice." Zkontrolujte profily Obecné, C#, VB a C++, jako jsou sdílené složky jedinečný klávesové zkratky. Zástupce je k dispozici, pokud není namapována v některém z těchto míst.