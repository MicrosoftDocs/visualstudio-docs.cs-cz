---
title: 'Postup: Otevřít standardní editory | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f42cfa64106acc41358568f4c8f6bca2cd1141fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710791"
---
# <a name="how-to-open-standard-editors"></a>Postup: Otevření standardních editorů
Při otevření standardního editoru, nechat IDE určit standardní editor pro určený typ souboru, namísto zadání editoru specifického pro projekt pro soubor.

 Proveďte následující postup <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> pro implementaci metody. Tím se otevře soubor projektu ve standardním editoru.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Implementace metody OpenItem pomocí standardního editoru

1. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> `RDT_EditLock`( ) k určení, zda je soubor datového objektu dokumentu již otevřen.

2. Pokud je soubor již otevřen, znovu vysušte soubor voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metody a zadáním hodnoty `IDO_ActivateIfOpen` parametru. `grfIDO`

     Pokud je soubor otevřený a dokument je vlastněn jiným projektem než volající projekt, projekt obdrží upozornění, že editor, který se otevírá, je z jiného projektu. Okno souboru se pak zobrazí.

3. Pokud dokument není otevřen nebo není v běžící <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> tabulce`OSE_ChooseBestStdEditor`dokumentu, zavolejte metodu ( ) a otevřete standardní editor souboru.

     Při volání metody ide provádí následující úkoly:

    1. IDE prohledává podklíč Editors/{guidEditorType}/Extensions v registru, aby zjistil, který editor může soubor otevřít, a má pro to nejvyšší prioritu.

    2. Poté, co rozhraní IDE určí, který editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>může soubor otevřít, volání rozhraní IDE . Editor implementace této metody vrátí informace, které je požadováno <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> pro rozhraní IDE volat a web nově otevřený dokument.

    3. Nakonec rozhraní IDE načte dokument pomocí obvyklého rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>perzistence, například .

    4. Pokud rozhraní IDE dříve zjistilo, že je k dispozici <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> položka hierarchie nebo hierarchie, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> volání metody IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> v projektu získá ukazatel kontextu na úrovni projektu, který se vrátí zpět s voláním metody.

4. Vrátí <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> ukazatel na rozhraní IDE při <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> volání rozhraní IDE na projektu, pokud chcete, aby editor získat kontext z vašeho projektu.

     Provedení tohoto kroku umožňuje projektu nabídnout další služby editoru.

     Pokud byl objekt zobrazení dokumentu nebo objekt zobrazení dokumentu úspěšně umístěn v rámečku okna, je objekt inicializován s daty voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Otevření a uložení položek projektu](../extensibility/internals/opening-and-saving-project-items.md)
- [Postup: Otevření editorů specifických pro projekt](../extensibility/how-to-open-project-specific-editors.md)
- [Postup: Otevření editorů pro otevřené dokumenty](../extensibility/how-to-open-editors-for-open-documents.md)
- [Zobrazení souborů pomocí příkazu Otevřít soubor](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
