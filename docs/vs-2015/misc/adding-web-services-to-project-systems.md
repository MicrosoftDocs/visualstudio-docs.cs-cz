---
title: Přidávání webových služeb do systémů projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: f5b192be8e5f68ad9314fe08fff963c032013cb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002666"
---
# <a name="adding-web-services-to-project-systems"></a>Přidávání webových služeb do systémů projektů
Webové služby XML jsou obecně adresovatelné prostředky URL, které vracejí programové informace do systému projektu pomocí protokolu SOAP (Simple Object Access Protocol). Webové služby můžete integrovat do vašeho systému projektů VSPackage pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> rozhraní.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>Přidání webové služby do systému projektu  
  
1. Volání `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> rozhraní prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> služby.  
  
2. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> metodu. Pokud předáte `pDiscoverySession` parametr jako, vytvoří se `NULL` pro vás relace zjišťování a relace se uloží do mezipaměti, aby byla k dispozici pro následné použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> Metoda vrací ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2> .  
  
3. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> metodu. Do objektu Automation předejte jako parametr složku odkazy webové služby `pUnkWebReferenceFolder` . Prostředí sady Visual Studio pak zkontroluje, zda je webová služba již přítomna. Pokud webová služba není k dispozici, prostředí stáhne a přidá webovou službu do složky a dalších souborů (například soubory. WSDL) do podřízených uzlů této složky.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>