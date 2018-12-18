---
title: 'Postupy: registrace pro textové vyrovnávací paměti události s rozhraním API starší verze | Dokumentace Microsoftu'
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
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e895f2d67c23454ad3f7481e558f6dde542867b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782775"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Postupy: registrace pro textové vyrovnávací paměti události s rozhraním API starší verze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud vyrovnávací paměť textu přistupujete pomocí starší verze rozhraní API, byste měli zaregistrovat pro události vyrovnávací paměti textu, jak je znázorněno v následujícím postupu.  
  
### <a name="to-advise-text-buffer-events"></a>Radit události vyrovnávací paměť textu  
  
1.  Z ukazatele na jedno z rozhraní na <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, volání `QueryInterface` ukazatele na <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Volání <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> metoda a předejte jí rozhraní ID událostí, pro které chcete zaregistrovat.  
  
     Například, pokud chcete zaregistrovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, pak předejte ID IID_IVsTextLinesEvents rozhraní.  
  
     Vrací ukazatel na textovou vyrovnávací paměť <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> rozhraní pro objekt bodu příslušné připojení.  
  
3.  Pomocí tohoto ukazatele, zavolejte <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> metodu ukazatel na implementaci rozhraní události, pro kterou chcete zaregistrovat, například `IVsTextLinesEvents` rozhraní.  
  
     Vrátí prostředí do souboru cookie, který potom slouží k zastavení naslouchá událostem voláním <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> metody.  
  
## <a name="see-also"></a>Viz také  
 [Události vyrovnávací paměti textu v zastaralém rozhraní API](../extensibility/text-buffer-events-in-the-legacy-api.md)

