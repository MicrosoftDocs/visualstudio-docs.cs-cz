---
title: Kontextové nabídky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184275"
---
# <a name="context-menus"></a>Místní nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kontextové nabídky se zobrazí, když uživatel klikne pravým tlačítkem myši v aktivní oblasti klientské oblasti a při uvolnění pravého tlačítka myši zaškrtnuto.  
  
## <a name="editor-context-menus"></a>Kontextové nabídky editoru  
 Zachytáváním `ECMD_SHOWCONTEXTMENU` může vaše jazyková služba řídit kontextové nabídky, které se zobrazí v editoru. Pokud chcete zobrazit vlastní kontextovou nabídku, zpracujte tento příkaz, když se předává do vašeho <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> . Pokud tento příkaz nezpracujete, rozhraní IDE zobrazí standardní kontextovou nabídku, která je k dispozici pro Editor. Můžete také řídit obsah místní nabídky podle značky. Další informace najdete v tématu [Použití textových značek se starší verzí rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md) a [zachycení příkazů služby starší verze jazyka](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Viz také  
 [Vývoj služby starší verze jazyka](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
