---
title: Rámy zásobníku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ea79ad199e20afeb5d2bf1ca6a3cf881c6d51c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712845"
---
# <a name="stack-frames"></a>Stohovat rámce
V architektuře ladicího programu *je rám zásobníku*:

- Je abstrakce zásobníku, který poskytuje kontext spuštění podprocesu. Vlákno se vždy spustí v rámci funkce. Rámec zásobníku obsahuje místní proměnné funkce a argumenty k němu. Chcete-li ladit s Visual Studio, jazyk nebo prostředí, které jsou laděny musí podporovat rámce zásobníku.

- Může identifikovat a popsat sám sebe a může vrátit přidružené vlákno. Rámec zásobníku můžete také vrátit kontext kódu, který představuje aktuální ukazatel instrukce a přidružené dokumentace a kontextu vyhodnocení výrazu.

- Má vlastnosti, které popisují název, typ a hodnotu místních proměnných a argumentů a které se zobrazují v různých oknech ladění ide.

- Je reprezentován [rozhraní MDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) obvykle vytvořené ladicí modul (DE) nebo virtuální počítač v důsledku provádění podprocesu.

## <a name="see-also"></a>Viz také
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
- [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md)
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
