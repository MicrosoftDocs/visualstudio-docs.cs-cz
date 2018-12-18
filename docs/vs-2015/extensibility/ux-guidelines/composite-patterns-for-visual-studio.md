---
title: Složené vzory
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51474047d5cb2b57a3d45df4009dccd3335ce759
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061192"
---
# <a name="composite-patterns-for-visual-studio"></a>Složené vzory pro sadu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Složené vzory kombinovat elementy interakce a návrhu v různých konfiguracích. Některé z vašich nejdůležitějších složené vzory v sadě Visual Studio s ohledem na konzistenci patří:

-   [Vizualizace dat](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

-   [Na objekt uživatelského rozhraní a prohlížení](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

-   [Výběr modely](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

-   [Trvalost a ukládají se nastavení](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

-   [Dotykové ovládání](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

##  <a name="BKMK_DataVisualization"></a> Vizualizace dat

### <a name="overview"></a>Přehled
 Grafy jsou vizuální způsob, jak agregovat a vizualizace dat, aby bylo možné vylepšit rozhodování. Mohou pomoci uživatelům s velké množství dat, ale trochu tj. podívejte se, co si zaslouží pozornost a co může být nutné akci.

 Uživatel bude přínosem z grafu, pokud je splněna některá z následujících podmínek:

-   Graf pomůže uživatelům určit úlohy, které se dají dále rozvíjet?

-   Graf vám umožní uživatelům prognózy důsledků potenciálních změn?

-   Graf uživatelům pomůže odhalovat trendy a identifikovat vzory?

-   Graf uživatelům umožní Rozhodujte se lépe?

-   Graf pomůže odpovědět konkrétní dotaz, který uživatelé mohou mít v daném kontextu?

#### <a name="general-rules-for-charts"></a>Obecná pravidla pro grafy

-   Jasně označit data. Ilustrace bez vysvětlení jsou právě to je dobré obrázky.

-   Začněte osy na nule, aby se zabránilo zkosení rozměry. Velikost řádku délku a panelu jsou důležité vizuální upozornění pro pochopení vztahů mezi datových bodů.

-   Vytváření grafů, ne infografika. Infografika je umělecký reprezentace dat a jejich hlavním cílem je vizuální vyprávění příběhu. Grafy můžete (a měli byste) být vizuálně přitažlivé ale nechat data hovořit sama za sebe.

-   Vyhněte se skeumorphism, obrazové pruhové grafy, hashmarks kontrast a další infografika dnešní.

-   Nepoužívejte 3D efekty jako dekorativní elementu. Použijte je jenom v případě jejich skutečně nedílnou součástí uživateli možnost pochopili informace.

-   Vyhněte se použití více čar a výplní, protože více než dvěma barvami může ztěžovat tento typ grafu a pochopitelnější správně.

-   Nepoužívejte graf (nebo libovolné obrázku) jako jediným prostředkem vysvětlení konceptu nebo interakci s daty. To představuje potíže uživatelům se zrakovým.

-   Nepoužívejte grafy jako dobrovolný nebo dekorativní elementů na stránce. Jinými slovy Pokud grafu nelze přidat že všechny hodnoty nebo nápovědy uživatele vyřešit problém, nepoužívejte ho.

### <a name="chart-types"></a>Typy grafů
 Typy grafů použít v sadě Visual Studio zahrnují pruhové grafy, spojnicové grafy, upravenou výsečový graf označované jako kanál grafu nebo "prstencový graf," časové osy, bodové grafy (také nazývané "clusteru grafy") a Ganttova diagramu. Každý typ grafu je užitečný pro komunikaci jiný druh informací.

### <a name="other-charting-considerations"></a>Další důležité informace o vytváření grafů

#### <a name="color"></a>Barva
 Neexistuje konkrétní paletu barev, které jsou definovány pro použití v sadě Visual Studio na graf. Na paletě je přístupný pro hlavní typy barvoslepostí nerozeznávající a barvy může lišit, i když se použije jako velmi krátkého řezy barvy. Tyto barvy v libovolnou kombinaci můžete použít pro jakýkoli typ grafu v uživatelském rozhraní. Není nutné používat všechny sedm barvy, pokud nepotřebujete daný počet různých barev. Tyto barvy obvykle nebyly navrženy pro použití s elementy popředí, takže Neumísťujte text nebo glyfy nad tyto barvy. Tyto bubliny by měla být pevně zakódované a vystavit do přizpůsobení na uživatele v rámci **nástroje > Možnosti** (naleznete v tématu [vystavení barvy pro koncové uživatele](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Vzorníku|Hex|RGB|
|------------|---------|---------|
|![Vzorník 71B252](../../extensibility/ux-guidelines/media/0711-71b252.png "0711_71B252")|#71B252|113,178,82|
|![Vzorník BF3F00](../../extensibility/ux-guidelines/media/0711-bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Vzorník FCB714](../../extensibility/ux-guidelines/media/0711-fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Vzorník 903F8B](../../extensibility/ux-guidelines/media/0711-903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Vzorník 117AD1](../../extensibility/ux-guidelines/media/0711-117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Vzorník 79D7F2](../../extensibility/ux-guidelines/media/0711-79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Vzorník B5B5B5](../../extensibility/ux-guidelines/media/0711-b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

##  <a name="BKMK_OnObjectUI"></a> Na objekt uživatelského rozhraní a prohlížení
 Tato část poskytuje kontext k prohlížení, označované také jako zobrazení náhledu kódu, typ objektu uživatelského rozhraní jedinečné pro Visual Studio.

### <a name="overview"></a>Přehled

- Uživatelského rozhraní na objekt by měl uživateli přidělit další informace nebo interaktivitu bez zasahoval svého hlavního úkolu.

- Hlavní vzor pro objektů uživatelského rozhraní v sadě Visual Studio se označuje jako "informace o místě pozornost."

- Na objekt uživatelského rozhraní v sadě Visual Studio je buď vložené nebo s plovoucí desetinnou čárkou a durable nebo přechodná.

  -   Zobrazení náhledu kódu, typ objektu uživatelského rozhraní v sadě Visual Studio je vložení a trvale.

  -   CodeLens, typ objektu uživatelského rozhraní v sadě Visual Studio, je s plovoucí desetinnou čárkou a přechodné

  Pochopení, jak kód funguje, nebo vyhledání podrobností o kódu, často vyžaduje vývojář, abyste mohli přepínat kontext a přejít na další obsah nebo jiné okno. Tyto staffhubu kontextu může být rušivé, protože uživatelé ztratit zaměřit se na jejich původní úkolu, pokud nechají jejich hlavní okno. Získávání kromě toho, že původní zpět kontext může být obtížné, zejména v případě, že přepínání mezi okny způsobila jejich původního kódu, chcete-li být skryty pomocí jiných uživatelského rozhraní.

  Uživatelského rozhraní na objekt má následující formát názvem "informace o místě pozornost." Tyto zprávy, automaticky otevíraná okna a dialogová okna uživatelům udělit další relevantní informace, které přidá další informace nebo interaktivitu bez ztráty zaměřit se na svého hlavního úkolu. Příkladem objektů uživatelského rozhraní jsou automaticky otevíraná okna, které se zobrazí, když uživatel najede myší ikonu v oznamovací oblasti, červená vlnovka pod chybně napsaná slova a zobrazení náhledu zavedena v sadě Visual Studio 2013 ukazatele.

### <a name="decision-points"></a>Rozhodovací body
 V sadě Visual Studio existuje několik způsobů, jak používat tento vzor informace o místě pozornost. Výběr správné mechanismus a implementace konzistentní vzhledem k aplikacím a předvídatelným způsobem je nezbytné pro celkové prostředí. V opačném případě uživatelé můžou se vám matoucí nebo nekonzistentní prostředí, který odvádějí zaměření samotného obsahu.

#### <a name="relationships-between-master-and-detail-content"></a>Vztahy mezi seznamu a podrobností obsahu
 Informace o místě pozornost slouží k zobrazení vztah mezi obsahem, aby uživatel byl soustředil ("hlavní" obsah) a další související obsah (obsah "podrobné"). V tomto modelu obsahu podrobností souvisí jasně obsah uživatel pracuje s a je možné zobrazit blízko hlavní obsah. Doplňující informace nebo informace, které nelze shrnout strhávat hlavní obsah by měly dodržovat jiný model, jako je panel nástrojů.

-   **Vždy** zobrazení Podrobnosti o obsahu v těsné blízkosti na hlavní obsah.

-   **Vždy** Ujistěte se, že obsah podrobností stále umožňuje uživateli zůstane zaměřují se na hlavní obsah. Často je nejlepší způsob, jak toho dosáhnout k vykreslení obsahu podrobností jako blízko hlavní obsah, jako je to možné. To můžete udělat vykreslování obsahu podrobností v překryvném okně vedle hlavní obsah nebo vykreslování vložený obsah podrobností pod hlavní obsah.

-   **Nikdy** použít informace o místě pozornost, který přebírá uživatelské mimo hlavní obsah. Pokud uživatelé potřebují k zobrazení Podrobnosti o obsahu samostatně, zveřejněte explicitní akci, která umožňuje uživatelům provést.

#### <a name="design-details"></a>Podrobnosti o návrhu
 Jakmile určíte, že na objekt uživatelského rozhraní je tou správnou volbou existují čtyři hlavní aspekty:

1. **Trvalost:** obsah má být trvalé nebo přechodné?
   Budou uživatelé chtějí zachovat informace k odkazovat a k interakci s? Nebo se uživatelé chtějí rychle okamžitý přehled o informace a potom pokračujte v jeho hlavního úkolu?

2. **Typ obsahu:** obsah bude informační, užitečné nebo navigační?
   Další podrobnosti o obsah předlohy musí uživatele? Potřebuje uživatel k dokončení úkolu, který má vliv na hlavní obsah? Nebo k přesměrováni na jiný prostředek potřebuje uživatel?

3. **Typ ukazatele:** indikátor okolí dávat smysl?
   Můžete informace uvedené v snadno a zobrazit strhávat hlavní obsah?

4. **Gesta:** co gesta se použije k vyvolání a zavřít uživatelského rozhraní?
   Jak uživatel zobrazte podrobnosti o obsahu, který se odesílat hned? Je v přidání gesta jako je například připínat přepínat mezi stavy přechodné a trvalý hodnota?

   Každá z těchto čtyř rozhodovací body budou mít vliv na hlavní součásti uživatelského rozhraní objektu.

### <a name="on-object-ui-components"></a>Součásti uživatelského rozhraní na objekt

1.  Typ kontejneru (obsahu skládání)

    -   S plovoucí desetinnou čárkou

    -   vložené

2.  Typ obsahu

    -   Informační: data, která může být statická nebo dynamická

    -   Užitečné: příkazy, které se mění hlavní obsah

    -   Navigační: odkazy, které uživatel přejít k jinému oknu nebo aplikace, jako je například MSDN

3.  Gesta

    -   Vyvolání

    -   Propuštění

    -   Připnutí

    -   Další interakce

4.  Trvalost a potvrďte změny modelu

    -   Přechodná

    -   trvalý

    -   Automatické

    -   Na vyžádání

5.  Ambientní ukazatele (volitelné)

    -   Vlnovku podtržení

    -   Ikona inteligentní značky

    -   Další indikátory okolí

#### <a name="container-content-presenter-type"></a>Typ kontejneru (obsahu skládání)
 Existují dvě hlavní možnosti, které jsou k dispozici k předkládání obsahu místě pozornost:

1.  **Vložené:** přednášejícího – vložené, jako je například zobrazení náhledu, která byla zavedena v aplikaci Visual Studio 2013 editoru kódu, se uvolnilo místo pro nový obsah přepínáním stávajícího obsahu.

    -   **Preferovat** vložené předvádějící Pokud očekáváte, že budou uživatelé chtít věnovat významné množství času odkazující na nebo interakci s obsahem je k dispozici.

    -   **Vyhněte se** vložené předvádějící Pokud očekáváte, že uživatelé chtít okamžitý přehled o informace k dispozici a potom pokračovat v jejich hlavního úkolu s minimálním dopadem.

2.  **S plovoucí desetinnou čárkou:** s plovoucí desetinnou čárkou skládání umístěné nejblíž vybraný obsah nejvíce nedojde však ke změně rozložení stávajícího obsahu. Mohou být použity různé strategie, jako je například zobrazení plovoucího panelu obsahu přes nejbližší dostupné prázdné znaky na vybraný symbol.

    -   **Preferovat** s plovoucí desetinnou čárkou předvádějící, pokud budou uživatelé chtít okamžitý přehled o informace k dispozici a potom pokračovat v jejich hlavního úkolu s minimálním dopadem.

    -   **Vyhněte se** s plovoucí desetinnou čárkou předvádějící, pokud budou uživatelé chtít strávit významné množství času odkazující na nebo interakci s obsahem je k dispozici.

#### <a name="content-type"></a>Typ obsahu
 Existují tři hlavní typy obsahu, který je možné zobrazit uvnitř žádný kontejner objektů uživatelského rozhraní. Libovolnou kombinaci těchto typů informace mohou být zobrazeny. Jsou tři typy:

1.  **Informační:** většinu objektů uživatelského rozhraní kontejnery se zobrazí nějaký druh informativní obsah. Obsah může představovat informace o stavu prostředí nebo ho může představovat informace o možných budoucích stav prostředí. Například může být používá k zobrazení efekt ke konkrétnímu příkazu, jako je refaktoring, na existující kód.

    -   **Vždy** použití canonical reprezentace informace, které můžete zobrazit. Například kód by měl vypadat jako kód, je kompletní mají funkci zvýraznění syntaxe a měli respektovat písmo a dalších nastaveních prostředí, které má uživatel nastaven.

    -   **Vždy** zvažte podporuje všechny akce informativní obsah, který by bylo možné, pokud se zobrazí tyto stejné informace jako hlavní obsah. Například pokud existující kód uvnitř kontejneru objektů uživatelského rozhraní, důkladně zvážit možnost podporuje možnost procházení a úpravy kódu.

    -   **Vždy** zvažte použití jinou barvu pozadí, pokud nabízí ten samý informativní obsah, který představuje potenciální budoucí stavu.

2.  Užitečné: některé kontejnery objektů uživatelského rozhraní bude poskytovat možnost provádět některé akce hlavní obsah, například při provádění operace refaktoringu názvů.

    -   **Vždy** umístit užitečné příkazy odděleně od informativní obsah.

    -   **Vždy** povolit a zakázat akce v případě potřeby.

    -   **Vždy** odkazovat na standardních pokynů pro zastoupení příkazů v dialogových oknech.

    -   **Vždy** zachovat minimální počet akcí, které jsou vystaveny kontejnerem objektů uživatelského rozhraní na absolutní. Interakce s uživatelským rozhraním objektů by měl být jednoduché a rychlé prostředí. Uživatel by nemělo být výdajů energie na správu kontejneru uživatelského rozhraní na objekt samotný.

    -   **Vždy** zvažte, jak a kdy se kontejner objektů uživatelského rozhraní uzavřený nebo zamítnuto. Jako osvědčený postup jakoukoliv akci, která končí dialog mezi seznam a podrobnosti obsahu také zavřete kontejneru objektů uživatelského rozhraní při vyvolání akce.

3.  **Navigační:** některých objektů uživatelského rozhraní kontejnery zahrnovat odkazy, které uživatel přejít k jinému oknu nebo aplikaci, jako je otevření článku MSDN ve webovém prohlížeči uživatele.

    -   **Vždy** předřaďte navigační odkaz s "Otevřít" tak, aby uživatelé nesmí být sledován se přejde poté nějaký obsah.

    -   **Vždy** nezávislá navigačních odkazů na užitečné odkazy.

#### <a name="ambient-indicators-optional"></a>Ambientní ukazatele (volitelné)
 Okolí ukazatele může být jednoduchý, včetně textu kontrastní barevné od zbývající části kódu, nebo zřejmé, včetně tickler symboly, jako je vlnovku vlnovkou a ikony inteligentních značek. Ambientní indikátory komunikovat dostupnosti další relevantní informace. V ideálním případě poskytují užitečné informace i bez nutnosti uživateli pracovat s nimi.

-   **Vždy** umístěte indikátor okolí tak, aby nepodporuje odklánět pozornost ani zahlcovat uživatele. Pokud není možné umístit indikátor okolí takovým způsobem, vezměte v úvahu jiným řešením.

-   **Vždy** počítače co nejblíž k obsahu, který má vztah k umístění indikátoru okolí.

-   **Vždy** pokusu o vytvoření indikátor, který shrnuje informace jsou k dispozici. Zvažte poskytnutí počet počet datových položek, které jsou k dispozici (například "3 odkazy" namísto jednoduše odkazy na"") nebo jiným způsobem slouží ke shrnutí dat si můžete představit.

    -   V případech, kdy data pro indikátor nemůže vždy být vypočítán a zobrazí okamžitě vezměte v úvahu poskytování zpětné vazby na postupné, jak se počítají hodnoty. Představte si třeba animace změn, které aktualizace k dispozici dat, podobně jako způsob, jakým živou dlaždici e-mailu na Windows Phone aktualizuje jako počet nepřečtených e-mailů zvyšuje.

-   **Nikdy** přidat další indikátory, než uživatel rozumně udělat pro určitou část obsahu. Ambientní ukazatele by měl být užitečné bez nutnosti zásahu uživatele. Indikátory ke ztrátě svých podmínek vyžadují přetečení a další ovládací prvky správy a změňte je na zobrazení.

#### <a name="gestures"></a>Gesta
 Klíčovým prvkem, které uživateli umožňují udržovat zaměřit se na hlavní obsah je díky podpoře správné gesta otevřít a zavřít obsah další podrobnosti.

-   **Vždy** bude uživatel muset provést některé explicitní gesta otevřete další obsah. Běžné otevřít gesta patří:

    -   **Při najetí myší:** popisky nebo jako neinteraktivní informativní obsah

    -   **Explicitní příkaz:** vložené přednášejícího

    -   **Dvakrát klikněte na indikátor okolí:** automaticky otevírané okno CodeLens

-   **Vždy** Zavřít podrobnosti o obsahu vždy, když uživatel stiskne klávesu Esc.

-   **Vždy** vezměte v úvahu kontext uživatelského rozhraní na objekt. Pro obsah předvádějící, které umožňují interakci v rámci kontejneru pečlivě zvažte, jestli se má zobrazit další informace při najetí myší, což je pravděpodobně rušivá pro uživatele pracovního postupu.

-   **Nikdy** zobrazení obsahu při najetí myší, který se zdá být upravitelné nebo pozvání interakci s uživatelem. Toto chování může frustrovat uživatele, pokud se pokusí obsah podrobností, přesuňte kurzor jako standardní chování pro popis okamžitě zavřít, když je ukazatel myši již přes hlavní obsah, který jej vytvořil.

##  <a name="BKMK_SelectionModels"></a> Výběr modely

### <a name="overview"></a>Přehled
 Výběr modelu je mechanismus, který se používá k označení a potvrzení operace na jeden nebo více objektů, které vás zajímají uživatelského rozhraní. Toto téma popisuje vzory interakcí výběru v rámci dokumentu editory sady Visual Studio: textových editorů, návrhové ploše a modelování plochy.

 Uživatelé musí mít k sadě Visual Studio vyjadřuje, co pracují a sady Visual Studio musí odpovídat předvídatelně odeslání zpětné vazby uživatelů o co funguje na. Rozdíly nebo chybnou komunikaci mezi uživatelem a uživatelské rozhraní může vést k uživatele není řadí akci, která může mít nežádoucí důsledky. Často přejde bez povšimnutí chybu, dokud uživateli se zobrazí, že něco chybí nebo se změnila. Výběr modely jsou proto jednu z nejdůležitějších částí návrh uživatelského rozhraní. I když se výběr modelů v sadě Visual Studio jsou v souladu s Windows, existují malé odchylky.

 V sadě Visual Studio jako Windows výběr modely lišit v závislosti na kontextu, ve kterém dojde k interakci. Vybrané možnosti se můžou vyskytnout v čtyři typy objektů:

- Text

- Grafické objekty

- Seznamy a stromové struktury

- Mřížky

  V rámci těchto objektů existují tři typy možností:

- Souvislé

- Nesouvislý

- Oblast

#### <a name="scope"></a>Rozsah
 Nejdůležitější komponenta výběr zajišťuje, že uživatel zná které okno pracují (aktivace) a kde je umístěn (výběr). Visual Studio rozšiřuje správu funkce okna ve Windows, ale schéma aktivace je stejný: interakce s oknem přenese fokus do okna. Visual Studio obsahuje dva ukazatele pro aktivaci: jeden pro okna dokumentu a jeden pro nástroje systému windows.

 Okna dokumentu je aktivní okno indikován kartě okna dokumentu přicházející na přední a změníte jeho barvu pozadí:

 ![Výběr Active kartu v sadě Visual Studio](../../extensibility/ux-guidelines/media/0713-01-activetab.png "0713 01_ActiveTab")

 **Výběr aktivní kartě**

 Pro nástroj windows je označeno aktivní okno a změní barva oblasti záhlaví okna nástroje:

 ![Výběr okno aktivní nástroje v sadě Visual Studio](../../extensibility/ux-guidelines/media/0713-02-activetoolwindow.png "0713 02_ActiveToolWindow")

 **Aktivní okno nástrojů zobrazen primární výběr uzlu**

 ![Okno Výběr neaktivní nástroje v sadě Visual Studio](../../extensibility/ux-guidelines/media/0713-03-inactivetoolwindow.png "0713 03_InactiveToolWindow")

 **Panel nástrojů neaktivní, zobrazen latentní výběr uzlu**

 Jakmile okno je aktivní, zaměřuje je označeno podle výběru modelů uvedených v této části pokyny.

#### <a name="context"></a>Kontext
 Visual Studio byla navržena pro zachování silné koncept kontextu, udržuje přehled o kde uživatel pracuje. Ať už jde nástroj nebo okno dokumentu je aktivní, pouze jedno okno. Okno nejvyšší dokumentu však vždy zůstane latentní výběru. I když fokus může být v panelu nástrojů, zobrazuje okno dokumentu, který byl naposledy aktivní výběr, i v neaktivním stavu. To slouží k zachování kontextu uživatele v dokumentu, který dříve upravovali, podtržení, že Visual Studio uchovává jejich stavu, tak, aby se můžete vrátit a shift bez problémů mezi okny nástrojů a oken dokumentu.

### <a name="text-selection"></a>Výběr textu
 Visual Studio editorů, které jsou výhradně textové, jako je integrované textový editor, použijte stejný model výběr textu a vzhled podle [myš a ukazatele](https://msdn.microsoft.com/library/dn742466.aspx) pokyny interakce zkušeností uživatelů Windows na stránce MSDN. Zaměření pro vstup v textovém editoru je označen symbolem svislá čára volá kurzor. Kurzor je jeden pixel silné a barevné jako inverzní cokoli, co se zobrazí pod ní. Ho bliká podle frekvence nastavil **rychlost blikání kurzoru** nastavení **rychlost** karty **klávesnice** apletu ovládacího panelu.

#### <a name="contiguous-and-disjoint-selection"></a>Souvislé a nesouvislý výběru
 Pouze je souvislý výběr v textovém editoru. Text výběru nejsou povolené, ale mělo by se řešit v editorech grafický objekt nesouvislý. Když se ukazatel myši je nad textová oblast, kurzor se změní na kurzor. Jediným kliknutím umístí kurzor v textovém editoru klikněte na místě. Podržte tlačítko myši začíná výběr zvýraznění a uvolníte tlačítko myši končí zvýraznění výběr.

#### <a name="region-selection-box-selection"></a>Výběr oblasti (pole výběru)
 Visual Studio podporuje oblasti výběrů v textovém editoru a tento postup se nazývá pole výběru. Výběr umožňuje uživateli vybrat oblast textu, který nedodržuje běžného textového datového proudu. Stejně jako u standardní text výběru, musí být souvislý výběr. Výběr je zahájeno tím, že podržíte stisknutou klávesu Alt při tažení myší. Výběr se navíc dají inicializovat podržte stisknutou klávesu Alt a Shift – klávesy a pomocí šipkových kláves k označení oblast výběru. Výběr používá zvýraznění normální výběru a ukazuje kurzor bodu vložení bliká vám kontrolka na konci výběrové oblasti.

 ![Regionální &#40;pole&#41; výběr v sadě Visual Studio](../../extensibility/ux-guidelines/media/0713-04-boxselection.png "0713 04_BoxSelection")

 **Výběr oblasti (pole) v sadě Visual Studio**

#### <a name="text-selection-appearance"></a>Vzhled výběru textu
 Je možné přizpůsobit barvy použité pro aktivní i neaktivní výběr v editoru. Chcete-li přizpůsobit vzhled editoru, uživatel přejít **nástroje > Možnosti**a podívejte se do **prostředí > písma a barvy > textový Editor**.

### <a name="graphical-selection"></a>Výběr grafického

#### <a name="interaction"></a>Interakce
 Výběr grafického objektu může být složité a závisí na několika faktorech:

-   **Model primární výběr editoru.** Editory, které obsahují grafických objektů lze také upravit text nebo tabulky. Editor může být například textový editor, který podporuje také umístění grafických objektů, jako je například Návrhář XAML Visual Studio. Podporuje různé typy objektů může ovlivnit, jak uživatel vybere skupiny tvořené různé typy objektů.

-   **Podpora pro výběr primární a sekundární stavy.** Editor může poskytnout primární a sekundární vybrané stavy tak, aby objekty lze upravit v článku, zarovnání mezi sebou, změně velikosti dohromady, a tak dále.

-   **Podpora úpravy na místě.** Editory můžete povolit také obsah grafické objekty, které má být upraven. Například tvar obdélníku může také obsahovat text uvnitř, který může uživatel změnit. Kromě toho může být tento text na střed nebo oprávněné. Místní úpravy. zahrnuje podrobnější úroveň interakci s uživatelem a proto vyžaduje odpovídající sadu vizuální prvky pro zobrazení informací o stavu uživatele.

#### <a name="mouse-interaction"></a>Interakce s myší

|Vstup|Výsledek|
|-----------|------------|
|Klikněte na objekt nevybrané|Vybere objekt a zobrazí na přerušovanou čáru a úchyty, pokud je objekt umožňující změnu velikosti.|
|Klikněte na vybraný objekt|Aktivuje, pokud objekt podporuje úpravy na místě. Režim úprav na místě kliknutí mimo objekt deaktivuje.|
|Poklikáním na objekt|Otevře se kódu na pozadí objektu pro úpravy a může vložit obslužnou rutinu výchozí události, v případě potřeby.|
|Přejděte na objekt|Ukazatel se změní na kurzor přesunutí. Vzhled objektu, například jeho světelnost nebo barvu, může se měnit.|
|Přejděte na úchytu|Ukazatel se změní na ukazatel změny velikosti. Pro objekty, které podporují otočení některé úchyty může změna ukazatele otočit kurzor jako ukazatel myši umístěn jinak (třeba přesunout dále od) s ohledem na úchyt.|
|Přetažení|I v případě, že objekt nebyl vybraný dříve, ukazatel se změní na kurzor přesunutí a přesune objekt.|
|Editor ztratí fokus.|Deaktivuje místní režim úprav, i když objekt uchovává obsah a vzhled, kterou měl při posledním stavu operace nebo výběru.|
|Výběr objektu|Indikován ohraničení, tečkovaná čára nebo jiných vizuálně odlišné zacházení zvýrazněte hranic objektu.|
|Změnit velikost vybraného objektu|Indikován úchyty.<br /><br /> Objekt umožňující změnu velikosti má osm popisovače představující všechny směry, ve kterém se dá změnit. Menší počet popisovačů mohou být použity, pokud objekt lze nastavit pouze v některých směrech. Pokud uživatel velikosti objektu dolů, kde by interaktivní osm obslužné rutiny, může použít čtyři obslužné rutiny. Popisovač velikosti by měl být svázané do okna metrik okraj a okraj s **GetSystemMetrics** – funkce rozhraní API na velikost výkonový zisk rozlišení obrazovky.<br /><br /> ![Úchyty pro změnu velikosti](../../extensibility/ux-guidelines/media/0713-05-resizehandles.png "0713 05_ResizeHandles")|
|Otáčení vybraného objektu|![Otočit popisovače](../../extensibility/ux-guidelines/media/0713-06-rotate.png "0713 06_Rotate")|

#### <a name="keyboard-interaction"></a>Interakce klávesnice

|Vstup|Výsledek|
|-----------|------------|
|Tabulátor|Posune indikátor fokus mezi logickému uspořádání objektů v editoru. Může to být zleva doprava nebo nahoru dolů v závislosti na **TabIndex** (nebo obdobných) hodnotu vlastnosti, pořadí vytváření objektů a obecný účel editoru. Shift + Tab obrátí směr ukazatele fokusu.|
|MEZERNÍK|Při stisknutí klávesy se zachová, aktivuje režim posouvání. Vstup z myši další je potřeba posunout zobrazení pozici.|
|Ctrl + mezerník|Při stisknutí klávesy se udržuje, aktivuje režim přiblížení. Vstup z myši další se vyžaduje ke zvýšení nebo snížení na faktor zvětšování.|
|Ctrl + Alt + mínus|Sníží na faktor zvětšování o jednu úroveň.|
|Ctrl + Alt + symbol plus|Zvýší na faktor zvětšování o jednu úroveň.|
|Ctrl nebo SHIFT|Přidá objekt do výběru skupiny. CTRL také umožňuje odebrat objekty jednotlivě ze skupiny pro výběr.|
|Enter|Provede výchozí příkaz pro objekt (obvykle otevřít nebo upravit).|
|F2|Aktivuje místní úpravy. pro objekt.|
|Klávesy se šipkami|Přesune vybrané objekty ve směru šipka stisknuto malých přírůstcích (třeba 1 pixelu po jednom)|
|CTRL + klávesy se šipkami|Přesune vybrané objekty ve směru šipka stisknutí, v přírůstcích větších (například 10 pixelech po jednom)|
|SHIFT + ŠIPKA klíče|Změní velikost vybrané objekty v jednom směru v malých přírůstcích (třeba 1 pixelu po jednom)|
|Ctrl + Shift + klávesy se šipkami|Změní velikost vybrané objekty v jednom směru, v přírůstcích větších (například 10 pixelech po jednom)|

 Když uživatelé upravit ovládací prvky na místě, může mít smysl pro objekty automaticky změní velikost s uživatelským vstupem. Například pokud uživatel upravuje ovládací prvek popisku, pak popisek by měl zvětší k zobrazení textu, který uživatel právě zadali. Pokud to neuděláte, uživatel musí změnit velikost ovládacího prvku ručně po dokončení úprav textu. Pokud uživatel má mnoho ovládacích prvků, to se stane rote a neproduktivní úloh.

#### <a name="graphical-containers"></a>Grafické kontejnery
 V některých případech grafické editory poskytují kontejnery pro další grafické objekty, jako je například ovládací prvek Windows Forms Panel nebo ovládací prvek rozložení mřížky v Návrháři HTML. Pokud editor poskytuje kontejnery pro další grafické objekty, následující Výběr modelu byste měli použít pouze kontejneru (objektů v rámci kontejneru použijte standardní model, jako je popsáno výše):

|Vstup|Výsledek|
|-----------|------------|
|Kliknutím na kontejner|Vybere objekt kontejneru bez přímo výběrem libovolné prvku obsažených objektů. Kontejner se můžou přesunout nebo změně velikosti se standardní zkratky myši a klávesnice (jak je popsáno výše). Obsažené objekty v relaci přesunou do kontejneru, ale obsažené objekty nelze změnit velikost, pokud je tato možnost také přímo vybrána.|
|Najeďte myší oblasti hranice kontejneru.|Přesunout kurzor, určující, že můžete přesunout kontejneru se změní myši.|
|Přetáhněte oblast hranice kontejneru.|Ukazatel myši se změní na kurzor přesunutí a přesune kontejneru (a obsažených objektů v rámci). Kontejner nelze přesunout, aniž byste nejdřív vybíraného jediným kliknutím.|
|Kliknutím na objekt v kontejneru|Zruší výběr kontejneru (Pokud je vybraná) a vybere pouze kliknutí na objekt.|
|SHIFT + klikněte na tlačítko nebo Ctrl + kliknutí myši na obsaženého objektu a/nebo kontejneru|Přidá kliknutí na objekt existujícím výběru nebo výběru skupiny. Pokud kliknutí na objekt je již členem skupiny výběru, bude odebrán ze skupiny pro výběr.|

 Obsažené objekty by měl splňovat základní Výběr modelu, jak je popsáno v předchozí části. Z Návrháře formulářů Windows testování použitelnosti, očekává uživatelům bezproblémový přístup k obsažené objekty bez použité kroků (uložené v objektu členství ve skupině).

#### <a name="disjoint-and-region-selections"></a>Nesouvislý a výběr oblastí
 Editory grafický objekt by měl podporovat nesouvislý výběry. Mějte prosím na paměti, že tento obrázek nezobrazuje vzhled ovládacího prvku pro sadu Visual Studio. Zobrazit [vzhled výběr grafického objektu](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) podrobné specifikace visual.

 ![Nesouvislý a oblasti selektory](../../extensibility/ux-guidelines/media/0713-07-disjointregionselectors.png "0713 07_DisjointRegionSelectors")

 **Nesouvislý výběru**

 Grafické editory by taky mělo poskytovat oblasti výběrů indikátor výběru marquee-type. Pokud grafický editor podporuje další typy objektů (například podle textu), nemusí být možné v závislosti na omezení tyto typy objektů oblast výběru.

 ![Výběr](../../extensibility/ux-guidelines/media/0713-08-marqueeselection.png "0713 08_MarqueeSelection")

 **Výběr**

#### <a name="primary-and-secondary-selections"></a>Výběr primární a sekundární
 Některé editory grafický objekt povolit uživatelům upravit nebo zarovnání objektů ve skupinách. V takovém případě koncept výběr primární a sekundární je potřeba zavést. Primární výběr je objekt, na které všechny ostatní objekty reagovat pro operace skupiny. Objekt, který uživatel vybere první stane primární ovládací prvek a následné výběry stát sekundární výběry. Primární výběr má odlišné visual ošetření ze sekundární vybrané položky k označení, který objekt je primární:

 ![Výběr primární a sekundární](../../extensibility/ux-guidelines/media/0713-09-primarysecondary.png "0713 09_PrimarySecondary")

 **Primární výběr dvě sekundární výběry**

####  <a name="BKMK_GraphicalObjectSelectionAppearance"></a> Vzhled výběr grafického objektu
 Výběr popisovače jsou čtverce obdélníkové vzoru kolem ohraničovací rámeček objektu. Následující graf ukazuje příklady různé stavy, které grafický objekt může mít s popisovač, velikost a místní úpravy vzhledu. Velikost úchyty by měl být svázané ohraničení okna a pomocí metriky edge **GetSystemMetrics** rozhraní API.


|          Stav          |  Vzhled   |                                                                  Vizuální podrobnosti                                                                  |
|-------------------------|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
|     **Nevybrané**      |    Výchozí    |                 ![Výchozí stav tlačítka](../../extensibility/ux-guidelines/media/0713-10-defaultstate.png "0713 10_DefaultState")                 |
|  **Primární výběr**  |   Umožňující změnu velikosti   |       ![Primární výběru s úchyty pro změnu velikosti](../../extensibility/ux-guidelines/media/0713-11-primaryresize.png "0713 11_PrimaryResize")        |
|  **Primární výběr**  | Není umožňující změnu velikosti |    ![Primární výběru bez úchyty pro změnu velikosti](../../extensibility/ux-guidelines/media/0713-13-primarynoresize.png "0713 13_PrimaryNoResize")    |
|  **Primární výběr**  |    Uzamčeno     |              ![Primární výběr uzamčen](../../extensibility/ux-guidelines/media/0713-15-primarylocked.png "0713 15_PrimaryLocked")              |
| **Sekundární výběru** |   Umožňující změnu velikosti   |    ![Sekundární výběru s úchyty pro změnu velikosti](../../extensibility/ux-guidelines/media/0713-17-secondaryresize.png "0713 17_SecondaryResize")     |
| **Sekundární výběru** | Není umožňující změnu velikosti | ![Sekundární výběru bez úchyty pro změnu velikosti](../../extensibility/ux-guidelines/media/0713-19-secondarynoresize.png "0713 19_SecondaryNoResize") |
| **Sekundární výběru** |    Uzamčeno     |           ![Sekundární výběr uzamčen](../../extensibility/ux-guidelines/media/0713-21-secondarylocked.png "0713 21_SecondaryLocked")           |
|      **Aktivní uživatelského rozhraní**      |    Výchozí    |                       ![Aktivního stavu uživatelského rozhraní](../../extensibility/ux-guidelines/media/0713-23-uiactive.png "0713 23_UIActive")                        |

### <a name="view-selection-models"></a>Zobrazit výběr modely

#### <a name="tree-view"></a>Stromové zobrazení
 Výběr v zobrazení stromu se zobrazí s jednoduchou zvýraznění. Pokud uživatel klikne na název uzlu nebo ikonu uzel, uzel stane vybrat. Trojúhelníkové glyfy nalevo od uzlu rozbalte nebo kontrakt ovládacího prvku stromu je ale nemají vliv na výběr uživatele, s jednou výjimkou: výběr při sbalení nadřazeného uzlu je výběr na podřízeným uzlem tohoto uzlu, se přesune na nadřazený prvek.

 ![Typické stromové zobrazení v sadě Visual Studio](../../extensibility/ux-guidelines/media/0713-25-treeview.png "0713 25_TreeView")

 **Typické stromové zobrazení v sadě Visual Studio**

 Stromová zobrazení může podporovat vybrané souvislých a nesouvislý, i přes různé úrovně ve stromové struktuře. Souvislý nebo nesouvislý více výběrů musí provést na uzlech viditelné stromu. Pokud je sbalený uzel, nesouvislým výběr dojde ke ztrátě a získá výběr uzlu, který se sbalil. Tímto způsobem může uživatel zobrazit uzly, které bude ovlivněná operací. Pokud uzly jsou sbaleny, bude jasné uzlů, které může to mít vliv.

 Pokud je vybrána nadřazeného uzlu, operace by se měly používat na hodnotu parent, ale můžou nastat případy, kdy je vhodné pro operace platí pro nadřazené a všechny její podřízené položky. V takovém případě zadejte dalšího uživatelského rozhraní během operace, jako je například zaškrtávací políčko nebo potvrzovací dialogové okno, aby možnost "platí pro všechny podřízené objekty" explicitní uživatele.

##### <a name="renaming"></a>Přejmenování
 Pokud uzly ve stromu, podporují přejmenování, přejmenování se má počítat na místě. Nahrazující operace by měla být standardní ve všech ovládacích prvcích stromů v sadě Visual Studio. Zadejte příkaz rename, která okamžitě aktivuje režim úprav na místě, s výběr textu pokrývající celý název uzlu přijímá vstup uživatele. Pokud uzel představuje soubor, by měl obsahovat název souboru rozšíření. Výběr zvýraznění by měl obsahovat pouze text není rozšíření a název souboru.

|Vstup|Výsledek|
|-----------|------------|
|Enter – klávesa|Potvrdí se operace přejmenování|
|Klávesy ESC|Zruší operaci přejmenování|
|Kliknutím mimo oblast úpravy na místě|Potvrdí se operace přejmenování|
|Vrácení zpět|Poskytují snadno zpět, chcete-li zrušit operaci přejmenování|

#### <a name="selection-within-lists-and-grid-controls"></a>Výběr v seznamech a ovládací prvky mřížky
 Klíčovým konceptem sady výběr v seznamu je, že je založené na řádek, to znamená, že když bude proveden výběr celého řádku je zvolen jako celek. Naopak mřížky můžete povolit konkrétní buňky, které chcete vybrat, aniž by to ovlivnilo ostatní aspekt řádku. Mřížka mohou také obsahovat hierarchii vnořené řádků (například TreeGrid), které umožňují celý větví úrovně hierarchie k vybrané a možnost to interakcí se nadřazených řádků. Výběr v seznamu se zobrazí podle jednoduchých zvýraznit barvy na celý řádek dat. Fokus je zobrazen v jednom pixelu tečkovaná ohraničení kolem aktuálního upravitelné řádku nebo buňky (řádek, pokud všechny buňky jsou jen pro čtení).

> [!NOTE]
>  **Fokus** a **výběr** jsou různé koncepty. *Fokus* slouží jako ukazatel toho, které uživatelského rozhraní je určená – element pro vstup není explicitně směrovat na jiný objekt, zatímco *výběr* týká stavu zařazení objektu v sadě objekty, na kterých následné operace může proběhnout.

 Výběry v seznamech může být souvislé, nesouvislé, nebo oblast. Když je povolené, souvislý více výběrů a nesouvislý by měl vždy být podporován výběr, při podporu pro výběr oblasti (pole) je volitelný. Výběr oblasti lze inicializovat pomocí přetahování v prázdné místo v seznamu obsahu.


| Objekt | Výběr  |
|--------|------------|
|  Seznam  | Souvislé |
|  Seznam  |  Nesouvislý  |
|  Seznam  |   Oblast   |

 Po kliknutí na seznamu vybere řádek, kde došlo k kliknutím na. Pokud uživatel se stane, klikněte v seznamu buňky, která podporuje úpravy na místě, buňku také okamžitě aktivuje pro místní úpravy. V opačném případě celý řádek okamžitě vybraný a zobrazuje zvýraznění.

 Přetažením v seznamu obsahu provede jednu tři věci:

-   Inicializuje oblast výběru, pokud ji podporuje v seznamu a tlačítko myši stisknuté je prázdné znaky

-   Zahájí operaci přetažení, pokud je seznam buňku nebo řádek podporuje se zdroji přetažení

-   Vybere aktuální řádek

##### <a name="in-place-editing"></a>Úpravy na místě
 Pokud místní úpravy. je povoleno, existují dva základní modely: výběr ovládacího prvku a vlastnost jednoduché úpravy. Pomocí jednoduchých úprav obsah je zvýraznit a připravený pro uživatele, poté, co se aktivuje místní úpravy. Tam, kde se implementuje vlastnost ovládacího prvku pro výběr, zobrazí se tlačítka, které se vyvolá vlastnost výběr místní režim úprav je aktivován a nezvýrazní se aktuální výběr. Tlačítko pro výběr by mělo být zarovnána vpravo v buňce. Příklady úpravy na místě, najdete v článku **okno vlastností** a **seznamu úkolů** v sadě Visual Studio.

##### <a name="keyboard-support"></a>Podpora klávesnice
 Podpora klávesnice pro výběr v seznamech a mřížky dodržuje standardní konvence Windows:

-   Klávesami se šipkami seznamu výběru každý řádek nebo buňku přesunout fokus.

-   SHIFT + ŠIPKA vede souvislý výběr směr klávesy se šipkami.

-   CTRL + ŠIPKA, za nímž následuje MEZERNÍK přepíná mezi přidávání a odebírání položek seznamu z výběru vytváření nesouvislý výběru.

-   Pro tabulky, které obsahují vnořené hierarchie klávesu šipka vpravo rozšiřuje nadřazený řádek a klávesu šipka vlevo sbalí jeden.

-   Stisknutím klávesy Tab přesunete fokus mezi buňkami v aktuálním řádku, pokud lze upravovat buňky.

-   Klávesy Enter provede výchozí příkaz pro položku v seznamu (často **otevřít**).

-   Klávesy F2 aktivuje místní úpravy. pro aktuálně vybranou buňku.

##  <a name="BKMK_PersistenceAndSavingSettings"></a> Trvalost a ukládají se nastavení

### <a name="overview"></a>Přehled
 Přestože jednotlivé softwarové komponenty v sadě Visual Studio je obvykle za svůj vlastní stav a stálost, Visual Studio automaticky ukládá nastavení v některých případech, jako s velikostí oken a umístění. Následující tabulka je kombinací nastavení automaticky ukládat a nastavení, které vyžadují explicitní uživatele nebo naprogramovat akce.

|Objekt|Co se má uložit|Kdy se mají uložit|Kam chcete uložit|
|------------|------------------|------------------|-------------------|
|Vybrat objekt (například řádek kódu)|Zarážku na řádek kódu<br /><br /> Zástupce uživatel přidružený k řádku kódu|Pokud je projekt uložen|**Uživatelské možnosti (.suo)** souboru projektu|
|Dialogové okno|Umístění dialogové okno, pokud byl přesunut<br /><br /> Zobrazení, které uživatel naposledy použil v dialogovém okně|Když se zavře dialogové okno<br /><br /> Po ukončení relace sady Visual Studio|V paměti<br /><br /> V registru **HKEY_Current_User**|
|Okno|Velikost a umístění okna|Když se zavře okno<br /><br /> Při změně režimu sady Visual Studio<br /><br /> Po ukončení relace sady Visual Studio|**Uživatelské možnosti (.suo)** souboru projektu<br /><br /> Soubor vlastní nastavení pro okno nastavení|
|Dokument|Aktuální výběr v dokumentu<br /><br /> Zobrazení dokumentu<br /><br /> Posledních několika místech uživatel navštívil|Když je dokument uložen|**Uživatelské možnosti (.suo)** souboru projektu|
|Projekt|Odkazy na soubory<br /><br /> Odkazy na adresáře na disku<br /><br /> Odkazy na ostatní software<br /><br /> Součásti<br /><br /> Stavové informace o samotném projektu|Pokud je projekt uložen|Soubor projektu|
|Řešení|Odkazy na projekty<br /><br /> Odkazy na soubory|Při uložení projektu nebo řešení|**Řešení (.sln)** souboru|
|Nastavení v **nástroje > Možnosti**|Přizpůsobení klávesnice<br /><br /> Přizpůsobení panelu nástrojů<br /><br /> Barevná schémata|Když **nástroje > Možnosti** zavře dialogové okno<br /><br /> Po ukončení relace sady Visual Studio|V registru **HKEY_Current_User**|

 Co uživatel provádí a při jejich aktivitě, určuje, zda se nastavení uložená v paměti (během relace), uloženo na disk (napříč relacemi jako nastavení registru), jako součást projektu nebo řešení samotný soubor, v rámci sady **řešení Možnosti (.suo)** souboru nebo souboru vlastního nastavení pouze komponenty softwaru ví o. V tabulce výše najdete několik událostí, na kterých je ukládat nastavení. Existují však jinou dobu, ve kterých můžete chtít uložit stav:

-   Když uživatel změní umístění v rámci dialogového okna nebo okno

-   Když uživatel přenese fokus do jiného okna

-   Když uživatel přepíná z návrhu na režim ladění

-   Když se uživatel odhlásí svůj účet

-   Když počítač přejde do režimu hibernace nebo ukončení

-   Když počítač nebo pevný disk se chystá naformátována a znovu nastavit

### <a name="window-configurations"></a>Konfigurace oken
 Konfigurace okna je základní prezentaci vývojové prostředí – je schéma skládající se z seznam oken nástrojů, které jsou k dispozici a způsob, ve kterém jsou uspořádány. Pro systém windows spravuje rozhraní IDE (integrované vývojové prostředí systému windows) se ukládají informace o rozložení na uživatele, takže když uživatel spustí, rozhraní IDE, rozložení okna se zobrazí stejně jako když trvají byl ukončen sady Visual Studio. Stav a umístění okna IDE se ukládají ve vlastních možností soubor ve formátu XML. Okna nástrojů, které vytváří balíčky načtena do integrovaného vývojového prostředí uchovávat informace o jejich stavu v registru a může nebo nemusí být na uživatele.

#### <a name="profile-specific-layouts"></a>Profil specifické rozložení
 Každý profil obsahuje rozložení oken nástrojů, uspořádány v podobě zkušenosti vývojáře konkrétní osoby (očekávat vývojáře v jazyce Visual C++ **Průzkumníka řešení** na levé straně rozhraní IDE, zatímco očekávatvývojářevC# **Průzkumník řešení** na pravé straně). Rozložení oken konkrétní profil jsou načteny po kliknutí na profil při spuštění. Autor balíčku ujasnit některé věci rozložení okna, která je nejvhodnější pro zkušenosti zákazníků vědomím, že změny, které uživatel provede konfiguraci okna se potom nastavit jako trvalý.

##  <a name="BKMK_TouchInput"></a> Dotykové ovládání
 Uživatelé stále používají vývoje produktů společnosti Microsoft na vaše zařízení dotykové. Existují však překážky, které se obtížně pomocí nástrojů pro vývoj na vaše zařízení dotykové. Uživatelé se očekávají, že naše produkty k poskytování spolehlivé a přesné dotykového ovládání. Účelem těchto pokynů, které je podkladem pro rozhodnutí o jaké schopnosti touch začlenit a poskytuje konzistentní dotykového ovládání v sadě Visual Studio a souvisejících produktů.

### <a name="levels-of-experience"></a>Úrovně zkušeností
 Následující úrovně prostředí mají sloužit jako průvodce k týmům, které rozhodnout, jaké funkce dotykového ovládání a nabídnout podle jejich požadované úrovni zájmu investic v kontaktu.

-   **Základní zkušenosti** je pro týmy, které chcete poskytnout dotykového ovládání možnosti tak, že neexistují žádné elementy dead v průběhu své práce.

-   **Optimalizované prostředí** je pro týmy, které chcete poskytnout nejvíce touch běžné možnosti (například na těch, obvykle k dispozici v aplikacích prohlížeče internet).

-   **Se zvýšenými oprávněními prostředí** je pro týmy, které chcete přidat tyto možnosti jako gesta nebo další volitelné možnosti, které můžete své aplikace dotykovými popisný.

||Základní zkušenosti|Optimalizované prostředí|Prostředí se zvýšenými oprávněními|
|-|----------------------|--------------------------|-------------------------|
|Umožňuje uživatelům...|Oprava kódu a řešení/na úrovni projektu pro čtení bez konce dead|Provádění úloh údržby, refactors a navigace|Probíhat konzistentní, intuitivní a plynulé prostředí s jistotou|
|Editor|Dotykové ovládání posouvání a výběr<br /><br /> Posuvník dotykové ovládání odkazů a stiskněte klávesu + přetažení|Přiblížení roztažením prstů<br /><br /> Rychlé posouvání<br /><br /> Výběr<br /><br /> Snadné použití místní nabídky||
|Začátek nástroje systému windows|Seznam posouvání<br /><br /> Výběr položky<br /><br /> Posuvník dotykové ovládání odkazů a stiskněte klávesu + přetažení|Snadné položky posouvání a výběr||
|Časová okna||Změňte velikost okna<br /><br /> Rychlý přístup||
|Dobře dokumentu||Snadnou navigaci mezi otevřených souborů||
|Gesta||Ujistěte se, že společné gesta pracovat v integrovaném vývojovém prostředí|Akce na základě gesta<br /><br /> Podpora přetahování myší a návrháři|
|Další důležité informace|||Vlastní klávesnice na obrazovce|

#### <a name="gestures"></a>Gesta
 Gesta poskytují uživatelům zástupce příkazy, které by jinak vyžadovaly složitější interakce. Další informace naleznete pokyny pro Windows v [gesta dotykového ovládání běžné pro desktopových aplikací](http://msdn.microsoft.com/library/windows/desktop/dd940543\(v=vs.85\).aspx)a postupovat podle těchto pokynů pro většinu gesta, včetně jednoduchá gesta jako je například posouvání a zvětšování.
