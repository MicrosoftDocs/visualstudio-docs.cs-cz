---
title: Možnosti krokování (starší verze) při ladění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b7dfaa4fb659418c26d5aa0144fac4188ef4b16b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899380"
---
# <a name="debug-stepping-options-legacy"></a>Možnosti krokování při ladění (starší verze)
Toto téma popisuje, jak ladit [!INCLUDE[wf](../includes/wf-md.md)] aplikace, které mají souběžných aktivit v starší [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Použijte starší [!INCLUDE[wfd2](../includes/wfd2-md.md)] potřeba cílit na platformu [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Když ladíte starší aktivity, které mají souběžné spouštění, jako například **aktivitě typu ParallelActivity** nebo **aktivitou skupiny ConditionedActivityGroup**, můžete použít jednu z následujících dvou možností pro jednotlivé kroky v kódu .  
  
- **Nepodmíněný skok krokování.** Tento režim krokování umožňuje procházet a ladit konkrétní větve složené aktivity, jako **aktivitě typu ParallelActivity** nebo **ConditionalActivityGroup** aktivity. Když použijete tuto možnost, chcete-li ladit, nebude Všimněte si, že dojde ke změně v ovládacím prvku z důvodu souběžných spuštění další aktivity v pracovním postupu. Pouze ladicí program prostřednictvím činností v aktuálně vybrané větve, zatímco ostatní aktivity v pracovním postupu mohou být prováděny současně. Například ve výchozím nastavení, úplně vlevo větve ve **aktivitě typu ParallelActivity** aktivity a první podřízená aktivita **aktivitou skupiny ConditionedActivityGroup** aktivity se používají pro procházení. Uživatel je v případě zájmu ladění jinou větev nebo podřízenou aktivitu, explicitní zarážky musí být umístěn na větev nebo podřízené aktivity. Krokování dál v této větvi, když se aktivuje zarážku.  
  
- **Instance, krokování.** Tento režim krokování umožňuje procházet a ladění souběžně prováděných aktivit v pracovním postupu. S touto možností můžete si všimnout, že dojde ke změně v ovládacím prvku při souběžné provádění aktivit spouštěná v rámci pracovního postupu.  
  
  Standardně je vybraná možnost krokování větve a mohou uživatelé přepínat mezi těmito dvěma možnostmi při ladění starších verzí pracovních postupů.  
  
  Měli byste vybrat instanci krokování možnost při ladění pracovních postupů starších verzí stav počítače.  
  
## <a name="see-also"></a>Viz také  
 [Ladění starších verzí pracovních postupů](../workflow-designer/debugging-legacy-workflows.md)   
 [Postupy: Změna možností krokování při ladění (starší verze)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)