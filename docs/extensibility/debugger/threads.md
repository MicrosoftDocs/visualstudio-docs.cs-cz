---
title: Vlákna | Microsoft Docs
description: Tento článek popisuje definici a roli vlákna v architektuře ladicího programu v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc745a4361c0935896048bbf72a4084f007ecf7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905732"
---
# <a name="threads"></a>Vlákna
V architektuře ladicího programu *vlákno*:

- Je základní výpočetní jednotkou. Vlákno postupně provádí své instrukce v kontextu jednoho zásobníku volání a přecházuje z jednoho kontextu kódu na další.

- Dokáže identifikovat sebe a program, ve které běží. Vlákna mohou být pojmenována, pozastavena a obnovena. Vlákno může také vytvořit výčet přidružených rámců zásobníku a za určitých podmínek může být přesunuto do jiného rámce zásobníku. Vzhledem k kontextu rámce zásobníku může vlákno vrátit přidružené logické vlákno, pokud je k dispozici. Vlákno má vlastnosti, například počet pozastavení, které lze zobrazit v **okně Vlákna** integrovaného vývojového prostředí.

- Je reprezentováno [rozhraním IDebugThread2,](../../extensibility/debugger/reference/idebugthread2.md) obvykle vytvořeným ladicím strojem (DE) nebo virtuálním strojem v důsledku spuštění programu.

## <a name="see-also"></a>Viz také
- [Programy](../../extensibility/debugger/programs.md)
- [Rámce zásobníku](../../extensibility/debugger/stack-frames.md)
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [Správce ladění relací](../../extensibility/debugger/session-debug-manager.md)
