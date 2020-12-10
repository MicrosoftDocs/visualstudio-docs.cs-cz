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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b259ffd7814b42145489ee5990cee6da891a9d10
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995951"
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
