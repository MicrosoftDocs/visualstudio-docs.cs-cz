---
title: 'Postupy: Změna možnosti krokování ladění (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5126b3dc45d33471080ae154e06f4a327e21fef7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663441"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Postupy: Změna možností krokování při ladění (starší verze)
Toto téma popisuje, jak změnit možnost krokování ladění pro [!INCLUDE[wf](../includes/wf-md.md)] aplikace ve starší verzi [!INCLUDE[wfd1](../includes/wfd1-md.md)] , které mají souběžné akce. Použijte starší verze, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Pokud potřebujete cílit buď na, [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Když ladíte starší aktivity, které mají souběžné provádění, jako je například **Aktivita typu ParallelActivity** nebo **aktivitou skupiny ConditionedActivityGroup**, můžete použít jednu ze dvou možností pro krokování kódu.

 Pomocí těchto kroků můžete změnit možnost krokování ladění v projektu starší verze pracovního postupu.

## <a name="procedures"></a>Procedury

#### <a name="to-change-the-debug-stepping-option"></a>Změna možnosti krokování ladění

1. Spusťte Visual Studio.

2. Otevřete existující starší projekt pracovního postupu nebo vytvořte nový projekt, který bude využívat souběžné aktivity a který cílí buď na, [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

3. V nabídce **pracovního postupu** ve starší verzi [!INCLUDE[wfd2](../includes/wfd2-md.md)] přejděte na **ladění**a pak přejděte na **Možnosti krokování**.

4. Vyberte možnost **instance** nebo **větev**.

## <a name="see-also"></a>Viz také
 Ladění možností krokování pro ladění [starších verzí pracovních postupů](../workflow-designer/debugging-legacy-workflows.md) [(starší verze)](../workflow-designer/debug-stepping-options-legacy.md)