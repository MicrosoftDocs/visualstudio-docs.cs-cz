---
title: VSCodeWindow – | Microsoft Docs
description: Seznamte se s okny kódu, což jsou specializovaná okna dokumentů, která mohou obsahovat jedno nebo více zobrazení textu, obvykle objekt VsTextView.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9803132605ee81c67785c8c0154861b26730ca5f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905329"
---
# <a name="vscodewindow-object"></a>Objekt VSCodeWindow
Okno kódu je specializované okno dokumentu, které může obsahovat jedno nebo více zobrazení textu, obvykle <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objekt .

 Okno kódu je architekturálně okno dokumentu, které je v rámci rámce okna. Funkční okno kódu je jednoduše okno dokumentu s dalšími funkcemi. V režimu MDI (multiple-document interface) je okno kódu podřízeným rámcem MDI. Další informace najdete v tématu [Přizpůsobení oken kódu pomocí starší verze rozhraní API.](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

 Následující tabulka obsahuje rozhraní v <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objektu .

|Metoda|Popis|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Poskytuje obecný přístupový mechanismus pro vyhledání služby, kterou identifikuje globálně jedinečný identifikátor (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Představuje podřízené rozhraní mdi (multiple document interface) obsahující jedno nebo více zobrazení kódu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Vyplní rámec okna.|

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Úpravy obrázků](https://www.microsoft.com/download/details.aspx?id=55984)