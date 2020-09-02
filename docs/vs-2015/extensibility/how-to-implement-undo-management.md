---
title: 'Postupy: Implementace správy akcí zpět | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831123"
---
# <a name="how-to-implement-undo-management"></a>Postupy: Implementace správy příkazu Zpět
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Primární rozhraní používané pro vrácení zpět se správou je <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> , které je implementováno prostředím. Pro podporu správy funkce undo implementujte samostatné jednotky vrácení zpět (tj <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> ., které mohou obsahovat více jednotlivých kroků).  
  
 Způsob implementace zrušení správy se liší v závislosti na tom, zda editor podporuje více zobrazení, nebo ne. Postupy pro jednotlivé implementace jsou podrobně popsané v následujících částech.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Případy, kdy editor podporuje jedno zobrazení  
 V tomto scénáři editor nepodporuje více zobrazení. Je k dispozici pouze jeden editor a jeden dokument a podpora funkce zpět. K implementaci správy zpět použijte následující postup.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Podpora vrácení se správou zpět pro Editor s jedním zobrazením  
  
1. Zavolejte `QueryInterface` na `IServiceProvider` rozhraní v rámečku okna pro `IOleUndoManager` , z objektu zobrazení dokumentu pro přístup k funkci Undo Manager ( `IID_IOLEUndoManager` ).  
  
2. Když je zobrazení umístěno do rámce okna, získá ukazatel na webu, který může použít k volání `QueryInterface` `IServiceProvider` .  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Případy, kdy editor podporuje více zobrazení  
 Pokud máte dokument a zobrazení oddělení, je obvykle k samotnému dokumentu přidružen jeden správce vrácení zpět. Všechny jednotky akcí zpět jsou umístěny na jednom vedoucím vrácení zpět přidruženém k datovému objektu dokumentu.  
  
 Namísto zobrazení dotazu pro správce vrácení, pro který existuje jeden pro každé zobrazení, objekt data dokumentu volá <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> k vytvoření instance Správce zrušení, zadáním identifikátoru třídy CLSID_OLEUndoManager. Identifikátor třídy je definován v souboru OCUNDOID. h.  
  
 Když použijete <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> k vytvoření vlastní instance správce zpět, pomocí následujícího postupu zapojte správce funkce undo do prostředí.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Připojení správce pro vrácení zpět do prostředí  
  
1. Volání `QueryInterface` objektu vráceného z <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> pro `IID_IOleUndoManager` . Uložte ukazatel na <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> .  
  
2. Zavolat `QueryInterface` na `IOleUndoManager` `IID_IOleCommandTarget` . Uložte ukazatel na <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
3. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Přesměrujte vaše volání do uloženého `IOleCommandTarget` rozhraní pro následující příkazy StandardCommandSet97:  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - cmdidRedo  
  
   - cmdidMultiLevelRedo  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. Zavolat `QueryInterface` na `IOleUndoManager` `IID_IVsChangeTrackingUndoManager` . Uložte ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> .  
  
    Použijte ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> k volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> metody, a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> .  
  
5. Zavolat `QueryInterface` na `IOleUndoManager` `IID_IVsLinkCapableUndoManager` .  
  
6. Zavolejte na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> svůj dokument, který by měl také implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> rozhraní. Když je dokument uzavřený, zavolejte `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` .  
  
7. Když je dokument uzavřený, zavolejte `QueryInterface` na správce vrácení zpět pro `IID_IVsLifetimeControlledObject` .  
  
8. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A> .  
  
9. Pokud jsou v dokumentu provedeny změny, zavolejte <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> na manažera s `OleUndoUnit` třídou. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>Metoda uchovává odkaz na objekt, takže ho obvykle vydáte hned po <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> .  
  
   `OleUndoManager`Třída představuje jednu instanci zásobníku pro vrácení zpět. Proto je pro vrácení zpět nebo opakování sledován jeden objekt správce změn na každou entitu dat.  
  
> [!NOTE]
> I když je objekt Undo Manager v textovém editoru široce používán, jedná se o obecnou součást, která nemá žádnou konkrétní podporu pro textový editor. Pokud chcete podporovat funkce zpět nebo opakovat na více úrovních, můžete k tomu použít tento objekt.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Postupy: Vymazání zásobníku příkazu Zpět](../extensibility/how-to-clear-the-undo-stack.md)
