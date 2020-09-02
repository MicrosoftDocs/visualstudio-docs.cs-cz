---
title: Dokumentovat okna | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e62be456422b7ee5e9f2828a44a6be05e1211d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64791116"
---
# <a name="document-windows"></a>Okna dokumentů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V aplikaci Visual Studio je *okno dokumentu* rámcové podřízené okno, které je spojeno s oknem MDI (Multiple Document Interface). Okna dokumentů se obvykle používají pro zobrazení a úpravy zdrojového kódu nebo textu, ale mohou také hostovat jiné funkční typy. Okna dokumentů:  
  
- Lze uspořádat do samostatných vodorovných nebo svislých skupin karet v nadřazeném MDI, aby bylo možné zobrazit současně více souborů.  
  
- Může být ukotven v libovolném pořadí v nadřazeném MDI.  
  
- Dá se volně uvolnit.  
  
- Jsou propojeny v pořadí prvků do jiných oken MDI.  
  
  Příkazy pro seskupování, ukotvení a plovoucí lze nalézt v místní nabídce karty okno dokumentu.  
  
  Další informace o chování okna v aplikaci Visual Studio naleznete v tématu [přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implementace okna dokumentu  
 Okna dokumentů jsou vytvořena implementací editoru. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>Rozhraní vytváří okna dokumentů jako součást vytváření instancí editoru. Další informace naleznete v tématu [starší rozhraní v editoru](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
> Chcete-li v okně poskytnout zpětné a předávací navigační body, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> rozhraní. Textový editor používá textové značky k identifikaci navigačních bodů v dokumentu.  
  
## <a name="the-running-document-table"></a>Spuštěná tabulka dokumentů  
 Rozhraní IDE používá spuštěnou tabulku dokumentů (RDT) ke sledování stavu každého okna dokumentu. RDT je mechanismus, pomocí kterého se okna dokumentů upozorní na události, například když je řešení uzavřeno nebo když byl soubor upravován. Další informace najdete v tématu [Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Viz také  
 [Odložené načtení dokumentu](../../extensibility/internals/delayed-document-loading.md)
