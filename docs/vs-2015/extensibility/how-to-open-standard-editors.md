---
title: 'Postupy: otevření standardních editorů | Dokumentace Microsoftu'
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
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc6829ba4d1267d7a17c609f973b5ee6b570e9ac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742508"
---
# <a name="how-to-open-standard-editors"></a>Postupy: otevření standardních editorů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při otevření standardní editor necháte rozhraní IDE, určení standardní editor pro určený typ souboru, místo určení editoru specifické pro projekt k souboru.  
  
 Proveďte následující postup k implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody. Otevře se soubor projektu v standardní editor.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>O implementaci metody OpenItem standardní Editor  
  
1.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) k určení, zda soubor dokumentu datový objekt je již otevřen.  
  
2.  Pokud soubor již je otevřen, resurface soubor voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodu, zadáte třeba hodnotu `IDO_ActivateIfOpen` pro `grfIDO` parametru.  
  
     Pokud je soubor otevřen a dokumentu vlastní jiný projekt než volajícího projektu, váš projekt se zobrazí upozornění, editor otevírané je z jiného projektu. Pak se zobrazí okno souboru.  
  
3.  Pokud dokument není otevřené nebo není v tabulce spuštěných dokumentů, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> – metoda (`OSE_ChooseBestStdEditor`) standardní editor pro tento soubor otevřít.  
  
     Při volání metody integrovaného vývojového prostředí provádí následující úlohy:  
  
    1.  Rozhraní IDE prohledá editorech / {guidEditorType} / rozšíření podklíč registru a určit, které editor můžete otevřít soubor a má nejvyšší prioritu, jak to udělat.  
  
    2.  Poté, co prostředí IDE určil, které editor můžete otevřít soubor, integrovaném vývojovém prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Editoru implementace této metody vrátí informace, které jsou požadovány pro integrované vývojové prostředí pro volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> a lokality nově otevřeném dokumentu.  
  
    3.  A konečně, rozhraní IDE načte dokument pomocí rozhraní obvykle trvalost <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  Pokud rozhraní IDE dříve určil, že je k dispozici na úrovni hierarchie nebo hierarchie položek, zavolá rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> metodu na projekt, abyste získali kontext projektu <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> ukazatel na předávání zpátky pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> volání metody.  
  
4.  Vrátí <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> ukazatel na rozhraní IDE při volání rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> na váš projekt, pokud chcete, aby kontextu editoru get z projektu.  
  
     Provedením tohoto kroku umožňuje projektu nabídky další služby do editoru.  
  
     Pokud zobrazení dokumentu nebo objekt zobrazení dokumentu byl úspěšně umístěn v rámci okna, objekt je inicializován s jeho daty voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Otevření a uložení položek projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Postupy: otevření editoru pro konkrétní projekt](../extensibility/how-to-open-project-specific-editors.md)   
 [Postupy: Otevření editorů pro otevřené dokumenty](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Zobrazení souborů pomocí příkazu Otevřít soubor](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

