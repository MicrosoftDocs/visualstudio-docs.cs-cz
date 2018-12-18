---
title: 'Postupy: použití správy propojená operace vrácení zpět | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 255ad8de79b13a74816b2abd28281ac5de6f1932
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370559"
---
# <a name="how-to-use-linked-undo-management"></a>Postupy: použití propojené správu zpět
Propojená operace vrácení zpět mu umožní současně zpět stejné úpravy ve více souborech. Například změny souběžných textu do více souborů programu, jako je například soubor hlaviček a soubor jazyka Visual C++ je propojená operace vrácení zpět transakcí. Propojená operace vrácení zpět funkce je integrovaná do prostředí provádění správce akcí zpět a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> umožňuje manipulaci s tuto funkci. Propojená operace vrácení zpět je implementováno nadřazenou jednotku, která můžete propojit samostatné zpět zásobníky dohromady a považovány za celek jedno vrácení zpět. Postup pro používání propojená operace vrácení zpět je podrobně popsán v následující části.  
  
## <a name="to-use-linked-undo"></a>Chcete-li použít propojená operace vrácení zpět  
  
1.  Volání `QueryService` na `SVsLinkedUndoManager` získat ukazatel na `IVsLinkedUndoTransactionManager`.  
  
2.  Vytvořte jednotku počáteční nadřazené propojená operace vrácení zpět voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Tím se nastaví výchozí bod pro sadu zásobníky akcí zpět na seskupené do zásobníků propojená operace vrácení zpět. V `OpenLinkedUndo` metoda budete taky muset zadat, jestli chcete propojená operace vrácení zpět striktní nebo nepřísném. Non striktní propojená operace vrácení zpět chování znamená, že některé z těchto dokumentů s propojená operace vrácení zpět na stejné úrovni můžete zavřít a nechat druhé propojené vrátit na stejné úrovni na svých zásobníků. Striktní propojená operace vrácení zpět chování Určuje, že všechny balíčky propojená operace vrácení zpět na stejné úrovni jako vrátit zpět společně nebo vůbec ne. Přidat další propojené zásobníky akcí zpět voláním [IOleUndoManager::Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) metody.  
  
3.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> vrátit zpět všechny jednotky propojená operace vrácení zpět jako jeden.  
  
    > [!NOTE]
    >  Implementace správy propojená operace vrácení zpět v editoru, přidáte zpět správy. Další informace o implementaci správy propojená operace vrácení zpět, najdete v části [postupy: implementace řízení zpět](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Viz také:  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Postupy: implementace řízení zpět](../extensibility/how-to-implement-undo-management.md)