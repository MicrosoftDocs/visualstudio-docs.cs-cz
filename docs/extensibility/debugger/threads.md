---
title: Vlákna | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ed5c06e0c42dac1f0539cc2c7c5886d95b23ae1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712482"
---
# <a name="threads"></a>Vlákna
V architektuře ladicího programu *vlákno*:

- Je základní jednotkou výpočtu. Podproces postupně provádí své pokyny v rámci jednoho zásobníku volání, přesunutí z jednoho kontextu kódu do dalšího.

- Dokáže identifikovat sebe a program, ve který běží. Vlákna mohou být pojmenována, pozastavena a obnovena. Vlákno může také vytvořit výčet jeho přidružené rámce zásobníku a za určitých podmínek lze přesunout do jiného rámce zásobníku. Vzhledem k kontextu rámce zásobníku může vlákno vrátit jeho přidružené logické vlákno, pokud existuje. Podproces má vlastnosti, jako je například počet pozastavení, které mohou být zobrazeny v okně **Vlákna** rozhraní IDE.

- Je reprezentován rozhraní [MDebugThread2,](../../extensibility/debugger/reference/idebugthread2.md) obvykle vytvořené ladicí modul (DE) nebo virtuální počítač v důsledku spuštění programu.

## <a name="see-also"></a>Viz také
- [Programy](../../extensibility/debugger/programs.md)
- [Stohovat rámce](../../extensibility/debugger/stack-frames.md)
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md)
- [Správce ladění relace](../../extensibility/debugger/session-debug-manager.md)
