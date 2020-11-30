---
title: Určení stavu příkazu pomocí definičních sestavení | Microsoft Docs
description: Naučte se určit stav příkazů, které jsou zpracovány v VSPackage, pomocí rozhraní Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget –.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e46252cea550a2caaa81c92853220db4fa2b5b1a
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328376"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Určení stavu příkazu pomocí definičních sestavení
VSPackage musí sledovat stav příkazů, které může zpracovat. Prostředí nemůže určit, kdy se má příkaz, který je zpracován v rámci rozhraní VSPackage, aktivovat nebo zakázat. Je zodpovědností vaší sady VSPackage o informování prostředí o stavech příkazů, například o stavu obecných příkazů, jako je například **vyjmutí**, **kopírování** a **vložení**.

## <a name="status-notification-sources"></a>Zdroje oznámení o stavu
 Prostředí přijímá informace o příkazech prostřednictvím <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody VSPackage, která je součástí implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní VSPackage. Prostředí volá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu VSPackage za dvou podmínek:

- Když uživatel otevře hlavní nabídku nebo kontextovou nabídku (kliknutím pravým tlačítkem myši), prostředí spustí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu pro všechny příkazy v této nabídce k určení jejich stavu.

- Když rozhraní VSPackage požaduje, aby prostředí aktualizovalo aktuální uživatelské rozhraní (UI). Tato aktualizace probíhá jako příkazy, které jsou aktuálně viditelné pro uživatele, například pro **vyjmutí**, **kopírování** a **vložení** na standardním panelu nástrojů, v reakci na akce kontextu a uživatele se aktivuje a zakáže.

  Vzhledem k tomu, že prostředí hostuje víc VSPackage, výkon tohoto prostředí by nepřijatelně snížil, pokud by byl potřebný k dotazování jednotlivých VSPackage na zjištění stavu příkazu. Místo toho by měl váš VSPackage aktivně upozorňovat prostředí, když se změní uživatelské rozhraní v době změny. Další informace o oznámení o aktualizacích najdete v tématu [aktualizace uživatelského rozhraní](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Selhání oznámení o stavu
 Selhání balíčku VSPackage pro oznámení prostředí změny stavu příkazu může umístit uživatelské rozhraní do nekonzistentního stavu. Mějte na paměti, že uživatel může umístit všechny příkazy nabídky nebo kontextové nabídky na panel nástrojů. Proto se aktualizace uživatelského rozhraní aktualizuje jenom v případě, že se otevře nabídka nebo místní nabídka není dostatečná.

## <a name="see-also"></a>Viz také
- [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementace](../../extensibility/internals/command-implementation.md)
