---
title: Zarážky (Visual Studio SDK) | Microsoft Docs
description: 'Přečtěte si o třech typech zarážek: nevyřízené, vázané a chybové. Tento článek obsahuje seznam rozhraní použitých k implementaci typů.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa9f244ec60e336e9a7596ff839842211d516b7d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930808"
---
# <a name="breakpoints-visual-studio-sdk"></a>Zarážky (Visual Studio SDK)
Existují tři typy zarážek: nevyřízené, vázané a chybové.

 **Nevyřízená zarážka:**

- Je abstrakcí, která obsahuje všechny informace potřebné k navázání zarážky na jeden nebo více kontextů kódu v jednom nebo více programech. Pokaždé, když je program, který se ladí, načetl kód příčiny, modul ladění zkontroluje všechny probíhající zarážky a zjistí, jestli se dají svázat.

   Nevyřízená zarážka sama o sobě nikdy neváže na kód, ale místo toho shromažďuje a je označována tak, aby obsahovala všechny vázané zarážky, které generuje.

- Je reprezentován rozhraním [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

  **Vázaná zarážka:**

- Je abstrakcí pro zarážku, která je přidružena k jednomu kontextu kódu nebo svázána s nimi. Každá vázaná zarážka je vygenerována v reakci na nevyřízenou zarážku. Nevyřízená zarážka může však generovat více než jednu vázanou zarážku.

   Když je kód uvolněný, může být vázaná zarážka nevázaná a zahozena.

- Je reprezentován rozhraním [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

  **Zarážka chyby:**

- Je abstrakcí pro popis chyby při pokusu o vytvoření vazby na nevyřízenou zarážku na kontext kódu. Chybná zarážka popisuje buď chybu v umístění, nebo samotný výraz zarážky. Další informace naleznete v tématu [vázání zarážek](../../extensibility/debugger/binding-breakpoints.md).

   Chyba zarážky může být buď chyba, nebo upozornění.

- Je reprezentován rozhraním [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

## <a name="see-also"></a>Viz také
- [Programy](../../extensibility/debugger/programs.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [Kontext kódu](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
