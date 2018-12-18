---
title: Pokyny pro správu Další zdroje pro projekty a editory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 454984334cbd91833447829227787b0679b4ed54
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497716"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Pokyny pro správu Další zdroje pro projekty a editory
Existuje mnoho pokyny, které projekty a editory by měl splňovat za účelem podpory správy zdrojového kódu.  
  
## <a name="guidelines"></a>Pokyny  
 Projekt nebo editor by měl provádět následující pro podporu správy zdrojového kódu:  
  
|Oblast|Projekt|Editor|Podrobnosti|  
|----------|-------------|------------|-------------|  
|Soukromé kopie souborů|X||Prostředí podporuje privátní kopie souborů. To znamená že každý uživatel, který uveden v projektu má jeho vlastní privátní kopii souborů v daném projektu.|  
|ANSI nebo Unicode trvalosti|X|X|Pokud píšete kód trvalost, zachovejte soubory ve formátu ANSI, protože většina zdrojových programů ovládací prvek aktuálně nepodporují kódování Unicode.|  
|Vytvoření výčtu souborů|X||Projekt musí obsahovat konkrétní seznam všech souborů v rámci něj a musí být schopen vytvořit výčet seznamu souborů s využitím <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Projekt by měly vystavit také názvy položek prostřednictvím jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> implementaci a podporu vyhledávání názvu (včetně speciálních soubory) prostřednictvím jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementace.|  
|Formát textu|X|X|Pokud je to možné, soubory by měly být ve formátu textu pro podporu sloučení různé verze. Soubory, které nejsou ve formátu textu nelze sloučit s jinými verzemi souboru později. Je upřednostňovaném textovém formátu XML.|  
|Na základě odkazu|X||Projekty založené na referenční snadno podporují ve správě zdrojového kódu. Ale projekty založené na adresáři jsou podporovány také správy zdrojového kódu jako projekt může vytvořit seznam svých souborů na vyžádání, bez ohledu na to, zda existují tyto soubory na disku. Při otevření projektu ze správy zdrojových kódů, soubor projektu se načtou první před všechny jeho soubory.|  
|Zachovat objekty a vlastnostmi v předvídatelné pořadí|X|X|Uchování souborů v předvídatelné pořadí, jako je například abecedním pořadí pro usnadnění sloučení.|  
|Znovu načíst|X|X|Při změně souboru na disku, musí být schopen jej znovu načíst editor. Při účasti ve správě zdrojového kódu, prostředí se znovu načte data pro vás voláním vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementace. Automatizování nejobtížnějších reload případ je, když je nastane, pokud jste volali IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a zpracovávají informace. Znovu načíst kód však musí být možné spouštět v této situaci.<br /><br /> Prostředí automaticky znovu načte soubory projektu. Však musí implementovat projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> pokud obsahuje vnořené hierarchie za účelem podpory znovu načíst vnořené soubory projektu.|  
  
## <a name="see-also"></a>Viz také:  
 [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)