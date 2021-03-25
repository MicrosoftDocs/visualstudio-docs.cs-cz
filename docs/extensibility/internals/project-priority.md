---
title: Priorita projektu | Microsoft Docs
description: Přečtěte si o schématu priority, které používá integrované vývojové prostředí (IDE) sady Visual Studio k určení nejlepšího projektu pro otevření položky, pokud je položka členem více než jednoho projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6aefb6b1670da812a36efcc1baa3cb23f23e2561
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064485"
---
# <a name="project-priority"></a>Priorita projektu
Položka projektu je obvykle členem pouze jednoho projektu v řešení. Proto může rozhraní IDE snadno určit, který projekt se má použít k otevření položky. Pokud je však položka členem více než jednoho projektu, rozhraní IDE používá schéma priority k určení nejvhodnějšího projektu pro otevření položky.

 Následující seznam uvádí schéma priority projektu:

- Rozhraní IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> metodu pro každý projekt v řešení a určí, zda je dokument členem daného projektu.

- Pokud je dokument členem projektu, projekt reaguje na prioritu, kterou projekt přiřadí podle jeho manipulace s tímto dokumentem. Například jazykový projekt reaguje s vysokou prioritou pro své jazykové zdrojové soubory, ale reaguje s nižší prioritou pro nerozpoznaný typ souboru, který se nepoužívá jako součást procesu sestavení.

- Projekty, které poskytují vlastní editory nebo návrháře specifické pro projekt pro dokument, také dostanou vysokou prioritu.

- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>Výčet poskytuje hodnoty priority dokumentu.

- Projekt, který určuje nejvyšší prioritu, je dán kontextem pro otevření dokumentu. Pokud dva projekty vrací stejné prioritní hodnoty, je upřednostňován aktivní projekt. Pokud žádný projekt v řešení nereaguje na to, že může otevřít dokument, rozhraní IDE vloží dokument do projektu různé soubory. Další informace naleznete v tématu [různé soubory projektu](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Viz také
- [Projekt Ostatní soubory](../../extensibility/internals/miscellaneous-files-project.md)
- [Postupy: Otevření editorů pro otevřené dokumenty](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
