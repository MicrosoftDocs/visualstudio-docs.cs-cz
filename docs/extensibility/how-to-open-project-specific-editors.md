---
title: 'Postup: Otevření editorů specifických pro projekt | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cb6e360a38d64de4976f83b0167d47dc03fbc87
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710845"
---
# <a name="how-to-open-project-specific-editors"></a>Postup: Otevření editorů specifických pro projekt
Pokud je soubor položky, který otevírá projekt, vnitřně vázán na konkrétní editor pro daný projekt, musí projekt otevřít soubor pomocí editoru specifického pro projekt. Soubor nelze delegovat na mechanismus ide pro výběr editoru. Například namísto použití standardního bitmapového editoru můžete pomocí této možnosti editoru specifického pro projekt určit konkrétní bitmapový editor, který rozpozná informace v souboru, který je jedinečný pro váš projekt.

 IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodu, když určuje, že soubor by měl být otevřen určitým projektem. Další informace naleznete v [tématu Zobrazení souborů pomocí příkazu Otevřít soubor](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Pomocí následujících pokynů `OpenItem` implementujte metodu, aby váš projekt otevřel soubor pomocí editoru specifického pro projekt.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Implementace metody OpenItem pomocí editoru specifického pro projekt

1. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metody`RDT_EditLock`( ) k určení, zda je soubor (datový objekt dokumentu) již otevřen.

    > [!NOTE]
    > Další informace o datech dokumentu a objektech zobrazení dokumentu naleznete [v tématu Data dokumentu a zobrazení dokumentů ve vlastních editorech](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Pokud je soubor již otevřen, znovu vysušte soubor <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> voláním `grfIDO` metody a zadáním hodnoty IDO_ActivateIfOpen parametru.

     Pokud je soubor otevřený a dokument je vlastněn jiným projektem než volajícím projektem, zobrazí se uživateli upozornění, že otevřený editor pochází z jiného projektu. Okno souboru se pak zobrazí.

3. Pokud je textová vyrovnávací paměť (datový objekt dokumentu) již otevřena a chcete k ní připojit jiné zobrazení, jste zodpovědní za připojení tohoto zobrazení. Doporučený přístup k vytvoření instance zobrazení (objekt zobrazení dokumentu) z projektu je následující:

    1. Volání `QueryService` služby <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> získat ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> rozhraní.

    2. Volání <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> metody k vytvoření instance třídy zobrazení dokumentu.

4. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> metody a určení objektu zobrazení dokumentu.

     Tato metoda navštíve objekt zobrazení dokumentu do okna dokumentu.

5. Proveďte příslušná volání <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> buď <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> nebo metody.

     V tomto okamžiku by měl být pohled plně inicializován a připraven k otevření.

6. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metody pro zobrazení a otevření zobrazení.

## <a name="see-also"></a>Viz také
- [Otevřít a uložit položky projektu](../extensibility/internals/opening-and-saving-project-items.md)
- [Postup: Otevření standardních editorů](../extensibility/how-to-open-standard-editors.md)
- [Postup: Otevření editorů pro otevřené dokumenty](../extensibility/how-to-open-editors-for-open-documents.md)
