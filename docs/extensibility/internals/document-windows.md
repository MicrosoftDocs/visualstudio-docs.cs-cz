---
title: Dokumentovat windows | Microsoft Docs
description: Přečtěte si o oknech dokumentů v Visual Studio, včetně toho, jak je implementovat a jak tabulka Spuštěný dokument sleduje jejich stav.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: df7a797c0b4587698197412f49eef6bfab183a7a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899911"
---
# <a name="document-windows"></a>Okna dokumentů
V Visual Studio je okno *dokumentu* orámované podřízené okno, které je přidruženo k oknu mdi (multiple-document interface). Okna dokumentů se obvykle používají k zobrazení a úpravám zdrojového kódu nebo textu, ale mohou hostovat i jiné funkční typy. Okna dokumentů:

- Může být uspořádaný do samostatných skupin s vodorovnými nebo svislými tabulátory v nadřazené MDI, aby bylo možné zobrazit více souborů současně.

- Lze ukotvit v libovolném pořadí v nadřazené mdi.

- Může být volně plovoucí.

- Jsou propojeny v pořadí podle karet s jinými okny MDI.

  Příkazy pro seskupení, ukotvení a plovoucí desetinnou čárku najdete na kartě okna dokumentu v místní nabídce.

  Další informace o chování okna v Visual Studio najdete v tématu [Přizpůsobení rozložení oken.](../../ide/customizing-window-layouts-in-visual-studio.md)

## <a name="document-window-implementation"></a>Implementace okna dokumentu
 Okna dokumentů se vytvářejí implementací editoru. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> vytvoří okna dokumentů jako součást vytváření instancí editoru. Další informace najdete v tématu [Starší verze rozhraní v editoru](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015).

> [!NOTE]
> Pokud chcete poskytnout navigační body zpět a vpřed v okně, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> rozhraní . Textový editor používá k identifikaci navigačních bodů v dokumentu textové značky.

## <a name="the-running-document-table"></a>Tabulka Spuštěný dokument
 Integrované vývojové prostředí (IDE) používá ke sledování stavu každého okna dokumentu spuštěnou tabulku dokumentů (RDT). RDT je mechanismus, pomocí kterého jsou okna dokumentů upozorňována na události, například při zavření řešení nebo úpravě souboru. Další informace najdete v tématu [Spuštění tabulky dokumentů.](../../extensibility/internals/running-document-table.md)

## <a name="see-also"></a>Viz také
- [Zpožděné načítání dokumentů](../../extensibility/internals/delayed-document-loading.md)
