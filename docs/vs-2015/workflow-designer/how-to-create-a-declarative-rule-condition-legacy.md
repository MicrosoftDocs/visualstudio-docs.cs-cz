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
ms.openlocfilehash: d3a15aad987e46edb58da3560828c70571df2227
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663419"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Postupy: vytvoření podmínky deklarativního pravidla (starší verze)
Toto téma popisuje, jak deklarovat podmínku pravidla pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)], která cílí na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Příkaz podmínky se vyhodnotí jako **true** nebo **false**. Podmínka deklarativního pravidla je příkaz podmínky, který se vytvoří pomocí [dialogového okna Editor podmínek pravidla (starší verze)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) a uložený jako XML s pracovním postupem. Může obsahovat predikáty, které porovnávají stav pracovního postupu a logickou algebraický, které kombinuje více predikátů.

 Podmínky deklarativního pravidla se používají v následujících programovací model Windows Workflow Foundationch aktivitách, které se doplňují po box:

- [Aktivitou skupiny ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

- [Aktivita ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

- [Aktivita typu WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

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
 [Starší aktivity pracovního postupu](../workflow-designer/legacy-workflow-activities.md) [pomocí aktivitou skupiny ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066) s použitím aktivity [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075) pomocí aktivity [replikátoru](http://go.microsoft.com/fwlink?LinkID=65080) v dialogovém okně Editor podmínek pro pravidlo [aktivity while](http://go.microsoft.com/fwlink?LinkID=65091) [(starší verze) ](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [Dialogové okno vybrat podmínku (starší verze)](../workflow-designer/select-condition-dialog-box-legacy.md) [s použitím podmínek v pracovních postupech](http://go.microsoft.com/fwlink?LinkID=65009)