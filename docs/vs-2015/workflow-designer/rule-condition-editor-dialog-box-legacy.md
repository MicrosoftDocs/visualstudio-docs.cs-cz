---
title: Dialogové okno Editor podmínek pravidla (starší verze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00df917b05f5073634b0956a0b44e5b0fc6026a6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846334"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Dialogové okno Editor podmínek pravidla (starší verze)
Toto téma popisuje, jak používat dialogové okno **Editor podmínek pravidla** ve starších [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Použijte starší [!INCLUDE[wfd2](../includes/wfd2-md.md)] potřeba cílit na platformu [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Podmínky deklarativního pravidla můžete vytvořit a upravit pomocí dialogového okna **Editor podmínek pravidla** . Tyto podmínky pravidla jsou zpřístupněny jako vlastnosti v následujících programovací model Windows Workflow Foundation nedostupné aktivity:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [Aktivita ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [Aktivita typu WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

  K dialogovému oknu **Editor podmínek pravidla** přistupujete pomocí [dialogového okna vybrat podmínku (starší verze)](../workflow-designer/select-condition-dialog-box-legacy.md).

  Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **Editor podmínek pravidla** .

|Prvek uživatelského rozhraní (UI)|Popis|
|----------------|-----------------|
|**Pomocné**|Zadejte výraz pro podmínku pravidla.|
|**OK**|Kliknutím uložíte podmínku pravidla.|

## <a name="entering-condition-expressions"></a>Vstupní výrazy podmínky
 Výrazy podmínky jsou zadány jako text. Tuto možnost můžete zadat **.** do editoru pro odkaz na pole, vlastnosti a metody použité v pracovním postupu pomocí nabídky podobné technologií IntelliSense. Případně můžete zadat název člena pracovního postupu přímo. Do podmínky můžete přidat logické operátory, jako například a, nebo, nikoli. Můžete také přidat predikáty. Predikát je binární operátor a dva operandy. Podporované binární operátory jsou **==** , **>** , **\<** , **>=** a **<=** . Podporované operandy jsou konstantní hodnota, Aritmetická funkce a obor veřejných členů.

 Můžete zadat typ porovnání a můžete porovnat s **hodnotou null** nebo prázdným řetězcem. Můžete provést vnořená volání členů na proměnné, která obsahuje komplexní typ, například `this.Address.State == "WA"`.

 Editor podmínek pravidla podporuje následující operátory:

- Relační operátory: = =, =,! =

- Operátory porovnání: <, \<=, >, > =

- Aritmetické operátory: +,-, *,/, MOD

- Logické operátory: a, & &, nebo, &#124; &#124;, not,!

- Bitové operátory: &,&#124;

  Priorita operátora výrazu C# sleduje pravidla priority operátora.

  Editor podmínek pravidla podporuje následující číselné výrazy:

  this. i = 1D (překládá na 1,0)

  this. i = = 1E1 (překládá na 10,0)

  this. i = = 1L (překládá se jako Long)

  this. i = 1M (překládá se jako desítkový)

  this. i = = 1F (překládá se jako jedna)

  this. i = = 1U (překládá se jako nepodepsaný int)

  Další informace o podmínkách najdete v tématu [použití podmínek v pracovních postupech](https://msdn2.microsoft.com/library/bb628447.aspx).

## <a name="see-also"></a>Viz také
 [IfElseActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelseactivity.aspx) [aktivitou skupiny ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx) [Aktivita ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx) [Aktivita typu WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx) [Select Condition (starší verze)](../workflow-designer/select-condition-dialog-box-legacy.md) [použijte podmínky v tématu pracovní postupy](https://msdn2.microsoft.com/library/bb628447.aspx) [starší verze návrháře pro programovací model Windows Workflow Foundation nápovědu k uživatelskému rozhraní](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md) .
