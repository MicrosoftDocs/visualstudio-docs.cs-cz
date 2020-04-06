---
title: Objekt VSTextView | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 81d5e02d6ec18f8561a83b414532a4b78def5c09
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697716"
---
# <a name="vstextview-object"></a>Objekt VSTextView

Zobrazení textu je okno, které umožňuje uživatelům zobrazit a upravit text Unicode textové vyrovnávací paměti. Zobrazení je v podstatě to, co většina uživatelů označuje jako editor. Vzhledem k tomu, že zobrazení je odděleno od vyrovnávací paměti různými textovými vrstvami (zalamování řádků, osnova textu a tak dále), není zaručeno, že zobrazení bude přesnou reprezentací textu ve vyrovnávací paměti. Další informace o zobrazení textu naleznete [v tématu Přístup k zobrazení Text pomocí starší rozhraní API](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015).

V následující tabulce jsou uvedena <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> rozhraní v objektu.

|Rozhraní|Popis|
|---------------|-----------------|
|[Zdroj IDrop](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standardní rozhraní OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standardní rozhraní OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standardní rozhraní OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standardní rozhraní OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umožňuje vytváření složených akcí (to znamená akcí seskupených do jedné jednotky vrátit nebo znovu).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Poskytuje základní metody pro správu a přístup k zobrazení. `IVsTextView`není bezpečně vytesána se závitem.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Vytvoří a spravuje podokno okna.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Spolupracuje s textovými vrstvami.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Provádí operace v zobrazení z jiného vlákna.|

## <a name="see-also"></a>Viz také

- [Úpravy obrázků](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objekt VSTextBuffer](../extensibility/vstextbuffer-object.md)
