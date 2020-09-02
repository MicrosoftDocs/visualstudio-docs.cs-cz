---
title: Možnosti krokování ladění (starší verze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 443cbac0ea9d74c61f24d6714162ec08e2906a62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656879"
---
# <a name="debug-stepping-options-legacy"></a>Možnosti krokování při ladění (starší verze)
Toto téma popisuje, jak ladit [!INCLUDE[wf](../includes/wf-md.md)] aplikace, které mají souběžné aktivity ve starších verzích [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Použijte starší verze, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Pokud potřebujete cílit buď na, [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Když ladíte starší aktivity, které mají souběžné spouštění, jako je například **Aktivita typu ParallelActivity** nebo **aktivitou skupiny ConditionedActivityGroup**, můžete použít jednu z následujících dvou možností pro krokování kódu.

- **Krokování větví.** Tento režim krokování umožňuje procházet a ladit konkrétní větev složené aktivity, jako je například **Aktivita typu ParallelActivity** nebo aktivita **ConditionalActivityGroup** . Když použijete tuto možnost k ladění, nebudete si všimnout, že změna v ovládacím prvku nastane v důsledku souběžného spouštění jiných aktivit v pracovním postupu. Ladicí program provádí pouze aktivity v aktuálně vybrané větvi, zatímco jiné aktivity v pracovním postupu mohou být spuštěny souběžně. Například ve výchozím nastavení se k krokování používá pouze jedna větev v aktivitě **Aktivita typu ParallelActivity** a první podřízená aktivita aktivity **aktivitou skupiny ConditionedActivityGroup** . Pokud uživatel zajímá ladění jakékoli jiné větve nebo podřízené aktivity, musí být explicitní zarážka umístěna na tuto větev nebo podřízenou aktivitu. Krokování pokračuje v této větvi při aktivaci zarážky.

- **Krokování instance.** Tento režim krokování umožňuje procházet a ladit souběžně vykonávané aktivity v pracovním postupu. Pomocí této možnosti si všimnete, že změna v ovládacím prvku nastane, když se v pracovním postupu souběžně spouštějí aktivity.

  Ve výchozím nastavení je zvolena možnost krokování a uživatelé mohou přepínat mezi těmito dvěma možnostmi při ladění starší verze pracovního postupu.

  Při ladění stavových pracovních postupů pro Stavový počítač starší verze byste měli vybrat možnost krokování instance.

## <a name="see-also"></a>Viz také
 [Ladění starších verzí pracovních postupů](../workflow-designer/debugging-legacy-workflows.md) [: Změna možnosti krokování ladění (starší verze)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)