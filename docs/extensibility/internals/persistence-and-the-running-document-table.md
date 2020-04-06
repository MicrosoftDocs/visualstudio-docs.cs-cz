---
title: Trvalosti a tabulka spuštěné tabulky dokumentů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba698f20b83d1a7af42aeca046aa2a8c943838ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706721"
---
# <a name="persistence-and-the-running-document-table"></a>Trvalost a spuštěná tabulka dokumentů
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ide projekty jsou zcela odpovědné za správu trvalosti jejich položek <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>projektu, které dosáhnou pomocí služby . Dokumenty jsou základní jednotkou trvalosti v prostředí sady Visual Studio. Projekty koordinují otevírání, ukládání a přejmenování dokumentů pomocí spuštěné tabulky dokumentů (RDT), což je prostředek, který sleduje stav všech otevřených dokumentů.

## <a name="managing-persistence"></a>Správa trvalosti
 Projekty řídí službu trvalost prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> implementací rozhraní. Zatímco prostředí nikdy přímo požádá dokument, aby přetrvával sám, požádá vlastnící projekt (nebo hierarchii) o uložení dokumentu. To umožňuje projektu uložit data položek projektu do místních souborů, vzdálených souborů, databáze, úložiště nebo jiného média.

 Globální prostředí udržuje RDT. Prostředí udržuje položky pro všechna otevřená okna a dokumenty v RDT, což jim umožňuje přijímat zvláštní oznámení, například při zavření řešení. RdT navíc umožňuje prostředí sledovat jejich odpovídající uzly v **Průzkumníku řešení**. RDT udržuje jeden záznam na otevřený, trvalý objekt, včetně souborů projektu a dokumentů položky projektu.

## <a name="see-also"></a>Viz také
- [Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md)
- [Výběr a měna v prostředí IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
