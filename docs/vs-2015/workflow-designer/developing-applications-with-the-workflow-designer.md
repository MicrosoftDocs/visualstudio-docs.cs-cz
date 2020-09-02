---
title: Vývoj aplikací pomocí Návrhář postupu provádění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848300c54800e229ee1f487fc415bad45d982a6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656827"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Vývoj aplikací pomocí Návrháře postupu provádění
[!INCLUDE[wfd1](../includes/wfd1-md.md)]Je vizuální Návrhář a ladicí program pro grafické vytváření a ladění [!INCLUDE[wf](../includes/wf-md.md)] aplikací v [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] , které jsou hostovány ve [!INCLUDE[vs2010](../includes/vs2010-md.md)] vývojovém prostředí. Umožňuje vytvořit složenou aplikaci pracovního postupu, knihovnu aktivit nebo [!INCLUDE[indigo1](../includes/indigo1-md.md)] službu prostřednictvím použití šablon a návrhářů aktivit. [!INCLUDE[crabout](../includes/crabout-md.md)] pracovní postupy najdete v [&#93;programovací model Windows Workflow Foundation &#91; .NET Framework 4 ](https://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Následující seznam obsahuje několik nových funkcí návrhu, které nastavují tuto novou verzi [!INCLUDE[wfd2](../includes/wfd2-md.md)] kromě starších verzí nástroje [!INCLUDE[wfd2](../includes/wfd2-md.md)] :

- [!INCLUDE[wfd2](../includes/wfd2-md.md)]Je sestaven pomocí [!INCLUDE[avalon1](../includes/avalon1-md.md)] . Tím se zlepší prostředí návrháře aktivit a zlepší se výkon u rozsáhlých i složitých pracovních postupů.

- Vlastní aktivity jsou teď navržené pomocí [!INCLUDE[avalon2](../includes/avalon2-md.md)] jazyka XAML a programovací model pro vytváření návrháře aktivit byl zjednodušen.

- Byla implementována aktivita vývojového diagramu, takže můžete vizualizovat tok programu pomocí známého stylu modelování vývojového diagramu.

- [!INCLUDE[wfd2](../includes/wfd2-md.md)]Má nového návrháře proměnných, který umožňuje deklarovat a oborovat proměnné v rámci vašich pracovních postupů, svázat je s aktivitami.

- V nástroji [!INCLUDE[vs2010](../includes/vs2010-md.md)] [!INCLUDE[wfd2](../includes/wfd2-md.md)] poskytuje kompletní funkce IntelliSense při vytváření Visual Basic výrazů v rámci vašich [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] pracovních postupů.

- Prostředí ladění teď rozšiřuje na XAML, což vám umožní nastavit zarážky v definici pracovního postupu XAML a krokovat kód XAML za běhu, což nabízí podobné možnosti jako ve spravovaném kódu.

- Opětovné hostování [!INCLUDE[wfd2](../includes/wfd2-md.md)] mimo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je v porovnání s předchozími verzemi významně zjednodušené, nyní vyžaduje pouze pár řádků kódu.

- Nová <xref:System.Activities.Statements.Flowchart> aktivita a její [vývojový diagram](../workflow-designer/flowchart-activity-designer.md) vám umožní vizualizovat tok programu pomocí známého stylu modelování vývojového diagramu.

- Byly vylepšeny aktivity zasílání zpráv, což vám umožňuje psát plně deklarativní (bez kódu) [!INCLUDE[indigo1](../includes/indigo1-md.md)] služeb.

- **Přidat odkaz na službu...** funkce umožňují automaticky generovat aktivity, které přistupují k webovým službám.

## <a name="in-this-section"></a>V tomto oddílu
 [Použití Návrhář postupu provádění](../workflow-designer/using-the-workflow-designer.md) Ukazuje, jak vytvořit nové aktivity a projekty pracovního postupu pomocí předdefinovaných návrhářů a jak používat jiné nástroje, které Návrhář poskytuje ke zpracování argumentů, proměnných, výrazů, importů a navigace s popisem cesty.

 [Používání návrháře aktivit](../workflow-designer/using-the-activity-designers.md) Popisuje kategorie aktivit a šablon a jejich designerů, které jsou k dispozici v systému.

 [Ladění pracovních postupů pomocí Návrhář postupu provádění](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) Popište, jak provádět tradiční ladicí postupy a také ladit XAML a výrazy.

 [Návrhář postupu provádění – pomáhat s uživatelským rozhraním](../workflow-designer/workflow-designer-ui-help.md) Obsahuje témata nápovědy k kontextové nápovědě pro dialogová okna, která nabízí [!INCLUDE[wfd1](../includes/wfd1-md.md)] , a také pokyny k funkcím návrháře prostředí, klávesových zkratek a chybových zpráv.

 [Vývoj aplikací pracovních postupů cílících na rozhraní .net 3,0 nebo .net 3,5 Framework](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md) Obsahuje pokyny k používání starší verze návrháře, který cílí na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 [Přehostování návrháře &#91;UKÁZEK WF&#93;](https://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d) Tento příklad ukazuje, jak vytvořit rozložení WPF, aby obsahovalo návrháře.

 [Vlastní návrháři aktivit](https://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075) Tato část obsahuje ukázky aktivity, které používají vlastní návrháře pro zobrazení v Návrháři pracovních postupů.