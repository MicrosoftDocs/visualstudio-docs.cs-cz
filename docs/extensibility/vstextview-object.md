---
title: Objekt VSTextView | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 927bbee8bde62ff24396ea7b50e55e901b8cff06
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189017"
---
# <a name="vstextview-object"></a>Objekt VSTextView

Textové zobrazení je okno, které umožňuje uživatelům zobrazit a upravit textovou vyrovnávací paměť textu v kódu Unicode. V podstatě se jedná o to, co většina uživatelů na Editor odkazuje. Vzhledem k tomu, že je zobrazení odděleno od vyrovnávací paměti různými textovými vrstvami (zalamování řádků, text sbalení a tak dále), není zaručeno, že zobrazení je přesná reprezentace textu ve vyrovnávací paměti. Další informace o zobrazení textu najdete v tématu [přístup k zobrazení TheText pomocí starší verze rozhraní API](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015).

Následující tabulka ukazuje rozhraní v objektu <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

|Rozhraní|Popis|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standardní rozhraní OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standardní rozhraní OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standardní rozhraní OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standardní rozhraní OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umožňuje vytváření složených akcí (tj. akcí, které jsou seskupeny v jedné jednotce zpět/znovu).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Poskytuje základní metody pro správu a přístup k zobrazení. `IVsTextView` není bezpečný pro přístup z více vláken.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Vytvoří a spravuje podokno okna.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Komunikuje s vrstvami textu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Provádí operace v zobrazení z jiného vlákna.|

## <a name="see-also"></a>Viz také:

- [Úpravy obrázků](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objekt VSTextBuffer](../extensibility/vstextbuffer-object.md)