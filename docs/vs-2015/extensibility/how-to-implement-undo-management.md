---
title: 'Postupy: Implementace správy Undo | Dokumentace Microsoftu'
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
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7eb3e3a1bbda905b2f5c5819835b10513d444fb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806097"
---
# <a name="how-to-implement-undo-management"></a>Postupy: Implementace správy zpět
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Primární rozhraní používá ke správě vrácení zpět se ale <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, která je implementována pomocí prostředí. Pro podporu správy vrácení zpět, implementovat samostatné zpět jednotky (tedy <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, který může obsahovat více jednotlivé kroky.  
  
 Implementace správy vrácení zpět se liší v závislosti na tom, zda editor podporuje několik zobrazení, nebo ne. Postupy pro každou implementaci jsou podrobně popsané v následujících částech.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Případy, kdy editor podporuje jedno zobrazení  
 V tomto scénáři editor nepodporuje více zobrazení. Existuje pouze jeden editor a jeden dokument a podporují vrácení zpět. Implementace správy zpět pomocí následujícího postupu.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Pro podporu zpět správy jedním zobrazením editoru  
  
1.  Volání `QueryInterface` na `IServiceProvider` rozhraní okna rámce pro `IOleUndoManager`, z objektu zobrazení dokumentu k tomuto správci vrácení zpět (`IID_IOLEUndoManager`).  
  
2.  Při zobrazení je umístěna do okna rámce, získá lokality ukazatel, který můžete použít k volání `QueryInterface` pro `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Případy, kdy editor podporuje více zobrazení  
 Pokud už máte dokument a zobrazení oddělení, je obvykle jeden vhodný program přidružený k samotný dokument. Všechny jednotky akcí zpět se umístí na jeden vhodný program přidružený k objektu data dokumentu.  
  
 Místo zobrazení, zadávání dotazů na vhodný, z nichž je jedna pro každé zobrazení, data dokumentu objektu volání <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> vytvořit instanci správce akcí zpět, určení identifikátoru třídy CLSID_OLEUndoManager. Identifikátor třídy je definována v souboru OCUNDOID.h.  
  
 Při použití <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> k vytvoření vlastní instance Správce akcí zpět, pomocí následujícího postupu připojí správce akcí zpět do prostředí.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Připojí správce akcí zpět do prostředí  
  
1. Volání `QueryInterface` objekt vrácený z <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> pro `IID_IOleUndoManager`. Ukazatel na Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2. Volání `QueryInterface` na `IOleUndoManager` pro `IID_IOleCommandTarget`. Ukazatel na Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3. Propojení vašich <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> volání do uložených `IOleCommandTarget` rozhraní pro následující příkazy StandardCommandSet97:  
  
   -   cmdidUndo  
  
   -   cmdidMultiLevelUndo  
  
   -   cmdidRedo  
  
   -   cmdidMultiLevelRedo  
  
   -   cmdidMultiLevelUndoList  
  
   -   cmdidMultiLevelRedoList  
  
4. Volání `QueryInterface` na `IOleUndoManager` pro `IID_IVsChangeTrackingUndoManager`. Ukazatel na Store <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
    Použít ukazatele <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> volat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> metody.  
  
5. Volání `QueryInterface` na `IOleUndoManager` pro `IID_IVsLinkCapableUndoManager`.  
  
6. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> s dokumentem, který by měly také implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> rozhraní. Při zavření dokumentu volání `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7. Při zavření dokumentu volání `QueryInterface` na vašeho správce akcí zpět pro `IID_IVsLifetimeControlledObject`.  
  
8. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Při změně v dokumentu, volání <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> na správce s `OleUndoUnit` třídy. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> Metoda uchovává odkaz na objekt, takže obecně, uvolníte ho hned po <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
   `OleUndoManager` Třída reprezentuje instanci zásobníku jedno vrácení zpět. Proto je jeden objekt správce akcí zpět na datové entity, které jsou sledovány pro vrácení zpět nebo znovu.  
  
> [!NOTE]
>  Zatímco objekt správce akcí zpět hojně používají textový editor, je hlavní komponenty, která nemá žádné specifické podpoře pro textový editor. Pokud chcete zajistit podporu více úrovní zpět nebo znovu, můžete k tomu tento objekt.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Postupy: Vymazání zásobníku příkazu Zpět](../extensibility/how-to-clear-the-undo-stack.md)

