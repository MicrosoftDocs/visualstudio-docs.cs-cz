---
title: Poskytování podpory v jazykové službě | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37deafa92477289a2124ecee101dd254e68ef01d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707973"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Postup: Poskytování rozšířené podpory ve starší jazykové službě
Existují dvě možnosti pro rozšíření osnovy podporu pro váš jazyk mimo podporu **Sbalit definice** příkazu. Můžete přidat oblasti osnovy řízené editorem a přidat oblasti osnovy řízené klientem.

## <a name="adding-editor-controlled-outline-regions"></a>Přidání oblastí osnovy řízených editorem
 Tento přístup slouží k vytvoření oblasti osnovy a potom povolit editoru zpracování, zda je oblast rozbalená, sbalená a tak dále. Ze dvou možností poskytování podpory je tato možnost nejméně robustní. Pro tuto možnost vytvoříte novou oblast osnovy nad <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>zadaným rozsahem textu pomocí aplikace . Po vytvoření této oblasti je jeho chování řízeno editorem. Pomocí následujícího postupu implementujte oblasti osnovy řízené editorem.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Implementace oblasti osnovy řízené editorem

1. Výzva `QueryService` k<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     To vrátí ukazatel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>na .

2. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, předávání ukazatele pro daný text vyrovnávací paměti. To vrátí ukazatel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> na objekt pro vyrovnávací paměť.

3. Volání <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> na ukazatel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>na .

4. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> pro přidání jedné nebo více nových oblastí osnovy najednou.

     Tato metoda umožňuje určit rozsah textu k osnově, zda jsou existující oblasti osnovy odebrány nebo zachovány a zda je oblast osnovy ve výchozím nastavení rozbalená nebo sbalená.

## <a name="add-client-controlled-outline-regions"></a>Přidání oblastí osnovy řízených klientem
 Tento přístup slouží k implementaci klientem řízeného (nebo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] inteligentního) osnovy, jako je ta, kterou používají jazykové služby a. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Jazyková služba, která spravuje vlastní osnovu, monitoruje obsah textové vyrovnávací paměti, aby zničila staré oblasti osnovy, když se stanou neplatnými, a podle potřeby vytvořila nové oblasti osnovy.

### <a name="to-implement-a-client-controlled-outline-region"></a>Implementace oblasti osnovy řízené klientem

1. Výzva `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>pro . To vrátí ukazatel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>na .

2. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, předávání ukazatele pro daný text vyrovnávací paměti. To určuje, zda relace skrytého textu již existuje pro vyrovnávací paměť.

3. Pokud textová relace již existuje, není nutné ji vytvářet a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> je vrácen ukazatel na existující objekt. Tento ukazatel slouží k vytvoření výčtu a vytvoření oblastí osnovy. V opačném <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> případě volání vytvořit skryté textové relace pro vyrovnávací paměť. Je vrácen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> ukazatel na objekt.

    > [!NOTE]
    > Při volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>můžete určit skrytétextového klienta (to znamená <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objekt). Tento klient vás upozorní, když je skrytý text nebo oblast osnovy rozbalen nebo sbalen uživatelem.

4. Call <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> structure) parametr: Zadejte <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> `iType` hodnotu <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> v člen u člena struktury k označení, že vytváříte oblast osnovy, nikoli skrytou oblast. Určete, zda je oblast řízena klientem nebo editorem v `dwBehavior` členu <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Implementace inteligentního osnovy může obsahovat kombinaci oblastí osnovy řízených editorem a klientem. Zadejte text nápisu, který se zobrazí při sbalení oblasti osnovy, například "...", v `pszBanner` členu <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Výchozí text banneru editoru pro skrytou oblast je "...".
