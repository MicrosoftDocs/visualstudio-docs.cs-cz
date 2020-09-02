---
title: Zakázání ladicího programu pro programovací model Windows Workflow Foundation (starší verze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eddd72d648e7349f51096a21131f38c2e370a277
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656788"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Zakázání ladicího programu sady Visual Studio pro programovací model Windows Workflow Foundation (starší verze)
Toto téma popisuje, jak zakázat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ladicí program pomocí konfiguračního souboru při sestavování [!INCLUDE[wf](../includes/wf-md.md)] aplikací ve starší verzi [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Použijte starší verze, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Pokud potřebujete cílit buď na, [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Ve výchozím nastavení [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] je ladicí program pro [!INCLUDE[wf](../includes/wf-md.md)] povolen pro hostitelský proces. Chcete-li zakázat ladění pracovního postupu, je nutné je explicitně vypnout přidáním prvku "DisableWorkflowDebugging" **\<switches>** v **\<system.diagnostics>** části konfiguračního souboru hostitele.

 Následující příklad ukazuje, jak upravit konfigurační soubor hostitele pro zákaz ladění pracovního postupu.

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>Viz také
 [Vyvolání ladicího programu sady Visual Studio pro programovací model Windows Workflow Foundation (starší verze)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [ladění starších verzí pracovních postupů](../workflow-designer/debugging-legacy-workflows.md)