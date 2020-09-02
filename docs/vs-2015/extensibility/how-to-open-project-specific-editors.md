---
title: 'Postupy: otevření editorů specifických pro projekt | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2439a07f63b8da854ca8dc331d26e30f49503257
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64826636"
---
# <a name="how-to-open-project-specific-editors"></a>Postupy: Otevření editoru pro konkrétní projekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud je soubor položky, který je otevřen projektem, vnitřně svázán s konkrétním editorem pro daný projekt, projekt musí otevřít soubor pomocí editoru specifického pro projekt. Soubor nelze delegovat na mechanismus rozhraní IDE pro výběr editoru. Například namísto použití standardního editoru rastrového obrázku můžete použít tuto možnost editoru pro konkrétní projekt k určení konkrétního editoru rastrového obrázku, který rozpozná informace v souboru, který je jedinečný pro váš projekt.  
  
 Rozhraní IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodu, když zjistí, že soubor by měl být otevřen pomocí konkrétního projektu. Další informace naleznete v tématu [zobrazení souborů pomocí příkazu otevřít soubor](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Použijte následující pokyny pro implementaci `OpenItem` metody, aby projekt otevřel soubor pomocí editoru specifického pro projekt.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Implementace metody OpenItem s editorem specifickým pro projekt  
  
1. Voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metody (RDT_EditLock) určíte, zda je soubor (datový objekt dokumentu) již otevřen.  
  
    > [!NOTE]
    > Další informace o datech dokumentů a objektech zobrazení dokumentu naleznete [v dokumentu data dokumentů a zobrazení dokumentu ve vlastních editorech](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2. Pokud je soubor již otevřen, přesměrujte soubor voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metody a zadáním hodnoty IDO_ActivateIfOpen pro `grfIDO` parametr.  
  
     Pokud je soubor otevřen a dokument vlastní jiný projekt než volající projekt, zobrazí se uživateli upozornění, že otevřený Editor je z jiného projektu. Okno soubor je pak Surface.  
  
3. Pokud je váš textový buffer (objekt dat dokumentu) už otevřený a chcete k němu připojit jiné zobrazení, zodpovídáte za připojení tohoto zobrazení. Doporučený postup pro vytvoření instance zobrazení (objekt zobrazení dokumentu) z projektu je následující:  
  
    1. Zavolejte `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> službu, abyste získali ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> rozhraní.  
  
    2. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> metodu pro vytvoření instance třídy zobrazení dokumentu.  
  
4. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> metodu a určete tak objekt zobrazení dokumentu.  
  
     Tato metoda vymístí objekt zobrazení dokumentu v okně dokumentu.  
  
5. Proveďte příslušná volání <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> metod nebo.  
  
     V tomto okamžiku by mělo být zobrazení zcela inicializováno a připraveno k otevření.  
  
6. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodu pro zobrazení a otevření zobrazení.  
  
## <a name="see-also"></a>Viz také  
 [Otevírání a ukládání položek projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Postupy: otevření standardních editorů](../extensibility/how-to-open-standard-editors.md)   
 [Postupy: Otevření editorů pro otevřené dokumenty](../extensibility/how-to-open-editors-for-open-documents.md)
