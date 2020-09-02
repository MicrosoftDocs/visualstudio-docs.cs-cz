---
title: Ukládání vlastního dokumentu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705618"
---
# <a name="saving-a-custom-document"></a>Uložení vlastního dokumentu
Prostředí zpracuje příkazy **Uložit**, **Uložit jako**a **Uložit všechny** . Když uživatel klikne na **Uložit**, **Uložit jako** **nebo Uložit vše** v nabídce **soubor** nebo zavře řešení a výsledkem je uložení všech, dojde k následujícímu procesu.

 ![Editor zákazníka – uložení](../../extensibility/internals/media/private.gif "Soukromá") Ukládat, ukládat jako a ukládat všechny zpracování příkazů pro vlastní editor

 Tento postup je podrobně popsán v následujících krocích:

1. V příkazech **Uložit** a **Uložit jako** prostředí <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> služba používá službu k určení aktivního okna dokumentu, takže by se měly položky ukládat. Po zjištění aktivního okna dokumentu prostředí nalezne ukazatel hierarchie a identifikátor položky (itemID) pro dokument v tabulce spuštěných dokumentů. Další informace najdete v tématu [Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md).

     V případě příkazu Uložit vše používá prostředí informace v tabulce spuštěných dokumentů ke kompilaci seznamu všech položek, které chcete uložit.

2. Když řešení přijme <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> volání, provede iteraci sadou vybraných položek (tj. vícenásobný výběr vystavený službou <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> ).

3. U každé položky ve výběru používá řešení ukazatel hierarchie pro volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metody k určení, zda by měl být povolen příkaz nabídky Uložit. Pokud je jedna nebo více položek nečistých, je povolen příkaz Uložit. Pokud hierarchie používá standardní editor, pak hierarchie deleguje dotaz na stav undirty do editoru voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metody.

4. Pro každou vybranou položku, která je nečistá, používá řešení ukazatel hierarchie pro volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody v příslušných hierarchiích.

     V případě vlastního editoru je komunikace mezi objektem dat dokumentu a projektem soukromá. Proto se mezi těmito dvěma objekty budou zpracovávat jakékoli zvláštní obavy o trvalosti.

    > [!NOTE]
    > Pokud implementujete vlastní trvalost, nezapomeňte zavolat <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> metodu a ušetřit tak čas. Tato metoda kontroluje, zda je bezpečné soubor uložit (například soubor není jen pro čtení).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)
