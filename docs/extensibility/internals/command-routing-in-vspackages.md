---
title: Směrování příkazů v VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 957ddcca46365a882609c15c96d666c2848ace6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709557"
---
# <a name="command-routing-in-vspackages"></a>Směrování příkazů v VSPackage
Příkaz je směrován v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] závislosti na kontextu, ve kterém je proveden. Je směrován z počátečního kontextu směrem ven do globálního kontextu.

## <a name="in-this-section"></a>V této části
- [Algoritmus směrování příkazů](../../extensibility/internals/command-routing-algorithm.md)

 Popisuje pořadí řešení směrování příkazů.

- [Dostupnost příkazu](../../extensibility/internals/command-availability.md)

 Popisuje směrování příkazů.

- [Příkazy a nabídky používající definiční sestavení](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Popisuje okolnosti při směrování příkazů mezi spravovaným kódem a COM.

## <a name="related-sections"></a>Související oddíly
- [Objekty kontextu výběru](../../extensibility/internals/selection-context-objects.md)

 Popisuje model, jak lze určit fokus kontextu výběru uživatele v okně.

- [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)

 Vysvětluje, jak vytvořit uživatelské rozhraní, které obsahuje nabídky, panely nástrojů a pole se seznamem příkazů.
