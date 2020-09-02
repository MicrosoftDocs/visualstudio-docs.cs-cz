---
title: Ladění pracovních postupů ze vzdáleného počítače (starší verze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bce98714832042471145bcf7d908a62b15bdb144
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656848"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Ladění pracovních postupů ze vzdáleného počítače (starší verze)
Toto téma popisuje, jak ladit vzdálené starší verze [!INCLUDE[wf](../includes/wf-md.md)] aplikací, které jsou sestavené se starší verzí [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Použijte starší verze, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Pokud vaše aplikace musí cílit na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Při instalaci nástroje [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] je jednou z možností instalace součástí instalace [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] ladicího programu pro nástroj [!INCLUDE[wf](../includes/wf-md.md)] . Tím se nainstaluje součásti vzdáleného ladění. Tyto komponenty vzdáleného ladění musí být nainstalovány na počítači, na který cílíte na ladění vzdáleného pracovního postupu.

 Kromě toho musí být sestavení, které obsahuje definici pracovního postupu starší verze pracovního postupu, který ladíte na vzdáleném počítači, nainstalováno v globální mezipaměti sestavení (GAC) místního počítače, ze kterého provádíte ladění. Pokud je například starší verze pracovního postupu spuštěná na vzdáleném počítači a a ladíte ho z místního počítače B, musí být definice pracovního postupu přítomna v globální mezipaměti sestavení (GAC) počítače B. To umožňuje návrháři deserializovat a zobrazit v počítači B označení pracovního postupu pracovního postupu, který běží vzdáleně na počítači A. Další informace o globální mezipaměti sestavení (GAC) najdete v knihovně MSDN.

 [!INCLUDE[wf2](../includes/wf2-md.md)] vzdálené ladění funguje stejně jako vzdálené ladění pro jiné [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] součásti. Další informace najdete v tématu [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] vzdálené ladění v knihovně MSDN.

## <a name="see-also"></a>Viz také
 [Ladění starších verzí pracovních postupů](../workflow-designer/debugging-legacy-workflows.md)