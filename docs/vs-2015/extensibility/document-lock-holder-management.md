---
title: Správa zámku vlastník dokumentu | Dokumentace Microsoftu
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
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8eaeb8529f570db112bf43813fe20339f3bca7c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786298"
---
# <a name="document-lock-holder-management"></a>Správa zámku dokumentu ze strany vlastníka
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spuštění dokumentu tabulky (rámcový) udržuje počet otevřených dokumentů a zámky jakékoli úpravy, které mají. Zámek upravit můžete umístit na dokumentu rámcový při programově úpravách na pozadí bez uživatele zobrazuje dokument otevřít v okně dokumentu. Tato funkce se často používá v návrháři, které mění více souborů přes grafické uživatelské rozhraní.  
  
## <a name="document-lock-holder-scenarios"></a>Scénáře vlastník zámku dokumentu  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Soubor "a" závislost na soubor má "b"  
 Představte si situaci, kdy implementovat standardní editor "A" pro typ souboru "a" a každý soubor typu "a" obsahuje odkaz na (nebo závislost na) soubor typu "b". Standardní editor "B" existuje pro soubory typu "b". Po otevření editoru "A" file "a" it načte odkaz na odpovídající soubor "b". Soubor "b", se nezobrazí, ale editoru "A" ho upravit. Editor "A" získá odkaz na data dokumentu souboru "b" z <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metoda a udržuje také upravit lock souboru "b". Po dokončení editoru "A" Úprava souborů "b" můžete snížit úpravy zámku Spolehněte se na soubor "b" voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metody. Tento krok můžete vynechat, pokud má volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metody s parametrem `dwRDTLockType` nastavena na <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Otevření souboru "b" podle jiný Editor  
 V případě, že soubor "b" je již otevřen v editoru "B" editoru "A" se pokusí otevřít, existují dva samostatné scénáře ke zpracování:  
  
-   Pokud není otevřený v editoru kompatibilní soubor "b", musíte mít editoru "A" registraci souboru "b" pomocí úpravy zámku dokumentu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metody. Po dokončení změny souboru "b" editoru "A" upravit zrušení registrace dokumentu pomocí zámku <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> metody.  
  
-   Pokud není otevřený v nekompatibilním způsob soubor "b", můžete buď nechat pokus o otevření souboru "b" editorem "A" selhání, nebo můžete nechat zobrazit přidružené k editoru "A" částečně otevřít a zobrazit příslušnou chybovou zprávu. Chybová zpráva by měla pokyn uživateli, aby v nekompatibilním editoru. Zavřete soubor "b" a pak znovu otevřít soubor "a" pomocí editoru "A". Můžete také implementovat [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> uživatele zavřete soubor "b", který je otevřený v nekompatibilním editoru. Pokud uživatel nezavře soubor "b", otevírání souboru "a" v editoru "A" pokračuje normálním způsobem.  
  
## <a name="additional-document-edit-lock-considerations"></a>Další dokument upravit zámek aspekty  
 Chcete získat různé chování editoru "A" je pouze editor, který má dokument upravit zámek na souboru "b", než kdybyste editoru "B" také obsahuje dokument upravit zámek na souboru "b". V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **návrhář tříd** je příkladem vizuálního návrháře, který neobsahuje upravit zámek na souboru přidružený kód. To znamená pokud má uživatel v návrhovém zobrazení otevřete diagram třídy a přidružen soubor kódu otevřete současně, a uživatel upraví soubor kódu, ale nedojde k uložení změn, změny jsou rovněž ztraceny soubor diagramu tříd (.cd). Pokud **návrhář tříd** má jediný dokument upravit zámek na soubor kódu, uživatel se vyzve k uložit změny při zavírání souboru kódu. Rozhraní IDE uživateli výzvu k uložení změn pouze poté, co uživatel zavře **návrhář tříd**. Uložené změny se projeví v obou souborech. Pokud **návrhář tříd** a editor souborů kódu zámky úpravy dokumentu uložené v souboru s kódem, pak bude uživatel vyzván k uložení při zavírání souboru kódu nebo formuláře. V tomto okamžiku uložené změny se projeví ve formuláři a soubor kódu. Další informace o diagramech tříd viz [práce s diagramy tříd (návrhář tříd)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Všimněte si, že pokud je potřeba zamknout úpravy dokumentu mimo editor, je nutné implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní.  
  
 V mnoha případech uživatelského rozhraní návrháře, který upraví soubory kódu prostřednictvím kódu programu provede změny více než jeden soubor. V takových případech <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> obsluhovala ukládání jeden nebo více dokumentů prostřednictvím **chcete uložit změny následujících položek?** dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 [Spuštění tabulky dokumentů](../extensibility/internals/running-document-table.md)   
 [Trvalost a spuštěná tabulka dokumentů](../extensibility/internals/persistence-and-the-running-document-table.md)

