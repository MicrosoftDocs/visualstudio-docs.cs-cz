---
title: Uložení standardního dokumentu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8d50a9e62e69f925564717020a51f88620f5f3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705552"
---
# <a name="saving-a-standard-document"></a>Uložení standardního dokumentu
Prostředí zpracovává příkazy Uložit, Uložit jako a Uložit všechny. Když uživatel vybere **možnost Uložit**, Uložit **jako**nebo **Uložit vše** z nabídky **Soubor** nebo zavře řešení, což vede k uložení **uložit vše**, dojde k následujícímu procesu.

 ![Standardní editor](../../extensibility/internals/media/public.gif "Public") Uložit, uložit jako a uložit vše pro standardní editor

 Tento proces je podrobně popsán v následujících krocích:

1. Když jsou vybrány příkazy **Uložit** a Uložit <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> **jako,** prostředí používá službu k určení aktivního okna dokumentu a tedy jaké položky by měly být uloženy. Jakmile je aktivní okno dokumentu známo, prostředí najde ukazatel hierarchie a identifikátor položky (itemID) pro dokument v běžící tabulce dokumentu. Další informace naleznete v [tématu Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md).

    Když je vybrán příkaz **Uložit vše,** prostředí použije informace v průběžné tabulce dokumentů ke kompilaci seznamu všech položek, které chcete uložit.

2. Když řešení přijme <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> volání, itetuje prostřednictvím sady vybraných položek (to znamená <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> více výběrů vystavených službou).

3. U každé položky ve výběru řešení používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> ukazatel hierarchie k volání metody k určení, zda má být povolen příkaz **Uložit** nabídku. Pokud je jedna nebo více položek znečištěná, je povolen příkaz **Uložit.** Pokud hierarchie používá standardní editor, pak hierarchie deleguje dotazování na dirty stav editoru voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metody.

4. U každé vybrané položky, která je znečištěná, řešení používá ukazatel hierarchie k volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody v příslušných hierarchiích.

    Je běžné, že hierarchie používá standardní editor k úpravám dokumentu. V takovém případě by měl <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> datový objekt dokumentu pro tento editor podporovat rozhraní. Po přijetí <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> volání metody by měl projekt informovat editor, že <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> dokument je uložen voláním metody na datovém objektu dokumentu. Editor může povolit prostředí zpracovat dialogové okno `Query Service` Uložit <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> **jako** voláním rozhraní. To vrátí ukazatel <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> na rozhraní. Editor pak musí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> volat metodu, předání ukazatele <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> na implementaci editoru pomocí parametru. `pPersistFile` Prostředí pak provede operaci Uložit a poskytne dialogové okno **Uložit jako** pro editor. Prostředí pak volá zpět do <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>editoru s .

5. Pokud se uživatel pokouší uložit dokument bez názvu (tj. dříve neuložený dokument), je skutečně proveden příkaz Uložit jako.

6. U příkazu Uložit jako se v prostředí zobrazí dialogové okno Uložit jako s výzvou uživateli k pojmenování souboru.

    Pokud se změnil název souboru, je hierarchie zodpovědná za aktualizaci informací <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>o souboru v mezipaměti rámce dokumentu voláním (VSFPROPID_MkDocument).

   Pokud příkaz **Uložit jako** přesune umístění dokumentu a hierarchie je citlivá na umístění dokumentu, je hierarchie zodpovědná za předání vlastnictví otevřeného okna dokumentu do jiné hierarchie. Například k tomu dochází, pokud projekt sleduje, zda je soubor interní nebo externí soubor (různé soubor) ve vztahu k projektu. Pomocí následujícího postupu můžete změnit vlastnictví souboru do projektu Různé soubory.

## <a name="changing-file-ownership"></a>Změna vlastnictví souboru

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Změna vlastnictví souboru v projektu Různé soubory

1. Služba dotazů <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> pro rozhraní.

     Je vrácen <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> ukazatel na.

2. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew` `punkWindowFrame`, ) metoda k přenosu dokumentu do nové hierarchie. Hierarchie provádějící příkaz Uložit jako volá tuto metodu.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)
