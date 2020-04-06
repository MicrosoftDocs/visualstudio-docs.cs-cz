---
title: Uložení vlastního dokumentu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705618"
---
# <a name="saving-a-custom-document"></a>Uložení vlastního dokumentu
Prostředí zpracovává příkazy **Uložit**, **Uložit jako**a **Uložit všechny.** Když uživatel klepne na tlačítko **Uložit**, **Uložit jako** **nebo Uložit vše** v **nabídce Soubor** nebo zavře řešení, což vede k uložení vše, dojde k následujícímu procesu.

 ![Uložení editoru zákazníků](../../extensibility/internals/media/private.gif "Private") Uložit, uložit jako a uložit vše pro vlastní editor

 Tento proces je podrobně popsán v následujících krocích:

1. U příkazů **Uložit** a **Uložit jako** prostředí <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> používá službu k určení okna aktivního dokumentu a tedy k uložení položek. Jakmile je aktivní okno dokumentu známo, prostředí najde ukazatel hierarchie a identifikátor položky (itemID) pro dokument v běžící tabulce dokumentu. Další informace naleznete v [tématu Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md).

     Pro příkaz Uložit vše používá prostředí informace v tabulce spuštěného dokumentu ke kompilaci seznamu všech položek, které chcete uložit.

2. Když řešení přijme <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> volání, itetuje prostřednictvím sady vybraných položek (to znamená <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> více výběrů vystavených službou).

3. U každé položky ve výběru řešení používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> ukazatel hierarchie k volání metody k určení, zda má být povolen příkaz Uložit nabídku. Pokud je jedna nebo více položek znečištěná, je povolen příkaz Uložit. Pokud hierarchie používá standardní editor, pak hierarchie deleguje dotazování na dirty stav editoru voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metody.

4. U každé vybrané položky, která je znečištěná, řešení používá ukazatel hierarchie k volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody v příslušných hierarchiích.

     V případě vlastního editoru je komunikace mezi datovým objektem dokumentu a projektem soukromá. Proto všechny zvláštní trvalost obavy jsou zpracovány mezi těmito dvěma objekty.

    > [!NOTE]
    > Pokud implementujete vlastní trvalost, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> nezapomeňte volat metodu ušetřit čas. Tato metoda zkontroluje, zda je bezpečné uložit soubor (například soubor není jen pro čtení).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)
