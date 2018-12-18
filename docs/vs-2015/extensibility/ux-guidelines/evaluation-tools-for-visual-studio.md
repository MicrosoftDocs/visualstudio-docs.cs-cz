---
title: Nástroje pro vyhodnocení
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18d055e5fc38c4bd212455773bc5d02ca741edf0
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052457"
---
# <a name="evaluation-tools-for-visual-studio"></a>Hodnocení nástroje pro Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="craftsmanship-checklist-for-visual-studio"></a>Kontrolní seznam řemeslné ruční práce pro Visual Studio
 Kontrolní seznam použijte k vyhodnocení kvality uživatelského prostředí podrobnější informace o vizuálu a interakce.

### <a name="overview"></a>Přehled

-   Ověřte, že všechny příkazy za následek zpětnou vazbu, která uživatele informuje, že byla provedena jejich příkazy.

-   Ověřte, že všechny prvky uživatelského rozhraní a ovládací prvky jsou viditelné ve všech motivů a v režimu vysokého kontrastu.

-   Ověřte, že aktivní a neaktivní výběru jsou vždy rozlišené, jak na úrovni standard a režim s vysokým kontrastem.

-   Ověřte, že fokus vždy viditelné a zřejmý.

### <a name="performance"></a>Výkon

-   Ověřte, že některé indikátor druh "zaneprázdnění" se zobrazí, pokud příkaz má více než jednu sekundu.

-   Ověřte, že pokud příkaz trvá déle než 10 sekund na dokončení, indikátor průběhu explicitní buď determinate (upřednostňováno) nebo neurčitý, se zobrazí.

### <a name="ui-text"></a>Text uživatelského rozhraní

-   Ověřte, že všechny popisky jsou věty nebo název případu a že žádný text je jenom malá písmena.

    ||Opravit|Nesprávný|
    |-|-------------|---------------|
    |**Text příkazu (vše)**|Věty:<br /><br /> **Název adresáře:**|Název adresáře:|
    |**Text tlačítka (klient)**|První velká písmena:<br /><br /> **[Nastavit jako výchozí]**|VÝCHOZÍ SADA AS|
    |**Text tlačítka (online)**|Věty:<br /><br /> **[Nastavit jako výchozí]**||

-   Ověřte, že všechny popisky, s výjimkou záhlaví skupiny a tlačítka, končit dvojtečkou a předcházet ovládací prvek, pomocí kterého se spárovat.

-   Ověřte, že tlačítka, příkazy a odkazy příkaz spustit uživatelské rozhraní pro zachycení uživatelského vstupu končit trojtečka **[...]** .

     Příklady:

    -   **[Rozšířené...]**  tlačítko dialogového okna.

    -   Možnosti příkazu v nabídce Nástroje (**nástroje > Možnosti**) by neměl získat třemi tečkami, protože spouští dialogového okna, samotného je cílem příkazu.

-   Ověřte, zda obsahuje uživatelské rozhraní bez zkratky, s výjimkou standardní podmínky. Pro instanci HTML ani TCP/IP musí být zadány, přestože by měl OOM (nedostatek paměti) a identifikovatelné osobní údaje (identifikovatelné osobní údaje).

### <a name="keyboard-access"></a>Použití klávesnice

-   Ověřte, zda existuje způsob, jak dosažení jednotlivých úkolů pomocí klávesnice. Obecně to lze provést pomocí klávesnice pro každý ovládací prvek, ale pro některé vysoce vizuální oblasti, je přijatelné alternativní řešení, jako je například, že přejdete na zobrazení kódu.

-   Ověřte, že vytvořit kartu pomocí ovládacích prvků v logickém pořadí (zleva doprava a shora dolů). Když je nejvhodnějším postupem pro většinu ovládacích prvků, ne všechny ovládací prvky vyžadují tento přístup. Ověřte například, že přepínač ovládací prvky jsou ve skupině s jednu zarážku tabulátoru.

-   Ověřte, že všechny ovládací prvky mají popisky a zda má každý popisek symbol a (výjimky zahrnují některé-označené jako ovládací prvky, které může díky tomuhle ovládacího prvku s popiskem v kartě).

-   Ověřte, že neexistují žádné mnemonická konflikty.

### <a name="fonts"></a>Písma

-   Ověřte, že všechna písma (pro rozpoznávání tváře, velikost, barvu) jsou používány konzistentně a Udržovat hierarchii.

