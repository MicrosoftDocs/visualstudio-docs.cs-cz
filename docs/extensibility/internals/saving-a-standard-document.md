---
title: Ukládání standardního dokumentu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df93813d339a45689845b82fe4f5a185301b6c74
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724088"
---
# <a name="saving-a-standard-document"></a>Uložení standardního dokumentu
Prostředí zpracuje příkazy Uložit, Uložit jako a uložit všechny. Když uživatel vybere příkaz **Uložit**, **Uložit jako**nebo **Uložit vše** v nabídce **soubor** nebo zavře řešení, výsledkem bude **uložení všech**, dojde k následujícímu procesu.

 ![Standardní editor](../../extensibility/internals/media/public.gif "Public") Uložit, Uložit jako a uložit všechny zpracování příkazů pro standardní editor

 Tento postup je podrobně popsán v následujících krocích:

1. Když jsou vybrané příkazy **Uložit** a **Uložit jako** , prostředí používá službu <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> k určení aktivního okna dokumentu, takže by se měly položky ukládat. Po zjištění aktivního okna dokumentu prostředí nalezne ukazatel hierarchie a identifikátor položky (itemID) pro dokument v tabulce spuštěných dokumentů. Další informace najdete v tématu [Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md).

    Když je vybraný příkaz **Uložit vše** , prostředí používá informace v tabulce spuštěných dokumentů ke kompilaci seznamu všech položek, které se mají uložit.

2. Když řešení přijme <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> volání, prochází sadu vybraných položek (to znamená vícenásobný výběr vystavený službou <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>).

3. U každé položky ve výběru používá řešení ukazatel hierarchie pro volání metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> k určení, zda by mělo být povoleno použití příkazu nabídky **Uložit** . Pokud je jedna nebo více položek nečistých, je povolen příkaz **Uložit** . Pokud hierarchie používá standardní editor, pak hierarchie deleguje dotaz na stav undirty do editoru voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>.

4. U každé vybrané položky, která je nečistá, používá řešení ukazatel hierarchie pro volání metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> v příslušných hierarchiích.

    V hierarchii se běžně používá standardní editor pro úpravy dokumentu. V tomto případě by měl datový objekt dokumentu pro tento editor podporovat rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>. Po přijetí volání metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> by měl projekt informovat editor, že se dokument ukládá, voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> na objektu data dokumentu. Editor umožňuje prostředí zpracovat dialogové okno **Uložit jako** voláním `Query Service` pro rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>. Tím se vrátí ukazatel na rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>. Editor musí potom zavolat metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> a předat ukazatel do implementace <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> editoru pomocí parametru `pPersistFile`. Prostředí pak provede operaci uložit a poskytne dialogové okno **Uložit jako** pro Editor. Prostředí pak zavolá zpět do editoru pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.

5. Pokud se uživatel pokouší uložit dokument bez názvu (tj. dříve neuložený dokument), pak se skutečně provede příkaz Uložit jako.

6. V případě příkazu Uložit jako prostředí se zobrazí dialogové okno Uložit jako s výzvou uživatele k zadání názvu souboru.

    Pokud se název souboru změnil, pak je zodpovědná za aktualizaci informací v mezipaměti rámce dokumentu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument).

   Pokud příkaz **Uložit jako** přesune umístění dokumentu a hierarchie je citlivá na umístění dokumentu, pak je hierarchie zodpovědná za předání vlastnictví otevřeného okna dokumentu do jiné hierarchie. K tomu dochází například v případě, že projekt sleduje, zda je soubor interním nebo externím souborem (soubor s různými soubory) ve vztahu k projektu. Chcete-li změnit vlastnictví souboru na projekt různé soubory, použijte následující postup.

## <a name="changing-file-ownership"></a>Změna vlastnictví souboru

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Změna vlastnictví souboru na projekt různé soubory

1. Služba dotazů pro rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>

     Vrátí se ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>.

2. Chcete-li přenést dokument do nové hierarchie, zavolejte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`). Hierarchie provádějící příkaz Uložit jako volá tuto metodu.

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)