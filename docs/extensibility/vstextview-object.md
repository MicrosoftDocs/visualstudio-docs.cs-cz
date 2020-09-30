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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06e1ba7c10912f23fedc09892e03e2105ff2bab4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583603"
---
# <a name="vstextview-object"></a>Objekt VSTextView

Textové zobrazení je okno, které umožňuje uživatelům zobrazit a upravit textovou vyrovnávací paměť textu v kódu Unicode. V podstatě se jedná o to, co většina uživatelů na Editor odkazuje. Vzhledem k tomu, že je zobrazení odděleno od vyrovnávací paměti různými textovými vrstvami (zalamování řádků, text sbalení a tak dále), není zaručeno, že zobrazení je přesná reprezentace textu ve vyrovnávací paměti. Další informace o zobrazení textu najdete v tématu [přístup k zobrazení TheText pomocí starší verze rozhraní API](../vs-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api.md?view=vs-2015&preserve-view=true).

V následující tabulce jsou uvedena rozhraní v <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objektu.

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

## <a name="see-also"></a>Viz také

- [Úpravy obrázků](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objekt VSTextBuffer](../extensibility/vstextbuffer-object.md)