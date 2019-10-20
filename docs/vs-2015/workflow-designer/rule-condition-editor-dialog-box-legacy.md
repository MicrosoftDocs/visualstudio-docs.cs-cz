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
ms.openlocfilehash: 93aef1e4466bd88d87ebce71161dcd1665178317
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663355"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Dialogové okno Editor podmínek pravidla (starší verze)
Toto téma popisuje, jak používat dialogové okno **Editor podmínek pravidla** ve starších [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Starší verze [!INCLUDE[wfd2](../includes/wfd2-md.md)] použijte, pokud potřebujete cílit buď na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)], nebo na [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Podmínky deklarativního pravidla můžete vytvořit a upravit pomocí dialogového okna **Editor podmínek pravidla** . Tyto podmínky pravidla jsou zpřístupněny jako vlastnosti v následujících programovací model Windows Workflow Foundation nedostupné aktivity:

- [Aktivitou skupiny ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

- [Aktivita ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

- [Aktivita typu WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

  K dialogovému oknu **Editor podmínek pravidla** přistupujete pomocí [dialogového okna vybrat podmínku (starší verze)](../workflow-designer/select-condition-dialog-box-legacy.md).

  Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **Editor podmínek pravidla** .

|Prvek uživatelského rozhraní (UI)|Popis|
|----------------|-----------------|
|**Pomocné**|Zadejte výraz pro podmínku pravidla.|
|**Ok**|Kliknutím uložíte podmínku pravidla.|

## <a name="entering-condition-expressions"></a>Vstupní výrazy podmínky
 Výrazy podmínky jsou zadány jako text. Tuto možnost můžete zadat **.** do editoru pro odkaz na pole, vlastnosti a metody použité v pracovním postupu pomocí nabídky podobné technologií IntelliSense. Případně můžete zadat název člena pracovního postupu přímo. Do podmínky můžete přidat logické operátory, jako například a, nebo, nikoli. Můžete také přidat predikáty. Predikát je binární operátor a dva operandy. Podporované binární operátory jsou **==** , **>** , **\<** , **>=** a **<=** . Podporované operandy jsou konstantní hodnota, Aritmetická funkce a obor veřejných členů.

 Můžete zadat typ porovnání a můžete porovnat s **hodnotou null** nebo prázdným řetězcem. Můžete provést vnořená volání členů na proměnné, která obsahuje komplexní typ, například `this.Address.State == "WA"`.

 Editor podmínek pravidla podporuje následující operátory:

- Relační operátory: = =, =,! =

- Operátory porovnání: <, \< =, >, > =

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

  Další informace o podmínkách najdete v tématu [použití podmínek v pracovních postupech](http://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Viz také
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033) [aktivitou skupiny ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) [Aktivita ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039) [Aktivita typu WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049) [vybrat podmínku (starší)](../workflow-designer/select-condition-dialog-box-legacy.md) [pomocí podmínek v pracovních postupech](http://go.microsoft.com/fwlink?LinkID=65009) [starší verze návrháře pro Windows Workflow Základní informace o uživatelském rozhraní](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)