---
title: Programy | Microsoft Docs
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
ms.openlocfilehash: d3fd1db5add74d2d94467e1f369916feb5f30d4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738206"
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
