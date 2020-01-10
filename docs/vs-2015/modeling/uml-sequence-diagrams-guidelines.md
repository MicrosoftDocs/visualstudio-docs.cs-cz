---
title: 'Sekvenční diagramy UML: pokyny | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cdd853307bdea28c48762a6a3f0416e698b577ff
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850126"
---
# <a name="uml-sequence-diagrams-guidelines"></a>Sekvenční diagramy UML: Pokyny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete nakreslit *sekvenční diagram* pro zobrazení interakce. Interakce je posloupnost zpráv mezi typickými instancemi tříd, komponent, subsystémů nebo Actors.

 Sekvenční diagramy UML jsou součástí modelu UML a existují pouze v rámci projektů modelování UML. Chcete-li vytvořit sekvenční diagram UML, v nabídce **Architektura** klikněte na **Nový UML nebo Diagram vrstev**. Další informace o [elementech sekvenčního diagramu UML](../modeling/uml-sequence-diagrams-reference.md) nebo [diagramech modelování UML](../modeling/edit-uml-models-and-diagrams.md) najdete v části Obecné. Ukázku videa najdete v tématu [náčrtace interakcí pomocí sekvenčních diagramů (2010)](https://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>V tomto tématu
 [Použití sekvenčních diagramů UML](#Using)

 [Základní kroky pro vykreslování sekvenčních diagramů](#BasicSteps)

 [Vytváření a používání jednoduchých sekvenčních diagramů](#Simple)

 [Třídy a životnosti](#ClassesAndLifelines)

 [Vytváření opakovaně použitelných sekvencí interakce](#Multiple)

 [Sbalení skupin životností](#Collapse)

 [Popis řídicích struktur s fragmenty](#Fragments)

## <a name="Using"></a>Použití sekvenčních diagramů UML
 Sekvenční diagramy můžete použít k nejrůznějším účelům na různých úrovních v podrobnostech o programu. Typickými případy při vykreslování sekvenčního diagramu jsou tyto:

- Pokud máte diagram případu použití, který shrnuje uživatele vašeho systému a jejich cíle, můžete nakreslit sekvenční diagramy, které popisují, jak hlavní součásti systému spolupracují na splnění cíle každého případu použití. Další informace najdete v tématu [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).

- Pokud jste identifikovali zprávy přicházející v rozhraní komponenty, můžete nakreslit sekvenční diagramy, abyste popsali, jak vnitřní části komponenty pracují, aby dosáhly výsledku vyžadovaného pro každou příchozí zprávu. Další informace najdete v tématu [diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md).

  Sestavování sekvenčních diagramů má několik výhod:

- Můžete snadno zjistit, jak jsou úlohy distribuované mezi komponentami.

- Můžete identifikovat vzorce interakce, které usnadňují aktualizaci softwaru.

## <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům
 Sekvenční diagramy UML můžete použít spolu s dalšími diagramy několika způsoby.

#### <a name="lifelines-and-types"></a>Životnosti a typy
 Životnosti, která kreslíte do sekvenčního diagramu, může představovat typické instance komponent nebo tříd v systému. Můžete vytvořit životnosti z typů a typů z životností a zobrazit typy v diagramech tříd UML a diagramech komponent UML. Další informace naleznete v tématu [třídy a životnosti](#ClassesAndLifelines).

#### <a name="parameter-types"></a>Typy parametrů
 Můžete také popsat v diagramu tříd UML typy parametrů a vrácené hodnoty, které byly použity ve zprávách odesílaných mezi životnosti.

#### <a name="use-case-details"></a>Podrobnosti případu použití
 Případ použití představuje cíl uživatele spolu s posloupností kroků pro dosažení cíle. Pořadí kroků lze popsat několika způsoby. Jednou z možností je nakreslit sekvenční diagram, který znázorňuje interakce mezi uživateli a hlavními součástmi systému. Další informace najdete v tématu [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Základní kroky pro vykreslování sekvenčních diagramů
 Úplný seznam prvků v sekvenčních diagramech najdete v tématu [sekvenční diagramy UML: referenční informace](../modeling/uml-sequence-diagrams-reference.md).

> [!NOTE]
> Podrobné pokyny k vytvoření některého z diagramů modelování jsou popsány v tématu [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-sequence-diagram"></a>Vytvoření sekvenčního diagramu

1. V nabídce **Architektura** klikněte na **Nový UML nebo Diagram vrstev**.

2. V části **šablony**klikněte na **sekvenční diagram UML**.

3. Pojmenujte diagram.

4. V nabídce **Přidat k projektu modelování**vyberte existující projekt modelování v řešení nebo **vytvořte nový projekt modelování**a pak klikněte na tlačítko **OK**.

    Zobrazí se nový sekvenční diagram se sadou nástrojů **sekvenčního diagramu** . Sada nástrojů obsahuje požadované prvky a konektory.

   ![Části sekvenčního diagramu](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>Nakreslení sekvenčního diagramu

1. Přetáhněte **životnosti** (1) z **panelu nástrojů** do diagramu, aby představovala instance tříd, komponent, aktérů nebo zařízení.

    > [!NOTE]
    > Můžete také vytvořit životnost přetažením existující třídy, rozhraní, objektu actor nebo komponenty z **Průzkumníka modelů UML** do diagramu. Tím se vytvoří životnost představující instanci zvoleného typu.

2. Nakreslete zprávy, abyste viděli, jak životnost spolupracuje, aby dosáhla konkrétního cíle.

     Chcete-li vytvořit zprávu (3, 4, 6, 7), klikněte na nástroj zprávy. Pak klikněte na čas odeslání v místě, kde chcete, aby se zpráva spustila, a pak klikněte na příjem životnosti.

     V přijímací životnosti se zobrazí výskyt spuštění (5). Výskyt spuštění představuje časový úsek, během kterého instance provádí metodu. Můžete vytvořit další zprávy, které začínají z výskytu spuštění.

3. Chcete-li zobrazit zprávu, která pochází z neznámého zdroje události (9) nebo všesměrová vysílání pro neznámé příjemce (10), vykreslete asynchronní zprávu z nebo do prázdného místa v diagramu. Tyto zprávy se nazývají *nalezené zprávy* (9) a *ztracené zprávy* (10).

    > [!NOTE]
    > Chcete-li přesunout skupinu životností, která ztratila nebo našla zprávy, použijte následující postup, chcete-li vybrat životnosti před jejich přesunutím: nakreslete obdélník kolem těchto životností nebo stiskněte a podržte klávesu **CTRL** a klikněte na jednotlivé životnosti. Pokud použijete **možnost Vybrat vše** nebo **CTRL** **+a** k výběru všech životností a jejich přesunutí, ztratí se všechny ztracené nebo nalezené zprávy připojené k těmto životnostem. Pokud k této situaci dojde, můžete tyto zprávy přesunout samostatně.

4. Nakreslete sekvenční diagramy pro každou hlavní zprávu do stejné součásti nebo systému.

#### <a name="to-change-the-order-of-messages"></a>Změna pořadí zpráv

- Přetáhněte zprávu v její životnosti nahoru nebo dolů. Můžete ho přetáhnout přes jiné zprávy nebo do bloku spuštění nebo z něj.

     \- nebo –

- Klikněte na zprávu a pomocí kláves ŠIPKA **nahoru** a šipka **dolů** upravte polohu zprávy. Pro změnu pořadí zpráv použijte **SHIFT + šipka nahoru** a **SHIFT + šipka dolů** .

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Přesunutí nebo zkopírování sekvencí zpráv v sekvenčním diagramu

1. Klikněte pravým tlačítkem na zprávu (3, 4) a pak klikněte na **Kopírovat**.

2. Klikněte pravým tlačítkem myši na výskyt spuštění (5) nebo životnost (1), ze které chcete odeslat novou zprávu, a potom klikněte na tlačítko **Vložit**. Pokud chcete, může být nový odesilatel v jiném diagramu.

     Kopie zprávy a všechny její dceřiné zprávy jsou přidány na konec spuštění nebo na konec životnosti.

    > [!NOTE]
    > Vložená zpráva se vždycky zobrazuje na konci výskytu nebo životnosti spuštění. Po vložení ji můžete přetáhnout do předchozí pozice.

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Zobrazení a úprava textu podpisu zprávy

- Aby byl text podpisu viditelný, musí být cílový životnost svázána nebo mapována na typy. K provedení této úlohy proveďte jeden z následujících kroků:

  - Klikněte pravým tlačítkem na životnost a pak zvolte **vytvořit třídu**.

     -nebo-

  - Vyberte životnost, stiskněte **F4**a potom v okně **vlastnosti** nastavte vlastnost **typ** na existující typ nebo zadejte název nového typu. Klikněte pravým tlačítkem myši na popisek zprávy a zvolte možnost **vytvořit operaci**.

    Text podpisu se zobrazí pod popiskem zprávy. Text podpisu teď můžete upravit. Další informace naleznete v tématu [třídy a životnosti](#ClassesAndLifelines).

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Vylepšení rozložení sekvenčního diagramu

- Klikněte pravým tlačítkem myši na prázdnou část diagramu a potom klikněte na tlačítko **změnit uspořádání rozložení**.

- Chcete-li operaci vrátit zpět, klikněte na tlačítko **Upravit**a pak klikněte na tlačítko **zpět**.

#### <a name="to-change-the-package-that-owns-the-interaction"></a>Změna balíčku, který vlastní interakci

1. V **Průzkumníku modelů UML**Najděte interakce, které sekvenční diagram zobrazuje.

    > [!NOTE]
    > Interakce se nezobrazí v **Průzkumníkovi modelů UML** , dokud nepřidáte první životnost do sekvenčního diagramu.

2. Přetáhněte interakci do balíčku.

     \- nebo –

     Klikněte pravým tlačítkem myši na interakci a pak klikněte na **Vyjmout**. Klikněte pravým tlačítkem na balíček a pak klikněte na **Vložit**.

## <a name="Simple"></a>Vytváření a používání jednoduchých sekvenčních diagramů
 Nejjednodušší a nejčastěji používaná forma sekvenčního diagramu obsahuje jenom životnosti a zprávy. Diagram tohoto druhu vám umožňuje zobrazit jasně typickou posloupnost interakcí mezi objekty v návrhu nebo mezi vaším systémem a jeho uživateli. To je často dostatečné, abychom vám pomohli diskutovat a sdělit návrh.

 Tady je několik věcí, které je potřeba vzít v úvahu při vykreslování jednoduchého sekvenčního diagramu.

### <a name="types-of-message"></a>Typy zpráv
 Existují tři nástroje, které můžete použít k vytvoření zpráv.

- Použijte **synchronní** nástroj k popisu interakce, ve které odesilatel čeká na vrácení odpovědi příjemce (3).

     Na konci spuštění se zobrazí **<\<vrátí > >** šipka. Indikuje vrácení ovládacího prvku odesílateli.

- Pomocí **asynchronního** nástroje můžete popsat interakce, ve kterých může odesílatel pokračovat bez čekání na příjemce (4).

- Pomocí nástroje pro **Vytvoření** popište interakci, ve které odesilatele vytvoří příjemce (8).

     Zpráva vytvořit by měla být první zprávou, kterou příjemce obdrží.

### <a name="annotating-the-interactions"></a>Přidávání poznámek k interakcím
 Pokud chcete podrobnější informace o sekvenci, můžete **Komentář** umístit kamkoli do diagramu.

 Pomocí **odkazů na komentáře**můžete propojit komentář k životnosti, spuštění, použití interakce a fragmentům.

> [!CAUTION]
> Pokud chcete k určitému bodu v sekvenci připojit komentář, propojte jej s výskytem spuštění, používáním interakce nebo fragmentem. Nepřipojujte ho k životnosti, protože v takovém případě není nadále připojená ke správnému bodu v sekvenci.

 Použijte komentář k těmto akcím:

- Všimněte si, co se dosáhlo u klíčových bodů v sekvenci. To pomáhá čtenářům zobrazit cíle interakcí.

- Popište celkový cíl celé sekvence. Připojte komentář k počátečnímu výskytu spuštění nebo nechte nepřipojený. Například "zákazník vybral položky z nabídky a byl mu přidělena cena."

- Popište zodpovědnosti každé životnosti. Připojte komentář k životnosti. Například "třídění manažera shromažďuje nabídky zákazníka."

- Všimněte si výjimek nebo alternativ, které mohou být provedeny jako alternativa k typickému zobrazené sekvenci. Například "zákazník se může rozhodnout pro přeskočení zbytku této sekvence".

  - Zvažte použití fragmentů jako formální alternativy k tomuto druhu poznámky. Viz [Popis řídicích struktur s fragmenty](#Fragments)

## <a name="deciding-the-scope-of-the-diagram"></a>Rozhodnutí o rozsahu diagramu
 Je důležité mít jasné informace o tom, co diagram má zobrazit.

#### <a name="initiating-event"></a>Událost inicializace
 Každý diagram by měl zobrazit sekvenci interakcí, které jsou výsledkem jedné události zahájení. Může to být například:

- Uživatel, který zahajuje případ použití, například otevření webové stránky pro nákup krupice.

- Zpráva z jedné součásti systému do druhé, například dotaz na dostupnost položek, které chce zákazník koupit.

- Událost aktivovaná změnou stavu, například akcie položky pod prahovou hodnotou.

#### <a name="level-of-detail"></a>Úroveň podrobností
 Sekvenční diagramy mohou zobrazovat různé úrovně podrobností. Úroveň podrobností ve dvou oddělených dimenzích je možné určit téměř nezávisle:

 Životnosti mohou představovat jednu z těchto úrovní podrobností:

- Objekty v kódu programu, které buď existují, nebo vyvíjíte.

- Komponenty nebo jejich dílčí komponenty, obvykle vynechává Facade, proxy a další mechanismy připojení.

- Váš systém a externí objekty actor

  Zprávy mohou představovat jednu z těchto úrovní podrobností:

- Softwarové zprávy v kódu programu, v rozhraní API nebo ve webovém rozhraní.

- Transakce nebo dílčí transakce, například mezi uživateli a systémem nebo mezi kódem a databází.

- Používejte případy – hlavní interakce mezi uživateli a systémem.

  Bez ohledu na to, zda zkoumáte existující kód nebo navrhujete nový návrh, je často užitečné vykreslovat a diskutovat o méně podrobných zobrazeních.

## <a name="describing-variations"></a>Popisující variace
 Diagram znázorňuje jednu typickou posloupnost událostí. Pokud chcete zobrazit alternativní možnosti, jako jsou například scénáře selhání, můžete použít některou z těchto možností:

- Nakreslete samostatné sekvenční diagramy, které popisují tyto scénáře.

- Použijte [Popis řídicích struktur s fragmenty](#Fragments) k zobrazení smyček, alternativ a tak dále.

## <a name="assessing-the-design"></a>Posouzení návrhu
 Diagram lze použít k vyhodnocení rozdělení úkolů mezi objekty nebo komponenty. Zvažte refaktoring, pokud vidíte tyto vzory:

- Zdá se, že jedna životnost provedla vše a provede volání na všechno ostatní, zatímco ostatní životnosti stačí přesně reagovat.

- Mnoho zpráv překračuje životnost. Každá životnost by měla posílat zprávy jenom k několika sousedním sousedům a neměla by komunikovat s okolními sousedními sousedy. Obvykle je možné uspořádat životnosti tak, aby bylo k dispozici pouze několik míst, kde jsou zprávy překročeny životnosti. a tam, kde existují křížení, by neměla cílová životnost také vyměňovat zprávy, které mají překročené životnosti.

- Některé životnosti se zdají zvládnout více než jeden druh úlohy. Měl by se snadno najít jedna Stručná věta, která popisuje zodpovědnost každé životnosti, a shrnout práci, kterou reaguje, na každou obdrženou zprávu.

## <a name="ClassesAndLifelines"></a>Třídy a životnosti
 Životnosti v sekvenčních diagramech ukazují instance tříd nebo rozhraní komponent. Životnost můžete pojmenovat dvěma způsoby:

|**Pro tento účel**|**Použít tento formát**|
|--------------------------|-------------------------|
|Anonymní instance typu<br /><br /> Tuto část použijte v případě, že máte pouze jednu životnost každého typu.|*typeName*|
|Pojmenovaná instance typu<br /><br /> Tuto hodnotu použijte, pokud chcete zobrazit sekvenci, která zahrnuje víc než jednu instanci stejného typu.|*ObjectName*:*TypeName*|

### <a name="creating-lifelines-from-types"></a>Vytváření životností z typů
 Můžete vytvořit nové životnosti z tříd, které jste již definovali, například v diagramu tříd.

> [!NOTE]
> Před provedením této úlohy se ujistěte, že máte existující sekvenční diagram.

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Vytvoření životnosti z existujícího typu

- Přetáhněte třídu, komponentu nebo rozhraní z Průzkumníka modelů UML do sekvenčního diagramu.

   \- nebo –

  1. V příslušném diagramu klikněte pravým tlačítkem na třídu, komponentu nebo rozhraní a pak klikněte na **vytvořit životnost**.

  2. V dialogovém okně **vytvořit životnost** vyberte sekvenční diagram a pak klikněte na **OK**.

     Zobrazí se nová životnost pojmenované instance, jejíž typ je typ, který jste přetáhli.

  > [!NOTE]
  > Tuto akci můžete opakovat tolikrát, kolikrát chcete. Tím se vytvoří životnost s různými názvy instancí.

##### <a name="to-change-the-type-of-a-lifeline"></a>Změna typu životnosti

1. Klikněte pravým tlačítkem na životnost a pak klikněte na **vlastnosti**.

2. V okně **vlastnosti** nastavte vlastnost **typ** . Můžete buď vybrat typ z rozevírací nabídky, nebo zadat nový název.

### <a name="creating-classes-from-lifelines"></a>Vytváření tříd z životností
 Když jste vytvořili jeden nebo více sekvenčních diagramů, můžete sumarizovat životnosti vytvořením tříd nebo rozhraní z nich.

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Vytvoření třídy nebo rozhraní z životnosti

1. Klikněte pravým tlačítkem na životnost a pak klikněte na **vytvořit třídu** nebo **vytvořit rozhraní**.

     V Průzkumníku modelů UML se zobrazí nová třída nebo rozhraní.

2. Vytvořte operace v třídě nebo rozhraní pro každou zprávu, kterou životnost přijímá:

    1. Vyberte všechny zprávy, které chcete zahrnout.

    2. Klikněte pravým tlačítkem na jednu ze zpráv a pak klikněte na **vytvořit metodu**.

         Nová třída nebo rozhraní obsahuje operace pro každou vybranou zprávu.

         Název operace se zobrazí pod každou šipkou zprávy a ve vlastnosti **operace** zprávy.

         Pokud vaše zpráva obsahuje parametry ve formátu "(parametr: Type)", zobrazí se v seznamu parametrů nové operace.

        > [!NOTE]
        > Pokud přidáte nové zprávy do sekvenčního diagramu, je nutné tento krok opakovat.

3. Chcete-li zobrazit novou třídu nebo rozhraní podrobněji, přidejte ji do diagramu tříd nebo komponent.

    1. Otevřete nebo vytvořte diagram třídy nebo komponenty.

    2. Přetáhněte novou třídu nebo rozhraní z **Průzkumníka modelů UML** do diagramu tříd.

         Třída nebo rozhraní se zobrazí v diagramu tříd.

         \- nebo –

    3. Přetáhněte nové rozhraní z **Průzkumníka modelů UML** na součást nebo port v diagramu komponent.

         Rozhraní se zobrazí v součásti jako Lupa.

### <a name="creating-classes-for-parameters"></a>Vytváření tříd pro parametry
 Můžete zahrnout parametry do zpráv v sekvenčním diagramu. K popisu typů parametrů lze použít diagram tříd UML.

## <a name="Multiple"></a>Vytváření opakovaně použitelných sekvencí interakce
 Pomocí samostatného diagramu můžete popsat sekvenci, která obsahuje podrobnosti, které chcete oddělit nebo které jsou běžné mezi několika diagramy.

 Můžete vytvořit interakci použít obdélník (12) v jednom diagramu, který odkazuje na podrobnosti v jiném diagramu.

 Dvakrát klikněte na použití interakce k otevření sekvenčního diagramu, který je k němu propojený.

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Vytvoření opakovaně použitelné sekvence interakce z existujících životností

1. V sadě **nástrojů**klikněte na možnost **použít interakci**.

2. V sekvenčním diagramu podržte stisknuté tlačítko myši při přetahování mezi životnostmi, které chcete zahrnout do opakovaně použitelné sekvence. Začněte na svislém místě, kam chcete vložit interakci.

     Použití interakce se zobrazí napříč vybranými životnostmi v sekvenčním diagramu.

3. Dvakrát klikněte na název při použití interakce a přejmenujte jej, abyste popsali účinek opakovaně použitelné sekvence v tomto diagramu.

     \- nebo –

     Napište název jako volání funkce s parametry.

4. Propojení použití interakce s jiným sekvenčním diagramem. Klikněte pravým tlačítkem myši na možnost použití interakce a pak na jednu z těchto akcí:

     Kliknutím na **vytvořit novou sekvenci** vytvoříte nový sekvenční diagram.

     \- nebo –

     Kliknutím na **propojit se sekvencí** můžete propojit s existujícím diagramem.

     Visual Studio vytvoří propojení mezi použitím interakce a nové posloupnosti interakcí.

     Ve vašem řešení se zobrazí nový sekvenční diagram. Obsahuje životnosti, které jste použili k vytvoření použití interakce.

    > [!NOTE]
    > Budou zahrnuty pouze životnosti, které jste použili k vytvoření použití interakce. Nový diagram nezahrnuje životnosti, kterou jste vytvořili po použití interakce, a to i v případě, že je interakce použita nyní.

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Vytvoření opakovaně použitelné sekvence z existujících zpráv

- Klikněte pravým tlačítkem myši na zprávu, kterou chcete přesunout, a potom klikněte na **přesunout do diagramu**.

  Visual Studio:

  - Nahradí pomocí interakce vybranou zprávu a všechny dceřiné zprávy.

  - Přesune nahrazené zprávy do nového sekvenčního diagramu.

  - Vytvoří propojení mezi použitím interakce a nového sekvenčního diagramu.

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Přechod na sekvenci, na kterou se odkazuje pomocí interakce

- Dvakrát klikněte na možnost použít interakci.

     \- nebo –

     Klikněte pravým tlačítkem myši na použití interakce a potom klikněte na tlačítko **Přejít ke sekvenci**.

### <a name="creating-a-placeholder-with-an-interaction-use"></a>Vytvoření zástupného textu s využitím interakce
 Můžete vytvořit interakci bez propojení s jiným diagramem. Můžete ji použít jako zástupný symbol pro část sekvence, jejichž podrobnosti jsou ještě odpracované. Použijte název použití interakce k označení výsledku, který chcete.

## <a name="Collapse"></a>Sbalení skupin životností
 Můžete sbalit sadu životností dohromady, aby se skupina zobrazovala jako jedna životnost. To vám pomůže vizualizovat skupinu objektů jako jednu komponentu. Zprávy a použití interakce mezi životnostmi ve sbalených skupinách jsou skryté. Zobrazují se zprávy a sekvence interakce, které zahrnují jiné životnosti.

#### <a name="to-collapse-a-group-of-lifelines-together"></a>Sbalení skupiny životností dohromady

1. Vyberte dvě nebo více životností.

2. Klikněte na jednu z nich pravým tlačítkem myši a potom klikněte na **sbalit**.

     Samostatné životnosti se nahrazují jedinou životností.

     Zprávy a interakce použití, které zahrnují pouze členy skupiny, jsou skryté.

3. Chcete-li přejmenovat skupinu, klikněte na její název.

    > [!NOTE]
    > Název skupiny se při rozbalení skupiny ztratí.

#### <a name="to-expand-a-collapsed-group"></a>Chcete-li rozbalit sbalenou skupinu

- Klikněte pravým tlačítkem na sbalený životnost a potom klikněte na tlačítko **Rozbalit**.

    > [!NOTE]
    > Název skupiny bude ztracen spolu s jakýmikoli odkazy ze skupiny na komentáře nebo pracovní položky.

## <a name="Fragments"></a>Popis řídicích struktur s fragmenty
 Můžete použít kombinované fragmenty (13) k definování smyček, větví a souběžného zpracování v sekvenčním diagramu. Případně zvažte místo toho použití diagramu činnosti. Diagram aktivity není tak užitečný, když zobrazuje zprávy mezi objekty Actors, ale v některých případech je lepší při zobrazování smyček, větví a souběžnosti.

 Úplný seznam typů fragmentů naleznete v tématu [Popis toku řízení pomocí fragmentů v sekvenčních diagramech UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).

#### <a name="to-create-a-combined-fragment"></a>Vytvoření kombinovaného fragmentu

1. Vyberte zprávu nebo posloupnost zpráv, které začínají na stejném výskytu nebo životnosti spuštění.

    > [!NOTE]
    > Vyberte šipky zpráv, nikoli výskyty, na které se zprávy odkazují.

2. Klikněte pravým tlačítkem myši na jednu ze zpráv, ukažte na možnost **prostorový s**a pak klikněte na požadovaný typ fragmentu.

     Zobrazí se nový fragment. Obsahuje zprávy, které jste vybrali.

     Pokud kombinovaný typ fragmentu umožňuje více fragmentů, zobrazí se také prázdný fragment.

3. Chcete-li nastavit ochranu fragmentu, klikněte pravým tlačítkem myši na ohraničení fragmentu a poté klikněte na příkaz **vlastnosti**. Nastavte vlastnost **Guard** .

     Guard slouží k definování podmínky pro větev nebo smyčku.

4. Chcete-li přidat nový fragment do druhu, který povoluje více fragmentů, klikněte pravým tlačítkem myši na hranici fragmentu a přejděte na příkaz **Přidat**. Klikněte buď na **operand interakce před** , nebo na **operand interakce po**.

5. Chcete-li přidat nové zprávy do fragmentu, použijte nástroje pro zprávy nebo je zkopírujte a vložte.

## <a name="see-also"></a>Viz také
 [Sekvenční diagramy UML: referenční](../modeling/uml-sequence-diagrams-reference.md) dokumentace [Upravit modely UML a diagramy](../modeling/edit-uml-models-and-diagrams.md) [případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md) [diagramy tříd](../modeling/uml-class-diagrams-reference.md) UML: referenční diagramy UML: referenční diagramy komponent UML: referenční [](../modeling/uml-component-diagrams-reference.md) [](../modeling/uml-component-diagrams-reference.md) [video: náčrtace interakcí pomocí sekvenčních diagramů](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases)
