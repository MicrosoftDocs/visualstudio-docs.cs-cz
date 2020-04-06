---
title: Určení stavu příkazu pomocí sestavení interop | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 52bea32997b083cd13349a37201411e357f94a90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708702"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Určení stavu příkazu pomocí mezioperačních sestavení
VSPackage musí sledovat stav příkazů, které může zpracovat. Prostředí nemůže určit, kdy se příkaz zpracovaný v rámci balíčku VSPackage stane povoleným nebo zakázaným. Je odpovědností vspackage informovat prostředí o stavech příkazů, například stav obecných příkazů, jako je **vyjmout**, **kopírovat**a **vložit**.

## <a name="status-notification-sources"></a>Zdroje oznámení o stavu
 Prostředí přijímá informace o příkazech prostřednictvím <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody VSPackages, která je součástí implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní VSPackage. Prostředí volá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu VSPackage za dvou podmínek:

- Když uživatel otevře hlavní nabídku nebo místní nabídku (kliknutím pravým <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> tlačítkem myši), prostředí provede metodu na všechny příkazy v této nabídce k určení jejich stavu.

- Když VSPackage požaduje, aby prostředí aktualizovat aktuální uživatelské rozhraní (UI). K této aktualizaci dochází jako příkazy, které jsou aktuálně viditelné pro uživatele, například **Vyjmout**, **Kopírovat**a **Vložit** seskupení na standardní panel nástrojů, stanou se povolenými a zakázanými v reakci na kontext a akce uživatele.

  Vzhledem k tomu, že prostředí hostuje více VSPackages, výkon prostředí by nepřijatelně snížit, pokud by bylo nutné dotazování každý VSPackage k určení stavu příkazu. Místo toho vspackage by měl aktivně upozornit prostředí při změně jeho ui v době změny. Další informace o oznámení o aktualizaci naleznete [v tématu Aktualizace uživatelského rozhraní](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Selhání oznámení o stavu
 Selhání vašeho VSPackage upozornit prostředí změny stavu příkazu může umístit ui v nekonzistentním stavu. Nezapomeňte, že kterýkoli z příkazů nabídky nebo kontextové nabídky může uživatel umístit na panel nástrojů. Aktualizace ui pouze při otevření nabídky nebo kontextové nabídky proto nestačí.

## <a name="see-also"></a>Viz také
- [Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementace](../../extensibility/internals/command-implementation.md)
