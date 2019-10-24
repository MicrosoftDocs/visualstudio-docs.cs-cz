---
title: Trvalost a běžící tabulka dokumentů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f03836e1faaac03fbd89c0b93f37a698cbdcd56a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726086"
---
# <a name="persistence-and-the-running-document-table"></a>Trvalost a spuštěná tabulka dokumentů
V rozhraní IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jsou projekty zcela zodpovědné za správu Persistence svých položek projektu, které provádějí používání služby, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Dokumenty jsou základní jednotkou trvalosti v prostředí sady Visual Studio. Projekty koordinují otevírání, ukládání a přejmenování dokumentů pomocí tabulky spuštěných dokumentů (RDT), prostředku, který sleduje stav všech otevřených dokumentů.

## <a name="managing-persistence"></a>Správa trvalosti
 Projekty ovládají Službu trvalosti prostředí implementací rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>. I když se v tomto prostředí nikdy přímo nedotazuje dokumentu na trvalé uložení, požádá o něj vlastnící projekt (nebo hierarchii), který dokument uloží. To umožňuje, aby projekt uložil data položky projektu do místních souborů, vzdálených souborů, databáze, úložiště nebo jiného média.

 Globální prostředí udržuje RDT. Prostředí uchovává záznamy všech otevřených oken a dokumentů v RDT, což umožňuje získat speciální oznámení, jako je například při zavření řešení. RDT navíc umožňuje prostředí sledovat své odpovídající uzly v **Průzkumník řešení**. RDT udržuje jeden záznam na otevřený a trvalý objekt, včetně souborů projektu a dokumentů položek projektu.

## <a name="see-also"></a>Viz také:
- [Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md)
- [Výběr a měna v prostředí IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)