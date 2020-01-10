---
title: Vytváření projektů a diagramů modelování UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 52c55b2cfdf000d91a83071b53e8e9450187b720
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852020"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Vytváření projektů a diagramů pomocí modelování UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modely UML vám pomůžou pochopit, diskutovat a navrhovat softwarové systémy. Visual Studio poskytuje šablony pro pět nejčastěji používaných diagramů UML: aktivita, třída, komponenta, sekvence a případ použití. Kromě toho můžete vytvářet diagramy vrstev, které vám pomohou definovat strukturu systému.

 Diagramy modelování UML a diagramy vrstev mohou existovat pouze v rámci projektu modelování. Každý projekt modelování obsahuje sdílený model UML a několik diagramů UML. Každý diagram je částečný pohled na model. Model UML obsahuje všechny prvky v diagramech UML a lze jej zobrazit pomocí Průzkumníka modelů UML. Informace o modelech a jejich vztahu k diagramům najdete v tématu [Úprava modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md). Informace o projektech modelování v rámci správy verzí naleznete v tématu [Správa modelů a diagramů v rámci správy verzí](../modeling/manage-models-and-diagrams-under-version-control.md) a [Strukturování řešení modelování](../modeling/structure-your-modeling-solution.md) .

> [!NOTE]
> Je k dispozici jiný druh diagramu, diagram tříd .NET, který slouží k vizualizaci kódu programu. Další informace najdete v tématu [navrhování a zobrazování tříd a typů](https://msdn.microsoft.com/library/ab7aty24.aspx).

## <a name="CreatingModelingDiagrams"></a>Vytvoření diagramu v projektu modelování
 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Vytvoření diagramu a jeho přidání do projektu

1. V nabídce **Architektura** vyberte **Nový UML nebo Diagram vrstev**.

2. V dialogovém okně **Přidat nový diagram** klikněte na typ diagramu modelování, který chcete.

    ![Přidat nový diagram – dialogové okno](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. Zadejte název nového diagramu.

4. V poli **Přidat do modelování projektu** :

   - Vyberte projekt modelování, který již existuje ve vašem řešení, a klikněte na tlačítko **OK**.

     \- nebo –

   1. Vyberte **vytvořit nový projekt modelování**a pak klikněte na **OK**.

   2. V dialogovém okně **vytvořit nový projekt modelování** zadejte název a umístění nového projektu a pak klikněte na **OK**.

        ![Dialogové okno vytvořit nový projekt modelování](../modeling/media/uml-createmodel.png "UML_CreateModel")

        Pokud je vaše řešení otevřené, přidá se do řešení nový projekt. Pokud nemáte otevřené řešení, můžete zadat název nového řešení.

   Pokud již máte projekt modelování, můžete použít také následující postup.

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Přidání diagramu do existujícího projektu modelování

1. V **Průzkumník řešení**klikněte na uzel modelování projektu.

    > [!NOTE]
    > Projekt modelování obsahuje složku definice modelu s názvem **ModelDefinition**.

2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

3. V dialogovém okně **Přidat novou položku –** *\<název projektu >* v části **šablony**klikněte na typ diagramu modelování, například **Diagram komponent UML**.

4. Zadejte název diagramu a pak klikněte na **Přidat**.

     Diagram modelování se otevře a zobrazí se v projektu modelování.

    > [!CAUTION]
    > Nepřidávat, kopírovat ani přetahovat existující soubory diagramu do jiných projektů modelování ani do jiných umístění v řešení. To způsobí, že prvky zmizí ze zkopírovaných diagramů nebo chyb, ke kterým dojde, když otevřete diagramy. Je nutné otevřít soubor diagramu z projektu modelování, ve kterém byl vytvořen. Je to proto, že diagram UML je zobrazení modelu, který vlastní projekt modelování. Chcete-li zkopírovat soubor diagramu, vytvořte nový diagram a potom zkopírujte prvky ze zdrojového diagramu do nového diagramu. Další informace najdete v tématu [řešení potíží s modelováním projektů a diagramů](#TroubleshootingModelingProjects).

#### <a name="to-create-a-blank-modeling-project"></a>Vytvoření prázdného projektu modelování

1. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

2. V dialogovém okně **Nový projekt** klikněte v části **Nainstalované šablony**na **modelování projektů**.

3. V prostředním okně klikněte na **modelování projektu**.

4. Pojmenujte projekt a zadejte umístění do polí **název** a **umístění** .

5. V poli **řešení** vyberte **Přidat do řešení** a přidejte nový projekt do řešení, které už máte otevřené. nebo můžete **vytvořit nové řešení** a zavřít otevřené řešení a přidat projekt do nového řešení.

## <a name="RemovingModelingDiagrams"></a>Odebrání diagramů modelování z projektu
 Diagram můžete trvale odstranit, nebo můžete z projektu dočasně vyloučit diagram a pak ho obnovit.

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Postup trvalého odstranění diagramu z projektu

- V **Průzkumník řešení**klikněte pravým tlačítkem myši na hlavní soubor, který představuje diagram, a pak klikněte na **Odstranit**.

     Diagram se odebere z projektu a systému souborů. Prvky zobrazené v diagramu nejsou odebrány z **Průzkumníka modelů UML**.

    > [!NOTE]
    > Každý diagram má dva soubory, jednu pobočku do druhé. Například pokud máte diagram komponent s názvem `CD1`, měli byste odstranit soubor s názvem `CD1.componentdiagram`. Soubor dceřiné společnosti s názvem `CD1.componentdiagram.layout` bude automaticky odstraněn.

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Dočasné vyloučení diagramu z projektu

- V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor diagramu a pak klikněte na **vyloučit z projektu**.

     Diagram se odebere z projektu. Není odebrán ze systému souborů.

    > [!NOTE]
    > Prvky zobrazené v diagramu nejsou odebrány z **Průzkumníka modelů UML**.

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Postup obnovení dočasně vyloučeného diagramu do projektu

1. V **Průzkumník řešení**klikněte na uzel modelování projektu.

    > [!NOTE]
    > Projekt modelování obsahuje složku definice modelu s názvem **ModelDefinition**.

2. V nabídce **projekt** klikněte na položku **Přidat existující položku**.

3. V dialogovém okně **Přidat existující položku** vyhledejte soubor diagramu, vyberte soubor a klikněte na tlačítko **Přidat**.

     Diagram modelování se otevře a zobrazí se v projektu modelování.

    > [!NOTE]
    > Každý diagram obsahuje dvojici souborů v systému souborů. Nevybírejte soubor, který má `.layout`rozšíření. Visual Studio také nepodporuje přidávání existujících diagramů UML do více projektů modelování. Každý soubor diagramu musí být otevřen v rámci projektu modelování, ve kterém byl vytvořen. Je to proto, že diagram UML zobrazuje zobrazení modelu, který vlastní projekt modelování.

## <a name="NonModelDiagrams"></a>Diagramy, které nevyžadují modelování projektů
 Následující typy diagramů nejsou součástí projektu modelování:

- Diagramy tříd, které jsou vytvořeny jako zobrazení zdrojového kódu. Nesouvisejí s diagramy tříd UML. Další informace najdete v tématu [navrhování a zobrazování tříd a typů](../ide/designing-and-viewing-classes-and-types.md).

- Mapy kódu. Zobrazit [mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md).

- Diagramy, které nejsou diagramy UML nebo diagramy vrstev, například jazyky specifické pro doménu.

## <a name="TroubleshootingModelingProjects"></a>Řešení potíží s modelováním projektů a diagramů
 Následující tabulka popisuje problémy, které mohou nastat v projektech modelování nebo diagramech a jejich řešení:

|**Problém**|**Mít**|**Řešení**|
|---------------|----------------|--------------------|
|Projekt modelování nelze otevřít nebo načíst do řešení.<br /><br /> Zobrazí se zpráva s informacemi o tom, že<br /><br /> Jeden nebo více projektů v řešení nebylo načteno správně. Podrobnosti najdete v okno Výstup. "<br /><br /> V okně výstup se zobrazí následující zpráva:<br /><br /> "*ModelingProjectFilenameAndPath*. modelproj: Error: nerozpoznaný formát GUID"|Projekt modelování má odkazy na projekty, které mají stejný název a jsou ve stejném řešení.<br /><br /> Například vrstva je propojena s projekty, které mají stejný název a jsou ve stejném řešení.|Pomocí textového editoru otevřete soubor projektu modelování, odeberte odkazy a pak zkuste projekt modelování znovu otevřít.<br /><br /> Chcete-li se tomuto problému vyhnout, nepřidávejte odkazy na projekty, které mají stejný název. Ujistěte se, že projekty mají jedinečné názvy.|
|V diagramech, které jsou přidány, zkopírovány nebo přetaženy na jiné projekty modelování nebo na jiná umístění v řešení, chybí prvky.<br /><br /> - nebo -<br /><br /> Při pokusu o otevření diagramu se zobrazí následující zprávy:<br /><br /> -"Některé obrazce nebo konektory v diagramu chybí, protože jejich definice v tomto projektu neexistují. Z modelu byly odstraněny buď definice v době, kdy byl diagram zavřen, nebo byl diagram zkopírován do jiného projektu, který tyto definice neobsahuje. "<br /><br /> - nebo -<br /><br /> – "Tento dokument je otevřen jiným projektem."|Soubor diagramu byl přidán, přetažen nebo zkopírován z projektu modelování do jiného projektu modelování nebo do jiného umístění v řešení.|Chcete-li zkopírovat soubor diagramu, vytvořte nový diagram a potom zkopírujte prvky ze zdrojového diagramu do nového diagramu.|

## <a name="see-also"></a>Viz také
 [Úprava modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md) [struktury řešení modelování](../modeling/structure-your-modeling-solution.md)
