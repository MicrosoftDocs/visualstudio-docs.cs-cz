---
title: Uzly programu | Microsoft Docs
description: Tento článek popisuje definice a roli uzlu programu v architektuře ladicího programu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 5658026b60006a58ba168ca713028b9876a3c57d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094624"
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
