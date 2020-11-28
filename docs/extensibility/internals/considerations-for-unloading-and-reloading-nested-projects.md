---
title: Uvolnění a opětovné načtení vnořených projektů
description: Přečtěte si další kroky, které je třeba provést při uvolňování a opětovném načítání vnořených projektů v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 62cb611e927b878b82e1b5a1025331e1a443560e
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304676"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Předpoklady pro uvolnění a opětovné načtení vnořených projektů

Při implementaci vnořených typů projektů je nutné provést další kroky při uvolňování a opětovném načtení projektů. Pro správné upozornění posluchačů na události řešení je nutné správně vyvolat `OnBeforeUnloadProject` události a `OnAfterLoadProject` .

Jedním z důvodů, jak tyto události vyvolat, je Správa zdrojového kódu (SCC). Nechcete, aby SCC odstranil položky ze serveru, a pak je přidat zpátky jako *nové* , pokud existuje `Get` operace z SCC. V takovém případě by byl nový soubor načten z SCC. Je nutné uvolnit a znovu načíst všechny soubory v případě, že se liší.

Volání správy zdrojového kódu `ReloadItem` . Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> rozhraní, které se má volat `OnBeforeUnloadProject` , a `OnAfterLoadProject` odstraňte projekt a vytvořte ho znovu. Při implementaci rozhraní tímto způsobem je SCC informován o tom, že projekt byl dočasně odstraněn a přidán znovu. Proto SCC nefunguje na projektu, jako kdyby byl projekt *skutečně* odstraněný a znovu přidaný.

## <a name="reload-projects"></a>Znovu načíst projekty

Pro podporu opětovného načtení vnořených projektů implementujete <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodu. V implementaci nástroje `ReloadItem` zavřete vnořené projekty a pak je znovu vytvořte.

Obvykle při opětovném načtení projektu rozhraní IDE vyvolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> události a. Pro vnořené projekty, které jsou odstraněny a znovu načteny, však nadřazený projekt zahájí proces, nikoli rozhraní IDE. Vzhledem k tomu, že nadřazený projekt nevyvolává události řešení a rozhraní IDE neobsahuje žádné informace o inicializaci procesu, události nejsou vyvolány.

Pro zpracování tohoto procesu nadřízený projekt volá `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> rozhraní. `IVsFireSolutionEvents` má funkce, které instruují rozhraní IDE, aby vyvolalo `OnBeforeUnloadProject` událost pro uvolnění vnořeného projektu, a poté vyvolá `OnAfterLoadProject` událost pro opětovné načtení stejného projektu.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Vnořit projekty](../../extensibility/internals/nesting-projects.md)
