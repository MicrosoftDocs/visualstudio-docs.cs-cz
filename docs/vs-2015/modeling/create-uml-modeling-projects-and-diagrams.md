---
title: Vytvářet projekty modelování UML a diagramy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5d841c9fde677eb4a8fb17e952a817364dab277e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738400"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Vytváření projektů a diagramů pomocí modelování UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modely UML pomůžou pochopit, popisují a návrh softwarové systémy. Visual Studio poskytuje šablony pro pět nejčastěji používané diagramy UML: aktivita, třídy, komponenty, pořadí a případ použití. Kromě toho můžete vytvořit diagramy vrstev, které vám pomůžou definovat strukturu systému.  
  
 Diagramy modelování UML a diagramy vrstev může existovat pouze v projektu modelování. Každý projekt modelování obsahuje sdílené modelu UML a několika diagramů UML. Každý diagram je částečné zobrazení modelu. UML model obsahuje všechny prvky v diagramech UML a lze je zobrazit pomocí Průzkumníka modelů UML. Informace o modelech a jejich vztah k diagramů naleznete v tématu [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md). Informace o modelování projektů do správy verzí, naleznete v tématu [Správa modelů a diagramů pomocí správy verzí](../modeling/manage-models-and-diagrams-under-version-control.md) a [strukturování řešení modelování](../modeling/structure-your-modeling-solution.md)  
  
