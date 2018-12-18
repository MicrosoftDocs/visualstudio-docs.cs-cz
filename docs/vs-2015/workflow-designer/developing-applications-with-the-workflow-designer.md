---
title: Vývoj aplikací pomocí návrháře postupu provádění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 71cde900802543a21a20bc02e95bcfedc50d5541
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259152"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Vývoj aplikací pomocí návrháře postupu provádění
[!INCLUDE[wfd1](../includes/wfd1-md.md)] Vizuálního návrháře a ladicí program pro grafický procesu vytváření a ladění [!INCLUDE[wf](../includes/wf-md.md)] aplikací v [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] , která je hostována v [!INCLUDE[vs2010](../includes/vs2010-md.md)] vývojové prostředí. Umožňuje sestavit aplikace složený pracovního postupu, knihovna aktivit nebo [!INCLUDE[indigo1](../includes/indigo1-md.md)] službu pomocí šablony a návrháři aktivit. [!INCLUDE[crabout](../includes/crabout-md.md)] pracovní postupy, najdete v článku [Windows Workflow Foundation &#91;rozhraní .NET Framework 4&#93;](http://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
 Následuje několik nových funkcí návrhu, které tuto novou verzi nastavit [!INCLUDE[wfd2](../includes/wfd2-md.md)] kromě starší verze [!INCLUDE[wfd2](../includes/wfd2-md.md)]:  
  
-   [!INCLUDE[wfd2](../includes/wfd2-md.md)] Se vytvořil pomocí [!INCLUDE[avalon1](../includes/avalon1-md.md)]. To vylepšuje možnosti návrháře aktivit a zvyšuje výkon u velkých a složitých pracovních postupů.  
  
-   Vlastní aktivity jsou teď navržené s [!INCLUDE[avalon2](../includes/avalon2-md.md)], pomocí XAML a programovací model pro vytváření návrháři aktivit je zjednodušené.  
  
-   Vývojový diagram aktivity byl implementován, takže teď můžete zobrazit tok programu pomocí známých vývojový diagram modelování style.  
  
-   [!INCLUDE[wfd2](../includes/wfd2-md.md)] Má nové proměnné návrháře, který umožňuje deklarovat a nastavovat jejich obory proměnné v rámci své pracovní postupy jejich vazbu na aktivity.  
  
-   V [!INCLUDE[vs2010](../includes/vs2010-md.md)], [!INCLUDE[wfd2](../includes/wfd2-md.md)] poskytuje úplné funkce IntelliSense při vytváření výrazy jazyka Visual Basic v rámci vaší [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] pracovních postupů.  
  
-   Možnosti ladění teď rozšíří do XAML, což vám umožní nastavit zarážky v definici pracovního postupu XAML a krokování s vnořením do kódu XAML za běhu, který poskytuje podobné ve spravovaném kódu.  
  
-   Změna hostování [!INCLUDE[wfd2](../includes/wfd2-md.md)] mimo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je výrazně zjednodušené porovnání s předchozími verzemi současnosti vyžaduje jenom pár řádků kódu.  
  
-   Nové <xref:System.Activities.Statements.Flowchart> aktivita a její [vývojový diagram](../workflow-designer/flowchart-activity-designer.md) můžete vizualizovat váš tok programu pomocí známých vývojový diagram modelování style.  
  
-   Byly vylepšeny zasílání zpráv aktivity díky tomu umožňuje zapisovat plně deklarativního (žádný kód) [!INCLUDE[indigo1](../includes/indigo1-md.md)] služby.  
  
-   **Přidat odkaz na službu...** funkce umožňuje generovat aktivity automaticky, které k webovým službám.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Používání návrháře postupu provádění](../workflow-designer/using-the-workflow-designer.md)  
 Ukazuje, jak vytvořit nové aktivity a projekty pracovního postupu pomocí integrované návrháře a jak použít jiné nástroje poskytované systémem návrháře pro zpracování argumentů, proměnných, výrazů, importy a navigace s popisem cesty.  
  
 [Používání návrhářů aktivit](../workflow-designer/using-the-activity-designers.md)  
 Popisuje kategorie aktivit a šablony a jejich designery, které jsou k dispozici systému.  
  
 [Ladění pracovních postupů pomocí návrháře postupu provádění](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Popisují, jak provádět tradiční ladění procedur i ladění XAML a výrazy.  
  
 [Nápověda k uživatelskému rozhraní návrháře postupu provádění](../workflow-designer/workflow-designer-ui-help.md)  
 Obsahuje témata pro dialogová okna poskytuje kontextové nápovědy [!INCLUDE[wfd1](../includes/wfd1-md.md)], a také pokyny, funkce prostředí návrháře, klávesové zkratky a chybové zprávy.  
  
 [Vývoj aplikací pracovních postupů určených pro .NET Framework verze 3.0 nebo 3.5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Obsahuje pokyny, pomocí starší verze návrháře, který se zaměřuje [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 [Změna hostování návrháře &#91;ukázky WF&#93;](http://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 Tento příklad ukazuje, jak vytvořit rozložení WPF tak, aby obsahovala návrháře.  
  
 [Návrháři vlastních aktivit](http://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075)  
 Tato část obsahuje ukázkové aktivity, které používají vlastní návrháři zobrazení v Návrháři pracovních postupů.