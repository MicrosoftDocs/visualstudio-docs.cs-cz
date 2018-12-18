---
title: 'Postupy: vyvolání události při editoru ztratí fokus. | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2875ff13302b1f54d87f1f69a68757b10fb98dca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749226"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Postupy: vyvolání události při editoru ztratí fokus.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Někdy je potřeba vědět, pokud editor ztratí fokus na okno rámce. Například můžete potřebovat po editoru už nemá fokus na něj extrahovat kód, z okna kódu. Následující postup vysvětluje, jak postupovat podle k přijímání oznámení tom editor ztráta fokusu.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Chcete-li vyvolat událost v reakci na editor ztráta fokusu  
  
1.  Monitorování událostí výběru získáním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> objektu z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> a poskytnout mu vaše <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objektu.  
  
3.  Ve volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, vyhledejte `elementid==SEID_WindowFrame`.  
  
4.  Test `varValueNew` parametr pro dvě věci:  
  
    1.  Snímek okna, které hledáte.  
  
    2.  Bod, ve kterém aplikace ztratí výběr do tohoto okna rámce.

