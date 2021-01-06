---
title: Trvalost a běžící tabulka dokumentů | Microsoft Docs
description: Přečtěte si, jak projekty koordinují otevírání, ukládání a přejmenování dokumentů v běžící tabulce dokumentů, které sledují stav dokumentu v integrovaném vývojovém prostředí sady Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bfc480c8b4a41fe29900681289ad08c54d3c1f31
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875957"
---
# <a name="persistence-and-the-running-document-table"></a>Trvalost a spuštěná tabulka dokumentů
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí jsou projekty zcela zodpovědné za správu Persistence svých položek projektu, které provádějí používání služby, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Dokumenty jsou základní jednotkou trvalosti v prostředí sady Visual Studio. Projekty koordinují otevírání, ukládání a přejmenování dokumentů pomocí tabulky spuštěných dokumentů (RDT), prostředku, který sleduje stav všech otevřených dokumentů.

## <a name="managing-persistence"></a>Správa trvalosti
 Projekty ovládají Službu trvalosti prostředí implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> rozhraní. I když se v tomto prostředí nikdy přímo nedotazuje dokumentu na trvalé uložení, požádá o něj vlastnící projekt (nebo hierarchii), který dokument uloží. To umožňuje, aby projekt uložil data položky projektu do místních souborů, vzdálených souborů, databáze, úložiště nebo jiného média.

 Globální prostředí udržuje RDT. Prostředí uchovává záznamy všech otevřených oken a dokumentů v RDT, což umožňuje získat speciální oznámení, jako je například při zavření řešení. RDT navíc umožňuje prostředí sledovat své odpovídající uzly v **Průzkumník řešení**. RDT udržuje jeden záznam na otevřený a trvalý objekt, včetně souborů projektu a dokumentů položek projektu.

## <a name="see-also"></a>Viz také
- [Spuštění tabulky dokumentů](../../extensibility/internals/running-document-table.md)
- [Výběr a měna v prostředí IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
