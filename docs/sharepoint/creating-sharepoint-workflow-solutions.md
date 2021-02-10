---
title: Vytváření řešení pracovního postupu služby SharePoint | Microsoft Docs
description: Vytvářejte řešení pracovního postupu služby SharePoint pomocí nástrojů a vytvářejte vlastní pracovní postupy, které spravují životní cyklus dokumentů a položek seznamu na SharePointových webech.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 28a5bc44b0f6fa04d32c574e9772369709736ddd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949074"
---
# <a name="create-sharepoint-workflow-solutions"></a>Vytváření řešení pracovního postupu služby SharePoint

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] poskytuje nástroje, které vám pomůžou vytvořit vlastní pracovní postupy, které spravují životní cyklus dokumentů a položek seznamu na webu SharePointu. K dispozici jsou tyto položky: Návrhář, sada ovládacích prvků aktivity a nezbytné odkazy na sestavení. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsahuje taky **Průvodce přizpůsobením SharePointu**, který vám umožní vytvořit a nakonfigurovat pracovní postupy.

Další informace o SharePointu naleznete v tématu [produkty a technologie Microsoft SharePoint](/sharepoint/dev/).

## <a name="workflows-in-sharepoint"></a>Pracovní postupy ve službě SharePoint
 Když přidáte pracovní postup do knihovny nebo seznamu služby SharePoint, vynutili jste obchodní proces na všech položkách v knihovně nebo seznamu. Pracovní postup popisuje akce, které musí systém nebo uživatelé provádět u každé položky, jako je například odeslání položky, která má být upravena a poté revidována. Tyto akce, označované jako *aktivity*, představují stavební kameny pracovního postupu.

 Můžete vytvářet pracovní postupy služby SharePoint v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a nasazovat je na web služby SharePoint. Po nasazení pracovního postupu do SharePointu ho přidružíte k knihovně nebo seznamu. Pak ji může spustit automaticky, proces nebo ručně uživatel. Další informace o operaci pracovního postupu najdete v tématu [Vývoj pracovních postupů služby SharePoint pomocí sady Visual Studio](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Vytváření vlastních pracovních postupů služby SharePoint
 K dispozici jsou dva projekty pracovního postupu služby SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] : **sekvenční pracovní** postup a **pracovní postup stavového stroje**.

 *Sekvenční pracovní postup* představuje posloupnost kroků. Kroky jsou provedeny po druhém až do dokončení poslední aktivity. Sekvenční pracovní postupy jsou vždy výhradně sekvenční při jejich provádění. Vzhledem k tomu, že mohou přijímat externí události a začlenit paralelní logiky toků, přesné pořadí spuštění se může lišit. Následující ilustrace znázorňuje příklad sekvenčního pracovního postupu.

 ![Sekvenční pracovní postup](../sharepoint/media/sp-sequential.png "Sekvenční pracovní postup")

 *Pracovní postup stavového stroje* představuje sadu stavů, přechodů a akcí. Kroky v pracovním postupu stavového stroje se spouštějí asynchronně. To znamená, že nejsou nutně provedeny po jiné, ale jsou aktivovány akcemi a stavy. Jeden stav je přiřazen jako počáteční stav a následně je proveden přechod na základě události do jiného stavu. Stavový počítač může mít konečný stav, který určuje konec pracovního postupu. Následující diagram znázorňuje příklad pracovního postupu stavového stroje.

 ![Pracovní postup stavového stroje](../sharepoint/media/sp-state.png "Pracovní postup stavového stroje")

 Další informace o typech pracovních postupů najdete v tématu [typy pracovních postupů](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14)).

