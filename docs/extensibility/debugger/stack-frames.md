---
title: Rámce zásobníku | Microsoft Docs
description: Tento článek popisuje definice a roli rámce zásobníku v architektuře ladicího programu v sadě Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77b503afcc38ab9427e5268097655433007de5d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898549"
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