-   Ověřte, zda všechny prvky uživatelského rozhraní pomocí služby písmo prostředí. (Viz [písma a formátování pro Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Pokud chcete zkontrolovat, pokud služba používá, přejděte na **nástroje > Možnosti > písma a barvy**. V rozevíracím seznamu nastavení zvolte písmo prostředí a změnit řez písma stylistically (například Svoboda nebo sítě SAN Comic) a nastavte velikost 12 bodů. Klikněte na tlačítko OK. Možná budete muset restartovat integrované vývojové prostředí, ale většina uživatelského rozhraní se změní okamžitě. Oblasti, které není získaly písma změny i na restartování nepoužívají písmo prostředí.

-   Ověřte, že písma, která jsou odvozen od třídy service (například text tučné písmo nebo zvětšeným) zachovat jejich velikost a formátování ve vztahu k "normální" text při změně velikost písma prostředí.

-   Ověřte, že zde nejsou žádné chyby výstřižek kvůli rozšířeným písma. Písma, která oříznut získat jsou pravděpodobně výsledkem pevnou výšku ovládacích prvků nebo pevnou výšku kontejnerů.

### <a name="dialogs"></a>Dialogy

-   Ověřte, že název dialogového okna je stejný jako příkaz, který je spouští.

-   Ověřte, že všechny standardní ovládací prvky jsou konzistentní s operačním systémem: je standardní barvu pozadí a žádné ovládací prvky by měly mít speciální bez vizuálního vzhledu re styl, který je odlišný od standardní ovládací prvky se zobrazí.

-   Ověřte, že okrajů formulář by měl být 12 pixelů a by se měla objevit jednotné a konzistentní vzhledem k aplikacím.

-   Ověřte, že dialogová okna na střed v integrovaném Vývojovém prostředí nebo v okně, který je vytvořený.

-   Pokud je to užitečné, dialogová okna by měl být umožňující změnu velikosti. Dialogová okna, které jsou umožňující změnu velikosti ověřte, že při změně velikosti, odpovídající ovládací prvky musí měnit velikost jiné části dialogového okna i nadále konstantní.

-   Ověřte, že umožňující změnu velikosti dialogová okna uchování všech velikostí upravit uživatele (velikost, umístění, rozšiřující ovládací prvky dialogového okna a tak dále).

-   Ověřte, že neexistuje žádná ikona v záhlaví programu.

-   Ověřte, že neexistují žádné tlačítka Minimalizovat a maximalizovat v záhlaví programu.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Operace tlačítka dialogového okna (jenom VS klienta)

-   Ověřte, zda operace tlačítek v tomto pořadí: **OK**, **zrušit**, **použít**.

-   Ověřte, že **OK** a **zrušit** tlačítka jsou standardní velikost: 75 × 23 pixelů.

-   Ověřte, že **OK** a **zrušit** tlačítka jsou stejné velikosti, bez ohledu na délku řetězce.

-   Pokud popisek tlačítka operace vyžaduje být širší než standardní tlačítko, ověřte, že odpovídající **zrušit** tlačítko je stejné velikosti.

-   Ověřte, zda je 6 pixel odsazení tlačítka a přidružených ovládacích prvcích.

-   Ověřte, že **OK** a **zrušit** tlačítka nemají klávesových zkratek (přístupové klávesy určené podtržené písmeno).

-   Ověřte, že jedno tlačítko (obvykle **OK**) ve výchozím nastavení má fokus.

-   Ověřte, že **Esc** zruší dialogového okna

-   Ověřte, že **Enter** výchozího tlačítka se spustí, pokud fokus není v ovládacím prvku, který zpracovává Enter.

-   Ověřte, že **OK** a **zrušit** tlačítka jsou umístěny v pravém dolním rohu dialogového okna. V vzácnými výjimkami je přijatelné pro ně být svisle nad sebou v pravém horním rohu.

-   Ověřte, že svislé konfigurace se používá jenom v případě, že další tlačítka jsou v vodorovné zarovnání v rámci dialogového okna.

### <a name="control-standards"></a>Ovládací prvek standardů

#### <a name="general"></a>Obecné

-   Ověření, pokud je to možné, že vhodné výchozí hodnoty pro urychlení interakci s uživatelem a uživatelé k bezpečné mimořádně nebo běžně výsledek.

-   Ověřte, že standardní ovládací prvky se chovají stejným způsobem tak, aby uživatelé věděli, co se stane, na základě předchozích zkušeností.

#### <a name="label-controls"></a>Ovládací prvky popisku

-   Ověřte, že má každý ovládací prvek popisek a, že každému popisku je vizuálně spárovaná s jeho ovládacího prvku (obvykle v rozsahu 4 až 6 pixel) a je blíž k jeho odpovídající ovládací prvek než pro ostatní ovládací prvky.

-   Ověřte, že popisky jsou umístěny zarovnané vlevo pomocí ovládacího prvku levá strana, pokud je umístěn nad a tak, aby standardních hodnot štítku je v souladu s účaří vstupního textu Pokud umístěny na levé straně, vodorovně na střed.

-   Ověřte, že pokud několik skládaný popisek a vstupní ovládací prvky jsou umístěny na levé straně ovládacího prvku, popisky jsou zarovnané vlevo a stejnou vzdálenost od levého okraje dialogového okna, nikdy zarovnání doprava a stejnou vzdálenost od ovládacích prvků. Dvojice mají rovnoměrně distribuovat pokud potřebují další mezery udávajících seskupení.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Vstupní ovládací prvky (textová pole a pole se seznamem)

-   Ověřte, že při použití výchozí písmo prostředí, výška zobrazení pro textová pole, pole se seznamem a tlačítka všechny 23 pixelů.

-   Pokud se používá text nápovědy, ověřte, že barva je nastavena na `Environment.ControlEditHintText` pomocí služby barvu.

-   Pokud je datové pole povinné pole, které musí být určen jako takové, ověření:

    -   který je nastaven na pozadí `Environment.ControlEditRequiredBackground` a popředí je nastavený na `Environment.ControlEditRequiredHintText`

    -   zda je text nápovědy v ovládacím prvku, který se zobrazí jako **"\<vyžaduje >"**

#### <a name="button-controls"></a>ovládací prvky tlačítek

-   Ověřte, že tlačítka minimální velikost v pixelech 75 × 23, pokud narážely delší text.

-   Ověřte, že tlačítka mít levým a pravým okrajem 3 až 5 pixelů, jakož i odsazení pro obsah.

-   Je nepřijatelné využívat malé čtvercového tlačítka se pouze třemi tečkami **[...]**  na místo něj **[Procházet...]**  tlačítko (nebo podobné funkce). Pokud použijete, ověřte, že tlačítko 23 x 23 velikosti.

-   Pokud existuje více než jeden **[Procházet...]**  tlačítko v dialogovém okně a ověřte, že zkrácenou verzi (jen pro tlačítko se třemi tečkami **[...]** ) se používá pro všechny.

-   Ověřte, že tlačítko se třemi tečkami **[...]**  tlačítka nemají symbol. Pokud je fokus na ovládací prvek vstupu vedle něj, by měla jedna karta přesune fokus na tlačítko se třemi tečkami.

-   Ověřte, že tlačítka, příkazy a odkazy příkaz Spustit sekundární uživatelské rozhraní konektoru, který zachycuje další uživatelský vstup musí končit na tři tečky **[...]** .

#### <a name="hyperlinks"></a>Hypertextové odkazy

-   Ověřte, že ovládací prvek hypertextového odkazu nikdy bliká červená, pokud je aktivní. To je indikátor, že služba barva není aktivováno použití

-   Ověřte, že VS barvy použité jsou:

    -   `Environment.ControlLinkText`

    -   `Environment.ControlLinkTextHover`

    -   `Environment.ControlLinkTextPressed`

-   Ověřte, že hypertextové odkazy modré s žádná podtržení, pokud součástí odstavce.

#### <a name="check-boxes"></a>Zaškrtávací políčka

-   Pokud zaškrtávací políčko víceřádkový text, ověřte, že pole je v souladu s první řádek textu, není svisle na střed ve všech oborech.

-   Ověřte, zda zaškrtávací políčka vždy označují binární volby a ne přesměrovat uživatele nebo otevřete nové okno nebo stránky.

-   Pokud zaškrtávací políčko představuje možnost související s vstupního ovládacího prvku, ověřte, že je umístěný zarovnané vlevo a velmi blízko pod ovládací prvek k označení jejich vztah.

-   Ověřte, zda je zaškrtávací políčko **nikdy** používá jako prostředek k povolení celý obsah dialogového okna nebo stránky.

#### <a name="group-boxes"></a>Skupinové rámečky

-   Ověřte, zda dialogové okno neobsahuje jednoduchý skupinový rámeček v něm, který obsahuje celý obsah dialogového okna.

-   Ověřte, že existují aspoň dva ovládací prvky v rámci každého pole skupiny.

-   Zřídka by měla existovat více než dva skupinové rámečky dialogového okna.

-   Zkontrolujte, že nemáte žádné vnořené skupinové rámečky.

### <a name="icons"></a>Ikony

-   Ověřte, že ikony správně obrácenou při tmavý motiv.

-   Ověřte, že všechny ikony jsou založeny na základní koncepty.

-   Ověřte, že jednotlivé ikony distinct, snadno rozpoznat a nesmí obsahovat více než dva pojmy (bez stavu modifikátor/jazyk).

-   Ověřte, že základní ikona se zobrazuje na střed v prostoru.

-   Ověřte, že všechny ikony čitelné v režimu vysokého kontrastu.

-   Ověřte, že všechny barva použitá v souladu s standardy použití barev.

-   Ověřte, že neexistují žádné olemování (hranice) kolem ikony. (Pokud jsou k dispozici, Haló efekt by měl odpovídat barvu pozadí sousední uživatelského rozhraní).

### <a name="touch-enabled-ui"></a>Dotykově ovládaný uživatelského rozhraní

-   Ověřte, že interaktivní ovládací prvky jsou dostatečně velký, aby se snadno touchable – minimální **23 x 23 pixelů** velikosti

-   Ověřte, zda jsou nejčastěji používané ovládací prvky alespoň **40 x 40 pixelů** velikosti.

-   Ověřte, že interaktivní ovládací prvky mají alespoň **5 pixelů mezery** mezi nimi
