---
title: Trvalost a běžící tabulka dokumentů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c422ad1735312c82c8dc027c4adf73c1b033685
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196092"
---
# <a name="persistence-and-the-running-document-table"></a>Trvalost a spuštěná tabulka dokumentů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaném vývojovém prostředí jsou projekty zcela zodpovědné za správu Persistence svých položek projektu, které provádějí používání služby, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Dokumenty jsou základní jednotkou trvalosti v prostředí sady Visual Studio. Projekty koordinují otevírání, ukládání a přejmenování dokumentů pomocí tabulky spuštěných dokumentů (RDT), prostředku, který sleduje stav všech otevřených dokumentů.  
  
## <a name="managing-persistence"></a>Správa trvalosti  
 Projekty ovládají Službu trvalosti prostředí implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> rozhraní. I když se v tomto prostředí nikdy přímo nedotazuje dokumentu na trvalé uložení, požádá o něj vlastnící projekt (nebo hierarchii), který dokument uloží. To umožňuje, aby projekt uložil data položky projektu do místních souborů, vzdálených souborů, databáze, úložiště nebo jiného média.  
  
 Globální prostředí udržuje RDT. Prostředí uchovává záznamy všech otevřených oken a dokumentů v RDT, což umožňuje získat speciální oznámení, jako je například při zavření řešení. RDT navíc umožňuje prostředí sledovat své odpovídající uzly v **Průzkumník řešení**. RDT udržuje jeden záznam na otevřený a trvalý objekt, včetně souborů projektu a dokumentů položek projektu.  
  
## <a name="see-also"></a>Viz také  
 [Běžící tabulka dokumentů](../../extensibility/internals/running-document-table.md)   
 [Výběr a měna v prostředí IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
