---
title: Poskytování podpory skrytých textů ve službě starší verze jazyka
description: Přečtěte si, jak poskytnout podporu skrytého textu ve službě starší verze jazyka přidáním textových oblastí řízených pomocí editoru nebo klientů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0c4951e1f3fbaf63bf0638965a7dee2db7be8830
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965249"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Postupy: poskytování podpory skrytého textu ve službě starší verze jazyka
Kromě oblastí obrysů můžete vytvářet i skryté oblasti textu. Skryté textové oblasti mohou být řízeny klientem nebo editorem a používají se k úplnému skrytí oblasti textu. Editor zobrazuje skrytou oblast jako vodorovné čáry. Příkladem je zobrazení **pouze skriptu** v editoru HTML.

## <a name="to-implement-a-hidden-text-region"></a>Implementace skryté oblasti textu

1. Volání `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Tím se vrátí ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> a předejte ukazatel pro danou textovou vyrovnávací paměť. Tato možnost určuje, zda již pro vyrovnávací paměť existuje relace skrytého textu.

3. Pokud již existuje, nemusíte ho vytvářet a ukazatel na stávající <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objekt je vrácen. Tento ukazatel použijte k zobrazení výčtu a vytvoření oblastí skrytého textu. V opačném případě zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> k vytvoření skryté textové relace pro vyrovnávací paměť.

     Vrátí se ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objekt.

    > [!NOTE]
    > Při volání `CreateHiddenTextSession` můžete zadat klienta skrytého textu (tj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> .). Klient skrytého textu vás upozorní, když uživatel rozbalí skrytý text nebo sbalení.

4. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> za účelem přidání jedné nebo více nových oblastí osnovy současně a zadáním následujících informací v `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> parametru ():

    1. Zadejte hodnotu `hrtConcealed` v `iType` členu <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury, abyste označili, že vytváříte skrytou oblast, nikoli oblast osnovy.

        > [!NOTE]
        > Když jsou skryté oblasti skryté, Editor automaticky zobrazuje čáry kolem skrytých oblastí, aby označovali jejich přítomnost.

    2. Určete, zda se jedná o oblast řízenou klientem nebo editorem v rámci `dwBehavior` členů <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Vaše implementace inteligentního vkládání se může skládat z kombinace osnovy a oblastí s skrytým textem v editoru a na straně klienta.
