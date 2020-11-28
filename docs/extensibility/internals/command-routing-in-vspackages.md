---
title: Směrování příkazů v VSPackage | Microsoft Docs
description: Přečtěte si o směrování příkazů v rozhraních VSPackage a způsobu směrování příkazů na základě kontextu, ve kterém jsou spouštěny v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8168fbe3ad5ba9b1b332aebc4675ecd8e752ee7e
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305215"
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
