---
title: Správa držitele zámku dokumentu | Microsoft Docs
description: Naučte se, jak umístit zámek pro úpravy dokumentu v tabulce spuštěných dokumentů, aniž by uživatel viděl otevřený dokument v okně dokumentu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c15696d81be92f0549069bad354e65356f7b2e7c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995899"
---
# <a name="document-lock-holder-management"></a>Správa držitele zámku dokumentu

Spuštěná tabulka dokumentů (RDT) udržuje počet otevřených dokumentů a všechny jejich zámky. Zámek úprav můžete umístit na dokument RDT, když se programově upraví na pozadí, aniž by uživatel viděl otevřený dokument v okně dokumentu. Tato funkce je často používána návrháři, kteří mění více souborů prostřednictvím grafického uživatelského rozhraní.

## <a name="document-lock-holder-scenarios"></a>Scénáře držitele zámku pro dokumenty

### <a name="file-a-has-a-dependence-on-file-b"></a>Soubor "a" má závislost na souboru "b".

Vezměte v úvahu situaci, kdy implementujete standardní editor "A" pro soubor typu "a" a každý soubor typu a má odkaz na (nebo závislosti na) souboru typu "b". Pro soubory typu b existuje standardní editor "B". Když editor "A" otevře soubor "a", načte odkaz na odpovídající soubor "b". Soubor "b" se nezobrazuje, ale editor "A" ho může upravit. Editor "A" Získá odkaz na data dokumentu souboru "b" z této <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metody a zároveň udržuje zámek úprav souboru "b". Poté, co Editor "A" dokončíte úpravou souboru "b", můžete snížit počet zámků pro úpravy v souboru "b" voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metody. Tento krok můžete vynechat, pokud jste volali <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodu s parametrem `dwRDTLockType` nastaveným na [_VSRDTFLAGS. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Soubor "b" je otevřen jiným editorem

V případě, že soubor "b" je již otevřen editorem "B", když se ho pokusí otevřít Editor "A", existují dva samostatné scénáře, které lze zpracovat:

- Pokud je soubor "b" otevřený v kompatibilním editoru, je nutné, abyste měli Editor "A", který umožňuje v souboru "b" zámek úprav dokumentu pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metody. Poté, co Editor "A" dokončíte úpravou souboru "b", zrušte registraci zámku úprav dokumentu pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> metody.

- Pokud je soubor "b" otevřený nekompatibilním způsobem, můžete buď nechat pokusit se otevřít soubor "b" editorem "A", nebo můžete nechat zobrazení spojené s editorem "A" částečně otevřené a zobrazit příslušnou chybovou zprávu. Chybová zpráva by měla uživateli pokyn, aby zavřel soubor "b" v nekompatibilním editoru a pak znovu otevřel soubor "a" pomocí editoru "A". Můžete také implementovat metodu, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] která <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> vyzve uživatele k zavření souboru "b", který je otevřen v nekompatibilním editoru. Pokud uživatel zavře soubor "b", otevření souboru "a" v editoru "A" bude normálně pokračovat.

## <a name="additional-document-edit-lock-considerations"></a>Další požadavky na úpravu zámku dokumentu

Pokud je editor "A" jediným editorem, který má zámek pro úpravy dokumentu v souboru "b", nemusíte mít k dispozici jiné chování jako v případě, že editor "B" obsahuje také zámek úprav dokumentu v souboru "b". V [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je **Návrhář tříd** příkladem vizuálního návrháře, který neobsahuje zámek úprav pro přidružený soubor kódu. To znamená, že pokud má uživatel otevřený diagram tříd v zobrazení Návrh a přidružený soubor kódu současně otevřený a pokud uživatel změní soubor kódu, ale neuloží změny, změny se také ztratí do souboru diagramu tříd (. CD). Pokud má **Návrhář tříd** jediný zámek úprav dokumentu v souboru kódu, uživateli není při zavírání souboru kódu požádán o uložení změn. Rozhraní IDE vyzve uživatele k uložení změn pouze poté, co uživatel zavře **Návrhář tříd**. Uložené změny se projeví v obou souborech. Pokud **Návrhář tříd** i Editor souboru kódu uchovávají úpravy zámků dokumentu v souboru kódu, bude uživatel vyzván k uložení při zavření souboru kódu nebo formuláře. V tomto okamžiku se uložené změny projeví ve formuláři i v souboru kódu. Další informace o diagramech tříd naleznete v tématu [práce s diagramy tříd (návrhář tříd)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Všimněte si, že pokud potřebujete umístit zámek pro úpravy dokumentu pro Editor, který není editor, je nutné implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní.

Mnohokrát je Návrhář uživatelského rozhraní, který upravuje soubory kódu programově, provádí změny ve více než jednom souboru. V takových případech <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> metoda zpracovává uložení jednoho nebo více dokumentů pomocí do dialogového okna **přejete si uložit změny do následujících položek?** .

## <a name="see-also"></a>Viz také

- [Běžící tabulka dokumentů](../extensibility/internals/running-document-table.md)
- [Trvalá a spuštěná tabulka dokumentů](../extensibility/internals/persistence-and-the-running-document-table.md)
