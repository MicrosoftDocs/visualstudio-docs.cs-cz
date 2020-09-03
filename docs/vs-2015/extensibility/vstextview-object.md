---
title: Objekt VSTextView | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22e4d4cdf1e5ca610dbdb067f8195fb730139c3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690689"
---
# <a name="vstextview-object"></a>VSTextView – objekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Textové zobrazení je okno, které umožňuje uživatelům zobrazit a upravit text ve vyrovnávací paměti textu v kódu Unicode. V podstatě se jedná o to, co většina uživatelů na Editor odkazuje. Vzhledem k tomu, že je zobrazení odděleno od vyrovnávací paměti různými textovými vrstvami (zalamování řádků, text sbalení a tak dále), není zaručeno, že zobrazení je přesná reprezentace textu ve vyrovnávací paměti. Další informace o zobrazení textu najdete v tématu [přístup k zobrazení TheText pomocí starší verze rozhraní API.](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 V následující tabulce jsou uvedena rozhraní v <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objektu.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standardní rozhraní OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standardní rozhraní OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standardní rozhraní OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standardní rozhraní OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umožňuje vytváření složených akcí (tj. akcí, které jsou seskupeny v jedné jednotce zpět/znovu).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Poskytuje základní metody pro správu a přístup k zobrazení. `IVsTextView` není bezpečná pro přístup z více vláken.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Vytvoří a spravuje podokno okna.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Komunikuje s vrstvami textu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Provádí operace v zobrazení z jiného vlákna.|  
  
## <a name="see-also"></a>Viz také  
 [Úpravy obrázků](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Objekt VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Přístup k textovému zobrazení pomocí zastaralého rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
