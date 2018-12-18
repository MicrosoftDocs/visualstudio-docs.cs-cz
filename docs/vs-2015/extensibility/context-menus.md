---
title: Kontextové nabídky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efd4e1c80b9af2a0d73730f0bd7d741cd877fb07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796841"
---
# <a name="context-menus"></a>Místní nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kontextové nabídky se zobrazí, když uživatel klepne pravým tlačítkem myši v aktivní oblasti od klientské oblasti a zrušte zaškrtnutí, když se uvolní pravé tlačítko myši.  
  
## <a name="editor-context-menus"></a>Kontextové nabídky editoru  
 Tím, že zachytává `ECMD_SHOWCONTEXTMENU`, vaše služba jazyka můžete řídit kontextové nabídky, které se zobrazí v editoru. Vlastní místní nabídce zobrazíte zpracování tohoto příkazu je předána do vaší <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Pokud tento příkaz nelze zpracovat, rozhraní IDE zobrazí standardní místní nabídka editoru k dispozici. Můžete také řídit obsah v místní nabídce základ jednotlivé značky. Další informace o tom, naleznete v tématu [pomocí značky Text pomocí rozhraní API pro starší verze](../extensibility/using-text-markers-with-the-legacy-api.md) a [zachycování příkazy služby starší verze jazyka](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Viz také  
 [Vývoj služby starší verze jazyka](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)

