---
title: Návrhář aktivity Návrhář postupu provádění – použitím objektu FlowDecision
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e405f82bcf33bc01ad07f1092879c17dec5849
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111433"
---
# <a name="flowdecision-activity-designer"></a>Návrhář aktivity FlowDecision

Uzel <xref:System.Activities.Statements.FlowDecision> je podmíněný uzel, který poskytuje větev pro tok řízení do jedné ze dvou alternativ na základě toho, zda je splněna zadaná podmínka. Pokud tok vyžaduje více než dvě větve, použijte místo toho <xref:System.Activities.Statements.FlowSwitch%601>.

## <a name="the-flowdecision-node"></a>Uzel použitím objektu FlowDecision

Použijte <xref:System.Activities.Statements.FlowDecision>, když se tok může rozvětvit do dvou cest. Uzel <xref:System.Activities.Statements.FlowDecision> má <xref:System.Activities.Statements.FlowDecision.Condition%2A> a <xref:System.Activities.Statements.FlowNode> přidružený ke každému ze dvou možných výsledků: <xref:System.Activities.Statements.FlowDecision.True%2A> nebo <xref:System.Activities.Statements.FlowDecision.False%2A>. <xref:System.Activities.Statements.FlowDecision.Condition%2A> se vyhodnotí a hodnota tohoto vyhodnocení Určuje další <xref:System.Activities.Statements.FlowNode>, který se má zpracovat v rámci <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Použití návrháře použitím objektu FlowDecision

Návrháře **použitím objektu FlowDecision** lze najít v kategorii **vývojové diagramy** v **sadě nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL**+**ALT**+**X**.

Návrhář **použitím objektu FlowDecision** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu v Návrháři aktivity **vývojového diagramu** . Tím se vytvoří <xref:System.Activities.Statements.FlowDecision> s označením **rozhodnutí** v rámci aktivity <xref:System.Activities.Statements.Flowchart>. Myš nad návrhářem a čtvercové táhlo **true** a **false** pro dvě větve se zobrazí.

Po přetažení návrháře **použitím objektu FlowDecision** a dalších návrhářů do **vývojového diagramu**lze uzly propojit dohromady, aby bylo možné určit pořadí spouštění. Chcete-li vytvořit propojení mezi zdrojovým uzlem (včetně hodnot **true** a **false** v **použitím objektu FlowDecision**) a cílového uzlu, myši v Návrháři zdrojového uzlu a čtvercového táhla se zobrazí na každé straně. Klikněte na jeden z čtvercových popisovačů a přetáhněte ho tak, že podržíte tlačítko myši na jeden z úchytů, který se zobrazí podobným způsobem kolem cílového uzlu při pohybu myší. Uvolněte tlačítko myši a propojení mezi vytvořením těchto dvou uzlů, které jsou reprezentovány jako šipka od zdrojového návrháře do cílového návrháře.

Výraz, který uvádí <xref:System.Activities.Statements.FlowDecision.Condition%2A> lze zadat v poli **Podmínka** v okně **vlastnosti** kliknutím na místo, kde text nápovědy říká "zadejte výraz VB".

### <a name="the-flowdecision-properties"></a>Vlastnosti použitím objektu FlowDecision

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.FlowDecision> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Pravda|Podmínka, která určuje, která cesta má řízení toku trvat.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|Nepravda|Cesta provedená řízením toku, pokud je splněna <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|Nepravda|Cesta provedená ovládacím prvkem flow, pokud <xref:System.Activities.Statements.FlowDecision.Condition%2A> není splněna.|

## <a name="see-also"></a>Viz také:

- [Vývojový diagram](../workflow-designer/flowchart-activity-designers.md)
- [Vývojový diagram](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
