---
title: Vytváření vlastních zobrazení dat v ladicím programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59e6c1879d5463682ee41d60e3928fce85c74a8d
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305140"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Vytváření vlastních zobrazení dat v ladicím programu sady Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ladicí program poskytuje celou řadu nástrojů pro prohlížení a úpravy stavu programu. Většina těchto nástrojů funguje pouze v režimu pozastavení.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Vytváření vlastních zobrazení dat v oknech proměnných a datové tipy
 Mnoho [ladicího programu systému windows](../debugger/debugger-windows.md), například **automatické hodnoty** a **Watch** windows, můžete kontrolovat proměnné. Můžete přizpůsobit typy jak nativní, spravované objekty, a vlastních typů jsou zobrazeny v oknech proměnných ladicího programu a [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Další informace najdete v tématu [vytváření vlastních zobrazení nativních objektů](../debugger/create-custom-views-of-native-objects.md) a [vytváření vlastních zobrazení spravovaných objektů](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Vytváření vlastních vizualizérů  
 Vizualizéry umožňují zobrazení obsahu objektu nebo proměnné srozumitelným způsobem. V ladicím programu sady Visual Studio vizualizéru odkazuje na jiný windows, které můžete otevřít pomocí na lupu ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Vizualizéru ikonu") ikonu. HTML vizualizér například ukazuje, jak by interpretován a zobrazen v prohlížeči jako řetězec HTML. K vizualizátorům můžete přistupovat z datových typů, **Watch** okně **automatické hodnoty** okně a **místní hodnoty** okna. **QuickWatch** dialogové okno obsahuje také vizualizéru. Další informace najdete v tématu [vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Viz také:  
 [Základy ladicího programu](../debugger/getting-started-with-the-debugger.md)   
 [Okno příkazového řádku](../ide/reference/command-window.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)