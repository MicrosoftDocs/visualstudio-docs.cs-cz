---
title: Dokument Windows | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711033a4ad2e782ecbe509595266426d186bed8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708515"
---
# <a name="document-windows"></a>Okna dokumentu
V sadě Visual Studio je *okno dokumentu* zarámované podřízeným oknem, které je přidruženo k oknu rozhraní MDI (multiple-document). Okna dokumentů se obvykle používají pro zobrazení a úpravu zdrojového kódu nebo textu, ale mohou také hostovat jiné funkční typy. Okna dokumentu:

- Lze uspořádat do samostatných vodorovných nebo svislých skupin karet v nadřazeném mdi, takže je možné zobrazit více souborů současně.

- Může být ukotven v libovolném pořadí v nadřazeném MDI.

- Může být volně vznášen.

- Jsou propojeny v pořadí karet s jinými okny MDI.

  Příkazy pro seskupení, ukotvení a plovoucí lze nalézt v místní nabídce pro kartu okna dokumentu.

  Další informace o chování oken v sadě Visual Studio naleznete v [tématu Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Implementace okna dokumentu
 Okna dokumentu jsou vytvořeny implementací editoru. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> vytvoří okna dokumentu jako součást vytváření instancí editoru. Další informace naleznete [v tématu Starší rozhraní v editoru](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015).

> [!NOTE]
> Chcete-li poskytnout navigační body vzad <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> a vpřed v okně, implementujte rozhraní. Textový editor používá textové značky k identifikaci navigačních bodů v dokumentu.

## <a name="the-running-document-table"></a>Tabulka Spuštěný dokument
 IDE používá tabulku Spuštěný dokument (RDT) ke sledování stavu každého okna dokumentu. RDT je mechanismus, jehož prostřednictvím jsou okna dokumentu upozorňována na události, například při zavření řešení nebo při úpravě souboru. Další informace naleznete v tématu [Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Viz také
- [Zpožděné načítání dokumentů](../../extensibility/internals/delayed-document-loading.md)
