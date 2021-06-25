---
title: Project Priority | Microsoft Docs
description: Přečtěte si o schématu priority, které integrované vývojové Visual Studio používá k určení nejlepšího projektu pro otevření položky, pokud je položka členem více než jednoho projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ac0556e63b25f0f2a0df399cb23d5e2e9473008
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899638"
---
# <a name="project-priority"></a>Priorita projektu
Položka projektu je obvykle členem pouze jednoho projektu v řešení. Integrované vývojové prostředí proto může snadno určit, který projekt se použije k otevření položky. Pokud je však položka členem více než jednoho projektu, integrované vývojové prostředí (IDE) používá schéma priority k určení nejlepšího projektu pro otevření položky.

 Následující seznam ukazuje schéma priority projektu:

- Integrované vývojové prostředí volá metodu pro každý projekt v řešení, aby určilo, zda je dokument <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> členem tohoto projektu.

- Pokud je dokument členem projektu, projekt odpoví prioritou, kterou projekt přiřadí na základě zpracování tohoto dokumentu. Například projekt jazyka odpovídá se zdrojovými soubory jazyka s vysokou prioritou, ale má nižší prioritu pro nerozpoznaný typ souboru, který se v rámci procesu sestavení nepouží.

- Projekty, které poskytují vlastní editory nebo návrháře pro dokument, mají také vysokou prioritu.

- Výčet <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> poskytuje hodnoty priority dokumentu.

- Projektu, který určuje nejvyšší prioritu, je dán kontext pro otevření dokumentu. Pokud dva projekty vrátí stejnou hodnotu priority, upřednostní se aktivní projekt. Pokud žádný projekt v řešení nereaguje na to, že dokument může otevřít, integrované vývojové prostředí (IDE) dokument vložilo do projektu Různé soubory. Další informace najdete v tématu [Různé soubory – projekt](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Viz také
- [Projekt Ostatní soubory](../../extensibility/internals/miscellaneous-files-project.md)
- [Postupy: Otevření editorů pro otevřené dokumenty](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
