---
title: Vstextview – objekt | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5815adbdc05685999d7dcd64139ebfd29b8776b9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765087"
---
# <a name="vstextview-object"></a>VSTextView – objekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení textu je okno, které umožňuje uživatelům zobrazit a upravit text v kódu Unicode textové vyrovnávací paměti. Zobrazení je v podstatě, co většina uživatelů označujeme jako editor. Protože zobrazení je oddělen od vyrovnávací paměti různé vrstvy text (zalamování řádků, osnovy textu a tak dále), nemusí být přesné reprezentace textu ve vyrovnávací paměti zobrazení. Další informace o zobrazení textu, naleznete v tématu [přístup k text zobrazení pomocí starší verze rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 V následující tabulce jsou uvedeny rozhraní v <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objektu.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Standardní rozhraní OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standardní rozhraní OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standardní rozhraní OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standardní rozhraní OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Povolí vytváření složených akce (to znamená, akce, které jsou seskupeny do jednoho zpět/znovu jednotka).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Poskytuje základní metody pro správu a přístup k zobrazení. `IVsTextView` není bezpečné.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Vytváří a spravuje podokno okna.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Komunikuje s vrstvami text.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Provádí operace pro zobrazení z jiného vlákna.|  
  
## <a name="see-also"></a>Viz také  
 [Úpravy obrázků](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Vstextbuffer – objekt](../extensibility/vstextbuffer-object.md)   
 [Přístup k textovému zobrazení pomocí zastaralého rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

