---
title: 'Postupy: otevření editoru pro konkrétní projekt | Dokumentace Microsoftu'
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
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 52d1fda1c3a1c2e8aac116c52afc8bf6738e23ea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817669"
---
# <a name="how-to-open-project-specific-editors"></a>Postupy: otevření editoru pro konkrétní projekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud je soubor položky jsou otevírány projekt vnitřně vázán na konkrétní editor pro tento projekt, musí projekt otevřete soubor pomocí editoru specifické pro projekt. Soubor není možné delegovat na rozhraní IDE mechanismus zvolení editoru. Například namísto použití editoru standardního rastrových obrázků, můžete použít tuto možnost editoru pro konkrétní projekt k určení editoru konkrétní rastrový obrázek, který rozpoznává informace v souboru, který je jedinečný pro váš projekt.  
  
 Volání rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodu, když zjistí, že soubor by měl být otevírány konkrétním projektu. Další informace najdete v tématu [zobrazení souborů pomocí příkazu Otevřít soubor](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Použijte následující pokyny k implementaci `OpenItem` metoda může mít projektu otevřete soubor pomocí editoru specifické pro projekt.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>O implementaci metody OpenItem editorem specifické pro projekt  
  
1.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> – metoda (RDT_EditLock) k určení, zda soubor (datový objekt dokumentu) je již otevřen.  
  
    > [!NOTE]
    >  Další informace o data dokumentu a objekty zobrazení dokumentu najdete v tématu [dat dokumentů a zobrazení dokumentu ve vlastních editorech](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Pokud soubor již je otevřen, resurface soubor voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metoda a zadáte třeba hodnotu IDO_ActivateIfOpen pro `grfIDO` parametru.  
  
     Pokud je soubor otevřen a vlastní dokumentu jiný projekt než volajícího projektu, zobrazí se upozornění pro uživatele, který je v editoru se otevře z jiného projektu. Pak se zobrazí okno souboru.  
  
3.  Pokud vaše textovou vyrovnávací paměť (datový objekt dokumentu) je již otevřen a chcete připojit se k němu jiné zobrazení, zodpovídáte za zapojování tohoto zobrazení. Doporučený postup pro vytváření instance zobrazení (objekt zobrazení dokumentu) z projektu, vypadá takto:  
  
    1.  Volání `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> služby získat ukazatel <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> rozhraní.  
  
    2.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> metodu pro vytvoření instance třídy zobrazení dokumentu.  
  
4.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> metoda zadáním objektu zobrazení dokumentu.  
  
     Tato metoda weby objekt zobrazení dokumentu v okně dokumentu.  
  
5.  Provést odpovídající volání na buď <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> nebo <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> metody.  
  
     Zobrazení by měl být v tuto chvíli plně inicializován a jste připravení otevřít.  
  
6.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodu pro zobrazení a otevřete zobrazení.  
  
## <a name="see-also"></a>Viz také  
 [Otevření a uložení položek projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Postupy: otevření standardních editorů](../extensibility/how-to-open-standard-editors.md)   
 [Postupy: Otevření editorů pro otevřené dokumenty](../extensibility/how-to-open-editors-for-open-documents.md)

