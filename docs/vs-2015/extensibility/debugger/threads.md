---
title: Vlákna | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 028ad25495ba01d9763c8bec3bbb9c4480d72ff8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185361"
---
# <a name="threads"></a>Vlákna
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V souvislosti s architekturou ladicího programu **vlákno**:  
  
- Je základní jednotkou výpočtu. Vlákno postupně provede své pokyny v rámci kontextu jediného zásobníku volání, přechod z jednoho kontextu kódu na další.  
  
- Může identifikovat sebe sama a program, ve kterém je spuštěný, a může být pojmenován, pozastavený a obnovený. Vlákno může také vytvořit výčet přidružených rámců zásobníku a za určitých podmínek lze přesunout do jiného rámce zásobníku. Vzhledem k kontextu bloku zásobníku může vlákno vracet své přidružené logické vlákno, pokud existuje. Vlákno má vlastnosti, jako je například počet pozastavení, které lze zobrazit v okně vláken rozhraní IDE.  
  
- Je reprezentován rozhraním [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , obvykle vytvořené modulem ladění (de) nebo virtuálním počítačem jako v důsledku provádění programu.  
  
## <a name="see-also"></a>Viz také  
 [Spuštěn](../../extensibility/debugger/programs.md)   
 [Rámce zásobníku](../../extensibility/debugger/stack-frames.md)   
 [Ladicí stroj](../../extensibility/debugger/debug-engine.md)   
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)   
 [Správce ladění relace](../../extensibility/debugger/session-debug-manager.md)
