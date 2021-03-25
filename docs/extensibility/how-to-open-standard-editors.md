---
title: 'Postupy: otevření standardních editorů | Microsoft Docs'
description: Naučte se implementovat metodu OpenItem pomocí standardního editoru. Rozhraní IDE určí standardní editor pro určený typ souboru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1b0de198e96ff268a0744a4a97a4a160c585af9c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069904"
---
# <a name="how-to-open-standard-editors"></a>Postupy: otevření standardních editorů
Otevřete-li standardní editor, rozhraní IDE určí standardní editor pro určený typ souboru namísto určení editoru specifického pro projekt pro daný soubor.

 K implementaci metody proveďte následující postup <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> . Tím se otevře soubor projektu ve standardním editoru.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Implementace metody OpenItem se standardním editorem

1. Voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> ( `RDT_EditLock` ) určíte, zda je soubor datového objektu dokumentu již otevřen.

2. Pokud je soubor již otevřen, přesměrujte soubor voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metody a zadáním hodnoty `IDO_ActivateIfOpen` `grfIDO` parametru.

     Pokud je soubor otevřen a dokument je vlastněn jiným projektem než voláním projektu, váš projekt obdrží upozornění, že editor, který je otevřen, je z jiného projektu. Okno soubor je pak Surface.

3. Pokud dokument není otevřen nebo není v tabulce spuštěných dokumentů, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodu ( `OSE_ChooseBestStdEditor` ) pro otevření standardního editoru souboru.

     Při volání metody provede rozhraní IDE následující úlohy:

    1. Rozhraní IDE prohledává podklíč Editors/{guidEditorType}/Extensions v registru, aby určil, který editor může soubor otevřít a má nejvyšší prioritu.

    2. Poté, co rozhraní IDE určí, který editor může soubor otevřít, rozhraní IDE volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . Implementace této metody v editoru vrátí informace, které jsou požadovány pro rozhraní IDE pro volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> a umístění nově otevřeného dokumentu.

    3. Nakonec rozhraní IDE načte dokument pomocí obvyklého rozhraní trvalosti, například <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .

    4. Pokud rozhraní IDE již zjistilo, že je hierarchie nebo položka hierarchie k dispozici, rozhraní IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> metodu projektu, aby získala ukazatel kontextu na úrovni projektu, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> který vrátí zpět pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> volání metody.

4. <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> Pokud chcete, aby Editor získal kontext z projektu, vraťte ukazatel na integrované vývojové prostředí (IDE) v případě volání rozhraní IDE na vašem projektu.

     Provádění tohoto kroku umožní projektu nabízet další služby pro Editor.

     Pokud byl objekt zobrazení dokumentu nebo zobrazení dokumentu v rámci okna úspěšně umístěn, je objekt inicializován s jeho daty voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> .

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Otevřít a uložit položky projektu](../extensibility/internals/opening-and-saving-project-items.md)
- [Postupy: otevření editorů specifických pro projekt](../extensibility/how-to-open-project-specific-editors.md)
- [Postupy: otevření editorů pro otevřené dokumenty](../extensibility/how-to-open-editors-for-open-documents.md)
- [Zobrazení souborů pomocí příkazu otevřít soubor](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
