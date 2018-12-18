---
title: Návrhář postupu provádění – Návrhář aktivity Flowchart
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3468e4e09f8e31ae6b3e8bf7a49b7a1c368b3e73
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877683"
---
# <a name="flowchart-activity-designer"></a>Návrhář aktivity Flowchart

<xref:System.Activities.Statements.Flowchart> Aktivita se používá k vytváření pracovních postupů, které definovat a spravovat komplexní tok řízení. A <xref:System.Activities.Statements.Flowchart> dají se vytvářet v kódu nebo s použitím návrháře postupu provádění. Toto téma popisuje prostředí návrháře postupu provádění. Návrhář aktivity pracovního postupu návrháře postupu provádění umožňuje vývojářům pro vytváření pracovních postupů přirozeným způsobem.

## <a name="the-flowchart-activity"></a>Vývojový diagram aktivity

<xref:System.Activities.Statements.Flowchart> Určuje jedinečný <xref:System.Activities.Statements.Flowchart.StartNode%2A> , která se spustí při spuštění pracovního postupu a používá propojená síť <xref:System.Activities.Statements.Flowchart.Nodes%2A> k vytvoření libovolného smyčky nebo k rozdělení toku provádění jinde v pracovním postupu v daném okamžiku.

### <a name="using-the-flowchart-activity-designer"></a>Návrhář aktivity Flowchart pomocí

**Vývojový diagram** návrháře aktivit najdete v **vývojový diagram** kategorii **nástrojů**, který přistupuje po kliknutí **nástrojů**kartě v Návrháři pracovních postupů. Můžete také vybrat **nástrojů** z **zobrazení** nabídky nebo stisknutím klávesy **Ctrl**+**Alt** + **X**.

**Vývojový diagram** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění bez ohledu na to návrháři aktivit jsou obvykle umístěny, buď jako kořenové aktivity nebo podřízená jiné aktivity toku řízení. Pokud **vývojový diagram** návrháře aktivit je přetaženy prázdné povrch návrháře postupu provádění, vytvoří <xref:System.Activities.Statements.Flowchart> aktivitu, která ve výchozím nastavení prezentuje v rozšířené zobrazení, ve kterém je počáteční uzel, který zahájí provádění reprezentovaná jako zelená koule. Pokud **vývojový diagram** návrháře aktivit je přetáhnout do jiné aktivity toku řízení, představuje sám v minimalizovaném okně zobrazení, které se dají rozšiřovat dvojitým kliknutím **vývojový diagram** návrháře aktivit. Žádné aktivity v aplikaci **nástrojů** můžete přetahovat přímo do **vývojový diagram** návrháře aktivit, včetně další aktivity toku řízení.

Po přetažení různých návrháři aktivit do plátna návrháře postupu provádění <xref:System.Activities.Activity> lze propojit objekty, které představují společně k určení pořadí provádění. Při vytváření propojení mezi aktivitou zdrojové a cílové aktivity se zobrazí po pozastavení ukazatele myši návrháře zdrojová aktivita a Čtvereček obslužné rutiny na obou stranách. Klikněte na některou Čtvereček obslužné rutiny a přetažení podržením tlačítka myši na jednu z obslužné rutiny, které se zobrazí kolem cílová aktivita podobným způsobem, když myší najedete myší. Uvolněte tlačítko myši a vytvoření propojení mezi těmito dvěma aktivitami, které je vyjádřena jako šipku z Návrháře zdroje do cílového návrháře.

### <a name="flowchart-activity-properties"></a>Vlastnosti aktivit vývojového diagramu

Následující tabulka ukazuje <xref:System.Activities.Statements.Flowchart> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje zobrazovaný název návrháře aktivit v záhlaví. Výchozí hodnota je Vývojový diagram. Hodnotu lze upravit v **vlastnosti** okno nebo přímo v hlavičce návrháře aktivit.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je osvědčeným postupem je použití jednoho.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Kolekce proměnných, které jsou v tomto oboru <xref:System.Activities.Statements.Flowchart> sdílení stavu mezi jeho podřízených aktivit.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|<xref:System.Activities.Statements.FlowNode> , Který je spuštěna při <xref:System.Activities.Statements.Flowchart> spustí.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Obsahuje kolekci <xref:System.Activities.Statements.FlowNode> objekty v <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Viz také:

- [Vývojový diagram](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)