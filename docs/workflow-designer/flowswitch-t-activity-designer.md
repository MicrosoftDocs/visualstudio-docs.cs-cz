---
title: Návrhář aktivity<T> Návrhář postupu provádění FlowSwitch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8271100936b9cf70e17c0e6279297d583714f018
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597149"
---
# <a name="flowswitcht-activity-designer"></a>Návrhář aktivit > FlowSwitch\<T

Aktivita <xref:System.Activities.Statements.FlowSwitch%601> je podmíněný uzel, který poskytuje větvení pro tok řízení na základě kritéria shody, pokud jsou vyžadovány více než dvě alternativní větve. Pokud větve toku vyžaduje pouze dvě cesty, použijte místo toho <xref:System.Activities.Statements.FlowDecision> aktivitu.

## <a name="the-flowswitcht-activity"></a>Aktivita > FlowSwitch\<T

Aktivita <xref:System.Activities.Statements.FlowSwitch%601> obsahuje <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, která vrací hodnotu typu *t* (zadanou obecným parametrem) při vyhodnocování. Aktivita také obsahuje sadu <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, která určuje jedinečné mapování z možných výsledků tohoto vyhodnocení na sadu <xref:System.Activities.Statements.FlowNode> objektů. Spouštěný <xref:System.Activities.Statements.FlowNode> je ten, jehož objekt typu *t* odpovídá hodnotě vyhodnoceného <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. V případě, že se nezíská shoda, může být <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> případ (volitelně).

### <a name="using-the-flowswitcht-activity-designer"></a>Použití návrháře aktivit > FlowSwitch\<T

Návrhář aktivity **FlowSwitch\<t >** můžete najít v kategorii **vývojové diagramy** v **sadě nástrojů**, ke které se dostanete kliknutím na kartu **panelu nástrojů** na levé straně Návrhář postupu provádění. Případně vyberte v nabídce **zobrazení** možnost **Sada nástrojů** nebo stiskněte klávesovou **zkratku CTRL**+**ALT**+**X**.

Návrhář aktivity **FlowSwitch\<t >** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění povrch v Návrháři aktivity **vývojového diagramu** . Použijte okno **vybrat typy** , které se zobrazí, chcete-li určit typ (přidružený v kódu s <xref:System.Activities.Statements.FlowSwitch%601> podle jeho obecného parametru) získaného při vyhodnocování <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Tento postup vytvoří <xref:System.Activities.Statements.FlowSwitch%601> aktivitu označenou **přepínačem** v rámci aktivity <xref:System.Activities.Statements.Flowchart>. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> lze zadat do pole **výrazu** v okně **vlastnosti** kliknutím na místo, kde text nápovědy říká "zadejte výraz VB".

Myš nad **FlowSwitch\<t >** návrháři aktivity způsobí, že čtvercové úchyty, které se používají k propojení <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, se zobrazí kolem jeho okrajů. Po přetažení návrháře aktivity **FlowSwitch < T\>** a dalších návrhářů aktivit do **vývojového diagramu**se objekty <xref:System.Activities.Activity>, které představují, připravené propojit dohromady, aby určovaly pořadí spouštění. Chcete-li vytvořit jednu z <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> přidružených k <xref:System.Activities.Statements.FlowSwitch%601>, klikněte na jeden z čtvercového táhla na okraji **FlowSwitch < t\>** a přetáhněte ho (tak, že podržíte tlačítko myši) k jednomu z popisovačů, které se zobrazí podobným způsobem kolem cílové aktivity, když ukazatel myši setrvá na návrháři. Po uvolnění tlačítka myši a šipky z **FlowSwitch < T\>** do cílového návrháře se zobrazí zpráva, která představuje tento případ. Výchozí hodnota pro tento případ se zobrazí na šipce a může být upravena v poli **případ** v okně **vlastnosti** .

### <a name="the-flowswitcht-properties"></a>Vlastnosti FlowSwitch\<T >

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.FlowSwitch%601> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Pravda|Určuje výraz, který se vyhodnocuje, aby se určilo, na který <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> se má přepnout v cestě k provedení.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Nepravda|Určuje jedinečné mapování z možných výsledků získaných z vyhodnocování <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> do sady objektů <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Pravda|Určuje mapování, pokud vyhodnocení <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> neodpovídá jedné z hodnot obsažených v objektu <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Viz také:

- [Vývojový diagram](../workflow-designer/flowchart-activity-designers.md)
- [Vývojový diagram](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
