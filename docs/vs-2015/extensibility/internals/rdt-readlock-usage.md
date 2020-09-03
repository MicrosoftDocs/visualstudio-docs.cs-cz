---
title: Využití RDT_ReadLock | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9a6b5f86f0cfbb71f6264bdc74df72ad9209c9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154132"
---
# <a name="rdt_readlock-usage"></a>Využití RDT_ReadLock
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> je příznak, který poskytuje logiku pro uzamykání dokumentu v běžící tabulce dokumentů (RDT), což je seznam všech dokumentů, které jsou aktuálně otevřeny v integrovaném vývojovém prostředí sady Visual Studio. Tento příznak určuje, kdy jsou otevřeny dokumenty a zda je dokument viditelný v uživatelském rozhraní nebo je držen v paměti.  
  
 Obecně platí, že byste měli použít, <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Pokud je splněna jedna z následujících podmínek:  
  
- Když chcete dokument otevřít jako nečitelný a jen pro čtení, ale ještě není vytvořený, který <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> by ho měl vlastnit.  
  
- Když chcete, aby uživatel byl vyzván k uložení dokumentu, který byl neviditelně otevřen předtím, než ho uživatel zobrazil v uživatelském rozhraní, a pak se pokusil jej zavřít.  
  
## <a name="how-to-manage-visible-and-invisible-documents"></a>Správa viditelných a neviditelných dokumentů  
 Když uživatel otevře dokument v uživatelském rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> musí být vytvořen vlastník dokumentu a <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> musí být nastaven příznak. Pokud není <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> možné navázat žádného vlastníka, dokument se neuloží, když uživatel klikne na **Uložit vše** nebo zavře IDE. To znamená, že pokud je dokument otevřený v paměti, kde je upravený, a uživatel se zobrazí výzva k uložení dokumentu při vypnutí nebo uložení, pokud je zvolena možnost **Uložit vše** , `RDT_ReadLock` nelze použít. Místo toho je nutné použít `RDT_EditLock` a <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> při použití <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> příznaku.  
  
## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock a úpravy dokumentu  
 Výše zmíněný příznak indikuje, že neviditelné otevření dokumentu vrátí, když ho `RDT_EditLock` uživatel otevře v viditelném **DocumentWindow**. Pokud k tomu dojde, zobrazí se uživateli při zavření viditelného **DocumentWindow** výzvy k **uložení** . Implementace Microsoft. VisualStudio. Package. Automation. OAProject. CodeModel, které používají <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> službu jako první, pracují pouze v případě, že je `RDT_ReadLock` proveden pouze příkaz (tj. když je dokument otevřen, je neviditelné k analýze informací). Později, pokud je potřeba dokument upravit, zámek se upgraduje na slabý **RDT_EditLock**. Pokud uživatel potom otevře dokument v viditelném **DocumentWindow**, `CodeModel` je jeho vydání slabé `RDT_EditLock` .  
  
 Pokud uživatel potom zavře **DocumentWindow** a při zobrazení výzvy k uložení otevřeného dokumentu zvolí možnost **ne** , pak implementace uvolní `CodeModel` všechny informace v dokumentu a znovu ho otevře z disku, a to i příště, než se další informace pro dokument vyžadují. Subtlety tohoto chování je instance, ve které uživatel otevře **DocumentWindow** neviditelného otevřeného dokumentu, změní ho, zavře ho a po zobrazení výzvy k uložení dokumentu vybere **ne** . V takovém případě, pokud dokument má `RDT_ReadLock` , dokument ve skutečnosti nebude zavřen a upravený dokument zůstane otevřený v paměti, i když uživatel neuloží dokument.  
  
 Pokud neviditelné otevření dokumentu používá slabý `RDT_EditLock` , pak vrátí jeho zámek, když uživatel otevře dokument viditelně a žádné další zámky nebudou uloženy. Když uživatel zavře **DocumentWindow** a při zobrazení výzvy k uložení dokumentu zvolí **ne** , musí být dokument uzavřený z paměti. To znamená, že neviditelný klient musí naslouchat událostem RDT, aby mohl sledovat tento výskyt. Při dalším požadavku dokumentu musí být dokument znovu otevřen.
