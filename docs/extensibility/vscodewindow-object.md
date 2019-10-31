---
title: Objekt VSCodeWindow | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36b7e0e6806f88efe373dffa3f21ba79baefb281
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189050"
---
# <a name="vscodewindow-object"></a>Objekt VSCodeWindow
Okno kódu je specializované okno dokumentu, které může obsahovat jedno nebo více textových zobrazení, obvykle objekt <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

 V architektuře je okno kódu okno dokumentu, které je v rámci rámce okna. V případě funkce je okno kódu jednoduše oknem dokumentu s dalšími funkcemi. V režimu MDI (Multiple Document Interface) je okno Code podřízeného rámce MDI. Další informace najdete v tématu [přizpůsobení oken kódu pomocí starší verze rozhraní API](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

 Následující tabulka obsahuje rozhraní v objektu <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>.

|Metoda|Popis|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Poskytuje obecný přístupový mechanismus pro vyhledání služby, kterou identifikuje globálně jedinečný identifikátor (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Představuje podřízený objekt MDI (Multiple Document Interface), který obsahuje jedno nebo více zobrazení kódu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Vyplní rámec okna.|

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Úpravy obrázků](https://www.microsoft.com/download/details.aspx?id=55984)