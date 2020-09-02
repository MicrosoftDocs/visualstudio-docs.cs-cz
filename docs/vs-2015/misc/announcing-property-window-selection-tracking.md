---
title: Oznamuje se sledování výběru okna vlastností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002452"
---
# <a name="announcing-property-window-selection-tracking"></a>Oznamuje se sledování výběru okna vlastností.
Chcete-li pracovat s oknem **vlastnosti** nebo se stránkami **vlastností** , například formulář, text nebo výběr, pro který chcete zobrazit vlastnosti, je nutné mít úplný přehled o tom, jak zakoordinujete výběr. Například je třeba zjistit, zda máte jeden nebo více výběrů. Pak je potřeba oznámit typ výběru (jeden nebo více) k rozhraní IDE pomocí <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> rozhraní. Toto rozhraní poskytuje informace vyžadované v okně **vlastnosti** .  
  
### <a name="to-announce-selection-to-the-environment"></a>Oznámení výběru do prostředí  
  
1. Volání `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> .  
  
    1. K tomu použijte ukazatel na lokalitu předaný do zobrazení při jeho vytvoření.  
  
    2. Zavolejte `QueryService` ze zobrazení pro `SID_STrackSelection` službu.  
  
         Tím se vrátí ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Volejte <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> metodu pokaždé, když se změní váš výběr, a předejte ukazatel na objekt, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
     Objekt kontejneru výběru může použít buď jeden nebo více výběrů, a obsahuje informace o výběru v `IDispatch` objektu. Volání <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> metody upozorní okno **vlastnosti** , že se výběr změnil. Okno **vlastnosti** poté používá objekty na <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> k určení, zda došlo k jednomu nebo více výběrům a co jsou výběry vlastních objektů.  
  
     Pokud zadáte vícenásobný výběr, okno **vlastnosti** najde průnik mezi běžnými vlastnostmi objektů. Zadáte-li výběr jednoho objektu, zobrazí se v okně **vlastnosti** všechny vlastnosti pro jeden objekt.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../extensibility/internals/extending-properties.md)   
 [Stránky vlastností](../extensibility/internals/property-pages.md)