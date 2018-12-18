---
title: Návrhář postupu provádění – Návrhář aktivity FlowDecision
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a87c5c9ebe1b3eed2c3c569e508c5b76ce6845d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818988"
---
# <a name="flowdecision-activity-designer"></a>Návrhář aktivity FlowDecision

<xref:System.Activities.Statements.FlowDecision> Uzel je podmíněné uzel, který poskytuje větev pro tok řízení do jedné ze dvou alternativních závislosti na tom, zda je zadaná podmínka splněna. Pokud tok vyžaduje více než dvě větve, použijte <xref:System.Activities.Statements.FlowSwitch%601> místo.

## <a name="the-flowdecision-node"></a>Uzel FlowDecision

Použití <xref:System.Activities.Statements.FlowDecision> když tok je možné větvit do dvou možných cest. A <xref:System.Activities.Statements.FlowDecision> má uzel <xref:System.Activities.Statements.FlowDecision.Condition%2A> a <xref:System.Activities.Statements.FlowNode> spojené s jednotlivými dva možné výsledky: <xref:System.Activities.Statements.FlowDecision.True%2A> nebo <xref:System.Activities.Statements.FlowDecision.False%2A>. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Je vyhodnocen a další určuje hodnota atributu toto vyhodnocení <xref:System.Activities.Statements.FlowNode> ke zpracování v rámci <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Pomocí návrháře FlowDecision

**FlowDecision** návrháře najdete v **vývojový diagram** kategorii **nástrojů**, který přistupuje po kliknutí **nástrojů** Karta v Návrháři pracovních postupů. Můžete také vybrat **nástrojů** z **zobrazení** nabídky nebo stisknutím klávesy **Ctrl**+**Alt** + **X**.

**FlowDecision** návrháře můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění v rámci **vývojový diagram** návrháře aktivit. Tím se vytvoří <xref:System.Activities.Statements.FlowDecision> označené **rozhodnutí** v rámci <xref:System.Activities.Statements.Flowchart> aktivity. Po pozastavení ukazatele myši návrháře a **True** a **False** se čtvereček úchyty pro dvě větve.

Po přetažení **FlowDecision** návrháře a jiné návrháře na **vývojový diagram**, lze propojit uzly společně k určení pořadí provádění. Chcete-li vytvořit propojení mezi zdrojový uzel (včetně **True** a **False** větve z **FlowDecision**) a cílový uzel, pozastavení ukazatele myši návrháře zdrojový uzel a Čtvereček úchyty na obou stranách. Klikněte na některou Čtvereček obslužné rutiny a přetažení podržením tlačítka myši na jednu z obslužné rutiny, které se zobrazí kolem cílový uzel podobným způsobem, když myš nad ním. Uvolněte tlačítko myši a odkaz se mezi těmito dvěma uzly, které je vyjádřena jako šipku z Návrháře zdroje do cílového návrháře.

Výraz, který uvádí <xref:System.Activities.Statements.FlowDecision.Condition%2A> lze napsat **podmínku** pomocí boxingu **vlastnosti** okno kliknutím, kde text nápovědy říká "Zadejte výrazu jazyka VB".

### <a name="the-flowdecision-properties"></a>Vlastnosti FlowDecision

Následující tabulka ukazuje <xref:System.Activities.Statements.FlowDecision> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Hodnota TRUE|Podmínka, která určuje, kterou cestu má řízení toku.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Cesta provedenou řízení toku, pokud <xref:System.Activities.Statements.FlowDecision.Condition%2A> je spokojeni.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Cesta provedenou řízení toku, pokud <xref:System.Activities.Statements.FlowDecision.Condition%2A> není splněná.|

## <a name="see-also"></a>Viz také:

- [Vývojový diagram](../workflow-designer/flowchart-activity-designers.md)
- [Vývojový diagram](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)