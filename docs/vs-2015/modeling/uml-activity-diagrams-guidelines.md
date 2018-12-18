---
title: 'Diagramy činnosti UML: Pokyny | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a13db375305e96c4657e007f9cd8bfffbf34f990
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722680"
---
# <a name="uml-activity-diagrams-guidelines"></a>Diagramy činnosti UML: Pokyny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio můžete nakreslit diagram aktivity popisující obchodních procesů nebo algoritmu softwaru jako tok práci prostřednictvím obnáší sérii akcí. Lidé, softwarové komponenty nebo zařízení můžete provádět tyto akce. Video ukázku naleznete v tématu: [zachycení obchodní pracovní postupy pomocí diagramů aktivit](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/).  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Chcete-li vytvořit diagram činností UML, na **architektura** nabídky, klikněte na tlačítko **nové UML nebo diagramu vrstev**.  
  
 Diagram činnosti můžete použít k mnoha účelům:  
  
- K popisu obchodních procesů nebo toku práce mezi uživateli a systému. Další informace najdete v tématu [modelování uživatelských požadavků](../modeling/model-user-requirements.md).  
  
- K popisu kroky v případu použití. Další informace najdete v tématu [diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- K popisu metody, funkce nebo operace v softwaru. Další informace najdete v tématu [modelování architektury aplikace](../modeling/model-your-app-s-architecture.md).  
  
  Náčrt diagramu aktivit vám může pomoct vylepšit proces. Pokud bude velmi složité ukáže jako diagram existujícímu procesu, můžete zvážit, jak může zjednodušit proces.  
  
  Referenční informace o prvcích v diagramech aktivit najdete v tématu [diagramy činnosti UML: referenční](../modeling/uml-activity-diagrams-reference.md).  
  
##  <a name="Relationships"></a> Vztah k jiným diagramům  
 Pokud si nakreslíte diagramu činnosti popisující obchodních procesů nebo způsobem, ve kterém uživatelé vašeho systému, lze nakreslit diagram případu použití a různých zobrazení stejné informace. V diagramu případu použití nakreslete akcí, které případy použití. Poskytněte stejné názvy jako odpovídající akce případy použití. Přináší výhody zobrazení případu použití, můžete:  
  
- Zobrazit jeden diagram jak větší akce/svědectví se skládají z menších pomocí vztahu zahrnuje.  
  
- Každý případ akce/použití připojení explicitně na uživatele nebo externí systémy, které jsou zahrnuté v jeho spuštění.  
  
- Nakreslete ohraničení kolem případy akce/použití nepodporuje systém nebo každou hlavní součást.  
  
  Můžete také nakreslit diagram aktivity k popisu podrobný návrh softwaru operace.  
  
  V diagramu činnosti můžete zobrazit tok dat předávaných mezi akcemi. Naleznete v části [popisující toku dat](#DataFlows). Ale diagramu činnosti nepopisuje struktury data. K tomuto účelu můžete nakreslit diagram tříd UML. Informace naleznete v tématu [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md).  
  
##  <a name="BasicSteps"></a> Základní postup pro vytvoření diagramů aktivit  
 Podrobné pokyny k vytvoření všech diagramů modelování jsou popsány v [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-draw-an-activity-diagram"></a>Chcete-li nakreslit diagram aktivity  
  
1.  Na **architektura** nabídky, klikněte na tlačítko **nové UML nebo diagramu vrstev**.  
  
2.  V části **šablony**, klikněte na tlačítko **Diagram činností UML**.  
  
3.  Pojmenujte diagram.  
  
4.  V **přidat k projektu modelování**, vyberte existující projekt modelování z řešení, nebo **vytvořit nový projekt modelování**.  
  
#### <a name="to-draw-elements-on-an-activity-diagram"></a>Chcete-li nakreslit prvků v diagramu činnosti  
  
1.  Prvky přetáhnout z panelu nástrojů do diagramu.  
  
     Začněte tím, že umístění hlavní činnosti v diagramu, jejich propojení a následným přidáním poslední detaily, jako jsou počáteční a konečné uzly.  
  
    > [!NOTE]
    >  Stávající prvky nelze přetáhnout do diagramu z Průzkumníku modelů UML.  
  
2.  Pro připojení prvky, postupujte takto:  
  
    1.  V **Diagram činnosti** sadě nástrojů klikněte na tlačítko **konektor**.  
  
    2.  V diagramu klikněte na source element.  
  
    3.  Klikněte na cílového prvku.  
  
        > [!NOTE]
        >  Pokud chcete použít nástroj pro více než jednou, dvakrát klikněte na nástroj v soupravě nástrojů.  
  
#### <a name="to-move-an-activity-to-another-package"></a>Aktivita přesunout do jiného balíčku  
  
-   V **Průzkumníku modelů UML**, přetáhněte aktivitu do balíčku.  
  
     \- nebo –  
  
-   V **Průzkumníku modelů UML**, klikněte pravým tlačítkem na aktivitu a klikněte na tlačítko **Vyjmout**. Klikněte pravým tlačítkem na balíček a klikněte na tlačítko **vložit**.  
  
    > [!NOTE]
    >  Aktivity se zobrazí v Průzkumníku modelů UML pouze při přidání prvního prvku do diagramu.  
  
##  <a name="SimpleControlFlow"></a> Popis toku řízení  
 Diagram činnosti popisuje algoritmu obchodního procesu nebo softwaru jako obnáší sérii akcí. Konektor šipky ukazují, jak řízení je předáno postupně z jedné akce na další. Obvykle akci můžete spustit až po dokončení předchozí akci.  
  
 Na následujícím obrázku je příklad, jak lze zobrazit posloupnost akcí s akcemi, konektory, větve a smyčky. Každý prvek je vysvětleno podrobněji v následujících částech.  
  
 ![Diagram jednoduchého činnosti](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")  
  
 Použití diagramů aktivit **akce** a **konektory** k popisu vašeho systému nebo aplikace jako řadu objektů akce s ovládacím prvkem postupně toku z jedné akce na další.  
  
- Vytvoření **akce** (1) pro každou hlavní úkol, který se provádí pomocí uživatele, systém nebo obojí ve spolupráci.  
  
  > [!NOTE]
  >  Pokuste Popsat algoritmus s několika akce nebo proces. Můžete použít **volání akce chování** definovat všechny akce podrobněji v samostatném diagramu, jak je popsáno v [popisující dílčí aktivity se volání akce chování](#Subactivities).  
  
- Ujistěte se, že název každé akce jasně Určuje, co obvykle dosahuje.  
  
- Odkaz akce v sekvenci s **konektory** (2).  
  
- Každá akce končí před začátkem další akce v toku řízení. Pokud budete chtít obsahují popis akcí, které se překrývají, použijte **Forku uzel** jak je popsáno v části [souběžných toků](#Concurrent).  
  
  I když diagram popisuje posloupnost akcí, nepopisuje jak akce, které provádějí, nebo jak řízení je předáno z jednoho akce na další. Pokud pomocí diagramu představují obchodní proces, ovládací prvek mohla být předána, třeba když jeden uživatel odešle e-mailovou zprávu na jiný. Pokud používáte diagramu pro reprezentaci návrh softwaru, ovládací prvek mohla být předána podle normálního toku provádění z jeden příkaz na další.  
  
### <a name="describing-decisions-and-loops"></a>Popis rozhodnutí a smyčky  
  
-   Použití **rozhodnutí uzel** (3) k označení bodu, kdy výsledek rozhodnutí určí další krok. Můžete nakreslit tolik odchozí cest.  
  
-   Pokud používáte diagramu činnosti k definování součástí aplikace, byste měli definovat chrání (4) tak, aby bylo zřejmé, když je potřeba vzít jednotlivé cesty. Klikněte pravým tlačítkem na konektor, klikněte na tlačítko **vlastnosti**a **vlastnosti** okno, zadejte hodnotu pro **Guard** pole.  
  
-   Není vždy nutné definovat chrání. Například pokud pomocí diagramu činnosti popisují obchodních procesů nebo protokol interakce, větev definuje řadu možností na uživatele nebo na komunikující komponenty.  
  
-   Použití **sloučit uzel** (5) a dejte dohromady dvě nebo více alternativní toky, které rozvětvených na **rozhodnutí uzel**.  
  
    > [!NOTE]
    >  Měli byste použít **sloučit uzel** spojit alternativních toků, namísto spojuje toků v akci. V tomto příkladu by správná připojení z uzlu rozhodnutí přímo zpět do **zvolte položku nabídky**. Je to proto, že akce se nespustí, dokud se všechny příchozí konektory dorazily vlákna ovládacího prvku. Proto vám by měl pohromadě pouze souběžných toků v akci. Další informace najdete v tématu [souběžných toků](#Concurrent).  
  
-   Pomocí větví popisují smyčky, jak je znázorněno v příkladu.  
  
    > [!NOTE]
    >  Zkuste vnořit smyčky strukturované způsobem, jako byste to udělali v programovém kódu. Pokud jsou popisující existující obchodní proces, to může odhalit některé příležitosti pro vylepšení ho.  
  
### <a name="starting-the-activity"></a>Spuštění aktivity  
 Existují dva způsoby označení vstupních bodů do aktivity:  
  
-   **Počáteční uzel**  
  
     Vytvořte si ho **počáteční uzel** (6) označuje první akci aktivity.  
  
     Tato metoda je nejužitečnější, když jsou popisující aktivitu dílčí, nebo pokud není potřeba explicitně uvést, co spustí aktivity. Například objednávka pokrmu aktivity jasně začíná, když zákazník získá jistě zájem své.  
  
-   **Přijímat události uzlu**  
  
     Vytvoření **přijímat události uzly**, jak je popsáno v části [souběžných toků](#Concurrent), k označení spuštění vlákna, které reaguje na konkrétní události, jako je například uživatelský vstup. Neposkytuje příchozí tok k uzlu. Vynechání příchozí tok, který označuje, že vlákno se spustí pokaždé, když dojde k události.  
  
     Tato metoda je nejužitečnější při popisují odpověď na konkrétní vnější události.  
  
### <a name="ending-the-activity"></a>Poslední aktivita  
 Použití **poslední uzel aktivity** (7) k označení konce aktivity.  
  
-   Dosáhne-li vlákno ovládacího prvku **poslední uzel aktivity**, všechny aktivity souběžných akce a dílčí aktivity ukončit.  
  
-   Pro přehlednost dalších konektorů, které můžete použít více než jeden uzel poslední aktivity.  
  
### <a name="interrupting-the-activity"></a>Přerušení aktivity  
 K popisu, jak běžný tok aktivity může dojít k přerušení, například pokud se uživatel rozhodne zrušit procesu, můžete vytvořit přijímat události uzlu, který čeká na tuto událost. Další informace najdete v části [souběžných toků](#Concurrent). Vytvoření toku řízení od uzlu poslední činnost (7).  
  
### <a name="swimlanes"></a>Plaveckých drah  
 Někdy je vhodné uspořádat akce aktivity do plochy na různé objekty nebo organizační role, které provádějí akce. Tyto oblasti jsou obvykle uspořádány do sloupců a jsou volány *plaveckých drah*.  
  
- Použít čáry nebo obdélníky z **jednoduché obrazce** část sady nástrojů pro kreslení plaveckých drah nebo v jiných oblastech.  
  
- Chcete-li označit každý plavecké dráhy, vytvořte komentář a nastavte jeho **Transparent** vlastnost **True**.  
  
  Jednoduché obrazce není součástí modelu UML a nezobrazují v Průzkumníku modelů UML.  
  
##  <a name="DataFlows"></a> Popis toku dat  
 Popíšete data vstupující do a z aktivity v jednom ze dvou způsobů:  
  
-   Použití **objekt uzlu**. Toto je nejjednodušší způsob popisující informace mezi aktivity. Objekt uzlu je jako proměnné v aplikaci. Představuje něco, co se ukládá jedna nebo více hodnot, které jsou z jedné akce předávání.  
  
-   Použití **výstupní kód Pin** a **zadání kódu Pin**. Tato metoda umožňuje samostatně popisují výstup z jednu akci a vstupy do jiného. PIN kódy jsou stejné jako parametry v aplikaci. PIN kódy představují porty, které objekty může vstupu a opuštění akce.  
  
    > [!NOTE]
    >  Přehled prvků, které slouží v této části najdete v tématu Data proudí části tohoto tématu naleznete v tématu [diagramy činnosti UML: referenční](../modeling/uml-activity-diagrams-reference.md).  
  
### <a name="describing-data-flow-with-object-nodes"></a>Popis toku dat s uzly objektu  
 Většina toků řízení přenášejí data. Například tok výstupu z akce "Zákazník poskytuje podrobnosti o" představuje odkaz na dodací adresu.  
  
 Pokud chcete popsat tato data v diagramu, můžete nahradit konektor s uzel objektu a dva konektory, jak je znázorněno na následujícím obrázku.  
  
 ![Uzly objektu lze zobrazit data odesílaná mezi akcemi](../modeling/media/uml-actguidedata.png "UML_ActGuideData")  
  
 Všimněte si, že zaoblenými obdélníky, jako je například odesílání zboží, představují akce, kde dochází k zpracování. Pravoúhlými obdélníky, jako je například adresa dodávky, představují tok objektů z jedné akce do jiného.  
  
 Pojmenujte uzel objektu, která odráží role uzlu jako přenos nebo vyrovnávací paměti objektů, které tok mezi akcemi.  
  
 Můžete nastavit **typ** z objektu uzlu v okně Vlastnosti. Typ může být primitivní typ jako celé číslo, nebo je třída, rozhraní nebo výčet, který jste definovali v diagramu tříd. Například můžete vytvořit třídu adresu dodávky, s atributy ulice, Město a tak dále, společně s přidružení k jiné třídy, která má název zákazníka. Další informace najdete v tématu [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md).  
  
> [!NOTE]
>  Pokud zadáte název typu, který ještě nebyl definován, položky budou přidány pod **nespecifikované typy** v Průzkumníku modelů UML. Pokud následně definovat typ s tímto názvem v diagramu tříd, byste měli obnovit typ uzlu objektu tak, aby odkazoval na nový typ.  
  
#### <a name="buffering-data-in-object-nodes"></a>Ukládání do vyrovnávací paměti dat v uzly objektu  
 Objekt uzlu může fungovat jako vyrovnávací paměť pro více objektů. Na následujícím obrázku zobrazuje tok řízení, že uživatel přejít [vybrat více] smyčky (1) v mnoha případech, když uzel objektu zvolené položky nabídky (2) shromažďuje volby uživatele. Nakonec po dokončení jeho výběr uživatele řízení se předá do potvrzení objednávky akce (3), která přijímá úplný seznam možností z vyrovnávací paměti zvolené položky nabídky.  
  
 ![Ukládání do vyrovnávací paměti dat v uzlech objektu](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")  
  
 Můžete určit, jak jsou položky ve vyrovnávací paměti uložené nastavením vlastnosti z objektu uzlu:  
  
-   Nastavte **řazení** vlastnost:  
  
    -   **Neseřazený** k určení náhodných nebo neurčené pořadí. (Výchozí).  
  
    -   **Seřazené** k určení pořadí podle určitého klíče.  
  
    -   **FIFO** k určení pořadí první dovnitř, první ven.  
  
    -   **LIFO** k určení pořadí poslední dovnitř, první.  
  
-   Nastavte **horní mez** vlastnosti a určit maximální počet objektů, které mohou být obsaženy ve vyrovnávací paměti. Výchozí hodnota je *. To znamená, že není nijak omezený.  
  
### <a name="describing-data-flow-with-input-and-output-pins"></a>Popis toku dat s vstupní a výstupní spojky.  
 Použití **výstupní spojky** a **zadání kódu Pin** samostatně popsat výstupy z jednu akci a vstupy do jiného.  
  
 ![Vstupní a výstupní spojky jsou parametry akce](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")  
  
 Chcete-li vytvořit kód pin, klikněte na tlačítko **zadání kódu Pin** nebo **výstupní spojky** na panelu nástrojů a potom klikněte na akci. Potom můžete přesunout PIN kódu kolem akce a změňte její název. Může vytvoření vstupní a výstupní spojky na libovolný typ akce, včetně **volání akce chování**, **volání operace akce**, **odesílat signál akce**, a  **Akce události přijmout**.  
  
 Konektor mezi dva kódy PIN představuje tok, který objekt, stejně jako tomu putuje do a z objektu uzlu.  
  
 Pojmenujte každý PIN kód, který označuje roli objekty vytváří nebo přijme, jako je například název parametru.  
  
 Můžete nastavit typ objektů přenášených v **typ** vlastnost. Musí se jednat o typ, který jste vytvořili v diagramu tříd UML.  
  
 Objekty mezi připojených kódy PIN musí být kompatibilní nějakým způsobem. To může být způsobeno objekty vytvořené metodou výstupní spojky patří do vstupní kód pin typu odvozeného typu.  
  
 Případně můžete určit, že objekt flow zahrnuje transformace, která převádí data mezi typem výstupní spojky a typ vstupních PIN kód. Nejběžnější transformace tohoto druhu pouze extrahuje odpovídající část z typu větší. Příklad na obrázku předpokládá existenci transformace, která extrahuje adresou pro doručení z detaily objednávky.  
  
##  <a name="Details"></a> Definování akce podrobněji  
 Kromě použití názvu akce, aby se vyjasnilo výsledek, který by měl obvykle dosáhnout, tady jsou některé způsobů akci můžete přidat další podrobnosti:  
  
-   Zadejte podrobnější popis **tělo** vlastnost. Můžete například napsat fragment kódu programu nebo pseudo kódu nebo úplný popis dosažené výsledky.  
  
-   Nahraďte chování akce volání akce a popište své podrobné chování v rámci diagram samostatné činnosti. Zobrazit [popisující dílčí aktivity s akcemi chování volání](#Subactivities).  
  
-   Nastavte akci **místní vstupních** a **místní předpoklady** vlastností, které popisují podrobně konkrétnější jeho výsledek. Další informace najdete v tématu [definování vstupních a předpoklady](#Postcondition).  
  
###  <a name="Subactivities"></a> Popisující dílčí aktivity s akcemi chování volání  
 Popíšete podrobné chování akci s použitím diagram samostatné činnosti. Volané chování je diagram aktivity, která je reprezentována chování akce volání na diagramu hlavní činnost. Chování akce volání můžete také použít k popisu chování, jež jsou sdílena mezi různé aktivity, takže není potřeba dílčí aktivity nakreslit více než jednou.  
  
 Na následujícím obrázku, obrázek 1 ukazuje aktivitu, která má chování akce volání a Diagram 2 je znázorněný dílčí aktivity diagram, který zobrazuje jen chování.  
  
 ![Samostatná aktivita diagram zobrazuje podrobné akce](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")  
  
##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>K popisu dílčí aktivitu se chování akce volání  
  
1.  Chcete-li vytvořit diagram pro dílčí aktivitu v **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt modelování, přejděte na **přidat**a potom klikněte na tlačítko **nová položka**.  
  
2.  V **přidat novou položku** dialogovém okně **šablony** klikněte na tlačítko **Diagram činnosti** a **název** pole zadejte název, který máte v úmyslu udělit vaše **volat akci chování**.  
  
3.  Nakreslete podrobný pracovní postup pro dílčí aktivitu. To je jen chování.  
  
    -   V diagramu volané dílčí činnosti **počáteční uzel** označuje, kde začíná ovládacího prvku při vyvolání volané chování. **Poslední uzel aktivity** ukazuje, kde by měl ovládací prvek vrátí na Nadřazená aktivita.  
  
4.  Nastavte **chování** vlastnost **akce volání chování** k odkazování na diagram volané chování.  
  
    > [!NOTE]
    >  Diagram činnosti dílčí musí mít některé prvky v něm nebo diagramu nebudou k dispozici v rozevíracím seznamu pro **chování** vlastnost. Navíc ikonu trident nebude zobrazovat na vaší **akce volání chování** obrazce, dokud nenastavíte jeho **chování** vlastnost.  
  
5.  Nastavte **je synchronní** vlastnost Akce, která označuje, zda vaše aktivita čeká na dokončení volané aktivity.  
  
    -   Pokud nastavíte **je synchronní** na hodnotu false, jsou označující, že tok můžete i nadále další akce před dokončením volané aktivity. Výstup by neměl definovat PIN kódy nebo odchozích dat toky z akce.  
  
### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Popis toku dat do a z dílčích aktivity  
 Popíšete dat odesílaných do a z dílčích aktivit, stejně jako použití parametrů v softwaru.  
  
- Vytvoření vstupní a výstupní spojky (1) na chování jako volá akci pro jednotlivá data, která prochází do nebo z něj akce. Název každé z nich odpovídajícím způsobem.  
  
- V diagramu dílčí činnosti, vytvořte **uzel parametru aktivity** (2) pro každý vstupní a výstupní kód pin na volání akce. Dejte každého uzlu se stejným názvem jako jeho odpovídajícího špendlíku.  
  
  > [!NOTE]
  >  Některý uzel parametr aktivity se podobá uzel objektu. Jaký typ uzlu, který chcete zkontrolovat, klikněte pravým tlačítkem na uzel a potom klikněte na **vlastnosti**. Typ uzlu je zobrazený v záhlaví okna Vlastnosti.  
  
- V diagramu činnosti dílčí nakreslete konektory, které znázorňuje tok objektů do nebo ven z každého uzlu parametru aktivity.  
  
  ![Vážou na mapě chování volání na parametry aktivity](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")  
  
###  <a name="Postcondition"></a> Definování vstupních a předpoklady  
 Můžete použít **místní vstupních** a **místní předpoklady** vlastnosti k určení podrobně výsledku akce. Tyto vlastnosti popisují vliv akce bez popisující, jak dosáhnout efekt.  
  
 Pokud chcete nastavit tyto vlastnosti, klikněte pravým tlačítkem na akce a potom klikněte na **vlastnosti**. Zadejte hodnoty do vlastnosti v okně Vlastnosti.  
  
#### <a name="local-postconditions"></a>Místní vstupních  
 Je neplatná následná podmínka, která musí splnit, aby akce lze považovat za dokončení. V příkladu akci potvrdit pořadí může být neplatná následná:  
  
 Zákazník poskytuje kompletní a platné podrobnosti, které jsou vyžadovány pro zpracování své platební karty.  
  
 Před a po provedení akce došlo k chybě, můžete vyjádřit neplatná následná vztahu mezi stavy. Příklad:  
  
 Úrokové sazby se double byl před.  
  
 Můžete napsat vstupních ve stylu formálnější odkazující na určité atributy dat. zabývá akce. Příklad:  
  
 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`  
  
#### <a name="local-preconditions"></a>Místní předběžné podmínky  
 Předpokladem je podmínku, která by měla být pravdivá, když je připraven k zahájení akce. Akci potvrďte pořadí může být například mají předpoklad:  
  
 Zákazník zvolil alespoň jednu položku v nabídce.  
  
### <a name="describing-calls-to-operations"></a>Popis volání operací  
 Obecně platí popisuje akce, práce, která se provádí pomocí libovolné směsi osob, softwaru nebo počítače. Ale můžete použít operaci akce volání pro popis volání metody konkrétní software nebo funkce.  
  
-   Nastavte název operace akce volání k označení, jaké operace je volána a na jaké objektu nebo komponenty.  
  
-   Přidáte vstupní a výstupní spojky do volání operace akce popisují parametry a návratové hodnoty.  
  
-   Můžete nastavit **je synchronní** vlastnost Akce, která označuje, zda vaše aktivita čeká na dokončení operace.  
  
    -   Pokud nastavíte **je synchronní** na hodnotu false, jsou označující, že tok můžete i nadále další akce před názvem operace se dokončila. Výstup by neměl definovat PIN kódy nebo odchozích dat toky z akce.  
  
##  <a name="Concurrent"></a> Souběžné toků  
 Můžete použít **Forku uzel** a **připojit k uzlu** k popisu dvě či více vláken aktivit, které můžete spustit ve stejnou dobu.  
  
 ![Uzly rozvětvení a spojení zobrazení souběžných toků](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")  
  
 Vliv **Forku uzel** (1) je rozdělit do dvou nebo více vláken vlákno ovládacího prvku. Po skončení předchozí akci, můžete spustit všechny akce na straně výstup z forku.  
  
 A **připojit k uzlu** (2) spojuje souběžných vláken. Akce po **připojit k uzlu** nespustí, dokud se všechny akce, což vede k **připojit k uzlu** se dokončí.  
  
### <a name="describing-signals-and-events"></a>Signály a události  
 Zobrazit krok v procesu, který vysílá signál jako odesílat signál akce v nějaké aktivitě. Můžete zobrazit krok, který čeká určitý signál ukládat nebo událost může pokračovat v kroku jako volby přijmout akci události.  
  
 Například může zobrazit krok, který odešle objednávky a pak další krok, který musí přijmout pořadí, než ji zpracuje tomto pořadí.  
  
#### <a name="sending-a-signal"></a>Odesílání signálu  
 Použijte akci odesílat signál (3) k označení, že signál nebo zprávy určitého druhu posílá do jiných aktivit nebo procesy. Můžete určit, jaký druh zprávu, odešle název akce.  
  
-   Řízení se předá okamžitě další akce v toku řízení, pokud existuje.  
  
-   Signál akce odeslání nelze použít k popisu, jak váš proces reagovat na všechny vrácené informace. K tomuto účelu použijte samostatné akce přijímat události.  
  
-   Příchozí tok dat můžete zobrazit signál odeslat akci k označení, jaká data je možné odeslat s odchozí zprávu. Další informace najdete v tématu [popisující toku dat](#DataFlows).  
  
#### <a name="waiting-for-a-signal-or-event"></a>Čekání na signál nebo událost  
 Přijmout akci události (4) slouží k označení, že tato aktivita čeká na některé externí událost nebo příchozí zprávy. Použijte název akci k označení typu události, která čeká.  
  
-   Pokud chcete zobrazit, že vaše aktivita čeká na externí události nebo zprávy v konkrétním bodě v jeho toku, nakreslete volby přijmout akci události s příchozí tok v příslušném umístění v rámci aktivity.  
  
-   Chcete-li zobrazit, že vaše aktivity můžete reagovat na externí události nebo zprávy v okamžiku, nakreslete volby přijmout akci události bez jakékoli příchozí tok. Pokud dojde k pojmenované externí události, nové vlákno začne v aktivitách, od volby přijmout akci události.  
  
-   Volby přijmout akci události nelze použít k popisu libovolnou hodnotu vrácenou odesílateli signálu. Pro tento účel použijte samostatnou akci odesílat signál.  
  
-   Můžete zobrazit odchozí toky dat z akce, se zobrazí, jak vaše aktivita zpracovává data přijatá v signál. Pokud chcete zobrazit více než jeden výstupní tok, byste měli nastavit **IsUnmarshall** vlastnost volby přijmout akci události, což znamená, že akce analyzuje příchozí signál do jeho jednotlivé součásti. Další informace najdete v tématu [popisující toku dat](#DataFlows).  
  
### <a name="describing-multiple-data-flows"></a>Popis více dat. toky  
 Můžete nakreslit více než jeden tok řízení nebo tok objektů vycházejících z akci k označení, že více než jedno vlákno splatit po skončení akce. Účinek se podobá u forku a s tím rozdílem, že používáte kombinaci ovládací prvek a objekt toky.  
  
 Následující příklad ukazuje několik toků z a do akcí.  
  
 ![Paralelní toky objektů](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")  
  
 Po dokončení akce "Zákazník poskytuje podrobnosti" vytvoří dva objekty: "Dodávky adresu" a "údajů z platební karty." Dva objekty pro zpracování různých akcí dopředu.  
  
 Protože akce vyžaduje jeho vstupů být k dispozici, aby mohla začít, od poslední akce se nespustí, dokud nebudou dokončeny všechny akce, které vedou k němu.  
  
### <a name="streams"></a>Datové proudy  
 Použijte diagram aktivity při popisu kanálu nebo posloupnost akcí, které jsou spouštěny ve stejnou dobu a průběžně předat data z jedné akce do jiného.  
  
 Záměr v následujícím příkladu je, že každá akce mohou vytvářet objekty a pokračovat v práci. Protože nepoužívají žádné toky ovládacího prvku, každou akci můžete spustit, jakmile obdrží první objekty.  
  
 Všimněte si, že konektory v tomto příkladu toky objektů, protože všechny obsahují aspoň jeden koncový na uzlu parametr aktivity uzel objektu, nebo na vstupu nebo výstupu Pin.  
  
 ![Tok dat](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")  
  
 1. V příkladu má tři uzly parametru činností, které představují její vstupy a výstupy.  
  
 2. Uzly objektu, vstupní spojky a výstupních spojek může představovat vyrovnávací paměti. Můžete nastavit vlastnost objektu uzlu do stavu objektů může být ve vyrovnávací paměti ve stejnou dobu horní mez.  
  
 3. Chcete-li zobrazit, že datový proud rozdělí, odesílání různé objekty dolů různými větvemi můžete uzlů rozhodnutí. Komentáře nebo názvy uzlů můžete použít k vysvětlení, co je dělicí kritérium.  
  
 4. Uzly rozvětvení můžete zobrazit, že jsou provedeny dvě nebo více kopií objektů, odesílání pro souběžné zpracování.  
  
 5. Připojení k uzlům můžete zobrazit, že dva proudy zpracování jsou sloučeny zpět do jedné.  
  
### <a name="selection-and-transformation"></a>Výběr a transformace  
 Můžete určit, že jsou transformovány objekty v tok, který objekt, vybrali, nebo obojí. Tok, který objekt je tok do nebo z kódu pin nebo uzel objektu.  
  
- Transformace popisuje, jak jsou objekty zadávání tok převést na jiného typu.  
  
- Výběr popisuje, jak pouze některé objekty zadávání toku se přenáší přijímající akce.  
  
  Příklad ukazuje transformace. První akcí v diagramu 1 vytváří PSČ nebo PSČ na výstupní spojky. To je připojen k vstupní kód pin na druhou akci. Ale druhou akci očekává, že adresu plně zadaný. Převod z jednoho typu na jiný je zadán v druhou aktivitu vyhledávání adresu. To se odkazuje z vlastnosti transformace toku objektu. Aktivita vyhledávání adresa obsahuje jeden uzel parametr aktivity pro příchozí poštovní směrovací číslo místa a další uzel parametr aktivity pro odchozí úplnou adresu.  
  
  ![Objekt transformace do jiného diagramu definované](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")  
  
  Transformace nebo výběr můžete zadat dvěma způsoby:  
  
- Připojte komentář k vstupní nebo výstupní kód pin.  
  
  -   K rozlišení tohoto popisu od obecné komentáře můžete začít komentář <\<**transformace**>> nebo <\<**výběr**>>.  
  
- Zadejte transformace nebo výběr podrobně v diagramu samostatné činnosti.  
  
  -   Pokud použijete tuto metodu, připojte komentář také, aby vymazat pro čtenáře definovala transformace.  
  
##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Chcete-li určit transformace nebo výběr v diagramu samostatné činnosti  
  
1. Vytvořte nový Diagram aktivity, ve které chcete popisovat tok transformace nebo výběru.  
  
   -   V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt, přejděte na **přidat**, klikněte na tlačítko **nová položka**a potom klikněte na tlačítko **Diagram činnosti**. Poskytnout vhodný název pro tok transformace nebo výběr diagramu. Klikněte na tlačítko **přidat**.  
  
2. V novém diagramu:  
  
   1.  Vytvořte dva uzly parametru činností, jeden pro vstupního toku a jeden pro výstup.  
  
   2.  Vytvoření akcí, které jsou propojeny s toky objektů. To ukazuje, jak transformace nebo výběr funguje.  
  
3. V jakékoli diagram, ve které chcete použít transformace nebo výběr:  
  
   1.  Vytvořte tok, který objekt, to znamená, že konektor do nebo z vstupní nebo výstupní spojky, uzel objektu nebo uzlu parametru aktivity.  
  
   2.  Klikněte pravým tlačítkem na objekt tok a pak klikněte na tlačítko **vlastnosti**.  
  
   3.  V **transformace** nebo **výběr** vlastnosti, vyberte diagram, ve kterém jste zadali tok transformace nebo výběru.  
  
   Můžete také definovat výběru pro objekt uzlu a na jednotlivých vstupní a výstupní spojky. Definujte výběr aktivitu, stejně jako v předchozím postupu a poté nastavte **výběr** vlastnost uzel objektu nebo vstupní nebo výstupní kód pin.  
  
## <a name="see-also"></a>Viz také  
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Sekvenční diagramy UML: referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)   
 [Video: Zaznamenání obchodních pracovních postupů pomocí diagramy činnosti](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/)



