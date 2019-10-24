---
title: Ukládání vlastního dokumentu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf67335b6a12b966eb148b3f8dcaf16339e2a29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724078"
---
# <a name="saving-a-custom-document"></a>Uložení vlastního dokumentu
Prostředí zpracuje příkazy **Uložit**, **Uložit jako**a **Uložit všechny** . Když uživatel klikne na **Uložit**, **Uložit jako** **nebo Uložit vše** v nabídce **soubor** nebo zavře řešení a výsledkem je uložení všech, dojde k následujícímu procesu.

 ![Editor zákazníka – uložení](../../extensibility/internals/media/private.gif "Soukromé") Ukládat, ukládat jako a ukládat všechny zpracování příkazů pro vlastní editor

 Tento postup je podrobně popsán v následujících krocích:

1. V příkazech **Uložit** a **Uložit jako** prostředí používá služba <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> k určení aktivního okna dokumentu a takže by se měly položky ukládat. Po zjištění aktivního okna dokumentu prostředí nalezne ukazatel hierarchie a identifikátor položky (itemID) pro dokument v tabulce spuštěných dokumentů. Další informace najdete v tématu [Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md).

     V případě příkazu Uložit vše používá prostředí informace v tabulce spuštěných dokumentů ke kompilaci seznamu všech položek, které chcete uložit.

2. Když řešení přijme <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> volání, prochází sadu vybraných položek (to znamená vícenásobný výběr vystavený službou <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>).

3. U každé položky ve výběru používá řešení ukazatel hierarchie pro volání metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> k určení, zda by mělo být povoleno použití příkazu nabídky Uložit. Pokud je jedna nebo více položek nečistých, je povolen příkaz Uložit. Pokud hierarchie používá standardní editor, pak hierarchie deleguje dotaz na stav undirty do editoru voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>.

4. U každé vybrané položky, která je nečistá, používá řešení ukazatel hierarchie pro volání metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> v příslušných hierarchiích.

     V případě vlastního editoru je komunikace mezi objektem dat dokumentu a projektem soukromá. Proto se mezi těmito dvěma objekty budou zpracovávat jakékoli zvláštní obavy o trvalosti.

    > [!NOTE]
    > Pokud implementujete vlastní trvalost, ujistěte se, že zavoláte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>, abyste ušetřili čas. Tato metoda kontroluje, zda je bezpečné soubor uložit (například soubor není jen pro čtení).

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)