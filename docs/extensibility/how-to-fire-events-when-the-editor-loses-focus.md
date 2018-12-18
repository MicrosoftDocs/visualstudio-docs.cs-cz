---
title: 'Postupy: vyvolání události při editoru ztratí fokus. | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af6abf503bec94cb45638b1e059f545f005cb318
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639653"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Postupy: vyvolání události při editoru ztratí fokus.
Někdy je potřeba vědět, pokud editor ztratí fokus na okno rámce. Například můžete potřebovat po editoru už nemá fokus na něj extrahovat kód, z okna kódu. Následující postup vysvětluje, jak postupovat podle k přijímání oznámení tom editor ztráta fokusu.  
  
## <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Chcete-li vyvolat událost v reakci na editor ztráta fokusu  
  
1.  Monitorování událostí výběru získáním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> objektu z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> a poskytnout mu vaše <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objektu.  
  
3.  Ve volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, vyhledejte `elementid==SEID_WindowFrame`.  
  
4.  Test `varValueNew` parametr pro dvě věci:  
  
    1.  Snímek okna, které hledáte.  
  
    2.  Bod, ve kterém aplikace ztratí výběr do tohoto okna rámce.