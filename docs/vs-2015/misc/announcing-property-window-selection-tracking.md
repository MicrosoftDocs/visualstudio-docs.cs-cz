---
title: Oznamujeme vydání vlastnost okno Výběr sledování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: 9639e0347689fc99e0b43c4b69394b522af984da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246737"
---
# <a name="announcing-property-window-selection-tracking"></a>Oznamujeme vydání výběr vlastností okna Sledování
Pokud budete chtít pracovat **vlastnosti** okno nebo **vlastnost** stránek, například formuláře, text nebo výběr, pro kterou chcete zobrazit vlastnosti, je nutné úplné znalosti toho, jak můžete koordinovat výběru. Například musíte vědět, jestli máte výběru jednoho nebo více výběrů. Bude potřeba oznámit typ vašeho výběru (jeden nebo více) pro integrované vývojové prostředí s využitím <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> rozhraní. Toto rozhraní poskytuje informace vyžadované **vlastnosti** okna.  
  
### <a name="to-announce-selection-to-the-environment"></a>Oznamujeme výběr prostředí  
  
1.  Volání `QueryInterface` pro <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>.  
  
    1.  K tomuto účelu použijte ukazatel lokality předána do zobrazení při vytvoření rovnou uložil.  
  
    2.  Volání `QueryService` ze zobrazení pro `SID_STrackSelection` služby.  
  
         Vrátí ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> pokaždé, když se změní výběr a předáte ukazatel na objekt, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
     Objekt kontejneru výběru můžete použít jeden nebo více výběrů a obsahuje informace o výběru v `IDispatch` objektu. Volání <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> metoda upozorní **vlastnosti** okno, které se změní výběr. **Vlastnosti** okno použije objekty na <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> k určení, jestli mají došlo k jedné nebo více výběrů a jaké jsou možnosti skutečný objekt.  
  
     Pokud zadáte více výběrů, pak bude **vlastnosti** okno zjistí průnik mezi běžné vlastnosti pro objekty. Pokud zadáte jeden objekt výběru, pak bude **vlastnosti** okně se zobrazí všechny vlastnosti pro jeden objekt.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../extensibility/internals/extending-properties.md)   
 [Stránky vlastností](../extensibility/internals/property-pages.md)