---
title: Priorita projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee4c0f41902e74f58684d6806877d352447351bf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725399"
---
# <a name="project-priority"></a>Priorita projektu
Položka projektu je obvykle členem pouze jednoho projektu v řešení. Proto může rozhraní IDE snadno určit, který projekt se má použít k otevření položky. Pokud je však položka členem více než jednoho projektu, rozhraní IDE používá schéma priority k určení nejvhodnějšího projektu pro otevření položky.

 Následující seznam uvádí schéma priority projektu:

- Rozhraní IDE volá metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> pro každý projekt v řešení, aby bylo možné určit, zda je dokument členem daného projektu.

- Pokud je dokument členem projektu, projekt reaguje na prioritu, kterou projekt přiřadí podle jeho manipulace s tímto dokumentem. Například jazykový projekt reaguje s vysokou prioritou pro své jazykové zdrojové soubory, ale reaguje s nižší prioritou pro nerozpoznaný typ souboru, který se nepoužívá jako součást procesu sestavení.

- Projekty, které poskytují vlastní editory nebo návrháře specifické pro projekt pro dokument, také dostanou vysokou prioritu.

- Výčet <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> poskytuje hodnoty priority dokumentu.

- Projekt, který určuje nejvyšší prioritu, je dán kontextem pro otevření dokumentu. Pokud dva projekty vrací stejné prioritní hodnoty, je upřednostňován aktivní projekt. Pokud žádný projekt v řešení nereaguje na to, že může otevřít dokument, rozhraní IDE vloží dokument do projektu různé soubory. Další informace naleznete v tématu [různé soubory projektu](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Viz také:
- [Projekt Ostatní soubory](../../extensibility/internals/miscellaneous-files-project.md)
- [Postupy: Otevření editorů pro otevřené dokumenty](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)