---
title: 'Postupy: implementace mechanismu Find and Replace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4362d0b0c3f013ce6f38d13265dcc181c77012c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62548691"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Postupy: Implementace mechanismu Najít a nahradit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio poskytuje dva způsoby implementace Find/Replace. Jedním ze způsobů je předat textový obrázek do prostředí a nechat ho zpracovávat hledání, zvýrazňování a nahrazování textu. To umožňuje uživatelům zadat více rozsahů textu. Další možností je, že VSPackage může tuto funkci řídit sám. V obou případech je nutné upozornit prostředí na aktuální cíl a cíle pro všechny otevřené dokumenty.  
  
### <a name="to-implement-findreplace"></a>Implementace Find/nahrazování  
  
1. Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> rozhraní na jeden z objektů vrácených vlastnostmi rámce <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> nebo <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> . Pokud vytváříte vlastní editor, měli byste implementovat toto rozhraní jako součást třídy vlastního editoru.  
  
2. Použijte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> metodu k určení možností, které editor podporuje, a k určení, zda implementuje vyhledávání obrázků.  
  
     Pokud editor podporuje vyhledávání textových obrázků, implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A> .  
  
     V opačném případě implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> .  
  
3. Pokud implementujete <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> metody a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> , můžete zjednodušit úlohy vyhledávání voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> rozhraní.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
