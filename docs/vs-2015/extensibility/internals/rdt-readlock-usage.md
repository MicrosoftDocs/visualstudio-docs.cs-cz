---
title: Využití RDT_ReadLock | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 337fa34bce713f743b8962f41a6889335b54b722
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817448"
---
# <a name="rdtreadlock-usage"></a>Využití RDT_ReadLock
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> je příznak, který obsahuje logiku pro uzamčení dokumentu v systémem dokumentu tabulky (r...), který je uvedený seznam všech dokumentů, které jsou právě otevřeny v integrovaném vývojovém prostředí sady Visual Studio. Tento příznak určuje, kdy jsou otevřené dokumenty a zda dokument je zobrazen v uživatelském rozhraní nebo pevné nezaregistroval v paměti.  
  
 Obecně byste použili <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> při je splněna jedna z následujících akcí:  
  
-   Pokud chcete otevřít dokument transparentně a jen pro čtení, ale je ještě není vytvořeno, který <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> by vlastnit.  
  
-   Když chcete uživateli výzva k uložení dokumentu, kterou jste otevřeli nezaregistroval předtím, než uživatel zobrazí v uživatelském rozhraní a pak se pokusila zavřít ho.  
  
## <a name="how-to-manage-visible-and-invisible-documents"></a>Jak spravovat viditelné a neviditelné dokumenty  
 Když uživatel otevře dokument v Uživatelském rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> vlastník dokumentu musí být stanovena a <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> musí být nastaven příznak. Pokud ne <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> vlastníka je možné navázat, pak dokument se neuloží, když uživatel klikne **Uložit vše** nebo ukončí rozhraní IDE. To znamená, že pokud je otevřený dokument nezaregistroval tam, kde je změněný v paměti a uživatel je vyzván k uložení dokumentu na vypnutí nebo uložit, pokud **Uložit vše** je vybrán, pak `RDT_ReadLock` nelze použít. Místo toho je nutné použít `RDT_EditLock` a registrovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> při <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> příznak.  
  
## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock a úpravy dokumentu  
<<<<<<< HEAD předchozí příznak uvedených označuje, že neviditelné otevření dokumentu přinese jeho `RDT_EditLock` při otevření dokumentu uživatelem do viditelné **DocumentWindow**. V takovém případě uživateli zobrazí s **Uložit** výzvu při viditelných **DocumentWindow** je zavřený. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` implementace, které používají <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> služby zpočátku fungovat, pokud je to jenom `RDT_ReadLock` se provede, (to znamená, když dokument je otevřen nezaregistroval k analýze informací o). Později, pokud je třeba upravit dokument, pak zámek se upgraduje na slabé **RDT_EditLock**. Pokud uživatel potom otevře dokument v viditelné **DocumentWindow**, `CodeModel`společnosti slabé `RDT_EditLock` vydání.  
=== Předchozí příznak uvedených označuje, že neviditelné otevření dokumentu přinese jeho `RDT_EditLock` při otevření dokumentu uživatelem do viditelné **DocumentWindow**. V takovém případě uživateli zobrazí s **Uložit** výzvu při viditelných **DocumentWindow** je zavřený. Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel implementace, které používají <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> služby zpočátku fungovat, pokud je to jenom `RDT_ReadLock` se provede, (to znamená, když dokument je otevřen nezaregistroval k analýze informací o). Později, pokud je třeba upravit dokument, pak zámek se upgraduje na slabé **RDT_EditLock**. Pokud uživatel potom otevře dokument v viditelné **DocumentWindow**, `CodeModel`společnosti slabé `RDT_EditLock` vydání.  
>>>>>>> 9c8493a8dd... Vyzkoušejte nový rozsah moniker pro potřeby podpory kombinace verzí
  
 Pokud uživatel potom jej zavře **DocumentWindow** a zvolí **ne** po zobrazení výzvy k uložení otevřít dokument, pak bude `CodeModel` implementace uvolní všechny informace v dokumentu a znovu neotevře dokument z disku neviditelné při příštím Další informace jsou nezbytné k dokumentu. Subtlety toto chování je instanci, kde uživatel otevře **DocumentWindow** neviditelné otevřeného dokumentu, změní se zavře a následně klikne **ne** po zobrazení výzvy k uložení dokumentu. V tomto případě, pokud má dokument `RDT_ReadLock`, dokument nebude ve skutečnosti byl a upravený dokument zůstanou otevřené nezaregistroval v paměti, i když se uživatel rozhodl nechcete uložit dokument.  
  
 Pokud neviditelné otevření dokumentu používá weak `RDT_EditLock`, pak bude vrácen platnost zámku, když uživatel otevře dokument viditelně a žádné další zámky. Když uživatel zavírá **DocumentWindow** a zvolí **ne** po zobrazení výzvy k uložení dokumentu, pak dokument musíte zavřít z paměti. To znamená, že neviditelné klient musí naslouchat událostem rámcový sledovat výskyt této události. Dalším vyžádáním dokumentu dokumentu musí být znovu otevřít.

