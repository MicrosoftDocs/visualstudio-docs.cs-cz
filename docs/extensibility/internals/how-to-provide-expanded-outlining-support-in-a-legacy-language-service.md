---
title: Poskytnutí podpory sbalení ve službě jazyka | Microsoft Docs
description: Přečtěte si, jak poskytnout rozšířenou podporu sbalení ve službě starší verze jazyka tím, že přidáváte oblasti osnovy se spravovanými editory a oblasti osnovy řízené klienty.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3db7c4f886a071b4b759072a1b141690f4e4b097
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890718"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Postupy: poskytování rozšířené podpory sbalení ve službě starší verze jazyka
Existují dvě možnosti, jak rozšířit podporu osnovy pro váš jazyk nad rámec podpory příkazu **sbalit na definice** . Můžete přidat oblasti osnovy řízené editorem a přidat oblasti osnovy řízené klientem.

## <a name="adding-editor-controlled-outline-regions"></a>Přidávání oblastí obrysů řízených editorem
 Použijte tento přístup k vytvoření oblasti osnovy a pak umožněte, aby Editor zpracoval, zda je oblast rozbalená, sbalená a tak dále. Z těchto dvou možností pro zajištění podpory sbalení je tato možnost nejméně robustní. Pro tuto možnost vytvoříte novou oblast osnovy přes zadaný rozsah textu pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> . Po vytvoření této oblasti je chování řízeno editorem. K implementaci oblastí obrysu řízených pomocí editoru použijte následující postup.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Implementace oblasti osnovy řízené editorem

1. Volání `QueryService` pro <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Tím se vrátí ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> a předejte ukazatel pro danou textovou vyrovnávací paměť. Tím se vrátí ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objekt pro vyrovnávací paměť.

3. Zavolejte <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> pro ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> .

4. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> na přidání jedné nebo více nových oblastí osnovy najednou.

     Tato metoda umožňuje zadat rozsah textu, který se má obrysem, zda jsou existující oblasti osnovy odebrány nebo zachované a zda je oblast osnovy ve výchozím nastavení rozbalená nebo sbalená.

## <a name="add-client-controlled-outline-regions"></a>Přidat oblasti osnovy řízené klientem
 Tento postup použijte k implementaci sbalení spravovaného na straně klienta (nebo inteligentního), jako je to, které používají [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] jazykové služby a. Služba jazyka, která spravuje vlastní osnovu, monitoruje obsah vyrovnávací paměti textu, aby se zničily staré oblasti obrysu, když se stanou neplatnými a podle potřeby vytvořily nové oblasti osnovy.

### <a name="to-implement-a-client-controlled-outline-region"></a>Implementace oblasti osnovy řízené klientem

1. Volání `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Tím se vrátí ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> a předejte ukazatel pro danou textovou vyrovnávací paměť. Tato možnost určuje, zda již pro vyrovnávací paměť existuje relace skrytého textu.

3. Pokud již relace textu existuje, nemusíte ji vytvářet a je vrácen ukazatel na existující <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objekt. Pomocí tohoto ukazatele můžete vytvořit výčet a vytvořit oblasti osnovy. V opačném případě zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> k vytvoření skryté textové relace pro vyrovnávací paměť. Vrátí se ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objekt.

    > [!NOTE]
    > Při volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> můžete zadat klienta skrytého textu (tj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> . objekt). Tento klient vás upozorní, když uživatel rozbalí skrytý text nebo oblast osnovy a uživatel ho sbalí.

4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>Structure – parametr): zadejte hodnotu <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> v `iType` členu <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury, abyste označili, že vytváříte oblast obrysu místo skryté oblasti. Určete, zda je oblast řízena klientem nebo editorem řízená v `dwBehavior` členovi <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Vaše implementace inteligentního vkládání se může skládat z kombinace oblastí osnovy řízených editorem a klientem. Určuje text banneru zobrazený při sbalení oblasti osnovy, jako je například "..." v `pszBanner` členu <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Výchozí text banneru v editoru pro skrytou oblast je "...".
