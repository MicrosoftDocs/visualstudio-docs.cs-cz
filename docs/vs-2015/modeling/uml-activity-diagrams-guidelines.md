---
title: 'Diagramy činnosti UML: pokyny | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 692859008891439e4af3d751306bfd3ee6d351e8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298985"
---
# <a name="uml-activity-diagrams-guidelines"></a>Diagramy činnosti UML: Pokyny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio můžete nakreslit diagram aktivity k popisu obchodního procesu nebo softwarového algoritmu jako toku práce prostřednictvím řady akcí. Tyto akce mohou provádět osoby, softwarové komponenty nebo zařízení. Ukázku videa najdete v tématu: [zachycení obchodních pracovních postupů pomocí diagramů aktivit](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows).

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Diagram činnosti UML vytvoříte tak, že v nabídce **Architektura** kliknete na **Nový UML nebo Diagram vrstev**.

 Diagram aktivity můžete použít pro mnoho účelů:

- Popisuje obchodní proces nebo tok práce mezi uživateli a systémem. Další informace najdete v tématu [Model požadavky uživatelů na uživatele](../modeling/model-user-requirements.md).

- Pro popis kroků provedených v případu použití. Další informace najdete v tématu [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).

- Popis metody, funkce nebo operace v softwaru. Další informace najdete v tématu [modelování architektury aplikace](../modeling/model-your-app-s-architecture.md).

  Vykreslení diagramu činnosti vám může pomoci vylepšit proces. Pokud se diagram existujícího procesu ukáže jako velmi složitý, můžete zvážit, jak by bylo možné proces zjednodušit.

  Referenční informace o prvcích v diagramech činnosti najdete v tématu [diagramy činnosti UML: referenční](../modeling/uml-activity-diagrams-reference.md)informace.

## <a name="Relationships"></a>Vztah k jiným diagramům
 Pokud nakreslíte diagram aktivity, který popisuje obchodní proces, nebo způsob, jakým uživatelé používají systém, můžete nakreslit diagram případu použití, který zobrazí různé zobrazení stejných informací. V diagramu případu použití vykreslíte akce jako případy použití. Udělte případům použití stejné názvy jako odpovídající akce. Výhody zobrazení případu použití vám umožní:

- Zobrazit v jednom diagramu, jak se větší akce/případy použití skládají z menších, pomocí vztahu include.

- Každou akci/případ použití připojte explicitně k uživatelům nebo externím systémům, které se podílejí na jeho spuštění.

