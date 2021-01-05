---
title: Objekt VSCodeWindow | Microsoft Docs
description: Seznamte se s okny kódu, což jsou specializovaná okna dokumentů, která mohou obsahovat jedno nebo více textových zobrazení, obvykle objekt VsTextView.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a778cde66bc85a6f3cd8a13b5f2bb6fdb41844de
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864001"
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