### <a name="use-the-wizard"></a>Použití Průvodce
 Při vytváření projektu pracovního postupu služby SharePoint v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] je třeba nejprve zadat jeho nastavení v **Průvodci vlastním nastavením služby SharePoint**. Průvodce používá tato nastavení k vytvoření projektu v **Průzkumník řešení**. Tento projekt obsahuje soubor kódu, několik souborů, které se používají k nasazení pracovního postupu, a odkazy na sestavení, která jsou nutná k vytvoření vlastního pracovního postupu služby SharePoint.

 Po vytvoření pracovního postupu můžete změnit jeho vlastnosti v okno Vlastnosti. I když většinu vlastností pracovního postupu lze změnit přímo v okno Vlastnosti, některé z nich vyžadují, abyste kliknutím na tlačítko se třemi tečkami (![elipsa ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")) změnili jejich hodnoty. Toto tlačítko spustí **Průvodce vlastním nastavením služby SharePoint**. Po provedení změny hodnoty vlastnosti klikněte na tlačítko **Dokončit** a dokončete je.

> [!NOTE]
> Vlastnost **Typ pracovního postupu** je určena jen pro čtení a nelze ji změnit. Chcete-li změnit typ pracovního postupu, je nutné vytvořit jiný pracovní postup.

## <a name="design-a-sharepoint-workflow"></a>Návrh pracovního postupu služby SharePoint
 Po definování všech kroků v obchodním procesu můžete pomocí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] návrháře pracovních postupů navrhnout pracovní postup služby SharePoint. Chcete-li otevřít návrháře, dvakrát klikněte na Workflow1.cs nebo Workflow1. vb v **Průzkumník řešení**, nebo otevřete místní nabídku pro některý z těchto souborů a pak zvolte možnost **otevřít**.

### <a name="activities"></a>Aktivity
 Chcete-li navrhnout pracovní postup, přidejte aktivity ze **sady nástrojů** do *plánu pracovního postupu* v návrháři. Plán pracovního postupu obsahuje posloupnost aktivit v pořadí, ve kterém by se měly provádět.

 Existují dva typy aktivit:

- *Jednoduché aktivity* provádějí jednu pracovní jednotku, například "zpoždění za 1 den" nebo "spustit webovou službu".

- *Složené aktivity* obsahují další aktivity; podmíněná aktivita může například obsahovat dvě větve.

  Oba typy aktivit jsou k dispozici v **sadě nástrojů**.

  Aktivity mohou mít vlastnosti, metody a události. K nastavení vlastností aktivity použijte okno **vlastnosti** .

  Můžete také vytvořit vlastní aktivitu. Další informace najdete v tématu [Návod: Vytvoření vlastní aktivity pracovního postupu webu](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Aktivity jsou uspořádány na následujících kartách v **sadě nástrojů**:

- **Pracovní postup služby SharePoint**

- **Windows Workflow v 3.0**

- **Windows Workflow v 3.5**

  Služba SharePoint nepodporuje všechny základní aktivity pracovního postupu. Další informace najdete v tématu [aktivity pracovního postupu pro službu Windows SharePoint Services – přehled](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="sharepoint-workflow-activities"></a>Aktivity pracovního postupu SharePointu
 Karty **pracovního postupu služby SharePoint** obsahují specializované aktivity pro použití v nástroji [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] . Tyto aktivity zjednodušují a zjednodušují vývoj pracovních postupů pro životní cyklus dokumentů. Další informace o aktivitách uvedených na kartě **pracovní postup služby SharePoint** najdete v tématu [aktivity pracovního postupu pro službu Windows SharePoint Services – přehled](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="windows-workflow-activities"></a>Aktivity pracovního postupu Windows
 Karty **pracovního postupu Windows** obsahují aktivity, které jsou k dispozici v [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] . Tyto aktivity můžete použít k vytvoření plánů pracovního postupu pro libovolný druh aplikace Windows Workflow.

 Další informace o aktivitách uvedených na kartě **pracovní postupy systému Windows** najdete v tématu [aktivity programovací model Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)). Další informace o programovací model Windows Workflow Foundation najdete v tématu [programovací model Windows Workflow Foundation Overview](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90)).

### <a name="work-with-activities-in-the-designer"></a>Práce s aktivitami v Návrháři
 Plán pracovního postupu může obsahovat kombinaci aktivit pracovních postupů Windows a aktivit pracovních postupů služby SharePoint.

 Návrhář zobrazí vizuální pomůcky, které vám pomůžou správně umístit a nakonfigurovat aktivity. Když přetáhnete nebo zkopírujete aktivitu do plánu pracovního postupu, Návrhář zobrazí zelenou ikonu znaménka plus (+), která zobrazí platná umístění pro tuto aktivitu v pracovním postupu. Aktivitu nelze umístit do umístění, kde by nebylo platné. Například nemůžete umístit aktivitu odeslání jako první aktivitu ve větvi aktivity naslouchání. Další informace najdete v tématu [středisko pro vývojáře návrháře služby SharePoint](https://developer.microsoft.com/office/docs).

## <a name="collect-information-during-the-workflow"></a>Shromažďování informací během pracovního postupu
 Je možné, že budete chtít shromažďovat informace od uživatelů v předdefinovaných časech pracovního postupu. Informace můžete shromažďovat pomocí vlastností formulářů nebo položek.

### <a name="forms"></a>Formuláře
 Formuláře jsou jako dialogová okna, která obsahují otázky a poskytují uživatelům možnosti pro poskytování odpovědí.

 Existují čtyři typy formulářů, které lze použít v pracovním postupu:

- Řídí

- Odůvodňují

- Úprava

- Úkol

  Z těchto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] důvodů zahrnuje šablony položek pro přidružení a inicializační formuláře. Příkladem *formuláře přidružení* je, který umožňuje správci nainstalovat pracovní postup zadáním parametrů, které se vztahují k pracovnímu postupu, jako je limit útraty pro pracovní postup výdaje. Příkladem *inicializačního formuláře* je ten, který umožňuje uživateli pracovního postupu výdajů zadat množství, které strávil do pracovního postupu. Další informace o těchto typech formulářů naleznete v tématu [šablony projektů a položek projektu služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Vlastnosti položky
 Můžete také shromažďovat informace od uživatelů pomocí vlastností položky v knihovně nebo seznamu služby SharePoint. Hlavní soubor kódu (Workflow1.cs nebo Workflow1. vb) deklaruje instanci třídy Microsoft. SharePoint. Workflow. SPWorkflowActivationProperties. WorkflowProperties s názvem `workflowProperties` . Použijte `workflowProperties` objekt pro přístup k vlastnostem knihovny nebo seznamu v kódu. Příklad najdete v tématu [Návod: vytvoření a ladění řešení pracovního postupu služby SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Ladění šablony pracovního postupu služby SharePoint
 Projekt pracovního postupu služby SharePoint můžete ladit stejně jako ladění dalších [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] webových projektů. Když spustíte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladicí program, nástroj [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] použije nastavení, které zadáte v **Průvodci přizpůsobením SharePointu** , a otevře příslušný web SharePointu a automaticky přiřadí šablonu pracovního postupu k příslušné knihovně nebo seznamu. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Nástroj také připojí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladicí program k [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] procesu s názvem *w3wp.exe*.

 Chcete-li otestovat pracovní postup, je nutné jej spustit ručně. Další informace najdete v části "pracovní postupy ladění" v tématu [ladění řešení služby SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Další informace o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladění webových aplikací najdete v tématu [ladění webových aplikací a skriptů](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Nasazení šablony pracovního postupu služby SharePoint
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Projekty pracovního postupu služby SharePoint se nasazují stejně jako jiné [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty služby SharePoint. Další informace najdete v tématech [balíček a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Import globálně opakovaně použitelných pracovních postupů
 Kromě vytváření opakovaně použitelných pracovních postupů pro konkrétní lokalitu umožňuje SharePoint Designer vytvářet *globálně opakovaně použitelné pracovní postupy*, což jsou pracovní postupy, které mohou být použity na libovolném webu služby SharePoint. Projekt importovat opakovaně použitelný pracovní postup v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] současné době neimportuje globálně opakovaně použitelné pracovní postupy. Můžete však použít SharePoint Designer k převedení globálně opakovaně použitelného pracovního postupu na opakovaně použitelný pracovní postup nebo importovat pracovní postup jako nepřevedený deklarativní pracovní postup. Další informace najdete v tématu [Import položek z existujícího webu služby SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Návod: vytvoření a ladění řešení pracovního postupu služby SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Provede vás podrobným vytvořením a laděním jednoduchého [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pracovního postupu.|
|[Návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Provede vás krok za krokem k vytvoření efektivnějšího [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pracovního postupu, který se dokončí pomocí formulářů přidružení a inicializace.|
|[Návod: Přidání stránky aplikace do pracovního postupu](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Sestavení v tématu [Návod: vytvoření pracovního postupu s formuláři přidružení a iniciace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) přidáním další stránky aplikace *aspx* , která oznamuje data zadaná do pracovního postupu.|
|[Návod: Vytvoření vlastní aktivity pracovního postupu webu](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Ukazuje, jak provést dvě klíčové úlohy: vytvořit pracovní postup na úrovni webu a vytvořit vlastní aktivitu pracovního postupu.|
|[Návod: import opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Ukazuje, jak importovat opakovaně použitelné deklarativní pracovní postupy, které byly vytvořeny v aplikaci SharePoint Designer 2010, do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint.|

## <a name="see-also"></a>Viz také

- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Vytváření stránek aplikací pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)