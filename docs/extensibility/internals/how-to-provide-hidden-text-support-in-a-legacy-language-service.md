---
title: Poskytování skryté textové podpory ve službě starších jazyků
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707928"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Postup: Poskytnutí skryté textové podpory ve službě starších jazyků
Kromě oblastí osnovy můžete vytvořit skryté oblasti textu. Oblasti skrytého textu lze řídit klientem nebo editorem a slouží k úplnému skrytí oblasti textu. Editor zobrazí skrytou oblast jako vodorovné čáry. Příkladem je zobrazení **Pouze skript v** editoru HTML.

## <a name="to-implement-a-hidden-text-region"></a>Implementace oblasti skrytého textu

1. Výzva `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>pro .

     To vrátí ukazatel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>na .

2. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, předávání ukazatele pro daný text vyrovnávací paměti. To určuje, zda relace skrytého textu již existuje pro vyrovnávací paměť.

3. Pokud jeden již existuje, není nutné jej vytvořit a je <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> vrácen ukazatel na existující objekt. Tento ukazatel slouží k vytvoření výčtu a vytvoření skrytých oblastí textu. V opačném <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> případě volání vytvořit skryté textové relace pro vyrovnávací paměť.

     Je vrácen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> ukazatel na objekt.

    > [!NOTE]
    > Při volání `CreateHiddenTextSession`můžete zadat skrytého textového klienta (to znamená). <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> Klient skrytého textu vás upozorní, když je skrytý text nebo osnova rozbalena nebo sbalena uživatelem.

4. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> pro přidání jedné nebo více nových oblastí osnovy najednou `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>a zadání následujících informací v parametru ( :

    1. Zadejte hodnotu `hrtConcealed` `iType` v <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> členu struktury, která označuje, že vytváříte skrytou oblast, nikoli oblast osnovy.

        > [!NOTE]
        > Pokud jsou skryté oblasti skryté, editor automaticky zobrazí řádky kolem skrytých oblastí, které označují jejich přítomnost.

    2. Určete, zda je oblast řízena klientem nebo editorem v `dwBehavior` členech <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Implementace inteligentního osnovy může obsahovat kombinaci oblastí osnovy řízených editorem a klientem a skrytých textových oblastí.
