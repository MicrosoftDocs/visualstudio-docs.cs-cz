---
title: Vlákna | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712482"
---
# <a name="threads"></a>Vlákna
V architektuře ladicího programu, *vlákno*:

- Je základní jednotkou výpočtu. Vlákno postupně provede své pokyny v rámci kontextu jediného zásobníku volání, přechod z jednoho kontextu kódu na další.

- Může identifikovat sebe sama a program, ve kterém je spuštěný. Vlákna mohou být pojmenována, pozastavena a obnovena. Vlákno může také vytvořit výčet přidružených rámců zásobníku a za určitých podmínek lze přesunout do jiného rámce zásobníku. Vzhledem k kontextu bloku zásobníku může vlákno vracet své přidružené logické vlákno, pokud existuje. Vlákno má vlastnosti, jako je například počet pozastavení, které lze zobrazit v okně **vláken** rozhraní IDE.

- Je reprezentován rozhraním [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , obvykle vytvořené modulem ladění (de) nebo virtuálním počítačem jako v důsledku provádění programu.

## <a name="see-also"></a>Viz také
- [Programy](../../extensibility/debugger/programs.md)
- [Rámce zásobníku](../../extensibility/debugger/stack-frames.md)
- [Ladicí stroj](../../extensibility/debugger/debug-engine.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [Správce ladění relace](../../extensibility/debugger/session-debug-manager.md)
