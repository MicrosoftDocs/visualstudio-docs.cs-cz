---
title: Dokumentovat okna | Microsoft Docs
description: Přečtěte si o oknech dokumentů v aplikaci Visual Studio, včetně způsobu jejich implementace a způsobu, jakým běžící tabulka dokumentů (RDT) sleduje svůj stav.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f62a6cc4f7b217bbcf8c94b437bcd7ce9d0d1b2b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946732"
---
# <a name="document-windows"></a>Okna dokumentů
V aplikaci Visual Studio je *okno dokumentu* rámcové podřízené okno, které je spojeno s oknem MDI (Multiple Document Interface). Okna dokumentů se obvykle používají pro zobrazení a úpravy zdrojového kódu nebo textu, ale mohou také hostovat jiné funkční typy. Okna dokumentů:

- Lze uspořádat do samostatných vodorovných nebo svislých skupin karet v nadřazeném MDI, aby bylo možné zobrazit současně více souborů.

- Může být ukotven v libovolném pořadí v nadřazeném MDI.

- Dá se volně uvolnit.

- Jsou propojeny v pořadí prvků do jiných oken MDI.

  Příkazy pro seskupování, ukotvení a plovoucí lze nalézt v místní nabídce karty okno dokumentu.

  Další informace o chování okna v aplikaci Visual Studio naleznete v tématu [přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Implementace okna dokumentu
 Okna dokumentů jsou vytvořena implementací editoru. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>Rozhraní vytváří okna dokumentů jako součást vytváření instancí editoru. Další informace naleznete v tématu [starší rozhraní v editoru](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015).

> [!NOTE]
> Chcete-li v okně poskytnout zpětné a předávací navigační body, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> rozhraní. Textový editor používá textové značky k identifikaci navigačních bodů v dokumentu.

## <a name="the-running-document-table"></a>Spuštěná tabulka dokumentů
 Rozhraní IDE používá spuštěnou tabulku dokumentů (RDT) ke sledování stavu každého okna dokumentu. RDT je mechanismus, pomocí kterého se okna dokumentů upozorní na události, například když je řešení uzavřeno nebo když byl soubor upravován. Další informace najdete v tématu [Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Viz také
- [Zpožděné načítání dokumentu](../../extensibility/internals/delayed-document-loading.md)
