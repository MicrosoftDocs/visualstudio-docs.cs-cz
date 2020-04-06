---
title: Správa držáku zámku dokumentů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9dd520f8ad5cab1f0cfee890c4bcc388c204bb1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712127"
---
# <a name="document-lock-holder-management"></a>Správa držáku zámku dokumentu

Spuštěná tabulka dokumentů (RDT) udržuje počet otevřených dokumentů a všechny úpravy zámků, které mají. Zámek úprav můžete umístit na dokument v RDT, když je programově upraven na pozadí, aniž by uživatel viděl otevřený dokument v okně dokumentu. Tato funkce je často používán návrháři, kteří upravují více souborů prostřednictvím grafického uživatelského rozhraní.

## <a name="document-lock-holder-scenarios"></a>Scénáře držitelů zámků dokumentů

### <a name="file-a-has-a-dependence-on-file-b"></a>Soubor "a" má závislost na souboru "b"

Zvažte situaci, kdy implementujete standardní editor "A" pro typ souboru "a" a každý soubor typu "a" má odkaz na (nebo závislost) soubor typu "b". Pro soubory typu "b" existuje standardní editor "B". Když editor "A" otevře soubor "a", načte odkaz na odpovídající soubor "b". Soubor "b" se nezobrazí, ale editor "A" jej může upravit. Editor "A" získá odkaz na data dokumentu souboru <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> "b" z metody a také udržuje zámek úprav na souboru "b". Po editoru "A" se provádí úprava souboru "b" můžete zmenšit <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> počet upravit zámek na souboru "b" voláním metody. Tento krok můžete vynechat, pokud jste <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodu `dwRDTLockType` zavolali s parametrem nastaveným na [_VSRDTFLAGS. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Soubor "b" je otevřen jiným editorem

V případě, že soubor "b" je již otevřen editor "B", když editor "A" se pokusí otevřít, existují dva samostatné scénáře pro zpracování:

- Pokud je soubor "b" otevřen v kompatibilním editoru, musíte mít editor "A" <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> zaregistrovat zámek pro úpravu dokumentu na souboru "b" pomocí metody. Po dokončení editoru "A" úprava souboru "b", un-registrovat zámek úprav dokumentu pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> metody.

- Pokud je soubor "b" otevřen nekompatibilním způsobem, můžete buď nechat pokus o otevření souboru "b" editorem "A" selhat, nebo můžete nechat zobrazení přidružené k editoru "A" částečně otevřít a zobrazit příslušnou chybovou zprávu. Chybová zpráva by měla dát uživateli pokyn k zavření souboru "b" v nekompatibilním editoru a následnému opětovnému otevření souboru "a" pomocí editoru "A". Můžete také implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> metodu [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] výzvu uživateli k zavření souboru "b", který je otevřen v nekompatibilním editoru. Pokud uživatel zavře soubor "b", otevření souboru "a" v editoru "A" pokračuje normálně.

## <a name="additional-document-edit-lock-considerations"></a>Další aspekty uzamčení zámku úprav dokumentu

Můžete získat různé chování, pokud editor "A" je jediný editor, který má zámek pro úpravu dokumentu na souboru "b", než byste, pokud editor "B" také obsahuje zámek pro úpravu dokumentu na souboru "b". V [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **aplikaci** je Návrhář tříd příkladem vizuálního návrháře, který neobsahuje zámek úprav v přidruženém souboru kódu. To znamená, že pokud má uživatel v návrhovém zobrazení otevřený diagram třídy a přidružený soubor kódu se otevře současně a pokud uživatel upraví soubor kódu, ale neuloží změny, změny se také ztratí v souboru diagramu třídy (.cd). Pokud **návrhář tříd má** jediný zámek úprav dokumentu v souboru kódu, uživatel není požádán o uložení změn při zavírání souboru kódu. Rozhraní IDE požádá uživatele o uložení změn až poté, co uživatel zavře **Návrhář e- třídy**. Uložené změny se projeví v obou souborech. Pokud **návrhář tříd y** editor souborů kódu držely zámky úprav dokumentu v souboru kódu, je uživatel vyzván k uložení při zavření souboru kódu nebo formuláře. V tomto okamžiku se uložené změny projeví ve formuláři i v souboru kódu. Další informace o diagramech tříd naleznete v [tématu Práce s diagramy tříd (Návrhář tříd)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Všimněte si, že pokud potřebujete umístit zámek úprav na dokument pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> non-editor, je nutné implementovat rozhraní.

Mnohokrát návrhář e-li modifikovat soubory kódu programově provede změny více než jeden soubor. V takových <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> případech metoda zpracovává ukládání jednoho nebo více dokumentů pomocí dialogového okna **Chcete uložit změny do následujících položek?**

## <a name="see-also"></a>Viz také

- [Spuštění tabulky dokumentů](../extensibility/internals/running-document-table.md)
- [Trvalost a spuštěná tabulka dokumentů](../extensibility/internals/persistence-and-the-running-document-table.md)
