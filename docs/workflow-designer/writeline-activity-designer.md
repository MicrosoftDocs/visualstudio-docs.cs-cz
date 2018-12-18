---
title: Návrhář postupu provádění – Návrhář aktivity WriteLine
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a512288d141823115361bf8eacfd179a74a1da1b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876708"
---
# <a name="writeline-activity-designer"></a>Návrhář aktivity WriteLine

**WriteLine** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.Activities.Statements.WriteLine> aktivity.

## <a name="the-writeline-activity"></a>Aktivity WriteLine

<xref:System.Activities.Statements.WriteLine> Aktivita zapíše text do zadaného <xref:System.IO.TextWriter> objektu. Pokud ne <xref:System.IO.TextWriter> není zadána, <xref:System.Activities.Statements.WriteLine> zapíše text do konzoly.

### <a name="using-the-writeline-activity-designer"></a>Návrhář aktivity WriteLine pomocí

Přístup **WriteLine** návrháře aktivit v **primitiv** kategorii **nástrojů**. **WriteLine** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na povrch návrháře postupu provádění bez ohledu na to aktivity jsou obvykle umístěny, například jako uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří <xref:System.Activities.Statements.WriteLine> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> WriteLine. <xref:System.Activities.Activity.DisplayName%2A> Můžete upravovat v záhlaví **WriteLine** Návrhář aktivity nebo v **DisplayName** pole mřížku vlastností.

### <a name="the-writeline-properties"></a>Vlastnosti WriteLine

Následující tabulka ukazuje <xref:System.Activities.Statements.WriteLine> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností a některé z nich můžete upravit na plochu návrháře postupu provádění.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název <xref:System.Activities.Statements.WriteLine> aktivity. Výchozí hodnota je WriteLine. I když <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je osvědčeným postupem použít jeden.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Text pro zápis. Chcete-li nastavena vlastnost, zadejte výraz jazyka Visual Basic v **Text** pole na **WriteLine** aktivity návrháře nebo v mřížce vlastností.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> Ke kterému <xref:System.Activities.Statements.WriteLine> zapíše <xref:System.Activities.Statements.WriteLine.Text%2A>. Výchozí hodnota je konzola.|

## <a name="see-also"></a>Viz také:

- [Primitiva](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)