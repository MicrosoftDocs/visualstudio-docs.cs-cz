---
title: Příkaz smlouvy v interop sestavení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f20a4f479d62cd1b64c3b13ff6e1a949656a668
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709677"
---
# <a name="command-contracts-in-interop-assemblies"></a>Příkazové kontrakty v interop sestaveních
Základní smlouva pro zpracování příkazů <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> prostřednictvím rozhraní je, že prostředí volá metodu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> k určení, zda je příkaz podporován a pokud je podporován, k určení jeho stavu a textu. Potom prostředí volá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodu ke spuštění příkazu.

 Metoda <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> je zpracována stejně pro všechny příkazy. Další komunikace, v případě potřeby (například s rozevíracíseznamy), je řízena voláním <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody s příslušnými parametry. Interpretace těchto parametrů závisí na zadaném příkazu.

 Pokud cíl příkazu vrátí hodnoty ve výstupním parametru, volající je vždy zodpovědný za uvolnění všech prostředků, které byly přiděleny. Vzhledem k tomu, že tento parametr je varianta, vymazání varianty uvolní prostředky.

 V případech, kdy příkazy musí pracovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> v okně hierarchie, rozhraní musí být použit. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> má podobnou smlouvu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> s <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>podobnými metodami: a .

## <a name="see-also"></a>Viz také
- [Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Směrování příkazů v balíčcích VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implementace příkazu](../../extensibility/internals/command-implementation.md)
