---
title: Složené vzory pro Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebc8f4f6c17af54f4dfdcfc0d0d05c5da9d2d88b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88114073"
---
# <a name="composite-patterns-for-visual-studio"></a>Složené vzory pro Visual Studio
Složené vzory kombinují interakce a prvky návrhu v různých konfiguracích. Mezi nejdůležitější složené vzory v aplikaci Visual Studio s ohledem na konzistenci patří:

- [Vizualizace dat](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Uživatelské rozhraní pro objekty a prohlížení](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modely výběru](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Nastavení trvalosti a ukládání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Dotykové zadání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a> Vizualizace dat

### <a name="overview"></a>Přehled
 Grafy představují vizuální způsob agregace a vizualizace dat s cílem zlepšit rozhodování. Můžou uživatelům pomáhat s velkým množstvím dat, ale málo znamenají, co zachovává pozornost a co by mohlo potřebovat akci.

 Pokud jsou splněné některé z následujících podmínek, bude mít uživatel výhodu z grafu:

- Pomůže vám graf uživatelům identifikovat úkoly, na kterých může pracovat?

- Bude graf uživatelům umožňovat předpověď následků potenciálních změn?

- Pomůže vám graf uživatelům zjišťovat trendy a identifikovat vzorce?

- Bude graf umožňovat uživatelům lepší rozhodování?

- Pomůže graf odpovědět na konkrétní otázku, kterou uživatelé mohou mít v daném kontextu?

#### <a name="general-rules-for-charts"></a>Obecná pravidla pro grafy

- Jasně pište data. Ilustrace bez vysvětlení jsou pouze poměrně obrázky.

- Počáteční osy na nulu, aby nedošlo k zkosení proporcí. Délka řádku a velikost pruhu jsou důležité vizuální pomůcky pro porozumění vztahům mezi datovými body.

- Vytváření grafů, nikoli infografika. Infografika jsou umělecká reprezentace dat a jejich primární cíl je Visual vyprávění příběhu. Grafy mohou (a by měly) vizuálně odvolat, ale nechat data mluvit sama pro sebe.

- Vyhněte se skeumorphism, pruhovým pruhům, kontrastu hashmarks a dalším infografika dotykům.

- Nepoužívejte trojrozměrné efekty jako dekorativní element. Používejte je pouze v případě, že jsou skutečně nedílnou schopností uživatele pochopit informace.

- Nepoužívejte více čar a výplní, protože je možné, že tento typ grafu je obtížné číst a interpretovat správně.

- Nepoužívejte graf (ani žádné ilustrace) jako jediný způsob porozumění konceptu nebo interakci s daty. To uživatelům přináší problémy s zrakovým postižením.

- Nepoužívejte grafy jako nedobrovolný nebo dekorativní prvky na stránce. Jinými slovy, pokud graf nepřidá žádnou hodnotu nebo pomůžete uživatelům problém vyřešit, nepoužívejte ho.

### <a name="chart-types"></a>Typy grafů
 Mezi typy grafů používaných v aplikaci Visual Studio patří pruhové grafy, spojnicové grafy, upravený výsečový graf známý jako kruhový graf nebo prstencový graf, časové osy, bodové pruhy (označují se také jako "diagramy clusterů") a Ganttovy diagramy. Každý typ grafu je užitečný pro komunikaci s různými typy informací.

### <a name="other-charting-considerations"></a>Další otázky k vytváření grafů

#### <a name="color"></a>Color
 K dispozici je určitá paleta barev grafů definovaných pro použití v aplikaci Visual Studio. Paleta je přístupná pro hlavní typy rolety barev a barvy lze odlišit i v případě, že se používají jako velmi úzké řezy barvy. Tyto barvy můžete v libovolné kombinaci použít pro libovolný typ grafu nebo grafu v uživatelském rozhraní. Pokud nepotřebujete mít spoustu různých barev, nemusíte používat všechny sedm barev. Tyto barvy nebyly navrženy pro použití s žádnými prvky popředí, takže neumísťujte text ani glyfy nad tyto barvy. Tyto odstíny by měly být pevně kódované a zpřístupněny vlastním úpravám uživatelů v nabídce **nástroje > možnosti** (viz vystavení [barev koncovým uživatelům](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Barvu|Soustavy|RGB|
|------------|---------|---------|
|![71B252 vzorníku](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113178, 82|
|![BF3F00 vzorníku](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191, 63, 0|
|![FCB714 vzorníku](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252183, 20|
|![903F8B vzorníku](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144, 63139|
|![117AD1 vzorníku](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17 122 209|
|![79D7F2 vzorníku](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121 215 242|
|![B5B5B5 vzorníku](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181 181 181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Uživatelské rozhraní pro objekty a prohlížení
 V této části je uveden kontext pro prohlížení, označovaný také jako náhled kódu, typ uživatelského rozhraní pro objekty, který je jedinečný pro sadu Visual Studio.

### <a name="overview"></a>Přehled

- Uživatelské rozhraní v uživatelském rozhraní by mělo dát uživateli více informací nebo interaktivitu bez odčítání od jejich hlavní úlohy.

- Hlavní model uživatelského rozhraní pro objekty v aplikaci Visual Studio se označuje jako "informace na místě pozornosti".

- Uživatelské rozhraní pro objekty v aplikaci Visual Studio je buď vloženo, nebo plovoucí a buď odolné, nebo přechodné.

  - Zobrazení náhledu kódu, typ uživatelského rozhraní v aplikaci Visual Studio, je vloženo a trvalé.

  - CodeLens, typ uživatelského rozhraní v aplikaci Visual Studio, je plovoucí a přechodný.

  Porozumět tomu, jak část kódu funguje, nebo najít podrobnosti o tomto kódu, často vyžaduje, aby vývojář přepnul kontext a přešel na jiný obsah nebo jiné okno. Tato kontextová posunutí můžou být rušivá, protože uživatelé můžou při opuštění hlavního okna přijít o původní úkol. Kromě toho může být obtížné získat původní kontext zpátky, zejména v případě, že přepnutí systému Windows způsobilo jeho původní kód na zakrytí jiným uživatelským rozhraním.

  Uživatelské rozhraní pro objekty se řídí vzorem s názvem "informace na místě pozornosti". Tyto zprávy, místní okna a dialogová okna poskytují uživatelům další důležité informace, které přidávají vyjasnění nebo interaktivitu bez ztráty fokusu na hlavní úkol. Příklady uživatelského rozhraní pro objekty zahrnují automaticky otevíraná okna, která se zobrazí, když uživatel najede ukazatelem myši na ikonu v oznamovací oblasti, červené vlnovky pod chybně napsaným slovem a náhledem, který se zavádí v Visual Studio 2013.

### <a name="decision-points"></a>Rozhodovací body
 V sadě Visual Studio existuje několik způsobů, jak použít tento model informací v okamžiku pozornosti. Výběr správného mechanismu a jeho implementace konzistentním a předvídatelným způsobem je zásadní pro celkové prostředí. V opačném případě se uživatelům můžou prezentovat matoucí nebo nekonzistentní prostředí, které odmítá fokus od samotného obsahu.

#### <a name="relationships-between-master-and-detail-content"></a>Vztahy mezi hlavním a podrobným obsahem
 Informace v bodě pozornosti slouží k zobrazení vztahu mezi obsahem, na kterém se uživatel zaměřuje ("hlavní" obsah ") a dalším souvisejícím obsahem (" podrobný "obsah). V tomto modelu je podrobný obsah jasně spojen s obsahem, se kterým uživatel pracuje, a může se zobrazit blízko k hlavnímu obsahu. Doplňující informace nebo informace, které nelze shrnout bez zahlcení hlavního obsahu, by měly následovat za jiným vzorem, jako je například okno nástroje.

- **Vždy** zobrazovat podrobný obsah v blízkosti hlavního obsahu.

- **Vždy** zajistěte, aby měl obsah podrobností stále fokus na hlavní obsah. Nejlepším způsobem, jak toho dosáhnout, je vykreslit podrobný obsah co nejblíže hlavnímu obsahu. To lze provést vykreslením podrobného obsahu v překryvném okně vedle hlavního obsahu nebo vykreslením podrobného obsahu vloženého pod hlavním obsahem.

- **Nikdy** nepoužívejte informace v bodě pozornosti, které uživateli přebírají z hlavního obsahu. Pokud uživatelé potřebují zobrazit podrobný obsah samostatně, vystavte explicitní akci, která uživateli umožní to provést.

#### <a name="design-details"></a>Podrobnosti návrhu
 Jakmile se rozhodnete, že uživatelské rozhraní je správné volbou, existují čtyři hlavní požadavky na návrh:

1. **Trvalost:** je očekáváno, že je obsah trvalý nebo přechodný?
   Budou si uživatelé chtít ponechat informace, které se budou zobrazovat, aby mohli odkazovat na nebo pracovat s nimi? Nebo se uživatelé budou chtít rychle podívat na informace a pak pokračovat s hlavní úlohou?

2. **Typ obsahu:** bude obsah informativní, napadnutelný nebo navigace?
   Potřebuje uživatel další podrobnosti o hlavním obsahu? Musí uživatel dokončit úkol, který má vliv na hlavní obsah? Nebo uživatel musí směrovat na jiný prostředek?

3. **Typ indikátoru:** provede okolní indikátor?
   Mohou být informace užitečné a zobrazeny bez zahlcení hlavního obsahu?

4. **Gesta:** jaká gesta budou použita k vyvolání a zavření uživatelského rozhraní?
   Jak si uživatel zavolá podrobný obsah a pošle ho hned? Existuje hodnota pro přidání gesta, jako je například připnutí pro přepínání mezi přechodnými a trvalými stavy?

   Každý z těchto čtyř rozhodovacích bodů bude mít dopad na hlavní součásti uživatelského rozhraní pro objekty.

### <a name="on-object-ui-components"></a>Komponenty uživatelského rozhraní pro objekty

1. Typ kontejneru (předvádějící obsah)

    - Dekadické

    - Přiřazený

2. Typ obsahu

    - Informativní: data, která mohou být statická nebo dynamická

    - Možné akce: příkazy, které mění hlavní obsah

    - Navigace: odkazy, které přijímají uživatele do jiného okna nebo aplikace, jako je například MSDN

3. Gesta

    - Invocation

    - Zavření

    - Připnutí

    - Další interakce

4. Model trvalosti a potvrzení

    - Dočasný

    - Odolné

    - Automaticky

    - Na vyžádání

5. Okolní indikátory (volitelné)

    - Podtržení vlnovkou

    - Ikona inteligentní značky

    - Další okolí ukazatelů

#### <a name="container-content-presenter-type"></a>Typ kontejneru (předvádějící obsah)
 K dispozici jsou dvě hlavní možnosti pro prezentování obsahu v okamžiku pozornosti:

1. **Inline:** vložený předvádějící, jako je náhled zobrazení, který byl představený v editoru kódu Visual Studio 2013, vytváří prostor pro nový obsah posunutím stávajícího obsahu.

    - **Dáváte přednost** vloženému předvádějící, pokud očekáváte, že uživatelé budou chtít strávit významné množství času, který bude odkazovat na obsah, který máte k dispozici, nebo v něm pracovat.

    - **Nepoužívejte** vložené prezentující, pokud očekáváte, že uživatelé budou chtít zobrazit informace, které máte k dispozici, a potom pokračovat v hlavním úkolu s minimálním přerušením.

2. **Floated:** plovoucí předvádějící je umístěn co nejblíže vybranému obsahu, ale nemění rozložení stávajícího obsahu. Můžete použít různé strategie, jako je například zobrazení plovoucího panelu obsahu na nejbližším dostupném prázdném místě pro vybraný symbol.

    - **Preferovat** plovoucí předvádějící, pokud očekáváte, že uživatelé budou chtít zobrazit informace, které jsou k dispozici, a pak pokračovat s hlavním úkolem s minimálním přerušením.

    - **Nepoužívejte** plovoucí předvádějící, pokud očekáváte, že uživatelé budou chtít strávit významné množství času, který bude odkazovat na nebo v interakci s obsahem, který máte k dispozici.

#### <a name="content-type"></a>Typ obsahu
 Existují tři hlavní typy obsahu, které lze zobrazit v jakémkoli kontejneru uživatelského rozhraní v objektu. Můžete zobrazit jakoukoli kombinaci těchto typů informací. Existují tři typy:

1. **Informativní:** Většina kontejnerů uživatelského rozhraní v objektu se zobrazí jako určitý druh informativního obsahu. Obsah může představovat informace o současném stavu prostředí nebo může představovat informace o možném budoucím stavu prostředí. Například lze použít k zobrazení efektu konkrétního příkazu, jako je refaktoring, pro existující kód.

    - **Vždy** používejte kanonickou reprezentaci informací, které zobrazíte. Kód by měl například vypadat jako kód, být dokončen s zvýrazňováním syntaxe a měl by respektovat libovolné písmo a další nastavení prostředí, které uživatel nastavil.

    - V případě, že se stejné informace zobrazují jako hlavní obsah, **vždy** zvažte podporu všech akcí nad informačním obsahem. Pokud například prezentujete existující kód v kontejneru uživatelského rozhraní v objektu, důrazně zvažte možnost Procházet a upravovat tento kód.

    - Při prezentování informačního obsahu, který představuje možný budoucí stav, **vždy** zvažte použití jiné barvy pozadí.

2. Možné akce: některé kontejnery uživatelského rozhraní v objektech budou mít možnost provádět určitou akci nad hlavním obsahem, například provedení operace refaktoringu.

    - **Vždycky** umístit příkazy, které se mají provést, nezávisle na informativním obsahu.

    - V případě potřeby **vždy** povolte a zakažte akce.

    - **Vždy** Přečtěte si standardní pokyny pro reprezentaci příkazů uvnitř dialogových oken.

    - **Vždy** Udržujte počet akcí, které jsou vystaveny v kontejneru uživatelského rozhraní v objektu, do absolutního minima. Interakce s uživatelským rozhraním v uživatelském rozhraní by měla být odlehčené a rychlé prostředí. Uživatel by neměl vyplatit energii při správě samotného kontejneru uživatelského rozhraní v objektu.

    - **Vždy** Vezměte v úvahu, jak a kdy se kontejner uživatelského rozhraní v objektu bude zavřít nebo zrušit. Osvědčeným postupem je, že všechny akce, které uzavírají dialog mezi hlavním a podrobným obsahem, by měly také při vyvolání této akce Zavřít kontejner uživatelského rozhraní v objektu.

3. **Navigace:** některé kontejnery uživatelského rozhraní v objektu obsahují odkazy, které přebírají uživatele do jiného okna nebo aplikace, jako je například otevření článku na webu MSDN v prohlížeči uživatele.

    - **Vždy** předřaďte jakékoli navigační propojení s "otevřený", aby se uživatelé nepřekvapeni pomocí přechodu na jiný obsah.

    - **Vždycky** oddělují navigační odkazy z odkazů s akcemi.

#### <a name="ambient-indicators-optional"></a>Okolní indikátory (volitelné)
 Okolní indikátory můžou být drobné, včetně textu, který je zobrazený v kontrastní barvě od zbytku kódu nebo zjevně, včetně tickler symbolů, jako jsou vlnovky podtržení a ikony inteligentních značek. Okolní indikátory komunikují dostupnost dalších relevantních informací. V ideálním případě poskytují užitečné informace, a to i bez nutnosti uživatele s nimi pracovat.

- **Vždy** umístěte okolí indikátoru tak, aby se uživatel nenavíc ani nepřezahltí. Pokud není možné umístit indikátor okolí takovým způsobem, zvažte jiné řešení.

- **Vždy** Umístěte indikátor okolí co nejblíže k obsahu, ke kterému se vztahuje.

- **Vždy** se pokuste vytvořit indikátor, který shrnuje informace, které zpřístupňuje. Zvažte zadání počtu dostupných datových položek (například "3 odkazy" místo jednoduše "odkazy") nebo si můžete představit jiný způsob sumarizace dat.

  - V případech, kdy data pro indikátor nelze vždy vypočítat a zobrazit, okamžitě zvažte poskytnutí progresivní zpětné vazby při výpočtu hodnot. Zvažte například animace změn, které odpovídají aktualizacím dostupných dat, podobně jako živá dlaždice e-mailu na Windows Phone aktualizuje se, jak se zvyšuje počet nepřečtených e-mailů.

- **Nikdy** Nepřidávat další indikátory, než uživatel může u daného obsahu rozumně brát v úvahu. Okolní indikátory by měly být užitečné bez nutnosti jakékoliv interakce od uživatele. Indikátory ztratí své Ambience, pokud vyžadují přetečení a jiné ovládací prvky pro správu, aby je bylo možné zobrazit.

#### <a name="gestures"></a>Gesta
 Klíčovým aspektem, který uživateli umožňuje zachovat fokus na hlavním obsahu, je podpora správných gest pro otevření a zavření dalšího obsahu podrobností.

- **Vždy** vyžadovat, aby uživatel prováděl nějaký explicitní gesto pro otevření dalšího obsahu. Mezi společná otevřená gesta patří:

  - **Najetí myší:** popisy a neinteraktivní informační obsah

  - **Explicitní příkaz:** vložený předvádějící

  - **Dvakrát klikněte na indikátor okolí:** Automaticky otevírané okno CodeLens

- **Vždy** zavřít podrobný obsah pokaždé, když uživatel stiskne klávesu ESC.

- **Vždy** Vezměte v úvahu kontext uživatelského rozhraní v objektu. Pro předvádějící obsah, který umožňuje interakci v rámci kontejneru, pečlivě zvažte, jestli se mají zobrazit další informace o ukazateli myši, což je pravděpodobně rušivé pro pracovní postup uživatele.

- **Nikdy** nezobrazovat obsah při najetí myší, který je možná upravitelný nebo pozve na interakci uživatele Toto chování může frustrovat uživatele, pokud se pokusí přesunout kurzor nad obsah s podrobnostmi, protože standardní chování pro popis tlačítka se okamžitě odvolá, když ukazatel už není nad hlavním obsahem, který ho vytvořil.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a> Modely výběru

### <a name="overview"></a>Přehled
 Model výběru je mechanismus používaný k označení a potvrzení operací na jednom nebo více objektech, které mají zájem v rámci uživatelského rozhraní. Toto téma popisuje vzory interakcí výběru v rámci editorů dokumentů sady Visual Studio: textové editory, návrhové plochy a povrchy modelování.

 Uživatelé musí mít způsob, jak v aplikaci Visual Studio navýšit, na čem pracují, a Visual Studio musí reagovat na předpověď s názory uživatelů na to, na čem pracuje. Rozdíly nebo nesprávná komunikace mezi uživatelem a uživatelským rozhraním může mít za následek, že uživatel nevšímáte akci, což může mít nezamýšlené důsledky. Často se chyba neprojeví, dokud se uživatel nestane, že nějaká položka chybí nebo se změnila. Modely výběru jsou proto jedním z nejdůležitějších částí návrhu uživatelského rozhraní. I když jsou modely výběru v aplikaci Visual Studio konzistentní s Windows, existují mírné odchylky.

 V aplikaci Visual Studio, jako v systému Windows, se modely výběru liší v závislosti na kontextu, ve kterém se interakce vyskytuje. Výběry mohou nastat ve čtyřech typech objektů:

- Text

- Grafické objekty

- Seznamy a stromy

- Mřížky

  V rámci těchto objektů existují tři typy výběru:

- Navazující

- Nesouvislý

- Oblast

#### <a name="scope"></a>Obor
 Nejdůležitější součástí výběru je zajistit, že uživatel ví, ve kterém okně pracují (aktivace) a kde se nachází fokus (výběr). Visual Studio rozšiřuje funkce správy oken ve Windows, ale schéma aktivace je stejné: interakce s oknem přináší fokus na okno. Visual Studio má dva indikátory pro aktivaci: jeden pro okna dokumentů a jeden pro okna nástrojů.

 V případě oken dokumentů je aktivní okno označeno na kartě okna dokumentu, které přichází dopředu a mění jeho barvu pozadí:

 ![Aktivní výběr karty v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713 – 01_ActiveTab")

 **Aktivní výběr karty**

 V případě oken nástrojů je aktivní okno označeno změnou barvy oblasti záhlaví okna nástroje:

 ![Aktivní výběr okna nástrojů v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713 – 02_ActiveToolWindow")

 **Aktivní okno nástroje znázorňující primární výběr uzlu**

 ![Neaktivní výběr okna nástrojů v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713 – 03_InactiveToolWindow")

 **Neaktivní okno nástroje, které zobrazuje latentní výběr uzlu**

 Jakmile je okno aktivní, jeho fokus je uveden podle modelů výběru popsaných v této části pokynů.

#### <a name="context"></a>Kontext
 Aplikace Visual Studio byla navržena tak, aby zachovala silný koncept kontextu a udržela přehled o tom, kde uživatel pracuje. Aktivní je pouze jedno okno, bez ohledu na to, zda se jedná o nástroj nebo okno dokumentu. U horního okna dokumentu se ale vždycky zachová latentní výběr. I když se fokus může nacházet v okně nástroje, okno dokumentu, které bylo naposledy aktivní, zobrazuje výběr, i v neaktivním stavu. K tomu je potřeba zachovat kontext uživatele v dokumentu, který upravovali, a zobrazit tak, že Visual Studio zachovalo svůj stav, aby se mohli bezproblémově vracet mezi okny nástrojů a dokumentací.

### <a name="text-selection"></a>Výběr textu
 Editory sady Visual Studio, které jsou čistě textové, jako je například Vestavěný textový editor, používají stejný model výběru textu a vzhled popsaný na stránce [myš a ukazatele](/windows/desktop/uxguide/inter-mouse) v pokynech pro interakci uživatelského prostředí systému Windows na webu MSDN. Vstupní fokus v textovém editoru je označen svislým pruhem nazývaným bod vložení. Bod vložení je široký a barevně se vybarví jako informující o tom, co se zobrazuje za ním. V Ovládacích panelech se v závislosti na kartě **rychlost** v apletu **klávesnice** v ovládacím **panelu bliká.**

#### <a name="contiguous-and-disjoint-selection"></a>Souvislý a nesouvislý výběr
 Výběr v rámci textového editoru je pouze souvislý. Nesouvislé výběry textu nejsou povolené, ale měly by se adresovat v grafických editorech objektů. Když je ukazatel myši uživatele nad textovou oblastí, ukazatel se změní na světlo. Jediným kliknutím umístíte kurzor v textovém editoru do umístění pro kliknutí. Podržením tlačítka myši v rozevíracím seznamu se zobrazí zvýraznění výběru a uvolnění tlačítka myši končí zvýrazněním výběru.

#### <a name="region-selection-box-selection"></a>Výběr oblasti (výběr pole)
 Visual Studio podporuje výběry oblastí v textovém editoru a tato možnost se nazývá výběr boxu. Výběr pole umožňuje uživateli vybrat oblast textu, která nenásleduje za běžným textovým datovým proudem. Stejně jako u výběru standardního textu musí být výběr souvislý. Výběr pole se iniciuje stisknutím klávesy ALT při přetahování myší. Výběr pole lze také iniciovat tak, že podržíte klávesy ALT a Shift při použití kláves se šipkami k označení oblasti výběru. Výběr pole používá zvýraznění normálního výběru a ukazuje kurzor místa kurzoru na konci oblasti výběru.

 ![Oblastní &#40;&#41; výběru v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713 – 04_BoxSelection")

 **Oblast (box) výběr v aplikaci Visual Studio**

#### <a name="text-selection-appearance"></a>Vzhled výběru textu
 Barvy používané pro aktivní a neaktivní výběr v editoru lze přizpůsobit. Chcete-li přizpůsobit vizuální vzhled editoru, může uživatel přejít na **nástroje > možnosti**a potom hledat v části **prostředí > písma a barvy > textový editor**.

### <a name="graphical-selection"></a>Grafický výběr

#### <a name="interaction"></a>Interakce
 Výběr grafického objektu může být složitý a závisí na několika faktorech:

- **Model primárního výběru editoru.** Editory, které obsahují grafické objekty, lze také použít k úpravě textu nebo mřížky. Editor může být například textový editor, který podporuje také umístění grafických objektů, jako je například Návrhář XAML sady Visual Studio. Podpora více typů objektů může ovlivnit způsob, jakým uživatel vybere skupiny vytvořené z různých typů objektů.

- **Podpora pro primární a sekundární stavy výběru.** Editor může poskytovat stavy primárního a sekundárního výběru, aby bylo možné objekty upravovat v úlohách, vzájemně zarovnané, velikost společně a tak dále.

- **Podpora místních úprav.** Editory mohou také umožňovat úpravu obsahu jejich grafických objektů. Například tvar obdélníku může obsahovat také text v rámci, který může změnit uživatel. Kromě toho může být tento text zarovnán na střed nebo odůvodněný. Místní úpravy zahrnují podrobnější úroveň interakce s uživatelem, a proto vyžadují vhodnou sadu vizuálních pomůcek pro prezentaci informací o stavu uživateli.

#### <a name="mouse-interaction"></a>Interakce myši

|Vstup|Výsledek|
|-----------|------------|
|Klikněte na nevybraný objekt.|Vybere objekt a zobrazí přerušované čáry a úchyty výběru, pokud lze změnit velikost objektu.|
|Klikněte na vybraný objekt.|Aktivuje místní úpravy, pokud je objekt podporuje. Kliknutím mimo objekt dojde k deaktivaci místního režimu úprav.|
|Dvakrát klikněte na objekt.|Otevře kód za objektem pro úpravy a může v případě potřeby Vložit výchozí obslužnou rutinu události.|
|Ukázat na objekt|Změní ukazatel na kurzor přesunutí. Vzhled objektu, jako je jeho světlost nebo barva, se může změnit.|
|Nasměrování na popisovač výběru|Změní ukazatel na kurzor pro změnu velikosti. U objektů, které podporují rotaci, může některé úchyty výběru změnit ukazatel na otočení kurzoru, protože ukazatel je umístěn odlišně (například přesunutím více) s ohledem na popisovač výběru.|
|Myší|I v případě, že objekt není dříve vybrán, změní ukazatel na kurzor přesunutí a přesune objekt.|
|Editor ztratí fokus|Deaktivuje místní režim úprav, i když objekt uchovává obsah a vzhled, který měl během posledního provozu nebo stavu výběru.|
|Výběr objektu|Označeno ohraničením, tečkovanou čárou nebo jiným vizuálně odlišným způsobem, který zvýrazní hranici objektu.|
|Změna velikosti vybraného objektu|Označeny popisovači výběru.<br /><br /> Objekt s možností změny velikosti má osm popisovačů, které představují jednotlivé směry, ve kterých se dá změnit její velikost. Pokud je možné změnit velikost objektu pouze v určitých směrech, lze použít méně popisovačů. Když uživatel velikost objektu rozloží na, kde osm popisovačů nebudou interaktivní, mohou být použity čtyři popisovače. Velikosti popisovačů by měly být svázané s metrikami ohraničení a okraje okna s funkcí rozhraní API **GetSystemMetrics** , aby se velikost zobrazovala v poměru k rozlišení obrazovky.<br /><br /> ![Úchyty pro změnu velikosti](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713 – 05_ResizeHandles")|
|Otočení vybraného objektu|![Úchyty pro otáčení](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713 – 06_Rotate")|

#### <a name="keyboard-interaction"></a>Interakce klávesnice

|Vstup|Výsledek|
|-----------|------------|
|Karta|Přesune ukazatel fokusu mezi logické pořadí objektů v editoru. To může být zleva doprava nebo shora dolů v závislosti na hodnotě vlastnosti **TabIndex** (nebo ekvivalentní), pořadí vytvoření objektu a celkovém účelu editoru. SHIFT + TAB obrátí směr indikátoru fokusu.|
|Mezerník|Aktivuje režim posouvání, když se zachová klávesová zkratka. K posunu pozice zobrazení je potřeba další vstup myši.|
|Ctrl + mezerník|Aktivuje režim lupy při údržbě klávesových zkratek. K navýšení a snížení měřítka lupy je potřeba další vstup myši.|
|CTRL + ALT + mínus – symbol|Zmenší faktor přiblížení o jednu úroveň.|
|CTRL + ALT + znaménko plus|Zvětší faktor přiblížení o jednu úroveň.|
|Shift nebo CTRL|Přidá objekt do skupiny výběru. CTRL také umožňuje odebrat objekty samostatně ze skupiny výběru.|
|Enter|Provede výchozí příkaz pro objekt (obvykle otevřít nebo upravit).|
|F2|Aktivuje místní úpravy objektu.|
|Šipkové klávesy|Přesune vybrané objekty ve směru stisknutí klávesy se šipkou, v malých přírůstcích (například po 1 pixelech v daném čase).|
|CTRL + klávesy se šipkami|Přesune vybraný objekt (y) ve směru stisknutí klávesy se šipkou, ve větších přírůstcích (například 10 pixelů najednou).|
|Shift + klávesy se šipkami|Změní velikost vybraných objektů v příslušném směru, a to v malých přírůstcích (například 1 pixel v čase).|
|CTRL + SHIFT + klávesy se šipkami|Změní velikost vybraných objektů v příslušném směru ve větších přírůstcích (například 10 pixelů najednou).|

 Když uživatelé upravují ovládací prvky, může být vhodné, aby objekty automaticky měnily velikost pomocí vstupu uživatele. Pokud uživatel například upraví ovládací prvek popisek, měl by popisek zvětšit, aby zobrazil text, který uživatel právě zadal. Pokud to není hotové, uživatel musí změnit velikost ovládacího prvku ručně po úpravě textu. Pokud má uživatel spoustu ovládacích prvků, jedná se o Rote a neproduktivní úkol.

#### <a name="graphical-containers"></a>Grafické kontejnery
 V některých případech grafické editory poskytují kontejnery pro jiné grafické objekty, jako je ovládací prvek panelu model Windows Forms nebo ovládací prvek rozložení mřížky v Návrháři HTML. Pokud editor poskytuje kontejnery pro jiné grafické objekty, měl by se použít následující model výběru pro kontejner (objekty v kontejneru se řídí standardním modelem, jak je popsáno výše):

|Vstup|Výsledek|
|-----------|------------|
|Jediné kliknutí na kontejner|Vybere objekt kontejneru bez přímého výběru některého z obsažených objektů. Kontejner se dá přesunout nebo změnit jeho velikost standardním vstupem myši a klávesnicí (jak je popsáno výše). Obsažené objekty jsou přesunuty ve vztahu ke kontejneru, ale u obsažených objektů se nezmění velikost, pokud nejsou zároveň přímo vybrány.|
|Najeďte myší na oblast hranice kontejneru|Zapne ukazatel myši na kurzor přesunutí, který označuje, že lze kontejner přesunout.|
|Přetáhněte oblast hranice kontejneru.|Změní ukazatel myši na kurzor přesunutí a přesune kontejner (a obsažené objekty v rámci). Kontejner nelze přesunout bez předchozího výběru jediným kliknutím.|
|Jedním kliknutím na objekt v kontejneru|Odškrtne kontejner (Pokud je vybrán) a vybere pouze vybraný objekt.|
|Shift + kliknutí nebo Ctrl + kliknutí na obsažený objekt a kontejner|Přidá vybraný objekt do existující skupiny výběru nebo výběru. Pokud je vybraný objekt již členem skupiny výběru, je odebrán ze skupiny výběru.|

 Obsažené objekty by měly splňovat základní model výběru, jak je popsáno v předchozí části. Z testování použitelnosti návrháře model Windows Forms uživatelé očekávali bezproblémový přístup k objektům, které obsahují, bez nutnosti přecházet k uvedeným krokům (uložené objektem omezení).

#### <a name="disjoint-and-region-selections"></a>Nesouvislé a výběr oblasti
 Grafické editory objektů by měly podporovat nesouvislé výběry. Uvědomte si prosím, že tento obrázek nezobrazuje vzhled ovládacího prvku pro Visual Studio. Podrobné specifikace vizuálů najdete v tématu [vzhled výběru grafického objektu](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) .

 ![Nesouvislé a selektory oblastí](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713 – 07_DisjointRegionSelectors")

 **Nesouvislý výběr**

 Grafické editory by měly také nabízet výběry oblastí s indikátorem výběru typu rámečku. Pokud grafický editor podporuje jiné typy objektů (například text), pak výběry oblastí nemusí být možné v závislosti na omezeních těchto jiných typů objektů.

 ![Výběr běžícího textu](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713 – 08_MarqueeSelection")

 **Výběr běžícího textu**

#### <a name="primary-and-secondary-selections"></a>Primární a sekundární výběr
 Některé editory grafických objektů umožňují uživateli upravovat nebo zarovnávat objekty ve skupinách. V tomto případě je potřeba zavést koncept primárního a sekundárního výběru. Primární výběr je objekt, na který všechny ostatní objekty reagují na operace skupiny. Objekt, který uživatel vybere jako první, se stane primárním ovládacím prvkem a následné výběry se stanou sekundárními výběry. Primární výběr má odlišné vizuální zpracování ze sekundárních výběrů k označení, který objekt je primární:

 ![Primární a sekundární výběr](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713 – 09_PrimarySecondary")

 **Primární výběr se dvěma sekundárními výběry**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Vzhled výběru grafického objektu
 Popisovače výběru jsou čtverce vykreslené v obdélníkovém vzoru kolem ohraničujícího rámečku objektu. Následující graf ukazuje příklady různých stavů, které může grafický objekt mít s popisovačem, velikostí a místním zobrazením úprav. Velikost popisovačů by měla být svázaná s metrikami ohraničení a okraje okna pomocí rozhraní API **GetSystemMetrics** .

| Stav | Příznaky | Podrobnosti vizuálu |
|-------------------------|---------------| - |
| **Nevybrané** | Výchozí | ![Výchozí stav tlačítka](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713 – 10_DefaultState") |
| **Primární výběr** | Možností změny velikosti | ![Primární výběr s úchyty pro změnu velikosti](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713 – 11_PrimaryResize") |
| **Primární výběr** | Nelze měnit velikost | ![Primární výběr bez úchytů pro změnu velikosti](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713 – 13_PrimaryNoResize") |
| **Primární výběr** | Uzamčeno | ![Primární výběr uzamčen](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713 – 15_PrimaryLocked") |
| **Sekundární výběr** | Možností změny velikosti | ![Sekundární výběr s úchyty pro změnu velikosti](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713 – 17_SecondaryResize") |
| **Sekundární výběr** | Nelze měnit velikost | ![Sekundární výběr bez úchytů pro změnu velikosti](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713 – 19_SecondaryNoResize") |
| **Sekundární výběr** | Uzamčeno | ![Sekundární výběr uzamčen](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713 – 21_SecondaryLocked") |
| **Uživatelské rozhraní aktivní** | Výchozí | ![Aktivní stav uživatelského rozhraní](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713 – 23_UIActive") |

### <a name="view-selection-models"></a>Zobrazit modely výběru

#### <a name="tree-view"></a>Stromové zobrazení
 Výběr ve stromovém zobrazení se zobrazí s jednoduchým zvýrazněním. Pokud uživatel klikne na název uzlu nebo na ikonu uzlu, uzel se vybere. Trojúhelníkové glyfy nalevo od uzlu rozbalí nebo nařídí stromovou strukturu, ale neovlivňují výběr uživatele, s jednou výjimkou: Při sbalení nadřazeného uzlu, pokud je výběr na podřízeném uzlu, výběr se přesune na nadřazenou položku.

 ![Typické stromové zobrazení v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713 – 25_TreeView")

 **Typické stromové zobrazení v aplikaci Visual Studio**

 Stromová zobrazení mohou podporovat souvislé a nesouvislé výběry, a to i na různých úrovních stromu. V viditelných uzlech stromu musí být proveden souvislý nebo nesouvislý vícenásobný výběr. Je-li uzel sbalen, je nesouvislý výběr ztracen a uzel, který byl sbalen, získá výběr. Tímto způsobem může uživatel zobrazit uzly, které budou mít vliv na operaci. Když jsou uzly sbaleny, je nejasné, které uzly mohou být ovlivněny.

 Pokud je vybrán nadřazený uzel, operace by měla být použita pro nadřazenou položku, i když se může jednat o případy, kde má smysl, aby se operace mohla vztahovat na nadřazenou položku a všechny její podřízené položky. V takovém případě poskytněte během operace další uživatelské rozhraní, například zaškrtávací políčko nebo potvrzovací dialog, aby byla možnost použít u všech podřízených prvků pro uživatele explicitní.

##### <a name="renaming"></a>Měníte
 Pokud uzly ve stromu podporují přejmenování, je třeba provést přejmenování na místě. Místní operace by měla být standardem ve všech ovládacích prvcích stromu v aplikaci Visual Studio. Poskytněte příkaz pro přejmenování, který okamžitě aktivuje místní režim úprav, přičemž výběr textu pokrývá celý název uzlu, připravený na přijetí vstupu uživatele. Pokud uzel představuje soubor, název souboru by měl obsahovat příponu. Zvýraznění výběru by mělo obsahovat pouze tělo názvu souboru a nikoli příponu.

|Vstup|Výsledek|
|-----------|------------|
|Enter – klávesa|Potvrdí operaci přejmenování.|
|Klávesa ESC|Zruší operaci přejmenování.|
|Kliknutí mimo místní oblast úprav|Potvrdí operaci přejmenování.|
|Zpět|Pro zrušení operace přejmenování zadejte snadné zrušení.|

#### <a name="selection-within-lists-and-grid-controls"></a>Výběr v rámci seznamů a ovládacích prvků mřížky
 Klíčovým konceptem výběru seznamu je to, že se jedná o řádek, což znamená, že když je výběr proveden jako jednotka, je vybrán celý řádek. Naopak mřížky umožňují vybrat konkrétní buňky, aniž by to ovlivnilo jakýkoliv jiný aspekt řádku. Mřížky mohou také obsahovat hierarchii vnořených řádků (například TreeGrid), které umožňují vybrat a zrušit výběr celé větve hierarchie, a to prostřednictvím interakce s nadřazenými řádky. Výběr v seznamech je zobrazený jednoduchou barvou zvýraznění na celém řádku dat. Fokus je zobrazen tečkovaným ohraničením s jedním pixelem kolem aktuálního upravitelného řádku nebo buňky (pokud jsou všechny buňky jen pro čtení).

> [!NOTE]
> **Zaměření** a **Výběr** jsou různé koncepty. *Fokus* je indikace toho, který prvek uživatelského rozhraní je zaměřen na příjem vstupu, který není explicitně směrován na jiný objekt, zatímco *Výběr* odkazuje na stav začlenění objektu do sady objektů, na kterých mohou být provedeny následné operace.

 Výběry v seznamech mohou být souvislé, nesouvislý nebo oblast. Je-li povoleno více výběrů, souvislý a nesouvislý výběr by měl být vždy podporován, zatímco podpora pro výběry oblastí (box) je volitelná. Výběry oblastí jsou iniciovány přetažením v prázdném místě textu seznamu.

| Objekt | Výběr |
|--------|------------|
| Seznam | Navazující |
| Seznam | Nesouvislý |
| Seznam | Oblast |

 Po kliknutí na seznam se vybere řádek, na kterém došlo k kliknutí. Pokud se uživatel stane, že klikne na buňku seznamu, která podporuje místní úpravy, je tato buňka také okamžitě aktivována pro místní úpravy. V opačném případě se vybere celý řádek a zobrazí se zvýraznění.

 Přetahování v těle seznamu má jednu ze tří věcí:

- Inicializuje výběr oblasti, pokud ho seznam podporuje a myš rozevíracího seznamu je v prázdném prostoru.

- Inicializuje operaci přetažení, pokud buňka nebo řádek seznamu podporuje zdroj přetažení.

- Vybere aktuální řádek.

##### <a name="in-place-editing"></a>Místní úpravy
 Pokud je povoleno místní úpravy, existují dva základní modely: jednoduchý ovládací prvek pro úpravy a výběr vlastností. U jednoduchého ovládacího prvku pro úpravy je obsah zvýrazněný a připravený pro vstup uživatele, jakmile se aktivuje místní úpravy. Kde je implementováno výběr vlastnosti, tlačítko, které vyvolá výběr vlastnosti, je zobrazeno po aktivaci režimu místní úpravy a aktuální výběr není zvýrazněn. Tlačítko pro výběr by mělo být v buňce zarovnané vpravo. Příklady místních úprav naleznete v **okně Vlastnosti** a **seznam úkolů** v aplikaci Visual Studio.

##### <a name="keyboard-support"></a>Podpora klávesnice
 Podpora klávesnice pro výběr v seznamech a Gridech se řídí standardními konvencemi Windows:

- Klávesy se šipkami budou procházet seznam a vybrat jednotlivé řádky nebo buňky při přesunu fokusu.

- Shift + šipka provede souvislý výběr ve směru šipky kláves.

- Ctrl + šipka následovaná klávesou mezerník přepíná mezi přidáváním a odebíráním položek seznamu z výběru a vytváří nesouvislý výběr.

- Pro mřížky, které obsahují vnořené hierarchie, klávesa šipka vpravo rozbalí nadřazený řádek a klávesou šipka vlevo sbalí jednu.

- Klávesa TAB přesouvá fokus mezi buňkami v aktuálním řádku, pokud jsou buňky editovatelné.

- Klávesa ENTER provede výchozí příkaz pro položku v seznamu (často **otevřít**).

- Klávesa F2 aktivuje místní úpravy pro aktuálně vybranou buňku.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Nastavení trvalosti a ukládání

### <a name="overview"></a>Přehled
 I když je každá součást softwaru v aplikaci Visual Studio obvykle zodpovědná za svůj stav a trvalost, Visual Studio automaticky ukládá nastavení v některých případech, například u velikostí oken a umístění. Tabulka níže je kombinací nastavení automaticky uložených a nastavení, které vyžaduje, aby se provedla explicitní akce uživatele nebo programu.

|Objekt|Co Uložit|Kdy se má uložit|Kam ukládat|
|------------|------------------|------------------|-------------------|
|Volitelný objekt (například řádek kódu)|Zarážka na řádku kódu<br /><br /> Zástupce uživatele přidružený k řádku kódu|Když je projekt uložený|Soubor **možností uživatele (. suo)** pro projekt|
|Dialogový|Umístění dialogového okna, pokud bylo přesunuto<br /><br /> Zobrazení, které uživatel naposledy použil v dialogovém okně|Po zavření dialogového okna<br /><br /> Po ukončení relace sady Visual Studio|V paměti<br /><br /> Registr v **HKEY_CURRENT_USER**|
|Okno|Velikost a umístění okna|Po zavření okna<br /><br /> Při změně režimu sady Visual Studio<br /><br /> Po ukončení relace sady Visual Studio|Soubor **možností uživatele (. suo)** pro projekt<br /><br /> Soubor vlastních možností pro nastavení okna|
|Dokument|Aktuální výběr v dokumentu<br /><br /> Zobrazení dokumentu<br /><br /> Posledních několik míst navštívených uživatelem|Při uložení dokumentu|Soubor **možností uživatele (. suo)** pro projekt|
|Project|Odkazy na soubory<br /><br /> Odkazy na adresáře na disku<br /><br /> Odkazy na jiný software<br /><br /> Komponenty<br /><br /> Informace o stavu samotného projektu|Když je projekt uložený|Soubor projektu|
|Řešení|Odkazy na projekty<br /><br /> Odkazy na soubory|Při uložení projektu nebo řešení|Soubor **řešení (. sln)**|
|Nastavení v **nabídce nástroje > možnosti**|Přizpůsobení klávesnice<br /><br /> Přizpůsobení panelu nástrojů<br /><br /> Barevná schémata|Po zavření dialogového okna **nástroje > možnosti**<br /><br /> Po ukončení relace sady Visual Studio|Registr v **HKEY_CURRENT_USER**|

 Co uživatel dělá a kdy to dělá, zjistí, zda je nastavení uloženo v paměti (během relace), uloženo na disk (napříč relacemi jako nastavení registru) jako součást samotného souboru projektu nebo řešení, jako součást souboru **možností řešení (. suo)** , nebo jako soubor vlastního nastavení, o kterém ví pouze tato softwarová součást. V tabulce výše najdete několik událostí, v nichž lze nastavení uložit. Existují však další časy, ve kterých byste mohli chtít uložit stav:

- Když uživatel změní umístění v rámci dialogového okna nebo okna

- Když uživatel přenese fokus do jiného okna

- Když uživatel přepne z návrhu do režimu ladění

- Když se uživatel odhlásí z účtu

- Když počítač přejde do režimu hibernace nebo se vypne.

- Když se chystá znovu naformátovat a nastavit počítač nebo pevný disk

### <a name="window-configurations"></a>Konfigurace oken
 Konfigurace okna je základní prezentace vývojového prostředí – jedná se o schéma sestávající ze seznamu oken nástrojů a způsobu, jakým jsou uspořádány. Pro systém Windows, který je spravován ROZHRANÍm IDE (Windows IDE), jsou informace o rozložení trvalé pro jednotlivé uživatele, takže když uživatel spustí integrované vývojové prostředí (IDE), rozložení okna se zobrazí stejně jako při posledním ukončení sady Visual Studio. Stav a poloha oken IDE jsou trvalé ve vlastním souboru možností ve formátu XML. Okna nástrojů, která jsou vytvořena balíčky načtenými do integrovaného vývojového prostředí, uchovávají informace o stavu v registru a mohou nebo nemusí být vázaná na uživatele.

#### <a name="profile-specific-layouts"></a>Rozložení pro konkrétní profil
 Každý profil zahrnuje rozložení oken nástrojů uspořádaná způsobem, který je obeznámen se specifickým vývojářům osoby (Visual C++ vývojářům očekávat **Průzkumník řešení** na levé straně rozhraní IDE, zatímco vývojáři v jazyce C# očekávají, že **Průzkumník řešení** na pravé straně). Rozložení okna pro konkrétní profil se načítají poté, co uživatel zvolí profil při spuštění. Autor balíčku by měl určit rozložení oken nejvhodnější pro činnost svého zákazníka, a to s vědomím, že změny, které uživatel provede v konfiguraci okna, budou trvalé.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a> Dotykové zadání
 U zařízení s dotykovým ovládáním se uživatelům stále častěji používají vývojové produkty Microsoftu. Existují však bariéry, které usnadňují použití vývojářských nástrojů na dotykové zařízeních. Uživatelé očekávají, že naše produkty budou poskytovat spolehlivé a přesné možnosti dotykového ovládání. Účelem těchto pokynů je informovat o rozhodnutích o tom, které dotykové možnosti začlenit a podpořit konzistentní možnosti dotykového ovládání v rámci sady Visual Studio a souvisejících produktů.

### <a name="levels-of-experience"></a>Úrovně zkušeností
 Následující úrovně zkušeností mají sloužit jako vodítko, které týmům usnadňují rozhodování o tom, které dotykové možnosti nabízí na základě požadované úrovně investičních zájmů.

- **Základní prostředí** je určené pro týmy, které chtějí poskytovat dotykové možnosti, takže nedochází k neaktivním koncům v průběhu práce.

- **Optimalizované prostředí** je určené pro týmy, které chtějí poskytovat nejběžnější možnosti dotykové ovládání (například ty, které jsou obvykle k dispozici v aplikacích Internet Browser).

- **Prostředí se zvýšenými oprávněními** je určené pro týmy, které chtějí přidat funkce, jako jsou gesta nebo jiné volitelné funkce, které jim umožní přizpůsobovat jejich použití.

||Základní prostředí|Optimalizované prostředí|Prostředí se zvýšenými oprávněními|
|-|----------------------|--------------------------|-------------------------|
|**Povoluje uživatelům...**|Opravit kód a řešení/projekt-úroveň čtení bez mrtvých konců|Provádění údržby, refaktorů a navigačních úloh|Spolehlivá, intuitivní a plynulé zážitky v provozu|
|**Editor**|Posouvání dotykem a výběr<br /><br /> Klávesa ScrollBar – dotykové ovládání a stisknutí klávesy Ctrl + přetažení|Gesto roztažení prstů přiblížení<br /><br /> Rychlý posun<br /><br /> Výběr<br /><br /> Snadné použití místní nabídky||
|**Okna hlavních nástrojů**|Posouvání seznamu<br /><br /> Výběr položky<br /><br /> Klávesa ScrollBar – dotykové ovládání a stisknutí klávesy Ctrl + přetažení|Snadné posouvání a výběr položek||
|**Oken**||Změnit velikost okna<br /><br /> Rychlý přístup||
|**Dobře zdokumentovat**||Snadná navigace mezi otevřenými soubory||
|**Gesta**||Zajištění fungování běžných gest napříč IDE|Akce založené na gestech<br /><br /> Podpora přetahování a návrhářů|
|**Další důležité informace**|||Vlastní klávesnice na obrazovce|

#### <a name="gestures"></a>Gesta
 Gesta poskytují uživatelům zástupce pro příkazy, které by jinak vyžadovaly složitější interakci. Přečtěte si pokyny pro systém Windows na [běžných gest dotykového ovládání pro aplikace klasické pracovní plochy](/windows/desktop/wintouch/windows-touch-gestures-overview)a postupujte podle těchto pokynů pro většinu gest, včetně jednoduchých gest, jako je například posouvání a přiblížení.