- Kreslete hranice kolem případů akce/použití, které podporuje váš systém, nebo každou hlavní komponentu.

  Diagram činnosti můžete také nakreslit a popsat tak podrobný návrh operace softwaru.

  V diagramu činnosti můžete zobrazit tok dat předávaných mezi akcemi. Přečtěte si část [popisující tok dat](#DataFlows). Diagram aktivity ale nepopisuje strukturu dat. Pro tento účel můžete nakreslit diagram tříd UML. Informace najdete v tématu [diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Základní kroky pro vykreslování diagramů činnosti
 Podrobné pokyny pro vytvoření některého z diagramů modelování jsou popsány v tématu [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-draw-an-activity-diagram"></a>Vykreslení diagramu činnosti

1. V nabídce **Architektura** klikněte na **Nový UML nebo Diagram vrstev**.

2. V části **šablony**klikněte na **Diagram činnosti UML**.

3. Pojmenujte diagram.

4. V rámci **Přidat do projektu modelování**vyberte existující projekt modelování ve vašem řešení nebo **vytvořte nový projekt modelování**.

#### <a name="to-draw-elements-on-an-activity-diagram"></a>Kreslení prvků v diagramu činnosti

1. Přetáhněte prvky ze sady nástrojů do diagramu.

     Začněte tím, že umístíte hlavní aktivity do diagramu, připojíte je a pak přidáte konečné změny, jako jsou počáteční a konečné uzly.

    > [!NOTE]
    > Existující prvky nelze přetáhnout do diagramu z Průzkumníka modelů UML.

2. Chcete-li propojit prvky, postupujte podle následujících kroků:

    1. Na panelu nástrojů **diagramu činnosti** klikněte na **spojnice**.

    2. V diagramu klikněte na zdrojový element.

    3. Klikněte na cílový element.

        > [!NOTE]
        > Chcete-li nástroj použít několikrát, dvakrát klikněte na nástroj v sadě nástrojů.

#### <a name="to-move-an-activity-to-another-package"></a>Přesunutí aktivity do jiného balíčku

- V **Průzkumníku modelů UML**přetáhněte aktivitu do balíčku.

     \- nebo –

- V **Průzkumníku modelů UML**klikněte pravým tlačítkem myši na aktivitu a pak klikněte na **Vyjmout**. Pak klikněte pravým tlačítkem na balíček a pak klikněte na **Vložit**.

    > [!NOTE]
    > Aktivita se zobrazí v Průzkumníku modelů UML pouze při přidání prvního prvku do diagramu.

## <a name="SimpleControlFlow"></a>Popis toku řízení
 Diagram činnosti popisuje obchodní proces nebo softwarový algoritmus jako řadu akcí. Šipky konektoru ukazují, jak se ovládací prvek předává postupně z jedné akce do další. Obvykle je možné akci spustit až po dokončení předchozí akce.

 Následující obrázek představuje příklad, jak můžete zobrazit posloupnost akcí s akcemi, konektory, větvemi a smyčkami. Jednotlivé prvky jsou podrobněji vysvětleny v následujících oddílech.

 ![Jednoduchý diagram aktivity](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")

 Diagramy aktivit používají **Akce** a **konektory** k popsání systému nebo aplikace jako řady akcí s řízením postupně z jedné akce do další.

- Vytvořte **akci** (1) pro každou významnou úlohu, kterou provede uživatel, systém nebo obojí v rámci spolupráce.

  > [!NOTE]
  > Zkuste svůj proces nebo algoritmus popište pouhými několika akcemi. Pomocí **akcí chování volání** můžete definovat každou akci podrobněji v samostatném diagramu, jak je popsáno v tématu [popisujícím dílčí aktivity s akcemi chování volání](#Subactivities).

- Ujistěte se, že název každé akce jasně označuje, co obvykle dosahuje.

- Propojte akce v sekvenci pomocí **konektorů** (2).

- Každá akce končí před zahájením další akce v toku řízení. Chcete-li popsat akce, které se překrývají, použijte **uzel rozvětvení** , jak je popsáno v části [souběžné toky](#Concurrent).

  I když diagram popisuje sekvenci akcí, nepopisuje, jak se akce provádějí, nebo jak je předána řízení z jedné akce k dalšímu. Použijete-li diagram k reprezentaci obchodního procesu, může být řízení úspěšné, například když jedna osoba pošle e-mailovou zprávu na jinou. Použijete-li diagram k reprezentaci návrhu softwaru, může být ovládací prvek předán normálním tokem spuštění z jednoho příkazu na další.

### <a name="describing-decisions-and-loops"></a>Popisující rozhodnutí a smyčky

- Použijte **rozhodovací uzel** (3) k označení bodu, ve kterém výsledek rozhodnutí určuje další krok. Můžete nakreslit tolik odchozích cest, kolik chcete.

- Použijete-li diagram aktivity k definování části aplikace, měli byste definovat příplatky (4), aby bylo jasné, že by měla být provedena každá cesta. Klikněte pravým tlačítkem na konektor, klikněte na **vlastnosti**a v okně **vlastnosti** zadejte hodnotu pro pole **Guard** .

- Není vždy nutné definovat ochranné kryty. Pokud například použijete diagram aktivity k popisu obchodního procesu nebo protokolu interakce, větev definuje rozsah možností, které jsou otevřené uživateli nebo interakci s komponentami.

- Použijte **slučovací uzel** (5) k spojování dvou nebo více alternativních toků, které jsou větvení v **rozhodovacím uzlu**.

    > [!NOTE]
    > K spojování alternativních toků byste měli použít **slučovací uzel** , místo aby se toky nacházely na akci. V tomto příkladu není správné připojení z rozhodovacího uzlu přímo zpět k **příkazu pro výběr položky nabídky**. Důvodem je to, že akce se nespustí, dokud nebudou do všech příchozích konektorů doručena vlákna řízení. Proto byste měli v jedné akci přenést jenom souběžné toky. Další informace najdete v tématu [souběžné toky](#Concurrent).

- Použijte větve k popisu smyček, jak je znázorněno v příkladu.

    > [!NOTE]
    > Zkuste vnořit smyčky dobře strukturovaným způsobem, jako byste museli v kódu programu. Pokud popisujíte stávající obchodní proces, může to odhalit některé příležitosti pro jeho vylepšení.

### <a name="starting-the-activity"></a>Spuštění aktivity
 Existují dva způsoby, jak označovat vstupní body do aktivity:

- **Počáteční uzel**

     Vytvořte jeden **počáteční uzel** (6), který označuje první akci aktivity.

     Tato metoda je nejužitečnější, když popisujete dílčí aktivitu nebo pokud nemusíte explicitně určit, co iniciuje aktivitu. Například objednávka aktivity může jasně začít, když zákazník získá náročné.

- **Akceptovat uzel události**

     Vytvořte **uzly události Accept**, jak je popsáno v části [souběžné toky](#Concurrent), aby označovaly začátek vlákna, které reaguje na konkrétní událost, jako je například vstup uživatele. Neposkytněte příchozí tok do uzlu. Vynechání příchozího toku znamená, že se spustí vlákno pokaždé, když dojde k události.

     Tato metoda je nejužitečnější, když popíšete odpověď na konkrétní externí událost.

### <a name="ending-the-activity"></a>Ukončení aktivity
 Použijte **konečný uzel aktivity** (7) k označení konce aktivity.

- Když podproces řízení dosáhne **koncového uzlu aktivity**, všechny souběžné akce a dílčí aktivity aktivity budou ukončeny.

- K omezení zbytečných dalších konektorů můžete použít více než jeden konečný uzel aktivity.

### <a name="interrupting-the-activity"></a>Přerušení aktivity
 Chcete-li popsat způsob přerušení normálního toku aktivity, například pokud se uživatel rozhodne pro zrušení procesu, můžete vytvořit uzel události přijetí, který pro danou událost naslouchá. Další informace najdete v části [souběžné toky](#Concurrent). Vytvořte tok řízení z tohoto objektu na konečný uzel aktivity (7).

### <a name="swimlanes"></a>Plavecké
 Někdy je užitečné uspořádat akce aktivity do oblastí odpovídajících různým objektům nebo obchodním rolím, které provádějí akce. Tyto oblasti jsou podle konvence uspořádány ve sloupcích a nazývají se *plavecké dráhy*.

- Použijte čáry nebo obdélníky z oddílu **jednoduchých tvarů** v sadě nástrojů k nakreslení plaveckých drah nebo jiných oblastí.

- Chcete-li popsat každou plaveckou dráhu, vytvořte komentář a nastavte jeho **průhlednou** vlastnost na **hodnotu true**.

  Jednoduché tvary netvoří součást modelu UML a nezobrazují se v Průzkumníku modelů UML.

## <a name="DataFlows"></a>Popisující tok dat
 Data, která jsou předávána a z aktivity, lze popsat dvěma způsoby:

- Použijte **uzel objektu**. Toto je nejjednodušší způsob, jak popsat informace toku mezi aktivitami. Uzel objektu je jako proměnná v programu. Představuje něco, co ukládá jednu nebo více hodnot, které jsou předány z jedné akce do druhé.

- Použijte **Výstupní kód PIN** a **vstupní PIN kód**. Tato metoda umožňuje samostatně popsat výstupy z jedné akce a vstupů do jiné. PIN kódy jsou jako parametry v programu. PIN kódy označují porty, kde můžou objekty zadat a opustit akci.

    > [!NOTE]
    > Přehled prvků, které jsou použity v této části, naleznete v části toky dat v tématu viz [diagramy činnosti UML: Reference](../modeling/uml-activity-diagrams-reference.md).

### <a name="describing-data-flow-with-object-nodes"></a>Popis toku dat pomocí uzlů objektů
 Většina řídicích toků provádí data. Například výstupní tok z akce "informace o zákaznících" obsahuje odkaz na dodací adresu.

 Chcete-li popsat tato data v diagramu, můžete změnit konektor pomocí uzlu objektu a dva konektory, jak je znázorněno na následujícím obrázku.

 ![Uzly objektů mohou zobrazovat data předávaná mezi akcemi.](../modeling/media/uml-actguidedata.png "UML_ActGuideData")

 Všimněte si, že obdélníky zaoblených rohů, jako je například expediční zboží, reprezentují akce, při kterých probíhá zpracování. Čtvercové rohové obdélníky, jako je adresa pro dodávku, reprezentují tok objektů od jedné akce k druhé.

 Přiřaďte uzlu objektu název, který odráží roli uzlu jako trubku nebo vyrovnávací paměť objektů, které jsou mezi akcemi toku.

 Můžete nastavit **typ** uzlu objektu v okno Vlastnosti. Typ může být primitivní typ, například celé číslo nebo třída, rozhraní nebo výčet, které jste definovali v diagramu tříd. Můžete například vytvořit adresu dodávky třídy s atributy ulice adresa, město a tak dále, spolu s přidružením k jiné třídě s názvem Customer. Další informace najdete v tématu [diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md).

> [!NOTE]
> Pokud zadáte název typu, který ještě nebyl definován, položka se přidá do **nespecifikovaných typů** v PRŮZKUMNÍKU modelů UML. Pokud následně definujete typ daného názvu v diagramu tříd, měli byste obnovit typ uzlu objektu tak, aby odkazoval na nový typ.

#### <a name="buffering-data-in-object-nodes"></a>Ukládání dat do vyrovnávací paměti v uzlech objektů
 Uzel objektu může fungovat jako vyrovnávací paměť pro více objektů. Na následujícím obrázku tok řízení ukazuje, že uživatel může přejít kolem smyčky [Choose More] (1) mnohokrát, zatímco zvolený uzel objekt položky nabídky (2) shromáždí volby uživatele. Nakonec, když uživatel dokončí svůj výběr, řízení se předá do akce potvrdit objednávku (3), která přijme úplný seznam voleb z vybrané vyrovnávací paměti položek nabídky.

 ![Ukládání dat do vyrovnávací paměti v uzlech objektů](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")

 Nastavením vlastností uzlu objektu můžete určit způsob ukládání položek ve vyrovnávací paměti:

- Nastavte vlastnost **řazení** :

  - **Neseřazeno** pro zadání náhodného nebo nezadaného pořadí. (Výchozí.)

  - **Objednáno** pro určení pořadí podle konkrétního klíče.

  - **FIFO** pro určení pořadí prvního vstupu, první ven.

  - Metoda **LIFO** pro určení pořadí, ve kterém se má pořídit.

- Nastavte vlastnost **horní mez** tak, aby určovala maximální počet objektů, které mohou být obsaženy ve vyrovnávací paměti. Výchozí hodnota je *. To znamená, že neexistuje žádné omezení.

### <a name="describing-data-flow-with-input-and-output-pins"></a>Popis toku dat pomocí vstupních a výstupních spojek
 Použijte **Výstupní kód PIN** a **vstupní kód PIN** pro samostatnou popsání výstupů z jedné akce a vstupů do jiné.

 ![Vstupní a výstupní kolíky jsou parametry akce.](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")

 Pokud chcete vytvořit kód PIN, klikněte na panelu nástrojů na **vstupní PIN** nebo **Výstupní kód PIN** a pak klikněte na akci. Potom můžete přesunout kód PIN kolem hranice akce a změnit jeho název. Vstupní a výstupní PIN kód můžete vytvořit na jakémkoli typu akce, včetně **akcí chování volání**, akcí **volání operací**, **akcí odeslání signálu**a akcí **přijetí událostí**.

 Konektor mezi dvěma kolíky představuje tok objektu, stejně jako toky do a z uzlu objektu.

 Každému PIN kódu zadejte název, který indikuje roli objektů, které vytváří nebo přijímá, jako je název parametru.

 Můžete nastavit typ objektů přenesených v rámci vlastnosti **typ** . Musí se jednat o typ, který jste vytvořili v diagramu tříd UML.

 Tok objektů mezi připojenými kolíky musí být nějakým způsobem kompatibilní. To může být způsobeno tím, že objekty vytvořené výstupním kódem PIN patří odvozenému typu vstupního kódu PIN.

 Případně můžete určit, že tok objektů zahrnuje transformaci, která převádí data mezi typem výstupního kódu PIN a typem vstupního PIN kódu. Nejběžnější transformace tohoto druhu pouze extrahuje příslušnou část z většího typu. Příklad na obrázku implikuje existenci transformace, která extrahuje dodací adresu z podrobností objednávky.

## <a name="Details"></a>Podrobněji definovat akci
 Kromě použití názvu akce pro vymazání výsledku, který by měl být obvykle dosažen, zde je několik způsobů, jak můžete do akce přidat další podrobnosti:

- Napište podrobnější popis vlastnosti **body** . Můžete například napsat fragment kódu programu nebo pseudo kód nebo úplný popis dosažených výsledků.

- Nahraďte akci akcí volání chování a popište její podrobné chování v rámci samostatného diagramu činnosti. Viz [popisující dílčí aktivity s akcemi chování volání](#Subactivities).

- Nastavením vlastností **místních následné podmínky** a **místních předběžných** hodnot akce popište výsledek podrobněji. Další informace najdete v tématu [Definování následné podmínky a předběžných podmínek](#Postcondition).

### <a name="Subactivities"></a>Popis dílčích aktivit s akcemi chování volání
 Podrobné chování akce můžete popsat pomocí samostatného diagramu aktivity. Volaný chování je diagram aktivity, který je reprezentován v hlavním diagramu aktivity pomocí akce chování volání. Akci volání chování můžete také použít k popisu chování, které je sdíleno mezi různými aktivitami, takže nemusíte kreslit dílčí aktivitu několikrát.

 Na následujícím obrázku znázorňuje diagram 1 aktivitu, která má akci volání chování a diagram 2 znázorňuje diagram dílčí aktivity, který zobrazuje volané chování.

 ![Diagram samostatné aktivity zobrazuje podrobné akce.](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")

##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Popis dílčí aktivity s akcí volání chování

1. Chcete-li vytvořit diagram pro dílčí aktivitu, v **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt modelování, přejděte na **Přidat**a klikněte na **Nová položka**.

2. V dialogovém okně **Přidat novou položku** v části **šablony** klikněte na možnost **Diagram aktivity** a do pole **název** zadejte název, který chcete poskytnout **akci chování volání**.

3. Nakreslete podrobný pracovní postup pro dílčí aktivitu. Toto chování se nazývá.

    - V diagramu s názvem Sub Activity označuje **počáteční uzel** , kde se ovládací prvek spustí při vyvolání volaného chování. **Konečný uzel aktivity** ukazuje, kde by se měl ovládací prvek vrátit k nadřazené aktivitě.

4. Nastavte vlastnost **chování** **akce volání chování** na odkaz na pojmenovaný diagram chování.

    > [!NOTE]
    > Diagram podaktivity musí obsahovat některé prvky nebo diagram nebude v rozevíracím seznamu pro vlastnost **chování** k dispozici. Kromě toho se ikona Trident nezobrazí na obrazci **akce chování volání** , dokud nenastavíte jeho vlastnost **chování** .

5. Nastavte vlastnost **je synchronní** pro akci, která určuje, zda vaše aktivita čeká na dokončení volané aktivity.

    - Pokud nastavíte hodnotu **synchronní** na false, znamená to, že tok může pokračovat další akcí před dokončením volané aktivity. V rámci této akce byste neměli definovat výstupní spojky ani toky odchozích dat.

### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Popis toku dat a z dílčích aktivit
 Můžete popsat tok dat v dílčích aktivitách a v nich stejným způsobem, jakým používáte parametry v softwaru.

- Vytvořte vstupní a výstupní kolíky (1) na akci volaného chování pro každou část dat, která se přetéká do akce nebo z ní. Pojmenujte je odpovídajícím způsobem.

- V diagramu podaktivity vytvořte pro každý vstupní a výstupní kód na akci volání **uzel parametr aktivity** (2). Dejte každému uzlu stejný název jako jeho odpovídající kód PIN.

  > [!NOTE]
  > Uzel parametru aktivity se podobá uzlu objektu. Chcete-li zjistit, jaký typ uzlu chcete vyhledat, klikněte pravým tlačítkem myši na uzel a potom klikněte na příkaz **vlastnosti**. Typ uzlu je zobrazen v záhlaví okno Vlastnosti.

- V diagramu dílčí aktivity nakreslete spojnice zobrazující tok objektů do nebo z každého uzlu parametru aktivity.

  ![PIN kódy v chování volání mapují parametry aktivity.](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")

### <a name="Postcondition"></a>Definování následné podmínky a předběžných podmínek
 Pomocí **místních vlastností následné podmínky** a **místních předběžných podmínek** můžete zadat podrobné informace o výsledku akce. Tyto vlastnosti popisují účinek akce bez popisu způsobu dosažení tohoto efektu.

 Tyto vlastnosti nastavíte tak, že kliknete pravým tlačítkem myši na akci a potom kliknete na **vlastnosti**. Zadejte hodnoty do vlastností v okno Vlastnosti.

#### <a name="local-postconditions"></a>Místní následné podmínky
 Následná podmínka je podmínka, která musí být splněna před tím, než bude možné akci považovat za dokončenou. V příkladu akce potvrdit objednávku může být následná podmínka:

 Zákazník zadal kompletní a platné podrobnosti, které jsou požadovány ke zpracování platební karty.

 Následná podmínka může vyjádřit relaci mezi stavy před a poté, co došlo k akci. Příklad:

 Úroková sazba se zdvojnásobí.

 Následné podmínky můžete napsat v lépe formálním stylu, který odkazuje na konkrétní atributy dat, se kterými se v akcích zabývá. Příklad:

 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`

#### <a name="local-preconditions"></a>Místní předběžné podmínky
 Podmínkou je podmínka, která by měla být pravdivá, pokud je akce připravena k zahájení. Například akce potvrdit objednávku může mít předběžnou podmínku:

 Zákazník vybral v nabídce alespoň jednu položku.

### <a name="describing-calls-to-operations"></a>Popisující volání operací
 Obecně akce popisuje práci, kterou provádí jakákoli kombinace lidí, softwaru nebo počítačů. Ale můžete použít akci operace volání k popisu volání konkrétní metody nebo funkce softwaru.

- Nastavte název akce operace volání, abyste označili, která operace je volána, a na jaký objekt nebo komponentu.

- Přidejte vstupní a výstupní spojky k akci operace volání, abyste popsali parametry a návratové hodnoty.

- Můžete nastavit vlastnost **je synchronní** pro akci, která určuje, zda vaše aktivita čeká na dokončení operace.

  - Pokud je nastavená hodnota **synchronní** na false, znamená to, že tok může pokračovat další akcí před dokončením volané operace. V rámci této akce byste neměli definovat výstupní spojky ani toky odchozích dat.

## <a name="Concurrent"></a>Souběžné toky
 **Uzel rozvětvení** a **spojovací uzel** můžete použít k popisu dvou nebo více podprocesů aktivity, které mohou být spuštěny ve stejnou dobu.

 ![Větvení a spojování uzlů zobrazují souběžné toky](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")

 Účinek **uzlu rozvětvení** (1) slouží k rozdělení vlákna ovládacího prvku do dvou nebo více vláken. Po ukončení předchozí akce může začít všechny akce na straně výstupu rozvětvení.

 **Uzel spojení** (2) přinese souběžná vlákna dohromady. Akce po **spojovacím uzlu** se nemusí spustit, dokud nebudou dokončeny všechny akce vedoucí k **uzlu JOIN** .

### <a name="describing-signals-and-events"></a>Popisující signály a události
 Můžete zobrazit krok v procesu, který odešle signál jako akci odeslání signálu v aktivitě. Můžete zobrazit krok, který čeká na konkrétní signál nebo událost předtím, než může krok pokračovat jako akce přijetí události.

 Můžete například zobrazit krok, který odešle objednávku a pak jiný krok, který musí obdržet objednávku před jejím zpracováním.

#### <a name="sending-a-signal"></a>Posílá se signál.
 Použijte akci odeslání signálu (3) k označení toho, že signál nebo zpráva nějakého druhu jsou odesílány jiným aktivitám nebo procesům. Použijte název akce, chcete-li určit, jaký druh zprávy odesílá.

- Řízení se okamžitě předává do další akce v toku řízení, pokud existuje.

- Akci odeslání signálu nemůžete použít k popsání způsobu reakce procesu na všechny vrácené informace. Uděláte to tak, že použijete samostatnou akci přijmout událost.

- Tok příchozích dat můžete zobrazit pro akci odeslání signálu a určit, jaká data se mají odeslat pomocí odchozí zprávy. Další informace najdete v tématu [popisujícím tok dat](#DataFlows).

#### <a name="waiting-for-a-signal-or-event"></a>Čekání na signál nebo událost
 Použijte akci přijmout událost (4) k označení toho, že tato aktivita čeká na určitou externí událost nebo příchozí zprávu. Použijte název akce, chcete-li určit typ události, pro kterou bude čekat.

- Pokud chcete zobrazit, že vaše aktivita čeká na externí událost nebo zprávu v určitém místě v toku, nakreslete na příslušné místo aktivity akci přijmout událost se vstupním tokem.

- Pokud chcete zobrazit, že vaše aktivita může kdykoli reagovat na externí událost nebo zprávu, vykreslete akci přijmout událost bez příchozího toku. Když dojde k pojmenované externí události, zahájí se v aktivitě nové vlákno, od akce přijmout událost.

- Akci přijmout událost nelze použít k popisu jakékoli hodnoty vrácené odesílateli signálu. Pro tento účel použijte akci samostatného signálu pro odeslání.

- Z akce můžete zobrazit toky odchozích dat, které ukazují, jak vaše aktivity zpracovávají data přijatá v signálu. Pokud chcete zobrazit více než jeden výstupní tok, měli byste nastavit vlastnost **IsUnmarshall** akce přijmout událost, která indikuje, že akce analyzuje příchozí signál na samostatné součásti. Další informace najdete v tématu [popisujícím tok dat](#DataFlows).

### <a name="describing-multiple-data-flows"></a>Popisování více toků dat
 Můžete nakreslit více než jeden tok řízení nebo tok objektů z akce k označení toho, že více než jedno vlákno se po ukončení akce vykoná. Efekt se podobá rozvětvení s tím rozdílem, že můžete použít kombinaci toků ovládacích prvků a objektů.

 Následující příklad ukazuje více toků z a do akcí.

 ![Toky paralelních objektů](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")

 Když se akce "zákaznické poskytování podrobností" dokončí, vytvoří se dva objekty: "adresa pro dodávku" a "Podrobnosti o kreditní kartě". Tyto dva objekty přecházejí ke zpracování různými akcemi.

 Vzhledem k tomu, že akce vyžaduje, aby všechny vstupy byly k dispozici před spuštěním, poslední akce se nespustí, dokud nebudou dokončeny všechny akce, které jí vedly.

### <a name="streams"></a>Datové proudy
 Diagram aktivity můžete použít k popsání kanálu nebo řady akcí, které se spouštějí současně, a nepřetržitě předávat data z jedné akce do druhé.

 Záměrem v následujícím příkladu je, že každá akce může vystavovat objekty a pokračovat v práci. Vzhledem k tomu, že neexistují žádné řídicí toky, každá akce může začít ihned po přijetí svých prvních objektů.

 Všimněte si, že konektory v tomto příkladu jsou toky objektů, protože všechny mají alespoň jeden konec na uzlu parametru aktivity, uzel objektu nebo vstupní nebo výstupní PIN kód.

 ![Tok dat](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")

 1. Příklad obsahuje tři uzly parametrů aktivity, které reprezentují jeho vstupy a výstupy.

 2. Uzly objektů, vstupní kolíky a výstupní kódy PIN mohou představovat vyrovnávací paměti. Můžete nastavit horní mez vlastnosti uzlu objektu na stav, kolik objektů může být ve vyrovnávací paměti ve stejnou dobu.

 3. Pomocí uzlů pro rozhodování můžete zobrazit, že je tok vydělený, odesláním různých objektů do různých větví. Pomocí komentářů nebo názvů uzlů můžete vysvětlit, co je dělené kritérium.

 4. Uzly rozvětvení lze použít k zobrazení, zda jsou vytvořeny dvě nebo více kopií objektů a jejich posílání pro souběžné zpracování.

 5. Uzly JOIN můžete použít k zobrazení, že dva datové proudy zpracování jsou sloučeny zpět do jedné.

### <a name="selection-and-transformation"></a>Výběr a transformace
 Můžete určit, že objekty v toku objektů jsou transformované, vybrané nebo oboje. Tok objektu je tok do nebo z kódu PIN nebo uzlu objektu.

- Transformace popisuje způsob, jakým jsou objekty, které vstupují do toku, převedeny na jiný typ.

- Výběr popisuje, jak jsou do přijímací akce přenášeny pouze některé objekty, které vstupují do toku.

  Příklad ukazuje transformaci. První akce v diagramu 1 vytvoří poštovní směrovací číslo nebo PSČ na výstupním PIN kódu. To je připojeno ke vstupnímu PIN kódu při druhé akci. Ale druhá akce očekává úplnou adresu. Konverze z jednoho typu na jiný je určena v druhé aktivitě, vyhledávání adres. Toto je odkazováno z vlastnosti Transform toku objektu. Aktivita vyhledávání adres obsahuje jeden uzel parametrů aktivity pro příchozí poštovní směrovací číslo a další uzel parametru aktivity pro odchozí úplnou adresu.

  ![Transformace objektů definovaná v jiném diagramu](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")

  Transformaci nebo výběr můžete zadat dvěma způsoby:

- Připojí komentář ke vstupnímu nebo výstupnímu PIN kódu.

  - Pokud chcete tento popis odlišit od obecného komentáře, můžete začít komentovat <\<**transformaci**> > nebo <\<**výběru**> >.

- V samostatném diagramu aktivity zadejte transformaci nebo výběr podrobněji.

  - Pokud použijete tuto metodu, připojte komentář také k tomu, aby bylo jasné, že byla transformace definována.

##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Určení transformace nebo výběru v diagramu samostatné aktivity

1. Vytvořte nový diagram aktivity, ve kterém můžete popsat transformaci nebo tok výběru.

   - V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt, přejděte na **Přidat**, klikněte na **Nová položka**a pak klikněte na **Diagram aktivity**. Poskytněte diagramu vhodný název pro transformaci nebo tok výběru. Klikněte na tlačítko **Add** (Přidat).

2. V novém diagramu:

   1. Vytvořte dva uzly parametrů aktivity, jednu pro vstupní tok a jednu pro výstup.

   2. Vytvoří akce propojené s toky objektů. To ukazuje, jak transformace nebo výběr funguje.

3. V jakémkoli diagramu, kde chcete použít transformaci nebo výběr:

   1. Vytvořte tok objektu, to znamená konektor k vstupnímu nebo výstupnímu PIN kódu, uzel objektu nebo uzel parametru aktivity.

   2. Klikněte pravým tlačítkem na tok objektů a pak klikněte na **vlastnosti**.

   3. Ve vlastnosti **transformace** nebo **výběru** vyberte diagram, ve kterém jste určili transformaci nebo tok výběru.

   Můžete také definovat výběr pro uzel objektu a na jednotlivé vstupní a výstupní kódy PIN. Definujte aktivitu výběru jako v předchozím postupu a pak nastavte vlastnost **výběru** uzlu objektu nebo vstupní nebo výstupní PIN kód.

## <a name="see-also"></a>Viz také
 Diagramy sekvence UML pro [Úpravy modelů a diagramů](../modeling/edit-uml-models-and-diagrams.md) UML [: referenční diagramy](../modeling/uml-sequence-diagrams-reference.md) [komponent UML](../modeling/uml-component-diagrams-reference.md) : referenční diagramy [případů použití](../modeling/uml-use-case-diagrams-reference.md) UML: referenční diagramy [tříd](../modeling/uml-class-diagrams-reference.md) UML: Referenční dokumentace k diagramům [komponent](../modeling/uml-component-diagrams-reference.md) UML: referenční [video: zachycení obchodních pracovních postupů pomocí diagramů činnosti](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows)
