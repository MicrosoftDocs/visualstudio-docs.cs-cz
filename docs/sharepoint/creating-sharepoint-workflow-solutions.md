---
title: Vytváření řešení pracovního postupu služby SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c4e808d93d2ae3039d4c5d79d1c14c65360bba32
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892308"
---
# <a name="create-sharepoint-workflow-solutions"></a>Vytváření řešení pracovního postupu služby SharePoint

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] poskytuje nástroje, které vám pomůžou vytvořit vlastní pracovní postupy, které spravují životní cyklus dokumenty a vypisovat položky ve webovém serveru SharePoint. Položky k dispozici zahrnují návrháře, sadu ovládacích prvků aktivity a odkazy na sestavení nezbytné. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zahrnuje také **Průvodce přizpůsobením SharePoint**, který pomáhá vytvářet a konfigurovat pracovní postupy.

Další informace o SharePoint, naleznete v tématu [Microsoft produktů a technologií SharePoint](http://go.microsoft.com/fwlink/?LinkId=178470).

## <a name="workflows-in-sharepoint"></a>Pracovní postupy v Sharepointu
 Když přidáte pracovní postup do knihovny SharePoint nebo seznam, vynucování obchodních procesů na všechny položky v seznamu nebo knihovně. Pracovní postup popisuje akce, které v systému nebo uživatelé musí provést pro každou položku, jako je odeslání položku, kterou chcete upravit a poté zkontrolovat. Tyto akce, označované jako *aktivity*, představují stavební kameny pracovního postupu.

 Můžete vytvářet pracovní postupy služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a nasaďte je u webu služby SharePoint. Po nasazení pracovního postupu služby SharePoint, přidružíte ho k knihovna nebo seznam. Umožní pak spuštění automaticky, proces, nebo ručně uživatelem. Další informace o operaci pracovního postupu najdete v tématu [pracovních postupů vývoj služby SharePoint pomocí sady Visual Studio](https://docs.microsoft.com/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Vytvoření vlastních pracovních postupů služby SharePoint
 Dva projekty pracovního postupu služby SharePoint jsou k dispozici v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **sekvenčního pracovního postupu** a **pracovní postup stavového stroje**.

 A *sekvenčního pracovního postupu* představuje posloupnost kroků. Kroky jsou prováděny jeden po druhém, dokud není dokončena poslední aktivita. Sekvenční pracovní postupy jsou vždy výhradně sekvenční při jejich provádění. Protože mohou přijímat externí události a zahrnovat paralelní logických toků, přesné pořadí provádění se mohou lišit. Následující obrázek znázorňuje příklad sekvenčního pracovního postupu.

 ![Sekvenční pracovní postup](../sharepoint/media/sp-sequential.png "sekvenčního pracovního postupu")

 A *pracovní postup stavového stroje* představuje sadu stavů, přechodů a akce. Kroky v pracovní postup stavového stroje spustit asynchronně. To znamená, že nejsou provedeny nutně jeden po druhém, ale místo toho se aktivují podle akcí a stavy. Jednoho stavu je přiřazen jako počáteční stav, a potom na základě události, je proveden přechod na jiný stav. Stavový počítač může mít koncový stav, který určuje konec pracovního postupu. Následující diagram ukazuje příklad pracovní postup stavového stroje.

 ![Stav pracovního postupu stroje](../sharepoint/media/sp-state.png "stavu počítače pracovního postupu")

 Další informace o typech pracovních postupů, najdete v části [typy pracovních postupů](http://go.microsoft.com/fwlink/?LinkId=178995).

### <a name="use-the-wizard"></a>Pomocí Průvodce
 Při vytváření projektu pracovního postupu služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Nejdřív musíte určit jeho nastavení v **Průvodce přizpůsobením SharePoint**. Toto nastavení používá průvodce k vytvoření projektu v **Průzkumníka řešení**. Tento projekt obsahuje soubor kódu, několik souborů, které jsou používány k nasazení pracovního postupu, a odkazy na sestavení, které jsou nutné k vytvoření vlastní pracovní postup služby SharePoint.

 Po vytvoření pracovního postupu jde upravit její vlastnosti v okně Vlastnosti. I když většina vlastností pracovního postupu lze změnit přímo v okně Vlastnosti, některé vyžadují, abyste klikněte na tlačítko se třemi tečkami (![ASP.NET – Návrhář mobilních řešení Elipsa](../sharepoint/media/mwellipsis.gif "elipsa ASP.NET – Návrhář mobilních řešení")) do změňte jejich hodnoty. Toto tlačítko restartuje **Průvodce přizpůsobením SharePoint**. Po provedení vlastnost hodnota změny, zvolte **Dokončit** tlačítko pro jejich dokončení.

> [!NOTE]
>  **Typ pracovního postupu** vlastnost je jen pro čtení a nedá se změnit. Pokud chcete změnit typ pracovního postupu, musíte vytvořit jiný pracovní postup.

## <a name="design-a-sharepoint-workflow"></a>Návrh pracovního postupu služby SharePoint
 Po definování všechny kroky v obchodním procesu použít [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] návrháře pracovních postupů pro návrh pracovního postupu služby SharePoint. Chcete-li otevřít Návrhář, dvakrát klikněte na panel Workflow1.cs nebo Workflow1.vb v **Průzkumníka řešení**, nebo otevřete místní nabídku pro jednu z těchto souborů a pak zvolte **otevřete**.

### <a name="activities"></a>Aktivity
 K návrhu pracovního postupu přidání aktivit z **nástrojů** k *pracovní postup plánu* v návrháři. Pracovní postup plánu obsahuje posloupnost aktivit v uvedeném pořadí, že má být provedena.

 Existují dva typy aktivit:

- *Jednoduché aktivity* provedení jedné jednotky práce, například jako ", než 1 den" nebo "spuštění webové služby."

- *Složené aktivity* obsahují další aktivity, například podmíněné aktivity může obsahovat dvě větve.

  Oba typy aktivit jsou k dispozici v **nástrojů**.

  Aktivity mohou mít vlastnosti, metody a události. Použití **vlastnosti** okna můžete nastavit vlastnosti aktivity.

  Můžete také vytvořit vlastní aktivitu. Další informace najdete v tématu [návod: vytvoření pracovního postupu aktivity vlastního webu](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Aktivity jsou uspořádány do následujících kartách v **nástrojů**:

- **Pracovní postup Sharepointu**

- **V3.0 pracovního postupu Windows**

- **Windows Workflow v3.5**

  Ne všechny aktivity pracovního postupu core jsou podporované službou SharePoint. Další informace najdete v tématu [přehled pracovního postupu aktivit pro Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="sharepoint-workflow-activities"></a>Aktivity pracovního postupu služby SharePoint
 **Pracovního postupu služby SharePoint** karty obsahují specializované aktivity pro použití v [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Tyto aktivity zjednoduší a zefektivní vývoje pracovních postupů životního cyklu dokumentů. Další informace o aktivitách, které jsou uvedeny v **pracovního postupu služby SharePoint** kartu, najdete v článku [přehled pracovního postupu aktivit pro Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="windows-workflow-activities"></a>Aktivity pracovního postupu Windows
 **Pracovního postupu Windows** karty obsahují aktivity, které jsou poskytovány [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. Vytváření plánů pracovního postupu pro libovolný typ aplikace pracovního postupu Windows můžete použít tyto aktivity.

 Další informace o aktivitách, které jsou uvedeny v **pracovních postupů Windows** kartu, najdete v článku [aktivity Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=156096). Další informace o modelu Windows Workflow Foundation, najdete v části [přehled Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=128632).

### <a name="work-with-activities-in-the-designer"></a>Práce s aktivitami v Návrháři
 Pracovní postup plánu může obsahovat kombinaci aktivity pracovního postupu Windows a aktivity pracovního postupu služby SharePoint.

 Návrhář zobrazí vizuální prvky můžete umístit a konfigurovat aktivity správně. Když jej přetáhnout nebo zkopírovat aktivitu do pracovního postupu plán, Návrhář zobrazí zeleně – znaménko plus (+) ikony, které ukazují platné umístění pro danou aktivitu v pracovním postupu. Aktivitu nelze umístit na místo, kde autoritou nebude platný. Například nelze umístit aktivity odeslání jako první aktivitu ve větvi naslouchání aktivity. Další informace najdete v tématu [středisko pro vývojáře aplikace SharePoint Designer](http://go.microsoft.com/fwlink/?LinkId=178476).

## <a name="collect-information-during-the-workflow"></a>Shromažďování informací během pracovního postupu
 Můžete chtít shromažďovat informace od uživatelů v předdefinované časy v pracovním postupu. Můžete shromažďovat informace prostřednictvím formulářů nebo vlastnosti položky.

### <a name="forms"></a>Formuláře
 Formuláře jsou jako dialogová okna, které obsahují dotazy a poskytují způsoby, jak uživatelům poskytnout odpovědi.

 Existují čtyři typy formulářů, které lze použít v pracovním postupu:

- Přidružení

- Zahájení

- Úpravy

- Úloha

  Z těchto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zahrnuje šablony položek pro formuláře pro asociaci a. Příklad *formulář přidružení* je ten, který umožňuje správci nainstalovat pracovního postupu zadejte parametry, které se vztahují k pracovnímu postupu, jako je nastavený limit útraty pro pracovní postup výdajů. Příklad *inicializační formulář* je ten, který umožňuje uživateli pracovního postupu výdajů zadejte velikost strávený do pracovního postupu. Další informace o těchto typech formuláře, naleznete v tématu [SharePoint šablony položek projektu a projekt](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Vlastnosti položky
 Pomocí vlastností položky v seznamu nebo knihovny služby SharePoint může také shromažďovat informace od uživatelů. Soubor hlavní kód (Workflow1.cs nebo Workflow1.vb) deklaruje instanci Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties třídy s názvem `workflowProperties`. Použití `workflowProperties` objektu pro přístup k vlastnostem knihovna nebo seznam v kódu. Příklad najdete v tématu [návod: vytváření a ladění řešení pracovního postupu služby SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Ladění šablony pracovního postupu služby SharePoint
 Můžete ladit projekt pracovního postupu služby SharePoint stejná jako ladění jiných [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] webové projekty. Při spuštění [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladicího programu, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] používá, které určíte v nastavení **Průvodce přizpůsobením SharePoint** otevřete příslušný web služby SharePoint a automaticky přidružit šablonu pracovního postupu s příslušnou knihovnu nebo seznamu. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] také připisuje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladicí program se má [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] proces s názvem *w3wp.exe*.

 K testování pracovního postupu, je nutné spustit ji ručně. Další informace najdete v části "Ladění pracovních postupech" v [ladění řešení služby SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Další informace o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Web ladění aplikací, přečtěte si [ladění webových aplikací a skriptu](../debugger/debugging-web-applications-and-script.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Nasazení šablony pracovního postupu služby SharePoint
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Projekty pracovního postupu služby SharePoint nasadit stejně jako ostatní [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektů služby SharePoint. Další informace najdete v tématu [balíčků a nasazení SharePoint řešení](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importovat globální opakovaně použitelných pracovních postupů
 Kromě vytvoření objektu pro určitou lokalitu opakovaně použitelných pracovních postupů, SharePoint Designer vám umožní vytvořit *globálně opakovaně použitelných pracovních postupů*, což jsou pracovní postupy, které mohou využívat všechny webu služby SharePoint. Projekt Import opakovaně použitelného pracovního postupu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aktuálně neimportuje globálně opakovaně použitelných pracovních postupů. Však můžete buď použijte k převedení globálně opakovaně použitelného pracovního postupu do opakovaně použitelného pracovního postupu návrháře služby SharePoint, nebo importovat pracovní postup jako nepřevedeném deklarativní pracovního postupu. Další informace najdete v tématu [Import položek z existující stránky SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Návod: Vytváření a ladění řešení pracovního postupu služby SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Vás provede vytvořením a ladění jednoduchý [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pracovního postupu.|
|[Návod: Vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Vás krok za krokem k vytvoření více plnohodnotné [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dokončení pracovního postupu pomocí formulářů přidružení a inicializace.|
|[Návod: Přidání stránky aplikace do pracovního postupu](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Navazuje na téma [návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) tak, že přidáte další *.aspx* stránku aplikace, která informuje o zadání dat do pracovního postupu.|
|[Návod: Vytvoření vlastní pracovní postup aktivity webu](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Ukazuje, jak provést dvě klíčové úlohy: vytvoření pracovního postupu úrovni webu a vytvořte vlastní pracovní aktivitu.|
|[Návod: Importujte opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Ukazuje, jak pro import opakovaně použitelných deklarativní pracovní postupy vytvořené v Návrháři SharePoint 2010 do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint.|

## <a name="see-also"></a>Viz také:

- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Vytváření stránek aplikací pro SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)