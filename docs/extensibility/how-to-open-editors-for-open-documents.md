---
title: 'Postup: Otevřít editory pro otevřené dokumenty | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d0986573ac0d53427f6490370be2bfa1c4cbe7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710912"
---
# <a name="how-to-open-editors-for-open-documents"></a>Postup: Otevření editorů pro otevřené dokumenty
Před otevřením okna dokumentu projektu musí nejprve určit, zda je soubor již otevřen v okně dokumentu pro jiný editor. Soubor může být buď otevřen v editoru specifickém pro projekt, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nebo v jednom ze standardních editorů registrovaných u aplikace .

## <a name="open-a-project-specific-editor"></a>Otevření editoru specifického pro projekt
 Pomocí následujícího postupu otevřete editor specifický pro projekt pro soubor, který je již otevřen.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Otevření editoru specifického pro projekt pro otevřený soubor

1. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metody.

    Toto volání vrátí ukazatele hierarchie dokumentu, položky hierarchie a rámečku okna, pokud je to vhodné.

2. Pokud je dokument otevřený, musí projekt zkontrolovat, zda existuje pouze datový objekt dokumentu nebo zda je k dispozici také objekt zobrazení dokumentu.

   - Pokud objekt zobrazení dokumentu existuje a toto zobrazení je pro jinou hierarchii nebo položku hierarchie, projekt použije ukazatel na rámeček okna zobrazení k opětovnému zobrazení existujícího okna.

   - Pokud objekt zobrazení dokumentu existuje a toto zobrazení je pro stejnou hierarchii a položku hierarchie, projekt může otevřít druhé zobrazení, pokud se může připojit k podkladovému datovému objektu dokumentu. V opačném případě by měl projekt použít ukazatel na rámeček okna zobrazení k opětovnému zobrazení existujícího okna.

   - Pokud existuje pouze datový objekt dokumentu, projekt by měl určit, zda může použít datový objekt dokumentu pro jeho zobrazení. Pokud je datový objekt dokumentu kompatibilní, proveďte kroky popsané v [části Otevřít editor specifický pro projekt](../extensibility/how-to-open-project-specific-editors.md).

     Pokud datový objekt dokumentu není kompatibilní, měla by být uživateli zobrazena chyba, která označuje, že soubor je právě používán. Tato chyba by měla být zobrazena pouze v přechodných případech, například při kompilaci souboru současně se uživatel pokouší [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otevřít soubor pomocí jiného editoru než základního textového editoru. Základní textový editor může sdílet datový objekt dokumentu s kompilátorem.

3. Pokud dokument není otevřen, protože neexistuje žádný datový objekt dokumentu nebo objekt zobrazení dokumentu, proveďte kroky v [otevřete editor specifický pro projekt](../extensibility/how-to-open-project-specific-editors.md).

## <a name="open-a-standard-editor"></a>Otevření standardního editoru
 Pomocí následujícího postupu otevřete standardní editor pro soubor, který je již otevřen.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Otevření standardního editoru pro otevřený soubor

1. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

     Tato metoda nejprve ověří, zda dokument <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>již není otevřen voláním . Pokud je dokument již otevřen, zobrazí se okno jeho editoru.

2. Pokud dokument není otevřený, proveďte kroky v [části Postup: Otevření standardních editorů](../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Viz také
- [Otevřít a uložit položky projektu](../extensibility/internals/opening-and-saving-project-items.md)
- [Postup: Otevření editorů specifických pro projekt](../extensibility/how-to-open-project-specific-editors.md)
- [Postup: Otevření standardních editorů](../extensibility/how-to-open-standard-editors.md)
