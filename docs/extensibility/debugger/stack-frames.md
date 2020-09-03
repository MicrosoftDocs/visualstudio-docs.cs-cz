---
title: Rámce zásobníku | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712845"
---
# <a name="stack-frames"></a>Rámce zásobníku
V architektuře ladicího programu, *rámec zásobníku*:

- Je abstrakcí zásobníku, který poskytuje kontext spuštění vlákna. Vlákno se vždy provádí v rámci funkce. Rámec zásobníku obsahuje místní proměnné funkce a argumenty. Aby bylo možné ladit v sadě Visual Studio, jazyk nebo prostředí, které je laděno, musí podporovat rámce zásobníku.

- Může identifikovat a popsat sám sebe a může vrátit přidružené vlákno. Rámec zásobníku může také vracet kontext kódu, který představuje aktuální ukazatel na instrukci a přidruženou dokumentaci a kontext vyhodnocení výrazu.

- Obsahuje vlastnosti, které popisují název, typ a hodnotu místních proměnných a argumentů a které se zobrazují v různých oknech ladění IDE.

- Je reprezentován rozhraním [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , obvykle vytvořené modulem ladění (de) nebo virtuálním počítačem jako v důsledku provádění vlákna.

## <a name="see-also"></a>Viz také
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [Ladicí stroj](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
