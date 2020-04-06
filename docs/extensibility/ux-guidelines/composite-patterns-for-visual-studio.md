---
title: Složené vzorky pro visual studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 500ea8ffe7c33c1d747590ea074bff43fa1a3ab3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698621"
---
# <a name="composite-patterns-for-visual-studio"></a>Složené vzory pro Visual Studio
Složené vzorky kombinují prvky interakce a návrhu v různých konfiguracích. Některé z nejdůležitějších složených vzorů v sadě Visual Studio s ohledem na konzistenci patří:

- [Vizualizace dat](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [UI na objektu a prohlížení](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Výběrové modely](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Nastavení trvalosti a ukládání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Dotykové ovládání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a>Vizualizace dat

### <a name="overview"></a>Přehled
 Grafy jsou vizuálním způsobem, jak agregovat a vizualizovat data za účelem zlepšení rozhodování. Mohou pomoci uživatelům, kteří čelí mnoha datům, ale jen málo to znamená, co si zaslouží pozornost a co by mohlo potřebovat akci.

 Uživatel bude mít prospěch z grafu, pokud jsou splněny některé z následujících podmínek:

- Pomůže graf uživatelům identifikovat úkoly, na které mohou působit?

- Umožní graf uživatelům předpovídat důsledky potenciálních změn?

- Pomůže graf uživatelům objevit trendy a identifikovat vzorce?

- Umožní graf uživatelům lépe se rozhodovat?

- Pomůže graf odpovědět na konkrétní otázku, kterou mohou mít uživatelé v daném kontextu?

#### <a name="general-rules-for-charts"></a>Obecná pravidla pro grafy

- Jasně označte data. Ilustrace bez vysvětlení jsou jen hezké obrázky.

- Začněte osy na nule, aby se zabránilo zkosení proporce. Délka čáry a velikost pruhu jsou důležitými vizuálními podněty k pochopení vztahů mezi datovými body.

- Vytvářejte grafy, ne infografiku. Infografika je umělecká reprezentace dat a jejich hlavním cílem je vizuální vyprávění. Grafy mohou (a měly by) být vizuálně přitažlivé, ale nechte data mluvit sama za sebe.

- Vyhněte se skeumorfismu, obrazovým pruhovým grafům, kontrastním hašišovým značkám a dalším infografickým prvkům.

- Nepoužívejte 3D efekty jako dekorativní prvek. Používejte je pouze v případě, že skutečně nedílnou součástí schopnosti uživatele pochopit informace.

- Nepoužívejte více čar a výplní, protože více než dvě barvy mohou tento typ grafu ztížit správné čtení a interpretaci.

- Nepoužívejte graf (nebo žádnou ilustraci) jako jediný prostředek k pochopení konceptu nebo interakci s daty. To představuje potíže pro uživatele se zrakovým postižením.

- Nepoužívejte grafy jako bezdůvodné nebo dekorativní prvky na stránce. Jinými slovy, pokud graf nepřidává žádnou hodnotu nebo pomáhá uživatelům problém vyřešit, nepoužívejte jej.

### <a name="chart-types"></a>Typy grafů
 Typy grafů používaných v sadě Visual Studio zahrnují pruhové grafy, spojnicové grafy, upravený výsečový graf známý jako prstencový graf nebo prstencový graf, časové osy, bodové grafy (nazývané také "clusterové grafy") a Ganttovy grafy. Každý typ grafu je užitečný pro sdělování jiného typu informací.

### <a name="other-charting-considerations"></a>Další aspekty vytváření grafů

#### <a name="color"></a>Barvy
 Existuje určitá paleta barev grafů definovaná pro použití v sadě Visual Studio. Paleta je přístupná pro hlavní typy barevné slepoty a barvy mohou být rozlišeny, i když se používají jako velmi úzké plátky barvy. Tyto barvy můžete použít v libovolné kombinaci pro libovolný typ grafu nebo grafu v unovém počítači. Nemusíte používat všech sedm barev, pokud nepotřebujete tolik odlišných barev. Tyto barvy nebyly navrženy pro použití s žádnými prvky popředí, proto neumisťují text ani glyfy nad tyto barvy. Tyto odstíny by měly být pevně zakódovány a vystaveny přizpůsobení uživatele v části **Nástroje > možnosti** (viz [Vystavení barev pro koncové uživatele](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Políčko|Hex|RGB|
|------------|---------|---------|
|![Vzorník 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Vzorník BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Vzorník FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Vzorník 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Vzorník 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Vzorník 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Vzorník B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a>UI na objektu a prohlížení
 Tato část poskytuje kontext pro prohlížení, označované také jako náhled kódu, typ ui na objektu jedinečné Visual Studio.

### <a name="overview"></a>Přehled

- Uživatelské rozhraní na objektu by měl poskytnout uživateli více informací nebo interaktivitu bez odlehčování od jejich hlavní úkol.

- Hlavní vzor pro ui na objekt v sadě Visual Studio se označuje jako "informace v místě pozornosti."

- UI na objekt v sadě Visual Studio je buď včleněné nebo plovoucí a trvalé nebo přechodné.

  - Zobrazení náhledu kódu, typ uj.

  - CodeLens, typ usvého uzla v aplikaci Visual Studio, je plovoucí a přechodný

  Pochopení fungování části kódu nebo hledání podrobností o tomto kódu často vyžaduje, aby vývojář přepnul kontext a přešel na jiný obsah nebo do jiného okna. Tyto posuny kontextu mohou být rušivé, protože uživatelé mohou ztratit zaměření na svůj původní úkol, pokud opustí své hlavní okno. Kromě toho získání, že původní kontext zpět může být obtížné, zejména v případě, že přepínání oken způsobil jejich původní kód, které mají být zakryty jiným i.

  UI na objektu následuje vzor s názvem "informace v místě pozornosti." Tyto zprávy, automaticky otevíraná okna a dialogová okna poskytují uživatelům další relevantní informace, které přidávají vysvětlení nebo interaktivitu, aniž by ztratili zaměření na svůj hlavní úkol. Příklady uživatelského rozhraní na objektu zahrnují automaticky otevíraná okna, která se zobrazí, když uživatel najede ukazatelem myši na ikonu v oznamovací oblasti, červené vlnovky pod chybně napsaným slovem a náhledu zavedeného v sadě Visual Studio 2013.

### <a name="decision-points"></a>Rozhodovací body
 V rámci sady Visual Studio existuje několik způsobů, jak použít tento vzor informací v místě pozornosti. Výběr správného mechanismu a jeho důsledné a předvídatelné zavedení je pro celkovou zkušenost zásadní. V opačném případě mohou být uživatelům prezentovány matoucí nebo nekonzistentní prostředí, které snižuje zaměření na samotný obsah.

#### <a name="relationships-between-master-and-detail-content"></a>Vztahy mezi hlavním a podrobným obsahem
 Informace v bodě pozornosti se používají k zobrazení vztahu mezi obsahem, na který je uživatel zaměřen (hlavní obsah) a dalším souvisejícím obsahem ("podrobný" obsah). V tomto vzoru je podrobný obsah jasně souvisí s obsahem, se kterým uživatel pracuje, a může být zobrazen v blízkosti hlavního obsahu. Doplňující informace nebo informace, které nelze shrnout bez zahlcení hlavního obsahu by měl následovat jiný vzor, například okno nástroje.

- **Obsah** podrobností vždy zobrazte v těsné blízkosti hlavního obsahu.

- **Vždy** se ujistěte, že podrobný obsah stále umožňuje uživateli zůstat zaměřena na hlavní obsah. Často je nejlepším způsobem, jak toho dosáhnout, vykreslit podrobný obsah co nejblíže k hlavnímu obsahu. To lze provést vykreslením obsahu podrobností v rozbalovacím okně vedle hlavního obsahu nebo vykreslením obsahu podrobností pod hlavním obsahem.

- **Nikdy nepoužívejte** informace v místě pozornosti, které uživatele odvádí od hlavního obsahu. Pokud uživatelé potřebují zobrazit podrobný obsah samostatně, vystavit explicitní akce, která umožňuje uživateli k tomu.

#### <a name="design-details"></a>Podrobnosti návrhu
 Jakmile zjistíte, že urozhraní na objektu je správná volba, existují čtyři hlavní aspekty návrhu:

1. **Trvalosti:** očekává se, že obsah bude trvalý nebo přechodný?
   Budou uživatelé chtít, aby informace byly viditelné pro odkazování nebo interakci s nimi? Nebo budou uživatelé chtít rychle podívat na informace a pak pokračovat ve svém hlavním úkolu?

2. **Typ obsahu:** bude obsah informační, žalovatelný nebo navigační?
   Potřebuje uživatel další podrobnosti o hlavním obsahu? Potřebuje uživatel dokončit úkol, který má vliv na hlavní obsah? Nebo musí být uživatel přesměrován na jiný zdroj?

3. **Typ indikátoru:** má indikátor okolí smysl?
   Mohou být informace shrnuty užitečným způsobem a zobrazeny, aniž by došlo k zahlcení hlavního obsahu?

4. **Gesta:** jaká gesta budou použita k vyvolání a zavření ui?
   Jak bude uživatel vychovávat podrobný obsah a odeslat jej pryč? Je hodnota při přidávání gesto, jako je připnutí přepínat mezi přechodné a trvalé stavy?

   Každý z těchto čtyř bodů rozhodnutí bude mít vliv na hlavní součásti uj.

### <a name="on-object-ui-components"></a>Součásti ui na objektu

1. Typ Kontejner (prezentující obsahu)

    - Plovoucí

    - Přiřazený

2. Typ obsahu

    - Informační: data, která mohou být statická nebo dynamická

    - Použitelné: příkazy, které mění hlavní obsah

    - Navigační: odkazy, které přenese uživatele do jiného okna nebo aplikace, například MSDN

3. Gesta

    - Vyvolání

    - Propuštění

    - Připnutí

    - Další interakce

4. Model trvalosti a potvrzení

    - Přechodné

    - Odolné

    - Automaticky

    - Na vyžádání

5. Okolní indikátory (volitelné)

    - Podtržení vlnovkou

    - Ikona inteligentní značky

    - Ostatní ukazatele okolního prostředí

#### <a name="container-content-presenter-type"></a>Typ Kontejner (prezentující obsahu)
 K dispozici jsou dvě hlavní možnosti prezentace obsahu v místě pozornosti:

1. **Vložkový:** Vložkový presenter, například náhled, který byl zaveden v Editoru kódu Visual Studia 2013, vytváří místo pro nový obsah přesunutím existujícího obsahu.

    - **Upřednostňujte** inline prezentující, pokud očekáváte, že uživatelé budou chtít strávit značné množství času odkazováním na obsah, který prezentujete, nebo s ním interagují.

    - **Vyhněte se** vsazeným prezentujícím, pokud očekáváte, že uživatelé budou chtít podívat na informace, které prezentujete, a pak pokračovat ve svém hlavním úkolu s minimálním narušením.

2. **Plovoucí:** Plovoucí presenter je umístěn co nejblíže k vybranému obsahu, ale nemění rozložení existujícího obsahu. Lze použít různé strategie, například zobrazení plovoucího panelu obsahu nad nejbližším dostupným prázdném místem k vybranému symbolu.

    - **Preferujte** plovoucí prezentující, pokud očekáváte, že uživatelé budou chtít podívat na informace, které prezentujete, a pak pokračovat ve svém hlavním úkolu s minimálním narušením.

    - **Vyhněte se** plovoucíprezentující, pokud očekáváte, že uživatelé budou chtít strávit značné množství času odkazováním nebo interakcí s obsahem, který prezentujete.

#### <a name="content-type"></a>Typ obsahu
 Existují tři hlavní typy obsahu, které lze zobrazit uvnitř libovolného kontejneru ui na objektu. Lze zobrazit libovolnou kombinaci těchto typů informací. Jedná se o tři typy:

1. **Informační:** většina kontejnerů ui na objekt u bude zobrazovat nějaký informační obsah. Obsah může představovat informace o současném stavu prostředí nebo může představovat informace o potenciálním budoucím stavu prostředí. Například může být použit k zobrazení vlivu určitého příkazu, jako je například refaktoring, na existující kód.

    - **Vždy** používejte kanonické znázornění zobrazených informací. Kód by měl například vypadat jako kód, doplněný zvýrazněním syntaxe a měl by respektovat jakékoli písmo a další nastavení prostředí, které uživatel nastavil.

    - **Vždy zvažte** podporu všech akcí nad informačním obsahem, který by byl možný, pokud by byly stejné informace prezentovány jako hlavní obsah. Například pokud představujete existující kód uvnitř kontejneru ui na objektu, důrazně zvažte podporu možnosti procházet a upravovat tento kód.

    - **Vždy** zvažte použití jiné barvy pozadí, pokud představujete informační obsah, který představuje potenciální budoucí stav.

2. Žalovatelné: některé kontejnery ui na objekt u poskytují možnost provádět některé akce přes hlavní obsah, jako je například provádění refaktoringu operace.

    - **Vždy** umístěte použitelné příkazy odděleně od informačního obsahu.

    - **Vždy** povolte a zakažte akce, pokud je to vhodné.

    - **Vždy** se podívejte na standardní pokyny pro reprezentaci příkazů uvnitř dialogových oken.

    - **Vždy** udržujte počet akcí, které jsou vystaveny v kontejneru ui na objekt u absolutní minimum. Interakce s uživatelským uživatelským prostředím na objektu by měla být zjednodušená a rychlá. Uživatel by neměl vynaložit energii na správu samotného kontejneru uživatelského rozhraní na objektu.

    - **Vždy zvažte,** jak a kdy bude kontejner umítaného zařízení na objekt uzavřen nebo zamítnut. Jako osvědčený postup by měla každá akce, která uzavírá dialog mezi hlavním a podrobným obsahem, také zavřít kontejner ui na objektu, když je tato akce vyvolána.

3. **Navigační:** některé kontejnery uživatelského rozhraní na objektu obsahují odkazy, které uživatele přenese do jiného okna nebo aplikace, například otevření článku MSDN ve webovém prohlížeči uživatele.

    - **Vždy** předřávejte navigační odkaz s "Otevřít", aby uživatelé nebyli překvapeni tím, že budou navigováni na jiný obsah.

    - **Navigační** odkazy vždy oddělte od žalovatelných odkazů.

#### <a name="ambient-indicators-optional"></a>Okolní indikátory (volitelné)
 Indikátory okolí mohou být jemné, včetně textu zobrazeného v kontrastní barvě od zbytku kódu, nebo zřejmé, včetně tickler symbolů, jako je podtržení vlnovkou a ikony inteligentních značek. Ukazatele okolního prostředí sdělují dostupnost dalších relevantních informací. V ideálním případě poskytují užitečné informace i bez nutnosti, aby s nimi uživatel spolupracoval.

- **Vždy** umístěte indikátor okolí tak, aby nerozptyloval nebo nezahltil uživatele. Pokud není možné umístit indikátor okolního prostředí takovým způsobem, zvažte jiné řešení.

- **Indikátor** okolí vždy umístěte co nejblíže obsahu, se kterým souvisí.

- **Vždy** se pokuste vytvořit indikátor, který shrnuje informace, které zpřístupní. Zvažte poskytnutí počtu dostupných datových položek (například "3 odkazy" namísto jednoduše "Odkazy") nebo zvažte nějaký jiný způsob, jak data shrnout.

  - V případech, kdy data pro indikátor nelze vždy vypočítat a zobrazit, okamžitě zvážit poskytnutí progresivní zpětnou vazbu jako hodnoty jsou počítány. Zvažte například animaci změn, které odrážejí aktualizace dostupných dat, podobně jako se aktualizuje živá dlaždice e-mailu ve Windows Phone s tím, jak se zvyšuje počet nepřečtených e-mailů.

- **Nikdy nepřidávejte** více indikátorů, než může uživatel rozumně přijmout pro daný obsah. Indikátory okolí by měly být užitečné bez nutnosti jakékoli interakce ze strany uživatele. Indikátory ztrácejí své prostředí, pokud vyžadují přetečení a další ovládací prvky řízení, aby je přivedly do zobrazení.

#### <a name="gestures"></a>Gesta
 Klíčovým aspektem, který umožňuje uživateli zachovat zaměření na hlavní obsah, je podpora správných gest k otevření a zavření dalšího podrobného obsahu.

- **Vždy** vyžadovat, aby uživatel provést některé explicitní gesto otevřít další obsah. Mezi běžná otevřená gesta patří:

  - **Najetí na další věc:** popisky nebo neinteraktivní informační obsah

  - **Explicitní příkaz:** inline presenter

  - **Poklepejte na indikátor okolí:** Automaticky otevírané okno CodeLens

- **Vždy** zavřete obsah podrobností vždy, když uživatel stiskne klávesu Esc.

- **Vždy** zvažte kontext ui na objekt. U prezentujících obsahu, kteří umožňují interakci v kontejneru, pečlivě zvažte, zda chcete zobrazit další informace o najetí přes, což může narušit pracovní postup uživatele.

- **Při** najetí na jev, který se jeví jako upravitelný, nikdy nezobrazovat obsah, který se zdá být upravitelný, nebo nevyzývá uživatelem k interakci. Toto chování může zmařit uživatele, pokud se pokusí přesunout kurzor nad obsah podrobností, protože standardní chování pro popisek je okamžitě zavřít, když kurzor již není nad hlavní obsah, který jej vytvořil.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a>Výběrové modely

### <a name="overview"></a>Přehled
 Model výběru je mechanismus používaný k označení a potvrzení operací na jednom nebo více objektech, které jsou předmětem zájmu v rámci uživatelského rozhraní. Toto téma popisuje vzory interakce výběru v editorech dokumentů sady Visual Studio: textové editory, návrhové povrchy a modelovací povrchy.

 Uživatelé musí mít způsob, jak označit Visual Studio, na čem pracují, a Visual Studio musí reagovat předvídatelně se zpětnou vazbou uživatelům o tom, co pracuje. Rozdíly nebo nesprávná komunikace mezi uživatelem a uživatelským rozhraním může vést k tomu, že si uživatel nevšímá akce, což může mít nezamýšlené důsledky. Často chyba zůstane bez povšimnutí, dokud uživatel zjistí, že něco chybí nebo se změnilo. Modely výběru jsou proto jedním z nejkritičtějších částí návrhu uživatelského rozhraní. Přestože modely výběru v sadě Visual Studio jsou konzistentní s Windows, existují mírné odchylky.

 V sadě Visual Studio, stejně jako v systému Windows, modely výběru se liší v závislosti na kontextu, ve kterém dojde k interakci. Výběry mohou probíhat ve čtyřech typech objektů:

- Text

- Grafické objekty

- Seznamy a stromy

- Mřížky

  V rámci těchto objektů existují tři typy výběrů:

- Souvislé

- Nesouvislé

- Region (Oblast)

#### <a name="scope"></a>Rozsah
 Nejdůležitější součástí výběru je zajistit, aby uživatel věděl, ve kterém okně pracuje (aktivace) a kde je umístěnfostřicát (výběr). Visual Studio rozšiřuje funkce správy oken v systému Windows, ale schéma aktivace je stejné: interakce s oknem přináší fokus do okna. Visual Studio má dva indikátory pro aktivaci: jeden pro okna dokumentu a jeden pro okna nástrojů.

 U oken dokumentu je aktivní okno označeno kartě okna dokumentu, která přichází dopředu a mění barvu pozadí:

 ![Aktivní výběr karet v Sadě Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Aktivní výběr karty**

 U oken nástrojů je aktivní okno označeno změnou barvy oblasti záhlaví okna nástroje:

 ![Výběr okna aktivního nástroje v sadě Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Okno aktivního nástroje zobrazující primární výběr uzlu**

 ![Výběr okna neaktivního nástroje v sadě Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Okno nástroje Neaktivní, zobrazující latentní výběr uzlu**

 Jakmile je okno aktivní, jeho zaměření je indikováno podle modelů výběru uvedených v této části pokynů.

#### <a name="context"></a>Kontext
 Visual Studio byl navržen tak, aby zachovat silný koncept kontextu, sledování, kde uživatel pracuje. Je aktivní pouze jedno okno, ať už se jedná o nástroj nebo okno dokumentu. Nejvyšší okno dokumentu však vždy zachová latentní výběr. Přestože fokus může být v okně nástroje, okno dokumentu, které bylo naposledy aktivní, zobrazí výběr, a to i v neaktivním stavu. To se provádí zachovat kontext uživatele v dokumentu, který upravovali, což ukazuje, že Visual Studio si zachovalo svůj stav, aby se mohli bez problémů vrátit a přesunout mezi okny nástrojů a okny dokumentů.

### <a name="text-selection"></a>Výběr textu
 Editory sady Visual Studio, které jsou striktně textové, například předdefinovaný textový editor, používají stejný model výběru textu a vzhled popsaný na stránce [Myš a ukazatele](/windows/desktop/uxguide/inter-mouse) pokynů pro interakci s uživatelským prostředím systému Windows v msdn. Vstupní fokus v textovém editoru je označen svislým pruhem nazývaným kurzor. Textový kurzor je jeden pixel tlustý a barevný jako inverzní k tomu, co se za ním objeví. Bliká podle rychlosti nastavené nastavením **rychlosti blikání kurzoru** na kartě **Rychlost** na ovládacím **panelu Klávesnice.**

#### <a name="contiguous-and-disjoint-selection"></a>Souvislý a nesouvislý výběr
 Výběr v textovém editoru je pouze souvislý. Nesouvislé výběry textu nejsou povoleny, ale měly by být řešeny v editorech grafických objektů. Když je ukazatel myši uživatele nad textovou oblastí, kurzor se změní na I-nosník. Jediným kliknutím umístíte textový kurzor do textového editoru na umístění kliknutí. Podržením tlačítka myši dolů se spustí zvýraznění výběru a uvolněním tlačítka myši se zvýraznění výběru ukončí.

#### <a name="region-selection-box-selection"></a>Výběr oblasti (výběr rámečku)
 Visual Studio podporuje výběry oblastí v textovém editoru a to se nazývá výběr pole. Výběr pole umožňuje uživateli vybrat oblast textu, která nesleduje běžný textový proud. Stejně jako u standardního výběru textu musí být výběr souvislý. Výběr pole se zahájí podržením klávesy Alt při tažení myší. Výběr rámečku lze také zahájit podržením kláves Alt a Shift při použití kláves se šipkami k označení oblasti výběru. Výběr rámečku použije normální zvýraznění výběru a zobrazí kurzor kurzoru kurzoru blikajícího na konci oblasti výběru.

 ![Výběr&#41; pole regionální &#40;v sadě Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Výběr oblasti (pole) v sadě Visual Studio**

#### <a name="text-selection-appearance"></a>Vzhled výběru textu
 Barvy použité pro aktivní a neaktivní výběr v editoru lze přizpůsobit. Chcete-li přizpůsobit vizuální vzhled editoru, může uživatel přejít na **nástroje > možnosti**a poté se podívat do části **Prostředí > Písma a barvy > textový editor**.

### <a name="graphical-selection"></a>Grafický výběr

#### <a name="interaction"></a>Interakce
 Výběr grafického objektu může být složitý a závisí na řadě faktorů:

- **Editor je primární model výběru.** Editory, které obsahují grafické objekty, lze také použít k úpravám textu nebo mřížky. Editor může být například textový editor, který také podporuje umístění grafických objektů, jako je například návrhář Visual Studio XAML. Podpora více typů objektů může ovlivnit způsob, jakým uživatel vybírá skupiny tvořené různými typy objektů.

- **Podpora pro primární a sekundární stavy výběru.** Editor může poskytovat primární a sekundární stavy výběru tak, aby objekty mohly být upravovány společně, vzájemně zarovnány, měnily velikost dohromady a tak dále.

- **Podpora úprav na místě.** Editoři mohou také povolit úpravy obsahu svých grafických objektů. Obrazec obdélníku může také obsahovat text uvnitř, který může uživatel změnit. Kromě toho může být tento text vycentrován nebo zarovnaný do bloku. Úpravy na místě zahrnují podrobnější úroveň interakce s uživatelem, a proto vyžadují vhodnou sadu vizuálních podnětů pro prezentaci informací o stavu uživateli.

#### <a name="mouse-interaction"></a>Interakce s myší

|Vstup|Výsledek|
|-----------|------------|
|Klepnutí na nevybraný objekt|Vybere objekt a zobrazí přerušovanou čáru a úchyty výběru, pokud lze objekt uznat.|
|Klepněte na vybraný objekt.|Aktivuje úpravy na místě, pokud je objekt podporuje. Klepnutím mimo objekt se deaktivuje režim úprav na místě.|
|Poklepání na objekt|Otevře kód za objektem pro úpravy a může vložit výchozí obslužnou rutinu události, pokud je to vhodné.|
|Přejděte na objekt|Změní ukazatel na kurzor přesunu. Vzhled objektu, například jeho světelnost nebo barva, se může změnit.|
|Přejděte na úchyt pro výběr.|Změní ukazatel na kurzor změny velikosti. U objektů, které podporují otočení, mohou některé úchyty výběru změnit ukazatel na otočení kurzoru, protože ukazatel je umístěn odlišně (například přesunutdále) vzhledem k úchytu výběru.|
|Přetáhněte|I když objekt není dříve vybraný, změní ukazatel na kurzor pro přesun a přesune objekt.|
|Editor ztrácí zaměření|Deaktivuje režim úprav na místě, i když objekt zachová obsah a vzhled, který měl během poslední operace/stavu výběru.|
|Výběr objektu|Označeno ohraničením, tečkovanou čárou nebo jiným vizuálně odlišným zpracováním, které zvýrazňuje hranici objektu.|
|Změna velikosti vybraného objektu|Označeno úchyty výběru.<br /><br /> Objekt s nastavitelnou velikost má osm úchytů představujících každý směr, ve kterém lze jeho velikost přizpůsobit. Méně úchytů lze použít, pokud lze velikost objektu pouze v určitých směrech. Pokud uživatel velikosti objektu dolů, kde osm popisovače by nebylo interaktivní, pak čtyři popisovače mohou být použity. Velikosti popisovače by měly být vázány na okraj okna a okraj metriky s **GetSystemMetrics** API funkce velikost v poměru k rozlišení zobrazení.<br /><br /> ![Změna velikosti úchytů](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Otočení vybraného objektu|![Otočení úchytů](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interakce s klávesnicí

|Vstup|Výsledek|
|-----------|------------|
|Karta|Přesune indikátor fokusu mezi logické pořadí objektů v editoru. To může být zleva doprava nebo shora dolů v závislosti na Hodnotě vlastnosti **TabIndex** (nebo ekvivalentní), pořadí vytváření objektů a celkový účel editoru. Shift+Tab obrátí směr indikátoru zaostření.|
|Mezerník|Aktivuje režim posouvání, když je stisknutí klávesy zachováno. K posouvání polohy výřezu je nutný další vstup myši.|
|Ctrl + mezerník|Aktivuje režim přiblížení, když je stisknutí klávesy zachováno. Další vstup myši je nutné zvýšit a snížit faktor zvětšení.|
|Ctrl+Alt+znaménko mínus|Sníží faktor zvětšení o jednu úroveň.|
|Ctrl+Alt+Znaménko plus|Zvýší faktor zvětšení o jednu úroveň.|
|Shift OR Ctrl|Přidá objekt do skupiny výběru. Ctrl také umožňuje odebrat objekty jednotlivě ze skupiny výběru.|
|Enter|Provede výchozí příkaz pro objekt (obvykle Otevřít nebo Upravit).|
|F2|Aktivuje úpravy objektu na místě.|
|Šipkové klávesy|Přesune vybraný objekt (objekty) ve směru stisknuté klávesy se šipkou v malých krocích (například po 1 obrazovém bodu)|
|Ctrl+šipky|Přesune vybraný objekt (objekty) ve směru stisknuté klávesy se šipkou ve větších krocích (například 10 pixelů najednou).|
|Shift+šipky|Změní velikost vybraného objektu (objektů) v příslušném směru v malých krocích (například po 1 obrazovém bodu)|
|Ctrl+Shift+šipky|Změní velikost vybraného objektu (objektů) v příslušném směru ve větších krocích (například 10 pixelů najednou).|

 Když uživatelé upravují ovládací prvky na místě, může být vhodné, aby objekty automaticky měšet velikost s uživatelským vstupem. Například pokud uživatel upraví ovládací prvek popisek, pak popisek by měl zvětšit zobrazit text, který uživatel právě zadali. Pokud tak neučinila, uživatel musí změnit velikost ovládacího prvku ručně po úpravě textu. Pokud má uživatel mnoho ovládacích prvků, stane se z toho úkol typu rote a neproduktivní.

#### <a name="graphical-containers"></a>Grafické kontejnery
 V některých případech grafické editory poskytují kontejnery pro jiné grafické objekty, jako je například ovládací prvek Windows Forms Panel nebo ovládací prvek Rozložení mřížky v návrháři HTML. Pokud editor poskytuje kontejnery pro jiné grafické objekty, měl by být použit následující model výběru pouze pro kontejner (objekty v kontejneru postupujte podle výše popsaného standardního modelu):

|Vstup|Výsledek|
|-----------|------------|
|Jedním kliknutím na kontejner|Vybere objekt kontejneru bez přímého výběru některého z obsažených objektů. Kontejner může být přesunut a/nebo může být velikost rozdělena standardním vstupem myši a klávesnice (jak je popsáno výše). Obsažené objekty jsou přesunuty vzhledem ke kontejneru, ale obsažené objekty nejsou velikosti, pokud jsou také přímo vybrané.|
|Najeďte nad hraniční oblastí kontejneru|Otočí myš na kurzor pohybu, což znamená, že kontejner lze přesunout.|
|Přetažení hraniční oblasti kontejneru|Změní myš na kurzor pohybu a přesune kontejner (a obsažené objekty uvnitř). Kontejner nelze přesunout, aniž by byl nejprve vybrán jediným kliknutím.|
|Jedním kliknutím na objekt v kontejneru|Odznačí kontejner (je-li vybrán) a vybere pouze klepnutnací objekt.|
|Shift+klepněte na tlačítko OR Ctrl+klikněte na obsažený objekt nebo kontejner|Přidá klepnutnaný objekt do existující skupiny výběru nebo výběru. Pokud je klepnut na objekt již členem skupiny výběru, bude odebrán ze skupiny výběru.|

 Obsažené objekty by měly přilnout k základnímu modelu výběru, jak je popsáno v předchozí části. Z testování použitelnosti návrháře Windows Forms uživatelé očekávali bezproblémový přístup k obsaženým objektům bez zásahů (vynucených objektem kontejnmentu).

#### <a name="disjoint-and-region-selections"></a>Nesouvislé a regionální výběry
 Grafické editory objektů by měly podporovat nesouvislé výběry. Upozorňujeme, že tato grafika nezobrazuje vzhled ovládacího prvku pro sady Visual Studio. Podrobné vizuální specifikace naleznete [v tématu Grafický vzhled výběru objektů.](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance)

 ![Nesouvislé a regionální voliče](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Nesouvislý výběr**

 Grafické editory by také měly poskytovat výběry oblastí s indikátorem výběru typu výběru. Pokud grafický editor podporuje jiné typy objektů (například text), nemusí být výběry oblastí možné v závislosti na omezeních těchto jiných typů objektů.

 ![Výběr výběru výběru](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Výběr výběru výběru**

#### <a name="primary-and-secondary-selections"></a>Primární a sekundární výběr
 Některé editory grafických objektů umožňují uživateli upravovat nebo zarovnávat objekty ve skupinách. V tomto případě je třeba zavést koncepci primárního a sekundárního výběru. Primární výběr je objekt, na který všechny ostatní objekty reagují pro skupinové operace. Objekt, který uživatel vybere jako první, se stane primárním ovládacím prvkem a následné výběry se stanou sekundárními výběry. Primární výběr má odlišné vizuální ošetření od sekundárního výběru (výběrů), který označuje, který objekt je primární:

 ![Primární a sekundární výběr](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Primární výběr se dvěma sekundárními výběry**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a>Grafický vzhled výběru objektů
 Úchyty výběru jsou čtverce nakreslené v obdélníkovém poli kolem ohraničovacího rámečku objektu. Níže uvedená tabulka ukazuje příklady různých stavů, které může mít grafický objekt s úchytem, velikostí a vzhledem úprav na místě. Velikost popisovačů by měla být vázána na metriky ohraničení okna a okraje pomocí rozhraní **API GetSystemMetrics.**

| Stav | Vzhled | Vizuální detaily |
|-------------------------|---------------| - |
| **Nevybrané** | Výchozí | ![Výchozí stav tlačítka](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Primární výběr** | Resizable | ![Primární výběr s úchyty pro měnit velikost](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Primární výběr** | Nelze si ji zmocnit | ![Primární výběr bez úchytů pro měnit velikost](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Primární výběr** | Uzamčeno | ![Primární výběr je uzamčen.](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Sekundární výběr** | Resizable | ![Sekundární výběr s úchyty pro měnit velikost](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Sekundární výběr** | Nelze si ji zmocnit | ![Sekundární výběr bez úchytů pro měnit velikost](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Sekundární výběr** | Uzamčeno | ![Sekundární výběr uzamčen](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **Aktivní uj.u.** | Výchozí | ![Aktivní stav uI](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Zobrazit modely výběru

#### <a name="tree-view"></a>Stromové zobrazení
 Výběr ve stromovém zobrazení se zobrazí jednoduchým zvýrazněním. Pokud uživatel klepne na název uzlu nebo ikonu uzlu, uzel se stane vybraným. Trojúhelníkové glyfy nalevo od uzlu rozbalí nebo zúží ovládací prvek stromu, ale nemají vliv na výběr uživatele, s jednou výjimkou: při sbalení nadřazeného uzlu při výběru na podřízeném uzlu tohoto uzlu se výběr přesune na nadřazený.

 ![Typické stromové zobrazení v sadě Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Typické stromové zobrazení v sadě Visual Studio**

 Stromová zobrazení mohou podporovat souvislé a nesouvislé výběry, a to i navíce úrovní ve stromu. Souvislé nebo nesouvislé více násobné výběry musí být provedeny na viditelné uzly stromu. Pokud je uzel sbalen, nesouvislý výběr je ztracen a uzel, který byl sbalen, získá výběr. Tímto způsobem může uživatel zobrazit uzly, které budou ovlivněny operací. Při sbalení uzlů, stane se nejasné, které uzly mohou být ovlivněny.

 Pokud je vybrán nadřazený uzel, operace by se měla vztahovat na nadřazený, i když mohou existovat případy, kdy má smysl, aby se operace vztahovala na nadřazený a všechny jeho podřízené položky. V takovém případě zadejte další uživatelské rozhraní během operace, jako je například zaškrtávací políčko nebo potvrzovací dialogové okno, aby se možnost "použít pro všechny podřízené položky" explicitní pro uživatele.

##### <a name="renaming"></a>Přejmenování
 Pokud uzly ve stromu podporují přejmenování, přejmenování by mělo být provedeno na místě. Operace na místě by měla být standardem pro všechny ovládací prvky stromu v sadě Visual Studio. Zadejte příkaz přejmenování, který okamžitě aktivuje režim úprav na místě, přičemž výběr textu bude zahrnovat celý název uzlu a je připraven přijmout vstup uživatele. Pokud uzel představuje soubor, název souboru by měl obsahovat příponu. Zvýraznění výběru by mělo obsahovat pouze tělo názvu souboru a nikoli příponu.

|Vstup|Výsledek|
|-----------|------------|
|Enter – klávesa|Potvrdí operaci přejmenování.|
|Esc|Zruší operaci přejmenování.|
|Kliknutí mimo oblast úprav na místě|Potvrdí operaci přejmenování.|
|Zpět|Poskytněte snadné zrušení operace přejmenování|

#### <a name="selection-within-lists-and-grid-controls"></a>Výběr v rámci seznamů a ovládacích prvků mřížky
 Klíčovým konceptem ve výběru seznamu je, že je založen na řádcích, což znamená, že při výběru je jako jednotka vybrán celý řádek. Naproti tomu mřížky mohou povolit výběr určitých buněk, aniž by to ovlivnilo jakýkoli jiný aspekt řádku. Mřížky mohou také obsahovat hierarchii vnořených řádků (například v treegridu), které umožňují výběr a zrušení zaškrtnutí celých větví hierarchie interakcí s nadřazenými řádky. Výběr v seznamech se zobrazuje jednoduchou barvou zvýraznění na celém řádku dat. Fokus je zobrazen tečkovaným ohraničením jednoho obrazového bodu kolem aktuálního upravitelného řádku nebo buňky (řádek, pokud jsou všechny buňky jen pro čtení).

> [!NOTE]
> **Zaměření** a **výběr** jsou různé pojmy. *Fokus* je označení, který prvek rozhraní je zaměřen a přijímat vstup není explicitně zaměřena na jiný objekt, zatímco *výběr* odkazuje na stav zahrnutí objektu do sady objektů, na kterých mohou probíhat následné operace.

 Výběry v seznamech mohou být souvislé, nesouvislé nebo oblasti. Pokud je povoleno více výběrů, souvislý a nesouvislý výběr by měl být vždy podporován, zatímco podpora výběrů oblastí (pole) je volitelná. Výběry oblastí jsou iniciovány přetažením v prázdném prostoru těla seznamu.

| Objekt | Výběr |
|--------|------------|
| Seznam | Souvislé |
| Seznam | Nesouvislé |
| Seznam | Region (Oblast) |

 Jednou kliknutím na seznam vyberete řádek, ve kterém došlo ke kliknutí. Pokud uživatel klikne do buňky seznamu, která podporuje úpravy na místě, je buňka okamžitě aktivována pro úpravy na místě. V opačném případě je okamžitě vybrán celý řádek a zobrazí se zvýraznění.

 Přetažením v těle seznamu se provádí jedna ze tří věcí:

- Zahájí výběr oblasti, pokud jej seznam podporuje a myš dolů je v prázdném místě.

- Zahájí operaci přetažení, pokud buňka seznamu nebo řádek podporuje zdroj přetažení.

- Vybere aktuální řádek.

##### <a name="in-place-editing"></a>Úpravy na místě
 Pokud je úpravy na místě povoleny, existují dva základní modely: jednoduchý ovládací prvek úprav a výběr vlastností. Díky jednoduchému ovládacímu prvku pro úpravy je obsah zvýrazněn a připraven pro vstup uživatele, jakmile je aktivována úprava na místě. Pokud je implementován výběr vlastností, tlačítko, které vyvolá výběr vlastností, se zobrazí, jakmile je aktivován režim úprav na místě a aktuální výběr není zvýrazněn. Tlačítko výběru by mělo být v buňce zarovnané doprava. Příklady úprav na místě najdete v tématu **Okno vlastností** a **Seznam úkolů** v sadě Visual Studio.

##### <a name="keyboard-support"></a>Podpora klávesnice
 Podpora výběru pomocí klávesnice v seznamech a mřížkách se řídí standardními konvencemi systému Windows:

- Klávesy se šipkami procházet seznam, výběrem každý řádek / buňka, jak je přesunuta fokus.

- Shift + šipka provádí souvislý výběr ve směru kláves se šipkami.

- Ctrl + šipka následovaná mezerníkem přepíná mezi přidáním a odebráním položek seznamu z výběru a vytvořením nesouvislého výběru.

- U mříží, které obsahují vnořené hierarchie, rozbalí klávesa Šipka vpravo nadřazený řádek a klávesa Šipka vlevo jeden sbalí.

- Klávesa Tab přesune fokus mezi buňkami v aktuálním řádku, pokud jsou buňky upravitelné.

- Klávesa Enter provede výchozí příkaz pro položku v seznamu (často **Otevřít).**

- Klávesa F2 aktivuje úpravy na místě pro aktuálně vybranou buňku.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a>Nastavení trvalosti a ukládání

### <a name="overview"></a>Přehled
 Přestože každá softwarová součást v sadě Visual Studio je obvykle zodpovědný za svůj vlastní stav a trvalost, Visual Studio automaticky uloží nastavení v některých případech, například s velikosti okna a pozice. Níže uvedená tabulka obsahuje kombinaci automaticky uložených nastavení a nastavení, která vyžadují explicitní akci uživatele nebo naprogramova.

|Objekt|Co ušetřit|Kdy uložit|Kde ušetřit|
|------------|------------------|------------------|-------------------|
|Volitelný objekt (například řádek kódu)|Zarážka na řádku kódu<br /><br /> Uživatelský zástupce přidružený k řádku kódu|Při uložení projektu|Soubor **uživatelských možností (.suo)** pro projekt|
|Dialog|Umístění dialogového okna, pokud byl přesunut<br /><br /> Zobrazení, které uživatel naposledy použil v dialogovém okně|Když se dialog zavře<br /><br /> Po ukončení relace sady Visual Studio|V paměti<br /><br /> Registr v **HKEY_Current_User**|
|Okno|Velikost a umístění okna|Když se okno zavře<br /><br /> Při změně režimu sady Visual Studio<br /><br /> Po ukončení relace sady Visual Studio|Soubor **uživatelských možností (.suo)** pro projekt<br /><br /> Soubor vlastních možností pro nastavení okna|
|Dokument|Aktuální výběr v dokumentu<br /><br /> Zobrazení dokumentu<br /><br /> Posledních několik míst, která uživatel navštívil|Při uložení dokumentu|Soubor **uživatelských možností (.suo)** pro projekt|
|Project|Odkazy na soubory<br /><br /> Odkazy na adresáře na disku<br /><br /> Odkazy na jiný software<br /><br /> Komponenty<br /><br /> Informace o stavu samotného projektu|Při uložení projektu|Soubor projektu|
|Řešení|Odkazy na projekty<br /><br /> Odkazy na soubory|Při uložení projektu nebo řešení|Soubor **řešení (.sln)**|
|Nastavení v **možnostech > nástrojů**|Vlastní nastavení klávesnice<br /><br /> Vlastní nastavení panelu nástrojů<br /><br /> Barevná schémata|Když se zavře dialogové okno **Možnosti > nástrojů**<br /><br /> Po ukončení relace sady Visual Studio|Registr v **HKEY_Current_User**|

 Co uživatel dělá, a když to dělají, určuje, zda je nastavení uloženo v paměti (během relace), uloženo na disk (napříč relacemi jako nastavení registru), jako součást samotného souboru projektu nebo řešení, jako součást **souboru možností řešení (.suo)** nebo jako vlastní soubor nastavení, o který ví pouze tato softwarová součást. Výše uvedená tabulka ukazuje několik událostí, při kterých lze uložit nastavení. Existují však i jiné časy, ve kterých můžete chtít uložit stav:

- Když uživatel změní umístění v dialogovém okně nebo okně

- Když uživatel přenese fokus do jiného okna

- Když uživatel přepne z režimu návrhu do režimu ladění

- Když se uživatel odhlásí ze svého účtu

- Když počítač přejde do režimu spánku nebo se vypne

- Když se má počítač/pevný disk přeformátovat a znovu nastavit

### <a name="window-configurations"></a>Konfigurace oken
 Konfigurace okna je základní prezentací vývojového prostředí - jedná se o schéma skládající se ze seznamu přítomných oken nástrojů a způsobu jejich uspořádání. Pro windows spravované IDE (IDE windows), informace o rozložení je zachována na uživatele, takže když uživatel spustí rozhraní IDE, rozložení okna se zobrazí stejně jako při posledním ukončení sady Visual Studio. Stav a umístění oken IDE je zachována v souboru vlastních možností ve formátu XML. Okna nástrojů, která jsou vytvořena balíčky načtenými do rozhraní IDE, zachovávají informace o stavu v registru a mohou nebo nemusí být na uživatele.

#### <a name="profile-specific-layouts"></a>Rozložení specifická pro profil
 Každý profil obsahuje rozložení okna nástroje, uspořádané způsobem známým konkrétním vývojářským osobám (vývojáři Visual C++ očekávají, že uvidí **Průzkumníka řešení** na levé straně rozhraní IDE, zatímco vývojáři jazyka C# očekávají, že uvidí **Průzkumníka řešení** vpravo). Rozložení oken specifické pro profil jsou načteny poté, co uživatel vybere profil při spuštění. Autor balíčku by měl určit rozložení okna nejvhodnější pro jejich zákazníka zkušenosti s vědomím, že změny, které uživatel provede v konfiguraci okna pak bude zachována.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a>Dotykové ovládání
 Uživatelé stále více používají vývojové produkty společnosti Microsoft na dotykových zařízeních. Existují však překážky, které ztěžují používání vývojových nástrojů na dotykových zařízeních. Uživatelé budou očekávat, že naše produkty poskytnou spolehlivý a přesný dotykový zážitek. Záměrem těchto pokynů je informovat rozhodnutí o tom, které možnosti dotykového ovládání začlenit a podporovat konzistentní dotykové ovládání v rámci sady Visual Studio a souvisejících produktů.

### <a name="levels-of-experience"></a>Úroveň zkušeností
 Následující úrovně zkušeností mají sloužit jako vodítko, které týmům pomůže rozhodnout, které dotykové funkce nabídnout na základě požadované úrovně investičního zájmu v kontaktu.

- **Základní zkušenost** je pro týmy, které chtějí poskytovat dotykové funkce, takže v jejich práci nejsou žádné slepé uličky.

- **Optimalizované prostředí** je pro týmy, které chtějí poskytnout nejběžnější dotykové funkce (například ty, které jsou obvykle k dispozici v aplikacích internetového prohlížeče).

- **Zvýšené prostředí** je pro týmy, které chtějí přidat funkce, jako jsou gesta nebo jiné volitelné funkce, které mohou jejich aplikace touch-first friendly.

||Základní zkušenosti|Optimalizované prostředí|Zvýšené zkušenosti|
|-|----------------------|--------------------------|-------------------------|
|Umožňuje uživatelům ...|Oprava kódu a odečtu na úrovni řešení/projektu bez slepicích uliček|Provádění úloh údržby, faktorů a navigace|Pracujte v konzistentním, intuitivním a plynulém prostředí s jistotou|
|Editor|Posouvání a výběr dotykového ovládání<br /><br /> Posuvník touch pro skok a stiskněte +táhnout|Přiblížení prstů<br /><br /> Rychlý posun<br /><br /> Výběr<br /><br /> Snadné použití kontextové nabídky||
|Horní okna nástrojů|Posouvání seznamu<br /><br /> Výběr položky<br /><br /> Posuvník touch pro skok a stiskněte +táhnout|Snadné posouvání a výběr položek||
|Okenní okna||Změnit velikost okna<br /><br /> Rychlý přístup||
|Dobře dokumentujte||Snadná navigace mezi otevřenými soubory||
|Gesta||Zajistěte, aby běžná gesta fungovala v rámci ide|Akce založené na gestech<br /><br /> Podpora přetahování a návrhářů|
|Další aspekty|||Vlastní klávesnice na obrazovce|

#### <a name="gestures"></a>Gesta
 Gesta poskytují uživatelům zástupce příkazů, které by jinak mohly vyžadovat složitější interakci. Podívejte se na pokyny systému Windows pro [běžná dotyková gesta pro desktopové aplikace](/windows/desktop/wintouch/windows-touch-gestures-overview)a postupujte podle těchto pokynů pro většinu gest, včetně jednoduchých gest, jako je posouvání a zvětšování.
