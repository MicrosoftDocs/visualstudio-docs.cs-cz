---
title: 'Postupy: vytvoření podmínky deklarativního pravidla (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c23fed64d7f3a7681fce96663262f6d633299a9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849339"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Postupy: vytvoření podmínky deklarativního pravidla (starší verze)
Toto téma popisuje, jak deklarovat podmínku pravidla pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)], která cílí na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Příkaz podmínky se vyhodnotí jako **true** nebo **false**. Podmínka deklarativního pravidla je příkaz podmínky, který se vytvoří pomocí [dialogového okna Editor podmínek pravidla (starší verze)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) a uložený jako XML s pracovním postupem. Může obsahovat predikáty, které porovnávají stav pracovního postupu a logickou algebraický, které kombinuje více predikátů.

 Podmínky deklarativního pravidla se používají v následujících programovací model Windows Workflow Foundationch aktivitách, které se doplňují po box:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [Aktivita ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [Aktivita typu WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Vytvoření podmínky deklarativního pravidla pomocí editoru podmínek pravidla

1. V okně **vlastnosti** aktivity klikněte v závislosti na aktivitě na vlastnost **Condition** nebo vlastnost **UntilCondition** .

2. V seznamu Vlastnosti vyberte **Podmínka deklarativního pravidla** .

3. Rozbalte vlastnost **Condition** nebo **UntilCondition** .

4. Klikněte na vlastnost **Condition** .

5. Kliknutím na **Podmínka** tři tečky **[...]** otevřete dialogové okno **vybrat podmínku** .

6. Kliknutím na **Nová podmínka** otevřete dialogové okno **Editor podmínek pravidla** .

7. Do textového pole **Podmínka** zadejte výraz pro podmínku.

     Informace o tom, jak vytvořit výrazy podmínky, najdete v tématu [dialogové okno Editor podmínek pravidla (starší verze)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Po dokončení vytváření výrazu podmínky kliknutím na tlačítko **OK** zavřete dialogové okno a vytvořte podmínku pravidla s přiřazeným názvem.

     Otevře se dialogové okno **vybrat podmínku** .

     Informace o tom, jak používat dialogové okno **vybrat podmínku** , najdete v části [dialogové okno vybrat podmínku (starší verze)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Viz také
 [Starší aktivity pracovního postupu](../workflow-designer/legacy-workflow-activities.md) [pomocí aktivitou skupiny ConditionedActivityGroup](https://msdn2.microsoft.com/library/bb675237.aspx) s využitím [aktivity IfElseBranchActivity](https://msdn2.microsoft.com/library/bb628465.aspx) pomocí aktivity [replikátoru](https://msdn2.microsoft.com/library/bb628544.aspx) , která se používá v dialogovém okně Editor podmínek pro pravidlo [aktivity while](https://msdn2.microsoft.com/library/bb628552.aspx) [(starší verze)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [Vyberte možnost podmínka](../workflow-designer/select-condition-dialog-box-legacy.md) [v pracovních postupech pomocí podmínek](https://msdn2.microsoft.com/library/bb628447.aspx)
