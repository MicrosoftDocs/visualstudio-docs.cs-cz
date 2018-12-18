---
title: 'Postupy: registrace pro textové vyrovnávací paměti události s rozhraním API starší verze | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ffe8362f26a55fdb6a9fe236782965a2062ed69
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639930"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Postupy: registrace pro události vyrovnávací paměti textu se starší verze rozhraní API
Pokud vyrovnávací paměť textu přistupujete pomocí starší verze rozhraní API, byste měli zaregistrovat pro události vyrovnávací paměti textu, jak je znázorněno v následujícím postupu.  
  
## <a name="to-advise-text-buffer-events"></a>Radit události vyrovnávací paměť textu  
  
1.  Z ukazatele na jedno z rozhraní na <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, volání `QueryInterface` ukazatele na <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Volání <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> metoda a předejte jí rozhraní ID událostí, pro které chcete zaregistrovat.  
  
     Například, pokud chcete zaregistrovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, pak předejte ID IID_IVsTextLinesEvents rozhraní.  
  
     Vrací ukazatel na textovou vyrovnávací paměť <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní pro objekt bodu příslušné připojení.  
  
3.  Pomocí tohoto ukazatele, zavolejte <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> metodu ukazatel na implementaci rozhraní události, pro kterou chcete zaregistrovat, například `IVsTextLinesEvents` rozhraní.  
  
     Vrátí prostředí do souboru cookie, který potom slouží k zastavení naslouchá událostem voláním <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> metody.  
  
## <a name="see-also"></a>Viz také:  
 [Události vyrovnávací paměti textu ve starší verzi rozhraní API](../extensibility/text-buffer-events-in-the-legacy-api.md)