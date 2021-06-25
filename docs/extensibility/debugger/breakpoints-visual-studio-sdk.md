---
title: Zarážky (Visual Studio SDK) | Microsoft Docs
description: 'Seznamte se se třemi typy zarážek: čekající, vázané a chybové. Tento článek uvádí rozhraní používaná k implementaci typů.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1fce472faf95aa77f87ab02d78a3da640b6bd3bf
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901484"
---
# <a name="breakpoints-visual-studio-sdk"></a>Zarážky (Visual Studio SDK)
Existují tři typy zarážek: čekající, vázané a chybové.

 **Čekající zarážka:**

- Je abstrakce, která obsahuje všechny informace potřebné k vytvoření vazby zarážky k jednomu nebo více kontextům kódu v jednom nebo více programech. Pokaždé, když laděné programy způsobí načtení kódu, ladicí modul zkontroluje všechny čekající zarážky a zjistí, jestli je možné je svázané.

   Samotná čekající zarážka se nikdy neváže na kód, ale spíše shromažďuje a je říká se, že obsahuje všechny vázané zarážky, které generuje.

- Je reprezentováno [rozhraním IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

  **Vázané zarážky:**

- Je abstrakcí pro zarážku přidruženou k jednomu kontextu kódu nebo s ním spojený. Každá vázaný zarážka se generuje v reakci na čekající zarážku. Čekající zarážka však může generovat více než jednu vázané zarážky.

   Při uvolnění kódu může být vázané zarážky nevázané a zahozené.

- Je reprezentováno [rozhraním IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

  **Chybová zarážka:**

- Je abstrakcí pro popis chyby při pokusu o vytvoření vazby čekající zarážky k kontextu kódu. Chybová zarážka popisuje chybu v umístění nebo v samotném výrazu zarážky. Další informace najdete v tématu [Vytváření vazeb zarážek](../../extensibility/debugger/binding-breakpoints.md).

   Chyba zarážky může být buď chyba, nebo upozornění.

- Je reprezentováno [rozhraním IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

## <a name="see-also"></a>Viz také
- [Programy](../../extensibility/debugger/programs.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [Kontext kódu](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
