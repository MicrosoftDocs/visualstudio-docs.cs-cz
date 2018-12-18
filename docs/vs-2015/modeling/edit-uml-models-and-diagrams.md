---
title: Úpravy modelů a diagramů UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 92d2be3abfb849b0b5cf5c1c820040b658e2240c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803432"
---
# <a name="edit-uml-models-and-diagrams"></a>Úpravy modelů a diagramů UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vytvořit a upravit model UML prostřednictvím zobrazení poskytuje několik různých typů diagramu. Zadáním různých perspektiv ve vašem systému tyto diagramy vám pomůže pochopit a probrat různé aspekty návrhu a požadavků. Visual Studio poskytuje šablony pro pět nejčastěji používané typy diagramu UML.  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Toto téma popisuje postupy pro úpravy modelu, které jsou společné mezi různé typy. Další informace, které jsou specifické pro konkrétní typy diagramů, naleznete v tématu [vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md).  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [Diagramy UML jsou zobrazením tohoto modelu UML](#Views)  
  
-   [Vytváření diagramů pomocí modelování UML](#Creating)  
  
-   [Vytvoření diagramů modelování UML](#Drawing)  
  
-   [Úpravy obrazců a konektorů](#Editing)  
  
-   [Ruší se provedené změny do modelu](#Undo)  
  
-   [Sdílení prvků mezi diagramů](#Sharing)  
  
-   [Kopírování prvků a skupiny souvisejících elementů](#Copying)  
  
-   [Odstranění prvku modelu a jeho zobrazení](#Deleting)  
  
-   [Hledání textu v diagramu](#Searching)  
  
-   [Příprava diagramu pro prezentaci](#presentation)  
  
-   [Rozšíření návrhářů UML](#extensions)  
  
##  <a name="Views"></a> Diagramy UML jsou zobrazením tohoto modelu UML  
 Můžete vytvořit a použít diagramy UML pouze v projekty modelování. Další informace o vytváření projektů a diagramů naleznete v tématu [vytvořit modelování projektů a diagramů UML](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
-   Projekt modelování obsahuje jednoho modelu UML. Každý diagram UML v projektu je zobrazení modelu UML.  
  
-   Zobrazí se model v **Průzkumníku modelů UML**. Na **architektura** nabídky, přejděte k **Windows**a potom klikněte na tlačítko **Průzkumníku modelů UML**.  
  
-   Všechny obrazce v diagramu je zobrazení elementu v modelu. Umístíte-li nový obrazec v diagramu, vytváření nového elementu v modelu.  
  
-   Soubor projektu, když uložíte jakýkoliv diagram, Visual Studio uloží celý model, všechny jeho diagramy a modelování.  
  
##  <a name="Creating"></a> Vytváření diagramů pomocí modelování UML  
  
1. Na **architektura** klikněte na tlačítko nabídky v sadě Visual Studio **nové UML nebo diagramu vrstev**.  
  
2. Vyberte a zadejte název vašeho diagramu.  
  
3. V **přidat do projektu modelování**, vyberte existující projekt modelování nebo **vytvořte nový projekt modelování**.  
  
   > [!NOTE]
   >  Diagram modelování musí existovat v projektu modelování.  
  
   Diagram můžete také přidat do existujícího projektu modelování v Průzkumníku řešení. Klikněte pravým tlačítkem na projekt modelování, přejděte na **přidat**a potom klikněte na tlačítko **nová položka**.  
  
#### <a name="to-create-an-empty-uml-modeling-project"></a>Chcete-li vytvořit prázdný projekt modelování UML  
  
- Na **souboru** nabídky, přejděte na **nový**, klikněte na tlačítko **projektu**a v **nový projekt** dialogové okno, dvakrát klikněte na panel **modelování Projekty**.  
  
  Další informace o tom, jak spravovat projekty modelování, naleznete v tématu [vytvořit modelování projektů a diagramů UML](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
##  <a name="Drawing"></a> Vytvoření diagramů modelování UML  
 Diagram modelování zobrazí kolekci prvků modelu propojených vztahů. Každý prvek se zobrazí jako tvar a každá relace se zobrazí jako konektor mezi dvěma tvary.  
  
 Existují dva druhy nástroje, jeden pro prvky a jeden pro relace. Například v diagramu tříd UML nástrojů **třídy** je nástroj elementu a **přidružení** je nástroj vztah.  
  
> [!NOTE]
>  Pokud chcete informace, které jsou specifické pro konkrétní diagram typy, najdete v článku [vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md).  
  
#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>K vytváření elementů a vztahů v diagramu modelování UML  
  
1. Vytvoření prvku modelu, nástroj prvek v sadě nástrojů klikněte na a pak klikněte na tlačítko diagram, ve kterém chcete, aby se zobrazí. Po vytvoření elementu, upravte jeho velikost a tvar přetáhněte její úchyty.  
  
    V některých případech můžete umístit nový prvek do jiného elementu. Například v diagramu tříd UML může umístit třídy uvnitř balíčku.  
  
   > [!NOTE]
   >  Pokud nevidíte panel nástrojů, klikněte na tlačítko **nástrojů** na **zobrazení** nabídky.  
  
2. K vytvoření relace, klikněte na nástroj relace, klikněte na prvek, kde chcete spustit relaci a klikněte na tlačítko elementu, kde chcete, aby ukončit.  
  
    Různé typy vztahů, může začínat ani končit na různé typy prvků. Například v diagramu tříd UML vztah přidružení nesmí začínat ani skončí prvek komentář.  
  
   > [!NOTE]
   >  Pokud chcete použít stejný nástroj několikrát, klikněte na nástroj dvakrát. Jakmile budete hotovi, klikněte na tlačítko **ukazatel** nástroj.  
  
   V některých typech diagramy můžete také nakreslit jednoduché obrazce. Tyto tvary, které nejsou součástí modelu, ale můžete je použít k přitažení pozornosti ke část diagramu a jeho rozdělení na různé oblasti.  
  
##  <a name="Editing"></a> Úpravy obrazců a konektorů  
 Při změně velikosti nebo barva obrazce nebo přesměrovat konektor, neexistuje žádný vliv na základní model. Ale při přejmenování obrazec v diagramu nebo v Průzkumníku modelů UML, odpovídající prvek je přejmenovat v Průzkumníku modelů UML a ostatní diagramy, které se tento element.  
  
> [!NOTE]
>  Neexistuje jednoduchý způsob, jak vytvořit nové položky panelu nástrojů, z nichž můžete vytvářet skupiny elementy nebo elementy s libovolným vlastnosti. Další informace najdete v tématu [definování vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
 Následující obrázek ukazuje, jak změnit velikost tvaru nebo jeho název.  
  
 ![Úprava prvku modelu](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")  
  
> [!TIP]
>  Integrované příkazy nezahrnujte příkaz pro elegantně zarovnání tvarů. Však můžete snadno vytvořit vlastní zarovnání příkazu zkopírováním kódem v příkladu v [zobrazení modelu UML v diagramech](../modeling/display-a-uml-model-on-diagrams.md).  
  
 Následující obrázek ukazuje, jak upravit trasu a pozice konektor nebo jeho popisků.  
  
 ![Nastavení konektoru](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")  
  
#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Na jednom konci spojnice přesunout do jiného obrazce  
  
1. Proveďte jednu z těchto akcí:  
  
   - Stisknutím klávesy **CTRL** a přesunout do konce.  
  
     \- nebo –  
  
   - Klikněte pravým tlačítkem na konektor a potom klikněte na tlačítko **volání metody Reconnect**.  
  
2. Klikněte na konci spojnice, ke které chcete přesunout.  
  
3. Klikněte na tvar, který chcete přesunout do konektoru.  
  
#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Změna barvy nebo dalších vlastností elementu, relace, nebo diagram  
  
-   Klikněte na prvek a nastavit pole **vlastnosti** okna.  
  
     Pokud nevidíte **vlastnosti** okna, klikněte pravým tlačítkem na elementu a klikněte na **vlastnosti.**  
  
#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Přiblížení a oddálení v diagramu modelování  
  
-   Stiskněte a podržte **CTRL** klávesu otočení kolečka myši.  
  
     \- nebo –  
  
-   Stiskněte a podržte **CTRL + SHIFT**a potom klikněte na tlačítko myši doleva nebo doprava.  
  
     \- nebo –  
  
-   Na **návrháři architektury** nástrojů, klikněte na znaménko plus (**+**) nebo minus (**-**), nebo zvolit úroveň zvětšení.  
  
##  <a name="Searching"></a> Hledání v diagramu  
 Funkce Rychlé hledání najdete položky v diagramu. Je nutné nastavit **oblast hledání:** k **aktuální dokument**.  
  
#### <a name="to-search-for-text-in-a-modeling-diagram"></a>K vyhledání textu v diagramu modelování  
  
1.  Stisknutím klávesy **CTRL + F**.  
  
     \- nebo –  
  
     Na **upravit** nabídky, přejděte k **najít a nahradit**a potom klikněte na tlačítko **rychlé hledání**.  
  
    > [!NOTE]
    >  V **najít a nahradit** dialogové okno, musí zůstat **Hledat v** pole nastaveno **aktuální dokument**. Další možnosti nejsou podporovány.  
  
2.  Zadejte text, který chcete vyhledat a potom klikněte na **najít další**.  
  
    > [!NOTE]
    >  Pokud je text, který má být nalezena uvnitř sbaleného obrazce, budou zvýrazněny tvaru. Rozbalte obrazec a potom klikněte na tlačítko **najít další** znovu.  
  
##  <a name="Undo"></a> Ruší se provedené změny do modelu  
 Lze vrátit zpět a znovu změny provedené do modelu a diagramů pomocí **zpět** a **znovu** příkazy na **upravit** nabídky.  
  
 **Každý projekt modelování nemá jedné sadě změn.** Všechny změny provedené modelu a diagramy jsou uloženy v tomto zásobníku. Zásobník obsahuje také změny fokus z jednoho diagramu do druhého. Příkaz Undo obrátí změny v tomto zásobníku.  
  
 Například Řekněme, že můžete provádět tyto operace: proveďte změnu Diagram1; Změňte fokus na Diagram 2; Změňte Diagram2. Při vrácení změn zpět první vrátíte zpět poslední změny; Další vrácení zpět se zpět do diagramu 1; přesunout fokus a třetí zpět vrátíte zpět změnu na hodnotu 1 diagramu.  
  
 **Zavření diagramu zkrátí sady změn.** Pokud zavřete diagram nelze vrátit zpět změny, které jste provedli v tomto diagramu a modelu nebo některý z jeho diagramy dřívější změny nejde vrátit zpět.  
  
 **Nelze vrátit zpět, když upravujete vlastnosti.** Když upravujete vlastnosti v okně Vlastnosti, nebo popisek v diagramu, je pouze vrátit zpět změny provedené v této vlastnosti. Stisknutím klávesy ENTER proveďte změny ve vlastnosti, nebo ji zrušte stisknutím klávesy ESC. Budete pak moct vrátit zpět změny v modelu a diagramů.  
  
 **Zavření diagramu bez uložení nemusí mít požadovaný efekt, které očekáváte.** Je-li provést nějaké změny a potom diagram zavřete bez uložení, provedené změny budou zachovány stále v modelu. Se doporučuje zavřít celý model, pokud budete chtít udělat bez uložení.  
  
##  <a name="Sharing"></a> Sdílení prvků mezi diagramů  
 Můžete vytvořit konkrétní instanci prvku modelu v diagramech objevit více než jednou. To platí pro třídy, rozhraní, komponenty, případy použití a objekty actor.  
  
 To je užitečné, pokud chcete zobrazit různé skupiny vztahů v různých diagramech. Například na jednom diagramu ukázat přidružení mezi třídami zákazníka a adresu. Na jiném může zobrazit třídu adresu znovu, s jeho přidružením k poštovní směrovací číslo oblasti.  
  
 Vlastnosti prvku modelu, například jeho název můžete změnit výběrem některé z jeho zobrazení na jakýkoliv diagram nebo tak, že ji vyberete v Průzkumníku modelů UML.  
  
 Každý typ diagramu můžou zobrazit jen některé typy prvku modelu. Například nelze zobrazit případ použití v diagramu komponent. Následující postupy proto bude fungovat pouze pro některé kombinace prvek modelu a diagram.  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>Přidat nové zobrazení prvku modelu s použitím Průzkumníka modelů UML  
  
1.  Chcete-li otevřít **Průzkumníku modelů UML**na **architektura** nabídky, přejděte **Windows**a potom klikněte na **Průzkumníku modelů UML**.  
  
2.  Přetáhněte prvku modelu z **Průzkumníku modelů UML** kompatibilní diagramu ve stejném projektu.  
  
     Obrazec za předpokladu, že se zobrazení prvku modelu, které mohou být kromě zobrazení na jiných diagramů nebo na stejném diagramu.  
  
    > [!NOTE]
    >  Účinek se liší, když přetahujete třídy nebo komponenty do sekvenčního diagramu. V takovém případě se vytvoří nové životnosti, jehož typ je této třídě nebo komponenty. Další informace najdete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Přidat nové zobrazení prvku modelu s použitím Vložit odkaz  
  
1.  Klikněte pravým tlačítkem na existující prvek a potom klikněte na tlačítko **kopírování**.  
  
    -   Můžete zkopírovat několik elementů ve stejnou dobu. Podržte stisknutou klávesu CTRL a klikněte na každý prvek, klikněte pravým tlačítkem na jeden z nich a pak klikněte na tlačítko **kopírování**.  
  
2.  Klikněte pravým tlačítkem na prázdnou část diagramu kompatibilní a potom klikněte na tlačítko **vložit odkaz**.  
  
     Zobrazí se jiný pohled stejného elementu.  
  
    > [!NOTE]
    >  Tím se liší od **vložit** příkaz, který vytvoří nový prvek v modelu. Další informace najdete v tématu [kopírování prvků a skupiny souvisejících prvků](#Copying).  
  
> [!NOTE]
>  Pokud chcete přidat do zobrazení diagramu dvou prvků modelu, které jsou již připojeny relací, zobrazení relace se také zobrazí v diagramu. Toto zobrazení můžete odstranit pouze tak, že odeberete některý z prvků v diagramu nebo tak, že odstraníte relaci z modelu.  
  
##  <a name="Copying"></a> Kopírování prvků a skupiny souvisejících elementů  
 Můžete zkopírovat a vložit prvky modelu, a můžete zkopírovat a vložit skupiny prvků spolu s vztahy mezi nimi.  
  
> [!NOTE]
>  **Vložit** a **vložit odkaz** příkazy mají různé účinky. **Vložit** vytvoří nové elementy, jejichž vlastnosti jsou podobné těm zkopírované elementy. **Vložit odkaz** vytvoří nová zobrazení stejné prvky.  
  
#### <a name="to-copy-elements-and-their-relationships"></a>Zkopírujte prvky a jejich vztahy  
  
1.  V diagramu s prvky, které chcete zkopírovat vyberte jeden nebo více prvků.  
  
    > [!NOTE]
    >  Vztahy s výjimkou nelze kopírovat v rámci skupiny prvků.  
  
2.  Na **upravit** nabídky, klikněte na tlačítko **kopírování**.  
  
3.  Pokud chcete kopírovat prvky do jiného diagramu, vytvořte nový diagram nebo otevřete existující diagram.  
  
4.  Na **upravit** nabídky, klikněte na tlačítko **vložit**.  
  
    -   Zkopíruje prvky se zobrazí spolu s kopií všechny vztahy, které jsou propojeny mezi nimi.  
  
    -   Každý nový prvek bude mít nový automaticky vygenerovaným názvem.  
  
5.  Upravte podle polohy, názvy a další vlastnosti nové prvky a vztahy.  
  
> [!NOTE]
>  Prvek modelu z jednoho modelu nelze zkopírovat do jiného, například pokud máte dva modely ve stejném řešení. Avšak prvky z jednoho diagramu můžete zkopírovat do jiného.  
  
#### <a name="to-copy-an-entire-diagram"></a>Zkopírujte celý diagram  
  
1. Vytvoření nového diagramu.  
  
2. Vybrat všechny elementy v diagramu existující, je zkopírujte a vložte je do nového.  
  
   Diagram nelze replikovat zkopírováním a vložením v Průzkumníku řešení.  
  
##  <a name="Deleting"></a> Odstranění prvku modelu a jeho zobrazení  
 Některé typy prvků, konkrétně třídění, můžete odebrat z diagramu bez jejich odstranění z modelu. Třídění jsou hlavní prvky, které jsou zobrazeny v diagramech tříd, diagramů komponent a diagramy případů použití. Můžete se zobrazí na více než jeden diagram. Pro tyto typy elementů jsou dva různé příkazy: **odebrat z diagramu** a **odstranit z modelu**.  
  
 Naopak když odstraníte relaci z diagramu, vždy odstraňujete ho z modelu.  
  
> [!NOTE]
>  Některé typy prvků v diagramu UML mají popisky. Když vyberete takovýchto prvků kreslením obdélník kolem sebe, je možné vybrat popisky, ale ne prvky, které vlastní tyto popisky. Odstranění podmnožinu prvků, které jsou vybrány tímto způsobem se nepodporuje. Pokud chcete vybrat podmnožinu těchto prvků, stiskněte a podržte **CTRL** klávesu klikněte na každý prvek.  
  
#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Odebrání třídění zobrazení diagramu  
  
- Klikněte pravým tlačítkem na elementu v diagramu a potom klikněte na **odebrat z diagramu**.  
  
  \- nebo –  
  
- Klikněte na tlačítko elementu v diagramu a potom stiskněte klávesu **odstranit** klíč.  
  
  -   Toto zobrazení elementu zmizí. Ale zůstává elementu v modelu a se stále nachází v **Průzkumníku modelů UML**. Zobrazení stejného elementu také zůstane.  
  
  -   Každý konektor, který končí na tento obrazec se odebere z diagramu, ale vztah představuje zůstane v modelu. Uvidíte relaci v **Průzkumníku modelů UML** pod **vztahy**, v části každý prvek, který se připojuje.  
  
#### <a name="to-delete-an-element-from-the-model"></a>Chcete-li odstranit prvek z modelu  
  
-   Klikněte pravým tlačítkem na element buď v **Průzkumníku modelů UML** nebo v diagramu a pak klikněte na tlačítko **odstranit z modelu**.  
  
    -   Prvek je odstraněn z každý diagram, ve kterém se zobrazí.  
  
    -   Každý vztah, který končí na tento element je také odstranit z modelu.  
  
#### <a name="to-delete-a-relationship-from-the-model"></a>Odstranění relace z modelu  
  
-   Klikněte pravým tlačítkem na vztah v diagramu nebo v **Průzkumníku modelů UML**a potom klikněte na tlačítko **odstranit z modelu**.  
  
    > [!CAUTION]
    >  Relaci nelze odebrat z diagramu bez odebrání z modelu.  
  
     Relace je odstranit z modelu a se odstraní ze všech diagramů, na kterém se zobrazí.  
  
##  <a name="presentation"></a> Příprava diagramu pro prezentaci  
 Tyto funkce umožňují přitažení pozornosti ke konkrétní části diagramu, přidejte vysvětlení nebo rozdělte diagramu do různých oblastí zájmu.  
  
-   Libovolnou část diagramu můžete zkopírovat do Word, PowerPoint nebo jiného dokumentu. Vyberte obrazců a konektorů, klikněte pravým tlačítkem a pak klikněte na tlačítko **kopírování**.  
  
-   Lze změnit barvu všech obrazec nebo spojnici. Vyberte jeden nebo více obrazců a změňte **barva** vlastnost. Pokud nevidíte **vlastnosti** okna, stisknutím klávesy **F4**.  
  
-   V diagramech některých druhů můžete kreslení čar, obdélníky a symbol tří teček z **jednoduché obrazce** části panelu nástrojů. Tyto obrazce netvoří součást modelu UML.  
  
-   Popisek oblasti, můžete přetáhnout komentář ze sady nástrojů a nastavte jeho **Transparent** vlastnost **True**. Jako jednoduché obrazce komentáře nejsou součástí modelu UML a nezobrazují se v Průzkumníku modelů UML.  
  
-   Přidat poznámky a vysvětlení k prvkům modelu, můžete vytvořit poznámky a propojit je s prvky.  
  
-   Chcete-li elegantně zarovnat sloupec nebo řádek tvary v diagramu, můžete nainstalovat příkazu Zarovnat obrazce. Tato možnost je dostupná jako ukázka rozšíření UML: [UML: příkaz pro zarovnání tvarů](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)  
  
### <a name="to-export-a-diagram-as-an-image"></a>Chcete-li exportovat diagram jako obrázek  
 Další informace najdete v tématu [exportování diagramů jako obrázků](../modeling/export-diagrams-as-images.md).  
  
##  <a name="extensions"></a> Rozšíření návrhářů UML  
 Můžete přidat nové funkce nástroje UML a přizpůsobit diagram zápis svých potřeb. Další informace najdete v tématu [modelů a diagramů UML rozšířit](../modeling/extend-uml-models-and-diagrams.md).  
  
 Nejsou k dispozici několik rozšíření vzorku. Můžete buď jen nainstalovat a používat je, nebo jejich zdrojový kód můžete použít jako základ pro vlastní rozšíření. Ukázky patří:  
  
|||  
|-|-|  
|[Zarovnání tvarů](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)|Příkaz nabídky, který vám pomůže přehledné diagramu.|  
|[Odkaz na webu docs](http://code.msdn.microsoft.com/Link-UML-elements-to-0adbf5a8)|Propojte libovolný prvek UML záhlaví Word, PowerPoint snímky, soubory libovolného typu, diagramy UML nebo další prvky UML. Propojení lze jednoduše přetažením. Později můžete dvakrát kliknout elementu, který chcete zobrazit propojenou položku. Můžete například propojit případy použití specifikace aplikace Word nebo diagramy činnosti podrobné a akce, které scénáře snímky.|  
|[Rychlé položka](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)|Rychlé vytváření modelu pomocí zadání textu. Užitečné pro zaznamenání myšlenky v schůzky.|  
|[Barva podle stereotypu](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Třídy barvy podle stereotypu. Můžete jednoduše rozšířit kód pro vlastní stereotypy.|  
|[Modelování domény](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4)|Vhodné výchozí hodnoty pro obchodní modely. Přidružení jsou zobrazeny bez šipek ve výchozím nastavení, a operace se nezobrazí ve třídách.|  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření modelování projektů a diagramů UML](../modeling/create-uml-modeling-projects-and-diagrams.md)   
 [Analýza a modelování vaší architektury](../modeling/analyze-and-model-your-architecture.md)   
 [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)



