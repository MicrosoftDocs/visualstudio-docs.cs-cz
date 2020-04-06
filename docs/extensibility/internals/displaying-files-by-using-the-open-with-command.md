---
title: Zobrazení souborů pomocí příkazu Otevřít pomocí | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708583"
---
# <a name="display-files-by-using-the-open-with-command"></a>Zobrazení souborů pomocí příkazu Otevřít pomocí
Projekt může požádat ide o zobrazení dialogového okna **Otevřít v aplikaci.** Tento požadavek vyzve uživatele k otevření souboru, který má výběr standardních editorů. Následující kroky popisují tento proces:

1. Projekt volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, určující hodnotu `OSE_UseOpenWithDialog` `OSEOpenDocEditor` parametru.

2. Na základě přípony názvu souboru dokumentu ide určuje, kteří editory uvedené v registru mohou otevřít zadaný dokument a zobrazí tyto informace v dialogovém okně **Otevřít v počítači.**

    > [!NOTE]
    > Projekty, které mají vnitřní editor, který musí být součástí dialogového okna **Otevřít s** musí zaregistrovat editor factory pro každý takový editor. Vnitřní editory fungují pouze společně s určitým typem projektu, který je <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> vynucen při implementaci metody. Rozhraní IDE má vestavěnou továrnu editoru pro základní textový editor a binární editor. Rozhraní IDE také vytvoří instanci editoru továrny jménem každé registrované přidružení souborů systému Windows. Příkladem takového souboru je aplikace Microsoft Word.

3. Jakmile uživatel vybere položku z dialogového okna **Otevřít v aplikaci,** rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> IDE pak otevře dokument voláním metody. Další informace naleznete v [tématu How to: Open standard editors](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Viz také
- [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)
- [Zobrazení souborů pomocí příkazu Otevřít soubor](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Postup: Otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)
