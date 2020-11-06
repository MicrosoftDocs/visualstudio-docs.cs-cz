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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d2cdbe12146dd5d3010b9bf8ffcdd130a0ea4bb
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414357"
---
# <a name="vscodewindow-object"></a>Objekt VSCodeWindow
Okno kódu je specializované okno dokumentu, které může obsahovat jedno nebo více textových zobrazení, obvykle <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objekt.

 V architektuře je okno kódu okno dokumentu, které je v rámci rámce okna. V případě funkce je okno kódu jednoduše oknem dokumentu s dalšími funkcemi. V režimu MDI (Multiple Document Interface) je okno Code podřízeného rámce MDI. Další informace najdete v tématu [přizpůsobení oken kódu pomocí starší verze rozhraní API](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

 Následující tabulka obsahuje rozhraní v <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objektu.

|Metoda|Popis|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Poskytuje obecný přístupový mechanismus pro vyhledání služby, kterou identifikuje globálně jedinečný identifikátor (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Představuje podřízený objekt MDI (Multiple Document Interface), který obsahuje jedno nebo více zobrazení kódu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Vyplní rámec okna.|

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Úpravy obrázků](https://www.microsoft.com/download/details.aspx?id=55984)