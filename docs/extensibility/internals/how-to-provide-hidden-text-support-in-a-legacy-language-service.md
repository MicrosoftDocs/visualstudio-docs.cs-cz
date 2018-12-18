---
title: 'Postupy: poskytování podpory skrytého textu ve službě starší verze jazyka | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d368caaa9b65f6f9ab8b12c1f49994e3bfe16670
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511957"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Postupy: Zadejte skrytého textu podporují ve službě starší verze jazyka
Můžete vytvořit skrytý text oblastech kromě oblasti osnovy. Oblasti skrytého textu může být spravovanými klienta nebo řídit editoru a umožňují zcela skrýt oblast textu. Editor zobrazí počet skrytých oblastí: jako vodorovné čáry. Příkladem je **pouze pro skript** zobrazení v editoru jazyka HTML.  
  
  
## <a name="to-implement-a-hidden-text-region"></a>K implementaci oblasti skrytého textu  
  
1.  Volání `QueryService` pro <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Vrátí ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>a předejte ukazatele pro dané textové vyrovnávací paměti. Určuje, zda relace skrytého textu, který je již existuje pro vyrovnávací paměť.  
  
3.  Pokud už existuje a není potřeba vytvořit jeden a ukazatel na existující <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> je vrácen objekt. Použijte tento ukazatel na výčet a nabídnout vytvořit oblasti skrytého textu. V opačném případě volat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> vytvořte relaci skrytého textu pro vyrovnávací paměť.  
  
     Ukazatel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> je vrácen objekt.  
  
    > [!NOTE]
    >  Při volání `CreateHiddenTextSession`, můžete zadat klienta skrytého textu (to znamená <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Klient skrytého textu vás upozorní, když skrytého textu nebo osnovy rozbalená nebo sbalená uživatelem.  
  
4.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> můžete přidat jednu nebo více nových popisují oblastí najednou, zadáním následujících informací v `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) parametru:  
  
    1.  Zadejte hodnotu `hrtConcealed` v `iType` člena <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury k označení, že při vytváření skrytých oblastí, nikoli na oblast osnovy.  
  
        > [!NOTE]
        >  Pokud se skryté oblasti jsou skryté, editoru automaticky zobrazí čáry kolem skryté regiony udávajících přítomnost.  
  
    2.  Určete, zda je oblast spravovanými klienta nebo editor spravovanými v `dwBehavior` členy <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Inteligentní sbalování implementace může obsahovat kombinaci řídit editoru a klient osnovy a skrytý text oblastech.