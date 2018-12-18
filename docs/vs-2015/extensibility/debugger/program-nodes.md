---
title: Program uzly | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3fa7e0969c9d45ae07280a8648036bd07c000974
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774481"
---
# <a name="program-nodes"></a>Uzly programů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Z hlediska architektury ladicího programu **program uzel**:  
  
- Představuje jednoduchý popis programu.  
  
- Můžete identifikovat samostatně a proces je spuštěn v a lze připojit k být odpojen od a popisují ladicího stroje (DE), který byl vytvořen, pokud existuje.  
  
- Je reprezentován [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) rozhraní, obvykle vytváří DE nebo portu. Uzly programů jsou přidána na port voláním [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Když program uzel se přidá k portu, přidá se do procesu obsahující program, který představuje tento uzel programu.  
  
  Nějakou dobu, po spuštění relace ladění, v závislosti na implementaci balíček ladicí program uzly slouží k vytvoření odpovídající programy. Když je proces pro jeho programy, jsou uvedené programy, jeden pro každý uzel programu.  
  
  Než programu přiřazen, rozhraní IDE potřebuje jednoduchý popis programu. Tyto informace můžete získat z uzlu programu. Jakmile program je připojen k, integrovaném vývojovém prostředí musí zobrazit podrobnější informace, jako je například seznam všechna vlákna spuštěná v programu. Tyto informace se získávají z této aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Programy](../../extensibility/debugger/programs.md)   
 [Procesy](../../extensibility/debugger/processes.md)   
 [Ladicí stroj](../../extensibility/debugger/debug-engine.md)   
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

