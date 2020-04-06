---
title: Programy | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738206"
---
# <a name="programs"></a>Programy
V architektuře ladicího programu *program*:

- Je kontejner pro sadu podprocesů a sadu modulů. Program nemá v operačním systému Windows žádnou analogii.

     Program je druh dílčího procesu. Například při ladění webu skript lze považovat za program. Zatímco skript běží v procesu skriptovacího stroje, nezávisle na jiných skriptech, má také vlastní sadu vláken. Ladicí modul (DE) se připojí k programu, nikoli k procesu nebo vláknu.

- Dokáže se identifikovat a proces, ve kterých běží. Program lze připojit, odpojit od a popsat DE, který jej vytvořil, pokud existuje. Program může také spustit, zastavit, pokračovat a být ukončen.

- Můžete výčet všech jeho podprocesů. Program může také zadat vlastní datový proud demontáže a může vytvořit výčet všech kontextů kódu dané pozice dokumentu.

- Je reprezentován [rozhraním IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) vytvořené před připojením programu nebo jako součást procesu připojení, v závislosti na implementaci. Když port vytvoří výčet programů procesu, každý program je vytvořen v souladu s odpovídající [rozhraní IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) předán jako argument [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Zatímco ladicí `IDebugProgram2` moduly také vytvářejí rozhraní představující programy, tyto programy nejsou vytvořeny v souladu s programovým uzdlením. Rozhraní `IDebugProgramNode2` vytvořená DE se používají pro skutečné ladění, zatímco rozhraní vytvořená portem se používají pouze pro zjišťování, které programy jsou spuštěny v procesu.

## <a name="see-also"></a>Viz také
- [Procesy](../../extensibility/debugger/processes.md)
- [Uzly programů](../../extensibility/debugger/program-nodes.md)
- [Moduly](../../extensibility/debugger/modules.md)
- [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md)
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [Pozice dokumentu](../../extensibility/debugger/document-position.md)
- [Kontext kódu](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
