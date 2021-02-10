---
title: Vlákna | Microsoft Docs
description: Tento článek popisuje definice a roli vlákna v architektuře ladicího programu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec3c427e722739f17984866b8756d606ecb57813
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965457"
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
