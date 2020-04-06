---
title: Uzly programu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2943f74c7316495be93c2f5c20998ffa685f5d01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738214"
---
# <a name="program-nodes"></a>Uzly programů
V architektuře ladicího programu *uzel programu*:

- Je lehký popis programu.

- Dokáže se identifikovat a proces, ve kterých běží. Uzel programu lze připojit, odpojit od a popsat ladicí modul (DE), který jej vytvořil, pokud existuje.

- Je reprezentován [rozhraním IDebugProgramNode2,](../../extensibility/debugger/reference/idebugprogramnode2.md) obvykle vytvořené DE nebo portem. Uzly programů jsou přidány do portu voláním [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Když je uzel programu přidán do portu, je přidán do procesu obsahujícího program, který tento uzel programu představuje.

  Někdy po spuštění relace ladění, v závislosti na implementaci balíčku ladění, program uzly se používají k vytvoření odpovídající programy. Při dotazování procesu pro jeho programy jsou programy uvedeny ve výčtu, jeden pro každý uzel programu.

  Před připojením programu ide potřebuje pouze zjednodušený popis programu. Tyto informace lze získat z uzlu programu. Jakmile je program připojen k, ide zobrazí podrobnější informace, jako je například seznam všech podprocesů spuštěných v programu. Tyto informace jsou získány ze samotného programu.

## <a name="see-also"></a>Viz také
- [Programy](../../extensibility/debugger/programs.md)
- [Procesy](../../extensibility/debugger/processes.md)
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
