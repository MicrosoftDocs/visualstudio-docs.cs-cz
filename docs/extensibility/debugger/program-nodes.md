---
title: Uzly programu | Microsoft Docs
description: Tento článek popisuje definice a roli uzlu programu v architektuře ladicího programu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4c26fa95a5fedf325591ce517e7c12ecebcd705c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899079"
---
# <a name="program-nodes"></a>Uzly programu
V architektuře ladicího programu, *uzel programu*:

- Je jednoduchý popis programu.

- Může identifikovat sebe sama a proces, ve kterém je spuštěný. Uzel programu lze připojit k, odpojit od a popsat modul ladění (DE), který jej vytvořil, pokud nějaký existuje.

- Je reprezentován rozhraním [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , obvykle vytvořeným pomocí de nebo portem. Uzly programu jsou přidány do portu voláním [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Když je do portu přidán uzel programu, je přidán do procesu obsahujícího program, který tento uzel programu představuje.

  Po spuštění relace ladění se v závislosti na implementaci balíčku pro ladění používají uzly programu k vytváření odpovídajících programů. Pokud se pro své programy dotazuje proces, jsou tyto programy vyhodnoceny, jeden pro každý uzel programu.

  Před připojením programu k rozhraní IDE potřebuje pouze jednoduchý popis programu. Tyto informace lze získat z uzlu program. Jakmile je program připojen k, rozhraní IDE zobrazí podrobnější informace, například seznam všech vláken spuštěných v programu. Tyto informace se získávají z samotného programu.

## <a name="see-also"></a>Viz také
- [Programy](../../extensibility/debugger/programs.md)
- [Procesy](../../extensibility/debugger/processes.md)
- [Ladicí stroj](../../extensibility/debugger/debug-engine.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
