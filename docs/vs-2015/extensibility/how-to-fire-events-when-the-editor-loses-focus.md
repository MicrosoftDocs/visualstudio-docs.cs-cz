---
title: 'Postupy: události požáru, když Editor ztratí fokus | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ebca733798636ca32787b88b8874c31a2ffffdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204197"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Postupy: Aktivace událostí, když editor ztratí fokus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Někdy je nutné znát, když Editor ztratí fokus na snímku okna. Například může být nutné extrahovat kód z okna kódu poté, co Editor již není zaměřen na něj. Následující postup popisuje, jak postupovat při obdržení oznámení o zamítnutí výběru.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Vyvolání události v reakci na Editor, který ztratí fokus  
  
1. Monitorování událostí výběru získáním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> objektu z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .  
  
2. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> a poskytněte svému <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objektu.  
  
3. Ve vašem volání na <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> , vyhledejte `elementid==SEID_WindowFrame` .  
  
4. Otestujte `varValueNew` parametr pro dvě věci:  
  
    1. Rámec okna, které hledáte.  
  
    2. Bod, ve kterém program ztratí výběr do tohoto rámce okna.
