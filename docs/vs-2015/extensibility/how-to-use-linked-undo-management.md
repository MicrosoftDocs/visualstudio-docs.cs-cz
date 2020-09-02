---
title: 'Postupy: použití propojené správy akcí zpět | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795504"
---
# <a name="how-to-use-linked-undo-management"></a>Postupy: Použití správy propojeného příkazu Zpět
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Odkaz na vrácení zpět umožňuje uživateli souběžně vrátit stejné úpravy ve více souborech. Například současná Změna textu mezi více soubory programu, jako je například hlavičkový soubor a Visual C++ soubor, je propojená transakce zpět. Odkazovaná funkce vrácení zpět je integrována do implementace nástroje Undo Manager v prostředí a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> umožňuje manipulaci s touto funkcí. Propojené vrácení zpět je implementováno nadřazenou jednotkou vrácení zpět, která může propojit samostatné zásobníky pro vrácení zpět, aby je bylo možné považovat za jedinou jednotku vrácení změn. Postup použití propojených akcí zpět je popsán v následující části.  
  
### <a name="to-use-linked-undo"></a>Použití propojených akcí zpět  
  
1. Zavolejte `QueryService` na, chcete-li `SVsLinkedUndoManager` získat ukazatel na `IVsLinkedUndoTransactionManager` .  
  
2. Vytvořte počáteční nadřazený objekt propojené jednotky vrácení zpět voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> . Tím se nastaví počáteční bod pro sadu zásobníků pro vrácení zpět, který se bude seskupovat do propojených zásobníků pro vrácení zpět. V `OpenLinkedUndo` metodě budete taky muset určit, jestli chcete, aby se odkaz zpátky vrátil na striktní nebo nestriktní. Nestriktní propojené chování při vracení znamená, že některé dokumenty s propojenými akcemi zpět na stejné úrovni můžou zavřít a pořád zůstat na všech svých zásobníkech zpátky na stejné úrovni. V případě striktního propojeného chování se určuje, že všechny propojené zásobníky zpět na stejné úrovni musí být nedokončené dohromady nebo vůbec ne. Přidejte následné propojené zásobníky pro vrácení zpět voláním metody [IOleUndoManager:: Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) .  
  
3. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> na vrácení všech propojených jednotek vrácení zpět jako jednoho.  
  
    > [!NOTE]
    > Chcete-li implementovat propojenou správu zpět v editoru, přidejte správu zpět. Další informace o implementaci propojené správy zpět naleznete v tématu [How to: Implementing Undo Management](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Postupy: Implementace správy příkazu Zpět](../extensibility/how-to-implement-undo-management.md)
