---
title: Kontrakty příkazů v sestaveních Interop | Microsoft Docs
description: Přečtěte si základní kontrakt pro zpracování příkazů prostřednictvím rozhraní Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget –.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 36c757faacb7fe3193f9acbbd040468f66b0623a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086050"
---
# <a name="command-contracts-in-interop-assemblies"></a>Kontrakty příkazů v sestaveních spolupráce
Základní kontrakt pro zpracování příkazů prostřednictvím <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní je, že prostředí volá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu k určení, zda je příkaz podporován a pokud je podporován, k určení jeho stavu a textu. Prostředí pak zavolá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodu pro provedení příkazu.

 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>Metoda je zpracována identicky pro všechny příkazy. Další komunikace, v případě potřeby (například s rozevíracími seznamy), je spravována voláním <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody s příslušnými parametry. Interpretace těchto parametrů závisí na zadaném příkazu.

 Pokud cílový příkaz vrátí hodnoty v parametru Output, volající je vždy zodpovědný za uvolnění všech prostředků, které byly přiděleny. Vzhledem k tomu, že tento parametr je typu variant, vymazání variant uvolňuje prostředky.

 V případech, kdy příkazy musí fungovat v rámci okna hierarchie, je <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> nutné použít rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Rozhraní má podobnou kontrakt s podobnými metodami: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

## <a name="see-also"></a>Viz také
- [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Směrování příkazů v VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implementace příkazu](../../extensibility/internals/command-implementation.md)
