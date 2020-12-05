---
title: Programy | Microsoft Docs
description: Tento článek popisuje definice a roli programu v architektuře ladicího programu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf0d3adb174e9b13cb09f9506927217326890c32
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606512"
---
# <a name="programs"></a>Programy
V architektuře ladicího programu *program*:

- Je kontejner pro sadu vláken i sadu modulů. Program nemá v operačním systému Windows žádnou jednoduchou analogii.

     Program je druh podprocesu. Například při ladění webu se skript může zobrazit jako program. Zatímco skript běží v procesu skriptovacího modulu, nezávisle na ostatních skriptech, má také svou vlastní sadu vláken. Ladicí stroj (DE) se připojí k programu, nikoli k procesu nebo vláknu.

- Může identifikovat sebe sama a proces, ve kterém je spuštěný. Program může být připojen k, odpojen od a popište DE, který ho vytvořil, pokud nějaký existuje. Program lze také spustit, zastavit, pokračovat a ukončit.

- Může vytvořit výčet všech jeho vláken. Program může také dodat svůj vlastní zpětný proud zpětného překladu a může vytvořit výčet všech kontextů kódu dané pozice dokumentu.

- Je reprezentován rozhraním [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , vytvořené před připojením programu, nebo jako součást procesu připojení v závislosti na implementaci. Když port vytvoří výčet programů procesu, každý program se vytvoří v souladu s odpovídajícím rozhraním [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , které se předává jako argument pro [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). I když moduly ladění také vytváří `IDebugProgram2` rozhraní, která představují programy, tyto programy se nevytvoří v souladu s uzlem programu. `IDebugProgramNode2`Rozhraní vytvořená nástrojem de se používají pro vlastní ladění, zatímco ta vytvořená portem se používají pouze pro zjišťování, které programy jsou spuštěny v procesu.

## <a name="see-also"></a>Viz také
- [Procesy](../../extensibility/debugger/processes.md)
- [Uzly programu](../../extensibility/debugger/program-nodes.md)
- [Moduly](../../extensibility/debugger/modules.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [Ladicí stroj](../../extensibility/debugger/debug-engine.md)
- [Pozice dokumentu](../../extensibility/debugger/document-position.md)
- [Kontext kódu](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
