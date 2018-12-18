---
title: Trvalost a spuštění dokumentu tabulky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51f3d2cc41c9adaf97215701ad01da2e59d245a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129732"
---
# <a name="persistence-and-the-running-document-table"></a>Trvalosti a tabulce dokument spuštěná
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, projekty jsou zcela zodpovědní za správu trvalost jejich položky projektu, které se toho dosáhnout pomocí služby, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Dokumenty jsou základní jednotkou trvalost v prostředí Visual Studio. Projekty koordinovat otevření, uložení a přejmenování dokumentů s spuštěné tabulce dokumentu r. (..), na prostředek, který sleduje stav všechny otevřené dokumenty.  
  
## <a name="managing-persistence"></a>Správa trvalost  
 Projekty řídit v prostředí trvalost služby pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> rozhraní. Když prostředí nikdy přímo požádá dokumentu trvání, požádá vlastnícím projektu (nebo hierarchie) k uložení dokumentu. To umožňuje projekt, který má-li uložit data položky projektu do místních souborů, vzdálené soubory, databáze, úložiště nebo jiné médium.  
  
 Globální prostředí udržuje r.... Prostředí udržuje položky pro všechna otevřená okna a dokumenty v r..., která vám umožní, aby přijímat speciální oznámení, například při uzavření řešení. Kromě toho r... umožňuje sledovat jejich odpovídajících uzlů v prostředí **Průzkumníku řešení**. R... udržuje jeden záznam za otevřený, trvalá objektu, včetně souborů projektu a položek projektů dokumenty.  
  
## <a name="see-also"></a>Viz také  
 [Spuštěné tabulce dokumentu](../../extensibility/internals/running-document-table.md)   
 [Výběr a měna v prostředí IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)