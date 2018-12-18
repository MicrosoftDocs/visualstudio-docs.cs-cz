---
title: Rámců zásobníku | Dokumentace Microsoftu
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
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebd9f1881f0e0579a3b319f6608cdbf348ed027b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789327"
---
# <a name="stack-frames"></a>Bloky zásobníku
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Z hlediska architektury ladicího programu **rámec zásobníku**:  
  
-   Je abstrakcí zásobníku, která poskytuje kontext spuštění vlákna. Vlákno vždy provede v rámci funkce. Rámec zásobníku obsahuje místní proměnné, funkce a argumenty do něj. Pokud chcete ladit pomocí sady Visual Studio, musí podporovat rámce zásobníku jazyka nebo prostředí, které jsou právě laděny.  
  
-   Můžete identifikovat a popsat sám sebe i může vrátit přidružené vlákno. Rámec zásobníku může také vrátit kontext kódu, který představuje aktuální ukazatele na instrukci, jakož i související dokumentaci a kontext vyhodnocení výrazu.  
  
-   Obsahuje vlastnosti, které popisují název, typ a hodnotu místní proměnné a argumenty a které jsou uvedeny v různých ladicích oknech integrovaného vývojového prostředí.  
  
-   Je reprezentován [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) rozhraní, obvykle vytvoří pomocí ladicího stroje (DE) nebo virtuální počítač následkem podproces.  
  
## <a name="see-also"></a>Viz také  
 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)   
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)   
 [Ladicí stroj](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)

