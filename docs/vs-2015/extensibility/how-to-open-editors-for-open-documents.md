---
title: 'Postupy: otevření editorů pro otevřené dokumenty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6e565e026ca49825a7b00a82e4e5c62a2f6c3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204138"
---
# <a name="how-to-open-editors-for-open-documents"></a>Postupy: Otevření editorů pro otevřené dokumenty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Před otevřením okna dokumentu musí projekt nejprve určit, zda je soubor již otevřen v okně dokumentu pro jiný Editor. Soubor může být buď otevřený v editoru specifickém pro projekt, nebo v jednom ze standardních editorů registrovaných pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="opening-a-project-specific-editor"></a>Otevření editoru specifického pro projekt  
 Následující postup slouží k otevření editoru specifického pro projekt pro soubor, který je již otevřen.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Otevření editoru specifického pro projekt pro otevřený soubor  
  
1. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodu.  
  
    Toto volání vrátí ukazatele na hierarchii dokumentu, položku hierarchie a rámec okna, pokud je to vhodné.  
  
2. Pokud je dokument otevřen, musí projekt ověřit, zda pouze existuje datový objekt dokumentu nebo zda je k dispozici také objekt zobrazení dokumentu.  
  
   - Pokud objekt zobrazení dokumentu existuje a toto zobrazení je pro jinou hierarchii nebo položku hierarchie, používá projekt ukazatel na rámec okna zobrazení k přepovrchování stávajícího okna.  
  
   - Pokud objekt zobrazení dokumentu existuje a toto zobrazení je pro stejnou hierarchii a položku hierarchie, může projekt otevřít druhé zobrazení, pokud se může připojit k objektu dat dokumentu podkladu. V opačném případě by měl projekt použít ukazatel na rámec okna zobrazení k přepovrchování stávajícího okna.  
  
   - Pokud existuje pouze datový objekt dokumentu, projekt by měl určit, zda může použít objekt data dokumentu pro jeho zobrazení. Pokud je datový objekt dokumentu kompatibilní, proveďte kroky popsané v tématu [otevření editoru specifického pro projekt](../extensibility/how-to-open-project-specific-editors.md).  
  
     Pokud datový objekt dokumentu není kompatibilní, zobrazí se uživateli chyba, která indikuje, že se soubor právě používá. Tato chyba by měla být zobrazena pouze v přechodných případech, například při kompilování souboru v době, kdy se uživatel pokouší otevřít soubor pomocí jiného editoru než [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] základního textového editoru. Základní textový editor může sdílet datový objekt dokumentu s kompilátorem.  
  
3. Pokud dokument není otevřen, protože neexistuje objekt datového objektu dokumentu nebo zobrazení dokumentu, proveďte kroky v části [otevření editoru specifického pro projekt](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Otevření standardního editoru  
 Pomocí následujícího postupu otevřete standardní editor pro soubor, který je již otevřen.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Otevření standardního editoru pro otevřený soubor  
  
1. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
     Tato metoda nejprve ověří, že dokument ještě není otevřený voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> . Je-li již dokument otevřen, je jeho okno editoru znovu nasurfované.  
  
2. Pokud dokument není otevřený, proveďte kroky v tématu [Postupy: otevření standardních editorů](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Viz také  
 [Otevírání a ukládání položek projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Postupy: otevření editorů specifických pro projekt](../extensibility/how-to-open-project-specific-editors.md)   
 [Postupy: Otevření standardních editorů](../extensibility/how-to-open-standard-editors.md)
