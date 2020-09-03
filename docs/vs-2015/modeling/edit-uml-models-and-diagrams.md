---
title: Úpravy modelů a diagramů UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00ac30cc7e9ee3aff0dd64f015a4b4954972c09a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295533"
---
# <a name="edit-uml-models-and-diagrams"></a>Úpravy modelů a diagramů UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Model UML můžete vytvořit a upravit pomocí zobrazení poskytovaných několika různými typy diagramu. Díky různým perspektivám v systému vám tyto diagramy pomůžou pochopit a diskutovat o různých aspektech návrhu a požadavků. Visual Studio poskytuje šablony pro pět nejčastěji používaných typů diagramu UML.

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Toto téma popisuje techniky pro úpravu modelu, které jsou společné mezi různými typy diagramů. Další informace, které jsou specifické pro konkrétní typy diagramů, najdete v tématu [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md).

## <a name="in-this-topic"></a>V tomto tématu

- [Diagramy UML jsou zobrazení modelu UML](#Views)

- [Vytváření diagramů modelování UML](#Creating)

- [Kreslení diagramů modelování UML](#Drawing)

- [Úpravy obrazců a konektorů](#Editing)

- [Rušení změn modelu](#Undo)

- [Sdílení prvků mezi diagramy](#Sharing)

- [Kopírování prvků a skupin souvisejících prvků](#Copying)

- [Odstranění prvku modelu nebo jeho zobrazení](#Deleting)

- [Hledání textu v diagramu](#Searching)

- [Příprava diagramu pro prezentaci](#presentation)

- [Rozšíření návrhářů UML](#extensions)

## <a name="uml-diagrams-are-views-of-a-uml-model"></a><a name="Views"></a> Diagramy UML jsou zobrazení modelu UML
 Diagramy UML můžete vytvářet a používat pouze v projektech modelování. Další informace o tom, jak vytvářet diagramy a projekty, najdete v tématu [vytváření projektů a diagramů modelování UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

- Projekt modelování obsahuje jeden model UML. Každý diagram UML v projektu je zobrazení modelu UML.

- Model můžete zobrazit v **Průzkumníku modelů UML**. V nabídce **Architektura** přejděte na **okna**a potom klikněte na **Průzkumník modelů UML**.

- Každý obrazec v diagramu je zobrazením elementu v modelu. Když umístíte nový tvar do diagramu, vytváříte nový prvek v modelu.

- Když uložíte libovolný diagram, Visual Studio uloží celý model, všechny jeho diagramy a soubor projektu modelování.

## <a name="creating-uml-modeling-diagrams"></a><a name="Creating"></a> Vytváření diagramů modelování UML

1. V nabídce **Architektura** v aplikaci Visual Studio klikněte na **Nový UML nebo Diagram vrstev**.

2. Vyberte a pojmenujte diagram.

3. V rámci **Přidat do projektu modelování**vyberte existující projekt modelování nebo vyberte **vytvořit nový projekt modelování**.

   > [!NOTE]
   > Diagram modelování musí existovat v rámci projektu modelování.

   Diagram můžete také přidat do existujícího projektu modelování v Průzkumník řešení. Klikněte pravým tlačítkem na projekt modelování, přejděte na **Přidat**a klikněte na **Nová položka**.

#### <a name="to-create-an-empty-uml-modeling-project"></a>Vytvoření prázdného projektu modelování UML

- V nabídce **soubor** přejděte na příkaz **Nový**, klikněte na **projekt**a v dialogovém okně **Nový projekt** poklikejte na **projekty modelování**.

  Další informace o tom, jak spravovat projekty modelování, najdete v tématu [vytváření projektů a diagramů modelování UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="drawing-uml-modeling-diagrams"></a><a name="Drawing"></a> Kreslení diagramů modelování UML
 Diagram modelování zobrazuje kolekci prvků modelu propojených pomocí vztahů. Každý prvek se zobrazí jako obrazec a každá relace se zobrazí jako spojnice mezi dvěma tvary.

 Existují dva druhy nástrojů – jeden pro elementy a jeden pro vztahy. Například na panelu nástrojů diagramu tříd UML je **Třída** nástrojem prvku a **přidružení** je nástroj relace.

> [!NOTE]
> Pokud chcete informace, které jsou specifické pro konkrétní typy diagramů, přečtěte si téma [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md).

#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Vytváření elementů a vztahů v diagramu modelování UML

1. Chcete-li vytvořit prvek modelu, klikněte na nástroj prvku v panelu nástrojů a pak klikněte na diagram, ve kterém se má zobrazit. Po vytvoření prvku upravte jeho velikost a tvar přetažením jeho táhel.

    V některých případech můžete umístit nový prvek uvnitř jiného elementu. Například v diagramu tříd UML můžete umístit třídu do balíčku.

   > [!NOTE]
   > Pokud sadu nástrojů nemůžete zobrazit, klikněte v nabídce **zobrazení** na **panel nástrojů** .

2. Chcete-li vytvořit relaci, klikněte na nástroj relace, klikněte na prvek, ve kterém chcete spustit relaci, a poté klikněte na prvek, kde má být ukončen.

    Různé typy vztahů mohou začínat nebo končit na různých typech prvků. Například v diagramu tříd UML nemůže relace přidružení začínat ani končit na elementu Comment.

   > [!NOTE]
   > Chcete-li použít stejný nástroj několikrát, dvakrát klikněte na nástroj. Po dokončení klikněte na nástroj **ukazatel** .

   U některých druhů diagramů můžete také kreslit jednoduché tvary. Tyto tvary nejsou součástí modelu, ale můžete je použít k upoutání pozornosti na části diagramu nebo k jejich rozdělení do různých oblastí.

## <a name="editing-shapes-and-connectors"></a><a name="Editing"></a> Úpravy obrazců a konektorů
 Když změníte velikost nebo barevný tvar nebo přesměrujete spojnici, neplatí to pro základní model. Pokud však přejmenujete tvar v diagramu nebo v Průzkumníku modelů UML, odpovídající element je přejmenován v Průzkumníku modelů UML a v jakémkoli jiném diagramu, který tento prvek prezentuje.

> [!NOTE]
> Existuje jednoduchý způsob, jak vytvořit nové položky sady nástrojů, ze kterých lze vytvořit skupiny prvků, nebo prvky s vlastní volbou vlastností. Další informace najdete v tématu [definice vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md).

 Následující obrázek ukazuje, jak změnit velikost tvaru nebo jeho názvu.

 ![Úprava prvku modelu](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")

> [!TIP]
> Předdefinované příkazy neobsahují příkaz pro úhledné zarovnání tvarů. Můžete však snadno vytvořit vlastní příkaz pro zarovnání zkopírováním kódu v příkladu v části [zobrazení modelu UML v diagramech](../modeling/display-a-uml-model-on-diagrams.md).

 Následující obrázek ukazuje, jak upravit trasu a polohu spojnice nebo jejích popisků.

 ![Úprava konektoru](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")

#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Přesunutí jednoho konce spojnice na jiný tvar

1. Proveďte jednu z následujících akcí:

   - Stiskněte klávesu **CTRL** a přesuňte konec.

     \- ani

   - Klikněte pravým tlačítkem na konektor a pak klikněte na **znovu připojit**.

2. Klikněte na konec konektoru, který chcete přesunout.

3. Klikněte na tvar, na který chcete spojnici přesunout.

#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Změna barvy nebo jiných vlastností prvku, vztahu nebo diagramu

- Klikněte na prvek a nastavte pole v okně **vlastnosti** .

     Pokud se okno **vlastnosti** nezobrazí, klikněte pravým tlačítkem myši na prvek a potom klikněte na příkaz **Vlastnosti.**

#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Přiblížení a oddálení diagramu modelování

- Stisknutím a podržením klávesy **CTRL** při otočení kolečka myši.

     \- ani

- Stiskněte a podržte **kombinaci kláves CTRL + SHIFT**a potom klikněte na levé nebo pravé tlačítko myši.

     \- ani

- Na panelu nástrojů **Návrháře architektury** klikněte na znaménko plus ( **+** ) nebo mínus ( **-** ) nebo vyberte úroveň přiblížení.

## <a name="searching-in-a-diagram"></a><a name="Searching"></a> Hledání v diagramu
 Funkce rychlého hledání bude vyhledávat položky v diagramu. Je nutné nastavit **Oblast hledání:** na **aktuální dokument**.

#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Hledání textu v diagramu modelování

1. Stiskněte **kombinaci kláves CTRL + F**.

     \- ani

     V nabídce **Upravit** přejděte na **Najít a nahradit**a pak klikněte na **Rychlé hledání**.

    > [!NOTE]
    > V dialogovém okně **Najít a nahradit** musíte ponechat pole **Hledat v** nastavené na **aktuální dokument**. Ostatní možnosti nejsou podporovány.

2. Zadejte text, který chcete najít, a potom klikněte na **Najít další**.

    > [!NOTE]
    > Pokud je text, který chcete najít, ve sbaleném tvaru, bude zvýrazněn tvar. Rozbalte tvar a pak znovu klikněte na **Najít další** .

## <a name="undoing-changes-to-the-model"></a><a name="Undo"></a> Rušení změn modelu
 Změny, které jste provedli v modelu a diagramech, můžete vrátit zpět a znovu pomocí příkazů **zpět** a **znovu** v nabídce **Upravit** .

 **Každý projekt modelování má jeden zásobník změn.** Všechny změny, které provedete v modelu a diagramech, se v tomto zásobníku uchovávají. Zásobník obsahuje také změny fokusu z jednoho diagramu na druhý. Příkaz zpět obrátí změny v tomto zásobníku.

 Řekněme například, že provedete tyto operace: Udělejte změnu na Diagram1; změnit fokus na diagram 2; Změňte diagram2. Při vrácení změn zpět vrátí poslední změnu zpět. Při dalším vrácení se fokus přesune zpátky na diagram 1; a třetí akce zpět vrátí změnu na diagram 1.

 **Zavření diagramu zkrátí zásobník změn.** Pokud diagram zavřete, nemůžete vrátit zpět změny provedené v tomto diagramu a nemůžete vrátit zpět předchozí změny modelu ani žádné z jeho diagramů.

 **Při úpravách vlastnosti nelze operaci vrátit zpět.** Při úpravách vlastnosti v okno Vlastnosti nebo v popisku diagramu můžete vrátit pouze změny, které jste v dané vlastnosti udělali. Změnu ve vlastnosti dokončíte stisknutím klávesy ENTER nebo kliknutím na tlačítko Storno ji zrušit stisknutím klávesy ESC. Pak budete moci vrátit změny v modelu a diagramech.

 **Zavření diagramu bez uložení nemusí mít očekávaný efekt.** Pokud provedete nějaké změny a pak diagram zavřete bez uložení, změny se v modelu pořád zachovají. Pokud to chcete provést bez uložení, doporučujeme celý model zavřít.

## <a name="sharing-elements-between-diagrams"></a><a name="Sharing"></a> Sdílení prvků mezi diagramy
 Konkrétní instanci prvku modelu můžete v diagramech Zobrazit více než jednou. To platí pro třídy, rozhraní, komponenty, případy použití a aktéry.

 To je užitečné, pokud chcete zobrazit různé skupiny vztahů v různých diagramech. Například v jednom diagramu můžete zobrazit přidružení mezi třídami zákazníka a adresy. Na jiném diagramu můžete znovu zobrazit třídu adres s její asociací k poštovní oblasti.

 Můžete změnit vlastnosti prvku modelu, jako je jeho název, výběrem kteréhokoli z jeho zobrazení v jakémkoli diagramu nebo jeho výběrem v Průzkumníku modelů UML.

 Každý druh diagramu může zobrazit pouze některé druhy prvku modelu. Například nelze zobrazit případ použití v diagramu komponent. Proto následující postupy budou fungovat pouze pro některé kombinace prvku modelu a diagramu.

#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>Přidání nového zobrazení prvku modelu pomocí Průzkumníka modelů UML

1. Chcete-li otevřít **Průzkumníka modelů UML**, v nabídce **Architektura** přejděte na položku **okna**a klikněte na možnost **Průzkumník modelů UML**.

2. Přetáhněte prvek modelu z **Průzkumníka modelů UML** do kompatibilního diagramu ve stejném projektu.

     Zobrazí se obrazec, který poskytuje zobrazení prvku modelu, což může být mimo zobrazení v jiných diagramech nebo ve stejném diagramu.

    > [!NOTE]
    > Když přetáhnete třídu nebo komponentu do sekvenčního diagramu, efekt se liší. V takovém případě je vytvořena nová životnost, jejíž typ je tato třída nebo komponenta. Další informace najdete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).

#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Přidání nového zobrazení prvku modelu pomocí odkazu pro vložení

1. Klikněte pravým tlačítkem na existující prvek a pak klikněte na **Kopírovat**.

    - Můžete kopírovat několik prvků současně. Podržte stisknutou klávesu CTRL a klikněte na jednotlivé prvky, klikněte na jednu z nich pravým tlačítkem myši a pak klikněte na **Kopírovat**.

2. Klikněte pravým tlačítkem myši na prázdnou část kompatibilního diagramu a potom klikněte na příkaz **Vložit odkaz**.

     Zobrazí se jiné zobrazení stejného prvku.

    > [!NOTE]
    > To se liší od příkazu pro **vložení** , který vytvoří nový prvek v modelu. Další informace naleznete v tématu [kopírování prvků a skupin souvisejících prvků](#Copying).

> [!NOTE]
> Pokud přidáte do zobrazení diagramu dvou prvků modelu, které jsou již propojeny pomocí relace, zobrazí se v diagramu také zobrazení vztahu. Toto zobrazení lze odstranit pouze odebráním jednoho z prvků z diagramu, nebo odstraněním vztahu z modelu.

## <a name="copying-elements-and-groups-of-related-elements"></a><a name="Copying"></a> Kopírování prvků a skupin souvisejících prvků
 Prvky modelu lze kopírovat a vkládat a můžete kopírovat a vkládat skupiny prvků spolu s relacemi mezi nimi.

> [!NOTE]
> Příkazy pro **vložení** a **vložení** mají různé účinky. **Vložení** vytvoří nové prvky, jejichž vlastnosti jsou jako prvky kopírovaných prvků. **Vložení odkazu** vytvoří nová zobrazení stejného prvku.

#### <a name="to-copy-elements-and-their-relationships"></a>Kopírování prvků a jejich vztahů

1. V diagramu s prvky, které chcete kopírovat, vyberte jeden nebo více prvků.

    > [!NOTE]
    > Relace s výjimkou nemůžete kopírovat jako součást skupiny prvků.

2. V nabídce **Upravit** klikněte na příkaz **Kopírovat**.

3. Chcete-li kopírovat prvky do jiného diagramu, vytvořte nový diagram nebo otevřete existující diagram.

4. V nabídce **Upravit** klikněte na příkaz **Vložit**.

    - Kopie prvků se zobrazí spolu s kopiemi vztahů, které mezi nimi propojuje.

    - Každý nový prvek bude mít nový automaticky generovaný název.

5. Upravte pozice, názvy a další vlastnosti nových prvků a vztahů.

> [!NOTE]
> Prvek modelu nelze kopírovat z jednoho modelu do jiného, například pokud máte dva modely ve stejném řešení. Prvky můžete ale kopírovat z jednoho diagramu na jiný.

#### <a name="to-copy-an-entire-diagram"></a>Zkopírování celého diagramu

1. Vytvořte nový diagram.

2. Vyberte všechny prvky v existujícím diagramu, zkopírujte je a vložte do nového.

   Diagram nelze replikovat zkopírováním a vložením do Průzkumník řešení.

## <a name="deleting-a-model-element-or-its-views"></a><a name="Deleting"></a> Odstranění prvku modelu nebo jeho zobrazení
 Některé druhy prvků, konkrétně třídění, lze z diagramu odebrat, aniž byste je museli odstraňovat z modelu. Klasifikátory jsou hlavní prvky, které se zobrazují v diagramech tříd, diagramech komponent a diagramech případů použití. Můžou se objevit ve více než jednom diagramu. Pro tyto typy prvků existují dva samostatné příkazy: **Odebrat z diagramu** a **Odstranit z modelu**.

 Naopak když odstraníte relaci z diagramu, vždy ji odstraníte z modelu.

> [!NOTE]
> Některé druhy prvků v diagramu UML mají popisky. Když vyberete tyto prvky kreslením obdélníku kolem nich, je možné vybrat popisky, ale ne prvky, které tyto popisky vlastní. Odstranění podmnožiny prvků, které jsou vybrány tímto způsobem, není podporováno. Chcete-li vybrat podmnožinu těchto prvků, stiskněte a podržte stisknutou klávesu **CTRL** a klikněte na jednotlivé prvky.

#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Odebrání zobrazení klasifikátoru z diagramu

- Klikněte pravým tlačítkem na prvek v diagramu a pak klikněte na **Odebrat z diagramu**.

  \- ani

- Klikněte na prvek v diagramu a potom stiskněte klávesu **Delete** .

  - Toto zobrazení elementu zmizí. Element však zůstane v modelu a stále jej můžete najít v **Průzkumníku modelů UML**. Všechna ostatní zobrazení stejného prvku také zůstanou.

  - Všechny konektory, které se ukončí tímto tvarem, se z diagramu odeberou, ale vztah, který představuje, zůstane v modelu. V **Průzkumníku modelů UML** pod položkou **relace**můžete v rámci každého elementu, který se připojuje, zobrazit vztah.

#### <a name="to-delete-an-element-from-the-model"></a>Odstranění elementu z modelu

- Klikněte pravým tlačítkem myši na prvek v **Průzkumníku modelů UML** nebo v diagramu a pak klikněte na **Odstranit z modelu**.

  - Prvek je odstraněn z každého diagramu, na kterém je zobrazen.

  - Z modelu se odstraní také všechny relace, které se ukončí v tomto elementu.

#### <a name="to-delete-a-relationship-from-the-model"></a>Odstranění vztahu z modelu

- Klikněte pravým tlačítkem na vztah v diagramu nebo v **Průzkumníku modelů UML**a pak klikněte na **Odstranit z modelu**.

    > [!CAUTION]
    > Nemůžete odebrat relaci z diagramu, aniž byste ji odebrali z modelu.

     Vztah je odstraněn z modelu a je odstraněn z každého diagramu, na kterém je zobrazen.

## <a name="preparing-a-diagram-for-presentation"></a><a name="presentation"></a> Příprava diagramu pro prezentaci
 Následující funkce vám pomůžou nakreslit pozornost na konkrétní části diagramu, přidat vysvětlení nebo rozdělit diagram do různých oblastí, které vás zajímají.

- Jakoukoli část diagramu můžete zkopírovat do Wordu, PowerPointu nebo jiného dokumentu. Vyberte požadované tvary a konektory, klikněte pravým tlačítkem myši a potom klikněte na tlačítko **Kopírovat**.

- Barvu libovolného tvaru nebo konektoru lze změnit. Vyberte jeden nebo více tvarů a změňte vlastnost **Color** . Pokud se okno **vlastnosti** nezobrazí, stiskněte **F4**.

- V diagramech některých druhů můžete kreslit čáry, obdélníky a elipsy z části **jednoduchých tvarů** v sadě nástrojů. Tyto tvary netvoří součást modelu UML.

- Chcete-li popsat oblast, můžete přetáhnout komentář ze sady nástrojů a potom nastavit jeho **průhlednou** vlastnost na **hodnotu true**. Podobně jako jednoduché tvary netvoří komentáře součást modelu UML a nezobrazují se v Průzkumníku modelů UML.

- Chcete-li přidat poznámky a vysvětlení k prvkům modelu, můžete vytvořit komentáře a propojit je s prvky.

### <a name="to-export-a-diagram-as-an-image"></a>Export diagramu jako obrázku
 Další informace najdete v tématu [Export diagramů jako obrázků](../modeling/export-diagrams-as-images.md).

## <a name="extending-the-uml-designers"></a><a name="extensions"></a> Rozšíření návrhářů UML
 Do nástrojů UML můžete přidat nové funkce a přizpůsobit zápis diagramu vlastním potřebám. Další informace najdete v tématu věnovaném [rozšiřování modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md).

## <a name="see-also"></a>Viz také
 [Vytváření projektů a diagramů modelování UML](../modeling/create-uml-modeling-projects-and-diagrams.md) [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md) [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md)
