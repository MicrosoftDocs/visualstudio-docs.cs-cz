---
title: Zarážky (Sada Visual Studio SDK) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739187"
---
# <a name="breakpoints-visual-studio-sdk"></a>Zarážky (Visual Studio SDK)
Existují tři typy zarážek: čekající, vázané a chyby.

 **Čekající zarážka:**

- Je abstrakce, která obsahuje všechny informace potřebné k vytvoření vazby zarážky na jeden nebo více kontextů kódu v jednom nebo více programech. Pokaždé, když program je laděný způsobit kód načíst, ladicí modul zkontroluje všechny čekající zarážky, zda mohou být vázány.

   Čekající zarážka sama nikdy váže na kód, ale spíše shromažďuje a je řekl, aby obsahoval všechny vázané zarážky, které generuje.

- Je reprezentován [rozhraním IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

  **Vázaná zarážka:**

- Je abstrakce pro zarážku přidružené nebo vázané na jeden kontext kódu. Každá vázaná zarážka je generována v reakci na čekající zarážku. Čekající zarážka však může generovat více než jednu vázanou zarážku.

   Při uvolnění kódu může být vázaná zarážka nevázaná a zahozená.

- Je reprezentován [rozhraním IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

  **Zarážka chyby:**

- Je abstrakce pro popis chyby při pokusu o vytvoření vazby čekající zarážky na kontext kódu. Zarážka chyby popisuje chybu v umístění nebo ve samotném výrazu zarážky. Další informace naleznete v [tématu Zarážky vazby](../../extensibility/debugger/binding-breakpoints.md).

   Chyba zarážky může být chyba nebo upozornění.

- Je reprezentován rozhraním [IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

## <a name="see-also"></a>Viz také
- [Programy](../../extensibility/debugger/programs.md)
- [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md)
- [Kontext kódu](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
