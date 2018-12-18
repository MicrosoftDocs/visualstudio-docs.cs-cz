---
title: 'Postupy: vytvoření podmínky deklarativního pravidla (starší verze) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 2508404840db81f03ba4865a3e5d5af91e5c653b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187405"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Postupy: vytvoření podmínky deklarativního pravidla (starší verze)
Toto téma popisuje, jak deklarovat podmínku pravidla, která pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)] , který cílí [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Příkaz podmínky vyhodnocen **True** nebo **False**. Podmínka deklarativního pravidla je podmínka příkazu, který je vytvořen pomocí [dialogové okno pravidla podmínky editoru (starší verze)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) a ukládají ve formátu XML s pracovním postupem. Může obsahovat predikáty, které porovnávají stavu pracovního postupu a algebraický logická hodnota, který kombinuje několik predikátů.  
  
 Podmínky deklarativního pravidla se používají v následujících aktivit Windows Workflow Foundation out-of-box:  
  
-   [Skupina ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [Aktivitou typu ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [Aktivita typu WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>K vytvoření podmínky deklarativního pravidla pomocí Editor podmínek pravidla  
  
1.  V rámci aktivity **vlastnosti** okna, klikněte na tlačítko **podmínku** vlastnost nebo **UntilCondition** vlastnost, v závislosti na aktivitě.  
  
2.  Vyberte **Podmínka deklarativního pravidla** ze seznamu pro vlastnost.  
  
3.  Rozbalte **podmínku** nebo **UntilCondition** vlastnost.  
  
4.  Klikněte na tlačítko **ConditionName** vlastnost.  
  
5.  Klikněte na tlačítko **ConditionName** symbol tří teček **[...]**  otevřít **vyberte podmínku** dialogové okno.  
  
6.  Klikněte na tlačítko **novou podmínku** otevřít **Editor podmínek pravidla** dialogové okno.  
  
7.  Zadejte výraz podmínky v **podmínku** textového pole.  
  
     Informace o tom, jak vytvořit podmínku výrazů naleznete v tématu [dialogové okno pravidla podmínky editoru (starší verze)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Po dokončení vytváření výraz podmínky, klikněte na tlačítko **OK** a zavřete dialogové okno Vytvořit podmínka pro pravidlo s názvem přiřazené.  
  
     **Vyberte podmínku** zobrazí se dialogové okno.  
  
     Informace o tom, jak používat **vyberte podmínku** dialogovém okně naleznete v tématu [vyberte podmínku dialogové okno (starší verze)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## <a name="see-also"></a>Viz také  
 [Aktivity starších verzí pracovních postupů](../workflow-designer/legacy-workflow-activities.md)   
 [Pomocí aktivitou skupiny ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Použití aktivity IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Použití aktivity replikátoru](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Pomocí While aktivity](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Editor podmínek pravidla dialogové okno (starší verze)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Dialogové okno Vybrat podmínku (starší verze)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Pomocí podmínek v pracovních postupech](http://go.microsoft.com/fwlink?LinkID=65009)