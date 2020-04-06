---
title: Důležité informace pro uvolnění a opětovné načtení vnořených projektů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab705953eea1fcac99883bb4f88c0e95eced108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709293"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Důležité informace pro uvolnění a opětovné načtení vnořených projektů

Při implementaci vnořených typů projektů je nutné provést další kroky při uvolnění a opětovném načtení projektů. Chcete-li správně upozornit posluchače na události `OnBeforeUnloadProject` `OnAfterLoadProject` řešení, musíte správně vyvolat události a.

Jedním z důvodů pro zvýšení těchto událostí je pro slučování zdrojového kódu (SCC). Nechcete, aby SCC odstranit položky ze serveru a pak je přidat `Get` zpět jako *nové,* pokud je operace z SCC. V takovém případě by byl načten nový soubor z SCC. Museli byste vyložit a znovu načíst všechny soubory pro případ, že by se lišily.

Volání `ReloadItem`správy zdrojového kódu . Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> rozhraní `OnBeforeUnloadProject` pro `OnAfterLoadProject` volání a odstranění projektu a znovu jej vytvořte. Při implementaci rozhraní tímto způsobem SCC je informován, že projekt byl dočasně odstraněn a znovu přidán. Proto SCC nefunguje na projektu, jako kdyby byl projekt *skutečně* odstraněn a znovu přidán.

## <a name="reload-projects"></a>Znovu načíst projekty

Chcete-li podporovat překládku vnořených projektů, implementujte metodu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Při implementaci `ReloadItem`aplikace zavřete vnořené projekty a potom je znovu vytvořte.

Obvykle při opětovném načtení projektu ide <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> vyvolá události a. Však pro vnořené projekty, které jsou odstraněny a znovu načíst nadřazený projekt iniciuje proces, nikoli IDE. Vzhledem k tomu, že nadřazený projekt nevyvolává události řešení a ide nemá žádné informace o inicializaci procesu, události nejsou vyvolány.

Chcete-li zpracovat tento `QueryInterface` proces, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> nadřazený projekt volá rozhraní. `IVsFireSolutionEvents`má funkce, které sdělují ide vyvolat `OnBeforeUnloadProject` událost k uvolnění `OnAfterLoadProject` vnořený projekt a potom zvýšit událost znovu načíst stejný projekt.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Projekty vnoření](../../extensibility/internals/nesting-projects.md)
