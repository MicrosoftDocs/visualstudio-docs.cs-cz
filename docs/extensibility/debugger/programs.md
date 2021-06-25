---
title: Programy | Microsoft Docs
description: Tento článek popisuje definici a roli programu v architektuře ladicího programu v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 07b23fbafd9342b555e2578c4bc0401371e30785
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901276"
---
# <a name="programs"></a>Programy
V architektuře ladicího programu *program*:

- Je kontejner pro sadu vláken i sadu modulů. Program nemá v operačním systému Windows žádnou analogii.

     Program je druh podprocesu. Když například ladíte web, můžete skript vidět jako program. Zatímco skript běží v procesu skriptovacího stroje, nezávisle na jiných skriptech, má také vlastní sadu vláken. Ladicí modul (DE) se připojí k programu, nikoli k procesu nebo vláknu.

- Dokáže identifikovat sebe a proces, ve které běží. Program lze připojit k, odpojit od a popsat destrukce, která ho vytvořila, pokud je k dispozici. Program může také provádět, zastavovat, pokračovat a být ukončen.

- Může vytvořit výčet všech vláken. Program může také zadat vlastní zpětný překlad datového proudu a může vytvořit výčet všech kontextů kódu dané pozice dokumentu.

- Je reprezentován [rozhraním IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) vytvořeným před připojením programu nebo jako součást procesu připojení v závislosti na implementaci. Když port vyjmenuje programy procesu, vytvoří se každý program v souladu s odpovídajícím [rozhraním IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) předaného jako argument uzlu [AddProgramNode.](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) Zatímco ladicí moduly také vytvářejí rozhraní pro reprezentaci programů, tyto programy se nevytvářely v souladu `IDebugProgram2` s uzlem programu. Rozhraní vytvořená DE se používají ke skutečnému ladění, zatímco rozhraní vytvořená portem slouží pouze ke zjištění, které programy běží `IDebugProgramNode2` v procesu.

## <a name="see-also"></a>Viz také
- [Procesy](../../extensibility/debugger/processes.md)
- [Uzly programu](../../extensibility/debugger/program-nodes.md)
- [Moduly](../../extensibility/debugger/modules.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [Pozice dokumentu](../../extensibility/debugger/document-position.md)
- [Kontext kódu](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