> [!NOTE]
>  Existuje jiný typ diagramu, diagram tříd .NET, který slouží k vizualizaci kódu programu. Další informace najdete v tématu [navrhování a zobrazování tříd a typů](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
##  <a name="CreatingModelingDiagrams"></a> Vytvoření diagramu v projektu modelování  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Vytvoření diagramu a přidat do projektu  
  
1. Na **architektura** nabídce zvolte **nové UML nebo diagramu vrstev**.  
  
2. V **přidat nový Diagram** dialogovém okně klikněte na typ diagramu modelování, který chcete.  
  
    ![Přidat nový Diagram dialog](../modeling/media/uml-adddiagram.png "UML_AddDiagram")  
  
3. Zadejte název pro nový diagram.  
  
4. V **přidat do projektu modelování** pole:  
  
   - Vyberte projekt modelování, který již existuje ve vašem řešení a potom klikněte na tlačítko **OK**.  
  
     \- nebo –  
  
   1.  Vyberte **vytvořte nový projekt modelování**a potom klikněte na tlačítko **OK**.  
  
   2.  V **vytvořit nový projekt modelování** dialogové okno, zadejte název a umístění nového projektu a pak klikněte na tlačítko **OK**.  
  
        ![Vytvoření dialogového okna Nový projekt modelování](../modeling/media/uml-createmodel.png "UML_CreateModel")  
  
        Pokud vaše řešení je otevřen, nový projekt je přidán do řešení. Pokud máte žádné otevřené řešení, můžete zadat název nového řešení.  
  
   Pokud už máte v modelovacím projektu, můžete také použít následující postup.  
  
#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Přidání diagramu do existujícího projektu modelování  
  
1.  V **Průzkumníka řešení**, modelování klikněte na uzel projektu.  
  
    > [!NOTE]
    >  Projekt modelování obsahuje definici modelu složku s názvem **ModelDefinition**.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
3.  V **přidat novou položku -**  *\<název projektu >* dialogovém okně **šablony**, klikněte na tlačítko modelování diagram typu, například **UML Diagram komponent**.  
  
4.  Zadejte název diagramu a potom klikněte na tlačítko **přidat**.  
  
     Diagram modelování se otevře a zobrazí se v projektu modelování.  
  
    > [!CAUTION]
    >  Přidat, kopírovat nebo přetáhnout existujících souborů diagramu na jiné projekty modelování nebo na jiná místa v řešení. To způsobí, že prvky zmizí ze zkopírovaného diagramů nebo chyby při otevření diagramy. Je nutné otevřít soubor diagramu z projektu modelování, ve kterém byla vytvořena. Toto je UML diagram je zobrazení modelu, který je vlastněn svůj projekt modelování. Zkopírujte soubor diagramu, vytvoření nového diagramu a potom zkopírujte prvky ze zdrojového diagramu do nového diagramu. Další informace najdete v tématu [řešení potíží s projekty modelování a diagramy](#TroubleshootingModelingProjects).  
  
#### <a name="to-create-a-blank-modeling-project"></a>Chcete-li vytvořit prázdný projekt pro modelování  
  
1.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** dialogovém okně **nainstalované šablony**, klikněte na tlačítko **projekty modelování**.  
  
3.  V prostředním okna, klikněte na tlačítko **projekt modelování**.  
  
4.  Pojmenujte projekt a zadejte umístění v **název** a **umístění** polí.  
  
5.  V **řešení** vyberte **přidat do řešení** přidat nový projekt do řešení již otevřeného; nebo **vytvořit nové řešení** zavřete všechny otevřené řešení a přidat projekt k novému řešení.  
  
##  <a name="RemovingModelingDiagrams"></a> Odebrání diagramů z projektu modelování  
 Můžete trvale odstranit diagramu, nebo můžete dočasně vyloučit diagramu z projektu a jeho následnému obnovení.  
  
#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Diagram trvale odstranit z projektu  
  
-   V **Průzkumníka řešení**, klikněte pravým tlačítkem na hlavní soubor, který představuje diagramu a potom klikněte na tlačítko **odstranit**.  
  
     Diagram se odebere z projektu a systému souborů. Prvky zobrazené v diagramu nejsou odebrány z **Průzkumníku modelů UML**.  
  
    > [!NOTE]
    >  Každý diagram má dva soubory, pobočka jeden na druhý. Například, pokud máte diagramu komponent s názvem `CD1`, odstraňte soubor s názvem `CD1.componentdiagram`. Jeho pomocný soubor s názvem `CD1.componentdiagram.layout` automaticky odstraní.  
  
#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Dočasné vyloučit diagramu z projektu  
  
-   V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor diagramu a potom klikněte na tlačítko **vyjmout z projektu**.  
  
     Diagram se odebere z projektu. Odebere se ze systému souborů.  
  
    > [!NOTE]
    >  Prvky zobrazené v diagramu nejsou odebrány z **Průzkumníku modelů UML**.  
  
#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Chcete-li obnovit dočasně vyloučené diagram do projektu  
  
1.  V **Průzkumníka řešení**, modelování klikněte na uzel projektu.  
  
    > [!NOTE]
    >  Projekt modelování obsahuje definici modelu složku s názvem **ModelDefinition**.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.  
  
3.  V **přidat existující položku** dialogovém okně vyhledejte soubor diagramu, vyberte soubor a potom klikněte na tlačítko **přidat**.  
  
     Diagram modelování se otevře a zobrazí se v projektu modelování.  
  
    > [!NOTE]
    >  Každý diagram nemá dvojici souborů v systému souborů. Nesmí být zvolen soubor, který má příponu `.layout`. Visual Studio navíc nepodporuje přidávání existujících diagramů UML do více projektů modelování. Každý diagram soubor musí být otevřen v rámci projektu modelování, ve kterém byla vytvořena. Je to proto diagramu UML se teď zobrazují modelu, který je vlastněn svůj projekt modelování.  
  
##  <a name="NonModelDiagrams"></a> Diagramy, které nevyžadují žádné projekty modelování  
 Následující typy diagramů nejsou součástí projektu modelování:  
  
-   Diagramy tříd, které jsou vytvořeny jako zobrazení zdrojového kódu. Tyto nesouvisejí s diagramy tříd UML. Další informace najdete v tématu [navrhování a zobrazování tříd a typů](../ide/designing-and-viewing-classes-and-types.md).  
  
-   Mapy kódu. Zobrazit [mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md).  
  
-   Diagramy, které nejsou v diagramech UML nebo diagramy vrstev, jako je například konkrétní jazyky domény.  
  
##  <a name="TroubleshootingModelingProjects"></a> Řešení potíží s projekty modelování a diagramy  
 Následující tabulka popisuje problémy, které mohou nastat u projektů nebo diagramy a způsob jejich řešení modelování:  
  
|**Problém**|**Způsobí, že**|**Řešení**|  
|---------------|----------------|--------------------|  
|Nejde otevřít nebo načtena do řešení projekt modelování.<br /><br /> Zobrazí se následující zpráva:<br /><br /> "Jeden nebo více projektů v řešení nebylo správně načteno. Podrobnosti najdete ve výstupním okně Podrobnosti."<br /><br /> V okně výstupu se zobrazí následující zpráva:<br /><br /> "*ModelingProjectFilenameAndPath*.modelproj: Chyba: Neznámý identifikátor Guid formátu."|Projekt modelování obsahuje odkazy na projekty, které mají stejný název a jsou ve stejném řešení.<br /><br /> Například vrstva je propojen s projekty, které mají stejný název a jsou ve stejném řešení.|Pomocí textového editoru otevřete projekt modelování soubor, odeberte odkazy a pak zkuste znovu otevřít projekt modelování.<br /><br /> K tomuto problému vyhnout, nepřidávejte odkazy na projekty, které mají stejný název. Ujistěte se, že projekty mají jedinečné názvy.|  
|Prvky jsou chybí diagramy, které jsou přidány, zkopírovat nebo přetáhnout na jiné projekty modelování nebo na jiná místa v řešení.<br /><br /> - nebo -<br /><br /> Při pokusu o otevření diagramu se zobrazí následující zprávy:<br /><br /> -"Nějaké obrazce konektorů v diagramu chybí nebo protože jejich definice neexistuje v tomto projektu. Buď definice byly odstraněny z modelu bylo ukončeno diagramu nebo diagramu byl zkopírován do jiného projektu, který neobsahuje tyto definice."<br /><br /> - nebo -<br /><br /> -"Tento dokument je otevřen v jiném projektu."|Soubor diagramu byl přidán, kvůli usnadnění použití vypsány nebo zkopírován z projektu modelování do jiného projektu modelování nebo do jiného umístění v řešení.|Zkopírujte soubor diagramu, vytvoření nového diagramu a potom zkopírujte prvky ze zdrojového diagramu do nového diagramu.|  
  
## <a name="see-also"></a>Viz také  
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Strukturování řešení modelování](../modeling/structure-your-modeling-solution.md)



