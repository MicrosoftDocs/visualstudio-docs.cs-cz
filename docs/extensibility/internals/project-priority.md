---
title: Priorita projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a75c1c333d88e1bf5524281bee8b2a683ca6c98e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706424"
---
# <a name="project-priority"></a>Priorita projektu
Položka projektu je obvykle členem pouze jednoho projektu v řešení. Proto ide můžete snadno určit, který projekt se používá k otevření položky. Pokud je však položka členem více než jednoho projektu, ide používá schéma priority k určení nejlepšího projektu pro otevření položky.

 V následujícím seznamu je uvedeno schéma priority projektu:

- IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> metodu pro každý projekt v řešení k určení, zda je dokument členem tohoto projektu.

- Pokud je dokument členem projektu, projekt odpoví s prioritou, kterou projekt přiřadí podle jeho zpracování tohoto dokumentu. Například jazykový projekt reaguje s vysokou prioritou pro své zdrojové soubory jazyka, ale reaguje s nižší prioritou pro nerozpoznaný typ souboru, který se nepoužívá jako součást procesu sestavení.

- Projekty, které poskytují vlastní editory specifické pro projekt nebo návrháře pro dokument také získat vysokou prioritu.

- Výčet <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> poskytuje hodnoty priority dokumentu.

- Projekt, který určuje nejvyšší prioritu je dána kontext k otevření dokumentu. Pokud dva projekty vrátí stejné hodnoty priority, je upřednostňován aktivní projekt. Pokud žádný projekt v řešení odpoví, že může otevřít dokument, ide umístí dokument v projektu Různé soubory. Další informace naleznete [v tématu Různé soubory project .](../../extensibility/internals/miscellaneous-files-project.md)

## <a name="see-also"></a>Viz také
- [Projekt Ostatní soubory](../../extensibility/internals/miscellaneous-files-project.md)
- [Postupy: Otevření editorů pro otevřené dokumenty](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
