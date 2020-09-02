---
title: Ukládání standardního dokumentu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5040070287db6486fa62c9010fe023be31b04cbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198091"
---
# <a name="saving-a-standard-document"></a>Uložení standardního dokumentu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Prostředí zpracuje příkazy Uložit, Uložit jako a uložit všechny. Když uživatel vybere příkaz **Uložit**, **Uložit jako**nebo **Uložit vše** v nabídce **soubor** nebo zavře řešení, výsledkem bude **uložení všech**, dojde k následujícímu procesu.  
  
 ![Standardní editor](../../extensibility/internals/media/public.gif "Veřejná")  
Uložit, Uložit jako a uložit všechny zpracování příkazů pro standardní editor  
  
 Tento postup je podrobně popsán v následujících krocích:  
  
1. Když jsou vybrané příkazy **Uložit** a **Uložit jako** , prostředí <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> službu používá k určení aktivního okna dokumentu, takže by se měly položky ukládat. Po zjištění aktivního okna dokumentu prostředí nalezne ukazatel hierarchie a identifikátor položky (itemID) pro dokument v tabulce spuštěných dokumentů. Další informace najdete v tématu [Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md).  
  
    Když je vybraný příkaz **Uložit vše** , prostředí používá informace v tabulce spuštěných dokumentů ke kompilaci seznamu všech položek, které se mají uložit.  
  
2. Když řešení přijme <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> volání, provede iteraci sadou vybraných položek (tj. vícenásobný výběr vystavený službou <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> ).  
  
3. U každé položky ve výběru používá řešení ukazatel hierarchie pro volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metody k určení, zda by měl být povolen příkaz nabídky **Uložit** . Pokud je jedna nebo více položek nečistých, je povolen příkaz **Uložit** . Pokud hierarchie používá standardní editor, pak hierarchie deleguje dotaz na stav undirty do editoru voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metody.  
  
4. Pro každou vybranou položku, která je nečistá, používá řešení ukazatel hierarchie pro volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody v příslušných hierarchiích.  
  
    V hierarchii se běžně používá standardní editor pro úpravy dokumentu. V tomto případě by měl objekt data dokumentu pro tento editor podporovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> rozhraní. Po přijetí <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> volání metody by měl projekt informovat editor, že dokument je uložen, voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> metody v objektu data dokumentu. Editor umožňuje prostředí zpracovat dialogové okno **Uložit jako** voláním `Query Service` <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> rozhraní. Tím se vrátí ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní. Editor musí potom zavolat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> metodu a předat ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> implementaci editoru prostřednictvím `pPersistFile` parametru. Prostředí pak provede operaci uložit a poskytne dialogové okno **Uložit jako** pro Editor. Prostředí pak zavolá zpět do editoru pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .  
  
5. Pokud se uživatel pokouší uložit dokument bez názvu (tj. dříve neuložený dokument), pak se skutečně provede příkaz Uložit jako.  
  
6. V případě příkazu Uložit jako prostředí se zobrazí dialogové okno Uložit jako s výzvou uživatele k zadání názvu souboru.  
  
    Pokud se název souboru změnil, pak je hierarchie zodpovědná za aktualizaci informací uložených v mezipaměti rámce dokumentu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument).  
  
   Pokud příkaz **Uložit jako** přesune umístění dokumentu a hierarchie je citlivá na umístění dokumentu, pak je hierarchie zodpovědná za předání vlastnictví otevřeného okna dokumentu do jiné hierarchie. K tomu dochází například v případě, že projekt sleduje, zda je soubor interním nebo externím souborem (soubor s různými soubory) ve vztahu k projektu. Chcete-li změnit vlastnictví souboru na projekt různé soubory, použijte následující postup.  
  
## <a name="changing-file-ownership"></a>Změna vlastnictví souboru  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Změna vlastnictví souboru na projekt různé soubory  
  
1. Služba dotazů pro <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> rozhraní  
  
     Ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> je vrácen.  
  
2. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> metodu ( `pszMkDocumentNew` , `punkWindowFrame` ) pro přenos dokumentu do nové hierarchie. Hierarchie provádějící příkaz Uložit jako volá tuto metodu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)
