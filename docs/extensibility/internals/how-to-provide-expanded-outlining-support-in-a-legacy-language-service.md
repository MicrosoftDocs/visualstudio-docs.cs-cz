---
title: Zadejte vymezující podporu ve službě jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 31ae8a6aeba28fbe90e68305f2b48021b4327c26
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511386"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Postupy: Rozšířená podpora osnovy ve službě starší verze jazyka
Existují dvě možnosti pro rozšíření podpora osnovy pro váš jazyk nad rámec podpora **sbalit do definic** příkazu. Můžete přidat oblasti řízené editor osnovy a přidat řízené klienta obrys oblasti.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Přidání oblasti řízené editor osnovy  
 Pomocí tohoto postupu můžete vytvořit určitá oblast osnovy a následné povolení editoru zpracovat, zda je rozbalená oblast, sbaleno a tak dále. Dvě možnosti pro poskytování podpora osnovy tato možnost je nejméně robustní. Pro tuto možnost, můžete vytvořit novou oblast osnovy textu s využitím zadaného konfigurovatelnou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Po vytvoření této oblasti své chování se řídí tím editoru. Pomocí následujícího postupu k implementaci řízené editor osnovy oblastech.  
  
### <a name="to-implement-an-editor-controlled-outline-region"></a>K implementaci určitá oblast spravovanými editor osnovy  
  
1.  Volání `QueryService` pro <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Vrátí ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>a předejte ukazatele pro dané textové vyrovnávací paměti. Vrátí ukazatel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objektu do vyrovnávací paměti.  
  
3.  Volání <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> ukazatele na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> k přidání jednoho nebo více nových popisují oblastí najednou.  
  
     Tato metoda umožňuje zadat text osnovy, určuje, zda jsou existující oblasti obrys odebrán nebo zachována, a určuje, zda je v oblasti obrys rozbalit nebo sbalit ve výchozím nastavení v rozsahu.  
  
## <a name="add-client-controlled-outline-regions"></a>Přidat řízené klienta obrys oblasti  
 Použijte tento přístup k sbalování implementace řízené klienta (nebo inteligentní) jako, který se používá [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] jazykových služeb. Služba jazyka, který spravuje svou vlastní sbalování sleduje obsah vyrovnávací paměti textu zničit staré obrys oblasti, jakmile budou neplatné a vytvořit nové oblasti obrys podle potřeby.  
  
### <a name="to-implement-a-client-controlled-outline-region"></a>K implementaci řízené klienta obrys oblasti  
  
1.  Volání `QueryService` pro <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Vrátí ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>a předejte ukazatele pro dané textové vyrovnávací paměti. Určuje, zda relace skrytého textu, který je již existuje pro vyrovnávací paměť.  
  
3.  Pokud text relace již existuje a není potřeba vytvořit jeden a ukazatel na existující <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> je vrácen objekt. Použijte tento ukazatel na výčet a nabídnout vytvořit obrys oblasti. V opačném případě volat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> vytvořte relaci skrytého textu pro vyrovnávací paměť. Ukazatel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> je vrácen objekt.  
  
    > [!NOTE]
    >  Při volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, můžete zadat klienta skrytého textu (to znamená, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objekt). Tento klient upozorní vás, když se skrytého textu nebo obrys oblasti je rozbalená nebo sbalená uživatelem.  
  
4.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> struktura) parametr: Zadejte hodnotu <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> v `iType` člena <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury k označení, že vytváříte určitá oblast osnovy, nikoli skryté oblasti. Určete, zda je oblast spravovanými klienta nebo editor spravovanými v `dwBehavior` člena <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Inteligentní sbalování implementace může obsahovat kombinaci řídit editoru a klientské oblasti osnovy. Zadejte text banner, který se zobrazí, když vaše osnovy oblast je sbalena, jako je například "...", v `pszBanner` člena <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Editoru výchozí banner text pro skryté oblasti je "...".