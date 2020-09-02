---
title: 'Postupy: registrace událostí pro ukládání textu do vyrovnávací paměti pomocí starší verze rozhraní API | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204096"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Postupy: Registrace událostí vyrovnávací paměti textu pomocí zastaralého rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud k textové vyrovnávací paměti přistupujete pomocí starší verze rozhraní API, měli byste se zaregistrovat pro události textové vyrovnávací paměti, jak je znázorněno v následujícím postupu.  
  
### <a name="to-advise-text-buffer-events"></a>Doporučení pro události textové vyrovnávací paměti  
  
1. Z ukazatele na jedno z rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> , zavolejte `QueryInterface` pro ukazatel na <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
2. Zavolejte <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> metodu a předejte ID rozhraní událostí, pro které chcete zaregistrovat.  
  
     Například pokud chcete zaregistrovat pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> , předejte ID rozhraní IID_IVsTextLinesEvents.  
  
     Vyrovnávací paměť textu vrací ukazatel na <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní pro příslušný objekt spojovacího bodu.  
  
3. Pomocí tohoto ukazatele zavolejte <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> metodu a předejte ukazatel na implementaci rozhraní události, pro které chcete zaregistrovat, například `IVsTextLinesEvents` rozhraní.  
  
     Prostředí vrátí soubor cookie, který pak můžete použít k zastavení naslouchání událostmi voláním <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> metody.  
  
## <a name="see-also"></a>Viz také  
 [Události vyrovnávací paměti textu v zastaralém rozhraní API](../extensibility/text-buffer-events-in-the-legacy-api.md)
