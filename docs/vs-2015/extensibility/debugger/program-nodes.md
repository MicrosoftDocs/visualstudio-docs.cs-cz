---
title: Uzly programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a06be4ef0a69ec173f171ba202f1f479448b1ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153649"
---
# <a name="program-nodes"></a>Uzly programů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V souvislosti s architekturou ladicího programu, **uzel programu**:  
  
- Je jednoduchý popis programu.  
  
- Může identifikovat sebe sama a proces, na kterém běží, a může být připojen k, oddělit se od a popsat modul ladění (DE), který ho vytvořil, pokud nějaký existuje.  
  
- Je reprezentován rozhraním [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , obvykle vytvořeným pomocí de nebo portem. Uzly programu jsou přidány do portu voláním [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Když je do portu přidán uzel programu, je přidán do procesu obsahujícího program, který tento uzel programu představuje.  
  
  Po spuštění relace ladění se v závislosti na implementaci balíčku pro ladění používají uzly programu k vytváření odpovídajících programů. Pokud se pro své programy dotazuje proces, jsou tyto programy vyhodnoceny, jeden pro každý uzel programu.  
  
  Před připojením programu k rozhraní IDE potřebuje pouze jednoduchý popis programu. Tyto informace lze získat z uzlu program. Jakmile je program připojen k, rozhraní IDE potřebuje zobrazit podrobnější informace, jako je například seznam všech vláken spuštěných v programu. Tyto informace se získávají z samotného programu.  
  
## <a name="see-also"></a>Viz také  
 [Spuštěn](../../extensibility/debugger/programs.md)   
 [Procesem](../../extensibility/debugger/processes.md)   
 [Ladicí stroj](../../extensibility/debugger/debug-engine.md)   
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
